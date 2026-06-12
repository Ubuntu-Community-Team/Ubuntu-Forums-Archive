---
title: "GRUB 16 error."
date: 2008-10-22
forum: New to Ubuntu
---

### Post by sergaz on 2008-10-22
Hi Guys,

I wanted to try the Ubuntu 8 and used the live cd.
Everything went fine, I liked the system and installed it on the hard drive. I previously had WindowsXP installed on that machine (IBM Thinkpad R40). In the Ubuntu istaller I used the option "install in the largest continuous space". After the installation completed I got the GRUB error 16. I tried to repair the MBR usign the Windows install cd, but got an error when tried to access C: drive. It seems like DOS cannot see the hard drive anymore. I could access it through Ubuntu with live cd though. I also tried to setup the grub but without any success. Thank you in advance for your help!

---

### Post by kilroy423 on 2008-10-23
Did you want to get rid of windows or keep it?

In my experience in dual booting it is always best to installs windows first and then to install Linux, letting Grub or Lilo take care of the MBR.

You might want to try this:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by caljohnsmith on 2008-10-23
Do you get the Grub error 16 before seeing a Grub menu (or before seeing something like "press ESC to see menu"), or do you get it after you see the Grub menu and choose an OS to boot?

From your Live CD, please open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also do the following:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, then reboot, and let me know if you still get the Grub error 16; we can work from there. :)

---

### Post by sergaz on 2008-10-25
I get the grub error before the grub menu. I tried to setup the grub using terminal commands but still getting the same error :-(. Thanks!

---

### Post by caljohnsmith on 2008-10-25
Can you post the output of all the commands from post #3? That would help to diagnose your problem.

---

### Post by sergaz on 2008-10-25
Here is the output of the terminal commands:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13081307

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    44936639    22468288+   7  HPFS/NTFS
/dev/sda2        44936640    78140159    16601760    f  W95 Ext'd (LBA)
/dev/sda5        44936703    72001439    13532368+   b  W95 FAT32
/dev/sda6        72001503    77747039     2872768+  83  Linux
/dev/sda7        77747103    78140159      196528+  82  Linux swap / Solaris

grub> find /boot/grub/stage1
 (hd0,5)

grub> find /grub/stage1

Error 15: File not found

grub> setup (hd0)

Error 12: Invalid device requested

Thanks!

---

### Post by caljohnsmith on 2008-10-25
You forgot the "root" command, so try this:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Post the output of the above commands, reboot, and let me know exactly what happens on start up.

---

### Post by Duck2006 on 2008-10-25
> grub> find /boot/grub/stage1
(hd0,5)

grub> find /grub/stage1

Error 15: File not found

grub> setup (hd0)


did you put root in the commands?

find /boot/grub/menu.lst
root (hd0,5)
setup (hdo)
quit

---

### Post by sergaz on 2008-10-25
This time setup worked:

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

After reboot I first get the vendor screen (IBM) and then the following message:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 16

---

### Post by caljohnsmith on 2008-10-25
OK, from your Live CD do:
```

sudo fsck -y /dev/sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda --recheck
```
And please post the output. Reboot, and let me know if you still get the Grub error 16.

---

### Post by sergaz on 2008-10-25
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda6
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda6: clean, 108504/180224 files, 532859/718192 blocks
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda --recheck
Probing devices to guess BIOS drives. This may take a long time.

Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda

Unfortunately, the grub error is still there :-(. Thanks!

---

### Post by caljohnsmith on 2008-10-25
OK, I'm thinking you might have a BIOS or cable problem with your HDD, but one more thing to try would be:
```
sudo e2fsck -p -v -C0 -f /dev/sda6
```
Please post the output of that command, and if it says it fixed anything, go ahead and reboot and let me know if anything changes on start up. :)

---

### Post by sergaz on 2008-10-25
ubuntu@ubuntu:~$ sudo e2fsck -p -v -C0 -f /dev/sda6
                                                                               
  108504 inodes used (60.21%)
     130 non-contiguous inodes (0.1%)
         # of inodes with ind/dind/tind blocks: 4750/30/0
  532859 blocks used (74.19%)
       0 bad blocks
       1 large file

   81288 regular files
   11441 directories
      69 character device files
      26 block device files
       2 fifos
       0 links
   15669 symbolic links (14917 fast symbolic links)
       0 sockets
--------
  108495 files

It seems like this command didn't fix anything and grub still doesn't work. 

I don't think it is a hardware problem (i.e. cable), since before Ubuntu installation I didn't have ANY problem with this machine for 5 years.

---

### Post by caljohnsmith on 2008-10-25
I think it is highly likely that you could have a cabling problem:
[QUOTE=sergaz]I wanted to try the Ubuntu 8 and used the live cd.
Everything went fine, I liked the system and installed it on the hard drive. I previously had WindowsXP installed on that machine (IBM Thinkpad R40). In the Ubuntu istaller I used the option "install in the largest continuous space". After the installation completed I got the GRUB error 16. [COLOR="Blue"]I tried to repair the MBR usign the Windows install cd, but got an error when tried to access C: drive. It seems like DOS cannot see the hard drive anymore.[/COLOR] I could access it through Ubuntu with live cd though. I also tried to setup the grub but without any success. Thank you in advance for your help![/QUOTE]
You mentioned that your Windows Install CD can't recognize the HDD any more, which could definitely signify a hardware problem. Can you at least check your HDD connections? 

Sometimes the Windows Install CD won't recognize a HDD if the partition table is corrupted. We should check if that is the case, so first post:
```
sudo fdisk -l
```
And then do:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by sergaz on 2008-10-25
Since it is not desktop but laptop machine, to check the cable connections is not that simple (at least for me :-) ). I think it is some kind of partition problem. I'll test it with the commands you suggested and will let you know asap. It takes some time to boot from live CD :-(...

