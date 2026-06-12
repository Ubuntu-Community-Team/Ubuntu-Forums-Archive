---
title: "Cannot boot Windows in dual-boot setup"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by spoketire on 2008-07-18
I'm trying to make a 2-hard-drive dual boot setup with XP on an NTFS drive and Ubuntu on an ext3 drive.  Both are 160GB.

I've finally gotten GRUB to boot Ubuntu, but for the Windows XP option, it just goes back to the GRUB menu.

Here's my **device.map**:
(hd0) /dev/sdb
(hd1) /dev/sda
I know that sdb is Ubuntu and sda is Windows, and I'm pretty confident that they're associated with hd0 and hd1 in the right order (I had to switch that around before Linux would boot).

Part of **menu.lst**:
title    Ubuntu 8.04.1, kernel 2.6.24-19-generic
root     (hd0,0)
kernel   /boot/vmlinuz-2.6.24-19-generic root=UUID=e068ee7d-0264-4bf1-a9e0-7eb4e19d9bd7 ro quiet splash
initrd   /boot/initrd.img-2.6.24-19-generic
quiet

              (that works)

title    Microsoft Windows XP Professional
root     (hd0,0)
savedefault
makeactive
chainloader +1

               (that doesn't work)

I think the windows part should have (hd1,0) as the root, but I've tried that and it doesn't work either.  I think it just brought me back to grub.

I think that I somehow got GRUB onto the windows hard drive, because if I boot to the windows drive directly from the BIOS boot menu, it still goes to grub.

I really hope that my XP installation is still intact.  Thanks for any help!

---

### Post by LowSky on 2008-07-18
I would download a Super Grub disk and try that. I set up my system on two drive and everything work correctly from dsay one, and I diidn't have to configue my Grub menu

---

### Post by spoketire on 2008-07-18
It still doesn't work if I set the windows to (hd1,0).  It just goes to the GRUB command line.  I think it might be because GRUB got onto both drives somehow.

---

### Post by spoketire on 2008-07-18
I have also tried the Super Grub disk.  It didn't really work, it just brought me to the grub menu and produced the exact same results.  Maybe I did the wrong super grub menu option?

---

### Post by spoketire on 2008-07-18
I've done some light reading, and I'm about to try FIXMBR from my Windows XP recovery CD.  I'm doing this because I think GRUB is on the windows disk.  So, if I take it off and put the Windows bootloader on that disk, I can just boot windows from the BIOS.  And then if I want to run Ubuntu, I can just boot from the Ubuntu disk.  It makes perfect sense to me, but it might be completely wrong.

I was about to do FIXMBR, and it said it might screw up the partition tables and make the whole hard drive inaccessible.  I don't want that, since everything important is on there and I didn't exactly back anything up.  So, is there really that big of a risk of losing data, or should I just go ahead?  Maybe I already wiped the windows drive somehow.

I would back it up from linux, but my Ubuntu can't even mount the NTFS drive anymore.

---

### Post by BGFG on 2008-07-18
If you can still boot linux, there is a utility that will help you mount NTFS drives, although my system could do it from the time i installed.
Ensure that you have these packages installed. 

libntfs-3g23
ntfs-3g
ntfs-config

Just open Synaptic Package manager and search in 'ALL' for ntfs. they should pop up. Once you get ntfs read and write support and you're able to backup your stuff you can then safely attempt to re-build your bootloader.

---

### Post by spoketire on 2008-07-18
Well, before I could read the NTFS Windows drive just fine (yesterday), but now I can't even mount it.  It does show up with fdisk -l though.

I'll look for those packages, but if I don't have some of them, I'm not sure how I'm going to install them, since the computer in question has no internet connection.

---

### Post by BGFG on 2008-07-18
If you do have a machine with a connection and any portable media you could try here 

[http://www.gnomefiles.org/app.php/ntfs-config](http://www.gnomefiles.org/app.php/ntfs-config)

if not, then in system>>administration>>software sources in the 'Software Sources' page you can add your install cd as a repository and use it to install the packages.

---

### Post by spoketire on 2008-07-18
All right, I got all the ntfs reading stuff installed, but my drive still isn't showing up.  I've tried manually mounting it also.

fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x765c765c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3498

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19270   154786243+  83  Linux
/dev/sdb2           19271       19457     1502077+   5  Extended
/dev/sdb5           19271       19457     1502046   82  Linux swap / Solaris

Disk /dev/sdc: 2004 MB, 2004353024 bytes
16 heads, 32 sectors/track, 7646 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000
```

I tried all of these: (/media/win having been created)
```
mount /dev/sda /media/win
mount /dev/sda1 /media/win
mount -t ntfs /dev/sda /media/win
mount -t hpfs /dev/sda /media/win
mount -t ntfs /dev/sda1 /media/win
mount -t hpfs /dev/sda1 /media/win
```

I've gone to the Partition Editor, and it says the drive is ntfs, but it can't read the contents of the filesystem.

I think that since GRUB is on the ntfs drive, it has made the windows installation and files unreadable, although I'm almost positive they're still there.  Is there any kind of software that would allow me to access at least some of the files on a drive with errors like this?

---

### Post by BGFG on 2008-07-18
One of those tools should be appearing in Applications>>System Tools>>NTFS configuration Tool. Have you tried that ?

---

### Post by spoketire on 2008-07-18
Yes, I've tried that, and no devices show up in the advanced options section.  The file browser still doesn't show the NTFS drive.

---

### Post by BGFG on 2008-07-18
Also, did some searching found this.

[http://www.sajithmr.com/mount-ntfs-file-system-in-ubuntu-debian/](http://www.sajithmr.com/mount-ntfs-file-system-in-ubuntu-debian/)

But before you do, i think you should try a restart. Also check this.

[http://ubuntuforums.org/showthread.php?t=780202](http://ubuntuforums.org/showthread.php?t=780202)

---

### Post by Mister.Vash on 2008-07-18
It appears from your fdisk -l output that your ntfs volume is on a different drive

I believe what you need to do is to use the map command to get that to work.  See the following for reference:
[http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows)

Try modifying the section in your menu.lst to the following

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader +1

---

### Post by spoketire on 2008-07-18
I tried the hard drive mapping reversal thing, with no luck.  It got to stage2 in grub, however, and just hung there.  I think it was trying to chainload the windows bootloader, which doesn't exist on that drive anymore because it has been overwritten by GRUB.

So, I'm back to these two options:

1.  run FIXMBR from the windows xp recovery disk (and possibly make the data unreadable, which it already is)

2.  use a data recovery tool and then run FIXMBR

It all depends on the actual risk involved with fixmbr.  Does anyone know of a really good data recovery tool?

---

