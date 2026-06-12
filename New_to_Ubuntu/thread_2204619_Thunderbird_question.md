---
title: "Thunderbird question"
date: 2014-02-09
forum: New to Ubuntu
---

### Post by mlvmhn on 2014-02-09
I am using TB as my default mail client. i have added my Gmail account to TB. 
Whenever i am recieving a new mail, it also lands in my "All mail" and "Important" folders. 
If i mark or read the mail in my "Inbox" folder, 2 copies of the mail also lands in these other 2 folders.
This means that if i read the mail, i still have 2 unread mails in these other folders.
 
How do i learn TB just to recieve mail in just one folder?

---

### Post by speartip on 2014-02-09
This has nothing to do with Thunderbird. It is your Gmail settings you need to change.
Log into your gmail account, click the settings cog, then settings again, go to "labels" & untick  the "show in imap" boxes on the right hand side that you do not want to appear in Thunderbird. In your case untick the "important" & "all mail" boxes, then restart Thunderbird.

---

### Post by Vladlenin5000 on 2014-02-09
Thanks :p

Simple and very informative. Indeed, TB only shows what the IMAP server tells it to show.

---

### Post by mlvmhn on 2014-02-09
Cool, now it is working. 

Another question; how do i learn TB to get a certain kind of mails in the same folder all the time?

---

### Post by Bill Tetzeli on 2014-02-09
> **mikael.hansson.967 said:**
> Cool, now it is working. 

Another question; how do i learn TB to get a certain kind of mails in the same folder all the time?

Tools > Message Filters

Click "New" in the box that pops up, give the filter a name, tell it to filter messages either by a certain subject heading, sender, etc., whatever other parameters you want to set, then under "Perform these actions" choose "Move Message to" from the first dropdown box and select the folder you want it to go to from the second.  Click OK, close the filters box and you're all set.  You can also make a filter retroactive by selecting Tools > Run Filters on Folder, but use with caution.  There may be some older email that triggers the filter that you don't want moved.

---

### Post by G_Ajith_Kumar on 2014-02-09
Hi, I had a similar problem with TB like mikael. I have now reconfigured GMail labels/folders and it is working well now. Thank you!!!!!!!!!!!!!!!

---