It seems like the testdisk application cannot be installed:

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk

---

### Post by Miljet on 2008-10-25
I find it difficult to convince myself that this is a cabling problem since GRUB setup can find the proper files on the disk. Seems like to me that if there were a cabling problem, the disk would be inaccessable. 

GRUB 16 error indicates an inconsistent filesystem structure usually caused by a corrupt filesystem.

Might be easier to just re-install.

---

### Post by sergaz on 2008-10-25
It would be nice to reinstall. But what should I do to make sure it will be properly installed this time? Thanks!

---

### Post by Miljet on 2008-10-25
First check your install disk to make sure there are no errors. Your partitions are already in place so use manual partitioning and use the existing partitions. Everything else should go fine.

---

### Post by caljohnsmith on 2008-10-26
> **Miljet said:**
> I find it difficult to convince myself that this is a cabling problem since GRUB setup can find the proper files on the disk. Seems like to me that if there were a cabling problem, the disk would be inaccessable. 

GRUB 16 error indicates an inconsistent filesystem structure usually caused by a corrupt filesystem.

Might be easier to just re-install.
I know it sounds hard to believe that a Grub error 16 can be a cabling problem, but here is at least one example (I've seen at least one more too, but I'm too lazy to dig it up right now :)):

[http://ubuntuforums.org/showthread.php?t=762870](http://ubuntuforums.org/showthread.php?t=762870)

Also, if he does indeed have a problem with his partition table, then I don't think reinstalling will fix that unless he changes his partition scheme. :)

Sergaz, I would still recommend checking your partition table, but it's up to you. If you want to try again, first enable all your repositories in System > Admin > Software Sources, and then you should be able to download testdisk and run it (you need an internet connection obviously). Let us know how it goes.

---

### Post by sergaz on 2008-11-10
I was out of town and yesterday finally had time to fix the problem with Ubuntu installation. I formated the whole hard drive using the LiveCD. I had one partition in NTFS, this could cause some problem for Ubuntu, so I converted it into FAT32. After that I re-installed Ubuntu again and this time it works fine. Since I do not need double boot this "brute force" solution worked for me. Thanks for your help!

---

