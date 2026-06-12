---
title: "clean install but grub didnt detect my xp install."
date: 2008-04-24
forum: New to Ubuntu
---

### Post by lordrick112 on 2008-04-24
Hello.

I have 2 hdd on my com here.
I first installed XP on my slave hdd, then installed xubuntu 8.04 on my primary hdd.

Everything went fine but upon reboot grub didn't detect my xp install on my slave.

Grub was installed to my primary hdd.

How do i get my XP back?

Here is a list of my partitions:

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8c3e8c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2373    19061091   83  Linux
/dev/sda2            2374        2482      875542+   5  Extended
/dev/sda5            2374        2482      875511   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b5861bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         178     1429753+   7  HPFS/NTFS  <-- Swap Partition for xp
/dev/sdb2             179       19456   154850535    f  W95 Ext'd (LBA)
/dev/sdb5             179       19456   154850503+   7  HPFS/NTFS  <-- Install Partiton for XP

Would a reinstall of grub fix my problems? Or should I install grub on my slave hdd?

If possible, do explain in "noob" terms. :)

Many thanks for the reply's.

---

### Post by Xiong Chiamiov on 2008-04-24
Add this to the bottom of your grub menu (/boot/grub/menu.lst):
```

title		Windows NT/2000/XP (loader)
root		(hd1,0)
#savedefault
makeactive
chainloader	+1

```
assuming that the first partition on your 2nd hard drive is the one where Windows is installed.  If not, you'll have to change the 2nd number in (hd1,0) to be the partition number -1.

---

### Post by lordrick112 on 2008-04-24
OK, this is what happened.

I edited the menu.lst and added the code you suggested.

title		Windows NT/2000/XP (loader)
root		(hd1,0)
#savedefault
makeactive
chainloader	+1

It hung @ "Starting up..."

That didn't work. :(

So I changed the "(hd1,0)" into "(hd1,1)".
and I got..

"Error 12: Invalid Device requested".

I even went into the BIOS and changed my boot configuration to boot from my slave expecting XP to boot but it hung there as well.

So I changed my BIOS again so I can get back into xubuntu here.

Am stumped @ the moment...

any suggestions anyone???

Many thanks in advance!!

---

### Post by zvacet on 2008-04-24
title Windows NT/2000/XP (loader)
root (hd1,0)
makeactive
map (hd0) (hd1)
 map (hd1) (hd0)
chainloader +1

---

### Post by lordrick112 on 2008-04-24
Thanks for the many quick responses!

OK, here we go again.

Deleted the following from my menu.lst

title		Windows NT/2000/XP (loader)
root		(hd1,0)
#savedefault
makeactive
chainloader	+1

Added the following to the menu.lst

title Windows NT/2000/XP (loader)
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

and got...

"NTLDR is missing"
"Press Ctrl+Alt+Del to restart"

Somewhat frustrating now. :lolflag:

I would imagine it would be easier if I just swapped the two HDDs,
making my 160.0GB HDD the primary and the 20.4 GB HDD the slave.

But I don't want to sit through installing both OS's again. :mad:

Thanks again for your time and wisdom! \\:D/

---

### Post by zvacet on 2008-04-24
I hope [this]("http://tinyempire.com/notes/ntldrismissing.htm") will help you.

---

### Post by lordrick112 on 2008-04-24
Thanks for the suggestion but it didn't work.

I burned the xpnt4lix.img but it wouldn't boot.

Am going to try to reinstall grub, ill post back anything if it works or fails.

---

### Post by lordrick112 on 2008-04-24
That didn't work also...
downloading the final realease now :D

Am going to swap HDDs, i gotta feeling that will work.

reinstall joyness!!!

thanks for everyones help!

---

