---
title: "HOWTO: Install Edgy 6.10 from an .iso file"
date: 2006-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by john_spiral on 2006-12-10
***ONLY USE THIS HOWTO IF YOU DON'T HAVE A WORKING CD DRIVE OR WANT TO SAVE THE TROUBLE OF BURNING A PHYSICAL DISC***

***THIS INSTALLATION METHOD WILL ONLY WORK WITH THE ALTERNATIVE ISO FILES OF UBUNTU/KUBUNTU/XUBUNTU - PLEASE CHOOSE THE RELEVANT .iso , vmlinuz & initrd.gz FILES FOR 7.04 & 7.10   ***

***SKIP STEPS 9/10 IF YOU ARE INSTALLING 7.04 & 7.10***

Hi,

Below is a micro step-by-step procedure for installing Ubuntu 6.10 from an .iso file. The below procedure might also be useful for installing Kubuntu/Edubuntu & Xubuntu.

Before I go any further I&#8217;m still relatively new to Ubuntu and would appreciate your help in refining/correcting this HOWTO and answering questions.

(1) Download the _**Alternative**_ Ubuntu/Kubuntu/Edubuntu/Xubuntu .iso file and run an md5 check on it. If you are running Windows drag your .iso file onto the below program (md5sums.exe) and it will spit out a long string of characters and numbers. Make sure the string it spits out matches the published md5 sum.

[http://www.pc-tools.net/files/win32/freeware/md5sums-1.2.zip](http://www.pc-tools.net/files/win32/freeware/md5sums-1.2.zip)

md5 sums look like the following:

549ef19097b10ac9237c08f6dc6084c6  ubuntu-6.10-alternate-i386.iso

(2) Before installing Ubuntu you will need to partition your drive. In essence you will need to boot from another media either a floppy, 2nd drive or USB key and run some type of partition software. Create one new partition for the Ubuntu installation, one to hold the .iso file & additional boot files (say 700megs). You might need to resize your existing OS to make space for the above 2 partitions.
 
(3) Install grub onto either a floppy or hard drive and create a similar entry in your menu.lst file:

title Install Ubuntu
root (hd0,2)
kernel /boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd /boot/initrd.gz

**([COLOR="Red"]hd0,2[/COLOR]) refers to the 1st hard drive [COLOR="Red"]'hd0'[/COLOR] and the 3rd partition [COLOR="Red"]'2'[/COLOR].

The counting of partitions and hard drives starts at zero. Linux loves making life complicated ;-)

Change (hd0,2) to match the drive and partition of your .iso file.

e.g (hd1,3) Refers to drive 2 and partition 4.  

(4) **_Download_** the vmlinuz & initrd.gz files from the below site (DON'T USE vmlinuz & initrd.gz FILES FROM .iso) :

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/)

(5) Plonk the .iso, vmlinuz & initrd.gz files onto the newly created partition from step (2) in a /boot directory. 

(6) **_NB_** Make sure all other Ubuntu/Kbuntu/Xubuntu/Debian .iso installer files have been renamed to .iso.somethingelse, this will prevent the installer from picking up the wrong .iso file.

(7) Boot the machine from the hard disk or floppy that has grub installed, you should see a menu that contains &#8216;Install Ubuntu&#8217;. Select &#8216;Install Ubuntu&#8217; and press enter.

(eight) Next run through the installation until it fails to find the .iso file. Then change to terminal 2 with (Ctrl-Alt-F2). Hit enter to activate this console.

(9) Type the below commands in terminal 2:

mkdir -p /dev/loop 
ln /dev/loop0 /dev/loop/0 

(10) Change back to terminal 1 (Ctrl-Alt-F1), scan again and the ISO will be detected.

(11) Voila! The install should be working, choose the manual option on the '[!!] Partition disks' screen, specify your large partition might be hda2 as your root/home....

(12) You will need to edit your grub entry to get it to work, please post problems. 

Thanks to all the helpful people on the forums for getting this procedure to work.

Thanks also to the busybox mailing list!

---

### Post by yuanfangcan on 2006-12-10
sounds like very complicated. 

But if you have cd rom. Things will be much easier.

What I have done with the .iso for Ubuntu 5.10 is just record the .iso on a CD. Then boot the computer from the CD. Then following the install process.

---

### Post by bodhi.zazen on 2006-12-11
Very cool. Thank you.

---

### Post by Sebastral on 2006-12-11
Thanks! This is gonna safe me and the environment some cd's :D. Also great for pc's with no media other than hd.

---

### Post by xabbott on 2006-12-11
> **yuanfangcan said:**
> sounds like very complicated. 

But if you have cd rom. Things will be much easier.

What I have done with the .iso for Ubuntu 5.10 is just record the .iso on a CD. Then boot the computer from the CD. Then following the install process.

The whole point of the HOWTO is to *not* use a CD.

---

### Post by keithweddell on 2006-12-12
Doesn't work for me.  The installer still fails to find the iso at step 9.  Any suggestions?

Keith

Edit: Looks like it's a known bug - [see here]("https://launchpad.net/distros/ubuntu/+source/busybox/+bug/66220")
And I just found your other thread [here]("http://www.ubuntuforums.org/showthread.php?t=298719").  No joy for me yet though.

---

### Post by john_spiral on 2006-12-12
Hi Keith,

A few people have got the procedure working with the method devised on the below thread:

