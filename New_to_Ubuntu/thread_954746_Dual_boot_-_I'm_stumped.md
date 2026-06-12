---
title: "Dual boot - I'm stumped"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by DChapman on 2008-10-21
New to forum, did search on thread but ran dry, or out of patience, in finding resolution...

I have tried dual booting XP and Ubuntu in I don't know how many ways and still have no success.

250GB HDD - partitioned 172 GB NTFS for XP; 30GB for Ubuntu; 5 GB swap; 30 GB FAT32 for share.

Installed 8.10 w/manual partitioning during install process and set 30 GB partition to Ext3.

I've tried allowing Grub to go to boot sector always get "error 17"

Followed notes from LiniuxDevCenter on creating a share and copying boot sector data to "ubuntu.bin" then copying to c: on primary drive to use Win loader.  When pointing to "Ubuntu" all I get is a black screen.

Installed and formatted again pointing boot record to the installed partition rather than MBR to attempt to have Acronis OS selector locate Ubuntu and load. The OS was detected as Linux but same response, black screen when booting.

Between my processes of installs, wiping partitions, re-installing, attempts to use Grub, not use Grub, use System Rescue CD to QtParted and dd if=/dev/drive of=/mnt/share/ubuntu.bin bs=512 count=1 (kind of Greek to me...) so I could copy to  share then copy to root of C so I could use the MS loader; use Super Grub to fixmbr to bring me back to load Windows, I've gotten myself so wrapped up in confusion I'm not sure where to go from here.


All that said and per HDD partition specs. mentioned above, XP is installed and running in primary partition, Ubuntu is installed and not functioning in Ext3.

Any assistance it truly appreciated,

Dave

---

### Post by caljohnsmith on 2008-10-21
So what happened when you let Grub install to the MBR (Master Boot Record)? When you ran the Ubuntu installer, and clicked on the "advanced" button at the end to tell Grub where to install to, did you use /dev/sda or (hd0) at some point? That would have put Grub in the MBR. So if you did that, was that when you got the Grub error 17 on start up? If so, did you get the error before seeing a Grub menu, or after getting the Grub menu and trying to boot Ubuntu? 

Also, please post:
```
sudo fdisk -lu
```
And we can work from there if you want. :)

---

### Post by _sAm_ on 2008-10-21
Perhaps Auto Super Grub disk could help you;
[http://ubuntulinuxhowtos.blogspot.com/2008/08/best-way-to-restore-lost-grub-or-boot.html](http://ubuntulinuxhowtos.blogspot.com/2008/08/best-way-to-restore-lost-grub-or-boot.html)

You don't need the 30gig fat32 disk, use the ntfs driver so Ubuntu can read/write from your ntfs partition, and this [http://www.fs-driver.org/](http://www.fs-driver.org/) for the opposite.

---

### Post by DChapman on 2008-10-21
[QUOTE=caljohnsmith;6007258]So what happened when you let Grub install to the MBR (Master Boot Record)? 

I've tried so many variants I hope I keep this straight:
w/8.04 I was not given any options to install Grub, it was just done for me. When rebooting I got error 17.  After this I did the Super grub trick to fixmbr so I could go look for help.  Somewhere inbetween I did the ubuntu.bin copy to share and relocate to root and use win loader, blank screen. Installind 8.10 (because I had done this a week or so back and I was given Grub install option, no success, wiped partition) and after following insrtuctions on copy and relocate ubuntu.bin and configuring the win loader all I would get is a blank screen again.  Installed 810 to Ext3 and told boot loader to install there, Acronis at least found the OS but once again, blank screen.

"When you ran the Ubuntu installer, and clicked on the "advanced" button at the end to tell Grub where to install to, did you use /dev/sda or (hd0) at some point? That would have put Grub in the MBR. So if you did that, was that when you got the Grub error 17 on start up?"

Yes


"If so, did you get the error before seeing a Grub menu, or after getting the Grub menu and trying to boot Ubuntu? "

No Grub nenu.

Currently in Ubuntu from CD boot.

Also, please post:
```
sudo fdisk -lu
```


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc916757

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       361269720   424180259    31455270   83  Linux
/dev/sda2   *          66   361269719   180634827    7  HPFS/NTFS
/dev/sda3       424180260   488392064    32105902+   f  W95 Ext'd (LBA)
/dev/sda5       424180323   434686769     5253223+  82  Linux swap / Solaris
/dev/sda6       434686833   488392064    26852616    b  W95 FAT32

Partition table entries are not in disk order

---

### Post by linuxluver on 2008-10-21
you dont need share partition, for windows to get files from linux all you have to do is mount the NTFS partition in somewhere like /media/win and drop the file in My Documents or something.
For linux to get files from windows just make a folder in My Documents called files4linux and put the file in that folder.
then go to linux and open files4linux or whatever you decided to call it and get the file.

---

### Post by tangibleorange on 2008-10-21
sorry if you've already posted this, but are you currently using NTLDR ?
(windows XP bootloader, no options).

---

### Post by DChapman on 2008-10-21
Was, did.  Set the windows loader after moving ubuntu.bin to c: and pointed in the loader via "c:\ununtu.bin "Ubuntu"

With no success there, blank screen, I went back edited out the line, turned off timing for the boot screen and went back into Windows to see if Acronis would locate, which it did.  When booting w/Acronis OS Selector, same blank screen result.

In addition to above comments I have more boot crap in root of C: that I have no idea about:

1) boot - directory
2) bootwiz - directory
3) The Win loader: (minus previously removed pointer to ubuntu.bin)
[boot loader]
;timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\windows
timeout=0
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\windows="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

