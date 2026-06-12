---
title: "[SOLVED] Bootloader committed seppuku"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by flynavy03 on 2008-11-22
My dual Vista/Kubuntu (Hardy) boot was working fine, until one day for unknown reasons it would no longer boot.  I can't remember what the initial problem was, but I tried to fix it by using the GRUB ==> MBR option from the Super Grub Disk.  This got me to the point where I could get the proper list of OSes to come up from the menu.lst file on my Linux partition.

However, when I tried to select Vista, I would get a "BOOTMGR is missing" error.  When I tried to select Ubuntu, I got a GRUB Error 22.  The weird thing is that if I used the Super GRUB disk option of LINUX(1) AUTO, I could boot both Ubuntu and Vista just fine from that same menu.lst.

So I decided since I had nothing important on the Linux side, I'd just erase the partitions, and give that whole hard drive to Intrepid.  SO I did.  Installed Intrepid, and took the CD out to reboot.  I figured that would reinstall GRUB correctly as a matter of course.  Wrong.

Now when I boot without Super GRUB disk, I get a GRUB error 17.  When I try to boot from the Super GRUB Disk into Linux, I get a GRUB error 15.  Which makes no sense, because there is a /boot/grub/menu.lst file on my Linux drive, and it includes Vista and Ubuntu.  I can boot to Windows with the Super GRUB disk just fine.

Ideas?

---

### Post by caljohnsmith on 2008-11-22
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
And please identify your partitions. Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by flynavy03 on 2008-11-22
OK, I'll pull all that info and post here.

---

### Post by flynavy03 on 2008-11-22
OK, here goes.

First:  
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk
/dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa65ac75a

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   293044223   146521088    7  HPFS/NTFS Disk

/dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xafc4fff1

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   613008269   306504103+  83  Linux
/dev/sdb2       613008270   625137344     6064537+   5  Extended
/dev/sdb5       613008333   625137344     6064506   82  Linux swap / Solaris

```

Next:
```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
GRUB
```
```
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB
```

Finally:
```

ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8100

```

```
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
ff04
```

---

### Post by caljohnsmith on 2008-11-22
OK, part of the confusion is that it looks like both sda and sdb have Grub in the MBR (sda gave a slightly anomalous output though), and only the Grub in sda points correctly to the Grub files on sdb1. Can you set your BIOS to boot the sdb Ubuntu drive on start up? That would be ideal, so then you can keep your drives independent of each other (less chance of problems). If you can set your BIOS to boot the sdb drive, how about doing the following to reinstall Grub to the MBR of sdb:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
And please post the output of all the above commands. Also do:
```
sudo dd if=/dev/sda count=20 | gzip -c > ~/Desktop/sda.MBR.gz
```
And please attach the "sda.MBR.gz" on your desktop to your next post. Next do the following to set the boot flag on your sdb1 linux partition; this is a good precaution because even though Grub can boot a partition regardless of whether the boot flag is set, some BIOSes will refuse to boot a drive that doesn't have one partition with the boot flag set:
```
sudo fdisk /dev/sdb
```
Enter "a", then "1" for the partition, then "w" to write the change, and finally "q" to quit. Next reboot, set your BIOS to boot the sdb drive, and you should hopefully get a Grub menu. Booting Ubuntu from the menu might result in a Grub error, but let me know how far you get.

---

### Post by flynavy03 on 2008-11-22
Oops. Forgot to save the output from GRUB when I exited.  But that worked for Ubuntu; I get GRUB now and I get Ubuntu to load just fine.  Vista, though, gets "GRUB Error 13:  Invalid or unsupported executable format."  It boots fine with the Super GRUB disk.

---

### Post by caljohnsmith on 2008-11-22
OK, as I mentioned in my previous post, please attach the following "sda.MBR.gz" file on your desktop to your next post so I can look at it:
```
sudo dd if=/dev/sda count=20 | gzip -c > ~/Desktop/sda.MBR.gz
```
Next open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your existing Vista entry with:
```
title	   Windows Vista
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, and let me know what happens when you boot Vista from Grub.

---

### Post by flynavy03 on 2008-11-22
Argh.  Failure to follow simple instructions.  Sorry.  Let me attach the zip file, and I'll see what happens when I edit menu.lst.

---

### Post by caljohnsmith on 2008-11-22
I'm leaving now and won't be around until tomorrow, but in the meantime, it would be good to restore a Windows MBR to your Vista drive now that you have the Ubuntu drive booting fine; that way if anything happens to Ubuntu or the Ubuntu drive, you should still be able to boot the Vista drive. Just do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
And then you should be able to boot the Vista drive directly on start up if you ever need to. Let me know how booting Vista from Grub goes though.

---

### Post by flynavy03 on 2008-11-22
That menu.lst entry seemed to do the trick!  Thanks for the help.  For my own edification, what did that entry do to make things work?

---

### Post by caljohnsmith on 2008-11-23
> **flynavy03 said:**
> That menu.lst entry seemed to do the trick!  Thanks for the help.  For my own edification, what did that entry do to make things work?
Glad to hear it worked OK. About the Vista entry, what it does is tells Grub to look on the second boot drive (hd1) in the first partition (hd1,0) for Vista (note the numbering begins with 0, not 1), and then Grub uses a mapping technique (the "map" lines) to fool Vista into thinking that it is actually being booted from the first boot drive (hd0) rather than the second boot drive (hd1) where Vista really is. That's necessary because in general, Windows will refuse to boot from anything other than the first drive in the BIOS boot order (hd0). 

So the bottom line is, if you boot Windows from the first boot drive (hd0), the mapping lines are not necessary; but if you boot Windows from any drive other than (hd0), you should include the mapping lines. If you want a little more detailed info, you might want to see this thread:

[http://ubuntuforums.org/showthread.php?t=984640&page=2](http://ubuntuforums.org/showthread.php?t=984640&page=2)

See post #17 where I tried to explain it a bit more in detail. Anyway, cheers and have fun with your OSes. :)

---