[http://www.ubuntuforums.org/showthread.php?t=298719](http://www.ubuntuforums.org/showthread.php?t=298719)

Have a look at your syslog file, created during the installation.

During the install jump to terminal 2 with ([COLOR="DarkRed"]Ctrl-Alt-F2[/COLOR])
press enter to activate terminal

[COLOR="DarkRed"]cd /
find / -name '*syslog*'[/COLOR]

should give you the location of syslog file. Mount one of your working partitions and copy the syslog file to your working os.

Reboot into your working os, search the syslog file for the partition containing the .iso file, E.g [COLOR="DarkRed"]hda2[/COLOR] (first hard drive, second partition)

There might be more than one instance of this. 

Should give you more detail on the failure. Come back to us.

---

### Post by nixclusive on 2006-12-12
Ultra cool man.. U just made me happier. :-D

---

### Post by bodhi.zazen on 2006-12-16
Nice How-to

This thread has been added to the UDSF wiki.

[Install_Edgy_6.10_from_an_.iso_file](http://doc.gwos.org/index.php/Install_Edgy_6.10_from_an_.iso_file)

---

### Post by john_spiral on 2006-12-17
Thanks for the addition bodhi! 

I'd like more input from users out there who have either failed or succeeded in getting Ubuntu to install from the above howto.

John

---

### Post by drtvasudevan on 2006-12-18
> **john_spiral said:**
> Thanks for the addition bodhi! 

I'd like more input from users out there who have either failed or succeeded in getting Ubuntu to install from the above howto.

John

i have working OS FC6
i tried to create a /boot folder on another partition but it firmly refused because it begins with  /
naturally the method failed as there was no 'boot folder only a boot folder

---

### Post by MannyL on 2006-12-18
I have followed the instructions and it still won't find the iso. Here is a desciption of my current system

I have a P-III 500 with 300 something megs of ram.
I have an IDE cd drive that does not want to boot any cds that I burn. At this point I don't know if it will even read them

The two hard drives that are attached right now are partitioned as

hda1-13999.43 mb ext2 running damnsmalllinux
hda2-4039.62   mb  Linux swap 

hdb1- 119184.31 mb ext2
hdb2- 847.21       mb ext2

hda1 is only using 949M.

I want to switch from damnsmalllinux to Ubuntu

```

Current listing of /boot on /dev/hda1

root@box:/boot# ls
System.map         System.map-2.4.26  boot-screens       grub               initrd.gz          linux              linux24            vmlinuz
root@box:/boot# 

listing mof /boot/grub/menu.lst

# This sets the default entry to boot. 
# Remember that GRUB counts from 0, so 1 is the second entry.

default 1
        
# This sets the length of time in seconds that grub will wait for the user to select an OS
# before it boots the default on. I reccommend at least 15 seconds.

timeout 15

# Enter the entry for DSL here. Something like this.

title Install Ubuntu
root (hd1,1)
kernel /boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd /boot/initrd.gz

title DSL
kernel /boot/linux24 root=/dev/hda1 quiet vga=normal noacpi noapm nodma noscsi frugal 

title DSL fb800x600
kernel /boot/linux24 root=/dev/hda1 quiet vga=788 noacpi noapm nodma noscsi frugal 

title DSL fb1024x768
kernel /boot/linux24 root=/dev/hda1 quiet vga=791 noacpi noapm nodma noscsi frugal 

title DSL fb1280x1024
kernel /boot/linux24 root=/dev/hda1 quiet vga=794 noacpi noapm nodma noscsi frugal 

#title DSL with toram, mydsl, restore, hostname, and passwords
#kernel /boot/linux24 root=/dev/hda1 quiet vga=normal noacpi noapm noscsi frugal dma toram mydsl=hda5 restore=hda5 host=DSL1 secure

#title DSL with XFree86
#kernel /boot/linux24 root=/dev/hda1 quiet vga=normal noacpi noapm noscsi frugal dma toram mydsl=hda5/xfree restore=hda6 host=DSL1 secure

#title DSL with mydsl, restore, persistentancy, hostname, and passwords
#kernel /boot/linux24 root=/dev/hda1 quiet vga=normal noacpi noapm noscsi frugal dma toram mydsl=hda3 restore=hda3 home=hda3 opt=hda3 host=DSL1 secure

#title DSL Runlevel 2
#kernel /boot/linux24 root=/dev/hda1 quiet vga=normal noacpi noapm noscsi nodma frugal 2 base norestore

#title Windows
#root (hd0,0)
#chainloader +1
#makeactive
#boot

on /dev/hdb2 I have 

root@box:/mnt/drive2# ls
boot        lost+found
root@box:/mnt/drive2# cd boot
root@box:/mnt/drive2/boot# ls 
initrd.gz                     ubuntu-6.10-desktop-i386.iso  vmlinuz

```

I can boot  to grub and scroll up to choose the Ubuntu installer. it starts and I get to the point it can not fiund the ISO.  I then do the alt-2 and switch to a terminal and enter the commands given in the first post. I swithc back to the installer screen, it rescans the sytsem and doesn't find the iso. Any suggestions?

---

### Post by drtvasudevan on 2006-12-19
one needs to copy verbatim the command 

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0 

or put in something for the /dev like hda2?
sorry for the noob question!

---

### Post by john_spiral on 2006-12-19
> **drtvasudevan said:**
> i have working OS FC6
i tried to create a /boot folder on another partition but it firmly refused because it begins with  /
naturally the method failed as there was no 'boot folder only a boot folder

Hi drtvasudevan,

I'm not sure If FC6 has a /boot directory in the same partition as the filesystem. Try the following:

(1) Boot into FC6
(2) open a terimal (run the below commands):

[FONT="Courier New"]cd /
ls -l >> ~/filesystem.txt[/FONT]

this will copy the list of your filesystem to a file called filesystem.txt

(3) In the same terminal, run the below:

[FONT="Courier New"]sudo fdisk -l >> ~/disks.txt[/FONT]

this will output your drive/partition structure, you will need to enter the root password.

post the contents of filesystem.txt & disks.txt.

It's important to run the below commands:

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0 

as specified in the howto.

Your /boot directory might be located on it's own partition?

---

### Post by john_spiral on 2006-12-19
Hi MannyL,

Have a look at your syslog file, created once it's failed to find the .iso

During the install jump to terminal 2 with (Ctrl-Alt-F2)
press enter to activate terminal

cd /
find / -name '*syslog*'

should give you the location of syslog file. Mount one of your working partitions (hda1) and copy the syslog file to DSL.

Reboot into DSL, search the syslog file for hd1. Use say the beaver editor.

[FONT="Courier New"]sudo beaver syslog &[/FONT]

There might be more than one instance of this.

Should give you more detail on the failure. Come back to us.

---

### Post by pinkertime on 2006-12-21
Hi,
I have followed the above procedure, with the difference that I don't use a floppy but I modify the grub config. on my hd directly. The problem is that, I can mount the iso image successfully (I can browse it in /cdrom), but the installer tells me it is not able to read the CDROM when loading the "installer components", and that maybe the driver is corrupted (but the md5 is ok) or not inserted. Where I am wrong? 
Thanks

---

### Post by drtvasudevan on 2006-12-21
of course, my FC partition has its own /boot folder.
you mean i can put the files in that partition and run?
i was only trying to put them in another partition.

file system.txt:
bin
boot
dev
etc
home
lib
lost+found
media
misc
mnt
net
opt
proc
root
sbin
selinux
srv
sys
tmp

and i am going to get reported for illegal operations as i am nota sudoer!
(so no disks list)

regards
tv

---

### Post by john_spiral on 2006-12-21
> **drtvasudevan said:**
> of course, my FC partition has its own /boot folder.
you mean i can put the files in that partition and run?
i was only trying to put them in another partition.


Hi drtvasudevan,

create an ubuntu folder inside the FC6 /boot folder, run the below commands in a terminal:

[FONT="Courier New"]
cd /boot
sudo mkdir ubuntu[/FONT]

you will need to have root access to complete the above and below steps.

Copy the .iso, vmlinuz & initrd.gz files to the /boot/ubuntu folder

Create a new entry in your /boot/grub/menu.lst file. See the begining of this thread for more info.

Give it a try and come back to us.

---

### Post by john_spiral on 2006-12-21
> **pinkertime said:**
> Hi,
I have followed the above procedure, with the difference that I don't use a floppy but I modify the grub config. on my hd directly. The problem is that, I can mount the iso image successfully (I can browse it in /cdrom), but the installer tells me it is not able to read the CDROM when loading the "installer components", and that maybe the driver is corrupted (but the md5 is ok) or not inserted. Where I am wrong? 
Thanks

Hi pinkertime,

It doesn't mater where grub resides as long as the installer boots. If you followed the steps (6 onwards) in the howto you should get the installer to find the .iso file. If it doesn't, you will need to have a closer look at your syslog file (see below steps). 

Have a look at your syslog file, created once it's failed to find the .iso

During the install jump to terminal 2 with (Ctrl-Alt-F2)
press enter to activate terminal

cd /
find / -name '*syslog*'

should give you the location of syslog file. Mount one of your working partitions and copy the syslog file to it. 

Use (Ctrl-Alt-F1) to get back to the installer so you can reboot.

Boot into a working os and have a closer look at the syslog file, search for the partition (hdx) where the ubuntu  .iso resides.

Please come back to us either way.

JOhn

---

### Post by pinkertime on 2006-12-21
Hi John, 
thank you for your fast replay. But the problem is not to find the .iso, because the installation mounts it correctly, and I can browse it in /cdrom. The problem is the second step, when the installation trays to read the device. 

But the iso is correctly found and mounted! I don't understand, if I can browse the cdrom it has to be readable...:-#

---

### Post by john_spiral on 2006-12-21
> **pinkertime said:**
> Hi John, 
thank you for your fast replay. But the problem is not to find the .iso, because the installation mounts it correctly, and I can browse it in /cdrom. The problem is the second step, when the installation trays to read the device. 

But the iso is correctly found and mounted! I don't understand, if I can browse the cdrom it has to be readable...:-#

What error does the installer give you?

---

### Post by drtvasudevan on 2006-12-21
pinkertime,
i dont understand.

the installer is a different program than what initiated the installation.
thi s  exactly why you need step 7.

---

### Post by pinkertime on 2006-12-22
> **john_spiral said:**
> What error does the installer give you?

I can go up to point (9) included successfully. That is the installer after hard drive scan says

[INDENT]"**Successfully mounted edgy installer ISO image.**"[/INDENT]

In fact, if I come back to terminal I can browse the mounted iso in /cdrom. In the next step the installer tries to load installer components from the installer ISO, but here it fails and the error is 

[INDENT]"[B]There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD-Rom.

Failed to copy from CD-ROM.[/B]" [/INDENT]

But the CD-ROM is mounted and is not corrupted because I have checked it with md5. It seems to be a problem of reading permissions.

---

### Post by pinkertime on 2006-12-22
I think to have understood why the procedure does not work for me. The installer, that is a debian installer, supports only installation from a /boot directory with an ext2 or ext3 file system ([http://lists.alioth.debian.org/pipermail/l10n-russian-cvs-commits/2005-April/000289.html]("http://lists.alioth.debian.org/pipermail/l10n-russian-cvs-commits/2005-April/000289.html"))
But my /boot file system is reiserfs. Could you confirm my hypothesis?

---

### Post by john_spiral on 2006-12-22
> **pinkertime said:**
> I think to have understood why the procedure does not work for me. The installer, that is a debian installer, supports only installation from a /boot directory with an ext2 or ext3 file system ([http://lists.alioth.debian.org/pipermail/l10n-russian-cvs-commits/2005-April/000289.html]("http://lists.alioth.debian.org/pipermail/l10n-russian-cvs-commits/2005-April/000289.html"))
But my /boot file system is reiserfs. Could you confirm my hypothesis?

Hi pinkertime,

The below lines are from the ./var/lib/dpkg/info/iso-scan.postinst file contained within the initrd.gz file:

[FONT="Courier New"][COLOR="DarkOrchid"]# Load up every filesystem known to man. The drive could have anything.
FS="ext2 ext3 reiserfs fat vfat xfs iso9660 hfsplus hfs ntfs"[/COLOR][/FONT]

as far as I know it should support reiserfs.

Does your machine have a physical cd-rom drive with another CD in the tray?

anyone else got a clue?

---

### Post by pinkertime on 2006-12-22
Just to give you more information I add my syslog (after the iso mounting):

 [INDENT]Dec 22 11:13:50 iso-scan: Found ISO boot/ubuntu-6.10-desktop-i386.iso on /dev/hda6
Dec 22 11:13:50 kernel: [  129.171974] ISO 9660 Extensions: Microsoft Joliet Level 3
Dec 22 11:13:50 kernel: [  129.195663] ISO 9660 Extensions: RRIP_1991A
Dec 22 11:13:50 iso-scan: Detected ISO with 'edgy' (edgy) distribution
Dec 22 11:13:52 anna-install: Queueing udeb apt-mirror-setup for later installation
Dec 22 11:13:52 iso-scan: Base system not installable from CD image, requesting choose-mirror
Dec 22 11:13:52 anna-install: Queueing udeb choose-mirror for later installation
Dec 22 11:13:52 main-menu[2757]: INFO: Modifying debconf priority limit from 'medium' to 'high' 
Dec 22 11:13:52 debconf: Setting debconf/priority to high
Dec 22 11:13:52 main-menu[2757]: DEBUG: resolver (libc6): package doesn't exist (ignored) 
Dec 22 11:13:52 main-menu[2757]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Dec 22 11:13:52 main-menu[2757]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 11:13:52 main-menu[2757]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 11:13:52 main-menu[2757]: INFO: Menu item 'load-iso' selected 
Dec 22 11:13:52 cdrom-retriever: warning: Unable to find main/debian-installer/binary-i386/Packages in /cdrom/dists/edgy/Release.
Dec 22 11:13:52 cdrom-retriever: warning: Unable to find main/debian-installer/binary-i386/Packages.gz in /cdrom/dists/edgy/Release.
Dec 22 11:13:52 cdrom-retriever: warning: Unable to find restricted/debian-installer/binary-i386/Packages in /cdrom/dists/edgy/Release.
Dec 22 11:13:52 cdrom-retriever: warning: Unable to find restricted/debian-installer/binary-i386/Packages.gz in /cdrom/dists/edgy/Release.
Dec 22 11:14:02 anna[10626]: WARNING **: bad d-i Packages file 
Dec 22 11:14:02 main-menu[2757]: INFO: Menu item 'load-iso' succeeded but requested to be left unconfigured. 
Dec 22 11:14:02 main-menu[2757]: INFO: Modifying debconf priority limit from 'high' to 'medium' 
Dec 22 11:14:02 debconf: Setting debconf/priority to medium
Dec 22 11:14:02 main-menu[2757]: DEBUG: resolver (libc6): package doesn't exist (ignored) 
Dec 22 11:14:02 main-menu[2757]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Dec 22 11:14:02 main-menu[2757]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 11:20:01 main-menu[2757]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 11:20:01 main-menu[2757]: INFO: Restoring default debconf priority 'high' 
Dec 22 11:20:01 debconf: Setting debconf/priority to high
Dec 22 11:20:01 main-menu[2757]: INFO: Menu item 'load-iso' selected 
Dec 22 11:20:01 anna[10714]: grep:  
Dec 22 11:20:01 anna[10714]: /cdrom/dists/edgy/Release 
Dec 22 11:20:01 anna[10714]: : No such file or directory 
Dec 22 11:20:01 cdrom-retriever: error: No components listed in /cdrom/dists/edgy/Release.
Dec 22 11:20:06 anna[10714]: WARNING **: bad d-i Packages file 
Dec 22 11:20:06 main-menu[2757]: INFO: Priority changed externally, setting main-menu default to 'high' (high) 
Dec 22 11:20:06 main-menu[2757]: INFO: Menu item 'load-iso' succeeded but requested to be left unconfigured. 
Dec 22 11:20:06 main-menu[2757]: INFO: Modifying debconf priority limit from 'high' to 'medium' 
Dec 22 11:20:06 debconf: Setting debconf/priority to medium
Dec 22 11:20:06 main-menu[2757]: DEBUG: resolver (libc6): package doesn't exist (ignored) 
Dec 22 11:20:06 main-menu[2757]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Dec 22 11:20:06 main-menu[2757]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 11:23:28 kernel: [  707.127671] ReiserFS: hda3: found reiserfs format "3.6" with standard journal
Dec 22 11:23:28 kernel: [  707.688587] ReiserFS: hda3: using ordered data mode
Dec 22 11:23:28 kernel: [  707.702360] ReiserFS: hda3: journal params: device hda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Dec 22 11:23:28 kernel: [  707.708107] ReiserFS: hda3: checking transaction log (hda3)
Dec 22 11:23:28 kernel: [  707.763246] ReiserFS: hda3: Using r5 hash to sort names[/INDENT]

Anyway, thank you for your help! :)

---

### Post by pinkertime on 2006-12-22
> **john_spiral said:**
> 

Does your machine have a physical cd-rom drive with another CD in the tray?



Hi John
No, it is empty.

---

### Post by Ninjagecko on 2006-12-22
I'm having the same problem -- the loopback fix doesn't work for me.

My syslog says, when it tried to load my hda1 and hda2, that it "Mounted /dev/hda# for first pass" then "Failed mounting /dev/hda#".

I frankly think it's ridiculous to release a distribution where your *installer doesn't work*

Any help would be greatly appreciated.
Thanks

---

### Post by Dr. Nick on 2006-12-22
Very Cool, Ive been wanting to do this for awhile now. I will try it next time i need to do this type of install

---

### Post by Liniment on 2006-12-22
I wish I could get to step 9 to fail. I can't even get it to load with GRUB. Whenever I try I get an error 15 cannot mount. I double checked that its the right partition and I even formatted the partition as ext3 just in case that was the problem, but nothing has worked. Any suggestions would be greatly appreciated.

---

### Post by pinkertime on 2006-12-23
**IT WORKS!!!**

This procedure does not work for me only with the desktop iso but works with the _alternate version_ (ubuntu and kubuntu). I only complain the fact that I was more interested in the desktop version to try ubuntu live. But ok thank you all.

---

### Post by goodbyegti on 2006-12-24
Hello all,

Just thought i'd add my 2 cents...

I can install Breezy badger using grub from an iso file no problem but....

kubuntu/ubuntu  6.10 desktop fail

I get the same problem john_spiral had so i try the fix here:

[http://doc.gwos.org/index.php/Install_Edgy_6.10_from_an_.iso_file](http://doc.gwos.org/index.php/Install_Edgy_6.10_from_an_.iso_file)

The iso is found but i get error:

"There was a problem reading data from the CD-ROM. Please make sure it is in the drive...."

Right away. Haven't tried the alternate versions yet...

---

### Post by akad_nedelchev on 2006-12-24
> **pinkertime said:**
> Just to give you more information I add my syslog (after the iso mounting):

 [INDENT]Dec 22 11:13:50 iso-scan: Found ISO boot/ubuntu-6.10-desktop-i386.iso on /dev/hda6
Dec 22 11:13:50 kernel: [  129.171974] ISO 9660 Extensions: Microsoft Joliet Level 3
Dec 22 11:13:50 kernel: [  129.195663] ISO 9660 Extensions: RRIP_1991A
Dec 22 11:13:50 iso-scan: Detected ISO with 'edgy' (edgy) distribution
Dec 22 11:13:52 anna-install: Queueing udeb apt-mirror-setup for later installation
Dec 22 11:13:52 iso-scan: Base system not installable from CD image, requesting choose-mirror
Dec 22 11:13:52 anna-install: Queueing udeb choose-mirror for later installation
Dec 22 11:13:52 main-menu[2757]: INFO: Modifying debconf priority limit from 'medium' to 'high' 
Dec 22 11:13:52 debconf: Setting debconf/priority to high
Dec 22 11:13:52 main-menu[2757]: DEBUG: resolver (libc6): package doesn't exist (ignored) 
Dec 22 11:13:52 main-menu[2757]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Dec 22 11:13:52 main-menu[2757]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 11:13:52 main-menu[2757]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 11:13:52 main-menu[2757]: INFO: Menu item 'load-iso' selected 
Dec 22 11:13:52 cdrom-retriever: warning: Unable to find main/debian-installer/binary-i386/Packages in /cdrom/dists/edgy/Release.
Dec 22 11:13:52 cdrom-retriever: warning: Unable to find main/debian-installer/binary-i386/Packages.gz in /cdrom/dists/edgy/Release.
Dec 22 11:13:52 cdrom-retriever: warning: Unable to find restricted/debian-installer/binary-i386/Packages in /cdrom/dists/edgy/Release.
Dec 22 11:13:52 cdrom-retriever: warning: Unable to find restricted/debian-installer/binary-i386/Packages.gz in /cdrom/dists/edgy/Release.
Dec 22 11:14:02 anna[10626]: WARNING **: bad d-i Packages file 
Dec 22 11:14:02 main-menu[2757]: INFO: Menu item 'load-iso' succeeded but requested to be left unconfigured. 
Dec 22 11:14:02 main-menu[2757]: INFO: Modifying debconf priority limit from 'high' to 'medium' 
Dec 22 11:14:02 debconf: Setting debconf/priority to medium
Dec 22 11:14:02 main-menu[2757]: DEBUG: resolver (libc6): package doesn't exist (ignored) 
Dec 22 11:14:02 main-menu[2757]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Dec 22 11:14:02 main-menu[2757]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 11:20:01 main-menu[2757]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 11:20:01 main-menu[2757]: INFO: Restoring default debconf priority 'high' 
Dec 22 11:20:01 debconf: Setting debconf/priority to high
Dec 22 11:20:01 main-menu[2757]: INFO: Menu item 'load-iso' selected 
Dec 22 11:20:01 anna[10714]: grep:  
Dec 22 11:20:01 anna[10714]: /cdrom/dists/edgy/Release 
Dec 22 11:20:01 anna[10714]: : No such file or directory 
Dec 22 11:20:01 cdrom-retriever: error: No components listed in /cdrom/dists/edgy/Release.
Dec 22 11:20:06 anna[10714]: WARNING **: bad d-i Packages file 
Dec 22 11:20:06 main-menu[2757]: INFO: Priority changed externally, setting main-menu default to 'high' (high) 
Dec 22 11:20:06 main-menu[2757]: INFO: Menu item 'load-iso' succeeded but requested to be left unconfigured. 
Dec 22 11:20:06 main-menu[2757]: INFO: Modifying debconf priority limit from 'high' to 'medium' 
Dec 22 11:20:06 debconf: Setting debconf/priority to medium
Dec 22 11:20:06 main-menu[2757]: DEBUG: resolver (libc6): package doesn't exist (ignored) 
Dec 22 11:20:06 main-menu[2757]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Dec 22 11:20:06 main-menu[2757]: INFO: Falling back to the package description for console-setup-udeb 
Dec 22 11:23:28 kernel: [  707.127671] ReiserFS: hda3: found reiserfs format "3.6" with standard journal
Dec 22 11:23:28 kernel: [  707.688587] ReiserFS: hda3: using ordered data mode
Dec 22 11:23:28 kernel: [  707.702360] ReiserFS: hda3: journal params: device hda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Dec 22 11:23:28 kernel: [  707.708107] ReiserFS: hda3: checking transaction log (hda3)
Dec 22 11:23:28 kernel: [  707.763246] ReiserFS: hda3: Using r5 hash to sort names[/INDENT]

Anyway, thank you for your help! :)

exactly the same here - kubuntu edgy - desktop ot alternate - the same thing.

---

### Post by john_spiral on 2006-12-24
> **Liniment said:**
> I wish I could get to step 9 to fail. I can't even get it to load with GRUB. Whenever I try I get an error 15 cannot mount. I double checked that its the right partition and I even formatted the partition as ext3 just in case that was the problem, but nothing has worked. Any suggestions would be greatly appreciated.

Hi Liniment,

post your menu.lst (normally in /boot/grub

and also the below command output:

sudo fdisk -l

---

### Post by john_spiral on 2006-12-24
Great news pinkertime!!!!

I've updated the HOWTO,it looks like this method will only work with the alt versions of the installer. It's important also to rename all other versions of the installer .iso file that might be lying around.

---

### Post by akad_nedelchev on 2006-12-25
my fault it was loading other iso from subfolder on some other partition - doblecheck this

rem -- i have tried now the kubuntu-6.10-alternate-i386.iso -  MD5 - 23347e2e519f0f638cf0161ae65f17f8 and still get the missing debian-installer errors ? 
is this any specific problem with the kubuntu installl ? 
shall i try ubuntu instead or the installers are the same?

10x for the excelent howto.!

---

### Post by john_spiral on 2006-12-25
> **akad_nedelchev said:**
> my fault it was loading other iso from subfolder on some other partition - doblecheck this

rem -- i have tried now the kubuntu-6.10-alternate-i386.iso -  MD5 - 23347e2e519f0f638cf0161ae65f17f8 and still get the missing debian-installer errors ? 
is this any specific problem with the kubuntu installl ? 
shall i try ubuntu instead or the installers are the same?

10x for the excelent howto.!

Hi akad_nedelchev,

The howto should work for all alt versions of the .iso. At what point do you get an error and what error do you get?

---

### Post by Ninjagecko on 2006-12-26
> **Ninjagecko said:**
> I'm having the same problem -- the loopback fix doesn't work for me.

My syslog says, when it tried to load my hda1 and hda2, that it "Mounted /dev/hda# for first pass" then "Failed mounting /dev/hda#".

I frankly think it's ridiculous to release a distribution where your *installer doesn't work*

Any help would be greatly appreciated.
Thanks


Nevermind, I decided I'm giving up on Ubuntu when I realized that even the GUI installer has a showstopper bug that's been not fixed for 2 months (hitting forward freezes the installer -- and I have very normal hardware...)

It's also ridiculous that this long-standing soapbox bugfix hasn't been incorporated into the release -- why have the hd-media installer anyway if it's been broken for months?

---

### Post by energiya on 2006-12-26
If you don't have Linux installed (yet), or just don't like using Grub there is [Gujin]("http://gujin.sourceforge.net/"). If you still have a floppy drive, it's very easy to use.

Hope this helps...

P.S.
You still have to use hd-media

---

### Post by goodbyegti on 2006-12-26
Ok, this works great with the alternative version of Ubuntu.

john_spiral, and everyone else who helped thanks a lot! :D

---

### Post by MangoSalsa on 2006-12-26
i get a different sum, how do i fix this? my sum is b950a4d7cf3151e5f213843e2ad77f. thanks, any help is appreciated.](*,)

---

### Post by drtvasudevan on 2006-12-26
> **MangoSalsa said:**
> i get a different sum, how do i fix this? my sum is b950a4d7cf3151e5f213843e2ad77f. thanks, any help is appreciated.](*,)

go to the site where you downloaded the iso file and see the mdsum for THAT iso which was downloaded.
if there is a difference you cant fix it.
it is a faulty download.
you have to re download i am afraid.
or try jigdo.
tv

---

### Post by john_spiral on 2006-12-27
> **Ninjagecko said:**
> Nevermind, I decided I'm giving up on Ubuntu when I realized that even the GUI installer has a showstopper bug that's been not fixed for 2 months (hitting forward freezes the installer -- and I have very normal hardware...)

It's also ridiculous that this long-standing soapbox bugfix hasn't been incorporated into the release -- why have the hd-media installer anyway if it's been broken for months?

Hi Ninjagecko,

Looks like you are giving up too easily!

There aren't many **_up to date_** Linux distributions that support an .iso file install.

If you find any please let us know.

John

---

### Post by john_spiral on 2006-12-27
> **energiya said:**
> If you don't have Linux installed (yet), or just don't like using Grub there is [Gujin]("http://gujin.sourceforge.net/"). If you still have a floppy drive, it's very easy to use.

Hope this helps...

P.S.
You still have to use hd-media

Hi energiya,

Gujin looks like an excellent piece of software, do you know if you can boot off .iso files located on another machine (NFS)?

---

### Post by energiya on 2007-01-03
I don't think so... 
> Gujin locates Linux kernel files by scanning all disc volumes and searching for the usual filenames in the root directory and the "/boot" subdirectory of the volume. When searching volumes for files, Gujin only understands the FAT12, FAT16, FAT32, ext2, ext3, and ISO 9660 filesystem formats. Gujin is capable of reading both the standard Linux file format and a raw (GNU zip) compressed memory image that it terms "native kernel format".
I also searched the install.txt file and it says nothing about "network" or "NFS". There is thow something about
> By the way, if you do, on a test floppy:
./instboot --full boot.bin /dev/fd0 --serial=com1,9600,n,8,1
put this floppy in the PC to boot, and link the two PCs by a crossed serial line (with or without two modems and a phone line in between)
at the bottom of the [page]("http://gujin.sourceforge.net/"), but never used crossed serial line. 

Cheers

---

### Post by stani on 2007-01-04
Thanks a lot! I just installed it on two laptops without cdrom. Before I was switching harddrives and tweaking the xorg.conf, but this is a better method. I have some humble suggestions:
1. Please add 'hd-media' to the title of your thread (eg between brackets). Now, I've bookmarked it, but otherwise it is a pain to find this thread.
2. For newbies it might be handy to mention the translation from the hda1 syntax into (hd0,0) syntax.

Stani

---

### Post by MetalHannes on 2007-01-07
Hello,
I run into the same problems as the posts above even though i try it with the alternate dapper xubuntu .iso
I'm having troubles mounting my hard drive on the command line (Its probably my fault). 
My .iso lies on a FAT32 partition wheras grub is on a ext2 partition.
Any help greatly appreciated
Hannes
EDIT: It maybe also good telling that its an old 450 MHz 75MB RAM Laptop.

---

### Post by john_spiral on 2007-01-08
> **MetalHannes said:**
> Hello,
I run into the same problems as the posts above even though i try it with the alternate dapper xubuntu .iso
I'm having troubles mounting my hard drive on the command line (Its probably my fault). 
My .iso lies on a FAT32 partition wheras grub is on a ext2 partition.
Any help greatly appreciated
Hannes
EDIT: It maybe also good telling that its an old 450 MHz 75MB RAM Laptop.

Hi MetalHannes, 

There is no need to use this method with the "alternate dapper xubuntu .iso" install.  This method is only for the edgy install.

create a grub entry that looks like the below. Follow steps 1-6 on page 1 of this thread:

title Xubuntu install
root (hd0,2)
kernel /boot/xubuntu/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd /boot/xubuntu/initrd.gz

Come back to us if you have any problems getting it to work.

Johne

---

### Post by john_spiral on 2007-01-08
> **stani said:**
> Thanks a lot! I just installed it on two laptops without cdrom. Before I was switching harddrives and tweaking the xorg.conf, but this is a better method. I have some humble suggestions:
1. Please add 'hd-media' to the title of your thread (eg between brackets). Now, I've bookmarked it, but otherwise it is a pain to find this thread.
2. For newbies it might be handy to mention the translation from the hda1 syntax into (hd0,0) syntax.

Stani

Hi Stani,

I've added "hd-media" to the title and will be adding a section on the hda1/(hd0,0) syntax. 

If you feel like improving this howto pop me a message with your additions/changes.

Johne

---

### Post by kultex on 2007-01-08
I made itup to finding the CD-Rom - I am using xubuntu-6.10-alternate

I have a strange massage on:

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0

I get: 

ln: /dev/loop0: No such file or diectory

the other thing is, that I am using a freecom traveller II - withPCMCIA-Card, that was supported  at least up to 5.10 - Ubuntu found the CD rom. So normally on this point my cd-rom was all the time found.

kultex

---

### Post by john_spiral on 2007-01-09
> **kultex said:**
> I made itup to finding the CD-Rom - I am using xubuntu-6.10-alternate

I have a strange massage on:

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0

I get: 

ln: /dev/loop0: No such file or diectory

the other thing is, that I am using a freecom traveller II - withPCMCIA-Card, that was supported  at least up to 5.10 - Ubuntu found the CD rom. So normally on this point my cd-rom was all the time found.

kultex

Hi kultex,

Strange error message? Have you completed all the steps in the howto? Correct files?

The /dev/loop0 directory is part of the initrd file structure.

From the terminal type:

[FONT="Courier New"]
cd /dev
ls l*[/FONT]

come back to us.

Johne

---

### Post by kultex on 2007-01-09
Sorry for my last posting - this happens, when you take the vmlinuz and initrd.gz from the cd

@john

thanks for this wonderful howto

I have two suggestions :

can you ad that you **_MUST_** take the two files from the archive - I am having every month troubles with my traffic limitation - so I thought I can take those from the cd

and next is the bootable floppy disk  -  I have no Windows installed and I was struggling around with the Super Grub floppy and dit not get it to work - afterwards I found gujin on the thread and it worked like a charm.

so perhaps you could add something like this:

Take the latest install version of gujin form:

[http://sourceforge.net/project/showfiles.php?group_id=15465](http://sourceforge.net/project/showfiles.php?group_id=15465)

extract the install-*,tar.gz  and make a boot floppy with the file boot.144 -  in windows with ntrawwrite ([http://ntrawrite.sourceforge.net/](http://ntrawrite.sourceforge.net/)) or dd in linux

insert the disk to the floppy and you will find any bootable file/partition available on your computer.

best regards

kultex

---

### Post by john_spiral on 2007-01-09
Hi kultex,

good to hear you are up and rolling!

Where did you place the .iso file in the above method?

---

### Post by kultex on 2007-01-09
I never changed the place - the iso, vmlinuz and initrd.gz have been always in hda5 (h0,5) in the directory /boot. 

kultex

---

### Post by drtvasudevan on 2007-01-16
> **john_spiral said:**
> ***ONLY USE THIS HOWTO IF YOU DON'T HAVE A WORKING CD DRIVE OR WANT TO SAVE THE TROUBLE OF BURNING A PHYSICAL DISC***

***THIS INSTALLATION METHOD WILL ONLY WORK WITH THE ALTERNATIVE ISO FILES OF UBUNTU/KUBUNTU/XUBUNTU***
..............................




thank you.
my son was over here and i gave him the print out of this howto.
he installed ubuntu from harddisk after a few tries.

one problem perhaps worth mentioning was that the installer searched for an iso to install.
it selected some other .iso that was in the first partition.
i had to quit and remove the iso s from the first partition after which it found the right one.

thanks once again

tv

---

### Post by john_spiral on 2007-01-16
> **drtvasudevan said:**
> thank you.
my son was over here and i gave him the print out of this howto.
he installed ubuntu from harddisk after a few tries.

one problem perhaps worth mentioning was that the installer searched for an iso to install.
it selected some other .iso that was in the first partition.
i had to quit and remove the iso s from the first partition after which it found the right one.

thanks once again

tv

Hi drtvasudevan,

good to hear you got it going!

see step (5b) for getting the installer to select the correct .iso file.

---

### Post by drtvasudevan on 2007-01-17
> **john_spiral said:**
> Hi drtvasudevan,

good to hear you got it going!

see step (5b) for getting the installer to select the correct .iso file.

that was not there when i printed that page!;) 
tv

---

### Post by L_V on 2007-01-26
> **john_spiral said:**
> 
(1) Download the _**Alternative**_ Ubuntu/Kubuntu/Edubuntu/Xubuntu .iso file and run an md5 check on it. If you are running Windows drag your .iso file onto the below program (md5sums.exe) and it will spit out a long string of characters and numbers. Make sure the string it spits out matches the published md5 sum.

md5 sums look like the following:

549ef19097b10ac9237c08f6dc6084c6  ubuntu-6.10-alternate-i386.iso

No success with KUbuntu 6.10 Alternate.
Can somebody confirms this method is compatible with KUbuntu ?

Is it planned to correct hd-media to avoid specific command lines ?

HD-media installation works very smoothly with Debian Sarge and Etch.

Other difference with Debian:
Broadcom 440x network card is OK with Debian.
Problem raised by hd-media ubuntu installation (net card not detected)

---

### Post by john_spiral on 2007-01-27
> **L_V said:**
> No success with KUbuntu 6.10 Alternate.
Can somebody confirms this method is compatible with KUbuntu ?

Is it planned to correct hd-media to avoid specific command lines ?

HD-media installation works very smoothly with Debian Sarge and Etch.

Other difference with Debian:
Broadcom 440x network card is OK with Debian.
Problem raised by hd-media ubuntu installation (net card not detected)

Hi,

Have you made sure the .iso file has the correct md5sum? 

To be honest I havn't done an install from the alternative Kubuntu .iso file, has anyone else got it working?

---

### Post by L_V on 2007-01-27
No success with:

kubuntu-6.06.1-alternate-i386.iso => e29a7bf1022e5d257b0f9d134c8b260f  
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/)
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/installer-i386/current/images/hd-media/)


kubuntu-6.10-alternate-i386.iso => 23347e2e519f0f638cf0161ae65f17f8  
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/)

+ never seen any problem with Broadcom440x network card with Debian (Sarge/Etch).

---

### Post by drtvasudevan on 2007-01-27
succeeded with ubuntu alternate amd x86 though it broke the mbr and i had to struggle to get it again. i should have said no for installation of grub and edited the existing grub.
anyway it works!
when i tried to download the alternate image with jigdo while giving the desktop cd as a source it did not find any files to use in it.
strange!
tv

---

### Post by L_V on 2007-01-28
I think the key problem I have is this one:

" never seen any problem with Broadcom440x network card with Debian (Sarge/Etch)."

Ubuntu hardware detection is stuck on this net card, and stops the process (no way to go further).

---

### Post by john_spiral on 2007-01-28
> **L_V said:**
> I think the key problem I have is this one:

" never seen any problem with Broadcom440x network card with Debian (Sarge/Etch)."

Ubuntu hardware detection is stuck on this net card, and stops the process (no way to go further).

Hi L_V,

Try skipping the network portion of the install.

Install ubuntu and then have a look into loading the same network drivers that got your Broadcom440x card working under Debian.

---

### Post by L_V on 2007-01-28
Problem solved.

The installer was looking in priority for a wrong iso on the same partition (Debian iso instead of Kubuntu iso).

The Dapper HD-media kernel was then confused.
Sorry.

---

### Post by Kane65 on 2007-02-09
I have a couple questions on this if someone wouldn't mind helping.  I'm pretty much a newbie.  I'm trying to install linux/ubuntu on an old Compaq 1270 laptop.  The cd drive is shot and it won't boot with an external so I'm having to use this method.  My questions are:

1) When I create a partition for the iso file, should it be a linux ext2 format partition or what?  I'll be using partition magic to create it and I wasn't sure.

2) Second question concerns floppy.  I created a floppy using the grub-floppy script (on another machine running linux).  The compaq boots to grub using this floppy so it's readable.  I'm not able to access the floppy in linux in order to create the menu.lst file however.  Says disk isn't accessible.

Thanks in advance

---

### Post by drizek on 2007-02-10
When I press ctrl-alt-f1, nothing happens on my laptop. I think the key might be broken or something. Is there another way to switch between the two terminals because i am stuck on ctrl-alt-f2 and cant go back to the installer.

---

### Post by pxwpxw on 2007-02-10
try alt -> or alt <- (shifts one terminal).

---

### Post by Kane65 on 2007-02-12
I finally got everything right... was having problems with several bad floppy disks... who knew disks from 1990 might not work now?

I get all the way through the part where it finds my ISO file.  However, I get the message "There was a problem reading data from the cd-rom.  Please make sure it is in the drive....." after I try to continue the install.  Does anyone have any ideas?  

*Ed.  Never mind previous, I was using the wrong ISO image.*

Thank you.

A side note... what files (besides the alternate ISO) would one use to install xbuntu the same way?

---

### Post by drtvasudevan on 2007-02-14
> **Kane65 said:**
> I
A side note... what files (besides the alternate ISO) would one use to install xbuntu the same way?

its own hard disc installer etc.

---

### Post by john_spiral on 2007-02-24
> **Kane65 said:**
> ...A side note... what files (besides the alternate ISO) would one use to install xbuntu the same way?

To install another version of Ubuntu just substitute the .iso file (remember step 6).

---

### Post by charlie_lj on 2007-04-10
I have a problem when i try to install from ISO file:
------------------------------------------------------------------------------------------------
                [!!] Load installer components from an install ISO
    No kernel modules were found. This probably is due to a mismatch
    between the kernel used by this version of the installer and the
    kernel version available in the archive.
    If you're installing from a mirror, you can work around this problem
    by choosing to install a different version of Debian. The install
   will probably fail to work if you continue without kernel modules.

   Continue the install without loading kernel modules?

     <Go Back>                                       <Yes>    <No>
------------------------------------------------------------------------------------------------
If I reply No, error continues, I can't complete the install.

actually I needn't go to step 9, installer found the iso file itself
(I can browse the /cdrom and it's the iso file)

I download the vmlinuz, intrid.gz, boot.img.gz from the link of howto
and I tried several alternate iso files (ubuntu-6.10-alternate-i386.iso, kubuntu-6.10-alternate-i386.iso), all the same result.

Can anyone help?

---

### Post by john_spiral on 2007-04-10
Hi charlie_lj,

have you renamed all other .iso files? step 6

come back to us.

John

---

### Post by Kizilbas on 2007-04-10
I installed the alternative Xubuntu 6.06 Dapper OS using a CD and it installed fine and working good now.

Is that a liveCD, when the installation began it said Xubuntu LiveCD or something like that??

---

### Post by john_spiral on 2007-04-10
Hi Kizilbas,

this HOWTO is only for mad people installing 6.1 X/K/Uubuntu alternative from an .iso file.

John

---

### Post by charlie_lj on 2007-04-11
> **john_spiral said:**
> Hi charlie_lj,

have you renamed all other .iso files? step 6

come back to us.

John

Hi John,
Yes, I renamed the Desktop ISO to *.iso.old, then try ubuntu 6.10 alternative ISO,  it failed.
And then delete this one, try Kubuntu 6.10 alternative iso, the same error...

And another question, is it posible to put the iso file on NTFS partition?

---

### Post by charlie_lj on 2007-04-11
I checkd the /proc/version, the kernel is 2.6.15-23-386 (the vmlinuz downloaded from the link)
and I think the ISO i downloaded is 2.6.17, kernel mismatch?

---

### Post by DaveQB on 2007-04-12
I am having the exact same problem here.  Is it a Feisty problem perhaps ?  Maybe I should try Edgy.

---

### Post by charlie_lj on 2007-04-12
I tried copy the vmlinuz from the ISO file, replace the one downloaded from the link
boot again, it failed at the stap SCAN ISO. 

Go to terminal 2, i found /dev/loop/0 already there, but it's empty in /cdrom
i can mount the FAT32 partition which contain the ISO, but i can't mount iso as loop device.

---

### Post by DaveQB on 2007-04-12
> **charlie_lj said:**
> I tried copy the vmlinuz from the ISO file, replace the one downloaded from the link
boot again, it failed at the stap SCAN ISO. 



Doing that here got me execution errors when hardware scan started, then it was stuck in a loop.

I have downloaded Edgy ISO (alternate), so will try that tonight with the Edgy version of 3 boot/installer files.

We'll see.

---

### Post by john_spiral on 2007-04-15
> **charlie_lj said:**
> Hi John,
Yes, I renamed the Desktop ISO to *.iso.old, then try ubuntu 6.10 alternative ISO,  it failed.
And then delete this one, try Kubuntu 6.10 alternative iso, the same error...

And another question, is it posible to put the iso file on NTFS partition?

Hi Charlie,

start with basics you have downloaded the correct vmlinuz & initrd.gz files from:

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/")

create a new entry in GRUB to make sure it's referencing the correct files:

ubuntu 6.10 alternative ISO
vmlinuz (downloaded from above URL)
initrd.gz (downloaded from above URL)

I'm sure a NTFS partition should be fine should be fine filesystem for the files.

check your **/boot/grub/device.map** to see what drive number grub is assigning to the above NTFS drive?  

All other .iso files on all discs & partitions must be renamed just to be sure.

From your last post it sounds like the wrong vmlinuz file is being loaded by GRUB.

come back to us.

John

---

### Post by john_spiral on 2007-04-15
> **DaveQB said:**
> I am having the exact same problem here.  Is it a Feisty problem perhaps ?  Maybe I should try Edgy.

Hi DaveQB,

This HOWTO is only for installing U/K/X-buntu 6.1 from alternative .iso files.

Is there a working .iso install method for Feisty?

---

### Post by john_spiral on 2007-04-15
> **DaveQB said:**
> Doing that here got me execution errors when hardware scan started, then it was stuck in a loop.

I have downloaded Edgy ISO (alternate), so will try that tonight with the Edgy version of 3 boot/installer files.

We'll see.

Hi All,

please use the vmlinuz & initrd.gz files from the below site:

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/")

The vmlinuz & initrd.gz files from the .iso have been coded for an install from a physical CD and will not work for an .iso based install.

thanks

John

---

### Post by charlie_lj on 2007-04-15
> **john_spiral said:**
> Hi Charlie,

start with basics you have downloaded the correct vmlinuz & initrd.gz files from:

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/")

create a new entry in GRUB to make sure it's referencing the correct files:

ubuntu 6.10 alternative ISO
vmlinuz (downloaded from above URL)
initrd.gz (downloaded from above URL)

I'm sure a NTFS partition should be fine should be fine filesystem for the files.

check your **/boot/grub/device.map** to see what drive number grub is assigning to the above NTFS drive?  

All other .iso files on all discs & partitions must be renamed just to be sure.

From your last post it sounds like the wrong vmlinuz file is being loaded by GRUB.

come back to us.

John

Thanks John,

I'm sure that I have downloaded the files from the same link. 
(But actually I download with some problems, intrid.gz is 4.2M, but after downloaded by IE, it's about 10M)
So I use Firefox download them again.

And I check the partition, i found there is another ISO file (not ubuntu, damn it, i didn't realize it effect the installation)
After deleted the iso, reboot OK, now i can enter to the installation panel...

---

### Post by rush_ad on 2007-04-23
> **john_spiral said:**
> ***ONLY USE THIS HOWTO IF YOU DON'T HAVE A WORKING CD DRIVE OR WANT TO SAVE THE TROUBLE OF BURNING A PHYSICAL DISC***

***THIS INSTALLATION METHOD WILL ONLY WORK WITH THE ALTERNATIVE ISO FILES OF UBUNTU/KUBUNTU/XUBUNTU***

Hi,

Below is a micro step-by-step procedure for installing Ubuntu 6.10 from an .iso file. The below procedure might also be useful for installing Kubuntu/Edubuntu & Xubuntu.

Before I go any further I’m still relatively new to Ubuntu and would appreciate your help in refining/correcting this HOWTO and answering questions.

(1) Download the _**Alternative**_ Ubuntu/Kubuntu/Edubuntu/Xubuntu .iso file and run an md5 check on it. If you are running Windows drag your .iso file onto the below program (md5sums.exe) and it will spit out a long string of characters and numbers. Make sure the string it spits out matches the published md5 sum.

[http://www.pc-tools.net/files/win32/freeware/md5sums-1.2.zip](http://www.pc-tools.net/files/win32/freeware/md5sums-1.2.zip)

md5 sums look like the following:

549ef19097b10ac9237c08f6dc6084c6  ubuntu-6.10-alternate-i386.iso

(2) Before installing Ubuntu you will need to partition your drive. In essence you will need to boot from another media either a floppy, 2nd drive or USB key and run some type of partition software. Create one new partition for the Ubuntu installation, one to hold the .iso file & additional boot files (say 700megs). You might need to resize your existing OS to make space for the above 2 partitions.
 
(3) Install grub onto either a floppy or hard drive and create a similar entry in your menu.lst file:

title Install Ubuntu
root (hd0,2)
kernel /boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd /boot/initrd.gz

**([COLOR="Red"]hd0,2[/COLOR]) refers to the 1st hard drive [COLOR="Red"]'hd0'[/COLOR] and the 3rd partition [COLOR="Red"]'2'[/COLOR].

The counting of partitions and hard drives starts at zero. Linux loves making life complicated ;-)

Change (hd0,2) to match the drive and partition of your .iso file.

e.g (hd1,3) Refers to drive 2 and partition 4.  

(4) **_Download_** the vmlinuz & initrd.gz files from the below site (DON'T USE vmlinuz & initrd.gz FILES FROM .iso) :

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/)

(5) Plonk the .iso, vmlinuz & initrd.gz files onto the newly created partition from step (2) in a /boot directory. 

(6) **_NB_** Make sure all other Ubuntu/Kbuntu/Xubuntu/Debian .iso installer files have been renamed to .iso.somethingelse, this will prevent the installer from picking up the wrong .iso file.

(7) Boot the machine from the hard disk or floppy that has grub installed, you should see a menu that contains ‘Install Ubuntu’. Select ‘Install Ubuntu’ and press enter.

(eight) Next run through the installation until it fails to find the .iso file. Then change to terminal 2 with (Ctrl-Alt-F2). Hit enter to activate this console.

(9) Type the below commands in terminal 2:

mkdir -p /dev/loop 
ln /dev/loop0 /dev/loop/0 

(10) Change back to terminal 1 (Ctrl-Alt-F1), scan again and the ISO will be detected.

(11) Voila! The install should be working.

Thanks to all the helpful people on the forums for getting this procedure to work.

Thanks also to the busybox mailing list!

i just want to add that this guide works on feisty fawn with appropriate adjustments. very helpful, thanks.

---

### Post by john_spiral on 2007-04-25
> **rush_ad said:**
> i just want to add that this guide works on feisty fawn with appropriate adjustments. very helpful, thanks.

Hi rush_ad,

did the installer from:

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/)

work without having to make the below steps?

[COLOR="Silver"]
(7) Boot the machine from the hard disk or floppy that has grub installed, you should see a menu that contains ‘Install Ubuntu’. Select ‘Install Ubuntu’ and press enter.

(eight) Next run through the installation until it fails to find the .iso file. Then change to terminal 2 with (Ctrl-Alt-F2). Hit enter to activate this console.

(9) Type the below commands in terminal 2:

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0

(10) Change back to terminal 1 (Ctrl-Alt-F1), scan again and the ISO will be detected.[/COLOR]

---

### Post by rush_ad on 2007-04-27
> **john_spiral said:**
> Hi rush_ad,

did the installer from:

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/)

work without having to make the below steps?

[COLOR="Silver"]
(7) Boot the machine from the hard disk or floppy that has grub installed, you should see a menu that contains ‘Install Ubuntu’. Select ‘Install Ubuntu’ and press enter.

(eight) Next run through the installation until it fails to find the .iso file. Then change to terminal 2 with (Ctrl-Alt-F2). Hit enter to activate this console.

(9) Type the below commands in terminal 2:

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0

(10) Change back to terminal 1 (Ctrl-Alt-F1), scan again and the ISO will be detected.[/COLOR]

In short, yes. it worked. i just had to change my vgs settings because i have a very old video card and monitor

---

### Post by TheByteRaper on 2007-04-28
I want to install Feisty on my notebook, downloaded the alternate version and the Feisty vmlinuz and initrd.gz.
It took me quite some time to find out how even to create a boot floppy with grub installed on it :D (I tried it [that]("http://gentoo-wiki.com/HOWTO_Bootable_Floppy_with_GRUB") way, maybe you could add that tutorial to your howto, there are enough newbies out there like me ^^ ...)
Ok, now I'm stuck between setp (7) and (eight).
GRUB is loading, and I "Install Ubuntu". But then this error shows up:

Error 17: Cannot mount selected partition.

I edited the menu.lst to "root (hd0,1) -> I have partitioned my drive and split it up in two parts (in Windows-terms: C: and D:). I inserted all the needed files in the /boot directory on D:.
Then I tried to start the system from the floppy, and the GRUB screen showed up. Then the error. First I thought: "Err, ok, D: it's NTFS, maybe GRUB can't read it." Then I formatted D: with FAT32, because I thought it would make a difference. Well, nothing changed ^^ still Error 17.

Logically, the D: Partition has to be (hd0,1)... I have no other drives in my notebook :( C = hd0,0 and D: = hd0,1 ... what else? O_o 

Did I miss something or what did go wrong?

Sorry for my crappy english ;D

=========
Edit:

Ehm,.. nevermind... I started the grub-command (pressing "c" in the GRUB menu) and used the command "find /boot/vmlinuz". It returned (hd0.4).... don't ask me how the D:-partition ended up at hd0,4... edited the root-values and now the install is working. Let's see how the whole story ends ;)

As said, nevermind, I was just too hasty ^^

---

### Post by uppercase on 2007-05-13
> **john_spiral said:**
> Hi rush_ad,

did the installer from:

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/)

work without having to make the below steps?

[COLOR="Silver"]
(7) Boot the machine from the hard disk or floppy that has grub installed, you should see a menu that contains ‘Install Ubuntu’. Select ‘Install Ubuntu’ and press enter.

(eight) Next run through the installation until it fails to find the .iso file. Then change to terminal 2 with (Ctrl-Alt-F2). Hit enter to activate this console.

(9) Type the below commands in terminal 2:

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0

(10) Change back to terminal 1 (Ctrl-Alt-F1), scan again and the ISO will be detected.[/COLOR]

-----------------------

I just installed ubuntustudio (DVD) iso using this guide thanks! :guitar: 

I used the above quoted link to get the installer files and steps 7 through 9 were not required.

Appreciate the HOW TO for this, saved me moving my dvd drive between desktops thanks!

---

### Post by amir907 on 2007-05-29
Thank you, It is working.
Ware can one find Xubuntu 6.10 ? Will it work the same?
Amir:)