4) A 0 byte file $bootdrive$ - temp of some kind I would assume
5) Bootmgr
6) Bootwiz.sys

---

### Post by caljohnsmith on 2008-10-21
One thing I notice is that your Ubuntu partition starts at about the 180 GB mark, and some BIOSes can't access anything past 137 GB, so your partition might be out of reach of BIOS. But that may not explain a Grub 17 error:
> Error 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Also, since you're using the new 8.10, I believe 8.10 uses the newer 256 byte inode size for its ext3 file system rather than the older 128 byte inode size. Unfortunately that can cause problems with older versions of Grub, but I think the 8.10 release comes with a patched version of Grub to handle it. That could explain a Grub error 17 I think. Anyway, we should check to see if that is an issue.

So from your Live CD, please do:
```
sudo dumpe2fs /dev/sda1 | grep -i "inode size"
```
And let me know what it returns. Also, to get a better idea if Grub is properly installed to the MBR, please post the output of:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And We can work from there. :)

---

### Post by cl0ckwork on 2008-10-21
i may have missed this but unless you are installing a 64-bit edition 5 gig of swap wont get you very far.

32-bit OS's only recognize up to 4 gig of ram + swap together
and even with that some kernels have limitations on how much memory they can handle by themselves. i know the recent one used in mandriva will only recognize 1 gig by default

---

### Post by DChapman on 2008-10-21
> **caljohnsmith said:**
> One thing I notice is that your Ubuntu partition starts at about the 180 GB mark, and some BIOSes can't access anything past 137 GB, so your partition might be out of reach of BIOS. But that may not explain a Grub 17 error:

Also, since you're using the new 8.10, I believe 8.10 uses the newer 256 byte inode size for its ext3 file system rather than the older 128 byte inode size. Unfortunately that can cause problems with older versions of Grub, but I think the 8.10 release comes with a patched version of Grub to handle it. That could explain a Grub error 17 I think. Anyway, we should check to see if that is an issue.

So from your Live CD, please do:
```
sudo dumpe2fs /dev/sda1 | grep -i "inode size"
```

ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sdal | grep -i "inode size"
dumpe2fs 1.41.0 (10-Jul-2008)
dumpe2fs: No such file or directory while trying to open /dev/sdal


please post the output of:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

ubuntu@ubuntu:/$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
ubuntu@ubuntu:/$ 


sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And We can work from there. :)

ubuntu@ubuntu:/$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff00                                   
0000002


Man, I don't think that baby steps nearly describes how I'm feeling with this install!  I really do appreciate your assistance.
Dave

---

### Post by caljohnsmith on 2008-10-21
You're certainly welcome for the help, Dave, I'm almost positive we can get your Grub working here. :) It looks like Grub may not be properly installed since that first "dd" command didn't return anything. Also, please rerun the dump2fs command (copy and paste it if you can), because you accidentally used a lower case L with sda1. 

So to reinstall Grub to your MBR, do:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And please post the output of the above commands. In the meantime, reboot, and let me know exactly what happens on start up.

---

