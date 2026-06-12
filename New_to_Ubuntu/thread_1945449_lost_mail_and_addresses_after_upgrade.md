---
title: "lost mail and addresses after upgrade"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by kenmac2 on 2012-03-23
Hi,
I have just completed the upgrade to the latest version of Ubuntu.
It seems to have completed successfully (after a few hours) but Thunderbird no longer holds any messages or addresses.
Is there some way that this data can be recovered?

Help!

kenmac2

---

### Post by codemaniac on 2012-03-23
Thunderbird stores all personal information such as messages, address books and configuration settings in a folder called the profile.
check in the below locations .
```

~/.thunderbird/<Profile name>/
~/.mozilla-thunderbird<Profile name>

```

---

### Post by kenmac2 on 2012-03-23
OK, I found a Profile folder.
It contains a couple of .rpt files - it's probably the new  versions.
Where would the original data be stored?

I don't know much about Ubuntu file system.

kenmac2

---

### Post by codemaniac on 2012-03-23
All of the messages for an account are stored in a subdirectory named after the mail server. For example if you have a Gmail POP account it would create a pop.gmail.com subdirectory in Mail. Your messages would be stored in text files with the folders name and no file extension called mbox files. For example, the inbox folder would be called "Inbox.". There would also be a inbox.msf file (a index file, it doesn't have any messages) and there might be a inbox.sbd subdirectory. The .sbd subdirectories are used to store the folders in a hierarchy, there is no master list describing how the folders should be organized.

---

### Post by kenmac2 on 2012-03-24
In the Thunderbird directory is a directory called "Removed Files".
This would have been created after the last update of Ubuntu I think.
On the list  is "defaults/profile/US/localstore.rdf" and "defaults/profile/US/mimeTypes.rdf"
I assume these contain the original data.
The problem is, how to put that back as the default?

kenmac2

---

### Post by kenmac2 on 2012-03-24
Hmmm, the fact that they have listed all "removed" files probably means they have been deleted.
In which case I have lost hundreds of messages and  addresses!
Maybe those two files should have been "saved" prior to any update activity.

kenmac2

---