---

### Post by john_spiral on 2007-05-30
> **amir907 said:**
> Thank you, It is working.
Ware can one find Xubuntu 6.10 ? Will it work the same?
Amir:)

Xubuntu will work the same, remember to pickup the alternative version from [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by amir907 on 2007-05-31
Hi John,
Thanks, it is working.

Laptop= Toshiba 3025CT (same as 3020CT)
CPU=300 Mhz  Pentium II MMX
Memory=94Mb (max)
HD=6Gb

WinME is working in first partitionon 1.5Gb, 4.5Gb left for D=800Mb, E=800Mb, and the rest for Xubuntu 

Was installed without a network connection, also 3com 3CCFE574BT netcard was in PCMCIA port.

Installation process said: "No network card found"

Want to make updates and after that make upgrade to 7.04

Can you help with that problem? status command didn't recognize any PCMCIA device.

Thank you  :)

---

### Post by homunq on 2007-06-01
I'm trying to install from HD using a DVD image (iso) of Fiesty Fawn.  I get into the installer, detect the iso, but during the base system install I get an error from debootstrap that file:///cdrom/pool/main/c/console-setup/console-setup?1.13ubuntu13_all.deb was corrupt. Followed by many more errors of the same nature. I suspect it's that something in my image is still hard-coding to look for the CD and not on the image on the hard disk. I'll try it with a CD rather than DVD image, but just sharing in case someone else plans to use the DVD iso.

