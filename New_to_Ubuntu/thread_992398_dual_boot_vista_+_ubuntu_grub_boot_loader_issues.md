---
title: "dual boot vista + ubuntu grub boot loader issues"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Clean1414 on 2008-11-24
i dual booted ubuntu and vista on my dell laptop. both OS,s work in the grub boot loader, i then used easyBCD to re install the vista boot loader. that successfully brought the vista boot loader back, in easybcd i then installed the nero grub boot loader and added the option to boot ubuntu in windows boot loader. i then restarted and tried to boot into ubuntu and it gives me a "error 17 file not found" error. so i reinstalled ubuntu and it brought back grub and they both work again but i need vista to be in charge. how can i make it work? im using ubuntu 8.10 with vista home prem with service pack 1.

---

### Post by caljohnsmith on 2008-11-24
One option is to just install Grub to the boot sector of the Ubuntu partition, and then you can add it to Vista's boot loader with EasyBCD by using this tutorial:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

And I should mention that you don't have to reinstall Ubuntu to install Grub to the boot sector of the Ubuntu partition; that can be done easily from the Live CD. Or if you want to use NeoGrub again, you would just have to make sure the Ubuntu entries use the correct (hdX,Y), which is most likely why you got that Grub error 17. Here is a tutorial that helps explain it, in case you haven't all ready seen it:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5)

Whichever option you choose, it would be really helpful if you would first boot your Live CD, open a terminal (Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by dj4mc on 2008-11-24
> **caljohnsmith said:**
> One option is to just install Grub to the boot sector of the Ubuntu partition, and then you can add it to Vista's boot loader with EasyBCD by using this tutorial:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

And I should mention that you don't have to reinstall Ubuntu to install Grub to the boot sector of the Ubuntu partition; that can be done easily from the Live CD. Or if you want to use NeoGrub again, you would just have to make sure the Ubuntu entries use the correct (hdX,Y), which is most likely why you got that Grub error 17. Here is a tutorial that helps explain it, in case you haven't all ready seen it:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5)

Whichever option you choose, it would be really helpful if you would first boot your Live CD, open a terminal (Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

I am having similar issues: I have read the above help tutorials and here is my situation:

1. I have 5 Hard Drives 2 in a Raid situation. I have a ASUS  Mother board with an AMD-X2 CPU THe drives are 2 160gig SATA drives and 2 300gig SATA drives int he RAID and one IDE 160gig drive that has OS-X on it. I dual booted (or did lol) Vista and OS-X with the MBR on the OS-X drive controlled from EasyBCD. Vista resides on one of the 160Gig SATA drives. I then put Ubuntu on the other 160gig SATA drive. I kept getting GRUB error 17 and if I went into BIOS boot screen could b oot into Vista or OS-X. I kept messing with things (I am good at that but a complete linux NOOB and a week ago thought Grub was an infant butterfly...) I coould boot into anything by going into the BIOS boot screen and telling it to boot from the specific drive that had the OS on it i.e. VIsta, Ubuntu or OS-X. Then I changed my GRUB settings from Ubuntu while booted from the Ubuntu HD using the drives as seen by Ubuntu at this point. Now I can't boot into anyting except the Live CD... I am pretty sure each OS sees the HD's differently. Any help would be greatly appreciated!

Most people seem to be booting from different partitions of the same HD. I am not locked into Easy BCD either. Just want to choose the OS as it boots and have one defaulted if I don'd do anything for 10 seconds!

Jules
Thanks in advance.

---

### Post by caljohnsmith on 2008-11-24
Jules, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like as far as booting is concerned. :)

---

### Post by dj4mc on 2008-11-25
> **caljohnsmith said:**
> Jules, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like as far as booting is concerned. :)

I will do this as soon as I get home. I appreciate the help. I am at the In Laws for Thankgsgiving. 

Jules

---

### Post by dj4mc on 2008-11-30
Here are my results. Interesting to me is that the BIOS only sees the three drives (the two SATA 160gigs and the PATA 160 gig) because the two 300gig drives are set up as a RAID in BIOS but Ubuntu sees all five and one of them has GRUB on it... Any and all help is much appreciated!

