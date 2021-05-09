# Working with Data
LWC- Working with the Data


## Summary
Now you know several ways to interact with Salesforce data in your Lightning web components. Some solutions are preferred to others under certain circumstances. This table summarizes recommended solutions by use case.

<p align="center">
  <b>Use Cases for Interacting with Salesforce Data
    
|   Use Case          |   Recommended Solution           | Notes  |
| ------------------- |--------------------------------  | -------|
| View or edit a record specifying its layout or a list of fields |     lightning-record-form     |  |
| View a record with a custom form layout or custom rendering of record data     |  lightning-record-view-form  |  |
| Edit a record with a custom form layout, custom rendering of record data, or prepopulated field values     |    lightning-record-edit-form      |    |
| Read metadata or read data for one record|  LDS wire adapters       |   Can be combined, but operations will run on independent transactions |
| Create, edit, or delete one record     |  LDS functions |   Can be combined, but operations will run on independent transactions |
| Read multiple records     |   Call Apex with @wire      |   Annotate the Apex method with cacheable=true |
| Read multiple records on a one-time invocation or modify multiple records |   Call Apex imperatively     |    For reads, annotate the Apex method with cacheable=true |
</p>

When you work with data in Lightning web components, error handling varies. How you access errors depends on how you’re interacting with the data.

<p align="center">
  <b>Handling Server Errors </b>
    
|   How to Work with Data         |  How to Access Server Errors     |
| --------------------------------|--------------------------------  |
|Use either an LDS wire adapter or an Apex method, and decorate a property  | Use reduceErrors to handle the error that’s returned to the wired property in decoratedProperty.error|
|Use either an LDS wire adapter or an Apex method, and decorate a function|Use reduceErrors to handle the error that’s returned in the object parameter received by the wired   ``` function decoratedFunction({data, error}) {...}```|
|Imperatively invoke either an LDS wire function or an Apex method| Use reduceErrors to handle the error that’s received as a parameter on the catch method's callback function  ``` functionToInvoke().then(data => {...}).catch(error => {...});```|

</p>