---

### Post by homunq on 2007-06-01
re above: I'm on 7.04

---

### Post by john_spiral on 2007-06-02
> **amir907 said:**
> Hi John,
Thanks, it is working.

Laptop= Toshiba 3025CT (same as 3020CT)
CPU=300 Mhz  Pentium II MMX
Memory=94Mb (max)
HD=6Gb

WinME is working in first partitionon 1.5Gb, 4.5Gb left for D=800Mb, E=800Mb, and the rest for Xubuntu 

Was installed without a network connection, also 3com 3CCFE574BT netcard was in PCMCIA port.

Installation process said: "No network card found"

Want to make updates and after that make upgrade to 7.04

Can you help with that problem? status command didn't recognize any PCMCIA device.

Thank you  :)

Hi amir,

why not install the latest Ubuntu from a ubuntu-7.04-alternate-i386.iso file.

you will need to get the initrd.gz & vmlinuz files from the below location:

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/)

john

---

### Post by john_spiral on 2007-06-02
> **homunq said:**
> I'm trying to install from HD using a DVD image (iso) of Fiesty Fawn.  I get into the installer, detect the iso, but during the base system install I get an error from debootstrap that file:///cdrom/pool/main/c/console-setup/console-setup?1.13ubuntu13_all.deb was corrupt. Followed by many more errors of the same nature. I suspect it's that something in my image is still hard-coding to look for the CD and not on the image on the hard disk. I'll try it with a CD rather than DVD image, but just sharing in case someone else plans to use the DVD iso.