sudo fdisk -lu

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d3722fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1172214854   586107396   42  SFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc4a229e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   321672959   160836448+  af  Unknown

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1c2d1c2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048   312578047   156288000    7  HPFS/NTFS

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7b0d7b0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63   299805029   149902483+  83  Linux
/dev/sde2       299805030   312576704     6385837+   5  Extended
/dev/sde5       299805093   312576704     6385806   82  Linux swap / Solaris

ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 

ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system

ubuntu@ubuntu:~$ sudo dd if=/dev/sdd count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 

ubuntu@ubuntu:~$ sudo dd if=/dev/sde count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system

ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8400

ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$  sudo dd if=/dev/sdd bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8100

---

### Post by dj4mc on 2008-11-30
Here are my results. Interesting to me is that the BIOS only sees the three drives (the two SATA 160gigs and the PATA 160 gig) because the two 300gig drives are set up as a RAID in BIOS but Ubuntu sees all five and one of them has GRUB on it... Any and all help is much appreciated!

sudo fdisk -lu

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d3722fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1172214854   586107396   42  SFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc4a229e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   321672959   160836448+  af  Unknown

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1c2d1c2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048   312578047   156288000    7  HPFS/NTFS

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7b0d7b0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63   299805029   149902483+  83  Linux
/dev/sde2       299805030   312576704     6385837+   5  Extended
/dev/sde5       299805093   312576704     6385806   82  Linux swap / Solaris

ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 

ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system

ubuntu@ubuntu:~$ sudo dd if=/dev/sdd count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 

ubuntu@ubuntu:~$ sudo dd if=/dev/sde count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system

ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8400

ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$  sudo dd if=/dev/sdd bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8100

---

### Post by caljohnsmith on 2008-11-30
OK, so according to those commands you ran, you have Grub installed to the MBR of both your sda and sdd drives, and yet Ubuntu is on the sde drive. Since you said you can easily change which drive boots on start up, I would recommend simply installing Grub to the Ubuntu sde drive and also installing a Windows MBR to your Vista sdd drive. Then you can boot your Ubuntu drive on start up, and if all goes well, you should be able to boot all your OSes from the Grub menu. If that sounds good to you, then first do:
```
sudo grub
grub> device (hd0) /dev/sde
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Also, to install a Windows MBR to your Vista sdd drive, just do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdd
```
Then see if you can boot your Ubuntu drive OK, and if you can, I'll give you entries for Vista and OS X to add to your Grub menu that you can try. Let me know how it goes. :)

---

### Post by dj4mc on 2008-11-30
> **caljohnsmith said:**
> OK, so according to those commands you ran, you have Grub installed to the MBR of both your sda and sdd drives, and yet Ubuntu is on the sde drive. Since you said you can easily change which drive boots on start up, I would recommend simply installing Grub to the Ubuntu sde drive and also installing a Windows MBR to your Vista sdd drive. Then you can boot your Ubuntu drive on start up, and if all goes well, you should be able to boot all your OSes from the Grub menu. If that sounds good to you, then first do:
```
sudo grub
grub> device (hd0) /dev/sde
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Also, to install a Windows MBR to your Vista sdd drive, just do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdd
```
Then see if you can boot your Ubuntu drive OK, and if you can, I'll give you entries for Vista and OS X to add to your Grub menu that you can try. Let me know how it goes. :)

Thanks! I did the above and now I boot into a DRUB boot screen where I can select Ubuntu or Vista/Longhorn loader or OSX (It is the screen I was setting up before I could not boot into anything) If I try Ubuntu I get an error 17 cn not mount selected partition and ress any key to continue. It goes to Grub loading stage 2 on VIsta then locks up.

Next step?

---

### Post by caljohnsmith on 2008-11-30
OK, that's great news, we're making progress. You also did the commands to install a Windows MBR to the sdd drive, and it didn't report any errors? That's important for making the next steps work.