### Post by DChapman on 2008-10-21
> **caljohnsmith said:**
> You're certainly welcome for the help, Dave, I'm almost positive we can get your Grub working here. :) It looks like Grub may not be properly installed since that first "dd" command didn't return anything. Also, please rerun the dump2fs command (copy and paste it if you can), because you accidentally used a lower case L with sda1. 

So to reinstall Grub to your MBR, do:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And please post the output of the above commands. In the meantime, reboot, and let me know exactly what happens on start up.

---------- hopefully w/o typos ------------

ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda1 | grep -i "inode size"
dumpe2fs 1.41.0 (10-Jul-2008)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 

Inode size:	          128


Thanks again for your continued support...
DC

---

### Post by DChapman on 2008-10-21
Boot screen

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17

Yipee, here we go again....

We're getting multiple computers involved now, on my daughters Mac Book rather than booting into and out of Windows and Linux

Dave

---

### Post by caljohnsmith on 2008-10-21
OK, I'm fairly certain you're running up against the 137 GB BIOS limitation, so we need move Grub closer to the beginning of your HDD. And since you have Windows before your Linux partition, I think the best solution is to use Grub4DOS in your Windows partition. So from your Live CD, follow these steps (if any of the steps return an error, do not proceed with the subsequent steps):
[LIST=1]
[*]First download the Grub4DOS package to your Ubuntu desktop from [here]("http://download.gna.org/grub4dos/grub4dos-0.4.3.zip").
[*]Next do:
```
sudo mkdir /mnt/sda1 /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
cd ~/Desktop
unzip grub*.zip
cd grub*
sudo cp glrdr /mnt/sda2/.
sudo cp /mnt/sda1/boot/grub/menu.lst /mnt/sda2/.
sudo dd if=grldr.mbr of=/dev/sda bs=440 count=1
sudo dd if=grldr.mbr of=/dev/sda skip=1 seek=1
```
[/LIST]
And please copy/paste the lines so you don't risk any typos (especially with the dd commands, as they could be really dangerous if you mistype anything). If all goes well with the steps, reboot and let me know what happens. :)

---

### Post by DChapman on 2008-10-21
Try (hd0,0): non-MS:skip
Try (hd0,1) NTFS5: No grldr
Try (hd0,2): Extended: invalid or null
Try (hc0,3): invalid or null
Error: Cannor find GRLDR in all devices. 

Rebooting....

---

### Post by caljohnsmith on 2008-10-21
It looks like you successfully installed the Grub4DOS MBR, but it couldn't find the glrdr boot file in your Windows directory. While you still have sda2 mounted, post the output of:
```
ls -l /mnt/sda2
```
Where "-l" is a lowercase L. Also, did any of the commands return any errors?

---

### Post by DChapman on 2008-10-21
... going back to square 1.5 - Just Suber Grubbed and fix[ed]mbr

---

### Post by DChapman on 2008-10-21
Jumped the gun I guess...

---

### Post by DChapman on 2008-10-21
If I'm intruding on personal space I apologize in advance...

Do you have an IM address you would be willing to forward for a live work through? (I'm back in Windoze) d_chapman on skype or dchapman on Messenger

---

### Post by caljohnsmith on 2008-10-21
I wished you hadn't jumped the gun and replaced the Grub4DOS MBR using Super Grub Disk; please stick with me if you want my help. :) So as long as you are in Windows, just download the Grub4DOS 0.4.3 package and the "grubinst 1.0.1" package from [here]("http://sourceforge.net/project/showfiles.php?group_id=104188"). Unzip them, and put the "glrdr" file in the root directory, i.e. the C:\ directory. You should have a menu.lst there from the previous commands you ran, but if not, put the menu.lst from the Grub4dos package in the root directory too. Then run the Grubinst_GUI program to reinstall Grub4DOS to your MBR again. Let me know how it goes; I have to go for a little while, but I'll be back in ~45 min or an hour.

---

### Post by caljohnsmith on 2008-10-21
So what's the status right now? How far did you get?

---

### Post by DChapman on 2008-10-21
The impatient one bows humbly requesting forgiveness for "jumping the gun" ;-)

Per comments downloaded the two suggested .zips, did the grub install and found that the menu.lst was empty and refused to load.  Booted into Win and copied from grub 4 dos.  Next boot got menu but when looking for Linux install got nothing.

---

### Post by DChapman on 2008-10-21
Just went and commented out most of the fluff in the menu.lst file but am a bit confused as to where to direct the loader to now find the ubuntu install

