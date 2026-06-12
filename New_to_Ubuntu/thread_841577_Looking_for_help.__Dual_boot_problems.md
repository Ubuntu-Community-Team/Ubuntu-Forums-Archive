---
title: "Looking for help.  Dual boot problems"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by cashel32 on 2008-06-26
Hello folks!

Brand new here and to ubuntu!

I have set up my computer to dual boot windows and ubuntu server.  I have done this before by partitioning a single HDD and I have been successful.  This time I added a second HDD to my computer.  One is the original SATA with Windows XP installed (changed nothing).  The other is an IDE with ubuntu installed.  The IDE jumper is set to master.  Ubuntu boots fine.  

The GRUB loads fine.  When I try to boot windows I get, "Error 12: Invalid Device Selected."  

I am selecting the SATA drive from the boot manager. The grub is installed on the IDE drive. Here is the result of fdisk -l and menu.lst.

_fdisk -l:_
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       18945   152127517+   7  HPFS/NTFS
/dev/sda3           18946       19452     4072477+  db  CP/M / CTOS / ...

Disk /dev/sdb: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3937    31623921   83  Linux
/dev/sdb2            3938        4111     1397655    5  Extended
/dev/sdb5            3938        4111     1397623+  82  Linux swap / Solari

_Menu.lst:_

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-17-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-17-server root=UUID=b5e6c29b-fdb9-4175-852d-b4ebd684fd3c ro quiet splash
initrd          /boot/initrd.img-2.6.20-17-server
quiet
savedefault

title           Ubuntu, kernel 2.6.20-17-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-17-server root=UUID=b5e6c29b-fdb9-4175-852d-b4ebd684fd3c ro single
initrd          /boot/initrd.img-2.6.20-17-server

title           Ubuntu, kernel 2.6.20-15-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-server root=UUID=b5e6c29b-fdb9-4175-852d-b4ebd684fd3c ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-server
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-server root=UUID=b5e6c29b-fdb9-4175-852d-b4ebd684fd3c ro single
initrd          /boot/initrd.img-2.6.20-15-server

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title           Microsoft Windows XP Professional
rootnoverify            (hd1,1)
savedefault
# makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1



I have been googling my **** off to no avail.  If there is a post already up that can help please point me in that direction as I have had no luck thus far on an answer.  The real funny thing is it worked for a while.  I can't seem to tell what changed.:mad:

Thank you in advance for your help!!

---

### Post by pytheas22 on 2008-06-26
Where is Windows on the first drive--i.e. is it on the first partition, second...?  Do you have any other operating systems installed anywhere?

By the way, is there a reason you chose Ubuntu server instead of the desktop edition?

---

### Post by cashel32 on 2008-06-26
Windows is on /dev/sda2.  I verified this by mounting the drive and looking at the windows files.  No other operating systems are involved.

As far as the reason for ubuntu server.  It is what we had lying around at work.  I am using it to manage an ldap database on one of our servers.  All of that works just fine.

---

### Post by bumanie on 2008-06-26
Your /boot/grub/menu.lst looks very mucked up. All the entries for ubuntu should be (hd1,0) and the windows drive should be (hd0,1). It would also be best to uncomment #makeactive ( in the windows entry), by removing #. Sometimes mixing sata and ide drives can confuse grub, but the map commands that have been entered should take care of that.
To edit the list > gksudo gedit /boot/grub/menu.lst and manually remove the # from makeactive, also change the (hdx,x) entries to those noted above. Hopefully that will sort everything out.

---

### Post by cashel32 on 2008-06-26
I made the recommended changes.  The good news is no more error!! :)

The bad news is now it says "Starting Up..." and does nothing else when I try to boot windows.  When I tried to boot linux it gave me an error (Error 17:  Cannot Mount the Selected Partition).  I changed the GRUB so linux is back on (hd0,0) and it is working again.  

I feel like progress is being made though.  I am finally rid of that stupid error! Thanks!

---

### Post by cashel32 on 2008-06-27
After research, enormous amounts of coffee, and several colorful words, I believe I have found the problem.  The GRUB was not installed on the IDE drive like I originally suspected.  It was installed on the SATA drive because it contained the master boot record.  Linux playing in windows land mucked up this master boot record.  Now windows doesn't work because it is no longer on (hd0,0)...I guess.

So the fix is to reinstall both, one at a time, with the other HDD off or physically unplugged while installing.  No master boot record, none of that.  I am going to use the bios to manually select the boot HDD.  This should work and will still allow me to mount the widows drive from linux without issues.  I will post the results of my attempt shortly.

If any one has any input to offer or a better reason I want to hear it.  Also if there is another, easier fix than the one I am trying I want to know that too.  Thanks to the folks that gave me some input!

[CENTER]*********[SIZE="5"]Warning!![/SIZE]***********[/CENTER]
When installing on separate drives, install Windows first, to the main drive.  When you install Linux, DO NOT install the GRUB to the master boot record.  Leave them totally separate.  Windows and Linux don't play nice.

---

### Post by bumanie on 2008-06-27
Your last point is not very accurate. I have set up many dual boot systems and had grub work well with wndows 90% of the time. The few, times it didn't work was tracked back to bios issues form some bios' made 6-7years ago. You should be able to reinstall grub and chainload windows. Changing bios each time should work Ok,, but I would try below method first and see if it fixes things.  Boot live cd  and reinstall grub. the terminal codes should be 
> sudo grub > root (hd1,0)> setup (hd0,1)> quit If this doesn't work you could try super grub disk that often cures grub problems - but it could be the issue of mixing a sata with an ide and may be the age of your bios.

---