Hi homunq,

try the latest Ubuntu, see above post.

remember to run a md5sum check on the .iso file.

---

### Post by YodaJones on 2007-06-02
I have been trying to get a Feisty HDD install working with this method without success.

I am a Ubuntu/Linux newbie and I am afraid that these directions are either incomplete, or above my head.

For example how is grub installed exactly?  Some of the steps listed here could be more detailed IMHO.

Has anyone written a more clear (read easy) set of steps to accomplish this?

Thanks

---

### Post by john_spiral on 2007-06-03
> **YodaJones said:**
> I have been trying to get a Feisty HDD install working with this method without success.

I am a Ubuntu/Linux newbie and I am afraid that these directions are either incomplete, or above my head.

For example how is grub installed exactly?  Some of the steps listed here could be more detailed IMHO.

Has anyone written a more clear (read easy) set of steps to accomplish this?

Thanks

Hi YodaJones,

I recommend using a CD if you are a Linux newbie, only use this method if you don't have a working CD-ROM.

What step did you reach?

---

### Post by YodaJones on 2007-06-03
Hi John,

Originally I had not seen this thread so I had started one at:

[http://ubuntuforums.org/showthread.php?t=461814](http://ubuntuforums.org/showthread.php?t=461814)

The laptop (Dell inspiron 4000) I am trying to install to has:

No CDROM drive
No functioning floppy drive
No boot from USB option in the BIOS
No bootable OS on the HDD (wiped)

I have removed the HDD from the laptop and installed in in an external USB HDD housing, connected it to a UbuntuStudio (7.04) system and gparted it with 2 partitions.  The first one just over 1 GB and the second one the remainder of the HDD capacity (approximately18 GB).

I don't seem to have been able to get grub installed.
When I boot the laptop with the HDD re-installed it say there is no bootable system.

I have downloaded the files and copied them to the 1 GB partition.

Thats about as far as I got.

---

### Post by john_spiral on 2007-06-03
> **YodaJones said:**
> Hi John,

Originally I had not seen this thread so I had started one at:

[http://ubuntuforums.org/showthread.php?t=461814](http://ubuntuforums.org/showthread.php?t=461814)

The laptop (Dell inspiron 4000) I am trying to install to has:

No CDROM drive
No functioning floppy drive
No boot from USB option in the BIOS
No bootable OS on the HDD (wiped)

I have removed the HDD from the laptop and installed in in an external USB HDD housing, connected it to a UbuntuStudio (7.04) system and gparted it with 2 partitions.  The first one just over 1 GB and the second one the remainder of the HDD capacity (approximately18 GB).

I don't seem to have been able to get grub installed.
When I boot the laptop with the HDD re-installed it say there is no bootable system.

I have downloaded the files and copied them to the 1 GB partition.

Thats about as far as I got.

We do like a challenge!

Try this lateral approach:

(1) Connect Laptop USB HDD onto "UbuntuStudio (7.04)" system.
(2) Disconnect all other hard drives except Laptop USB HDD, or disable internal hdd drives inside BIOS (safer to disconnect drives).
(3) Boot from Ubuntu CD.
(4) Install Ubuntu onto Laptop USB HDD, you will need to choose the 18 gig partition as the destination.
(5) Check Ubuntu boots from laptop USB HDD on "UbuntuStudio (7.04)" system, you can skip this step if your system can't boot from USB.
(6) Reconnect other hard drives - keep laptop drive connected, set system to boot from original (7.04) system hard disk .
(7) mkdir (make directory) on 1gig USB partition called /boot/ubuntu7 , you will more than likely be creating a directory on sda1 or sda2 , use the **sudo fdisk -l** command to see what the USB drive is called.
(8 )Copy ubuntu-7.04-alternate-i386.iso & initrd.gz , vmlinuz files from the below location:

[http://archive.ubuntu.com/ubuntu/dis...ages/hd-media/](http://archive.ubuntu.com/ubuntu/dis...ages/hd-media/)

to newly created /boot/ubuntu7 (USB hdd partiton 1gig) directory.

(9) edit /boot/grub/menu.lst file (18gig USB partition)so it has the following entry:

title Install Ubuntu
root (hd0,0)
kernel /boot/ubuntu7/vmlinuz vga=normal ramdisk_size=14972 root=/dev/sda1 rw --
initrd /boot/ubuntu7/initrd.gz

NOTE** you might need the below command to see what the 18gig partition is called.

sudo fdisk -l

(10) Place hdd back into laptop, select the above entry on the grub boot screen, cross your fingers & see what happens.

Please come back to me either way.

---

### Post by YodaJones on 2007-06-04
Hi John,

Thank you for the tip.  I will do this tonight, or tomorrow night and write me experience here for you and all to see. 
The computer with the Ubuntu Studio installed in in a rack with mucho cables which are kinda tight.

Does it matter that the Ubuntu Studio system is SATA and the laptops drive is ATA?  I presume that the tower Ubuntu Studio system has both on the motherboard.

---

### Post by john_spiral on 2007-06-04
> **YodaJones said:**
> ...Does it matter that the Ubuntu Studio system is SATA and the laptops drive is ATA?  I presume that the tower Ubuntu Studio system has both on the motherboard.

Hi,

The whole dance above is to get grub on the drive without playing too much with the command shell. 

I googled "Grub install" and most of the hits looked too painful, so I came up with this approach. 

step (9) might need to read:

title Install Ubuntu
root (hd0,0)
kernel /boot/ubuntu7/vmlinuz vga=normal ramdisk_size=14972 root=**/dev/hda1** rw --
initrd /boot/ubuntu7/initrd.gz

note the bold difference.

I hope you are successful. Please come back to us either way

---

### Post by YodaJones on 2007-06-27
Hi John!

I finally was able to get back to this matter.
I used your 9 step process with the change you suggested in your last post (/dev/hda1).  I was able to get the setup to run, however when I got to the disk partitioning part of the installation I found myself in a loop because I was unable to create/modify the partitions on the drive.

So I did some checking and found that indeed installing grub alone is kind of funky, but I managed to get it working.  I gparted the drive again by removing it from the insides of the laptop and installing in a empty USB drive caddy which I then plugged into a running Ubuntu system.

This time the installation ran like a champ!

You are not going to believe this part:  When I finally got the laptop running the display is not working properly.  It is af iff the display is divided vertically into thirds.  On the left hand side of the screen you can see the menu's (applications, Places and System) however the center "third" and the right hand "third" of the screen repeat the normal right hand side of the screen (power off icon, date/time).  I suppose that there is a display driver issue now.

This computer ran windows properly, so I do not believe that the problem is hardware.  Also the text mode installation ran properly, although small since it seemed that the script vga=normal forces perhaps 640x480 mode.

This is a Dell Inspiron 4000 laptop.  I am not sure what the display adapter is inside.

Some additional info:  I can logon to the laptop, it is just impossible to do anything since everything that gets displayed is missing the right side, like menu's and dialog boxes.  To logon I must do so blind because I cannot see the text box where the username and password go.

So this has been quite a ride.  I struggled to get Ubuntu on this laptop (and it does run nice and quick!) only the display is a issue now.

Any suggestions?

Thanks!
John

---

### Post by Dr. Nick on 2007-06-28
@yoda, try to start in the recovery mode from grub. You can manipulate your video setting from their using the file /etc/X11/xorg.conf 

At everyone. I just used the process with gusty. Had a text mode dapper install and I used its grub menu to do this. Made a /boot on another ext3 partition and dropped the alternate-gusty and the 2 files from the online archive for gusty in the folder. The install picked up the iso first time without me switching consoles. It warned me about not loading kernel modules and said the install will probably fail, well it didnt find my lan card but since i had the iso no network was needed anyway. It installed fine and booted perfectly :)

---

### Post by john_spiral on 2007-06-28
Hi YodaJones,

Dr. Nick's suggestion about editing the /etc/X11/xorg.conf file is valid but you might run into more problems for the following reasons:

Your laptop hard drive now has a copy of Ubuntu that's meant to run on your UbuntuStudio/Desktop system. You might get it to work by editing lots of files like the above /etc/X11/xorg.conf file, but it will mean more pain in the long run.

I personally think it will be easier to go back to this stage:

> **YodaJones said:**
> I used your 9 step process with the change you suggested in your last post (/dev/hda1).  I was able to get the set-up to run, however when I got to the disk partitioning part of the installation I found myself in a loop because I was unable to create/modify the partitions on the drive.

Choose the 'Manual' option on the below '[!!]  Partition disks' screen:

[IMG]http://safewaytobank.com/2.png[/IMG]

I unfortunately do not have screen shots for the next section. You will need to specify your large partition
hda2 as your root, home etc... proceed from here.

Choose not to install Grub as it is already installed.

You should now have a copy of Ubuntu installed but correctly configured for your laptop hardware.

It might not boot as the Grub entry will be configured for the UbuntuStudio/Desktop system? Try editing the Grub entry so root points to:

title Ubuntu, kernel 2.6.20-16-generic
root (hd3,0)
kernel /boot/vmlinuz-2.6.20-16-generic **root=/dev/hda2** ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

notice **root=/dev/hda2** change. Once you get into Ubuntu edit the menu.lst file so the **root=/dev/hda2** edit is permanent.

Please come back to us either way. I know this seems like a very long painful process but you will be helping lots of people in a similar predicament.

Ciao

John

---

### Post by john_spiral on 2007-06-28
> **Dr. Nick said:**
>  It warned me about not loading kernel modules and said the install will probably fail, well it didnt find my lan card but since i had the iso no network was needed anyway. It installed fine and booted perfectly :)

Hi Dr. Nick,

did you choose the vmlinuz & initrd.gz files from the **gusty** download site?

John

---

### Post by Dr. Nick on 2007-06-28
> **john_spiral said:**
> Hi Dr. Nick,

did you choose the vmlinuz & initrd.gz files from the **gusty** download site?

John

Yep, chose them from the gusty site and got the alternate cd via bit torrent. They had a /current folder and 2 others that had dates in them. I just got the one out of /current so maybe it was newer then the last iso released.

As I said It installed fine and I didnt have to drop to terminal 2 and run any commands at all, After I renamed all the other .iso files I had, it picked the alternate up automatically.

Due to the kernel modules I had no network card, but that didnt hurt at all. Network worked on first reboot and I had a kernel update waiting for me then, Which leads me to think that the kernel I had on the iso was the version just before the vmlinuz and initrd  from /current causing the mismatch.

I imagine once gusty is final that issue will disappear.

---

### Post by YodaJones on 2007-06-29
Hi John,

I will have time tomorrow (Saturday) to try your suggestions.

Interestingly, when Ubuntu (7.04) boots the pre-login screens display perfectly.

I tried to use "Envy" but it said that there were no drivers for my card.  I was able to determine that the laptop has a "Rage Mobility M3 AGP 2X" in case that helps find a solution.

John

---

### Post by martin lawrence olivier on 2007-07-24
I only have windows installed on the machine I am trying to move Feisty onto and my only boot option aside from the hard drive is to USB but I do not have the original USB floppy drive hardware the BIOS probably expects.  Anyways, is there anyway to install GRUB without already having linux?  Can I reference an ISO that is on a Windows partition?  Is there any hope for me or should I start buying USB drives in the hope that one will be bootable?

---

### Post by Dr. Nick on 2007-07-24
Just to confirm,  Burning the iso as a cd image and booting off the cd are not a possibility in your case?

If you can that is always the easiest method, If not though thier is still some hope.

It looks like your machine doesnt have a boot from cd option from what you said.


You can install grub in windows from here
[https://sourceforge.net/projects/grub4dos/](https://sourceforge.net/projects/grub4dos/)

and it can be setup to read the iso off a windows partition I believe. The only problem is this.

If you only have one partition then you will have to wipe your windows partition out in the installer, including grub and the .iso you will install from. You may be able to resize the partitions and work around it somehow.

---

### Post by DaveQB on 2007-07-25
Definitely the partitioning will be the problem.  Cant boot with gparted LiveCD etc.

I would suggest pulling the Hard disk out and doing all the work on it in another, more modern PC.  You can partition it while in Linux on another system [LiveCD or an install OS] and get the iso on to it all ready to go.

Also, unlike Windows, you could do the whole install on the other system and them plunk the HDD back into the original system and all done, ready for you to use.

---

### Post by martin lawrence olivier on 2007-07-25
I already considered doing that but I dont really have access to another computer in that way and furthermore i'm pretty sure the hard drive in this has a proprietary connector.  this thing is like the size of a big paperback.

---

### Post by john_spiral on 2007-07-27
Hi martin lawrence olivier,

have a look at the below page:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

see the section titled 'The CD image approach'

come back to us.

---

### Post by martin lawrence olivier on 2007-07-28
thanks for the help everyone.  I'm posting this from ubuntu right now.  I did end up finding that page linked above, which helped me a lot.  it turned out that the two problems i was having were that grub4dos wouldn't mount anything but the first partition (which i solved by putting the iso/kernel/initrd there) and the install eventually objected to me using an iso with a different kernel than the one i was running.  That i solved by using the kernel/initrd from the iso to from grub4dos, so no problem.

I didn't even realize though that it was possible to do a network install that pulled files from the ubuntu archive itself!  i thought you needed a local server to do that!  I ended up using the network install more or less by accident, which took a while (24 hours with me not watching it the whole time) but by golly it worked.

thanks again!

---

### Post by Dr. Nick on 2007-07-28
I knew their was a network install at one time, wasnt sure if it was still available though.

Glad it worked out for you. Those sort of installations are tricky and frustrating at times. Usually if you have any errors you have to start back at the start and redownload.

Know that you have it installed I hope you made 2 partitions so you can backup easier. A 2nd partition will also help if you need to reinstall now, I have mine setup so i can download a iso to a backup partition and then modify the installed grub to boot off that iso using this threads method. Helps me avoid burning cds or doing network installs each time

---

### Post by TwistedGrim on 2007-07-29
Hi I have been struggling with getting Ubuntu working on my small Pentium 3 sony laptop. I have a PCG-SR17 Vaio, which **_did not_** include a PCMCIA CDROM or USB Floppy nor did I ever get one. I had got by with Windows ME/XP and know how to install those but am looking to install 7.04 now. I am typing from the 64 bit version on my desktop so I sorta know how to get it working but the problem is its a bit harder on my laptop. I have tried and succeeded getting Knoppix working from an iso using the grub installer they used but it was extremely slow on my laptop. I had a problem with having bad sectors and got that fixed via spinrite and finally was able to repartition the 20GB drive with partition magic 8. 

My problem is that I got grub installed, I have tried the knoppix grub and  grub4dos with the CD installer like used in a few posts above. I downloaded the vmlinuz and initrd.gz from the fiesty fawn site and started doing your steps. I am having an error 19 cannot mount selected partition , partitioned it as a fat32 partition after my primary winxp partition following empty space to be partitioned by the install for linux install. 

booting 'Install Ubuntu'
root (hd0,1)
Filesystem type unknown, partition typ 0xf
kernel blah blah see below

error 19: Cannot mount selected partition

> title Install Ubuntu
root (hd0,1)
kernel /boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd /boot/initrd,gz


Am I supposed to use NTFS or ext3 or something? i'm kinda baffled and to the point i'm not sure what to do. Is there a certain GRUB that is precompiled I should be using or somewhere to download the version?

---

### Post by DaveQB on 2007-07-29
output of sudo fdisk -l ?

Your aiming for /dev/hda2 ?

---

### Post by TwistedGrim on 2007-07-29
not quite sure what /dev/hda2 but i guess your trying to make sure I got the partitions setup right
I am running only 1 HDD and in windows under partition magic it shows windows partition then install partition then empty unpartitioned space  hence (hd0,1) hard drive 1 partition 2 as I understand it. I dont have linux running ATM so I cannot do any sudo fdisk command as I see?

I dont see anywhere to download a version of GRUB that should work with this install I guess is my problem?
[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/) has it but complile it? which version?

---

### Post by TwistedGrim on 2007-07-29
success I downloaded wingrub and it works like a charm.  DaveQB you were correct my actually partition # was not 0,1 but 0,4 for some reason. I guess partition magic kinda screwed it up. Installing it put the swap file as partition 6 and install as partition 3 makes no sense other than maybe because its some form of extended partition. john_spiral I would highly suggest you have people use wingrub or atleast post about it on your how-to. It has a partition list and installs grub very easily from windows. Had everything right except for a 1 instead of a 4. Great how too thanks.!

---

### Post by Dr. Nick on 2007-07-29
The partitions are not always consistent depending on primary/logical. If unsure just edit the grub command for boot by pressing 'E' at the screen and plugging n different numbers, saves multiple edits of the grub.conf or menu.lst files

---

### Post by wandaa on 2007-08-14
hello, I have gotten my hands on an old laptop, which has enough power to run xubuntu, but thats pretty much it, and I just found out that the cd drive is broken (:() NOW, I am a newbie at linux and stuff and from what I've been googling the last few days I haven't found out how to install grub onto a floppy from windows (I dont have any installs of linux atm in my house... :confused:) I also am wondering that can I just install 7.04 (or what ever is the newest linux) straight away, or do I have to install 6.10, from what I've read from this thread, it looks like I CAN install the newest one, but didn't really get how to do that, and well, I think I can manage the rest :P I hope, I'm pretty sure you will be hearing of me more soon =(

edit: found grub4dos link... :) 1 problem (almost) solved
edit2: dont really understand that grub4dos, might be due to being this tired, im off to bed, be back tomorrow =)

---

### Post by john_spiral on 2007-08-15
Hello wandaa,

Does your machine have a copy of Windows on it? If so right click on your C: drive and see what file system it uses, NTFS or FAT?

In essence you will need to boot off a floppy that will allow you to partition (split up) your hard drive.

It doesn't matter if the floppy can only make NTFS or FAT partitons.

run a google on:

**floppy make partitions**

choose a suitable tool.

Once you have an extra partition on your drive follow the [[COLOR="Blue"]Installation From Windows guide[/COLOR]]("https://help.ubuntu.com/community/Installation/FromWindows"). 

Choose the alternative version of (7.4) Xubuntu with the relevant vmlinuz & initrd.gz files.

install to the newly created partition. 

**See the 1st page of this howto for more info.**

Please come back to us, I'm sure we will get you up and running.

John

> **wandaa said:**
> hello, I have gotten my hands on an old laptop, which has enough power to run xubuntu, but thats pretty much it, and I just found out that the cd drive is broken (:() NOW, I am a newbie at linux and stuff and from what I've been googling the last few days I haven't found out how to install grub onto a floppy from windows (I dont have any installs of linux atm in my house... :confused:) I also am wondering that can I just install 7.04 (or what ever is the newest linux) straight away, or do I have to install 6.10, from what I've read from this thread, it looks like I CAN install the newest one, but didn't really get how to do that, and well, I think I can manage the rest :P I hope, I'm pretty sure you will be hearing of me more soon =(

edit: found grub4dos link... :) 1 problem (almost) solved
edit2: dont really understand that grub4dos, might be due to being this tired, im off to bed, be back tomorrow =)

