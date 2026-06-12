---
title: "Can't boot Windows after Ubuntu install! [not total noob]"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Mpemba on 2008-09-16
Hello!

I have just installed Ubuntu (latest version). I used the partitioner tool to make a partition in my existing XP install. This worked fine, and am now posting from my Ubuntu install (which I love).

My other (xp) partition mounted automatically, so I copied some folders from that partition to my Ubuntu partition. 

Now when I go to load my XP it doesn't want to boot. I can see it in GRUB, but it BSOD's before the login screen. I am no longer able to automatically mount the partition in Ubuntu due to it not Windows not been shut down properly, however a force mount allows me to access the partition..

Is this clear? How can I fix this please? Sorry if this is the wrong forum. I don't want to format my XP partition, just need to boot into it. Can't boot in any mode (safe etc..!)

Kind Regards!

---

### Post by halitech on 2008-09-16
before you did the partitioning, did you reboot windows a few times and run defrag at least twice to get all the windows files to the beginning of the drive?

---

### Post by Mpemba on 2008-09-16
> **halitech said:**
> before you did the partitioning, did you reboot windows a few times and run defrag at least twice to get all the windows files to the beginning of the drive?

I did reboot a bit but did not defrag! :(

---

### Post by Tatty on 2008-09-16
It sounds like something might have got corrupted in your windows install.  Did you defrag it before you partitioned?

You might need to perform a repair of your XP machine.  Have a read of this page:

[http://www.michaelstevenstech.com/XPrepairinstall.htm](http://www.michaelstevenstech.com/XPrepairinstall.htm)

However, as always, make sure you back up all your essential data before doing this!

---

### Post by halitech on 2008-09-16
> **Mpemba said:**
> I did reboot a bit but did not defrag! :(

you probably messed up the windows install. check the link provided by Tatty and see if that helps you out any.

---

### Post by Tatty on 2008-09-16
> **Mpemba said:**
> I did reboot a bit but did not defrag! :(

You should always defrag windows before partitioning.  You should run defrag a few times (at least 3 is a good number) because the out-of-the-box windows defrag tool is pretty poor.

Chkdsk is something you should do too - but really you should run chkdsk before any degfrag anyway.

Let us know how you get on with your windows repair.

---

### Post by Mpemba on 2008-09-16
> **Tatty said:**
> It sounds like something might have got corrupted in your windows install.  Did you defrag it before you partitioned?

You might need to perform a repair of your XP machine.  Have a read of this page:

[http://www.michaelstevenstech.com/XPrepairinstall.htm](http://www.michaelstevenstech.com/XPrepairinstall.htm)

However, as always, make sure you back up all your essential data before doing this!

Yes this is what I can see being the problem. However when I put in a recovery cd, it goes through the loading of files and then BSODs. I assume the recovery CD BSOD is the same as the regular loading BSOD (although the one which flashes up on XP loading goes so quick I can't see it as the system reboots almost instantly)

---

### Post by Tatty on 2008-09-16
> **Mpemba said:**
> Yes this is what I can see being the problem. However when I put in a recovery cd, it goes through the loading of files and then BSODs. I assume the recovery CD BSOD is the same as the regular loading BSOD (although the one which flashes up on XP loading goes so quick I can't see it as the system reboots almost instantly)

Are you sure its definately loading from the CD?  Double-check your boot order (although i imagine it should be correct as you have just installed ubuntu, but its best to check).

It might be worth running a memtest from the grub menu.  If it BSOD's from both the hard drive and the CD then it suggests a possible hardware issue, and RAM is usually a good place to check first.

---

### Post by Mpemba on 2008-09-16
Basically I can't run the repair CD, the only option is a complete format of both partitions and then set it up again (though i'm tempted to just have a single boot Ubuntu).

This is not a problem as now I can mount the drive I can get my files (mp3's).

However, I have some important files which i cant access. These files are saved in the 'shared documents' folder, but this folder is a .ink folder?! How can I open this? Gah I hate MS sometimes:(

---

### Post by Mpemba on 2008-09-16
> **Tatty said:**
> Are you sure its definately loading from the CD?  Double-check your boot order (although i imagine it should be correct as you have just installed ubuntu, but its best to check).

It might be worth running a memtest from the grub menu.  If it BSOD's from both the hard drive and the CD then it suggests a possible hardware issue, and RAM is usually a good place to check first.

Would the Ubuntu install not encounter the same hardware issue?

---

### Post by PocketDog on 2008-09-16
A .lnk (link) is what Windows calls a shortcut - it links to the files which are elsewhere on the Windows  disk.

---

### Post by Mpemba on 2008-09-16
> **PocketDog said:**
> A .lnk (link) is what Windows calls a shortcut - it links to the files which are elsewhere on the Windows  disk.

do you happen to know where 'My Sharing Folder.lnk' points to by default?

---

### Post by Tatty on 2008-09-16
> **Mpemba said:**
> Would the Ubuntu install not encounter the same hardware issue?

Im not an expert on this, but I think the answer to that is that it may or may not.  It may just be that the windows executable tries to load into a certain part of the memory which is damaged.

Either way checking your hardware just seems like the next logical step.

If your Windows install CD crashes then unfortunately a re-install isnt going to be an option, as you cannot load the installer ;) Is it definately a classic BSOD you are seeing with the CD?

---

### Post by ajsinclair on 2008-09-17
I have the same problem under the same circumstances... up until the Windows CD attempted repair.  When I used the Windows CD, I got past the BSOD, but the Windows installer claimed not to recognize the OS on the partition (windows on 1, Ubuntu on 2).  Then when I restarted, Grub is gone so I can't get back into Ubuntu.  I decided to use the Windows CD to reinstall over the original install (keeping the 2 partitions for now).  It looks like Windows is working again.

---

