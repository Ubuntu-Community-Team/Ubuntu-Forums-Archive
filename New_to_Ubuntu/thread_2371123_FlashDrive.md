---
title: "FlashDrive"
date: 2017-09-11
forum: New to Ubuntu
---

### Post by iblueflash on 2017-09-11
hello ,so i have a flashdrive ,I plugd-in my pc.
I start to reformat it and I plugd-out before it was done and now my flashdrive don't work.It work's before I start reformating , now I plugd -in and nothing happend.

my pc don't see the flashdrive and the same problem appears to my phone now

---

### Post by sudodus on 2017-09-11
Are there valuable data on the flashdrive? If yes, try to repair it, otherwise create a new partition table and file system.

What file system is there on the flashdrive?

If the 'standard file system', it is best to repair it in Windows, because it is probably FAT32 or exFAT.

See this link with more details,

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by mrgnome on 2017-09-11
If there wasn't valuble stuff on the drive, then you should reformat it and regenerate the partition table. To do this, open Disks and press Shift+Crtl+F to format the disk, then create a new partition by clicking the cog and clicking "Create partition image..." If you're planning to use it with other computers, I recommend using exFAT. Otherwise, use ext4.

If there is good stuff on there, do what the other guy said and use [URL=[URL="http://[URL=&quot;http://[URL=&quot;http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986&quot;&quot;"]http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986] for instructions on recovering your drive
[/URL][URL="http://[URL=&quot;http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986&quot;"]

 
[/URL]

---

### Post by iblueflash on 2017-09-12
thanks

---

### Post by radioactive.exe on 2017-09-18
I'd recommend using fdisk, the CLI way of formatting your flash drive. From my own experience, I've found gui based formatting to sometimes not work (I have no idea why), but fdisk has never failed me, despite me having very limited experience with it.

---