Next step, boot to the Grub menu again, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers (or if it has a "uuid" line, select that), press "e" to edit it, change it to "root (hd0,0)", press return to save the change, then press "b" to boot; that should hopefully be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" (or it might use a long UUID) to:
```
# groot=(hd0,0)
```
Next add the following entries at the bottom of file:
```
title	   HDD 1
rootnoverify (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   HDD 2
rootnoverify (hd2)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   HDD 3
rootnoverify (hd1)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1

title	   HDD 4
rootnoverify (hd4)
map        (hd0) (hd4)
map        (hd4) (hd0)
chainloader +1
```
And lastly run:
```
sudo update-grub
```
Reboot, and try each of the four new entries above in the Grub menu, and let me know exactly what happens when you try each one. :)

---

### Post by dj4mc on 2008-11-30
I am now loading Ubuntu form a Hard Drive! Yea!!!! I had to edit the boot up in Grub by pressing "e" and changing HD(1,0) to HD(0,0) It mounts the Vista Drive, OSX drive and my RAID form the 2 300gig SATA drives. 

Here is what is weird: Now from Ubuntu sda is vista, sdb is Ubuntu sdc and sdd are the two 300 gig drives by them selves and sde is the OSX drive.  That is looking at them from GNOME partition editor.

My big concern is getting Vista back! I will do the above and report back.

Edit: I changed the GRUB drives listed and Vista is booting from hd(3,0) and OSX from hd(2,0)   THANK YOU THANK YOU THANK YOU!!!!!!!!!!!!!!!!!!!!!!

Jules

---

### Post by danfrompiter on 2008-12-02
Hello folks,

I am new to this Forum as well as UBUNTU ):P - but the subject of this thread is very "dear to my heart" :lolflag: 

I have a AMD 64 bit based PC with 2 HDDs: first is IDE Master 160 GB and second is SATA 320 GB (both Western Digital if that matters at all).

I have Vista installed and working fine (up until installation of UBUNTU) on the SATA drive (which shows "after" IDE one in the boot BIOS flash) - b/c I have selected that drive to be the first Bootable HDD in the BIOS.

The IDE drive has 2 Windows NTFS and 3 LUNIX partitions - I can't take a snapshot of them but they look smth like:

Disk /dev/sda: 160.0 GB
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc25760bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       17165   137877831    7  Linux
/dev/sda2   *           17166    29857 137877831    7   HPFS/NTFS
/dev/sda3               29858    30401 137877831    7   HPFS/NTFS
/dev/sda4          17166       29857   101948490   83   Linux
/dev/sda5           29858       30401     4369680    5  Extended
/dev/sda6           29858       30401     4369648+  82  Linux swap / Solaris

Again - that is just to illustrate that my "sda" drive has mixed partitions and the first Linux one **does not have a "boot" star near it despite that I have selected that partition as a target for UBUNTU 8.10 installation...**

When I run "fdisk -l" the IDE drive (above)  shows up first and the SATA one (Win VISTA only) - second, so I figure that in the /boot/grub/menu.1st I should use entries like:

**root (hd0,0)** to boot Windows OS and
 **root (hd1,0)** to boot LINUX

I have made these changes, tried to reboot - and GRUB stage 1.5 bootloader just hangs w/o giving me an expected menu of bootable OSs.

I burned the unofficial "Super Grub Disk" and tried fixing the GRUB menu using it - but no luck, keep getting "Error 15 - file not found" error.

Questions please: 

1) Assuming that my newly installed UBUNTU Linux lives on IDE drive partitions /sd1, /sda4 and /sda6 - where exactly GRUB should be installed?

2) How can I fix this - either using UBUNTU LiveCD or unofficial "super Grub Disk". As of now - i cannot boot "either OS and am dead in the water"

many thanks & sorry for the long post,

Dan

---

### Post by caljohnsmith on 2008-12-02
Danfrompiter, about the boot flag, you don't need to worry about that. The boot flag is for two purposes: one is that some BIOSes will refuse to boot a drive that doesn't have one partition marked as bootable, because the BIOS assumes the drive is then a data drive with no bootable OS. The other purpose for the boot flag is for Windows type MBRs (Master Boot Record) that merely boot whichever partition on the HDD is marked as bootable. But Grub can boot an OS regardless of whether the boot flag is set on the OS's partition, so if you use Grub, it is entirely arbitrary which partition you set as bootable; but to make sure you don't have problems with the BIOS refusing to boot the drive, you should set the boot flag on either a primary or extended partition, but not a logical one. 