---

### Post by DChapman on 2008-10-21
title Load Windows XP Pro
fallback 1
find --set-root /ntldr
chainloader /ntldr
savedefault --wait=2

title find and boot Ubuntu with menu.lst already installed
fallback 5
find --set-root /sbin/init
savedefault --wait=2
configfile /boot/grub/menu.lst

---

### Post by caljohnsmith on 2008-10-21
OK, please boot your Live CD, and copy over the Ubuntu menu.lst with:
```
sudo mkdir /mnt/sda1 /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
sudo cp /mnt/sda1/boot/grub/menu.lst /mnt/sda2/.
```
Then edit the menu.lst with:
```
gksudo gedit /mnt/sda2/menu.lst
```
And make sure all the Ubuntu entries use "root (hd0,0)", and at the end of the file add:
```
title Windows XP
root (hd0,1)
chainloader +1
```
Save, reboot, and let me know what happens.

---

### Post by DChapman on 2008-10-21
Will do and this time I'll attempt patience... ;-)

---

### Post by DChapman on 2008-10-21
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda1 /mnt/sda2
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/sda2

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo cp /dev/sda1/boot/grub/menu.lst /mnt/sda2/.
cp: cannot stat `/dev/sda1/boot/grub/menu.lst': Not a directory

---

### Post by caljohnsmith on 2008-10-21
My mistake, I corrected my previous post. Please try again. :)

---

### Post by DChapman on 2008-10-21
Well I did it again and the menu.lst is blank?

Output from above (with fdisk -lu)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcc916757

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       262212930   325123469    31455270   83  Linux
/dev/sda2   *          66   262212929   131106432    7  HPFS/NTFS
/dev/sda3       325123470   488392064    81634297+   5  Extended
/dev/sda5       325123533   477885554    76381011    7  HPFS/NTFS
/dev/sda6       477885618   488392064     5253223+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda1 /mnt/sda2
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/sda2
ubuntu@ubuntu:~$ sudo cp /mnt/sda1/boot/grub/menu.lst /mnt/sda2/.
ubuntu@ubuntu:~$ gksudo gedit /mnt/sda2/menu.lst

---

### Post by caljohnsmith on 2008-10-21
I don't know how your menu.lst ended up being blank, but you can follow these steps to regenerate a new one:
```
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
sudo mount --bind /dev /mnt/sda1/dev
sudo mount --bind /proc /mnt/sda1/proc
sudo chroot /mnt/sda1 /bin/bash
update-grub
exit
```
Then follow the steps from post #25 to copy it over again and edit it. By the way, I have to leave in about 10 minutes and won't be back until tomorrow morning sometime. Hopefully you will have it working, but if not we can pick up in the morning. Good luck and let me know how it goes. :)

---

### Post by DChapman on 2008-10-21
Will do, you're a good man, I truly appreciate all your help.
Dave

---

### Post by eternalnewbee on 2008-10-21
Just wanted to salute you caljohnsmith. This is some serious display of knowledge and patience you are showing!

---

### Post by DChapman on 2008-10-21
I wish patience weren't necessary, this is WAY beyond me and I'm wondering how in the world I will ever learn to resolve issues like this myself! 

Per Mr.Patiences' instructions I have successfully gotten grub to load at boot but into Windows only.  When rebuilding Grub all menu.lst information is commented out with no loader for the installed Ubuntu called out.  So, at this point knowing just enough to really screw things up I searched this forum for examples of menu.lst data, found some text I inserted and tried to no avail.  

That said, with appreciation for help rendered so far, am still without a successful boot into Ubuntu via Grub....

Day is short here in the K.C. metro so it's time to call it quits for 21 November.

Dave

---

### Post by bobpur on 2008-10-22
I've got to hand it to both of you. That's a lot of effort. I hope it works out  for you DChapman.

I didn't see any specs on your machine and I, really, don't buy into the BIOS limitation unless you have an older machine. I'm running two 160 gb Maxtors in a 8 yr old Compaq 5WV252. The mobo is the only original piece left in the machine. One of those drives is for WinXP Pro and the other is for LinuxMint v5 KDE CE. I have full capacity from both of them. I prefer to dualboot with two different drives; one for each OS.

Did you install the 250 gb drive yourself? Is it a a PATA drive? If so, is the jumper correct and is the drive placed correctly on the cable. These issues will affect your computers ability to read and write to/from the drive.

I guess, what I'm trying to say in so many words is that, to have the read/write problems you're having, in my experience, is hardware related. 

And... I'm not blessed with an over-abundance of patience, either. :) Neither, am I a code genius. I respect those that are, but, I'm not.

Good Luck.

---

### Post by bobpur on 2008-10-22
This has been a long day for me as well and I'm beyond tired.

I'd like to offer some advise that supplements my previous post. Maybe, you've already considered it. Start over one more time. Check your hardware and settings, burn another  distro (Ubuntu) cd at 4X or less from a new download (not the same one as there might be a problem with it). Forget all of the programs not on the cd needed for installation. Everything you need for a dualboot is on your linux cd. Just follow the prompts and you'll be up and running soon enough.

I'm not detracting from the work done so far, I've just never had those kinds of problems that took that much effort to fix in a dualboot build.

I'm going to bed. I'll apologize for butting in tomorrow. :) (yawn.)

---

### Post by caljohnsmith on 2008-10-22
Sorry to hear you had problems with the newly created menu.lst, Dave. How about going through the steps in post #30 again, but please post the output of all the commands. Also, at the end after you've exited the chroot environment (with "exit"), also post:
```
ls -lR /mnt/sda1/boot
cat /mnt/sda1/boot/grub/menu.lst
```

---

### Post by caljohnsmith on 2008-10-22
> **eternalnewbee said:**
> Just wanted to salute you caljohnsmith. This is some serious display of knowledge and patience you are showing!
Thanks for the vote of confidence, I try to help out when I can. :)

---

### Post by DChapman on 2008-10-22
Per your request...

ubuntu@ubuntu:~$ sudo mkdir /mnt/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sda1
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/sda1/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/sda1/proc
ubuntu@ubuntu:~$ sudo chroot /mnt/sda1 /bin/bash
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-4-generic
Found kernel: /boot/last-good-boot/vmlinuz
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ ls -lR /mnt/sda1/boot
/mnt/sda1/boot:
total 12188
-rw-r--r-- 1 root root  504774 2008-09-24 03:15 abi-2.6.27-4-generic
-rw-r--r-- 1 root root   95910 2008-09-24 03:15 config-2.6.27-4-generic
drwxr-xr-x 2 root root    4096 2008-10-22 14:53 grub
-rw-r--r-- 1 root root 8354874 2008-10-22 09:26 initrd.img-2.6.27-4-generic
-rw-r--r-- 1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r-- 1 root root 1041452 2008-09-24 03:15 System.map-2.6.27-4-generic
-rw-r--r-- 1 root root    1073 2008-09-24 03:17 vmcoreinfo-2.6.27-4-generic
-rw-rw-rw- 1 root root 2305072 2008-10-22 09:23 vmlinuz-2.6.27-4-generic

/mnt/sda1/boot/grub:
total 216
-rw-r--r-- 1 root root    197 2008-10-22 09:26 default
-rw-r--r-- 1 root root     15 2008-10-22 09:26 device.map
-rw-r--r-- 1 root root   8108 2008-10-22 09:26 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-10-22 09:26 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-22 09:27 installed-version
-rw-r--r-- 1 root root   8712 2008-10-22 09:26 jfs_stage1_5
-rw-r--r-- 1 root root   4788 2008-10-22 14:53 menu.lst
-rw-r--r-- 1 root root   4788 2008-10-22 14:53 menu.lst~
-rw-r--r-- 1 root root   7352 2008-10-22 09:26 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-10-22 09:26 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-10-22 09:26 stage1
-rw-r--r-- 1 root root 121500 2008-10-22 09:27 stage2
-rw-r--r-- 1 root root   9556 2008-10-22 09:26 xfs_stage1_5
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ cat /mnt/sda1/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fb5873d1-2743-acc3-42da-3082d5f3fc95 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=fb5873d1-2743-acc3-42da-3082d5f3fc95 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=fb5873d1-2743-acc3-42da-3082d5f3fc95 ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd0,0)
kernel		/boot/last-good-boot/vmlinuz root=UUID=fb5873d1-2743-acc3-42da-3082d5f3fc95 ro quiet splash  last-good-boot
quiet

title		Ubuntu intrepid (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

ubuntu@ubuntu:~$

---

### Post by DChapman on 2008-10-22
Where does one turn off "smileys" for this forum...

---

### Post by caljohnsmith on 2008-10-22
OK, that's great, looks like the menu.lst will be just fine this time. So follow these steps again to copy over the menu.lst to the Windows directory:
```
sudo mkdir /mnt/sda1 /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
sudo cp /mnt/sda1/boot/grub/menu.lst /mnt/sda2/.
```
Please post the output of the above commands so I can make sure it all went OK, reboot, and let me know what happens when you try Ubuntu and Windows from the Grub menu. :)

P.S. If you highlight the output of the commands you paste into the message box and click the pound symbol graphic # at the top of the message box, it will put the highlighted text in code tags so it is more readable. Then you don't have to worry about smileys where they shouldn't be.

---

### Post by DChapman on 2008-10-22
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda1 /mnt/sda2
mkdir: cannot create directory `/mnt/sda1': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sda1
mount: /dev/sda1 already mounted or /mnt/sda1 busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/sda2
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /mnt/sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /mnt/sda2 ntfs-3g force 0 0
ubuntu@ubuntu:~$ sudo cp /mnt/sda1/boot/grub/menu.lst /mnt/sda2/.
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-10-22
OK, the problem is your Windows is marked as having an "unclean shutdown". Try the following:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda2
```
Post the output of that, and if ntfsfix says it completed successfully, then try again:
```
sudo rm /mnt/sda2/menu.lst
sudo mkdir /mnt/sda2 /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
sudo cp /mnt/sda1/boot/grub/menu.lst /mnt/sda2/.
```
And please post the results.

---

### Post by DChapman on 2008-10-22
ubuntu@ubuntu:~$ sudo apt-get install ntfsprogs

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfsprogs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda2
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda2 was processed successfully.
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo rm /mnt/sda2/menu.lst
rm: cannot remove `/mnt/sda2/menu.lst': No such file or directory
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda2 /mnt/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/sda2
ubuntu@ubuntu:~$ sudo cp /mnt/sda1/boot/grub/menu.lst /mnt/sda2/.
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-10-22
That's great, so reboot, try both Windows and Ubuntu from the the Grub menu, and let me know what happens. :)

