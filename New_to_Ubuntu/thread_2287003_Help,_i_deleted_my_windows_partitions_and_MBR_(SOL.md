---
title: "Help, i deleted my windows partitions and MBR (SOLVED)"
date: 2015-07-16
forum: New to Ubuntu
---

### Post by phill3 on 2015-07-16
Install seemed to go well, was having issues with partitions so i followed some advice and 

sudo gdisk /dev/sda
x - exprtt
z- zap GPT data
y - yes
n - no about blanking mbr

now i have no os 

ran boot-repair 

[http://paste.ubuntu.com/11886818/](http://paste.ubuntu.com/11886818/)

any assistance would be greatly appreciated

---

### Post by stalkingwolf on 2015-07-16
what are the specs of the computer? what version of windows?

---

### Post by oldfred on 2015-07-16
What advice was it to erase entire drive? That should almost never be done.
That is what you did with the zap command in gdisk. It removed all gpt partitions. And Windows 8 in UEFI mode only boots from gpt.
You might want to totally repartition if you had purchased another copy and really wanted to revert to the 35 year old BIOS/MBR. But that is a total reinstall.

I might try testdisk. If you have done nothing else to drive it may find & recover partitions. But Windows has a system reserved partition that is unformatted & that often is not found. And then Windows partition is at wrong place on drive. And then only may be repairable.

Do you have a backup copy of partition table before you started? Or even a hard copy printout?
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

    
Be sure to choose gpt
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by phill3 on 2015-07-17
Solution to problem was to create a windows 8.1 restore flash drive from a friends windows 8.1 without copying the boot sector
That allowed windows to boot again.
Next i needed to load Ubuntu open a terminal and then 

[COLOR=#000000]sudo parted -l[/COLOR]
[COLOR=#000000]sudo fdisk -lu   

([/COLOR]http://ubuntuforums.org/showthread.php?t=2223958)

[COLOR=#000000]had to repair partitions and move bits to the start etc.
Funny thing is was all meant to be on a virtual machine lol , least i have it for real now

Thankyou all for help and advice.

[/COLOR]

---