So which drive are you booting on start up? How about first doing the following to make sure Grub is properly installed to the MBR of your sda drive:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then reboot, make sure your BIOS is set to boot the sda Linux drive, and you should at least get a Grub menu on start up. Let me know if you can get this far or if you run into problems.

---

### Post by dj4mc on 2008-12-02
Dan one of the things that helped me sort this out (Other than this board) was stopping in the grub boot sequence and editing the entry live and telling it to boot. press "e" at the boot screen as the timer times out to booting. I am like you in that I have SATA srives and a PATA drive. I discovered that BIOS and the LIVE CD of Ubuntu order the drives differently (I think that is what was happening) I changed (hd0,0) to (hd1,0) during the boot sequence till I got it right. After booting I edited GRUB Menu.lst to match what I saw working. 

Good Luck!

---

### Post by danfrompiter on 2008-12-02
Thanks John and DJ4MC for quick replies!

So - just to clarify for a dumbfounded me :=) - if my IDE drive shows up as /dev/sda (which means it is "hd0"?) and my SATA drive shows up as /dev/sdb (which means it is "hd1"?), I should be setting up the grub like this:

grub> root (hd0,0)
grub> setup (hd0)
grub> quit

After which I can reboot and at least get my UBUNTU boot up - and if not, I can stop the boot sequence per DJ4MC's posting above and edit the /grub/menu.1st file to change the root entries? 

And - most importantly - if my **PC's BIOS is set up to first boot off SATA HDD which does NOT have Grub installed** - should I switch BIOS HDD boot sequence every time or install GRUB loader to the SATA drive and if so - how please?

thank much again,
++Dan

---

### Post by caljohnsmith on 2008-12-02
> **danfrompiter said:**
> Thanks John and DJ4MC for quick replies!

So - just to clarify for a dumbfounded me :=) - if my IDE drive shows up as /dev/sda (which means it is "hd0"?) and my SATA drive shows up as /dev/sdb (which means it is "hd1"?), I should be setting up the grub like this:

grub> root (hd0,0)
grub> setup (hd0)
grub> quit

After which I can reboot and at least get my UBUNTU boot up - and if not, I can stop the boot sequence per DJ4MC's posting above and edit the /grub/menu.1st file to change the root entries? 

And - most importantly - if my **PC's BIOS is set up to first boot off SATA HDD which does NOT have Grub installed** - should I switch BIOS HDD boot sequence every time or install GRUB loader to the SATA drive and if so - how please?

thank much again,
++Dan
You should be able to go into your BIOS and change the boot order so that you can always boot the sda Ubuntu drive on start up, and then you won't have to install Grub to your sdb drive. Try that first, and if for some reason you can't change your BIOS to boot the sda drive, then we can install Grub to the sdb drive. Also, if you boot the Ubuntu drive on start up, that drive is then (hd0) or the 1st boot drive, so your Ubuntu entries in Grub's menu.lst file should all use (hd0,0). How about trying the steps I gave in my previous post to install Grub to the MBR of your sda drive, and then try booting it on start up. Let me know exactly what happens and we can work from there if you want. :)

---

### Post by danfrompiter on 2008-12-04
John,

Thanks again for the last tip. The fact that I am posting this from my homecomputer (booted as UBUNTU ):P) says a lot - the problme is 50% solved:D

Here's what I get for fdisk -lu:

**Disk /dev/sda: 160.0 GB, 160041885696 bytes** <== my IDE drive
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x78507850

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    98253539    49126738+  83  Linux
/dev/sda2        98253540   312576704   107161582+   f  W95 Ext'd (LBA)
/dev/sda5       117595863   196603469    39503803+   7  HPFS/NTFS
/dev/sda6       196603533   278277929    40837198+   7  HPFS/NTFS
/dev/sda7       278277993   312576704    17149356   82  Linux swap / Solaris
/dev/sda8        98253666   117595799     9671067   83  Linux

