---
title: "removing the dual boot up"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by csapty1 on 2013-02-25
hey 
after installing Ubuntu onto my PC, I eventually thought I could get rid of it completely by uninstalling it.
so I downloaded Easy BCD and looked up how to do it, great! but even after using it, I still get the dual boot up screen and when I click on Ubuntu, im getting this message
 
"Windows Failed to start. A recent hardware or software change might be the cause. To fix the problem:

[LIST=1]
[*]Insert your windows installation disc and restart your computer.
[*]Choose your language settings, and then click "next."
[*]Click "Repair your computer."
[/LIST]If you do not have this disc, contact your system administrator or computer manufacturer for assistance.
 
File: \ubuntu\winboot\wubildr.mbr
 
status: 0xc000000e
 
Info: The selected entry could not be loaded because the application is missing or corrupt."
 
after using Easy BCD and deleting the partition for it and assumed it was then completely gone, but im still getting this message
 
this may be a stupid question but if i were to install a current version of Ubuntu, would this problem stop? because i want to start using it again, but am unable.:confused::confused:
 
thanks

---

### Post by rcayea on 2013-02-25
A bit more info might help someone help you. Do you mean, if you reinstall with WUBI or do you mean reinstall as in actually partioning your hard drive?

---

### Post by csapty1 on 2013-02-25
> **rcayea said:**
> A bit more info might help someone help you. Do you mean, if you reinstall with WUBI or do you mean reinstall as in actually partioning your hard drive?
 
would using WUBI be more advisable? because ive started to download Ubuntu 12.10  as of now using WUBI...?

---

### Post by Mark Phelps on 2013-02-25
> **csapty1 said:**
> ...after using Easy BCD and deleting the partition for it and assumed it was then completely gone, but im still getting this message

Wubi does NOT install to a Linux filesystem partition, but instead, to a file INSIDE an existing Windows partition -- usually the "C:" partition.

If you installed Ubuntu to that partition, and then deleted it, you deleted Windows.

You should boot into Ubuntu using a LiveCD, select Try Ubuntu, and when the desktop comes up, use the "home" icon on the left to launch a file browser and look at the Windows partitions to see of the files are still there.

---

### Post by csapty1 on 2013-02-25
[QUOTE=If you installed Ubuntu to that partition, and then deleted it, you deleted Windows. [/QUOTE]
 
originally I created a new partition and did it from there to make sure I didn't delete Windows, which I haven't
once the download has finished, ill try what you've said and go from there
would it be worth creating a new partition again and putting Ubuntu into there instead to make sure I haven't deleted Windows ?

---

### Post by pfeiffep on 2013-02-25
> **csapty1 said:**
> originally I created a new partition and did it from there to make sure I didn't delete Windows, which I haven't
once the download has finished, ill try what you've said and go from there
would it be worth creating a new partition again and putting Ubuntu into there instead to make sure I haven't deleted Windows ?

So what is your endpoint?
Windows only?
Ubuntu only?
Both?

If both I'm not certain how you would access both without a dual boot

---

### Post by csapty1 on 2013-02-25
ill re rexplain it because agreed, ive made it confusing
 
okay, instead of trying to make life much more complicated for myself
ill ask:
how can I simply remove the dual boot and just use Windows? ive used Easy BCD and the program says its worked and been deleted
I no longer have the Ubuntu partition either 
so when I click on Ubuntu, I get that same error message each time
 
how can I completely remove the dual boot and just stick to windows?

---

### Post by Mark Phelps on 2013-02-26
It's confusing because you're mixing contradictory information ...

Wubi does NOT create a partition; instead, it installs INSIDE an existing Windows partition.  To remove a Wubi install, you go into Programs and Features (inside Control Panel in Windows) and remove the Ubuntu "program".  That will remove the Ubuntu virtual filesystem file (root.disk) and remove the entry from the BCD (in Win7).

If you installed Wubi to a different partition and only deleted that partition, that will NOT remove the Application launch information from the registry, nor will it remove the entry from the BCD.

You should go into Programs and Features, see if "Ubuntu" is still there and attempt to remove it.

Also, if there is still an Ubuntu entry in the BCD, then it was not removed properly using EasyBCD.

If these don't work, then you may be looking at a clean-reinstall of Windows -- and to do that, you REALLY need to go to a Win7 forum and ask there -- recommend Sevenforums.com.

---