---

### Post by dam2 on 2007-08-17
Hello,
First I m a newbe.
I followed the guide to install on the hard disk.
My version is Xubuntu 7.04 and I took the vmlinuz & initrd.gz from ubuntu version 7.04 from here :
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/)

two strange things :
first, the iso file has been found automatically, I didn t need to write

[HTML]mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0[/HTML]

Well, or I couldn't because no problem occured.

Second, at the end I reboot everything (I have another mini distro on the computer called Puppy linux), and I chose Ubuntu as a choice (I believe he thinks the version is ubuntu but the iso was XUbuntu). However, after I enter my password, there is nothing. The xubuntu screen is not coming and I m stuck in console mode...:confused:

Did somebody have the same problem,
Can somebody help ?

Thank you,
DAM

---

### Post by john_spiral on 2007-08-17
Hi,

To answer your questions:

> **dam2 said:**
> 
first, the iso file has been found automatically, I didn t need to write

[HTML]mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0[/HTML]

Well, or I couldn't because no problem occured.

The install has been fixed for versions 7.04 / 7.10 and above. No need for the mkdir.... dance.

> **dam2 said:**
> 
Second, at the end I reboot everything (I have another mini distro on the computer called Puppy linux), and I chose Ubuntu as a choice (I believe he thinks the version is ubuntu but the iso was XUbuntu). However, after I enter my password, there is nothing. The xubuntu screen is not coming and I m stuck in console mode...:confused:


 I can't remember if the alternative install comes with a window manager (GNOME/KDE/XFE) pre-installed ?

try:

**startx**

from the command line?

Please come back to us.

---

### Post by dam2 on 2007-08-18
Hello John_Spirale,
Thank you fro your following.
So, I wrote startx
and I got 
the program 'startx' is not currently installed. You can install it by typing : sudo pat-get install xinit

I type it, the computer is proceeding, ask password, ok

I'm asked : after unpacking 496kB of additionnl disk space will be used. Do you want to continue ? 

Yes

But the he askes to instert the disc labeled Xubuntu in the drive /cdrom/ and to press enter

That is no chance because I have no CDROM, and that is why I used this method... hum


I'm stuck here right now.
Maybe I can force him to startx during the installation but I don't know how
Maybe he can look in the computer, but the program is stuck asking me to install from the cd rom.

I hope I'm precise enough,
Looking for support,

Cheers,
DAM

---

### Post by john_spiral on 2007-08-19
> **dam2 said:**
> ...But the he askes to instert the disc labeled Xubuntu in the drive /cdrom/ and to press enter

That is no chance because I have no CDROM, and that is why I used this method... hum

Dam,

There is a solution:

(STEP 1)

at the prompt type:

[B]sudo mount -o loop [COLOR="Red"]cd.iso[/COLOR] /mnt/image
sudo rm /cdrom
sudo ln -s /mnt/image /cdrom
sudo apt-cdrom -m add[/B]

In the above change [COLOR="Red"]**cd.iso**[/COLOR] to the name of the x/u/k/buntu iso file.

the above dance makes your x/u/k/buntu iso file behave like a real cd-rom.

(STEP 2)

I got most of the below steps from the [[COLOR="Blue"]**Installation/LowMemorySystems**[/COLOR]]("https://help.ubuntu.com/community/Installation/LowMemorySystems") page:

next type the below:

**sudo aptitude install xorg**

This will install the X window server, aptitude is a command similar to apt.

Step (3)

Adding a Window Manager:

Now for the exciting part, a Window manager is like Windows Vista or MacOS.it's the beautiful interface we interactive with while we are using a computer.

Unlike Microsoft Windows or MacOS you have the option to install more than one interface.

I'm guessing you have a system that is slightly long in the tooth so can I suggest you use XFE (the default interface for Xubuntu) or Fluxbox (for a very fast interface) or if like me you like the feel of something fast, pretty but slightly less stable go for Enlightenment.

to install XFE:

**sudo aptitude install xubuntu-desktop**

You might have some problems with the above steps, please come back to us.

John

---

### Post by dam2 on 2007-08-19
Dear John,

Thank you very much for your instruction, and it is always very nice to hear at the end of the message 'please come back to us'.

To be more precise about my system, the xubuntu704.iso file is on dev/hda1 and the xubuntu system is on dev/hda5. I have puppy linux installed on hda2.

OK, so I tried the procedure :

sudo mount -o loop cd.iso /mnt/image
sudo rm /cdrom
sudo ln -s /mnt/image /cdrom
sudo apt-cdrom -m add

but the first line did not work. I wrote XUBUNTU704.iso instead of cd.iso, first in capital then changed it to normal but it was useless. Capital can be a problem ? my file name is in capital.

I also moved the iso file in hda5, but it did not work. I don't know what to write for the system to find the iso that is in hda1. 

I have puppy linux installed also. So I can use this OS to change iso file from one place to another if it is needed.

John, thank you for your support (and other people as well), I hope I'm precise enough,

Cheers,
Dam

---

### Post by john_spiral on 2007-08-20
Hi Dam,

Linux is case sensitive so you need to put the exact file name

Under Linux the file name :

xubuntu704.iso

is different to :

Xubuntu704.iso

is different to :

XUBUNTU.ISO

e.t.c....

it looks like you have already made a copy of the .iso file on your dev/hda5 partition?

at the command type:

find / -name '*.iso'

it will give you the location of all the .iso files in your file system.

***ignore the one under the /mnt directory.***

change to the directory where the copied "xubuntu704.iso" is living, then try the below command:

sudo mount -o loop cd.iso /mnt/image

come back to us.

John

---

### Post by dam2 on 2007-08-20
Hi John, thank you for your following,
I understand what you want me to do, but the computer is not very bright.

I wrote the command line :
find / -name '*.iso'

