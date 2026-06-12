---
title: "HOWTO: Gmail in Thunderbird"
date: 2006-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2006-06-25
Hi,
    Again this is a bit I copied from some site, with a few small changes for the latest versions. All credit goes to the unknown author:

_Howto Gmail in Thunderbird_
Create a new account in Thunderbird/Mozilla Suite
Open Thunderbird or Mozilla Suite Mail, go to "Tools -> Account Settings" (or for Mozilla Suite: "Edit -> Mail & Newsgroup Account Settings"), click the "Add Account" button, select "Email Account" and click "Next". 
Enter your name in the "Your Name:" field, and enter your entire Gmail address (yourname@gmail.com) in the "Email Address:" field. Click the "Next" button. 
Select "POP" as the account type and enter pop.gmail.com in the "Incoming Server" field. If you don't want your Gmail messages to be stored in Local Folders, unselect "Use Global Inbox (Store Mail in Local Folders)". Click the "Next" button. 
Enter your entire Gmail address (yourname@gmail.com) in the "Incoming User Name:" field. Click the "Next" button. 
Enter a name (such as "Gmail") for your Gmail account in the "Account Name:" field, click the "Next" button and then the "Finish" button. There will now be new account showing in "Account Settings" called "Gmail" or whatever you named it. 

Add additional account settings
Still in "Account Settings", click on "Server Settings" (under "Gmail" in the left panel) and select the checkbox for "Use Secure Connection (SSL)". Optionally, also select the checkbox for "Check for new messages every 10 minutes". Don't select anything else. 
Next, click on "Outgoing Server (SMTP)" in the left panel (you may need to scroll down), click the "Add" button. 
In the "Server Name" field write smtp.gmail.com. The "Use name and password" box must be selected. In the "User Name" field enter your entire Gmail address (yourname@gmail.com). Under "Use Secure Connection" select SSL. After selecting SSL, the port number will automatically change from 25 to 465. This is correct! Now click "OK". (Note: for all Gmail accounts SSL should be used!) 
Go back to "Server Settings" under "Gmail", click the "Advanced" button and  select "Inbox for this server's account". Click the "OK" button. Close Thunderbird/Mozilla Suite and restart the application. 

Enable POP in Gmail
You also need to perform one last step: log in to your Gmail account using the web interface and enable POP for the account. After logging into your Gmail account, click on "Settings -> Forwarding and POP -> POP Download:" and choose either "Enable POP for all mail (even mail that's already been downloaded)" or "Enable POP only for mail that arrives from now on". (Either option you choose that fits your needs will work here.) Finally, click the "Save Changes" button. 

Send a test message
Try to send and receive e-mail messages in Thunderbird/Mozilla Suite using the Gmail account. Thunderbird and Mozilla Suite mail will ask for your Gmail password twice, once when you send, then again when you receive e-mail. You should enter the password correctly both times when prompted. If desired, select "Use Password Manager to remember this password" so that it won't ask for your password the next time you send and receive e-mail. To protect your privacy, you can instead leave the "Use Password Manager to remember this password" un-checked if someone other than yourself may have access to your e-mail client. 
That is all. Now you can send and receive Gmail messages in Thunderbird/Mozilla Suite mail while online and read the messages when you are offline. 

Troubleshooting and Gmail quirks
If you send a message from your Gmail account to the same Gmail account in Thunderbird/Mozilla Suite, that message will not be downloaded into Thunderbird/Mozilla Suite. The message will, however, appear in your Gmail Inbox if you log into you account using the Gmail web interface. This is not a bug in Thunderbird/Mozilla Suite; it is a quirk in the way Gmail implements POP. 
Gmail's SMTP server ignores whatever "From:" address you might specify using multiple identity support unless you add it in the Gmail web page at Setting -> Accounts -> "Add another email address". 
If Thunderbird is refusing to use the correct outgoing (SMTP) server, see the "Troubleshooting" section in this article.

---

### Post by trbloomer on 2006-08-02
Thanks for this I keep forgetting about the port 465 in the smtp setup. The other online guides say a different port is correct.

---