---

### Post by DChapman on 2008-10-22
Will do (fingers crossed...)

---

### Post by eternalnewbee on 2008-10-22
Just knocked on wood

---

### Post by egalvan on 2008-10-22
> **cl0ckwork said:**
> i may have missed this but unless you are installing a 64-bit edition 5 gig of swap wont get you very far.

**32-bit OS's only recognize up to 4 gig of ram + swap together**
and even with that some kernels have limitations on how much memory they can handle by themselves.
i know the recent one used in mandriva will only recognize 1 gig by default

That TOTALLY depends on the kernel. 

The limits are 1gb, 4gb, and 64gb.

I would be surprised if any distro less than two years old has not enabled at least the 4gb option.

I'm running 8.04.1 32bit with 4gb ram and a 2gb swap, no problems.

BTW, the 'server' install of 8.04LTS has the bigmem memory and smp ops enabled.

---

### Post by DChapman on 2008-10-22
I had to use Grubinst again to get the menu to come up at boot.  Great, now I have a menu.  Getting closer. Now I'm getting error 19 can not load partition.  Looked here in forum and on Grub Page.  I'm going to buy a Grub book!  I think I'm going to go out and find a Tandy or Atari computer that ran on my cassette tape player, life was simpler then...

Following is from menu.lst.  


