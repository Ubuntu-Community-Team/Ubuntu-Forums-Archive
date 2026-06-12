---
title: "ERROR While installing Ubuntu inside Win7"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by eng-a-hesham on 2011-10-14
Hi, while installing Ubuntu inside Win7 using "Wubi" and running it as admin. a message including the following shows up and the installation stops:
------------------------------------------------------------------------------------------------
 Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {44f91797-76cb-11e0-a5f5-db09947f7df8} device partition=B:
>>retval=1
>>stderr=An error occurred setting the element data. The request is not supported.
>>stdout=

For more information,please see the log file:
c:\users\abdelr~2\appdata\local\temp\wubi-9.04-rev128.log
------------------------------------------------------------------------------------------------

N.B: this error occurred with 10.04 11.04 and 9.04 !! :(

---

### Post by bcbc on 2011-10-14
This is not actually a wubi error - it just doesn't 'dress it up' in a user friendly way. It's windows rejecting the attempt to boot from a specific 'drive' - and it usually does this if you have dynamic disks set up and the 'drive' you installed to is not physically in the partition table.

If you have dynamic disks, don't install Ubuntu either with wubi or direct as Linux does not recognize the dynamic partitions and so you could end up losing data.

Unfortunately Win 7 allows you to easily switch to dynamic disks, but doesn't allow you to switch back. But that's what you should do.

---