Partition table entries are not in disk order

**Disk /dev/sdb: 320.0 GB, 320072933376 bytes** <== my SATA drive
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d7c1d5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   332272394   166136166    7  HPFS/NTFS  <== MBR is here??
/dev/sdb2       332272395   625137344   146432475    f  W95 Ext'd (LBA)
/dev/sdb5       332272458   430172504    48950023+   7  HPFS/NTFS
/dev/sdb6       430172568   527928029    48877731    7  HPFS/NTFS
/dev/sdb7       527928093   625137344    48604626    7  HPFS/NTFS
====================================================================

Here's the meaningful portion of my /boot/grub/menu.1st file:

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd1,0)
uuid		7c398380-e568-4e3e-989f-7ea89c643793
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7c398380-e568-4e3e-989f-7ea
89c643793 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root (hd1,0)
uuid		7c398380-e568-4e3e-989f-7ea89c643793
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7c398380-e568-4e3e-989f-7ea
89c643793 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root (hd1,0)
uuid		7c398380-e568-4e3e-989f-7ea89c643793
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista Business (loader)
rootnoverify	(hd0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

===================================================

Obviously - the UBUNTU entries work but I don't understand why :o - it is installed on **sda** which is **hd0**, but I use** root(hd1)**  no?

When I select Windows Vista (I changed the name) - I get "Error 12: Invalid device requested" error and GRUB halts

I did copy that entry from your earlier posts on the thread when you were helping "DJ4MC" guy. Could you examine the data above and advise further pls?

thanx!

++Dan

---

### Post by caljohnsmith on 2008-12-04
OK, first open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And then in all your Ubuntu entries, remove the "root (hd1,0)" line so that you are left with the "uuid" line similar to:
```
title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid 7c398380-e568-4e3e-989f-7ea89c643793
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=7c398380-e568-4e3e-989f-7ea89c643793 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet
```
In other words, you only need to use either a root line that gives the drive/partition, or a uuid line that simply gives the UUID of the Ubuntu partition. Next change your Vista entry to:
```
title Windows Vista
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
And that should hopefully be all it takes to boot Vista, assuming you are booting the Ubuntu drive on start up and that Vista is on the 1st partition of the other drive. 
[QUOTE=danfrompiter]Obviously - the UBUNTU entries work but I don't understand why  - it is installed on sda which is hd0, but I use root(hd1) no?
[/quote]
Actually the way it works is that on start up, (hd0) is the 1st boot drive (the first drive in the BIOS boot order), (hd1) is the 2nd boot drive, (hd2) the 3rd boot drive, etc. So if you set your BIOS to boot the Ubuntu drive, then Ubuntu is on (hd0). Anyway, how about rebooting, and let me know if the above Vista entry works from the Grub menu. If not, let me know exactly what happens when you try it, and we can work from there. :)

---

### Post by danfrompiter on 2008-12-05
Hi John,

Thaks gfor your fast reply again - and sorry for being sorta pain in the rear, but unfortunately my problem is STILL UNRESOLVED - ;please see below after your text.

> **caljohnsmith said:**
> OK, first open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And then in all your Ubuntu entries, remove the "root (hd1,0)" line so that you are left with the "uuid" line similar to:
```
title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid 7c398380-e568-4e3e-989f-7ea89c643793
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=7c398380-e568-4e3e-989f-7ea89c643793 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet
```
In other words, you only need to use either a root line that gives the drive/partition, or a uuid line that simply gives the UUID of the Ubuntu partition.

Dan: thanks, I have done that and yes - UBUNTU still booted up OK!

 Next change your Vista entry to:
```
title Windows Vista
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
And that should hopefully be all it takes to boot Vista, assuming you are booting the Ubuntu drive on start up and that Vista is on the 1st partition of the other drive. 

DZ: I have done that as well - :D - and thanks for explaining how BIOS handles Hard drives order. I did set the IDE (UBUNTU) drive to be the first drive to boot form - and it does start up GRUB etc etc
Actually the way it works is that on start up, (hd0) is the 1st boot drive (the first drive in the BIOS boot order), (hd1) is the 2nd boot drive, (hd2) the 3rd boot drive, etc. So if you set your BIOS to boot the Ubuntu drive, then Ubuntu is on (hd0). Anyway, how about rebooting, and let me know if the above Vista entry works from the Grub menu. If not, let me know exactly what happens when you try it, and we can work from there. :)