title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=fb5873d1-2743-acc3-42da-3082d5f3fc95 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-4-generic
quiet

title		Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-4-generic root=UUID=fb5873d1-2743-acc3-42da-3082d5f3fc95 ro  single
initrd		/boot/initrd.img-2.6.27-4-generic

title		Ubuntu intrepid (development branch), kernel Last successful boot
root		(hd0,0)
kernel		/boot/last-good-boot/vmlinuz root=UUID=fb5873d1-2743-acc3-42da-3082d5f3fc95 ro quiet splash  last-good-boot
quiet

title		Ubuntu intrepid (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2008-10-22
Just wondering, but why did you have to use grubinst to get the Grub menu again? I thought you were previously getting the Grub4DOS menu, but you just couldn't use it to boot anything. Can you boot into Windows from the Grub menu now? 

It looks very likely that there is a problem with your Intrepid partition at this point, since both grub4DOS and Intrepid's Grub gave the same "couldn't mount partition" type error. One of your previous posts showed that your Intrepid partition uses the older 128 byte inode size, so that shouldn't be an issue, because Grub4DOS can handle the newer 256 byte inode size anyway. I'm thinking your problem may be a bug with how Intrepid set up the partition, or it could be a generic problem with your HDD's partition table. 

We can easily check the integrity of your HDD's partition table with "testdisk", so let's start there. Please first post:
```

sudo dumpe2fs /dev/sda1 | grep -i "inode size"
sudo fdisk -l
```
Note it uses "-l" rather than "-lu", which will make it easy to compare with testdisk's results. Then enable all your repositories in System > Admin > Software Sources, and download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", N to search for Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen once the search finishes.

---

### Post by DChapman on 2008-10-22
I probably should have been more specific on the "grubinst" comment, I had to run that from w/in Windows because after executing previous steps this morning (step 48) the grub menu did not come up at boot, the systems booted straight into Windows. From there ran per our conversation yesterday and subsequent download of the two grub .zip's.  After running the grub menu did come up with both the Ubuntu and Windows load lines (as detailed in 48) but when attempting to enter Ubuntu I was given the "19" error "could not load partition". Then, here we speak...


ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda1 | grep -i "inode size"
dumpe2fs 1.41.0 (10-Jul-2008)
Inode size:	          128
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc916757

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           24808       28723    31455270   83  Linux
/dev/sda2   *           1       24807   199262194+   7  HPFS/NTFS
/dev/sda3           28724       30401    13478535    f  W95 Ext'd (LBA)
/dev/sda5           28724       29747     8225248+   b  W95 FAT32
/dev/sda6           29748       30401     5253223+  82  Linux swap / Solaris

Partition table entries are not in disk order

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  testdisk
0 upgraded, 1 newly installed, 0 to remove and 448 not upgraded.
Need to get 1225kB of archives.
After this operation, 3858kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe testdisk 6.9-1.1 [1225kB]
Fetched 1225kB in 3s (380kB/s)    
Selecting previously deselected package testdisk.
(Reading database ... 101874 files and directories currently installed.)
Unpacking testdisk (from .../testdisk_6.9-1.1_i386.deb) ...
Processing triggers for man-db ...
Setting up testdisk (6.9-1.1) ...
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo testdisk
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
TestDisk need 25 lines to work.
Please enlarge the terminal and restart TestDisk.
ubuntu@ubuntu:~$ 

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P Linux                24807   0  1 28722 254 63   62910540 [Ubuntu]
 2 * HPFS - NTFS              0   1  4 24806 254 63  398524389 [Windows XP Pro]
 3 E extended LBA         28723   0  1 30400 254 63   26957070
 5 L FAT32                28723   1  1 29746 254 63   16450497
   X extended             29747   0  1 30400 254 63   10506510
 6 L Linux Swap           29747   1  1 30400 254 63   10506447


TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition               Start        End    Size in sectors
D FAT16 >32M               0   1  1    49 254 63     803187 [DellUtility]
D Linux                10663   2  1 16938 254 63  100823814
D Linux Swap           16939   1  1 17211 254 63    4385682
D Linux                17212   1  1 23586 254 63  102414312
D Linux Swap           23587   1  1 23864 254 63    4466007
D HPFS - NTFS          23865   0  1 27789 254 63   63055125 [Ubuntu]
D Linux Swap           27790   1  1 30400 254 63   41945652






Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 411 MB / 392 MiB

---

### Post by caljohnsmith on 2008-10-22
Your partition table looks just fine, and testdisk didn't report any errors, so I think we can safely cross that off the list of possible causes of the boot problem. I realized that one thing we haven't done yet is a simple file system check on the Ubuntu partition; I assumed the file system was OK because you've been able to mount it with no problems, but maybe there is a small glitch that is making Grub choke. So from your Live CD again, do:
```
sudo umount /dev/sda1
sudo fsck -y /dev/sda1
```
And post the output of those commands.

---

### Post by DChapman on 2008-10-22
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1
fsck 1.41.0 (10-Jul-2008)
e2fsck 1.41.0 (10-Jul-2008)
Adding dirhash hint to filesystem.

Ubuntu: clean, 110177/3932160 files, 632927/7863817 blocks

---

### Post by DChapman on 2008-10-22
Is there a way of getting a digest of this thread emailed?

---

### Post by caljohnsmith on 2008-10-22
I'm not sure exactly what you mean by getting a digest of the thread emailed, but one thing you can do is if you subscribe to the thread (using the "Thread Tools" link at the top of the thread), you can set it so that you are instantly emailed the replies to the thread. Is that maybe what you are looking for? 

Anyway, it looks like the file system is OK according to fsck. So from your Live CD, try this:
```
sudo grub
grub> root (hd0,0)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
```
And please post the output. By the way, when you post the output, if you highlight the text and click the pound sign graphic # at the top of the message box, it will put code tags around the text so it is more readable. Next reboot, and let me know exactly what happens on start up. :)

---

### Post by DChapman on 2008-10-22
[quote] [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,0)

grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst

grub>

---

### Post by DChapman on 2008-10-22
All I get is

GRUB_

---

### Post by caljohnsmith on 2008-10-22
I've helped quite a few people with Grub problems, but I must admit that I've never come across a situation quite as unique and stubborn as yours, Dave. :) Can you give any more clues about how your originally set up the HDD or anything else unusual might have done during the Ubuntu installation? Did you use the Ubuntu partitioner to create the new partitions, or did you use something in Windows? And you said you tried 8.04 and got the same Grub error 17, correct? 