### Post by Duck2006 on 2008-06-27
Some info on grub that may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by cashel32 on 2008-06-30
I changed the GRUB.  When I went to boot ubuntu I got the same Error 17 that I got before.  When I tried to boot Windows I got the "Starting up..." then directly underneath it says GRUB.  Then does nothing.  You are right about Windows and Linux being fine 90% of the time :) I was just angry at the time.  Something strange going on here though.

---

### Post by bumanie on 2008-06-30
Can you boot live cd and post output of > sudo fdisk -l Also, are your hard drive jumpers set correctly? This is what Herman (see link above) says about error 17 and mixed ide/sata drives.
Mixed IDE and SATA hard disks
Error 17 also commonly occurs when we have a mixture of IDE and SCSI or SATA hard drives plugged into the same motherboard.
Try switching the 'Hard Disk Boot  Priority' around in your BIOS. 
Note that 'Hard Disk Boot  Priority' is something different from 'Changing the boot sequence', but all computers are different, so it's hard to give exact information that will suit everyone.
Here's a series of illustrations showing how I do mine, Changing the hard Disk Boot Priority.
For some computers that's the fastest, easiest and best solution and no time consuming editing of files is necessary when the problem can be solved that way. 
That method worked for NavyRST in the following thread: HOW-TO install boot loader from Ubuntu.
That solution will be fine for most computers, and it's well worth a try before resorting to editing configuration files and re-installing GRUB.
Make sure your hard disks are properly detected in your BIOS too, and set to AUTO, (not LBA, large or normal). You could try super grub disk. 
With the bios issue I mentioned last time, that's the only way I could boot into ubuntu - dual booting off one hard drive worked fine with that computer, by the way.
Also wonder whether your windows mbr is OK or whether it's been corrupted. Suspect it is probably a combination of bios issues with the mixed ide/sata hard drives - could be wrong however. 
Here's the approriate section of Herman's grub page [http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by cashel32 on 2008-06-30
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       18945   152127517+   7  HPFS/NTFS
/dev/sda3           18946       19452     4072477+  db  CP/M / CTOS / ...

Disk /dev/sdb: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3937    31623921   83  Linux
/dev/sdb2            3938        4111     1397655    5  Extended
/dev/sdb5            3938        4111     1397623+  82  Linux swap / Solaris
calen@sheltonpc:~$


that is the output from sudo fdisk -l 
I will also play with the bios and see what I can do.  Thanks for all the help.

---

### Post by bumanie on 2008-06-30
Sorry should have asked for /boot/grub/menu.lst As you can't boot into ubuntu at present, you should be able to get a static list from the live cd by opening filesytem and opening boot --> grub and finding the menu.lst Copy and paste it if able to find. Does your windows drive boot if ubutnu drive is unplugged? This will give an indication on whether the windows mbr is OK or not.

---

### Post by cashel32 on 2008-06-30
> (hd0)   /dev/sda
        (hd1)   /dev/sdb
That is the output from cat /boot/grub/device.map It seems to be right in line with the fdisk -l output which shows the windows partition on /dev/sdb2.  Should I change the** (hd1,1)** to (hd1,2)?

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title           Microsoft Windows XP Professional
rootnoverify            **(hd1,1)**
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by bumanie on 2008-06-30
> That is the output from cat /boot/grub/device.map It seems to be right in line with the fdisk -l output which shows the windows partition on /dev/sdb2. Should I change the (hd1,1) to (hd1,2)?

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title Microsoft Windows XP Professional
rootnoverify (hd1,1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
Windows should be (hd0,1) Dell's restore partition is on (hd0,0) and windows is on (hd0,1). The windows partition is sda2, not sdb2 according to the original fdisk -l and the one you just posted (unless  bios changes altered anything, but bios changes should not change the /boot/grub/menu.lst).
(hd1,1) is the extended partition on the second drive. Need to try to reinstall grub again from the live cd. At the moment grub is looking for windows on the second hard disk and finds ubuntu, that's why  it is giving error 17 it is looking for an ntfs filesystem, not the ext3 filesystem it is finding. Redo the steps I posted 3 days ago about installing grub - it should work. If it doesn't, post output of > sudo grub> find /boot/grub/stage1

---

### Post by cashel32 on 2008-06-30
re-installed the grub.  Then changed windows to (hd0,1)  still no worky.  

 The result of the change you suggested was the "Starting up..." with "GRUB" underneath.  Then it hangs and won't do anything.  I do see windows showing on sda2 and (hd0) listed as containing sda2.  That is what is strange, Linux has been running just fine this whole time booting off the IDE hdd.  Menu.lst has (hd0,0) listed next to it.  I haven't modified the BIOS nor have I modified the device.map file.  So I guess I understand why Windows DOESN'T work alot more than I understand why Linux DOES.
Output from find /boot/grub/stage1: (hd1,0)

---

### Post by bumanie on 2008-06-30
Sorry, I can't be of more help, as said, an old computer I had, did this with two hard drives, but dual booted fine with one hard drive. I would try super grub disk and see if it can fix things or at least allow you to boot. Grub seems to be in the right place, windows is (hd0,1) - why it doesn't work, I can't tell; needs someone more expert than me to fix the issue. I know sometimes people have had success changing the boot order in bios as suggested on Herman's grub page. Good Luck, but it may just come down to some type of bios incompatability and the mixed ide/sata drives.

---

### Post by cashel32 on 2008-06-30
I think your probably right on the whole compatibility thing.  There are many linux experts around the office and they all seem to be just as perplexed as we are.  Thank you very much for your help.  I am going to take the last resort and bring everything down and start from scratch.  Hopefully I will have more luck!

---

