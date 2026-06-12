---
title: "Help booting XP with grub from my External Harddrive"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by KuroYoma on 2008-06-17
I had Windows Xp installed on my laptop.  I used Casoer 5.0 to move my c:\ partition to my External Harddrive.  Then i installed ubuntu on my laptop and i am wondering if i can add my old windows xp on the external harddrive to grubs boot list.

---

### Post by Ptero-4 on 2008-06-17
You may try using fixmbr and fixboot on the external HD and then boot from it using the BIOS boot menu.

---

### Post by KuroYoma on 2008-06-17
I am sorry but what is fixmbr or fixboot and how do i use them.  I have tried using the boot menu to boot from external HD but without the correct boot path i know it won't work.

---

### Post by logos34 on 2008-06-17
> **KuroYoma said:**
>  i am wondering if i can add my old windows xp on the external harddrive to grubs boot list.

One way to boot windows on the usb is to do as Ptero-4 suggested.  But if you want to boot it from grub, you'll need to add an XP entry to /boot/grub/menu.lst [with mapping]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

---

### Post by KuroYoma on 2008-06-17
But what i need is a more indepth description of Ptero-4's suggestion.

Don't want to step on toes and i apoligize profusly if i do but thats is why i went with the "Absolute Beginner Talk" section.

---

### Post by logos34 on 2008-06-17
> **KuroYoma said:**
> But what i need is a more indepth description of Ptero-4's suggestion.

Don't want to step on toes and i apoligize profusly if i do but thats is why i went with the "Absolute Beginner Talk" section.

Boot into the recovery console on the windows install cd and run **fixboot c:**
and **fixmbr**.

Or use **Super Grub Disk**.

---

### Post by KuroYoma on 2008-06-17
Ok i have tried the Super Grub Disk and i didn't work.  
But let me thank you for telling me, this is a great tool to have.
With the disk i have discovered that not all the needed information has not been presented.
I am on a Dell Laptop, with a 40 gig internal HD with ubuntu OS.  I have an external 500gig HD with a "Casper 5.0" HD copy on the 2nd partition.  I have tried the modifing the grub list, and the Super Grub Disk with no prevail.  Now knowing that the windows is on the second partition will the windows xp disc fixmbr work or is there anything else that will work.

I apologize for being repetetive but i want to make sure i do everything right.  Also thank you so much for all your help.

---

### Post by logos34 on 2008-06-17
> **KuroYoma said:**
> I am on a Dell Laptop, with a 40 gig internal HD with ubuntu OS.  I have an external 500gig HD with a "Casper 5.0" HD copy on the 2nd partition.  I have **tried the modifing the grub list**, and the Super Grub Disk with no prevail.  Now knowing that the **windows is on the second partition will the windows xp disc fixmbr** work or is there anything else that will work.

Post the exact entry you tried on the grub menu.lst.

If windows was in the usual place (1st partition) on the internal before you cloned it to the 2nd on the external, you'll most likely have to change **boot.ini** file to match. (i.e. change it to ...'partition (**2**)')

Post output of 

sudo fdisk -l

---

### Post by KuroYoma on 2008-06-18
title              Windows XP
rootnoverify               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

is the entry and ...

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00096851

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf87b4c9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       44619   358402086    7  HPFS/NTFS
/dev/sdb2           44620       49473    38989755    6  FAT16
/dev/sdb3           49474       60801    90992160    b  W95 FAT32

which confuses me because the windows xp partition was put on a ntfs partition but the only one listed is the biggest partition which is just main storage.

---

### Post by logos34 on 2008-06-18
> **KuroYoma said:**
> which confuses me because the windows xp partition was put on a ntfs partition but the only one listed is the biggest partition which is just main storage.

are you sure this is not it:

> /dev/sdb2 44620 49473 38989755 6 FAT16

it could be detecting the filesystem type incorrectly. (fat16 instead of ntfs).

49473 - 44620 = 4853 (that's close to size of sda - 4864 cylinders)

???

---

### Post by KuroYoma on 2008-06-18
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00096851

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf87b4c9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       44619   358402086    7  HPFS/NTFS
/dev/sdb2           44620       49473    38989755    6  FAT16
/dev/sdb3           49474       60801    90992160    7  HPFS/NTFS
root@mine:~# 

i refomated the extra unpartitioned space to ntfs with my laptops windows xp HD (the one i am trying to copy and boot from the EXT HD) so the fat16 is the only partition that WNDs XP can be on and my boot.ini on that drive says

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

---

### Post by logos34 on 2008-06-18
> **KuroYoma said:**
> which confuses me because the windows xp partition was put on a ntfs partition but the only one listed is the biggest partition which is just main storage.

...

> i refomated the extra unpartitioned space to ntfs with my laptops windows xp HD (the one i am trying to copy and boot from the EXT HD) so the fat16 is the only partition that WNDs XP can be on and my boot.ini on that drive says

Hmm...

[edit-obviously you can mount sdb2]

If sdb2 really is the windows c: system drive that you cloned (it must be), boot.ini is already correct (maybe you had a recovery/utility partition preceding it when it was still on the internal?), so make one small change to grub entry:

> title Windows XP
rootnoverify (hd1,**[COLOR="Red"]1[/COLOR]**)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

but the incorrect fs type may cause a problem.

You could try using TestDisk from within ubuntu to try to fix the partition table on sdb, and hope that allows you to boot xp

---

### Post by logos34 on 2008-06-18
Do you have XP install cd?

Because if you do try this:

-boot into recovery console and run
[B]
chkdsk /r[/B]

and then **fixboot**, followed by **fixmbr**.

Or if no xp install cd but you can manage to get as far as the xp splash logo, go into safe mode and run chkdsk there

add:

Your laptop Bios does support USB boot, right?  In other words you can change to boot order to boot from external first?  Sorry, I had to ask

---

### Post by KuroYoma on 2008-06-18
I change rootnoverify through the grub boot screen because it wasn't working to root and the splash comes up for a second and then blue screen flash and then my laptop reboots.  When i change the file permanently with the OS loaded and then reboot and select Windows XP, i get "Error 5: Partition table invalid or corrupt." 

I will have an Xp disc tomarrow (sry)  and yes it des support usb boot.  When i boot directly from my Ext HD the screen goes blank with the blinking thing up in the left corner and doesn't do anything

---

### Post by logos34 on 2008-06-18
on second thought this may not be possible, especially with a cloned XP.  I mean, you can see if TestDisk will solve the corrupt partition table error and allow you to boot, but I'm not so sure.  I thought usb boot problems with XP Pro were a thing of the past post-SP2 and especially SP3 (flash is reportedly easier).  eSata no problem.  But it apparently briefly cuts off the usb during bootup, driver loading and hardware initialization, which is why you get the XP splash but then it bluescreens and reboots.  So to get this working I think you'll have to reinstall XP Pro.  I hope that's an option for you (If you have your product code and the XP disc you say you'll have tomorrow is Xp Pro, then you should be set.)  Backup all your files to one of the other partitions, and then follow [this guide]("http://www.ngine.de/index.jsp?pageid=4176"). It seems quite popular. Looks a little scary, but if you look closely all you're doing is copying the iso from cd, extractiing and editing files, then repackaging them to iso.

---

### Post by KuroYoma on 2008-06-18
Okay that the end of that then.  Thank you so much for all your help i really appreciate it.

---