If you're up for it, I'm thinking maybe if you try and reinstall Ubuntu, but instead use some other file system like ext2, maybe that will work. If you do decide to give it a shot, I would use 8.04 just to make sure we don't first run into any Intrepid bugs; and if 8.04 works, you could try 8.10.

---

### Post by DChapman on 2008-10-22
Let's see, this is a new HDD, installed about two weeks ago, initially setup cloned via Acronis True Image.  After installation I removed the hidden partition that Dell likes to toss out there for recovery.  I used Acronis Disk Director to re-partition the drive with the intent of setting up Ubuntu and Vista (for test).  The Vista install became a headache so I chose to toss the Vista idea and stick with only Ubuntu.  I formatted the partition setup for Vista via  Acronis Disk Director.

The first install I attempted was 8.04, I let it do automatic setup so it grabbed part of the NTFS partition and did its thing.  Then the fun began with error 17.  From here it's a blur of formats and Super Grubs to keep me up and running in Windows.  That lead to a "what the heck" attitude and I thought I'd attempt 8.10.  Ending with the same result and not liking to have inanimate objects (like computers) best me, I started digging about to solve the issue.  From here I found a puzzle master on Ubuntuforums.com who graciously offered assistance and has yet to be rid of me and my problems!  ;-)  As I type this I'm downloading a fresh copy of 8.04 to do a new burn to CD and will for the most part start over.

