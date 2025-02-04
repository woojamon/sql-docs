---
title: "Release notes for SQL Server Management Studio (SSMS)| Microsoft Docs"
ms.prod: sql
ms.prod_service: "sql-tools"
ms.reviewer: ""
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
author: markingmyname
ms.author: maghan
ms.custom: ""
ms.date: 07/26/2019 
---

# Release notes for SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md.md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

This article provides details about updates, improvements, and bug fixes for the current and previous versions of SSMS.

<!--
The latest ## H2 section of this Release Notes article has been reformatted to match the new standard.
The new standard replaces the use of bullet lists with the 2-column markdown table format.
Please use the new 2-column table format going forward.
And please do include the final blank row of "| &nbsp;| &nbsp;|".

The ## H2 titles are also being shortened, by the removal of unnecessary repetitive strings.
In this case, "## SSMS 17.9" is being shortened to "## 17.9" (as one standard actual example).
And we are appending the 'Month yyyy'.

Also, this file has been renamed to the new standard, which calls for the file name to be with "release-notes-[techAreaName].md".
The old name for this file was 'sql-server-management-studio-changelog-ssms.md'.
But today the new file name is 'release-notes-ssms.md' (still in 'docs/ssms/').

Thank you.
GeneMi. 2019/04/02.
-->

## SSMS 18.2

Download: [Download SSMS 18.2](download-sql-server-management-studio-ssms.md)  
Build number: 15.0.18142.0  
Release date: July 25, 2019

SSMS 18.2 is the latest general availability (GA) release of SSMS. If you need a previous version of SSMS, see [previous SSMS releases](release-notes-ssms.md#previous-ssms-releases).

18.2 is an update to 18.1 with the following new items and bug fixes.

## What's new in 18.2

|  New Item  |  Details  |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Intellisense/Editor | Added support for Data Classification. |
| OPTIMIZE_FOR_SEQUENTIAL_KEY | Added Intellisense support. |
| OPTIMIZE_FOR_SEQUENTIAL_KEY | Turns on an optimization within the database engine that helps improve throughput for high-concurrency inserts into the index. This option is intended for indexes that are prone to last-page insert contention, typically seen with indexes that have a sequential key such as an identity column, sequence, or date/time column. See [CREATE INDEX](../t-sql/statements/create-index-transact-sql.md#sequential-keys) for more details. |
| Query Execution or Results | Added a *Completion time* in the messages to track when a given query completed its execution. |
| Query Execution or Results | Allow more data to be displayed (Result to Text) and stored in cells (Result to Grid). SSMS now allows up to 2M characters for both (up from 256   and 64K, respectively). This also addressed the issue of users not able to grab more than 43680 chars from the cells of the grid. |
| ShowPlan | Added a new attribute in QueryPlan when [inline scalar UDF feature](../relational-databases/performance/intelligent-query-processing.md#scalar-udf-inlining) is enabled  (ContainsInlineScalarTsqlUdfs). |
| SMO | Added support for *Feature Restrictions*. For more information on the feature itself, see [Feature Restrictions](https://docs.microsoft.com/sql/relational-databases/security/feature-restrictions). |
| Integration Services (SSIS) | Perf optimization for SSIS package scheduler in Azure. |
|  |  |

## Bug fixes in 18.2

|  New Item  |  Details  |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Accessibility | Updated the XEvent UI (the grid) to be sortable by pressing F3. |
| Always On | Fixed an issue where SSMS was throwing an error when trying to delete an Availability Group (AG) |
| Always On | Fixed an issue where SSMS was presenting the wrong failover wizard, when replicas are configured as Synchronous, when using read scale AGs (cluster type=NONE). Now, SSMS presents the wizard for Force_Failover_Allow_Data_Loss option, which is the only one allowed for cluster type NONE Availability |
| Always On | Fixed an issue where the wizard was restricting the number of allowed synchronizations to three |
| Data Classification | Fixed an issue where SSMS was throwing an *Index (zero-based) must be greater than or equal to zero* error when trying to view data classification reports on databases with CompatLevel less than 150. |
| General SSMS | Fixed an issue where the user was unable to horizontal scroll Results pane via mouse wheel. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/34145641) for more details. |
| General SSMS | Updated *Activity Monitor* to ignore benign wait types SQLTRACE_WAIT_ENTRIES |
| General SSMS | Fixed an issue where some color options *(Text Editor > Editor Tab and Status Bar)* were not persisted. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37924165)
| General SSMS | In connection dialog, replaced *Active Directory - Universal with MFA support* with *Azure Active Directory - Universal with MFA* (functionality is the same, but hopefully it's less confusing). |
| General SSMS | Updated SSMS to use correct defaults values when creating an Azure SQL Database. |
| General SSMS | Fixed an issue where the user was not able to *Start PowerShell* from a node in [Register Servers](register-servers/register-servers.md) when the server is a [SQL Linux container](../linux/quickstart-install-connect-docker.md). |
| Import Flat File | Fixed an issue where *Import Flat File* was not working after upgrading from SSMS 18.0 to 18.1. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37912636) |
| Import Flat File | Fixed an issue where *Import Flat File Wizard was reporting a duplicate or invalid column* on a .csv file with headers with Unicode characters. |
| Object Explorer | Fixed an issue where some menu items (for example, SQL server *Import and Export Wizard*) where missing or disable when connected to SQL Express. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37500016) for more details. |
| Object Explorer | Fixed an issue which was causing SSMS to crash when an object is dragged from Object Explorer to the editor. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37887988) for more details. |
| Object Explorer | Fixed an issue where renaming databases was causing incorrect database names to show up in Object Explorer. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37638472) for more details. |
| Object Explorer | Fixed a long outstanding issue where trying to expand the *Tables* node in Object Explorer for a database which is set to use a collation that is not supported by Windows anymore triggers an error (and the user can't expand his or her tables). An example of such collation would be Korean_Wansung_Unicode_CI_AS. |
| [Register Servers](register-servers/register-servers.md) | Fixed an issue where trying to issue a query against multiple servers (under a *Group* in Registered Servers) when the Registered Server uses either *Active Directory - Integrated* or *Azure Active Directory - Universal with MFA* did not work because SSMS failed to connect. |
| [Register Servers](register-servers/register-servers.md) | Fixed an issue where trying to issue a query against multiple servers (under a *Group* in Registered Servers) when the registered server uses either *Active Directory - Password* or *SQL Auth* and the user chose not to remember the password would cause SSMS to crash. |
| Reports | Fixed an issue in *Disk Usage* reports where the report was failing to when data files had a vast number of extents. |
| Replication Tools | Fixed an issue where Replication Monitor was not working with publisher DB in AG and distributor in AG (this was previously fixed in SSMS 17.x |
| SQL Agent | Fixed an issue that when Adding, inserting, editing or removing job steps, was causing focus to be reset the first row instead of the active row. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/38070892) for more details. |
| SMO/Scripting | Fixed an issue where *CREATE OR ALTER* was not scripting objects that had extended properties on them. See [UserVoice](https://feedback.azure.com/forums/908035-sql-server/suggestions/37236748) for more details. |
| SMO/Scripting | Fixed an issue where SSMS wasn't able to script CREATE EXTERNAL LIBRARY correctly. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37868089) for more details. |
| SMO/Scripting |  Fixed an issue where trying to run the *Generate Scripts* against a database with a few thousand tables (was causing the progress dialog to appear to be stuck. |
| SMO/Scripting | Fixed an issue where scripting of *External Table* on SQL 2019 did not work. |
| SMO/Scripting | Fixed an issue where scripting of *External Data Source* on SQL 2019 did not work. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/34295080) for more details. |
| SMO/Scripting | Fixed an issue where *extended  properties* on columns were not scripted when targeting Azure SQL DB. See [stackoverflow](https://stackoverflow.com/questions/56952337/how-can-i-script-the-descriptions-of-columns-in-ms-sql-server-management-studio) for more details. |
| SMO/Scripting | Last-page insert: SMO - Add property *Index.IsOptimizedForSequentialKey* |
|**SSMS Setup**| **Mitigated an issue where SSMS setup was incorrectly blocking the installation of SSMS reporting mismatching languages. This could have been an issue in some abnormal situations, like an aborted setup or an incorrect uninstall of a previous version of SSMS. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37483594/) for more details.** |
| XEvent Profiler | Fixed a crash when the viewer is being closed. |

### Known issues (18.2)

- Database Diagram created from on an SSMS running on machine A cannot be modified from machine B (it would crash SSMS). See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37992649) for more details.

- SSMS 18.0 redraw issues when switching between multiple query windows. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37474042) - there is a workaround for this one listed, which is to disable h/w acceleration in Tools | Options

You can reference [UserVoice](https://feedback.azure.com/forums/908035-sql-server) for other known issues and to provide feedback to the product team.

## Previous SSMS releases

Download previous SSMS versions by clicking the title links in the following sections:

## ![download](../ssdt/media/download.png) [SSMS 18.1](https://go.microsoft.com/fwlink/?linkid=2094583)

- Release number: 18.1  
- Build number: 15.0.18131.0  
- Release date: June 11, 2019  

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x804) | [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x404) | [English (United States)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x409) | [French](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x40c) | [German](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x407) | [Italian](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x410) | [Japanese](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x411) | [Korean](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x412) | [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x416) | [Russian](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x419) | [Spanish](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x40a)

SSMS 18.1 is the latest general availability (GA) release of SSMS. If you need a previous version of SSMS, see [previous SSMS releases](release-notes-ssms.md#previous-ssms-releases).

18.1 is a small update to 18.0 with the following new item and bug fixes.

## What's new in 18.1

| New item| Details|
| :-------| :------|
| Database diagrams | [Database diagrams were added back into SSMS](https://feedback.azure.com/forums/908035/suggestions/37507828).
| SSBDIAGNOSE.EXE |The SQL Server Diagnose (command line tool) was added back into the SSMS package.|
| Integration Services (SSIS) | Support for scheduling SSIS package, located in SSIS Catalog in Azure or File System, in Azure. There are three entries for launching the New Schedule dialog, *New Schedule…* menu item shown when right-clicking the SSIS package in SSIS Catalog in Azure, *Schedule SSIS Package in Azure* menu item under *Migrate to Azure* menu item under *Tools* menu item and "Schedule SSIS in Azure" shown when right-clicking Jobs folder under SQL Server agent of Azure SQL Database Managed Instance.|

## Bug fixes in 18.1

| New Item | Details |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Accessibility | Improved accessibility of the Agent Job UI. |
| Accessibility | Improved accessibility on Stretch Monitor page by adding accessible name for *Auto Refresh* button and also adding an intelligent Accessible Name that will help users know not only what button they are on but the impact of pressing it. |
| ADS integration| Fixed a possible crash in SSMS when trying to use the ADS registered servers.|
| Database designer | Added support for Latin1_General_100_BIN2_UTF8 collation (available in SQL Server 2019 CTP3.0) |
| Data classification | Prevent adding sensitivity labels to columns in history table, which isn't supported. |
| Data classification | Addressed issue related to incorrect handling of compatibility level (server vs database). |
| Database designer | Added support for Latin1_General_100_BIN2_UTF8 collation (available in SQL2019 CTP3.0). |
| General SSMS | Fixed an issue where scripting of pseudo columns in an index was incorrect. |
| General SSMS | Fixed an issue in Login properties page where clicking on the *Add Credential* button could throw a Null Reference Exception. |
| General SSMS | Fixed money column size display in index properties page. |
| General SSMS | Fixed an issue where SSMS wasn't honoring the Intellisense settings from *Tools/Options* in the SQL editor window. |
| General SSMS | Fixed an issue where SSMS wasn't honoring the Help settings (online vs offline). |
| High DPI | Fixed layout of controls in error dialogs for unsupported query options. |
| High DPI | Fixed layout of controls in *New Availability Group* page which on some localized version of SSMS. |
| High DPI | Fixed layout of *New Job Schedule* page. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37632094) for more details. |
| Import flat file | Fixed in issue where rows could be silently lost during the import.|
| Intellisense/editor | Reduced SMO-based query traffic to Azure SQL databases for intellisense. |
| Intellisense/editor | Fixed grammatical error in the tooltip displayed when typing T-SQL to create a user. Also, fixed the error message to disambiguate between users and logins. |
| Log Viewer | Fixed an issue were SSMS always opens the current server (or agent) log, even if double-clicking an older archive sign in the Object explorer. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37633648) for more details. |
| SSMS setup | Fixed the issue that was causing SSMS setup to fail when the setup log path contained spaces. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37496110) for more details. |
| SSMS setup | Fixed an issue where SSMS was exiting immediately after showing the splash screen. </br> See these sites for more details: [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37502512), [SSMS Refuses to Start](https://dba.stackexchange.com/questions/238609/ssms-refuses-to-start), and [Database Administrators](https://dba.stackexchange.com/questions/237086/sql-server-management-studio-18-wont-open-only-splash-screen-pops-up). |
| Object explorer | Lifted restriction on enabling *start PowerShell* when connected to SQL on Linux. |
| Object explorer | Fixed an issue that was causing SSMS to crash when trying to expand the Polybase/Scale-out Group node (when connected to a compute node). |
| Object explorer | Fixed an issue where the *Disabled* menu item was still enabled, even after disabling a given Index. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37735375) for more details. |
| Reports | Correcting report to actually display GrantedQueryMemory in KB (SQL Performance   Dashboard report). See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37167289) for more details. |
| Reports | Improved the tracing of the log block in Always-On scenarios. |
| ShowPlan | Added new showplan element *SpillOccurred* to showplan schema. |
| ShowPlan | Added remote reads (*ActualPageServerReads*, *ActualPageServerReadAheads* *ActualLobPageServerReads*, *ActualLobPageServerReadAheads*) to showplan schema. |
| SMO/scripting | Avoid querying edge constraints during scripting for non-graph tables. |
| SMO/scripting | Removed constraint on sensitivity classification when scripting columns with *Data classification*. |
| SMO/scripting | Fixed in issue where "Generate Script" on a graph table fails when   generating data. See [UserVoice](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898466) for more details. |
| SMO/scripting | Fixed an issue where the EnumObjects() method wasn't fetching   schema name for a Synonym. |
| SMO/scripting | Fixed an issue in UIConnectionInfo.LoadFromStream() where the *AdvancedOptions* section wasn't read (when a password wasn't specified). |
| SQL Agent | Fixed an issue that was causing SSMS to crash while working with a Job Properties window. See [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37164244) for more details. |
| SQL Agent | Fixed an issue where the "View" button on the *Job-Step Properties* wasn't always enabled, thus preventing viewing the output of a given job step. |
| XEvent UI | Added "Package" column to XEvents list to   disambiguate events with identical names. |
| XEvent UI | Added missing "EXTERNAL LIBRARY" class type mapping to XEventUI. |

