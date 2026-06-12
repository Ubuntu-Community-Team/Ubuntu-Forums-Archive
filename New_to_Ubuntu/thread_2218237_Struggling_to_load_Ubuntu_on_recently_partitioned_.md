---
title: "Struggling to load Ubuntu on recently partitioned SSD."
date: 2014-04-19
forum: New to Ubuntu
---

### Post by joe66ano on 2014-04-19
Hi. I'm a noob and I think this is my first post. 

I partitioned a portion of my SSD for Ubuntu, setting aside 50 GiB.

Then I tried rebooting, hoping to have the option to choose between Win7 & Ubuntu.

It gave me no such option and said that something was preventing wrong with Windows, so I used the repair disc and everything went as expected.

When I checked my SSD, I noticed that the 50 GiB was missing and invisible. As in, I couldn't see or explore that part of the drive, but the drive was smaller. 

So basically Windows works fine and I can't load Ubuntu.. yet.

I tried holding down shift on start up but, nothing. 

Info: [http://i.imgur.com/KGeaEkA.png](http://i.imgur.com/KGeaEkA.png)

---

### Post by joe66ano on 2014-04-19
Oh, a buddy of mine told me it could be a problem with grub?

I never heard of it, totally clueless there.

---

### Post by oldfred on 2014-04-19
Windows cannot see Linux formatted partitions. Do not use Windows to modify any Linux partitions as you probably will just end up deleting them.
Linux does see and use NTFS partitions without issue, but best not to write into Windows system partition, just set it as read only and use a shared NTFS data partition for any data you may want in both installs.

Grub2 is the boot loader. The Windows boot loader in the MBR does not have a name as far as I know.

When you install Ubuntu you have to specify where to install the grub2 boot loader. That would be the MBR of a hard drive. The MBR is the master boot record. Unless you have a new UEFI system then it is all different.

Or if you used any of the auto install options it installed grub2's boot loader into the MBR of the drive seen as sda. If you have more than one drive, you may just need to change BIOS to boot from the other drive. Or if you have a one time boot key (f12 on my system, but varies) you can try booting the other drive.

What version Ubuntu?
Boot into installer in try mode or the live mode.

In terminal post this:

sudo parted -l

---

### Post by joe66ano on 2014-04-20
I don't recall being asked where to install grub, but I hope it was installed on the partition I designated for Ubuntu 14.04. 

Terminal Results: 

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA OCZ-VERTEX4 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  106MB  105MB   primary  ntfs         boot
 2      10.9GB  202GB  191GB   primary  ntfs
 3      202GB   256GB  53.7GB  primary  ext4


Model: ATA ST31000528AS (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  106MB   105MB   primary   ntfs         boot
 2      108MB   1000GB  1000GB  extended               lba
 5      108MB   571GB   571GB   logical   ntfs
 6      571GB   1000GB  429GB   logical   ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

---

### Post by oldfred on 2014-04-20
You cannot install grub to a partition and have it work. 
BIOS boots from a MBR. You do have two drives so you have two MBRs and could have different boot loaders in each. But Windows only boots from drive  set in BIOS as boot drive and then from partition with boot flag.

Grub does not use boot flag and finds Windows on its own and will add a boot entry to boot it from the grub menu.

If this is 12.04, run this
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If you have 14.04, the ppa is not set up yet and you have to run a work around.
      
 [https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)

---

### Post by joe66ano on 2014-04-20
I have 14.04 

So... Let me make sure I understand you want me to open the Termianl and type... 

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

sudo apt-get install -y boot-repair

Then, open new PPA entry. (IDK WHAT THIS IS)

gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list

Change trusty to saucy - remember sometime in future to change back. (WHERE IS THIS DONE?)

sudo apt-get update

sudo apt-get install -y boot-repair

history 

(THEN...)

Reboot (HOLD SHIFT, SELECT UBUNTU)

I'm still a little confused.. thanks.

---

### Post by oldfred on 2014-04-20
Only change the ppa you just added:
gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)'
Change to this - trusty to saucy then if you later see the trusty ppa is working change it back
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages)'

Boot-Repair can run auto fixes, but it is probably better to review your configuration. 
Run the BootInfo report and post the link to the report it gives you.

---

### Post by joe66ano on 2014-04-20
That first link doesn't work. 

I have something called the "yannubuntu-boot-repair-trusty.list" opened up in Text Editor "(/etc/apt/sources.list.d) - gedit"