I see in Disk Director that when formatting again I have Ext2, Ext3, and ReiserFS available.  I would assume I can use any of the three when doing the 8.04 install as well.  You mentioned Ext2, I also saw comment earlier in the thread of ReiserFS.  Being that we're goin' from scratch which direction would be best?

Do you have a suggestion on swap size?  (figured I'd really start from scratch)

Do I or don't I need a common FAT32 partition to share data between Ubuntu and Windows?

Any other install suggestion you have will at this point be greatly appreciated, and, let me add once again, you have shown great patience in assiting me on this, thank you.

DC

---

### Post by meierfra. on 2008-10-22
Before reinstalling I suggest to check out these  two posts: 

It could be a bios issue:

[http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")

or a problem with your cables


[http://ubuntuforums.org/showthread.php?t=768101]("http://ubuntuforums.org/showthread.php?t=768101")

(the first post looks more promising to me)

---

### Post by caljohnsmith on 2008-10-22
[QUOTE=meierfra.]Before reinstalling I suggest to check out these two posts:

It could be a bios issue:

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

or a problem with your cables


[http://ubuntuforums.org/showthread.php?t=768101](http://ubuntuforums.org/showthread.php?t=768101)

(the first post looks more promising to me)
[/QUOTE]
+1. Dave, I agree with meierfra, especially the link about tweaking your BIOS settings. I think that is your best bet before doing an entire reinstall. Be sure to write down any BIOS settings you change in case you need to revert back. Let us know how it goes. :)

---

### Post by DChapman on 2008-10-22
Unfortunatly this is a production machine/laptop that I dare not risk wiping and starting over on. It isn't worth the risk of down time if a rebuild goes south.  That said however, I can move partitions just about anywhere I want with Acronis so may attempt a move of the Linux part to the front of the drive, if you think this would be beneficial.

---

