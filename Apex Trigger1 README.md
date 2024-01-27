trigger AccountTrigger on Account (before insert, before update) {
    // This trigger runs before records are inserted or updated

    // List to store records that need to be updated
    List<Account> accountsToUpdate = new List<Account>();

    // Iterate through the incoming records
    for (Account acc : Trigger.new) {
        // Perform your custom logic here
        // For demonstration purposes, let's say we want to set a custom field based on a condition
        if (acc.Industry == 'Technology') {
            acc.CustomField__c = 'Tech Industry';
        } else {
            acc.CustomField__c = 'Other Industry';
        }

        // Add the record to the list for update
        accountsToUpdate.add(acc);
    }

    // Update the records with the custom field value
    update accountsToUpdate;
}