Do you want me to paste the text in the second link inside this document and then RENAME the document ""yannubuntu-boot-repair-saucy.list"?

Shouldn't I remove this document so it doesn't interfear with anything? How do I do that? :s

---

### Post by joe66ano on 2014-04-20
ubuntu@ubuntu:~$ sudo apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgksu2-0
The following NEW packages will be installed:
  gksu libgksu2-0
0 upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
Need to get 99.6 kB of archives.
After this operation, 740 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe libgksu2-0 amd64 2.0.13~pre1-6ubuntu4 [71.8 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe gksu amd64 2.0.2-6ubuntu2 [27.8 kB]
Fetched 99.6 kB in 0s (320 kB/s)
Selecting previously unselected package libgksu2-0.
(Reading database ... 169090 files and directories currently installed.)
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu4_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-6ubuntu2_amd64.deb ...
Unpacking gksu (2.0.2-6ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gksu (2.0.2-6ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
ubuntu@ubuntu:~$ gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list

(gksudo:4655): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed

---

### Post by joe66ano on 2014-04-20
I don't understand what you mean by "BootInfo report" or "Boot-Repair" or "ppa" :C

---

### Post by oldfred on 2014-04-20
See post #5. Direct link to Boot-Repair instructions.

        ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)

---

### Post by joe66ano on 2014-04-20
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-extra gawk glade2script libsigsegv2 pastebinit
Suggested packages:
  mbr mdadm clean-ubiquity os-uninstaller gawk-doc
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra gawk glade2script libsigsegv2 pastebinit
0 upgraded, 7 newly installed, 0 to remove and 7 not upgraded.
Need to get 1,473 kB of archives.
After this operation, 5,025 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  glade2script boot-sav boot-repair boot-sav-extra
E: There are problems and -y was used without --force-yes

---

### Post by joe66ano on 2014-04-20
Ok. Now I'm at a part where I type: 

sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linux

into the terminal and it says:

ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linuxsudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linuxsudo
E: Unable to locate package chroot
E: Unable to locate package /mnt/boot-sav
E: Unable to locate package apt-get
E: Unable to locate package install
E: Unable to locate package linux

THEN it won't let me go forward because GRUB is still absent?

---

### Post by oldfred on 2014-04-20
If this is what you typed. Looks like two lines combined?
> ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda3" apt-get install -y  --force-yes grub-pc linuxsudo chroot "/mnt/boot-sav/sda3" apt-get  install -y --force-yes grub-pc linux

It is not this:
> sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linux

Spaces and having everything on one line is critical.

---

### Post by joe66ano on 2014-04-20
I typed this 

sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linux

Which is what this thing told me to do: [http://i.imgur.com/9CfC3Yz.jpg](http://i.imgur.com/9CfC3Yz.jpg)

---

### Post by joe66ano on 2014-04-20
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux


That's what the terminal says... Should I click DISCARD?

---

### Post by joe66ano on 2014-04-20
I did what Boot Repair said, i don't understand...

---

### Post by joe66ano on 2014-04-20
help.

my computer has been stuck at this screen now for hours.

---

### Post by joe66ano on 2014-04-20
Something worked, but i'm stuck again. 

[http://imgur.com/a/BZ94j#0](http://imgur.com/a/BZ94j#0)

Won't let me install GRUB to the location i want..

---

### Post by joe66ano on 2014-04-20
APPARENTLY YOU MUST PRESS SPACE TO SELECT THE OPTION AND THEN TAB TO MOVE TO OK. THANKS, INSTRUCTIONS. 

HISTORY: 

ubuntu@ubuntu:~$ history
    1  gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
    2  sudo apt-get install gksudo
    3  sudo apt-get install gksu
    4  gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
    5  deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) saucy main
    6  sudo apt-get install -y boot-repair
    7  boot-repair
    8  sudo apt-get install -y boot-repair
    9  yes
   10  sudo apt-get install -y boot-repair
   11  sudo apt-get install --force yes boot-repair
   12  sudo apt-get install -y--force yes boot-repair
   13  sudo apt-get install -y boot-repair
   14  boot-repair
   15  sudo apt-get install -y boot-repair
   16  ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair
   17  Reading package lists... Done
   18  Building dependency tree       
   19  Reading state information... Done
   20  The following extra packages will be installed:
   21  Suggested packages:
   22  The following NEW packages will be installed:
   23  0 upgraded, 7 newly installed, 0 to remove and 7 not upgraded.
   24  Need to get 1,473 kB of archives.
   25  After this operation, 5,025 kB of additional disk space will be used.
   26  WARNING: The following packages cannot be authenticated!
   27  E: There are problems and -y was used without --force-yes
   28  ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair
   29  Reading package lists... Done
   30  Building dependency tree       
   31  Reading state information... Done
   32  The following extra packages will be installed:
   33  Suggested packages:
   34  The following NEW packages will be installed:
   35  0 upgraded, 7 newly installed, 0 to remove and 7 not upgraded.
   36  Need to get 1,473 kB of archives.
   37  After this operation, 5,025 kB of additional disk space will be used.
   38  WARNING: The following packages cannot be authenticated!
   39  E: There are problems and -y was used without --force-yes
   40  sudo apt-get --force yes install -y boot-repair
   41  sudo apt-get --force-yes install -y boot-repair
   42  boot-repair
   43  sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linux
   44  sudo chroot "/mnt/boot-sav/sda3" dpkg --configure -a
   45  sudo chroot "/mnt/boot-sav/sda3" apt-get install -fy
   46  sudo chroot "/mnt/boot-sav/sda3" apt-get purge -y --force-yes grub* shim-signed linux-signed*
   47  sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linux
   48  sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linuxsudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linux
   49  sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linux
   50  sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linux 
   51  ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linuxsudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linux 
   52  ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc linuxsudo chroot "/mnt/boot-sav/sda3
   53  sudo chroot "/mnt/boot-sav/sda3" dpkg --configure -a
   54  sudo chroot "/mnt/boot-sav/sda3" apt-get install -fy
   55  sudo chroot "/mnt/boot-sav/sda3" apt-get install -y --force-yes grub-pc
   56  history
ubuntu@ubuntu:~$ 

REBOOTING NOW...

---

### Post by joe66ano on 2014-04-20
Well, I rebooted. And, no option to select Linux. :( 

Rebooted again while holding down shift and, no option to select Linux...

---

### Post by oldfred on 2014-04-20
Listing history by itself does not do anything other than show all the command you ran.

I cannot see your img. Use advanced editor and paperclip icon to attach images.
If terminal output do not post screen shot but just copy & paste terminal output like you did above. But if longer use the # in the Go Advanced editor to add code tags.

---

### Post by joe66ano on 2014-04-21
I don't understand what you're saying, try harder to view the image links. They work. 

There's nothing to copy & paste any more, I'm past that. If you want me to I can boot Ubuntu off the disc and run some commands but you're going to have to tell me what to run and what information is going to help you help me.

---

### Post by oldfred on 2014-04-21
Space usually works to get grub menu with BIOS installs. You have to hold it until menu appears.
But if you have an UEFI install you may need to use the escape key. I think you do not hold it though?

If not boot live installer in live working mode and then install Boot-Repair. In live installer you have to reinstall each time.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

With 14.04 you can use any of these alternatives to get Boot-Repair to work so you can run BootInfo report from it.

 [https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)
gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)'
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages)'
 ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)

---

### Post by joe66ano on 2014-04-21
I used WORKAROUND 2 and successfully got to this screen: [http://i.imgur.com/LTZkUfz.jpg](http://i.imgur.com/LTZkUfz.jpg)

One thing I think is weird is that there are so many options for Windows 7. Why is that? 

Well, at least I can boot Ubuntu. Although preformance is sluggish. what can I do about that? Thanks.

---

### Post by joe66ano on 2014-04-21
Oh. Nevermind, I figured that out... I'm learnding. :3

Thanks for all your help! <3

---

### Post by oldfred on 2014-04-21
Boot-Repair does copy bootmgr & BCD from Boot partition to main install, as so many users just delete the Boot partition not knowing it is essential. But then grub2's os-prober finds both and adds them to grub menu.

Some instructions on methods to clean up grub menus in UEFI systems, but some also applies to BIOS systems in link in my signature.

---

### Post by joe66ano on 2014-04-21
Ok, I'll look at that link once I get done installing updates. 

Here's a good question.. Is there a command I can run that will produce a LOT of data for people to look over to make sure that there's nothing "bad" going on with my computer?

---

### Post by oldfred on 2014-04-21
See post #24, Bootinfo report.

It should end with a screen like this. Then copy and paste the link shown.

---