he will then sort a long list (at least two screeens, so it is hard to see what is on the first one because I don't know how to pause) of places he found something. There are many and they are all access denied.
for instance : 
find : /proc/3886/task/3886/fd: Permission denied
find : /proc/3876/fd: Permission denied

there is quite a long list. Many of them are beginning with /proc... and finishing with /fd
there is also /root/.aptitude : permission denied and others

I don't know if it is linked but at the very beginning of the boot process, there is this line

kinit : no resume image, doing normal boot



don't give up on me (and my computer),
Thanks,
Dam

---

### Post by john_spiral on 2007-08-21
Dan,

sorry my mistake.

type:

**suso su**

and provide your password, this will put you into the necessary super user mode required for all the steps.

then try the find command, once you have found the .iso file on hda5 you will need to use the **cd** command to change to the relavent directory.

proceed from there with the other steps.

John

---

### Post by dam2 on 2007-08-22
Dear John,

Thank you for your brave following.
But the mistake is mine.

I tried some other distro, without success (zenwalk), and I reinstalled xubuntu.
Last time I must have forgotten to check the box install software, and that is why I was left without nothing (no X).
Apologies m(..)m

I eventually managed to fully install xubuntu on my little Fujitsu Loox FMV - biblo s7/60, processor cruzoe 600Mhz (I believe) and 128 meg of RAM.

The community knowledge concerning (X)ubuntu is awesome, and it is very plesant not to be left alone (Surely, this is not to critize community with smaller density that can not necessary support every here and then).

Thank you very very much,
Cheers,
Dam

---

### Post by say2sky on 2007-09-09
> **john_spiral said:**
> Hi All,

please use the vmlinuz & initrd.gz files from the below site:

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/")

The vmlinuz & initrd.gz files from the .iso have been coded for an install from a physical CD and will not work for an .iso based install.

thanks

John

Thanks for this info and it is useful.

But I wonder what is the difference between initrd.gz inside .iso and initrd.gz specially for hard drive installation in website. I indeed have found sometimes a new .iso is out but initrd.gz have not be updated in website. Could we just make some adjustment to let initrd.gz from .iso useful for hard drive installation. Thanks!

---

### Post by Allener on 2007-10-20
> **john_spiral said:**
> ***ONLY USE THIS HOWTO IF YOU DON'T HAVE A WORKING CD DRIVE OR WANT TO SAVE THE TROUBLE OF BURNING A PHYSICAL DISC***

***THIS INSTALLATION METHOD WILL ONLY WORK WITH THE ALTERNATIVE ISO FILES OF UBUNTU/KUBUNTU/XUBUNTU - PLEASE CHOOSE THE RELEVANT .iso , vmlinuz & initrd.gz FILES FOR 7.04 & 7.10   ***

***SKIP STEPS 9/10 IF YOU ARE INSTALLING 7.04 & 7.10***

Hi,

Below is a micro step-by-step procedure for installing Ubuntu 6.10 from an .iso file. The below procedure might also be useful for installing Kubuntu/Edubuntu & Xubuntu.

Before I go any further I’m still relatively new to Ubuntu and would appreciate your help in refining/correcting this HOWTO and answering questions.

(1) Download the _**Alternative**_ Ubuntu/Kubuntu/Edubuntu/Xubuntu .iso file and run an md5 check on it. If you are running Windows drag your .iso file onto the below program (md5sums.exe) and it will spit out a long string of characters and numbers. Make sure the string it spits out matches the published md5 sum.

[http://www.pc-tools.net/files/win32/freeware/md5sums-1.2.zip](http://www.pc-tools.net/files/win32/freeware/md5sums-1.2.zip)

md5 sums look like the following:

549ef19097b10ac9237c08f6dc6084c6  ubuntu-6.10-alternate-i386.iso

(2) Before installing Ubuntu you will need to partition your drive. In essence you will need to boot from another media either a floppy, 2nd drive or USB key and run some type of partition software. Create one new partition for the Ubuntu installation, one to hold the .iso file & additional boot files (say 700megs). You might need to resize your existing OS to make space for the above 2 partitions.
 
(3) Install grub onto either a floppy or hard drive and create a similar entry in your menu.lst file:

title Install Ubuntu
root (hd0,2)
kernel /boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd /boot/initrd.gz

**([COLOR="Red"]hd0,2[/COLOR]) refers to the 1st hard drive [COLOR="Red"]'hd0'[/COLOR] and the 3rd partition [COLOR="Red"]'2'[/COLOR].

The counting of partitions and hard drives starts at zero. Linux loves making life complicated ;-)

Change (hd0,2) to match the drive and partition of your .iso file.

e.g (hd1,3) Refers to drive 2 and partition 4.  

(4) **_Download_** the vmlinuz & initrd.gz files from the below site (DON'T USE vmlinuz & initrd.gz FILES FROM .iso) :

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/hd-media/)

(5) Plonk the .iso, vmlinuz & initrd.gz files onto the newly created partition from step (2) in a /boot directory. 

(6) **_NB_** Make sure all other Ubuntu/Kbuntu/Xubuntu/Debian .iso installer files have been renamed to .iso.somethingelse, this will prevent the installer from picking up the wrong .iso file.

(7) Boot the machine from the hard disk or floppy that has grub installed, you should see a menu that contains ‘Install Ubuntu’. Select ‘Install Ubuntu’ and press enter.

(eight) Next run through the installation until it fails to find the .iso file. Then change to terminal 2 with (Ctrl-Alt-F2). Hit enter to activate this console.

(9) Type the below commands in terminal 2:

mkdir -p /dev/loop 
ln /dev/loop0 /dev/loop/0 

(10) Change back to terminal 1 (Ctrl-Alt-F1), scan again and the ISO will be detected.

(11) Voila! The install should be working, choose the manual option on the '[!!] Partition disks' screen, specify your large partition might be hda2 as your root/home....

(12) You will need to edit your grub entry to get it to work, please post problems. 

Thanks to all the helpful people on the forums for getting this procedure to work.

Thanks also to the busybox mailing list!

[SIZE="4"]Thanks for your guide .Following it,I managed to scan and detect the ISO image form the hd. It showed as :
*Successfully mounted gutsy installer ISO image The ISO file /ubuntu-7.10-alternate-amd64.iso on /dev/sda8 (gutsy) will be used as the installation ISO image*.However,it failed at* Load installer components r\from an installer ISO reading data from the CD-ROM*. I installed my ubuntu from hd. How come that it needs to read from the CD-ROM? How to straighten this out?
Thanks a million![/SIZE]

---

### Post by bbruecker on 2007-11-10
Hi,
I've tryed to install ubuntu server 7.10 -- but the installer does not find the iso-file. Does this procedere only work with desktop-alternate versions?
Benjamin

---

### Post by john_spiral on 2007-11-10
> **bbruecker said:**
> Hi,
I've tryed to install ubuntu server 7.10 -- but the installer does not find the iso-file. Does this procedere only work with desktop-alternate versions?
Benjamin

As far as I'm aware you will need to use the alternative version of 7.10 with files from the below download:

[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/)

---

### Post by john_spiral on 2007-11-11
> **Allener said:**
> [SIZE="4"]Thanks for your guide .Following it,I managed to scan and detect the ISO image form the hd. It showed as :
*Successfully mounted gutsy installer ISO image The ISO file /ubuntu-7.10-alternate-amd64.iso on /dev/sda8 (gutsy) will be used as the installation ISO image*.However,it failed at* Load installer components r\from an installer ISO reading data from the CD-ROM*. I installed my ubuntu from hd. How come that it needs to read from the CD-ROM? How to straighten this out?
Thanks a million![/SIZE]

Where did you download the vmlinuz & initrd.gz files from?

---

### Post by john_spiral on 2007-11-11
> **say2sky said:**
> Thanks for this info and it is useful.

But I wonder what is the difference between initrd.gz inside .iso and initrd.gz specially for hard drive installation in website. I indeed have found sometimes a new .iso is out but initrd.gz have not be updated in website. Could we just make some adjustment to let initrd.gz from .iso useful for hard drive installation. Thanks!

Give it a try to see what happens? 

Also try running a md5sum check on the .iso's initrd.gz file compared to the downloaded initrd.gz file?

---

### Post by madmatrixz3000 on 2007-11-13
Okay I am using the gusty altermate and I am getting the error of it cannot find the iso neither in the same dir nor on a USB which it is able to detect

Also, do I need the boot.img.gz file or just the other 2?

---

### Post by madmatrixz3000 on 2007-11-15
Does anyone know what I need to do?

---

### Post by garuhhh on 2007-11-15
i'm stuck... my installation got to the iso detected, and when it starts the   "partman" (i think its the partition manager) it just shows a blank screen and does nothing.. what seems to be wrong? thanks

am installing xubuntu 7.10 alternate iso. the partition where my win2000 is located is ntfs. have 128MB ram, 800Mhz Duron.

---

### Post by garuhhh on 2007-11-15
> **madmatrixz3000 said:**
> Okay I am using the gusty altermate and I am getting the error of it cannot find the iso neither in the same dir nor on a USB which it is able to detect

Also, do I need the boot.img.gz file or just the other 2?

did you do this?
> (eight) Next run through the installation until it fails to find the .iso file. Then change to terminal 2 with (Ctrl-Alt-F2). Hit enter to activate this console.

(9) Type the below commands in terminal 2:

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0

(10) Change back to terminal 1 (Ctrl-Alt-F1), scan again and the ISO will be detected.


---

### Post by john_spiral on 2007-11-16
> **garuhhh said:**
> i'm stuck... my installation got to the iso detected, and when it starts the   "partman" (i think its the partition manager) it just shows a blank screen and does nothing.. what seems to be wrong? thanks

am installing xubuntu 7.10 alternate iso. the partition where my win2000 is located is ntfs. have 128MB ram, 800Mhz Duron.

have you checked the md5sum of the .iso file?

---

### Post by john_spiral on 2007-11-16
> **madmatrixz3000 said:**
> Okay I am using the gusty altermate and I am getting the error of it cannot find the iso neither in the same dir nor on a USB which it is able to detect

Also, do I need the boot.img.gz file or just the other 2?

You just need the .iso , vmlinuz & initrd.gz files in one folder.

remove the USB drive.

check the md5sum of the .iso file.

---

### Post by gadgetwizard1 on 2007-12-03
Brilliant, brilliant, brilliant.

Found this post using a google search.

Here is my hardware:

IBM240 with no CD and Fedora Core 1 installed
Purchased from eBay for £50.00
333mhz processor
192mb RAM (hence Xubuntu)
10GB HD
External floppy
Intel Pro 2011b 802.11B PCMCIA Wireless card (does not work with Fedora Core 1)




Here are my details:
Partitioned the drive so that i had a 750mb partition.
Followed all the steps and presto chango, Xubuntu 7.04 installed and working.
Make sure you use the vmlinuz and initrd.gz from the link. In my case i used the link to find the correct files for 7.04. The ones in the link are for 6.10. The 6.10 files did not work for 7.04.
I used the alternate install .iso not the live CD.
I did not need to use steps 9 and 10.
I used the manual  install option and chose the fedora core 1 partitions, a bit scary as that destroys my fedora install, however as i only have 10gb HD then better use of my space. BTW fedora core 1 is the only distro i have found that will boot  from a floppy and then install from an external USB cdrom!. Although this is a working linux, FC1 is not very good with wireless cards.
I have left the 750mb partition/.iso files where they are and updated the Xubuntu Grub menu.lst so that if i have an issue in the future i should still be able to re-install again. A bit like one of those emergency return to factory configuration partitions you usually get with Windows machines these days.

Now i have an ultra portable laptop with a useful operating system that's better than Windows.

Well done and thanks for this thread, keep up the good work everyone.

---

### Post by skroops on 2007-12-03
a

---

### Post by john_spiral on 2008-01-15
Hi,

I've put together a small HOWTO on the Gujin bootloader, really useful for booting any LiveCD or OS from a .iso file

[http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

John

---

### Post by send2toonie on 2008-02-13
Hello all,

First off, I'm completely new to Linux.  My understanding of linux is non-existent.

Anyways, I'm really interested in trying Xubuntu, but am not quite ready to leave Windows XP.  My question is would this method work for a dual boot system.  1 harddrive: 1st partition XP, 2nd partition xubuntu?

I'm asking because my old laptop has only one hard drive, no cdrom, non bootable usb.  Specs are 12GB, 320MB RAM, Celeron 400 MHz.

Current I have three partitions on the hard drive... 1st has 6GB for WinXP, 2nd has 5GB blank, and 3rd has 800MB also blank.  I was hoping to get xubuntu on to the 2nd partition, and putting the alternate iso along with install files into the third partition.

One more thing, partitions 1 and 3 are ntfs, and the 2nd is ext3.

Help Please!

---

### Post by john_spiral on 2008-02-18
> **send2toonie said:**
> ...I'm asking because my old laptop has only one hard drive, no cdrom, non bootable usb.  Specs are 12GB, 320MB RAM, Celeron 400 MHz...

any chance of inserting the hard drive into another computer to complete the partition process?

---

### Post by send2toonie on 2008-02-19
> **john_spiral said:**
> any chance of inserting the hard drive into another computer to complete the partition process?


yes, i have a desktop and usb connector that has both 2.5 and 3.5 adapters.  so i can take out the hard drive and use that.  will that work?

thanks for the reply.

---

### Post by john_spiral on 2008-02-19
> **send2toonie said:**
> yes, i have a desktop and usb connector that has both 2.5 and 3.5 adapters.  so i can take out the hard drive and use that.  will that work?

thanks for the reply.

yes, split the drive into 3 partitions, one for Windows another for the Ubuntu installation and another smaller one for the .iso, vmlinuz & initrd.gz files. Then install grub to the disc with an entry similar to the one on the first page of the howto. 

Please check this forum/wiki docs for instructions on how install grub.

Please come back to us.

---

### Post by iblicf on 2008-02-23
im trying to install hardy alpha5 and downoad the ISO file  , i have arch linux in /dev/sda3 , wanna  to intall without CD neither windows 
 
```

/dev/sda1  winxp
/dev/sda2  intend to install ubuntu hardy
/dev/sda3  arch 
```

first i use the way this thread says ... 
copy init*.gz vmlinuz hardy-desktop-i386.iso to /boot
and make the menu.lst like below : ( initrd.gz vmlinuz copy from iso casper folder )
[HTML]title Install without CD
root (hd0,2)
kernel /boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd /boot/initrd.gz
boot[/HTML]
but , it can not change the virtual console within the install process , i google somebody use this in windows/grub4dos way :
[HTML]title Install without CD2
#find --set-root /boot/hardy-desktop-i386.iso
root (hd0,2)
kernel  /boot/vmlinuz boot=casper find_iso=/boot/hardy-desktop-i386.iso
initrd  /boot/initrd.gz[/HTML]

now , it make progress a little more ^^ 
stopped at  [initramfs~] , like a shell environment ... 

then , what can i do next :(
thanks .

---

### Post by john_spiral on 2008-02-24
> **iblicf said:**
> im trying to install hardy alpha5 and downoad the ISO file.....

I'm sorry but this HOWTO will only work with certain ubuntu alternative .iso files.

Please try my below thread:

[ [COLOR="Blue"]_HOWTO Boot from a .iso file without needing a working CD-ROM - REALLY USEFUL!_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=666267")

---

### Post by send2toonie on 2008-02-25
I think i'm going to give up.  I have no idea how to install grub, and yes I've tried reading up on it but i'm just lost.

Thanks for you help John.

Maybe i'll give it another shot when I find an easier way to install it.

---

### Post by johnraff on 2008-02-26
Before you give up, here's an alternative to John's method:
[http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)
unetbootin is a file that sits in your Windows (or other linux) partition and starts off an installation from the net instead of an iso file. You don't need to make a new partition if you've got an existing system on your machine, and once the installation gets going there's a partitioner that helps you set things up, just like the regular Ubuntu install disk.

I've just used it and it was pretty easy. :)

---

### Post by send2toonie on 2008-03-15
Thanks for the net install idea, but i've tried that before this method and that didn't work.

But I really wanted to try ubuntu, so i went out and bought a new laptop.  I now have dual boot vista and ubuntu, and i LOVE ubuntu.

Anyways, thanks all for trying to help me.  It really was an old system, i think buying a new afford me a chance to really give ubuntu a fair try, rather than try running it on a slower machine and not really 'experience' it fully.

Thanks again.

---

### Post by john_spiral on 2008-03-16
have you tried this?

[http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

---

### Post by Replika on 2008-04-26
> **Allener said:**
> [SIZE="4"]Thanks for your guide .Following it,I managed to scan and detect the ISO image form the hd. It showed as :
*Successfully mounted gutsy installer ISO image The ISO file /ubuntu-7.10-alternate-amd64.iso on /dev/sda8 (gutsy) will be used as the installation ISO image*.However,it failed at* Load installer components r\from an installer ISO reading data from the CD-ROM*. I installed my ubuntu from hd. How come that it needs to read from the CD-ROM? How to straighten this out?
Thanks a million![/SIZE]

I've the same problem when trying to install v8.04 alternative(checksum ok)
Does this tip work with v8.04?

---

### Post by john_spiral on 2008-04-27
> **Replika said:**
> I've the same problem when trying to install v8.04 alternative(checksum ok)
Does this tip work with v8.04?

not sure, could you give it a try?

thanks

John 

or try the following method:

[http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

---

### Post by Kidaf on 2008-05-01
john,

I used your tuto to install Gutsy, and tried on Hardy, but had problems.

Fixed them, thou, with these 2 simple changes on your tuto:


**FIRST:** change the link to the vmlinuz & initrd.gz files, from edgy to hardy. This way, you can get the needed compressed kernel files to install.

_old >_ [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)[COLOR="Red"]edgy[/COLOR]/main/installer-i386/current/images/hd-media/

_change to >_ [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)[COLOR="Red"]hardy[/COLOR]/main/installer-i386/current/images/hd-media/


**SECOND:** rise the set ramdisk_size for the decompressed kernel files on the new entry for Grub, as 14972 seemed not to be enough.

_old >_ kernel /boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --

_change to >_ kernel /boot/vmlinuz vga=normal ramdisk_size=14972[COLOR="Red"]0[/COLOR] root=/dev/rd/0 rw --


In fact, I am not really sure how much ramdisk_size is actually needed, but 10x the original solved the problem.


Other than that, Hardy installed smoothly, just as Gutsy with yout original tuto.


Thanks!

---

### Post by aarmelvin on 2008-05-08
HOWTO: Install Edgy 6.10 from an .iso file

can i use the same method to install gOS since it also based on ubuntu...
i need ur help regarding this...

i tried the method that was explained above....

i have resized one of my older partition........

when i reboot my machine.....
when i select to install gOS
i got the error
Error 2 : Bad file or directory...

any idea...
tahnks in advance

---

### Post by john_spiral on 2008-05-09
> **aarmelvin said:**
> HOWTO: Install Edgy 6.10 from an .iso file

can i use the same method to install gOS since it also based on ubuntu...
i need ur help regarding this...

i tried the method that was explained above....

i have resized one of my older partition........

when i reboot my machine.....
when i select to install gOS
i got the error
Error 2 : Bad file or directory...

any idea...
tahnks in advance

try this method:

[http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

---

### Post by Kidaf on 2008-05-15
As requested, and posted above:

> **Kidaf said:**
> john,

I used your tuto to install Gutsy, and tried on Hardy, but had problems.

Fixed them, thou, with these 2 simple changes on your tuto:


**FIRST:** change the link to the vmlinuz & initrd.gz files, from edgy to hardy. This way, you can get the needed compressed kernel files to install.

_old >_ [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)[COLOR="Red"]edgy[/COLOR]/main/installer-i386/current/images/hd-media/

_change to >_ [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)[COLOR="Red"]hardy[/COLOR]/main/installer-i386/current/images/hd-media/


**SECOND:** rise the set ramdisk_size for the decompressed kernel files on the new entry for Grub, as 14972 seemed not to be enough.

_old >_ kernel /boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --

_change to >_ kernel /boot/vmlinuz vga=normal ramdisk_size=14972[COLOR="Red"]0[/COLOR] root=/dev/rd/0 rw --


In fact, I am not really sure how much ramdisk_size is actually needed, but 10x the original solved the problem.


Other than that, Hardy installed smoothly, just as Gutsy with yout original tuto.


Thanks!


I've grabbed your tuto, modifed it and posted a new one, for Hardy, on [http://ubuntuforums.org/showthread.php?t=782603](http://ubuntuforums.org/showthread.php?t=782603)


Cya!

---

### Post by nlbs on 2009-01-12
I applied the same technique with kubuntu 8.10
and I used kubuntu 8.10's hd-media's vmlinuz and initrd
but This time its not rqequired to do ln /dev/loop0 /dev/loop/0
it finds the ISO without that

But the problem is **Partitioner doesn't shows any partitions** I've never seen such a problem on any forum

---

### Post by john_spiral on 2009-01-12
> **nlbs said:**
> I applied the same technique with kubuntu 8.10
and I used kubuntu 8.10's hd-media's vmlinuz and initrd
but This time its not rqequired to do ln /dev/loop0 /dev/loop/0
it finds the ISO without that

But the problem is **Partitioner doesn't shows any partitions** I've never seen such a problem on any forum

If you boot from .iso file B on say hard disk A , you won't be able to partition disk A while running operating system from .iso file B.

you will need to either use a whole new drive OR:

"(2) Before installing Ubuntu you will need to partition your drive. In essence you will need to boot from another media either a floppy, 2nd drive or USB key and run some type of partition software. Create one new partition for the Ubuntu installation, one to hold the .iso file & additional boot files (say 700megs). You might need to resize your existing OS to make space for the above 2 partitions."

If you are running Windows you could try the wubi installer, no need to partition drive.

hope this helps

John

---

### Post by nlbs on 2009-01-14
> **john_spiral said:**
> "(2) Before installing Ubuntu you will need to partition your drive. In essence you will need to boot from another media either a floppy, 2nd drive or USB key and run some type of partition software. Create one new partition for the Ubuntu installation, one to hold the .iso file & additional boot files (say 700megs). You might need to resize your existing OS to make space for the above 2 partitions."
Ya I've made a new partition and I am doing all this things on that partition. and Its /dev/sda3

I don't have another 2nd hard disk and My floppy disk drive is broken.

---

### Post by john_spiral on 2009-01-14
> **nlbs said:**
> Ya I've made a new partition and I am doing all this things on that partition. and Its /dev/sda3

I don't have another 2nd hard disk and My floppy disk drive is broken.

try using the method from this HOWTO, make sure you have followed all the steps & use the new vmlinuz & initrd files. It should work.

---

### Post by azpaul on 2009-02-17
Hello,

I went through and followed the original procedures with no luck.  The install can not find the iso file when scanning the drives

My configuration is -
1 bootable 8G hard drive with  Ubuntu 8.10 desktop (hd0)
1 80G new drive (hd1)- This used to have windows on it.

Downloaded from the tutorial the initrd.gz, boot.img.gz, vmlinuz.  I copied these to my working linux directory /home/paul/ubuntu-install.  I copied the newest 8.10 iso to this directory as well.

On hd1, the 80G, I partitioned the drive as 1 drive, flagged a bootable and created a /boot directory.  I copied the same files to the boot directory.

I edited the grub menu for the install to point to these directories for the install. menu.lst below

The setup started and when I got to the scan drives for iso, it continually fails. 

Realizing that the initrd.gz and the vmlinuz I downloaded from the tutorial was for a different version of an iso, I copied the two files to from the 8.10 distribution iso.  

I ran the install again through grub, the install starts up then gives up waiting for root device.

Message as follows
Give up waiting for root device.  Common problem:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/rd/0 does not exist.  Dropping to a shell

It appears that there is an issue with the ram disk?

There is a boot.img.gz I believe is called but I can not find this file for the newest release.   I think my problems are now with the wrong version of the boot.img.gz.

Any help would greatly be appreciated.

Thanks.


menu.lst

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            1a239ce4-4555-4d09-bde5-09c77e652d66
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=1a239ce4-4555-4d09-bde5-09c77e652d66 ro quiet splash 
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            1a239ce4-4555-4d09-bde5-09c77e652d66
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=1a239ce4-4555-4d09-bde5-09c77e652d66 ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            1a239ce4-4555-4d09-bde5-09c77e652d66
kernel          /boot/memtest86+.bin
quiet

title Install Ubuntu
root (hd0,0)
kernel /home/paul/ubuntu-install/vmlinuz vga=normal ramdisk_size=149720 root=/dev/rd/0 rw - 
initrd /home/paul/ubuntu-install/initrd.gz

---

### Post by azpaul on 2009-02-17
OK,  Made small progress since the above post.  

I found the images at this link.

[http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/hd-media/)

When through grub and got past last problem but during the scan for the iso, the installer can not find it.  I did a thorough scan with the same results.  I know the file is there.

On the new hard drive I still have the /boot directory with the iso image in it.  Should this image be somewhere else? 

It is also on hd0, the drive I originally booted from. 

I went to a terminal and did a find for *.iso  

2 entries came up 
/hd-media/boot/ubuntu-8.10.desktop-i386.iso
/hd-media/home/paul/ubuntu-install/ubuntu-8.10-desktop-1386.iso

Any ideas?

Thanks.

---

### Post by john_spiral on 2009-02-18
> **azpaul said:**
> OK,  Made small progress since the above post.  

I found the images at this link.

[http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/hd-media/)

When through grub and got past last problem but during the scan for the iso, the installer can not find it.  I did a thorough scan with the same results.  I know the file is there.

On the new hard drive I still have the /boot directory with the iso image in it.  Should this image be somewhere else? 

It is also on hd0, the drive I originally booted from. 

I went to a terminal and did a find for *.iso  

2 entries came up 
/hd-media/boot/ubuntu-8.10.desktop-i386.iso
/hd-media/home/paul/ubuntu-install/ubuntu-8.10-desktop-1386.iso

Any ideas?

Thanks.

azpaul try the alternative installer .iso, think that should work, rename all other .iso files to .iso.old

There was another thread on the forums for a 8.1 iso install, have a search

---

### Post by kjtruitt on 2009-03-24
Gateway Solo 9500 SE BUSINESS
745.7 mhz coppermine processor
128mb ram
30+/- G HD

--computer is "locked in": broken cdrom drive, modem is probably software-based winmodem, hard drive wiped, no os, basiclinux 3.5 could not use modem or dLink ethernet pcmcia, or Linksys wpc11 pcmcia wireless.

Nothing worked.  Has floppy drive.  I have cheap enclosure and another hard drive to play with.

So Hard drive install was the way to go.  I tried 8.1-alternate, then I tried 7.1.  In both cases, the following happened.

1)cardbus bridge detected, triggering modprobe yenta_socket , which is not found and does not load, but installation continues...
2)xubuntu-8.1-alternate-i386.iso is FOUND
3)an "installable kernel" is not found in the iso. what??

The iso is mounted in CDROM.  You can browse the directory.  On another attempt to install the alternate version from an actual cdrom on another computer, I checked my cdrom using the ubuntu menu option to do this--and it said debootstrap (something like this) files were corrupt and that some files related to the kernel, if not the kernel files themselves (I wouldn't know) were corrupt.  Later, almost 80% into the install, it said that no usable kernel was found in the iso.  This is a similar message to the one I got on the hard drive install attempt, but it came alot later.  The hard drive installer discovers this problem almost immediately.

So the download file was corrupt, though I thought the iso itself passed md5.  So I've downloaded 8.04.1 and I'm trying again...

Any insight would be appreciated.

kt

---

### Post by kjtruitt on 2009-03-24
This time the problem was what it said it was--corrupt files.
Somehow, despite my md5summing of my downloads, a corrupt iso got on my hard drive (and on a cdrom I tried with another computer that has a drive).

I have succeeded with 8.04.1 on my gateway Solo 9500.

Thank you very much for the excellent instructions, meeting the needs of a few of us out here with no other good options.

Cheers!

Kt

---

### Post by farley13 on 2009-08-22
All this having to create a new partition to install an iso is hogwash. Linux has loop mounting to handle it and it works as well in the installer as it does in full blown linux. 

Use a bootloader or unetbootin to launch the install
Wait until it complains that it can't find the cd rom
Press alt F2 to bring up a BusyBox console.

mount your filesystem contain the iso (mine was sda3 since I've got an sata hd)

Then follow the instructions from:

[http://forum.synology.com/enu/viewtopic.php?f=27&t=6647&p=28071&hilit=+mknod+mknod+loop0#p28071](http://forum.synology.com/enu/viewtopic.php?f=27&t=6647&p=28071&hilit=+mknod+mknod+loop0#p28071) 

Namely

Create loopback device:
: mknod /dev/loop0 b 7 0

Mount the image in /mnt/iso:
: mount file.iso /cdrom -t iso9660 -o loop=/dev/loop0

Or as alternative to the command above:
: losetup /dev/loop0 file.iso
: mount /dev/loop0 /cdrom -t iso9660

This second one worked for me. I could then mount the loop device on /cdrom and the install proceeded as normal.

Hope this non-destructive install helps someone else too. It couldn't be simplier.... :P

---

### Post by john_spiral on 2009-08-23
> **farley13 said:**
> All this having to create a new partition to install an iso is hogwash...
Greetings farley13, we do like friendly responses,

On what partition does the mounted .iso reside with your method?

---

