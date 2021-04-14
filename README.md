# Parent-Child Hierarchy Conversion Script Repository
*SQL Script templates for hierarchy conversions - from Parent-Child to Level format*

This repository contains two sample table functions that perform Parent-Child hierarchy conversions to a level hierarchy format.
The table functions can be used as input in Calculation Views that define the level columns as SAP HANA level hierarchy (in the Calculation View's 'Semantics' node). As a consequence, the parent-child hierarchy information can be consumed as hierarchy in Tableau analytics (SAP HANA level hierarchies are natively supported).

The hierarchy conversion process is lightweight and fast so that it can be executed on-the-fly without the need to persist the hierarchy data in the level format.
If desired, the table function could also be scheduled to perform the conversion periodically with persisted results. In most cases this should not be necessary.

The two provided sample functions can be copied & pasted in your SAP HANA environment.
The function name, source information (where the parent & child columns can be found) and amount of levels should be adjusted to reflect your data model.

**BW_GENERATED_HIERARCHY.hdbtablefunction**

 - can be used on **BW generated Parent-Child hierarchy views**
 - comes with an **input parameter** that supports the selection of a specific hierarchy when multiple are contained in the same table / view (as is usual in SAP BW)
 - supports handling of separate **key and text columns** from the hierarchy master data
 - written for a 9 level Parent-Child hierarchy, but can be easily adjusted to reflect the depth of the Parent-Child hierarchy

 **SIMPLE_PCH_CONVERSION.hdbtablefunction**
 
 - **simple & minimalistic** version for better understanding of the hierarchy conversion process
 - **no input parameter** defined
 - **only parent and child source columns** to be provided (no differentiation between key and text)
 - written for a 5 level Parent-Child hierarchy, but can be easily adjusted to reflect the depth of the Parent-Child hierarchy

It is a best practice to create a dimensional Calc View as a shell for the table function in order to define the columns as SAP HANA level hierarchy.
This Calc View can then be joined whenever the level hierarchy needs to be added to a an existing / new view.
