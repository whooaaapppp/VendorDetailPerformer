# VendorDetailPerformer

UiPath Automation Using REFrameWork Exercise

Here are the steps performed by the Robot:
1. Log in to https://www.acme-test.com.
2. On the landing page, Dashboard, click or hover over the Vendors menu item and then click on Search for Vendor. Click on Display All Vendors. Scrape the data from the whole table displayed. The resulting datatable will be used as the input data for the process. Navigate back to the dashboard.
3. For each Tax ID:
- Navigate to Vendors - Search page (click or hover over the Vendors menu item and then click on Search for Vendor);
- Type the Tax ID into the Vendor Tax ID field;
- Click on Search;
- Extract the values for the Address, City and Country and compare them with the values from the previously extracted table from the Display All Vendors page (check for EXACT match for all fields!);
- If the values are not matching, this should be categorized as a Business Rule Exception;
- If the City does NOT belong to the group {""Koln"", ""Lyon"", ""Torino"", ""Rimini"", ""Brasov""}, this should be categorized as the second Business Rule Exception. We can only process requests from these cities. Check the City value extracted after the individual Tax ID search;
- If no Business Rule Exception, Append the resulting datatable from each page into an Excel worksheet; you shouldn't worry about the headers and format of the output file.

Limitations:
1. TransactionItem datatype should be a DataRow. The process should recover and retry 2 times in case of errors in navigation between the Vendor Search and Vendor Search Results pages. One transaction is the action of navigating to the Vendor Search page, searching for the TaxID and scraping the values from the resulting one row table. (Similar to ACME Process 5 from the UiPath Academy). 
2. Create a separate workflow file for the Login to ACME. File input arguments: URL ; Username ; Password .
3. Create a separate workflow file for closing ACME. 
4. Add the ACME_URL and ACME_Credential to the Excel Config file.
5. Populate InitAllApplications.xaml from the Framework folder with Invoking the Login to ACME and navigation to the Work Items.
6. Populate CloseAllApplications.xaml from the Framework folder with Invoking the Close ACME.
7. Populate KillAllProcesses.xaml from the Framework folder with killing the process used.
8. Populate the Process.xaml file with the following actions: Navigation, Searching for TaxID, Scraping, Checking if the values match, Checking for the correct City, Appending to Excel.