DZ: the problem is that I have tried to fix the whole thing with "Unofficial Super Grub Disk" and believe that I have installed some GRUB footprint to the MBR record of the WINDOWS HDD (hd1). The reasons for that is when I selected "Windows Vista" - it went in there, displayed the word "GRUB" and hung. I have tested this scenario 3 times in a row.

Then - stupidly - I tried fixing the problem  by un-installing GRUB form the HD1 (SATA) drive using same Super Grub Disk - but apparently I have removed it from HD0 because that program doesn't tell you which disk is currently active.

So - now I have regressed back to where I started from ... I need to know how to:

1) correctly uninstall GRUB from the HD1 and restore MBR,

2) correctly re-install GRUB on HD0,

3) making this whole thing work together 

All of the above - without using Super Grub.

thanks MUCH in advance!

++Dan

---

### Post by caljohnsmith on 2008-12-05
So what happened that you needed to use the Super Grub Disk? I thought we were close to getting your setup booting OK. How about redoing the Grub commands from post #15 to reinstall Grub to the MBR of your Ubuntu drive, and then you can restore a Windows equivalent MBR to your sdb drive with:
```
sudo lilo -M  /dev/sdb mbr
```
Then just follow the directions from post #18 if you haven't all ready to make sure your menu.lst is OK. Let me know how that goes.

---

### Post by danfrompiter on 2008-12-05
Thanks again John... I actually used Super Grub Disk *before* I started posting here - or maybe during an initial installation of UBUNTU I specified incorrect destination for GRUB being the SDB (VISTA) drive...

I will reinstall GRUB on HDA following your posts and I was looking for exactly this command:

```
sudo lilo -M  /dev/sdb mbr
```

that restores Windows MBR on my SDB (hd1) drive.

thanks,
++Dan

> **caljohnsmith said:**
> So what happened that you needed to use the Super Grub Disk? I thought we were close to getting your setup booting OK. How about redoing the Grub commands from post #15 to reinstall Grub to the MBR of your Ubuntu drive, and then you can restore a Windows equivalent MBR to your sdb drive with:
```
sudo lilo -M  /dev/sdb mbr
```
Then just follow the directions from post #18 if you haven't all ready to make sure your menu.lst is OK. Let me know how that goes.

---

### Post by danfrompiter on 2008-12-08
OK - finally IT WORKED John :guitar:

However since my Windows drive after intervention from Super Grub Disk went FUBAR :confused: - OI had to restore Windows from System backup. But after that GRUB worked beautifully when BIOS boots the UBUNTU IDE HDD first (becomes hd0) and then calls chainloader to boot Windows from the hd1 9which happens to be SATA). 

The only thing which I'd like to understand is that 

:code map (hd0)(hd1) 
      map  (hd1) (hd0) code : 

just for my understanding!

THANKS MUCH AGAIN MUCH APPRECIATED

---

### Post by caljohnsmith on 2008-12-08
> **danfrompiter said:**
> 
The only thing which I'd like to understand is that 

:code map (hd0)(hd1) 
      map  (hd1) (hd0) code : 

just for my understanding!

THANKS MUCH AGAIN MUCH APPRECIATED
That's great news to hear you got your setup working. :) About those "map" lines, Windows normally can't be booted from any other drive than (hd0), or the first drive in the BIOS boot order; those "map" lines are a trick that Grub uses to fool Windows into thinking it is booting off of (hd0), when really Windows is on (hd1). So the bottom line is, if Windows is on the first boot drive or (hd0), no mapping is necessary, but if Windows is on another drive, you normally have to use Grub's mapping technique in order to boot it. Anyway, cheers and have fun with your OSes. :)

---