### Known issues (18.1)

- Users may see an error when dragging a table object from the Object Explorer into the Query Editor. We are aware of the issue, and the fix is planned for the next release.

- The *Group connections* and *Single server connections* color options under the Options -> Text Editor -> Editor Tab and Status Bar -> Status Bar Layout and Colors do not persist after closing SSMS 18.1. After you reopen SSMS, the Status Bar Layout and Colors option reverts to default (white).

## ![download](../ssdt/media/download.png) [SSMS 18.0](https://go.microsoft.com/fwlink/?linkid=2088649)

- Release number: 18.0  
- Build number: 15.0.18118.0  
- Release date: April 24, 2019

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x40a)

### What's new in 18.0

| New item| Details|
| :-------| :------|
|Support for SQL Server 2019|SSMS 18.0 is the first release that is fully *aware* of SQL Server 2019 (compatLevel 150).|
|Support for SQL Server 2019|Support for "BATCH_STARTED_GROUP" and "BATCH_COMPLETED_GROUP" in SQL Server 2019 and SQL Managed Instance.|
|Support for SQL Server 2019|SMO: Added support for UDF Inlining.|
|Support for SQL Server 2019|GraphDB: Add flag in showplan for Graph TC Sequence.|
|Support for SQL Server 2019|Always Encrypted: added support for AEv2 / Enclave.|
|Support for SQL Server 2019|Always Encrypted: connection dialog has a new tab "Always Encrypted" when the user clicks on the "Options" button to enable/configure Enclave support.|
|Smaller SSMS download size| The current size is ~500 MB, approximately half of the SSMS 17.x bundle.
|SSMS is based on the Visual Studio 2017 Isolated Shell|The new shell (SSMS is based on Visual Studio 2017 15.9.11) unlocks all the accessibility fixes that went into both SSMS and Visual Studio, and includes the latest security fixes.|
|SSMS accessibility improvements| Much work went in to address accessibility issues in all the tools (SSMS, DTA, and Profiler)|
|SSMS can now be installed in a custom folder| This option is available from both the command line (useful for unattended installation) and the setup UI. From the command line, pass this extra argument to the SSMS-Setup-ENU.exe:   SSMSInstallRoot=C:\MySSMS18  By default, the new install location for SSMS is: %ProgramFiles(x86)%\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe.  This does not mean that SSMS is multi-instance.|
|SSMS allows installing in a language other than the OS language|The block on mixed languages setup has been lifted. You can, for example, install SSMS German on a French Windows. If the OS language does not match the SSMS language, the user needs to change the language under **Tools** > **Options** > **International Settings**, otherwise SSMS will show the English UI.|
|SSMS no longer shares components with the SQL Engine|Much effort went in to avoid sharing components with SQL Engine, which often resulted in serviceability issues (one clobbering the files installed by the other).|
|SSMS requires NetFx 4.7.2 or greater|We upgraded our minimum requirement from NetFx4.6.1 to NetFx4.7.2: this allows us to take advantage of the new functionality exposed by the new framework.|
|Ability to migrate SSMS settings| When SSMS 18 is started for the first time, the user will be prompted to migrate the 17.x settings. The user setting files are now stored as a plain XML file, thus improving portability and possibly allowing editing.|
|Support for High DPI| High DPI is now enabled by default.|
|SSMS ships with the Microsoft OLE DB driver| For details, see [Download Microsoft OLE DB Driver for SQL Server](https://docs.microsoft.com/sql/connect/oledb/download-oledb-driver-for-sql-server).|
|SSMS isn't supported on Windows 8. Windows 10 and Windows Server 2016 require version 1607 (10.0.14393) or later|Due to the new dependency on NetFx 4.7.2, SSMS 18.0 does not install on Windows 8 and older versions of Windows 10 and Windows Server 2016. SSMS setup will block on those systems. Windows 8.1 is still supported.|
|SSMS is no longer added to the PATH environment variable|Path to SSMS.EXE (and tools in general) isn't added to the path anymore. Users can either manually add it, or if on a modern Windows computer, use on the Start menu.|
|Package IDs are no longer needed to develop SSMS Extensions| In the past, SSMS was selectively loading only well-known packages, thus requiring developers to register their own package. This is no longer the case.|
|General SSMS|Exposing AUTOGROW_ALL_FILES config option for Filegroups in SSMS.|
|General SSMS|Removed risky 'lightweight pooling' and 'priority boost' options from SSMS GUI. For details, see [Priority boost details – and why it’s not recommended](https://blogs.msdn.microsoft.com/arvindsh/2010/01/26/priority-boost-details-and-why-its-not-recommended/).
|General SSMS|New menu and key bindings to creates files: **CTRL+ALT+N**. **CTRL+N** will continue to create a new query.|
|General SSMS|**New Firewall Rule** dialog now allows the user to specify a rule name, instead of automatically generating one on behalf of the user.|
|General SSMS|Improved intellisense in Editor especially for v140+ T-SQL.|
|General SSMS|Added support in SSMS UI for UTF-8 on collation dialog.|
|General SSMS|Switched to "Windows Credential Manager" for connection dialog MRU passwords. This addresses a long outstanding issue where persistence of passwords wasn't always reliable.|
|General SSMS|Improved support for multi-monitor systems by making sure that more and more dialogs and windows pop up on the expected monitor.|
|General SSMS|Exposed the 'backup checksum default' server configuration in the new Database Settings page of the Server Properties Dialog. For details, see [https://feedback.azure.com/forums/08035-sql-server/suggestions/34634974](https://feedback.azure.com/forums/08035-sql-server/suggestions/34634974).|
|General SSMS|Exposed "maximum size for error log files" under "Configure SQL Server Error Logs". For details, see  [https://feedback.azure.com/forums/908035/suggestions/33624115](https://feedback.azure.com/forums/908035/suggestions/33624115).|
|General SSMS|Added "Migrate to Azure" under Tools menu – We have integrated Database Migration Assistant and Azure Database Migration Service to provide quick and easy access to help accelerate your migrations to Azure.|
|General SSMS|Added logic to prompt the user to commit open transactions when "Change connection" is used.|
|Azure Data Studio integration|Added menu item to start/download Azure Data Studio.|
|Azure Data Studio integration|Added "Start Azure Data Studio" menu item to Object Explorer.|
|Azure Data Studio integration|When right-clicking on a database node in OE, the user is presented with context menus to either run a query or create a new notebook in Azure Data Studio.|
|Azure SQL support| SLO/Edition/MaxSize database properties now accept custom names, making it easier to support future editions of Azure SQL databases.|
|Azure SQL support| Added support for recently added vCore SKUs (General Purpose and Business Critical): Gen4_24 and all the Gen5.|
|Azure SQL Managed Instance|Added new "AAD logins" as a new login type in SMO and SSMS when connected to an Azure SQL Managed Instance.|
|Always On|Rehash RTO (estimated recovery time)  and RPO (estimated data loss) in SSMS Always on Dashboard. See the updated documentation at [https://docs.microsoft.com/sql/database-engine/availability-groups/windows/monitor-performance-for-always-on-availability-groups](../database-engine/availability-groups/windows/monitor-performance-for-always-on-availability-groups.md).|
|Always Encrypted| The Enable Always Encrypted checkbox in the new Always Encrypted tab in the Connect to Server dialog now provides an easy way to enable/disable Always Encrypted for a database connection.|
|Always Encrypted with secure enclaves| Several enhancements have been made to support  Always Encrypted with secure enclaves in SQL Server 2019 preview:  A text field for specifying enclave attestation URL in the Connect to Server dialog (the new Always Encrypted tab).  The new checkbox in the New Column Master Key dialog to control whether a new column master key allows enclave computations.  Other Always Encrypted key management dialogs now expose the information on which column master keys allow enclave computations.|
|Audit Files|Changed authentication method from Storage Account Key based to Azure AD-based authentication.|
|Audit Files|Updated list of known audit actions to include FEATURE RESTRICTION ADD/CHANGE GROUP/DROP.|
|Data Classification| Reorganized data classification task menu: added sub menu to the database tasks menu and added an option to open the report from the menu without opening the classify data window first.|
|Data Classification|Added new feature 'Data classification' to SMO. Column object exposes new properties: SensitivityLabelName, SensitivityLabelId, SensitivityInformationTypeName, SensitivityInformationTypeId, and IsClassified (read-only). For more information, see [ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/add-sensitivity-classification-transact-sql)|
|Data Classification|Added new "Classification Report" menu item to the "Data Classification" flyout.|
|Data Classification| Updated recommendations.|
|Database Compatibility Level Upgrade|Added a new option under ***Database name*** > ***Tasks*** > ***Database Upgrade***. This starts the new **Query Tuning Assistant (QTA)** to guide the user through the process of: Collecting a performance baseline before upgrading the database compatibility level. Upgrading to the desired database compatibility level.  Collecting a second pass of performance data over the same workload. Detect workload regressions, and provide tested recommendations to improve workload performance.  This is close to the database upgrade process documented in [query store usage scenarios](https://docs.microsoft.com/sql/relational-databases/performance/query-store-usage-scenarios#CEUpgrade), except for the last step where QTA does not rely on a previously known good state to generate recommendations.|
|Data-tier Application Wizard|Added support to import/export data tier application with graph tables.|
|Flat File Import Wizard|Added logic to notify the user that an import may have resulted in a renaming of the columns.|
|Integration Services (SSIS)|Added support to allow customers to schedule SSIS packages on Azure-SSIS IRs that are in Azure Government cloud.|
|Integration Services (SSIS)|When you use SQL Agent of Azure SQL Managed Instance via SSMS, you can configure parameter and connection manager in SSIS agent job step.|
|Integration Services (SSIS)|When connecting to Azure SQL DB/Managed Instance, you can connect to it with *default* as initial db.|
|Integration Services (SSIS)|Added a new entry item **Try SSIS in Azure Data Factory** under "Integration Services Catalogs" node, which can be used to launch the "Integration Runtime Creation Wizard" and create "Azure-SSIS Integration Runtime" quickly.
|Integration Services (SSIS)|Added **Create SSIS IR** button in "Catalog Creation Wizard", which can be used to launch the "Integration Runtime Creation Wizard" and create "Azure-SSIS Integration Runtime" quickly.|
|Integration Services (SSIS)|ISDeploymentWizard now supports SQL Auth, Azure Active Directory Integrated Auth, and Azure Active Directory Password Auth in command-line mode.|
|Integration Services (SSIS)|Deployment Wizard now supports creating and deploying to Azure Data Factory SSIS Integration Runtime.|
|Object Scripting|Add new menu items for "CREATE OR ALTER" when scripting objects.|
|Query Store|Improved usability of some reports (Overall Resource Consumptions) by adding thousands separator to numbers displayed on the Y-axis of the charts.|
|Query Store|Added a new Query Wait Statistics report.|
|Query Store|Added "Execution Count" metric to "Tracked Query" View.|
|Replication Tools|Added support for non-default port specification feature in Replication Monitor and SSMS.|
|ShowPlan|Added actual time elapsed, actual vs estimated rows under ShowPlan operator node if they are available. This will make actual plan look consistent with Live Query Stats plan.|
|ShowPlan|Modified tooltip and added comment when clicking on Edit Query Button for a ShowPlan, to indicate to user that the ShowPlan might be truncated by the SQL engine if the query is over 4000 characters.|
|ShowPlan|Added logic to display the "Materializer Operator (External Select)".|
|ShowPlan|Add new showplan attribute BatchModeOnRowStoreUsed to easily identify queries that are using the " batch-mode scan on rowstores" feature. Anytime a query performs batch-mode scan on rowstores, a new attribute (BatchModeOnRowStoreUsed="true") gets added to StmtSimple element.|
|ShowPlan|Added Showplan Support to LocalCube RelOp for DW ROLLUP and CUBE.|
|ShowPlan|New LocalCube operator for the new ROLLUP and CUBE aggregation feature in Azure SQL Data Warehouse.|
|SMO| Extend SMO Support for Resumable Index Creation.|
|SMO| Added new event on SMO objects ("PropertyMissing") to help application authors to detect SMO performance issues sooner.|
|SMO| Exposed new DefaultBackupChecksum property on the Configuration object which maps to the "backup checksum default" server configuration.|
|SMO| Exposed new ProductUpdateLevel property on the Server object, which maps to the servicing level for the version of SQL in use (for example, CU12, RTM).|
|SMO| Exposed new LastGoodCheckDbTime property on  Database object, which maps to "lastgoodcheckdbtime" database property. If such property isn't available, a default value of 1/1/1900 12:00:00 AM will be returned.|
|SMO|Moved location for RegSrvr.xml file (Registered Server configuration file) to "%AppData%\Microsoft\SQL Server Management Studio" (unversioned, so it can be shared across versions of SSMS).|
|SMO|Added "Cloud Witness" as a new quorum type and as a new resource type.|
|SMO|Added support for "Edge Constraints" in both SMO and SSMS.|
|SMO|Added cascade delete support to "Edge Constraints" in both SMO and SSMS.|
|SMO|Added support for data classification "read-write" permissions.|
|Vulnerability Assessment| Enabled Vulnerability Assessment tasks menu on Azure SQL DW.|
|Vulnerability Assessment|Change the set of vulnerability assessment rules that are run on Azure SQL Managed Instance servers, so that "Vulnerability Assessment" scan results will be consistent with the ones in Azure SQL DB.|
|Vulnerability Assessment| "Vulnerability Assessment" now supports Azure SQL DW.|
|Vulnerability Assessment|Added a new exporting feature to export the vulnerability assessment scan results to Excel.|
|XEvent Viewer|XEvent Viewer: enabled showplan window for more XEvents.|

### Bug fixes in 18.0

| New item| Details|
| :-------| :------|
|Crashes and freezes|Fixed a source of common SSMS crashes related to GDI objects.|
|Crashes and freezes|Fixed a common source of hangs and poor performance when selecting "Script as Create/Update/Drop" (removed unnecessary fetches of SMO objects).|
|Crashes and freezes|Fixed a hang when connecting to an Azure SQL DB using MFA while ADAL traces are enabled.|
|Crashes and freezes|Fixed a hang (or perceived hang) in Live Query Statistics when invoked from Activity Monitor (the issue manifested when using SQL Server authentication with no "Persist Security Info" set).|
|Crashes and freezes|Fixed a hang when selecting "Reports" in Object Explorer which could manifest on high latency connections or temporary non-accessibility of the resources.|
|Crashes and freezes|Fixed a crash in SSSM when trying to use Central Management Server and Azure SQL servers. For details, see [SMSS 17.5 application error and crash when using Central Management Server](https://feedback.azure.com/forums/908035/suggestions/33374884).|
|Crashes and freezes|Fixed a hang in Object Explorer by optimizing the way IsFullTextEnabled  property is retrieved.|
|Crashes and freezes|Fixed a hang in "Copy Database Wizard" by avoiding to build unnecessary queries to retrieve Database properties.|
|Crashes and freezes|Fixed an issue that was causing SSMS to hang/crash while editing T-SQL.|
|Crashes and freezes|Mitigated an issue where SSMS was becoming unresponsive when editing large T-SQL scripts.|
|Crashes and freezes|Fixed an issue that was causing SSMS to run out of memory when handling the big datasets returned by queries.|
|General SSMS|Fixed an issue there the "ApplicationIntent" wasn't passed along in connections in "Registered Servers".|
|General SSMS|Fixed in issue where the "New XEvent Session Wizard UI" form wasn't rendered properly on High DPI monitors.|
|General SSMS|Fixed an issue where trying to import a bacpac file.|
|General SSMS|Fixed an issue where trying to display the properties of a database (with FILEGROWTH > 2048GB) was throwing an arithmetic overflow error.|
|General SSMS|Fixed an issue where the Perf Dashboard Report was reporting PAGELATCH and PAGEIOLATCH waits that could not found in subreports.|
|General SSMS|Another round of fixes to make SSMS more multi-monitor aware by having it open dialog in the correct monitor.|
|Analysis Services (AS)|Fixed an issue where the "Advanced Settings" to the AS XEvent UI was clipped.|
|Analysis Services (AS)|Fixed an issue where DAX parsing throws file not found exception.|
|Azure SQL Database|Fixed an issue where the database list wasn't populated correctly for Azure SQL Database query window when connected to a user database in Azure SQL DB instead of to master.|
|Azure SQL Database|Fixed an issue where it wasn't possible to add a "Temporal Table" to an Azure SQL database.|
|Azure SQL Database|Enabled the Statistics properties sub menu option under menu Statistics in Azure, since it has been fully supported for quite some time now.|
|Azure SQL - General Support|Fixed issues in common Azure UI control that was preventing the user from displaying Azure subscriptions (if there were more than 50). Also, the sorting has been changed to be by name rather by Subscription ID. The user could run into this one when trying to restore a backup from URL, for example.|
|Azure SQL - General Support|Fixed an issue in common Azure UI control when enumerating subscriptions which could yield a "Index was out of range. Must be non-negative and less than the size of the collection." error when the user had no subscriptions in some tenants. The user could run into this one when trying to restore a backup from URL, for example.|
|Azure SQL - General Support|Fixed issue where Service Level Objectives were hardcoded, thus making it harder for SSMS to support newer Azure SQL SLOs. Now, the user can sign in to Azure and allow SSMS to retrieve all the applicable SLO data (Edition and Max Size)|
|Azure SQL DB Managed Instance support|Improved/polished the support for Managed Instances: disabled unsupported options in UI and a fix to the View Audit Logs option to handle URL audit target.|
|Azure SQL DB Managed Instance support|"Generate and Publish scripts" wizard scripts unsupported CREATE DATABASE clauses.|
|Azure SQL DB Managed Instance support|Enable Live Query Statistics for Managed Instances.|
|Azure SQL DB Managed Instance support|Database properties->Files was incorrectly scripting ALTER DB ADD FILE.|
|Azure SQL DB Managed Instance support|Fixed regression with SQL Agent scheduler where ONIDLE scheduling was chosen even when some other scheduling type was chosen.|
|Azure SQL DB Managed Instance support|Adjusting MAXTRANSFERRATE, MAXBLOCKSIZE for doing backups on Azure Storage.|
|Azure SQL DB Managed Instance support|The issue where tail log backup is scripted before RESTORE operation (this isn't supported on CL).|
|Azure SQL DB Managed Instance support|Create database wizard not scripting correctly CREATE DATABASE statement.|
|Azure SQL DB Managed Instance support|Special handling of SSIS packages within SSMS when connected to Managed Instances.|
|Azure SQL DB Managed Instance support|Fixed an issue where an error was displayed while trying to use "Activity Monitor" when connected to Managed Instances.|
|Azure SQL DB Managed Instance support|Improved support for AAD Logins (in SSMS Explorer).|
|Azure SQL DB Managed Instance support|Improved scripting of SMO Filegroups objects.|
|Azure SQL DB Managed Instance support|Improved UI for credentials.|
|Azure SQL DB Managed Instance support|Added support for Logical Replication.|
|Azure SQL DB Managed Instance support|Fixed an issue which was causing right-clicking on a database and choosing 'Import data-tier application' to fail.|
|Azure SQL DB Managed Instance support|Fixed an issue which was causing right-clicking on a "TempDB" to show errors.|
|Azure SQL DB Managed Instance support|Fixed an issue where trying to scripting ALTER DB ADD FILE statement in SMO was causing the generated T-SQL script to be empty.|
|Azure SQL DB Managed Instance support|Improved display of Managed Instances server-specific properties (hardware generation, service tier, storage used and reserved).|
|Azure SQL DB Managed Instance support|Fixed an issue where scripting of a database ("Script as Create...") wasn't scripting extra filegroups and files. For details, see [https://feedback.azure.com/forums/908035/suggestions/37326799](https://feedback.azure.com/forums/908035/suggestions/37326799). |
|Backup/Restore/Attach/Detach DB|Fixed an issue where the user was unable to attach a database when physical filename of .mdf file does not match the original filename.|
|Backup/Restore/Attach/Detach DB|Fixed an issue where SSMS might not find a valid restore plan or might find one which is sub-optimal. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/32897752](https://feedback.azure.com/forums/908035-sql-server/suggestions/32897752). |
|Backup/Restore/Attach/Detach DB|Fixed issue where the "Attach Database" wizard wasn't displaying secondary files that were renamed. Now, the file is displayed and a comment about it is added (e.g. "Not Found"). For details, see [https://feedback.azure.com/forums/908035/suggestions/32897434](https://feedback.azure.com/forums/908035/suggestions/32897434). |
|Copy Database Wizard|Generate scripts/Transfer/Copy Database Wizard try to create a table with an in memory table doesn't force ansi_padding on.|
|Copy Database Wizard|Transfer Database task/Copy Database Wizard broken on SQL Server 2017 and SQL Server 2019.|
|Copy Database Wizard|Generate scripts/Transfer/Copy Database Wizard script table creation before creation of associated external data source.|
|Connection dialog|Enabled the removal of usernames from previous username list by pressing the DEL key. For details, see [Allow deletion of users from SSMS login window](https://feedback.azure.com/forums/908035/suggestions/32897632).|
|DAC Import Wizard|Fixed an issue DAC Import Wizard wasn't working when connected using AAD.|
|Data Classification|Fixed an issue when saving classifications in the data classification pane while there are another data classification panes open on other databases.|
|Data-tier Application Wizard|Fixed an issue where the user wasn't able to import a Data-tier Application (.dacpac) due to limited access to the server (e.g. no access to all the databases on the same server).|
|Data-tier Application Wizard|Fixed an issue which was causing the import to be extremely slow when many databases happened to be hosted on the same Azure SQL server.|
|External Tables|Added support for Rejected_Row_Location in template, SMO, intellisense, and property grid.|
|Flat File Import Wizard|Fixed an issue where the "Import Flat File Wizard" wasn't handling double quotes correctly (escaping). For details, see [https://feedback.azure.com/forums/908035/suggestions/32897998](https://feedback.azure.com/forums/908035/suggestions/32897998). |
|Flat File Import Wizard|Fixed an issue where related to incorrect handling of floating-point types (on locales that use a different delimiter for floating points).|
|Flat File Import Wizard|Fixed an issue related to importing of bits when values are 0 or 1. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898535](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898535). |
|Flat File Import Wizard|Fixed an issue where floats were entered as nulls.|
|Flat File Import Wizard|Fixed an issue where the import wizard wasn't able to process negative decimal values.|
|Flat File Import Wizard|Fixed an issue where the wizard wasn't able to import from single column CSV files.|
|Flat File Import Wizard|will be in SSMS 17.9] Fixed issue where Flat File Import does not allow changing destination table when table is already existing. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186](https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186). |
|Help Viewer|Improved logic around honoring the online/offline modes (there may still be a few issues that need to be addressed).|
|Help Viewer|Fixed the "View Help" to honor the online/offline settings. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/32897791](https://feedback.azure.com/forums/908035-sql-server/suggestions/32897791). |
|High Availability Disaster Recovery (HADR)<BR> Availability Groups (AG)|Fixed an issue where roles in "Fail Over Availability Groups" wizard was always displayed as "Resolving".|
|High Availability Disaster Recovery (HADR)<BR> Availability Groups (AG)|Fixed an issue where SSMS was showing truncated warnings in "AG Dashboard".|
|Integration Services (IS)|Fixed a SxS issue that deployment wizard will fail to connect to sql server when SQL Server 2019 and SSMS 18.0 are installed on the same machine.|
|Integration Services (IS)|Fixed an issue that maintenance plan task can’t be edited when designing the maintenance plan.|
|Integration Services (IS)|Fixed an issue that deployment wizard will stuck if the project under deployment is renamed.|
|Integration Services (IS)|Enabled environment setting in Azure-SSIS IR schedule feature.|
|Integration Services (IS)|Fixed an issue that SSIS Integration Runtime Creation Wizard stops responding when the customer account belongs to more than 1 tenant.|
|Job Activity Monitor|Fixed crash while using Job Activity Monitor (with filters).|
|Object Explorer|Fixed an issue where SSMS was throwing an "Object cannot be cast from DBNull to other types" exception when trying to expand "Management" node in OE (misconfigured DataCollector).|
|Object Explorer|Fixed an issue where OE wasn't escaping quotes before invoking the "Edit Top N..." causing the designer to get confused.|
|Object Explorer|Fixed an issue where the "Import Data-Tier application" wizard was failing to launch from the Azure Storage tree.|
|Object Explorer|Fixed an issue in "Database Mail Configuration" where the status of the SSL checkbox wasn't persisted. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/32895541](https://feedback.azure.com/forums/908035-sql-server/suggestions/32895541). |
|Object Explorer|Fixed an issue where SSMS grayed out option to close existing connections when trying to restore database with is_auto_update_stats_async_on.|
|Object Explorer|Fixed an issue where right-clicking on nodes in OE the (e.g. "Tables" and wanting to perform an action such as filtering tables by going to Filter > Filter Settings, the filter settings form can appear on the other screen than where SSMS is currently active). For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/34284106](https://feedback.azure.com/forums/908035-sql-server/suggestions/34284106). |
|Object Explorer|Fixed a long outstanding issue where the DELETE key wasn't working in OE while trying to rename an object. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/33073510](https://feedback.azure.com/forums/908035-sql-server/suggestions/33073510), [https://feedback.azure.com/forums/908035/suggestions/32910247](https://feedback.azure.com/forums/908035/suggestions/32910247) and other duplicates.|
|Object Explorer|When displaying the properties of existing database files, the size appears under a column "Size (MB)" instead of "Initial Size (MB)" which is what is displayed when creating a new database. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/32629024](https://feedback.azure.com/forums/908035-sql-server/suggestions/32629024). |
|Object Explorer|Disabled the "Design" context-menu item on "Graph Tables" since there is no support for those kind of tables in the current version of SSMS.|
|Object Explorer|Fixed an issue where the "New Job Schedule" dialog wasn't rendering properly on High DPI monitors. For details, see [https://feedback.azure.com/admin/v3/suggestions/35541262](https://feedback.azure.com/admin/v3/suggestions/35541262). |
|Object Explorer|Fixed/improved the way an issue where a database size ("Size (MB)") is displayed in Object Explorer details: only 2 decimal digits and formatted using the thousands separator. For details, see [https://feedback.azure.com/forums/908035/suggestions/34379308](https://feedback.azure.com/forums/908035/suggestions/34379308).|
|Object Explorer|Fixed an issue that was causing the creation of a "Spatial Index" to fail with an error like "To accomplish this action, set property PartitionScheme".|
|Object Explorer|Minor performance improvements in Object Explorer to avoid issuing extra queries, when possible.|
|Object Explorer|Extended logic to request confirmation when renaming a database to all the schema objects (the setting can be configured).|
|Object Explorer|Added proper escaping in Object Explorer filtering. For details, see [https://feedback.azure.com/forums/908035/suggestions/36678803](https://feedback.azure.com/forums/908035/suggestions/36678803). |
|Object Explorer|Fixed/improved the view in Object Explorer Details to show numbers with proper separators. For details, see [https://feedback.azure.com/forums/908035/suggestions/32900944](https://feedback.azure.com/forums/908035/suggestions/32900944). |
|Object Explorer|Fixed context menu on "Tables" node when connected to SQL Express, where the "New" fly-out was missing, Graph tables were incorrectly listed, and System-Versioned table was missing. For details, see [https://feedback.azure.com/forums/908035/suggestions/37245529](https://feedback.azure.com/forums/908035/suggestions/37245529). |
|Object Scripting|Overall perf improvements - Generate Scripts of WideWorldImporters takes half the time compared to SSMS 17.7.|
|Object Scripting|When scripting objects, DB Scoped configuration which has default values are omitted.|
|Object Scripting|Don't generate dynamic T-SQL when scripting. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898391](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898391). |
|Object Scripting|Omit the graph syntax "as edge" and "as node" when scripting a table on SQL Server 2016 and earlier.|
|Object Scripting|Fixed an issue where scripting of database objects was failing when connecting to an Azure SQL DB using AAD with MFA.|
|Object Scripting|Fixed an issue where trying to script a spatial index with GEOMETRY_AUTO_GRID/GEOGRAPHY_AUTO_GRID on an Azure SQL DB was throwing an error.|
|Object Scripting|Fixed an issue which was causing the database scripting (of an Azure SQL database) to always target an on-prem SQL, even if the "Object Explorer" scripting settings were set to match the source.|
|Object Scripting|Fixed an issue where trying to script a table in a SQL DW database involving clustered and non-clustered indexes was generating incorrect T-SQL statements.|
|Object Scripting|Fixed an issue where trying to script a table in a SQL DW database with both "Clustered Columnstore Indexes" and "Clustered Indexes" was generating incorrect T-SQL (duplicate statements).|
|Object Scripting|Fixed Partitioned table scripting with no range values (SQL DW databases).|
|Object Scripting|Fixed an issue where the user would be unable to script an audit/audit specification SERVER_PERMISSION_CHANGE_GROUP.|
|Object Scripting|Fix and issue where the user is unable to script statistics from SQL DW. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/32897296](https://feedback.azure.com/forums/908035-sql-server/suggestions/32897296). |
|Object Scripting|Fixed an issue where the "Generate script wizard" shows incorrect table having scripting error when "Continue scripting on Error" is set to false.|
|Object Scripting|Improved script generation on SQL Server 2019.|
|Profiler|Added "Aggregate Table Rewrite Query" event to Profiler events.|
|Query Data Store|Fixed an issue where a "DocumentFrame (SQLEditors)" exception could be thrown.|
|Query Data Store|Fixed an issue when trying to set a custom time interval in the build-in Query Store reports the user wasn't able to select AM or PM on the start/end interval.|
|Results Grid|Fixed an issue that was causing the in High Contrast mode (selected line numbers not visible).|
|Results Grid|Fixed an issue which resulted in an "Index out of range" exception when clicking on the grid.|
|Results Grid|Fixed an issue where the grid result background color was being ignored. For details, see [https://feedback.azure.com/forums/908035/suggestions/32895916](https://feedback.azure.com/forums/908035/suggestions/32895916). |
|ShowPlan|New memory grant operator properties display incorrectly when there is more than one thread.|
|ShowPlan|Add the following 4 attributes in RunTimeCountersPerThread of actual execution xml plan: HpcRowCount (Number of rows processed by hpc device), HpcKernelElapsedUs (elapsed time wait for kernel execution in use), HpcHostToDeviceBytes (bytes transferred from host to device), and HpcDeviceToHostBytes (bytes transferred from device to host).|
|ShowPlan|Fixed an issue where the similar plan nodes are highlighted in the wrong position.|
|SMO|Fixed an issue where SMO/ServerConnection did not SqlCredential-based connections correctly. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/33698941](https://feedback.azure.com/forums/908035-sql-server/suggestions/33698941). |
|SMO|Fixed an issue where an application written using SMO would encounter an error if it tried to enumerate databases from the same server on multiple threads even though it uses separate SqlConnection instances on each thread.|
|SMO|Fixed performance regression in Transfer from External Tables.|
|SMO|Fixed issue in ServerConnection thread-safety which was causing SMO to leak SqlConnection instances when targeting Azure.|
|SMO|Fixed an issue which was causing a StringBuilder.FormatError when trying to restore a database which had curly braces in its name.|
|SMO|Fixed an issue where Azure databases in SMO were defaulting to Case-Insensitive collation for all string comparisons instead of using the specified collation for the database.|
|SSMS Editor|Fixed an issue where "SQL System Table" where restoring the default colors was chancing the color to lime green, rather than the default green, making it very hard to read on a white background. For details, see [Restoring wrong default color for SQL System Table](https://feedback.azure.com/forums/908035-sql-server/suggestions/32896906). The issue still persists on non-English versions of SSMS.|
|SSMS Editor|Fixed issue where intellisense wasn't working when connected to Azure SQLDW using AAD authentication.|
|SSMS Editor|Fixed intellisense in Azure when user lacks access to **master** database.|
|SSMS Editor|Fixed code snippets to create "temporal tables" which were broken when the collation of the target database was case-sensitive.|
|SSMS Editor|New TRANSLATE function now recognized by intellisense. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898430](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898430). |
|SSMS Editor|Improved intellisense on FORMAT built-in function. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898676](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898676). |
|SSMS Editor|LAG and LEAD are now recognized as built-in functions. For details, see [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898757](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898757). |
|SSMS Editor|Fixed an issue where intellisense was giving a warning when using "ALTER TABLE...ADD CONSTRAINT...WITH(ONLINE=ON)".|
|SSMS Editor|Fixed an issue where several system views and table values functions were not properly colorized.|
|SSMS Editor|Fixed an issue where clicking on editor tabs could cause the tab to be closed instead of getting the focus. For details, see [https://feedback.azure.com/forums/908035/suggestions/37291114](https://feedback.azure.com/forums/908035/suggestions/37291114). |
|SSMS Options|Fixed an issue where **Tools** > **Options** > **SQL Server Object Explorer** > **Commands** page wasn't resizing properly.|
|SSMS Options|SSMS will now by default disable automatic download of DTD in XMLA editor -- XMLA script editor (which uses the xml language service) will by default now prevent automatically downloading the DTD for potentially malicious xmla files. This is controlled by turning off the “Automatically download DTDs and Schemas” setting in **Tools** > **Options** > **Environment** > **Text Editor** > **XML** > **Miscellaneous**.|
|SSMS Options|Restored **CTRL+D** to be the shortcut as it used to be in older version of SSMS. For details, see [https://feedback.azure.com/forums/908035/suggestions/35544754](https://feedback.azure.com/forums/908035/suggestions/35544754). |
|Table Designer|Fixed a crash in "Edit 200 rows".|
|Table Designer|Fixed an issue where the designer was allowing to add a table when connected to an Azure SQL database.|
|Vulnerability Assessment|Fixed an issue where the scan results are not being loaded properly.|
|XEvent|Added two columns "action_name" and "class_type_desc" that show action ID and class type fields as readable strings.|
|XEvent|Removed the event XEvent Viewer cap of 1,000,000 events.|
|XEvent Profiler|Fixed an issue where XEvent Profiler failed to launch when connected to a 96-core SQL Server.|
|XEvent Viewer|Fixed an issue where XEvent Viewer was crashing when trying to group the events using the "Extended Event Toolbar Options".|

### Deprecated and removed features in 18.0

Deprecated / Removed Features
- T-SQL Debugger
- Database Diagrams
- The following tools are no longer installed with SSMS:
  - OSQL.EXE
  - DReplay.exe
  - SQLdiag.exe
  - SSBDiagnose.exe
  - bcp.exe
  - sqlcmd.exe
- Configuration Manager tools:
  - Both SQL Server  Configuration Manager and Reporting Server Configuration Manager are not part of SSMS setup anymore.
- DMF Standard Policies
  - The policies are not installed with SSMS anymore. They will be moved to Git. Users will be able to contribute and download/install them, if they want to.
- SSMS command-line option -P removed
  - Due to security concerns, the option to specify clear-text passwords on the command line was removed.
- Generate Scripts > Publish to Web Service removed
  - This deprecated feature was removed from the SSMS UI.
- Removed node "Maintenance > Legacy" in Object Explorer.
  - The really old "Database Maintenance Plan" and "SQL Mail" nodes won't be accessible anymore. The modern "Database Mail" and "Maintenance Plans" nodes will continue to work as usual.

### Known issues (18.0)

- You might encounter an issue installing version 18.0, where you cannot run SQL Server Management Studio. If you encounter this issue, please follow the steps from the [SSMS2018 - Installed, but will not run](https://feedback.azure.com/forums/908035-sql-server/suggestions/37502512-ssms2018-installed-but-will-not-run) article.

## ![download](../ssdt/media/download.png) [SSMS 17.9.1](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409)

- Release number: 17.9.1<br>
- Build number: 14.0.17289.0<br>
- Release date: November 21, 2018

17.9.1 is a small update to 17.9 with the following bug fixes:

- Fixed an issue where users may experience their connection being closed and reopened with each query invocation when using "Active Directory - Universal with MFA Support" authentication with the SQL query editor. Side effects of the connection closing included global temporary tables being dropped unexpectedly, and sometimes a new SPID given to the connection.
- Fixed a long outstanding issue where restore plan would fail to find a restore plan, or would generate an inefficient restore plan under certain conditions.
- Fixed an issue in the "Import Data-tier Application" wizard which could result in an error when connected to an Azure SQL database.

> [!NOTE]
> Non-English localized releases of SSMS 17.x require the [KB 2862966 security update package](https://support.microsoft.com/kb/2862966) if installing on: Windows 8, Windows 7, Windows Server 2012, and Windows Server 2008 R2.

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40a)

## ![download](../ssdt/media/download.png) [SSMS 17.9](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x409)

Build number: 14.0.17285.0<br>
Release date: September 04, 2018

> [!NOTE]
> Non-English localized releases of SSMS 17.x require the [KB 2862966 security update package](https://support.microsoft.com/kb/2862966) if installing on: Windows 8, Windows 7, Windows Server 2012, and Windows Server 2008 R2.

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x40a)

### What's new

**General SSMS**

ShowPlan:

- Graphical Showplan now shows the new row mode memory grant feedback attributes when the feature is activated for a specific plan: IsMemoryGrantFeedbackAdjusted and LastRequestedMemory added to the MemoryGrantInfo query plan XML element. For more on row mode memory grant feedback, For details, see [Adaptive query processing in SQL databases](https://docs.microsoft.com/sql/relational-databases/performance/adaptive-query-processing).

Azure SQL:

- Added support for vCore SKUs in Azure DB creation. For more information, For details, see [vCore-based purchasing model](https://docs.microsoft.com/azure/sql-database/sql-database-service-tiers#vcore-based-purchasing-model).
 

### Bug fixes

**General SSMS**

Replication Monitor:

- Fixed an issue that was causing Replication Monitor (SqlMonitor.exe) not to start (User Voice item: https://feedback.azure.com/forums/908035-sql-server/suggestions/34791079).

Import Flat File Wizard:

- Fixed the link to the help page for "Flat File Wizard" dialog 
- Fixed issue where the wizard did not allow changing the destination table when the table already existed: this allows users to retry without having to exit the wizard, delete the failed table, and then reenter the information into the wizard (User Voice item: https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186).

Import/Export Data-Tier Application:

- Fixed an issue (in DacFx) which was causing the import of a .bacpac could fail with a message like "Error SQL72014: .Net SqlClient Data Provider: Msg 9108, Level 16, State 10, Line 1 This type of statistics isn't supported to be incremental. " when dealing with tables with partitions defined and no indexes on the table.

Intellisense:

- Fixed an issue where intellisense completion wasn't working when using AAD with MFA.

Object Explorer:

- Fixed an issue where the "Filter Dialog" was displayed on random monitors instead of the monitor where SSMS was running (multi-monitor systems).

Azure SQL:

- Fixed an issue related to enumeration of databases in the "Available Databases" where "master" wasn't displayed in the dropdown when connected to a specific database.
- Fixed an issue where trying to generate a script ("Data" or "Schema and Data") was failing then connected to the Azure SQL Database using AAD with MFA.
- Fixed an issue in the View Designer (Views) where it wasn't possible to select "Add Tables" from the UI when connected to a Azure SQL Database.
- Fixed an issue where SSMS Query Editor was silently closing and reopening connections during MFA token renewal. This prevents side effects unbeknownst to the user (like closing a transaction and never reopening again) from happening. The change adds the token expiration time to the properties window. 
- Fixed an issue where SSMS wasn't enforcing password prompts for imported MSA accounts for AAD with MFA login. 

Activity Monitor:

- Fixed an issue that was causing "Live Query Statistics" to hang when launched from Activity Monitor and SQL Authentication was used. 

Microsoft Azure integration: 

- Fixed an issue where SSMS only shows the first 50 subscriptions (Always Encrypted dialogs, Backup/Restore from URL dialogs, and other dialogs).
- Fixed an issue where SSMS was throwing an exception ("Index out of range") while trying to sign in to a Microsoft Azure account that did not have any storage account (in Restore Backup from URL dialog). 

Object Scripting:

- When scripting "Drop and Create", SSMS now avoids generating dynamic T-SQL.
- When scripting a database object, SSMS now does not generate script to set database scoped configurations, if they are set to default values.

Help:

- Fixed a long outstanding issue where "Help on Help" wasn't honoring the online/offline mode.
- When clicking on "Help| Community Projects and Samples" SSMS now opens the default browser that points to a Git page and shows no errors/warnings due to old browser being used.

### Known issues

> [!IMPORTANT]
> When using *Active Directory - Universal with MFA Support* authentication with the SQL query editor, users may experience their connection being closed and reopened with each query invocation. Side effects of such closure include global temporary tables being dropped unexpectedly and sometimes a new SPID being given to the connection. This closure will not occur if there is an open transaction on the connection. To work around this issue, users can set `persist security info=true` in the connection parameters.

## ![download](../ssdt/media/download.png) [SSMS 17.8.1](https://go.microsoft.com/fwlink/?linkid=875802)
*A bug was discovered in 17.8 related to provisioning SQL databases, so SSMS 17.8.1 replaces 17.8.*

Build number: 14.0.17277.0<br>
Release date: June 26, 2018

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x40a)

### What's new

**General SSMS**

Database Properties:

- This improvement exposes the **AUTOGROW_ALL_FILES** configuration option for Filegroups. This new config option is added under the Database Properties > Filegroups window in the form of a new column (Autogrow All Files) of checkboxes for each available Filegroup (except for Filestream and Memory Optimized Filegroups). The user can enable/disable AUTOGROW_ALL_FILES for a particular Filegroup by toggling the corresponding Autogrow_All_Files checkbox. Correspondingly, the **AUTOGROW_ALL_FILES** option is properly scripted when scripting the database for CREATE / generating scripts for the database (SQL2016 and above).

SQL Editor:

- Improved experience with Intellisense in Azure SQL Database when the user doesn't have master access.

Scripting:

- General performance improvements, especially over high-latency connections.

**Analysis Services (AS)**

- Analysis Services client libraries and data providers updated to the latest version, which added support for the new Azure Government AAD authority (login.microsoftonline.us).

### Bug fixes

**General SSMS**

Maintenance Plans:

- Fixed an issue when editing maintenance plans with Sql Authentication where "Notify Operator Task" was failing when using SQL authentication.
	
Scripting:

- Fixed an issue where PostProcess actions in SMO lead to resource exhaustion and SQL login failures
	
SMO:

- Fixed an issue where Table.Alter() fails if adding a column with a default constraint and the table already has data. For details, see [sql server smo generating inline default constraint when adding a column to a table containing data](https://feedback.azure.com/forums/908035-sql-server/suggestions/32895625).
	
Always Encrypted:

- Fixed an issue (in DacFx) which was causing a lock timeout error when enabling Always Encrypted on a partitioned table
	

**Analysis Services (AS)**

- Fixed an issue that occurred when modifying an OAuth datasource in a Tabular Analysis Services 1400-level compatibility model, which caused the changes in the OAuth tokens to not get updated in the data source.
- Fixed a crash in SSMS that may have occurred when using some invalid data source credentials or editing data sources that didn't support Change Data Source migration in Power Query (for example, Oracle) in Analysis Services Tabular 1400-level compatibility models.


### Known issues

- Clicking the *Script* button after modifying any filegroup property in the *Properties* window, generates two scripts - one script with a *USE <database>* statement, and a second script with a *USE master* statement.  The script with *USE master* is generated in error and should be discarded. Run the script that contains the *USE <database>* statement.
- Some dialogs display an invalid edition error when working with new *General Purpose* or *Business Critical* Azure SQL Database editions.
- Some latency in XEvents viewer may be observed. This is a [known issue in the .Net Framework](https://github.com/Microsoft/dotnet/blob/master/releases/net472/dotnet472-changes.md#sql). Consider upgrading to NetFx 4.7.2.




## ![download](../ssdt/media/download.png) [SSMS 17.7](https://go.microsoft.com/fwlink/?linkid=873126)

Build number: 14.0.17254.0<br>
Release date: May 09, 2018

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x40a)


### What's new

**General SSMS**

Replication Monitor:   
- Replication monitor now supports registering a listener for scenarios where publisher database and/or distributor database is part of Availability Group. You can now monitor replication environments where publisher database and/or distribution database is part of Always On. 
 
Azure SQL Data Warehouse: 
- Add Rejected Row Location support for External Tables in Azure SQL Data Warehouse. 

**Integration Services (IS)**

- Added a scheduling feature for SSIS packages deployed to Azure SQL Database. Unlike SQL Server on premises and SQL Database Managed Instance, which have SQL Server Agent as a first-class job scheduler, SQL Database does not have a built-in scheduler. This new SSMS feature provides a familiar user interface that's similar to SQL Server Agent for scheduling packages deployed to SQL Database. If you're using SQL Database to host the SSIS catalog database, SSISDB, you can use this SSMS feature to generate the Data Factory pipelines, activities, and triggers required to schedule SSIS packages. You can then edit and extend these objects in Data Factory. For more info, For details, see [Schedule SSIS package execution on Azure SQL Database with SSMS](../integration-services/lift-shift/ssis-azure-schedule-packages-ssms.md). To learn more about Azure Data Factory pipelines, activities, and triggers, For details, see [Pipelines and activities in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-pipelines-activities) and [Pipeline execution and triggers in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-pipeline-execution-triggers).
- Support for SSIS package scheduling in SQL Agent on SQL Managed instance. It is now possible to create SQL Agent jobs to execute SSIS packages on the managed instance. 

### Bug fixes

**General SSMS** 

Maintenance Plan:   
- Fixed an issue where trying to change the schedule of an existing Maintenance Plan was throwing an exception. For details, see [SSMS 17.6 crashes when clicking on a schedule in a maintenance plan](https://feedback.azure.com/forums/908035-sql-server/suggestions/33712924).

Always On: 
- Fixed an issue where Always On Latency Dashboard wasn't working with SQL Server 2012.
 
Scripting: 
- Fixed an issue where scripting stored procedure against Azure SQL Data Warehouse, isn't working for non-admin user.
- Fixed an issue where scripting a database against Azure SQL Database wasn't scripting the *SCOPED CONFIGURATION* properties.
 
Telemetry: 
- Fixed issue where  SSMS crashes then trying to connect to a server, after opting out of sending telemetry.
 
Azure SQL Database: 
- Fixed an issue  where the user wasn't able to set or change compatibility level (the drop-down from empty). In order to set the compatibility level to 150, the user still needs to use the *Script* button and manually edit the script. 
 
SMO: 
- Exposed Error Log Size setting in SMO. For details, see [Set the Maximum Size of the SQL Server Error Logs](https://feedback.azure.com/forums/908035-sql-server/suggestions/33624115).  
- Fix linefeed scripting in SMO on Linux.
- Miscellaneous perf improvement when retrieving rarely used properties.  

Intellisense: 
- Perf improvement: reduced volume of intellisense queries for column data. This is especially beneficial when working on tables with huge number of columns. 

SSMS User settings:
- Fixed an issue where the options page wasn't resizing properly.

Misc:  
- Improved how text is displayed on *Statistics details* page. 

**Integration Services (IS)**

- Better support for Azure SQL Database Managed Instance.
- Fixed an issue where the user was unable to create a catalog for SQL Server 2014 or before.
- Fixed two issues with reports:
   - Removed the machine name for Azure servers.
   - Improved handling of localized object name.


### Known issues

Some dialogs display an invalid edition error when working with new *General Purpose* or *Business Critical* Azure SQL Database editions.

## ![download](../ssdt/media/download.png) [SSMS 17.6](https://go.microsoft.com/fwlink/?linkid=870039)

Build number: 14.0.17230.0<br>
Release date: March 20, 2018

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x40a)

### What's new

**General SSMS**

SQL Database Managed Instance:

- Added a support for [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance). Azure SQL Database Managed Instance provides near 100% compatibility with SQL Server on-premises, a native [virtual network (VNet)](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) implementation that addresses common security concerns, and a [business model](https://azure.microsoft.com/pricing/details/sql-database/) favorable for on-premises SQL Server customers.
- Support for common management scenarios like:
   - Create and alter databases.
   - Back up and restore databases.
   - Importing, exporting, extracting, and publishing Data-tier Applications.
   - Viewing and altering Server properties.
   - Full Object Explorer support.
   - Scripting database objects.
   - Support for SQL Agent jobs.
   - Support for Linked Servers.
- Learn more about Managed Instances [here](https://azure.microsoft.com/blog/migrate-your-databases-to-a-fully-managed-service-with-azure-sql-database-managed-instance/).

Object Explorer:
- Added settings to not force brackets around names when dragging & dropping from Object Explorer to Query Window. (User suggestions [32911933](https://feedback.azure.com/forums/908035-sql-server/suggestions/32911933), and [32671051](https://feedback.azure.com/forums/908035-sql-server/suggestions/32671051).)

Data Classification:
- General improvements and bug fixes.

**Integration Services (IS)**

- Added support to deploy packages to a [SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).

### Bug fixes

**General SSMS**

Data Classification:

- Fixed an issue in *Data Classification that was causing newly added classifications to be displayed with stale *information type* and *sensitivity label*.
- Fixed an issue where *Data Classification* wasn't working when targeting a server set to a case-sensitive collation.
		
Always On:

- Fixed an issue in AG Show Dashboard where clicking on *Collect Latency Data* could result in an error when the server was set to a case-sensitive collation.
- Fixed an issue where SSMS was incorrectly reporting an AG as *Distributed* when the Cluster service shuts down.
- Fixed an issue when creating AG using *Create Availability Group* dialog the *ReadOnlyRoutingUrl* is required.
- Fixed an issue when the primary is down and manually failover to secondary, a NullReferenceException is thrown.
- Fixed an issue when creating Availability Group using backup/restore to initialize a database, on the secondary replicas, the database files are created in the default directory. The fix includes:
   - Add the data/log directory validator.
   - Only do the file relocation when the replica is on a different OS to the primary replica.
- Fixed an issue where SSMS wizard doesn't generate *CLUSTER_TYPE* option, causing secondary join to fail.

Setup:
- Fixed issue where trying to upgrade SSMS by installing the "upgrade package" was failing when SSMS was installed in a non-default location.

SMO:
- Fixed performance issue where scripting tables on SQL Server 2016 and above could take up to 30 seconds (now, it's down to less than 1 second).

Object Explorer:
- Fixed an issue where SSMS could throw an exception like "Object cannot be cast from DBNull to other types" when trying to expand *Management* node in Object Explorer.
- Fixed an issue where *Start PowerShell* wasn't detecting the SQLServer module when user-defined PS profile emitted output.
- Fixed an intermittent hang that could occur when right-clicking a Table or Index node in Object Explorer.

Database Mail:
- Fixed an issue where *Database Mail Configuration Wizard* was throwing an exception when trying to display/manage more than 16 profiles.


**Analysis Services (AS)**

- Fixed as issue where modifying a data source on a 1400 compatibility level model in SSMS the changes are not saved to the server.

**Integration Services (IS)**

- Fixed an issue where SSMS did not show SSIS catalog node and reports when connected to SQL Database Managed Instance

### Known issues

> [!WARNING]
> There is a known issue where SSMS 17.6 becomes unstable and crashes when using [Maintenance Plans](../relational-databases/maintenance-plans/maintenance-plans.md). If you use Maintenance Plans, do not install SSMS 17.6. Downgrade to SSMS 17.5 if you already installed 17.6 and this issue is affecting you. 



## ![download](../ssdt/media/download.png) [SSMS 17.5](https://go.microsoft.com/fwlink/?linkid=867670)
Generally available| Build number: 14.0.17224.0

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x40a)

### What's new

**General SSMS**

Data Discovery & Classification:

- Added a new SQL Data Discovery & Classification feature for discovering, classifying, labeling & reporting sensitive data in your databases. 
- Auto-discovering and classifying your most sensitive data (for example, business, financial, healthcare, personal data) can play a pivotal role in your organizational information protection stature.
- Learn more at [SQL Data Discovery & Classification](../relational-databases/security/sql-data-discovery-and-classification.md).

Query Editor:

- Added support for SkipRows option to the Delimited Text External File Format for Azure SQL DW. This capability allows users to skip a specified number of rows when loading delimited text files into SQL DW. Also added the corresponding intellisense/SMO support for the FIRST_ROW keyword. 

Showplan:

- Enabled display of estimated plan button for SQL Data Warehouse
- Added new showplan attribute *EstimateRowsWithoutRowGoal*; and added new showplan attributes to *QueryTimeStats*: *UdfCpuTime* and *UdfElapsedTime*. For more information, For details, see [Optimizer row goal information in query execution plan added in SQL Server 2017 CU3](https://support.microsoft.com/help/4051361).



### Bug fixes

**General SSMS**

Showplan:

- Fixed Live Query Statistics elapsed time, to show engine execution time instead of time elapsed for LQS connection.
- Fixed an issue where showplan wasn't able to recognize Apply logical operators like GbApply and InnerApply.
- Fixed an issue related to ExchangeSpill.

Query Editor:

- Fixed on issue related to SPIDs where SSMS could throw an error like "Input string wasn't in a correct format. (mscorlib)" when executing a simple query preceded by a "SET SHOWPLAN_ALL ON". 


SMO:

- Fixed an issue where SMO wasn't able to fetch AvailabilityReplica properties in case the server collation happened to be case-sensitive (as a result, SSMS could display an error message like "The multi-part identifier "a.delimited" could not be bound."
- Fixed an issue in DatabaseScopedConfigurationCollection class, where incorrectly handling collations (as a result, an SSMS running on an ma machine with a Turkish locale could display an error like "legacy cardinality estimation isn't valid scoped configuration" when right-clicking on a database running on a server with a case-sensitive collation).
- Fixed an issue in JobServer class, where SMO wasn't able to fetch SQL Agent properties on a SQL 2005 server (as a result, SSMS was throwing an error like "Cannot assign a default value to a local variable. Must declare the scalar variable "\@ServiceStartMode" and, ultimately, wasn't displaying the SQL Agent node in Object Explorer).

Templates: 

- "Database Mail": fixed a couple of typos [(https://feedback.azure.com/forums/908035/suggestions/33143512)](https://feedback.azure.com/forums/908035/suggestions/33143512).  

Object Explorer:
- Fixed an issue where Managed Compression would fail for indexes (https://feedback.azure.com/forums/908035-sql-server/suggestions/32610058-ssms-17-4-error-when-enabling-page-compression-o).

Auditing:
- Fixed an issue with the *Merge Audit Files* feature.
<br>

### Known issues

Data classification:
- Removing a classification and then manually adding a new classification for the same column results in the old information type and sensitivity label being assigned to the column in the main view.<br>
*Workaround*: Assign the new information type and sensitivity label after the classification was added back to the main view and before saving.


## ![download](../ssdt/media/download.png) [SSMS 17.4](https://go.microsoft.com/fwlink/?linkid=864329)
Generally available| Build number: 14.0.17213.0

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40a)


### What's new

**General SSMS**

Vulnerability Assessment:
- Added a new SQL Vulnerability Assessment service to scan your databases for potential vulnerabilities and deviations from best practices, such as misconfigurations, excessive permissions, and exposed sensitive data. 
- Results of the assessment include actionable steps to resolve each issue and customized remediation scripts where applicable. The assessment report can be customized for each environment and tailored to specific requirements. Learn more at [SQL Vulnerability Assessment](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment).

SMO:
- Fixed issue where *HasMemoryOptimizedObjects were throwing exception on Azure.
- Added support for new CATALOG_COLLATION feature.

Always On Dashboard:
- Improvements for latency analysis in Availability Groups.
- Added two new reports: *AlwaysOn\_Latency\_Primary* and *AlwaysOn\_Latency\_Secondary*.

Showplan:
- Updated links to point to correct documentation.
- Allow single plan analysis directly from actual plan produced.
- New set of icons.
- Added support for recognize "Apply logical operators" like GbApply, InnerApply.

XE Profiler:
- Renamed to XEvent Profiler.
- Stop/Start menu commands now stop/start the session by default.
- Enabled keyboard shortcuts (for example, **CTRL+F** to search).
- Added database\_name and client\_hostname actions to appropriate events in XEvent Profiler sessions. For the change to take effect, you may need to delete existing QuickSessionStandard or QuickSessionTSQL session instances on the servers - [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981)

Command line:
- Added a new command-line option ("-G") that can be used to automatically have SSMS connect to a server/database using Active Directory Authentication (either 'Integrated' or 'Password'). For details, see [Ssms utility](ssms-utility.md).

Import Flat File Wizard:
- Added a way to pick a schema name other than the default ("dbo") when creating the table.

Query Store:
- Restored the "Regressed Queries" report when expanding the Query Store available reports list.

**Integration Services (IS)**
- Added package validation function in Deployment Wizard, which helps the user figure out components inside SSIS packages that are not supported in Azure-SSIS IR.

### Bug fixes

**General SSMS**

- Object Explorer:
Fixed an issue where Table-Valued Function node wasn't showing up for database snapshots - [Connect 3140161](https://connect.microsoft.com/SQLServer/feedback/details/3140161).
Improved performance when expanding *Databases* node when the server has autoclose databases.
- Query Editor:
Fixed an issue where IntelliSense was failing for users that don't have access to the master database.
Fixed an issue that was causing SSMS to crash in some cases when the connection to a remote machine was closed - [Connect 3142557](https://connect.microsoft.com/SQLServer/feedback/details/3142557).
- XEvent Viewer:
Re-enabled functionality to export to XEL.
Fixed issues where in some cases the user wasn't able to load an entire XEL file.
- XEvent Profiler:
Fixed an issue that was causing SSMS to crash when the user did not have *VIEW SERVER STATE* permissions.
Fixed an issue where closing the XE Profiler Live Data window did not stop the underlying session.
- Registered Servers:
Fixed an issue where the "Move To..." command stopped working - [Connect 3142862](https://connect.microsoft.com/SQLServer/feedback/details/3142862) and [Connect 3144359](https://connect.microsoft.com/SQLServer/feedback/details/3144359/).
- SMO:
Fixed an issue where the TransferData method on the Transfer object wasn't working.
Fixed an issue where Server databases throws exception for paused SQL DW databases.
Fixed an issue where scripting SQL database against SQL Data Warehouse generated incorrect T-SQL parameter values.
Fixed an issue where scripting of a stretched DB incorrectly emitting the *DATA\_COMPRESSION* option.
- Job Activity Monitor:
Fixed an issue where the user was getting an "Index was out of range. Must be non-negative and less than the size of the collection. 
		Parameter name: index (System.Windows.Forms)" error when trying to filter by Category - [Connect 3138691](https://connect.microsoft.com/SQLServer/feedback/details/3138691).
- Connection Dialog:
Fixed an issue where domain users without access to a Read/Write domain controller could not sign in to a SQL Server using SQL Authentication - [Connect 2373381](https://connect.microsoft.com/SQLServer/feedback/details/2373381).
- Replication:
Fixed an issue where an error similar to "Cannot apply value 'null' to property ServerInstance" was displayed when looking at properties of a pull subscription in SQL Server.
- SSMS Setup:
Fixed an issue where SSMS setup was incorrectly causing all the installed products on the machine to be reconfigured.
- User Settings:
   - With this fix, Azure Government users have uninterrupted access to their Azure SQL Database and Azure Resource Manager resources with SSMS via Universal authentication and Azure Active Directory login.  Users of prior versions of SSMS would need to open Tools|Options|Azure Services and under Resource Management change the configuration of the "Active Directory Authority" property to https://login.microsoftonline.us.

**Analysis Services (AS)**

- Profiler: fixed an issue when trying to connect using Window Authentication against Azure AS.
- Fixed an issue that could cause a crash when canceling connection details on a 1400 model.
- When setting an Azure blob key in the connection properties dialog when refreshing credentials, it will now be visually masked.
- Fixed an issue in the Azure Analysis Services User selection dialog to show the Application ID guid instead of the Object ID when searching.
- Fixed an issue in the Browse Database\MDX query designer toolbar that caused the icons to be incorrectly mapped for some buttons.
- Fixed an issue that prevented connecting to SSAS using msmdpump IIS http/https addresses.
- Several strings in the Azure Analysis Services User Picker dialog have now been translated for additional languages.
- MaxConnections property is now visible for data sources in tabular models.
- Deployment Wizard will now generate correct JSON definitions for Azure AS role members.
- Fixed an issue in SQL Profiler where selecting Windows Authentication against Azure AS would still prompt for login.



## ![download](../ssdt/media/download.png) [SSMS 17.3](https://go.microsoft.com/fwlink/?linkid=858904)
Generally available| Build number: 14.0.17199.0

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40a)


### Enhancements

- New "Import Flat File" wizard added to streamline the import experience of CSV files with an intelligent framework, requiring minimal user intervention, or specialized domain knowledge. For details, see [Import Flat File to SQL Wizard](../relational-databases/import-export/import-flat-file-wizard.md).
- Added "XEvent Profiler" node to Object Explorer. For details, see [Use the SSMS XEvent Profiler](../relational-databases/extended-events/use-the-ssms-xe-profiler.md).
- Updated waits filtering and categorization in Performance Dashboard historical waits report.
- Added the syntax check of the "Predict" function.
- Added the syntax check of the External Library Management queries.
- Added SMO support for External Library Management.
- Added "Start PowerShell" support to "Registered Servers" window (requires a new SQL PowerShell module).
- Always On: added [read-only routing support](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md) for availability groups.
- Added an option to send tracing details to the Output Window for "Active Directory - Universal with MFA support" logins (off by default; needs to be turned on in user settings under "Tools > Options > Azure Services > Azure Cloud > ADAL Output Window Trace Level"). 
- Query Store: 
  - Query Store UI will be accessible even when QDS is OFF as long as QDS have recorded any data.
  - Query Store UI now exposes waits categorization in all the existing reports. This lets customers unlock the scenarios of Top Waiting Queries and many more.
- Made inclusion of the scripting parameters headers optional (off by default;  can be enabled in user settings under "Tools > Options > SQL Server Object Explorer > Scripting > Include scripting parameters header") - [Connect item 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199).
- Removed "RC" branding.

### Bug Fixes

**General SSMS**

- XEvent: 
   - Fixed issue where SSMS opens only part of the events in .xel file.
   - Improved "Watch Live Data" experience when default database isn't 'master' - [Connect item 1222582](https://connect.microsoft.com/SQLServer/feedback/details/1222582).
- Always On: Fixed issue where "Restore log backups" may fail with error "The sign in this backup set terminates at LSN x, which is too early to apply to the database".
- Job Activity Monitor: fixed inconsistent icons - [Connect item 3133100](https://connect.microsoft.com/SQLServer/feedback/details/3133100).
- Query Store: Fixed Issue where user cannot choose "custom" date range for Query Store reports. Linked to below connect items.
   - [Connect item 3139842](https://connect.microsoft.com/SQLServer/feedback/details/3139842)
   - [Connect item 3139399](https://connect.microsoft.com/SQLServer/feedback/details/3139399)
- Fixed issue where connection dialog doesn't "clear" the most recently used database when saved info has named database and user selects default.
- Object Scripting:
Fixed an issue where "Generate database script" not working and throwing an error when the user has a paused DW database on the server, but selected another non-DW database and tried t script it.
Fixed issue where the header for scripted Stored Procedures wasn't matching the script settings, resulting in a misleading script - 
		[Connect item 3139784](https://connect.microsoft.com/SQLServer/feedback/details/3139784).
Re-enabled the "Script button" when targeting Azure SQL objects.
Fixed issue where SSMS wasn't allowing scripting for "Alter" or "Execute" on some objects (UDF, View, SP, Trigger) when connected to an Azure SQL database - 
		[Connect item 3136386](https://connect.microsoft.com/SQLServer/feedback/details/3136386).
- Query editor:
  - Improved intellisense when targeting Azure SQL databases.
  - Fixed an issue where queries failed due to an expired authentication token (Universal Authentication).
  - Improved intellisense when working against Azure SQL databases (particularly, when connecting to Azure SQL Database, the latest T-SQL grammar (140) will be used).
  - Fixed issue where open a query window with a connection to a non-DataWarehouse database on a server would cause all subsequent query windows for that server to DataWarehouse databases to throw various errors about unsupported types/options.
- Always On:
   - Added For details, seeding mode column to Always On dashboard and AG properties page.
   - Fixed issue where it wasn't possible to create a Linux AG when primary is on Windows - [Connect item 3139856](https://connect.microsoft.com/SQLServer/feedback/details/3139856).
- Fixed several "Out of Memory" issues in SSMS when running queries - 
	[Connect item 2845190](https://connect.microsoft.com/SQLServer/feedback/details/2845190), 
	[Connect item 3123864](https://connect.microsoft.com/SQLServer/feedback/details/3123864).
- Profiler: 
   - Fixed issue where Profiler wasn't working when targeting SQL 2005.
   - Fixed issue where Profiler wasn't honoring the "trust server certificate" connection option.
- Activity Monitor: fixed an issue where Activity Monitor does not work when pointed at SQL Server running on Linux.
- Fixed an issue with the SMO Transfer class where it wouldn't transfer External Data Source or External File Format objects, objects of those types should now correctly be included in the transfer.
- Registered Servers:
   - Enabled multiserver query for UA servers (it tries to use the same token for every UA server in the group).
- AD Universal Authentication:
   - Fixed issue where Azure AD authentication wasn't supported.
   - Fixed issue where table/view designer wasn't working.
   - Fixed issue where "Select Top 1000 rows" and "Edit Top 200 rows" were not working.
- Database restore: fixed an issue where restore omits the last folder in the path when moving files to an alternate location.
- Compress wizard:
   - Fixed an issue with manage compression wizard for indexes; fixed issue where compress data wizards were broken for SQL 2016 and lower.
		https://connect.microsoft.com/SQLServer/feedback/details/3139342
   - Added Compress wizard to Azure tables and indexes.
- Showplan: 
   - Fixed issue where PDW operators were not recognized.
- Server Properties:
   - Fixed issue with not being able to modify server processor affinity.


**Analysis Services (AS)**

- Fixed a number of issues with Deployment Wizard to support tabular 1400 compat-level models and Power Query data sources.
- Deployment Wizard can now deploy to AS Azure when running from command line.
- When using Windows Auth in AS Azure the user will now For details, see the name of the user account in Object Explorer correctly.


### Known issues in this 17.3 release:

**General SSMS**

- The following SSMS functionality isn't supported for Azure AD auth using UA with MFA:
   - Database Engine Tuning Advisor isn't supported for Azure AD auth; there is a known issue where the error message presented to the user is a bit cryptic "Could not load file or assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,..." instead of the expected "Database Engine Tuning Advisor does not support Microsoft Azure SQL Database. (DTAClient)".
- Trying to analyze a query in DTA results in an error: "Object must implement IConvertible. (mscorlib)".
- *Regressed Queries* is missing from the Query Store list of reports in Object Explorer.
   - Workaround: Right-click the **Query Store** node and select **View Regressed Queries**.

**Integration Services (IS)**

- The [execution_path] in [catalog].[event_messagea] isn't correct for package executions in Scale Out. The [execution_path] starts with "\Package" instead of the object name of the package executable. When viewing the overview report of package executions in SSMS, the link of "Execution Path" in Execution Overview cannot work. The workaround is to click "View Messages" on overview report to check all event messages.


## ![download](../ssdt/media/download.png) [SSMS 17.2](https://go.microsoft.com/fwlink/?linkid=854085)
Generally available| Build number: 14.0.17177.0

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40a)

### Enhancements

- Multi-Factor Authentication (MFA)
  - Multiple-user Azure AD authentication for Universal authentication with Multi-factor authentication (UA with MFA)
  - A new user credential input field was added for Universal Authentication with MFA to support multi-user authentication.
- The connection dialog box now supports the following 5 authentication methods:
  - Windows Authentication
  - SQL Server Authentication
  - Active Directory - Universal with MFA support
  - Active Directory - Password
  - Active Directory - Integrated

- Database export/import for DacFx wizard using Universal Authentication with MFA.
- For API support, see [IUniversalAuthProvider Interface](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx).
- ADAL managed library used by Azure AD Universal Authentication with MFA was upgraded to 3.13.9 version.
- In addition, a new CLI interface was delivered supporting Azure AD admin setting for SQL Database and SQL Data Warehouse.

 For more information on the Active Directory authentication methods, For details, see [Universal Authentication with SQL Database and SQL Data Warehouse (SSMS support for MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) and [Configure Azure SQL Database multi-factor authentication for SQL Server Management Studio](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- Output window has entries for queries run during expansion of Object Explorer nodes
- Enabled View designer Azure SQL Databases
- The default scripting options for scripting objects from Object Explorer in SSMS have changed:
  - Previously, the default on a new install was to have the generated script target the latest version of SQL Server (currently SQL Server 2017).
  - In SSMS 17.2 a new option has been added: *Match Script Settings to Source*. When set to *True*, the generated script targets the same version, engine type, and engine edition as the server the object being scripted is from.
  - The *Match Script Settings to Source* value is set to *True* by default, so new installs of SSMS will automatically default to always scripting objects to the same target as the original server.
  - When the *Match Script Settings to Source* value is set to *False*, the normal scripting target options will be enabled and function as they did previously.
Additionally, all the scripting options have been moved to their own section - *Version Options*. They are no longer under *General Scripting Options*.

- Added support for National Clouds in "Restore from URL"
- QueryStoreUI reports now supports additional metrics (for example, RowCount, DOP, CLR Time) from sys.query_store_runtime_stats.
- IntelliSense is now supported for Azure SQL Database
https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases
- Security: connection dialog will default to not trusting server certificates and to requesting encryption for Azure SQL DB connections
- General improvements around support for SQL Server on Linux:
 - Database Mail node is back
 - Addressed misc issues related to paths
 - Activity Monitor is more stable
 - Connection Properties dialog displays correct platform
- Performance Dashboard server report now available as a default report:
  - Can connect to SQL Server 2008 and newer versions.
  - Missing indexes sub-report uses scoring to assist in identifying most useful indexes.
  - Historical wait stats subreport now aggregates waits be category. Idle and sleep waits filtered out by default.
  - New Historical latches subreport.
- Showplan node search allows searching in plan properties. Easily look for any operator property such as table name. To use this option when viewing a plan:
  - Right-click on plan, and in the context menu click on Find Node option
  - Use **CTRL+F**


**Analysis Services (AS)**

- New AAD role member selection for users without email addresses in AS Azure models in SSMS

**Integration Services (IS)**

- Added new column ("Executed Count") to the execution report for SSIS

### Known issues in this release:

- Query windows using "Active Directory - Universal with MFA Support" authentication may experience an error similar to the following, when attempting to execute a query after being open for one hour:

   `Msg 0, Level 11, State 0, Line 0
The connection is broken and recovery isn't possible. The client driver attempted to recover the connection one or more times and all attempts failed. Increase the value of ConnectRetryCount to increase the number of recovery attempts.`

   Rerunning the query should get past the error and succeed.

- The following SSMS functionality isn't supported for Azure AD auth using Universal Authentication with MFA:
  - The **New Table/View** designer shows the old-style login prompt, and does not work for Azure AD authentication.
  - The **Edit Top 200 Rows** feature doesn't support Azure Ad authentication.
  - The **Registered Server** component does not support Azure AD authentication.
  - The **Database Engine Tuning Advisor** isn't supported for Azure AD authentication. There is a known issue where the error message presented to the user is less than helpful: *Could not load file or assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,...* instead of the expected *Database Engine Tuning Advisor does not support Microsoft Azure SQL Database. (DTAClient)*.

**Analysis Services (AS)**

- Object Explorer in SSAS will not show the Windows Auth username in AS Azure connection properties.

### Bug fixes

- Fixed an issue when trying to print the results of a query (as text).  https://connect.microsoft.com/SQLServer/feedback/details/3055225/
- Fixed an issue where SSMS was incorrectly dropping tables and other objects when scripting the deletion of such objects on a Azure SQL database.
- Fixed an issue where SSMS occasionally SSMS refuses to start with an error like "Cannot find one or more components. Please reinstall the application"
- Fixed an issue where the SPID in SSMS UI could get stale and out of sync. https://connect.microsoft.com/SQLServer/feedback/details/1898875
- Fixed an issue in SSMS (silent) setup where the /passive argument was treated as /quiet.
- Fixed an issue where SSMS occasionally throws an "Object reference not set to an instance of the object" error on startup. https://connect.microsoft.com/SQLServer/feedback/details/3134698
- Fixed an issue on the "Data Compression Wizard" that was causing SSMS to crash when pressing 'Calculate' on Graph Table
- Addressed performance issue when right-clicking on an index for a table (over a slow internet connect). https://connect.microsoft.com/SQLServer/feedback/details/3120783
- Fixed an issue where SSMS wasn't able to enumerate backup files on servers with a case-sensitive collation. https://connect.microsoft.com/SQLServer/feedback/details/3134787 and https://connect.microsoft.com/SQLServer/feedback/details/3137000
- Showplan and showplan compare assorted fixes
- Fixed an issue where the Connection Dialog  wasn't allowing the user to specify the "Network Protocol" to use for the connection, unless SQL Server was installed on the machine running SSMS. https://connect.microsoft.com/SQLServer/feedback/details/3134997
- Improved support for multi-monitor configurations where some SSMS dialog were showing up on "random" locations. Added new option "Task Dialogs" under "SQL Server Object Explorer| Commands" user settings to allow remembering the position of a task dialog or property sheet when it closes. https://connect.microsoft.com/SQLServer/feedback/details/889169, https://connect.microsoft.com/SQLServer/feedback/details/1158271, https://connect.microsoft.com/SQLServer/feedback/details/3135260 
- Fixed an issue where SSMS wasn't able to change DB properties for encrypted Azure SQL DB
- Improved "Discard results after execution" option. https://connect.microsoft.com/SQLServer/feedback/details/1196581
- Improved/fixed issue where users are not able to access Azure subscriptions for which they are not administrators.
- Improved "Database Restore" wizard to keep the target database selected in OE regadless of the source database selection. https://connect.microsoft.com/SQLServer/feedback/details/3118581
- Fixed an issue where Object Explorer wasn't sorting incorrectly newly added "Natively compiled stored procedures". https://connect.microsoft.com/SQLServer/feedback/details/3133365
- Fixed an issue where "SELECT TOP n ROWS" did not include the "TOP" clause. For Azure SQLDW. https://connect.microsoft.com/SQLServer/feedback/details/3133551 and https://connect.microsoft.com/SQLServer/feedback/details/3135874
- QueryStoreUI: fixed issue where non-custom time intervals were not working correctly for all reports.
- Always Encrypted:
Improved messaging for AKV permission status in New CMK dialog
Added tooltips to CEK dropdown to make it easier to distinguish CEKs with long names
Fixed an issue where some CNG key store providers would not be displayed in the New Column Master Key dialog for Always Encrypted
- Fixed inconsistent "Application Name" for SSMS connections. https://connect.microsoft.com/SQLServer/feedback/details/3135115
- Fixed an issue where SSMS wasn't generating correct scripts for Azure SQL (tables and indexes with DATA_COMPRESSIONS option). https://connect.microsoft.com/SQLServer/feedback/details/3133148
- Fixed an issue where user wasn't able to use **CTRL+Q** shortcut for Quick Launch (the new key bindings to toggle the "IntelliSense Enabled" option in Query Editor is now **CTRL+B**, **CTRL+I**. https://connect.microsoft.com/SQLServer/feedback/details/3131968
- Fixed an issue in "Restore Database" where SSMS was throwing an exception when trying to select a storage account from a subscription that has accounts with custom domains defined
- Fixed an issue in "Database Diagram" where SSMS was throwing an "Index was outside the bounds of the array" error; also, the user wasn't able to change the "Table View" to anything but standard. https://connect.microsoft.com/SQLServer/feedback/details/3133792 and https://connect.microsoft.com/SQLServer/feedback/details/3135326
- Fixed an issue in "Backup/Restore to URL" where SSMS wasn't enumerating classic storage accounts.
- Fixed an issue where an exception was being thrown when trying to add schema-bound securables to DB Roles. https://connect.microsoft.com/SQLServer/feedback/details/3118143
- Fixed an issue where SSMS was intermittently showing the error "Data is Null. This method or property cannot be called on Null values." when expanding a table node https://connect.microsoft.com/SQLServer/feedback/details/3136283
- DTA: Fixed an issue where DTAEngine.exe terminates with Heap Corruption when evaluating Partition Function with Certain Boundary Values.


**Analysis Services (AS)**

- Fixed an issue where AS Restore Database would fail with an error if the DB had a different Name than ID
- Fixed an issue causing the DAX query window to disregard the menu option for toggling IntelliSense Enabled
- Fixed an issue that prevented connecting to SSAS through msmdpump IIS http/https addresses
- Allow connecting to AS Azure using a password that contains a semi-colon
- Scripting out AS Restore Database command with "Skip Membership" option will include the new corresponding JSON option when used with SQL Server 2017 AS server or AS Azure
- Fixed an extremely rare issue that could cause the delete database dialog to raise an error when loading
- Fixed an issue that may occur when attempting to view partitions in 1400-compat level model containing a mix of SQL query and M partition definitions

**Integration Services (IS)**
- Fixed issue where the execution information reports of SSISDB catalog can't be displayed
- Addressed issues in SSMS related to poor performance with large number of projects/packages

## ![download](../ssdt/media/download.png) [SSMS 17.1](https://go.microsoft.com/fwlink/?linkid=849819)
Generally available| Build number: 14.0.17119.0

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40a)

### Enhancements

- Profiler: Help > About now displays release version number (e.g 17.1)
- Analysis Service users can refresh credentials for their datasources for 1200 TM models and above from the context menu on the datasource
- Built-in SSIS reports now show logs from SSIS scale-out execution in CTP 2.1
- SSIS scale-out management application
  - View basic information about scale-out master.
  - Easily add a Worker to the scale-out deployment.
  - View all the scale-out workers and basic information about them, and can also enable or disable them easily.

### Bug fixes
- Always On:
  - Fixed an issue where the properties of an Availability Replica was always displayed as "Automatic failover" mode for WSFC AGs.
  - Fixed an issue where the read-only routing list was overwritten when updating the Availability Group
- Always Encrypted: fixed an issue where log file generated was missing the information generated by DacFx.
- ShowPlan: fixed in issue where the UI was always showing the Actual join type attribute for non-adaptive join operators.
- Setup:
  - Fixed an issue where SSMS 17.0 was breaking SSDT on Visual Studio 2013 [Connect Item 3133479]
  - Fixed an issue where clicking on "Restart" at the end of setup wasn't restarting the machine
- Scripting: temporarily preventing SSMS from accidentally deleting Azure database objects when trying to script the deletion by disabling that option.  Proper fix will be in an upcoming release of SSMS.
- Object Explorer: fixed an issue where "Databases" node wasn't expanded when connected to an Azure database created using "AS COPY"

## ![download](../ssdt/media/download.png) [SSMS 17.0](https://go.microsoft.com/fwlink/?LinkID=847722)
Generally available| Build number: 14.0.17099.0

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x40a)

### Enhancements 

- Upgrade package and Windows Software Update Services (WSUS) 
Future 17.X releases include a smaller cumulative update package 
  - The update package will also be published to the WSUS catalog  
- Icon Updates
Icons have been updated to be consistent with VS Shell provided icons and support High DPI resolutions
New SSMS and Profiler program icons to differentiate between 16.X and 17.X versions
- SQL PowerShell Module
  - SQL Server PowerShell module removed from SSMS and now ships via the PowerShell gallery (PowerShell 5.0 now required to support module versioning)
  - Miscellaneous improvements to the "presentation" (formatting) of some SMO objects (e.g. databases now show the size and the available space and tables show row count and space usage)
  - Added colorization when the PowerShell command prompt is invoked from the "Start PowerShell" menu in OE
  - Added -ClusterType and -RequiredCopiesToCommit parameter to AG cmdlets (New-SqlAvailabilityGroup, Join-SqlAvailabilityGroup, and Set-SqlAvailabilityGroup cmdlets)
  - Added parameters -ActiveDirectoryAuthority and -AzureKeyVaultResourceId to Add-SqlAzureAuthenticationContext cmdlet
  - Added	Revoke-SqlAvailabilityGroupCreateAnyDatabase, Grant-SqlAvailabilityGroupCreateAnyDatabase and Set-SqlAvailabilityReplicaRoleToSecondary cmdlets
  - Added -For details, seedingMode parameter to Set-SqlAvailabilityReplica and New-SqlAvailabilityReplica cmdlets
  - Added -ConnectionString parameter to Get-SqlDatabase
- SQL Server on Linux
General improvements and fixes for Log Shipping
  - Added support for native Linux paths Attach, Restore and Backup database
  - Added support for native Linux paths for audit log destination folder
- Analysis Services
  - DAX Query Window:
    - Parentheses matching in the editor
    - DEFINE MEASURE and DEFINE VAR syntax support
    - Assorted Intellisense improvements
  - Universal Authentication
    - Allows users to specify a username and no password and the Azure Login Dialog will handle the connection
  - SSMS PQ Integration: 
    - Scripting of structured data sources works 
    - Viewing and Editing of structured data sources in PQ UI
- New "Add Unique Constraint" template
- Showplan
Show max instead of sum across the threads in properties window for elapsed time
Expose new mem grant operator properties
Enabled the "Edit Query" button in Live Query Statistics
Support for interleaved execution
  - New option to "Analyze Actual Execution Plan"
  - General improvements to showplan compare
  - Introduced functionality in Showplan Comparison feature to find significant differences in Cardinality Estimation between matching nodes of two query plans and perform basic analysis of the possible root causes
- Removed Configuration Manager from Registered Servers explorer
- Enable reading audit logs from Azure blob storage
- Added Parameterization for Always Encrypted, please refer to [this page](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/) for more details 
- AAD Universal auth connection to Azure SQL DB supports custom tenant ID 
- Generate scripts for Azure SQL Database, now scripts full text, rules, and database
- Branding fixes in splash screens for SSMS and Profiler
- Removed Utility Control Point UI from SSMS
- SSMS can now create "PremiumRS" edition Azure SQL databases
- Always On Availability Groups
  - Add support for new cluster types: EXTERNAL and NONE
Add support for SQL Server on Linux
Add automatic For details, seeding as an option for initial data synchronization
Fixed some defects, e.g. endpoint URL handling, DB refresh and UI layout
Removed Azure replica-related features
  - Improved IntelliSense for several Availability Group keywords
- Activity Monitor
  - Added new "Activity Monitor" pane to the SSMS Output window
  - Changed connection error/timeout message to log info to output window rather than a pop-up message
  - Removed empty chart (5th chart) in Overview section
  - Added "(paused)" to Overview title if the Activity Monitor data collection is paused
  - Graph Extensions to SQL Server 
New icons for graph node and edge tables
Graph node and edge tables will be displayed under Graph Tables folder
Templates to create graph node and edge tables available
- Presentation Mode
3 new tasks available via Quick Launch (Ctr-Q)
PresentOn - Turn on presentation mode
PresentEdit - Edit the presentation font sizes for presentation mode.  "Text Editor font" for the Query Editor.  "Environment font" for other components.
RestoreDefaultFonts - Revert back to default settings. There is currently no PresentOff command at this time. Use RestoreDefaultFonts to turn off Presentation Mode*

### Bug fixes

- Fixed an issue where SSMS crashed when showplan scrolled via surface book touchpad
- Fixed an issue where SSMS hangs for a long time while getting the properties of a database which is being restored or offline 
- Fixed an issue where "Help viewer" could not be opened in RC builds
- Fixed an issue where "Maintenance Plans Tasks Toolbox" items may be missing in SSMS.
- Fixed an issue in SSMS where the user was unable to shrink a database when the database name contained curly braces. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3122618)
- Fixed an issue where SSMS was trying to script the deletion of an Azure database was actually causing the deletion of the database itself. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3131458/)
- Fixed an issue where default values were not scripted for user-defined table types. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3119027)
- Another round of perf improvements around context menu on indexes. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3120783)
- Fixed issue which was causing excessive flickering when hovering mouse over missing index in execution plan. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3118510)
- Fixed an issue where SSMS was taking the DB offline when scripting [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3118550)
- Miscellaneous UI fixes on localized (non-English) versions of SSMS.
- Fixed issue where "Always Encrypted Keys" node was missing when targeting SQL 2016 SP1 Standard Edition.
- Always Encrypted
"Always Encrypted" menu was incorrectly enabled when targeting SQL 2016 RTM Standard Edition or any SQL 2014 (and below) servers
Fixed an issue where IntelliSense is reporting an error when the CREATE OR ALTER syntax is used
Fixed issue where encryption fails in case CMK/CEK contain characters that should be escaped, i.e. enclosed in brackets
When an Out of Memory exception occurs in SSMS, the user is presented an error that suggests using the native (64bit) PowerShell instead.
Fixed issue where the AE wizard was failing in case the user was using Resource Group Manager subscriptions instead of Classic Azure subscriptions
Fixed issue where AE wizard was showing an incorrect error when the user had no permissions in any subscriptions or had no Azure Key Vaults in any of them.
Fixed issue in AE wizard where the Azure Key Vault sign-in page wasn't showing Azure subscriptions in case of multiple AAD
Fixed issue in AE wizard where the Azure Key Vault sign-in page wasn't showing Azure subscriptions for which the user has reader permission
  - Fixed an issue where resource files may not be loaded correctly, thus resulting in inaccurate error messages
- Improved contrast of hyperlinks on SSMS Setup page
- Fixed an issue where PolyBase nodes were not displayed when connected to SQL Server Express (2016 SP1)
- Fixed an issue where SSMS is unable to change the Compatibility Level of an Azure DB to v140
- Improved performance of Object Explorer when expanding the list of Azure databases [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3100675)
- Fixed an issue where "View SQL Server Log" context menu item appeared incorrectly for non-relational server types (AS\RS\IS) 
- Fixed an issue where checking syntax of an Analysis Services partition query using SQL auth could result in login failed message
- Fixed an issue where renaming a preview 1400 compat-level AS tabular model would fail in SSMS
- Fixed an "operation failed on model" issue that could occur after attempting an invalid operation on the AS server in rare circumstances, revert local changes after unsuccessful save on the model
- Fixed a typo in Analysis Services Synchronize Database popup dialog
- Backup/restore container dialogs come up offscreen on multiple monitor setups. 
- SecurityPolicy create fails if target object has `]` in its name.
- SSMS 2016 "Open recent" menu doesn't show recently saved files. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)
- Removed reset of user settings when VS Shell is updated.
- Fixed an issue that was preventing the user from being able to change Compatibility Level of a database on SQL Server 2017.
- Query windows using AAD Universal authentication cannot refresh the query after an hour.
- Utility Control Point UI removed from SSMS.
- AD Universal auth connections fail to query data after the initial token expiration.
- Unable to script Rules from Azure SQL DB to Azure SQL DB.
- Fixed issue where SQL PowerShell wasn't able to connect legacy SQL instances (2014 and older). [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/1138754/sql-server-sqlps-powershell-module-fails-connection-to-sql-2012-instance)
- Fixed an issue that was causing SSMS to crash when failing to import registered servers.
- Fixed an issue that was causing SSMS to crash if a user has certain permissions in a database.
- SSMS - tables disappear from design surface while reviewing views. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/2946125/ssms-tables-disappears-from-design-surface-while-reviewing-views) 
- The table scrollbar does not allow the user to scroll the table content, only the up/down Arrow allow this. It's also possible to scroll the table content after trying to scroll using the scrollbar which is a bug. [Connect Item](
https://connect.microsoft.com/SQLServer/feedback/details/3106561/sql-server-manager-2016-bug-in-design-view) 
- Registered Servers not displaying icons after refreshing the root node.
- Script button for Create Database on Azure v12 servers executes script then displays message "No action to be scripted".
- SSMS Connect to Server dialog does not clear "Additional Properties" tab for each new connection.
- Generate Tasks script doesn't generate Create Database scripts for an Azure SQL DB.
- Scrollbar in View Designer appears disabled.
- Always Encrypted AVK key paths do not include version IDs.
- Reduced number of engine edition queries in the query window. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3113387)
- Always Encrypted errors from refreshing modules after encryption are incorrectly handled.
- Changed default connection timeout for OLTP and OLAP from 15 to 30 seconds to fix a class of ignored connection failures. 
- Fixed a crash in SSMS when custom report is launched. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3118856)
- Fixed an issue where "Generate Script..." fails for Azure SQL databases.
- Fix "Script As" and "Generate Script Wizard" to not add extra newlines when scripting objects such as stored procedures. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3115850)
- SQLAS PowerShell Provider: Add LastProcessed property to Dimension and MeasureGroup folders. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3111879)
- Live Query Statistics: fixed issue where it was only showing the first query in a batch. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3114221)  
- Showplan: show max instead of sum across the threads in properties window.
- Query Store: add new report on queries with high execution variation.
- Object explorer performance issues: [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3114074)
Context menu for tables momentarily hangs
SSMS is slow when right-clicking an index for a table (over a remote (Internet) connection). 
Avoid issuing table queries that sort on the server
- Removed Azure Deployment Wizard (Deploy Database to Azure VM) from SSMS
- Fixed issue where missing indexes were not shown in execution plans in SSMS [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3114194)
- Fixed common crash-on-shutdown issue in SSMS
- Fixed issue in Object Explorer where an error occurred when bringing up the context menu on the PolyBase|Scale-Out Group nodes [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3115128)
- Fixed an issue where SSMS may crash when trying to display the permissions on a database
- Query Store: general enhancements in context menu items for result grids of query store report
- Configuring Always Encrypted for an existing table fails with errors on unrelated objects. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3103181)
- Configuring Always Encrypted for an existing database with multiple schemas doesn't work. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3109591)
- The Always Encrypted, Encrypted Column wizard fails due to the database containing views that reference system views. [Connect Item](https://connect.microsoft.com/SQLServer/feedback/details/3111925)
- When encrypting using Always Encrypted, errors from refreshing modules after encryption are incorrectly handled.
- Fixed UI truncation issue on "New Server Registration" dialog
- Fix DMF Condition UI incorrectly updating expressions that contain string constant values with quotes in them
- Fixed an issue that may cause SSMS to crash when running custom reports
- Add "Execution in Scale Out..." menu item to the folder node
- Fixed an issue with Azure SQL DB firewall IP address allow list feature
- Fixed an issue in SSMS which caused an Object reference not set exception when editing the source of AS multi-dimensional partition
- Fixed an issue in SSMS which caused an Object reference not set exception when deleting a customer assembly from multi-dimensional AS server
- Fixed an issue where renaming an AS tabular 1400 db failed
- Fixed an issue with scripting a 1400 compat-level AS tabular datasource from connection properties dialog
- Remove assumption that tables in AS 1400 compat-level model have at least one partition
- Ctrl-R now toggles results pane in SSMS DAX query editor


## ![download](../ssdt/media/download.png) [SSMS 16.5.3](https://go.microsoft.com/fwlink/?LinkID=840946)
Generally available| Build number: 13.0.16106.4

[Chinese (Simplified)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x804)| [Chinese (Traditional)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x404)| [English (United States)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x409)| [French](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40c)| [German](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x407)| [Italian](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x410)| [Japanese](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x411)| [Korean](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x412)| [Portuguese (Brazil)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x416)| [Russian](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x419)| [Spanish](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40a)

The following issues were fixed this release:

* Fixed an issue introduced in SSMS 16.5.2 which was causing the expansion of the 'Table' node when the table had more than one sparse column.

* Users can deploy SSIS packages containing OData Connection Manager which connect to a Microsoft Dynamics AX/CRM Online resource to SSIS catalog. For more information, For details, see [OData Connection Manager](../integration-services/connection-manager/odata-connection-manager.md).

* Configuring Always Encrypted on an existing table fails with errors on unrelated objects. [Connect ID 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects)

* Configuring Always Encrypted for an existing database with multiple schemas doesn't work. [Connect ID 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work)

* The Always Encrypted, Encrypted Column wizard fails due to the database containing views that reference system views. [Connect ID 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors)

* When encrypting using Always Encrypted, errors from refreshing modules after encryption are incorrectly handled.

* *Open recent* menu doesn't show recently saved files. [Connect ID 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)

* SSMS is slow when right-clicking an index for a table (over a remote (Internet) connection). [Connect ID 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection)

* Fixed an issue with the SQL Designer scrollbar. [Connect ID 3114856](https://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016)

* Context menu for tables momentarily hangs 
 
* SSMS occasionally throws exceptions in Activity Monitor and crashes. [Connect ID 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/)

* SSMS 2016 crashes with error "The process was terminated due to an internal error in the .NET Runtime at IP 71AF8579 (71AE0000) with exit code 80131506"


## Uninstall and reinstall SSMS 17.x

If your SSMS installation is having problems, and a standard uninstall and reinstall doesn't resolve them, you can first try [repairing](https://support.microsoft.com/help/4028054/windows-10-repair-or-remove-programs) the Visual Studio 2015 IsoShell. If repairing the Visual Studio 2015 IsoShell doesn't resolve the problem, the following steps have been found to fix many random issues:

1. Uninstall SSMS the same way you uninstall any application (using *Apps & features*, *Programs and features*, depending on your version of Windows).

2. Uninstall Visual Studio 2015 IsoShell **from an elevated cmd prompt**:

    ```PUSHD "C:\ProgramData\Package Cache\FE948F0DAB52EB8CB5A740A77D8934B9E1A8E301\redist"```

    ```vs_isoshell.exe /Uninstall /Force /PromptRestart```

3. Uninstall Microsoft Visual C++ 2015 Redistributable the same way you uninstall any application. Uninstall both x86 and x64 if they're on your computer.

4. Reinstall Visual Studio 2015 IsoShell **from an elevated cmd prompt**:  

    ```PUSHD "C:\ProgramData\Package Cache\FE948F0DAB52EB8CB5A740A77D8934B9E1A8E301\redist"```  

    ```vs_isoshell.exe /PromptRestart```

5. Reinstall SSMS.

6. Upgrade to the [latest version of the Visual C++ 2015 Redistributable](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads) if you're not currently up to date.

## Additional Downloads

For a list of all SQL Server Management Studio downloads, search the [Microsoft Download Center](https://www.microsoft.com/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending).  
  
For the latest release of SQL Server Management Studio, For details, see [Download SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md).  
