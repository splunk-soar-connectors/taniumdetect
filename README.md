[comment]: # "Auto-generated SOAR connector documentation"
# Tanium Detect

Publisher: Robert Drouin  
Connector Version: 1\.5\.3  
Product Vendor: Tanium  
Product Name: Detect  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.6\.19142  

This app integrates with Tanium Detect to perform several investigate, generic, and ingest type of actions

[comment]: # ""
[comment]: # "    File: readme.md"
[comment]: # "    Copyright (c) 2018-2020 Splunk Inc."
[comment]: # ""
[comment]: # "    Licensed under Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0.txt)"
[comment]: # ""
Tanium Detect is a module for Tanium to detect compromised machines with continuous monitoring,
real-time alerting, and the flexibility to use a wide range of threat data sources for in-depth
endpoint scanning.


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Detect asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base\_url** |  required  | string | IP or Hostname of Tanium Server
**Verify Server Certificate** |  optional  | boolean | Verify Server Certificate
**Username** |  required  | string | Username
**Password** |  required  | password | Password
**timezone** |  required  | timezone | Tanium server timezone

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[get suppression rule](#action-get-suppression-rule) - Get a suppression rule by ID  
[create suppression rule](#action-create-suppression-rule) - Create a new suppression rule  
[list suppression rules](#action-list-suppression-rules) - List all available suppression rules in the system  
[delete suppression rule](#action-delete-suppression-rule) - Delete one suppression rule  
[get source](#action-get-source) - Get a single source by ID  
[delete source](#action-delete-source) - Delete an existing source by ID  
[list sources](#action-list-sources) - List sources configured to manage IOC's in the system  
[get sourcetype](#action-get-sourcetype) - Show details for a single source type by ID  
[list sourcetypes](#action-list-sourcetypes) - List source types supported on this system  
[get notification count](#action-get-notification-count) - List notification counts for the last N days in UTC by default  
[get notification](#action-get-notification) - Show a single notification by ID  
[update notification](#action-update-notification) - Update the state of one notification by ID  
[list notifications](#action-list-notifications) - List notifications with optional filtering, sorting, and pagination  
[delete notification](#action-delete-notification) - Delete one notification by ID  
[modify label](#action-modify-label) - Modify the properties of an existing label by ID  
[get label](#action-get-label) - Request a single label by ID  
[delete label](#action-delete-label) - Delete an existing label by ID\. Will fail if label is used in group configurations  
[create label](#action-create-label) - Create a new label  
[list labels](#action-list-labels) - List all available labels in the system  
[get intel](#action-get-intel) - Show a single Intel Document by ID  
[delete intel](#action-delete-intel) - Delete the identified intel document by ID  
[list intel](#action-list-intel) - List intel documents  
[get counts group](#action-get-counts-group) - List alert counts grouped by computer name or intel id  
[get alert count](#action-get-alert-count) - List alert counts for the last N days, in UTC by default  
[get alert](#action-get-alert) - Show a single alert by ID  
[update state](#action-update-state) - Update the state of an alert  
[list alerts](#action-list-alerts) - List alerts with optional filtering, sorting, and pagination  
[delete alert](#action-delete-alert) - Delete an alert by ID  
[on poll](#action-on-poll) - Callback action for the on\_poll ingest functionality  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'get suppression rule'
Get a suppression rule by ID

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the suppression rule | numeric |  `tanium detect suppression rule id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect suppression rule id` 
action\_result\.status | string | 
action\_result\.data\.\*\.id | numeric |  `tanium detect suppression rule id` 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.description | string | 
action\_result\.data\.\*\.intelDocId | numeric |  `tanium detect intel doc id` 
action\_result\.data\.\*\.revision | numeric | 
action\_result\.data\.\*\.createdAt | string | 
action\_result\.data\.\*\.updatedAt | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'create suppression rule'
Create a new suppression rule

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**name** |  required  | The name for the new rule | string | 
**config** |  optional  | The new config for the rule | string | 
**description** |  optional  | The new description for the rule | string | 
**inteldocid** |  optional  | The ID of the intel doc to associate the rule to | numeric |  `tanium detect intel doc id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.name | string | 
action\_result\.parameter\.config | string | 
action\_result\.parameter\.description | string | 
action\_result\.parameter\.inteldocid | numeric |  `tanium detect intel doc id` 
action\_result\.status | string | 
action\_result\.data | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list suppression rules'
List all available suppression rules in the system

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**limit** |  optional  | The maximum number of rules to return\. \(Default\: 100\) | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.limit | numeric | 
action\_result\.status | string | 
action\_result\.data\.\*\.\*\.name | string | 
action\_result\.data\.\*\.\*\.description | string | 
action\_result\.data\.\*\.\*\.intelDocId | numeric |  `tanium detect intel doc id` 
action\_result\.data\.\*\.\*\.updatedAt | string | 
action\_result\.data\.\*\.\*\.id | numeric |  `tanium detect suppression rule id` 
action\_result\.data\.\*\.\*\.createdAt | string | 
action\_result\.data\.\*\.\*\.revision | numeric | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete suppression rule'
Delete one suppression rule

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the rule to delete | numeric |  `tanium detect suppression rule id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect suppression rule id` 
action\_result\.status | string | 
action\_result\.data | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get source'
Get a single source by ID

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the source to show | numeric |  `tanium detect source id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect source id` 
action\_result\.status | string | 
action\_result\.data\.\*\.id | numeric |  `tanium detect source id` 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.description | string | 
action\_result\.data\.\*\.type | string | 
action\_result\.data\.\*\.enabled | string | 
action\_result\.data\.\*\.indicatorCount | numeric | 
action\_result\.data\.\*\.signalCount | numeric | 
action\_result\.data\.\*\.createdAt | string | 
action\_result\.data\.\*\.updatedAt | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete source'
Delete an existing source by ID

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the source to delete | numeric |  `tanium detect source id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect source id` 
action\_result\.status | string | 
action\_result\.data | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list sources'
List sources configured to manage IOC's in the system

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**limit** |  optional  | The maximum number of sources to return\. \(Default\: 100\) | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.limit | numeric | 
action\_result\.status | string | 
action\_result\.data\.\*\.\*\.name | string | 
action\_result\.data\.\*\.\*\.type | string | 
action\_result\.data\.\*\.\*\.description | string | 
action\_result\.data\.\*\.\*\.enabled | boolean | 
action\_result\.data\.\*\.\*\.updatedAt | string | 
action\_result\.data\.\*\.\*\.id | numeric |  `tanium detect source id` 
action\_result\.data\.\*\.\*\.createdAt | string | 
action\_result\.data\.\*\.\*\.indicatorCount | numeric | 
action\_result\.data\.\*\.\*\.signalCount | numeric | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get sourcetype'
Show details for a single source type by ID

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the source type to get | numeric |  `tanium detect sourcetype id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect sourcetype id` 
action\_result\.status | string | 
action\_result\.data\.\*\.id | numeric |  `tanium detect sourcetype id` 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.description | string | 
action\_result\.data\.\*\.canAutoQuickScan | boolean | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list sourcetypes'
List source types supported on this system

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.data\.\*\.\*\.name | string | 
action\_result\.data\.\*\.\*\.type | string | 
action\_result\.data\.\*\.\*\.description | string | 
action\_result\.data\.\*\.\*\.id | numeric |  `tanium detect sourcetype id` 
action\_result\.data\.\*\.\*\.canAutoQuickScan | boolean | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get notification count'
List notification counts for the last N days in UTC by default

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**num\_days** |  optional  | Past number of days to account for \(Default\: 30\) | numeric | 
**inteldocid** |  optional  | Intel doc ID to filter by | numeric |  `tanium detect intel doc id` 
**scanconfigid** |  optional  | Scan config ID to filter by | numeric |  `tanium detect scan config id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.num\_days | numeric | 
action\_result\.parameter\.inteldocid | numeric |  `tanium detect intel doc id` 
action\_result\.parameter\.scanconfigid | numeric |  `tanium detect scan config id` 
action\_result\.status | string | 
action\_result\.data\.\*\.\*\.date | string | 
action\_result\.data\.\*\.\*\.count | numeric | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get notification'
Show a single notification by ID

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the notification to show | numeric |  `tanium detect notification id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect notification id` 
action\_result\.status | string | 
action\_result\.data\.\*\.id | string |  `tanium detect notification id` 
action\_result\.data\.\*\.type | string | 
action\_result\.data\.\*\.guid | string | 
action\_result\.data\.\*\.state | string | 
action\_result\.data\.\*\.priority | string | 
action\_result\.data\.\*\.severity | string | 
action\_result\.data\.\*\.details | string | 
action\_result\.data\.\*\.alertedAt | string | 
action\_result\.data\.\*\.createdAt | string | 
action\_result\.data\.\*\.updatedAt | string | 
action\_result\.data\.\*\.computerName | string | 
action\_result\.data\.\*\.compurterIpAddress | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'update notification'
Update the state of one notification by ID

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the notification to update | numeric |  `tanium detect notification id` 
**state** |  optional  | The new state for the notification | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect notification id` 
action\_result\.parameter\.state | string | 
action\_result\.status | string | 
action\_result\.data\.\*\.\*\.id | string |  `tanium detect notification id` 
action\_result\.data\.\*\.type | string | 
action\_result\.data\.\*\.guid | string | 
action\_result\.data\.\*\.state | string | 
action\_result\.data\.\*\.priority | string | 
action\_result\.data\.\*\.severity | string | 
action\_result\.data\.\*\.details | string | 
action\_result\.data\.\*\.alertedAt | string | 
action\_result\.data\.\*\.createdAt | string | 
action\_result\.data\.\*\.updatedAt | string | 
action\_result\.data\.\*\.computerName | string | 
action\_result\.data\.\*\.compurterIpAddress | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list notifications'
List notifications with optional filtering, sorting, and pagination

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**type** |  optional  | Filter notifications by the specified type\(s\) | string | 
**sort** |  optional  | A comma\-separated list of \+/\- pairs controlling sort ordering | string | 
**limit** |  optional  | The maximum number of notifications to return\. \(Default\: 100\) | numeric | 
**offset** |  optional  | The offset at which to begin listing notifications | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.type | string | 
action\_result\.parameter\.sort | string | 
action\_result\.parameter\.limit | numeric | 
action\_result\.parameter\.offset | numeric | 
action\_result\.status | string | 
action\_result\.data\.\*\.\*\.id | string |  `tanium detect notification id` 
action\_result\.data\.\*\.\*\.type | string | 
action\_result\.data\.\*\.\*\.guid | string | 
action\_result\.data\.\*\.\*\.state | string | 
action\_result\.data\.\*\.\*\.priority | string | 
action\_result\.data\.\*\.\*\.severity | string | 
action\_result\.data\.\*\.\*\.details | string | 
action\_result\.data\.\*\.\*\.alertedAt | string | 
action\_result\.data\.\*\.\*\.createdAt | string | 
action\_result\.data\.\*\.\*\.updatedAt | string | 
action\_result\.data\.\*\.\*\.computerName | string | 
action\_result\.data\.\*\.\*\.compurterIpAddress | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete notification'
Delete one notification by ID

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the notification to delete | numeric |  `tanium detect notification id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect notification id` 
action\_result\.status | string | 
action\_result\.data | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'modify label'
Modify the properties of an existing label by ID

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the label to update | numeric |  `tanium detect label id` 
**name** |  required  | The new name for the label | string | 
**description** |  required  | The new description for the label | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect label id` 
action\_result\.parameter\.name | string | 
action\_result\.parameter\.description | string | 
action\_result\.status | string | 
action\_result\.data\.\*\.id | numeric |  `tanium detect label id` 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.description | string | 
action\_result\.data\.\*\.indicatorCount | numeric | 
action\_result\.data\.\*\.signalCount | numeric | 
action\_result\.data\.\*\.createdAt | string | 
action\_result\.data\.\*\.updatedAt | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get label'
Request a single label by ID

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the label to get | numeric |  `tanium detect label id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect label id` 
action\_result\.status | string | 
action\_result\.data\.\*\.id | numeric |  `tanium detect label id` 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.description | string | 
action\_result\.data\.\*\.indicatorCount | numeric | 
action\_result\.data\.\*\.signalCount | numeric | 
action\_result\.data\.\*\.createdAt | string | 
action\_result\.data\.\*\.updatedAt | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete label'
Delete an existing label by ID\. Will fail if label is used in group configurations

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the label that will be deleted | numeric |  `tanium detect label id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect label id` 
action\_result\.status | string | 
action\_result\.data | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'create label'
Create a new label

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**name** |  required  | User facing text to show for the label | string | 
**description** |  required  | Description for the label | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.name | string | 
action\_result\.parameter\.description | string | 
action\_result\.status | string | 
action\_result\.data\.\*\.id | numeric |  `tanium detect label id` 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.description | string | 
action\_result\.data\.\*\.indicatorCount | numeric | 
action\_result\.data\.\*\.signalCount | numeric | 
action\_result\.data\.\*\.createdAt | string | 
action\_result\.data\.\*\.updatedAt | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list labels'
List all available labels in the system

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**limit** |  optional  | The maximum number of labels to return\. \(Default\: 100\) | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.limit | numeric | 
action\_result\.status | string | 
action\_result\.data\.\*\.\*\.name | string | 
action\_result\.data\.\*\.\*\.description | string | 
action\_result\.data\.\*\.\*\.updatedAt | string | 
action\_result\.data\.\*\.\*\.id | numeric | 
action\_result\.data\.\*\.\*\.createdAt | string | 
action\_result\.data\.\*\.\*\.indicatorCount | numeric | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get intel'
Show a single Intel Document by ID

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the intel document to show | numeric |  `tanium detect intel doc id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect intel doc id` 
action\_result\.status | string | 
action\_result\.data\.\*\.id | numeric |  `tanium detect intel doc id` 
action\_result\.data\.\*\.revisionId | numeric | 
action\_result\.data\.\*\.type | string | 
action\_result\.data\.\*\.typeVersion | string | 
action\_result\.data\.\*\.isSchemaValid | boolean | 
action\_result\.data\.\*\.intrinsicId | string | 
action\_result\.data\.\*\.md5 | string | 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.description | string | 
action\_result\.data\.\*\.size | numeric | 
action\_result\.data\.\*\.alertCount | numeric | 
action\_result\.data\.\*\.complied | string | 
action\_result\.data\.\*\.unresolvedAlertCount | numeric | 
action\_result\.data\.\*\.labelIds | string |  `tanium detect label id` 
action\_result\.data\.\*\.sourceId | numeric | 
action\_result\.data\.\*\.contents | string | 
action\_result\.data\.\*\.createdAt | string | 
action\_result\.data\.\*\.updatedAt | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete intel'
Delete the identified intel document by ID

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the intel document to delete | numeric |  `tanium detect intel doc id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect intel doc id` 
action\_result\.status | string | 
action\_result\.data | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list intel'
List intel documents

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**name** |  optional  | Include only IntelDocs whose "name" matches the given field | string | 
**description** |  optional  | Include only IntelDocs whose "description" matches the given field | string | 
**type** |  optional  | Include only IntelDocs whose "type" matches the given field | string | 
**sort** |  optional  | Use to sort columns using "\+/\-", comma\-separate for multiples\. Ex\: \-alertedAt,\+name | string | 
**limit** |  optional  | The maximum number of IntelDocs to return\. \(Default\: 100\) | numeric | 
**offset** |  optional  | The offset number to begin listing alerts | numeric | 
**nolimit** |  optional  | If TRUE, it will not limit the number of items returned | boolean | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.name | string | 
action\_result\.parameter\.description | string | 
action\_result\.parameter\.type | string | 
action\_result\.parameter\.sort | string | 
action\_result\.parameter\.limit | numeric | 
action\_result\.parameter\.offset | numeric | 
action\_result\.parameter\.nolimit | boolean | 
action\_result\.status | string | 
action\_result\.data\.\*\.\*\.unresolvedAlertCount | numeric | 
action\_result\.data\.\*\.\*\.name | string | 
action\_result\.data\.\*\.\*\.description | string | 
action\_result\.data\.\*\.\*\.typeVersion | string | 
action\_result\.data\.\*\.\*\.sourceId | numeric | 
action\_result\.data\.\*\.\*\.compiled | boolean | 
action\_result\.data\.\*\.\*\.revisionId | numeric | 
action\_result\.data\.\*\.\*\.intrinsicId | string | 
action\_result\.data\.\*\.\*\.isSchemaValid | boolean | 
action\_result\.data\.\*\.\*\.alertCount | numeric | 
action\_result\.data\.\*\.\*\.updatedAt | numeric | 
action\_result\.data\.\*\.\*\.md5 | string | 
action\_result\.data\.\*\.\*\.type | string | 
action\_result\.data\.\*\.\*\.id | numeric | 
action\_result\.data\.\*\.\*\.createdAt | string | 
action\_result\.data\.\*\.\*\.labelIds | string |  `tanium detect label id` 
action\_result\.data\.\*\.\*\.sourceId | numeric | 
action\_result\.data\.\*\.\*\.contents | string | 
action\_result\.data\.\*\.\*\.size | numeric | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get counts group'
List alert counts grouped by computer name or intel id

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**groupby** |  required  | Group alerts by specified group name \(Default\: 'computerName'\) | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.groupby | string | 
action\_result\.status | string | 
action\_result\.data\.\*\.\*\.groupById | string | 
action\_result\.data\.\*\.\*\.groupByValue | string | 
action\_result\.data\.\*\.\*\.count | numeric | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get alert count'
List alert counts for the last N days, in UTC by default

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**num\_days** |  optional  | Past number of days to account for \(Default\: 30\) | numeric | 
**inteldocid** |  optional  | Filter by alerts with specified intel doc ID | numeric |  `tanium detect intel doc id` 
**scanconfigid** |  optional  | Filter by alerts with the specified scan config ID | numeric |  `tanium detect scan config id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.num\_days | numeric | 
action\_result\.parameter\.inteldocid | numeric |  `tanium detect intel doc id` 
action\_result\.parameter\.scanconfigid | numeric |  `tanium detect scan config id` 
action\_result\.status | string | 
action\_result\.data\.\*\.\*\.date | string | 
action\_result\.data\.\*\.\*\.count | numeric | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get alert'
Show a single alert by ID

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the alert to show | numeric |  `tanium detect alert id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect alert id` 
action\_result\.status | string | 
action\_result\.data\.\*\.id | numeric |  `tanium detect alert id` 
action\_result\.data\.\*\.state | string | 
action\_result\.data\.\*\.type | string | 
action\_result\.data\.\*\.guid | string | 
action\_result\.data\.\*\.priority | string | 
action\_result\.data\.\*\.severity | string | 
action\_result\.data\.\*\.intelDocId | numeric |  `tanium detect intel doc id` 
action\_result\.data\.\*\.intelDocRevisionId | numeric | 
action\_result\.data\.\*\.scanConfigId | numeric |  `tanium detect scan config id` 
action\_result\.data\.\*\.scanConfigRevisionId | numeric | 
action\_result\.data\.\*\.computerName | string | 
action\_result\.data\.\*\.compurterIpAddress | string | 
action\_result\.data\.\*\.details | string | 
action\_result\.data\.\*\.alertedAt | string | 
action\_result\.data\.\*\.createdAt | string | 
action\_result\.data\.\*\.updatedAt | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'update state'
Update the state of an alert

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | The ID of the alert to update | numeric |  `tanium detect alert id` 
**state** |  optional  | The new state for the alert | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect alert id` 
action\_result\.parameter\.state | string | 
action\_result\.status | string | 
action\_result\.data\.\*\.id | numeric |  `tanium detect alert id` 
action\_result\.data\.\*\.state | string | 
action\_result\.data\.\*\.type | string | 
action\_result\.data\.\*\.guid | string | 
action\_result\.data\.\*\.priority | string | 
action\_result\.data\.\*\.severity | string | 
action\_result\.data\.\*\.intelDocId | numeric |  `tanium detect intel doc id` 
action\_result\.data\.\*\.intelDocRevisionId | numeric | 
action\_result\.data\.\*\.scanConfigId | numeric |  `tanium detect scan config id` 
action\_result\.data\.\*\.scanConfigRevisionId | numeric | 
action\_result\.data\.\*\.computerName | string | 
action\_result\.data\.\*\.compurterIpAddress | string | 
action\_result\.data\.\*\.details | string | 
action\_result\.data\.\*\.alertedAt | string | 
action\_result\.data\.\*\.createdAt | string | 
action\_result\.data\.\*\.updatedAt | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list alerts'
List alerts with optional filtering, sorting, and pagination

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**state** |  optional  | Filter alerts by the specified states | string | 
**type** |  optional  | Filter alerts by the specified types | string | 
**priority** |  optional  | Filter alerts by they specified priorities | string | 
**severity** |  optional  | Filter alerts by the specified severities | string | 
**inteldocid** |  optional  | Filter alerts by the specified intelDocIds | numeric |  `tanium detect intel doc id` 
**scanconfigid** |  optional  | Filter alerts by the specified scanConfigIds | numeric |  `tanium detect scan config id` 
**computername** |  optional  | Filter alerts by the specified computerNames | string | 
**computeripaddress** |  optional  | Filter alerts by the specified computerIpAddresses | string | 
**sort** |  optional  | Use to sort columns using "\+/\-", comma separate for multiples | string | 
**limit** |  optional  | The maximum number of alerts to return\. \(Default\: 100\) | numeric | 
**offset** |  optional  | The offset number to begin listing alerts | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.state | string | 
action\_result\.parameter\.type | string | 
action\_result\.parameter\.priority | string | 
action\_result\.parameter\.severity | string | 
action\_result\.parameter\.inteldocid | numeric | 
action\_result\.parameter\.scanconfigid | numeric | 
action\_result\.parameter\.computername | string | 
action\_result\.parameter\.computeripaddress | string | 
action\_result\.parameter\.sort | string | 
action\_result\.parameter\.limit | numeric | 
action\_result\.parameter\.offset | numeric | 
action\_result\.status | string | 
action\_result\.data\.\*\.\*\.id | numeric |  `tanium detect alert id` 
action\_result\.data\.\*\.\*\.state | string | 
action\_result\.data\.\*\.\*\.type | string | 
action\_result\.data\.\*\.\*\.guid | string | 
action\_result\.data\.\*\.\*\.priority | string | 
action\_result\.data\.\*\.\*\.severity | string | 
action\_result\.data\.\*\.\*\.intelDocId | numeric |  `tanium detect intel doc id` 
action\_result\.data\.\*\.\*\.intelDocRevisionId | numeric | 
action\_result\.data\.\*\.\*\.scanConfigId | numeric | 
action\_result\.data\.\*\.\*\.scanConfigRevisionId | numeric | 
action\_result\.data\.\*\.\*\.computerName | string | 
action\_result\.data\.\*\.\*\.compurterIpAddress | string | 
action\_result\.data\.\*\.\*\.details | string | 
action\_result\.data\.\*\.\*\.alertedAt | string | 
action\_result\.data\.\*\.\*\.createdAt | string | 
action\_result\.data\.\*\.\*\.updatedAt | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete alert'
Delete an alert by ID

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | ID of the alerts to delete | numeric |  `tanium detect alert id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.id | numeric |  `tanium detect alert id` 
action\_result\.status | string | 
action\_result\.data | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'on poll'
Callback action for the on\_poll ingest functionality

Type: **ingest**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**container\_id** |  optional  | Container IDs to limit the ingestion to | string | 
**start\_time** |  optional  | Start of time range, in epoch time \(milliseconds\) | numeric | 
**end\_time** |  optional  | End of time range, in epoch time \(milliseconds\) | numeric | 
**container\_count** |  optional  | Maximum number of container records to query for | numeric | 
**artifact\_count** |  optional  | Maximum number of artifact records to query for | numeric | 

#### Action Output
No Output