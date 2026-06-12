---
title: "while in suspend battery dies . Can boot to screen then can't find /dev/sdasbin targ"
date: 2015-03-25
forum: New to Ubuntu
---

### Post by nu2u904 on 2015-03-25
Acer one aspire running ok; put in suspend ok; battery 50% ok; unplugged power ok. Next day computer dead; plugged in power; attempted boot' got the boot screen; clicked on ubuntu; several pages  code then something about can't find target on /dev/sda1; then switched me to busy box. I tried this in recovery mode and with other vsns same result. 
where do I start. To add to my trials unable to boot live usb; same one I originally installed ubuntu with.

---

### Post by veddox on 2015-03-27
What were the precise error messages you got? That is important for us to be able to diagnose the problem... If you can't get them any other way, take pictures of the computer while it's booting. (Though note that pictures you upload here should be 100kb max, see the [Forum Rules]("http://ubuntuforums.org/misc.php?do=showrules").)

Also a bit more information about your computer would be useful: which operating systems are you booting? What partitions do you have? What boot manager do you use?

---

### Post by nu2u904 on 2015-03-29
> **veddox said:**
> What were the precise error messages you got? That is important for us to be able to diagnose the problem... If you can't get them any other way, take pictures of the computer while it's booting. (Though note that pictures you upload here should be 100kb max, see the [Forum Rules]("http://ubuntuforums.org/misc.php?do=showrules").)

Also a bit more information about your computer would be useful: which operating systems are you booting? What partitions do you have? What boot manager do you use?

Thank you veddox. I am running u1404 on Acer aspire one D255 netbook .  Prior to this problem; each time I booted u1404 or recovered from suspend I would get message system error and to report it; which I did. It was only when I let the battery discharge too low and the system shut down that I've had a problem.  This is part of last page code before Busybox
```

1. 1212.387655] sd0:0:0:0:0: [sda]
12.7387720] Add. Sense: Unrecovered read error - auto reallocate failrd
12,387822] sd 0:0:0:0: [sda] GDB:
12.387886] Read(10): 28 

skip---

1266862] EXT4-fs. (sda2):. error loading journal
mount:. mounting /dev/disk/by-uuid/ ----- on /root failed: invalid argument
begin: Running /scripts/local-bottom ... done
Begin: Running /scripts/init-bottom ... mount: mounting /ev on /root/dev failed : no such file or directory done.
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/procfailed no such file or directory,
Target filesystem doesn't have a requested /sbin/init.
No init found. Try passing init=bootarg.
:1.21.0-lubuntu1} built-n shell (ash)
Busybox v1.21.1 (ubuntu 

```
Which commands do I use?

---

### Post by DuckHook on 2015-03-29
Your HDD has been corrupted, including the journal, which is serious. This happens far too often when suspending or hibernating, which is why many old-timers won't use either function. The messages are saying that GRUB cannot find your system and init folder. It may be as simple as running Boot Repair, or you may have to run TestDisk. But either method requires a LiveUSB.

I'm more worried about "unable to boot LiveUSB" which should not be the case. Was it plugged into your laptop when battery ran down? Have you checked whether BIOS was changed to disallow USB boot? Is something loopy like secureboot or fastboot turned on?

If nothing else works, try burning another LiveUSB on a different USB stick and try booting from that.

Is all of your data safe? Have you backed it up?

---

### Post by veddox on 2015-03-30
Thanks, DuckHook, I wouldn't have known that ;-)

Why would suspend/hibernate corrupt your FS?

@nu2u904: If live USB doesn't work, you can still try with a live DVD - dead slow, but hopefully works. And like DuckHook says, it's probably a good idea to backup your data if you haven't done so yet before doing anything else. If you find you cannot access your HDD at all, try recovering it with [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") (this can be found in the repos).

---

### Post by nu2u904 on 2015-03-30
> **DuckHook said:**
> Your HDD has been corrupted, including the journal, which is serious. This happens far too often when suspending or hibernating, which is why many old-timers won't use either function. The messages are saying that GRUB cannot find your system and init folder. It may be as simple as running Boot Repair, or you may have to run TestDisk. But either method requires a LiveUSB.

I'm more worried about "unable to boot LiveUSB" which should not be the case. Was it plugged into your laptop when battery ran down? Have you checked whether BIOS was changed to disallow USB boot? Is something loopy like secureboot or fastboot turned on?

If nothing else works, try burning another LiveUSB on a different USB stick and try booting from that.

Is all of your data safe? Have you backed it up?

Thank you DuckHook. No usbs were plugged in at the time of failure. I have now made in turn priority one: usb HDD, USB FDD, USB CDROM and rebooted ; the usb lights up and the basic grub  screen appears. How can I access the HDD? The current LibreOffice files are not backed up. I'll try burning another usb stick. Is there any way I can make use of the commands in BusyBox? The netbook does not have a CD ROM drive.

---

### Post by DuckHook on 2015-03-30
> **veddox said:**
> Why would suspend/hibernate corrupt your FS?Suppose you have a database stored on a USB HDD and are referencing it (have it open and a record locked). You start fiddling with its data, but like most OS implementations these days, in the interest of efficiency, the system stores your most recent changes in its cache and waits to write to HDD. Before it does that, you suspend or hibernate. The system is supposed to flush its cache before suspending or hibernating, and it does this in one massive blast. But your HDD has its own cache, again, in the interest of efficiency. It accepts all of that input into an onboard cache before slowly writing it out to the magnetic medium. However, before it can finish, the laptop, having spat out all its data successfully, thinks that everything is just hunky-dory and shuts down power, including that to the USB port while your HDD is in mid-write.

It is well known that a power-off to a database while the file is open and data is in mid-write will often corrupt the database sometimes beyond repair. It also has the real potential to corrupt the inode and file pointers.

Another problem arises because we are human: I must shamefully confess to suspending a laptop, forgetting that it was just in suspension, and yanking out the thumbdrive. Problem? I was running a Persistent LiveUSB session on that thumbdrive, lost tons of files and corrupted the thumbdrive. The fact that I felt like an idiot only added insult to injury.

---

### Post by DuckHook on 2015-03-31
> **nu2u904 said:**
> ...How can I access the HDD? The current LibreOffice files are not backed up. I'll try burning another usb stick. Is there any way I can make use of the commands in BusyBox? The netbook does not have a CD ROM drive.Conceptually, what you want to do is boot from a LiveUSB. By doing so, you can can use the environment of the LiveUSB as a platform to:

1. copy your important data off the HDD, and
2. attempt a repair of the HDD itself.

To salvage your data, you need a working LiveUSB that you can boot from. You also need a second empty thumbdrive or USB-HDD/SSD to copy your data to. When the LiveUSB gets to a desktop, you should be able to see your HDD as a drive on the launcher. Hopefully, it is only GRUB that is corrupted. If so, then you can still launch Nautilus, navigate to your /home directory on the HDD and simply copy all of your important data onto the empty thumbdrive. Note: we are talking about the /home directory on your HDD, not the one on your LiveUSB. Don't confuse the two.

Once the data has been copied and safeguarded, make sure you can read it by opening up the thumbdrive and clicking on a document. If everything works, then *properly* unmount the thumbdrive, remove it and put it someplace safe.

To repair GRUB or the bootloader use the follow instructions:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It is not realistic to try anything meaningful from busybox. The command set that is available in GRUB is not even really busybox, but a severely stunted subset that is designed to do a few elementary housekeeping/probing tasks. Your only real option is to use a complete and sophisticated set of tools, such as Boot-Repair, that can only be accessed from a LiveUSB.

I know it's too late, but if your data is important to you, you simply *must* back it up from now on.

---

### Post by nu2u904 on 2015-04-06
> **DuckHook said:**
> Suppose you have a database stored on a USB HDD and are referencing it (have it open and a record locked). You start fiddling with its data, but like most OS implementations these days, in the interest of efficiency, the system stores your most recent changes in its cache and waits to write to HDD. Before it does that, you suspend or hibernate. The system is supposed to flush its cache before suspending or hibernating, and it does this in one massive blast. But your HDD has its own cache, again, in the interest of efficiency. It accepts all of that input into an onboard cache before slowly writing it out to the magnetic medium. However, before it can finish, the laptop, having spat out all its data successfully, thinks that everything is just hunky-dory and shuts down power, including that to the USB port while your HDD is in mid-write.

It is well known that a power-off to a database while the file is open and data is in mid-write will often corrupt the database sometimes beyond repair. It also has the real potential to corrupt the inode and file pointers.

Another problem arises because we are human: I must shamefully confess to suspending a laptop, forgetting that it was just in suspension, and yanking out the thumbdrive. Problem? I was running a Persistent LiveUSB session on that thumbdrive, lost tons of files and corrupted the thumbdrive. The fact that I felt like an idiot only added insult to injury.

Thank you DuckHook for the dtailed explanation of how suspend can corrupt the hard drive. In my cae there were no other usb drives connected however I did click Shutdown/Restart and before the system had shutdown removed the live usb so that it would reboot after shutdown from the HDD.

While waiting to recreate a new live usb I turned my attention to hp Z400 w/s which similar suspend recovery problems. I followed your links and installed disk-repair during a live session using u14.04 DVD. I then rebooted the system got the grub menu and that was that. There were several unreadable error screens about suspend. What log would these be in? The code below captures my boot-repair experience,

```


http://paste.ubuntu.com/10739975.


/media/ubuntu/KINGSTON/Untitled Document 2boot-repair


ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: https://launchpad.net/boot-repair
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpp1xt_vlo/secring.gpg' created
gpg: keyring `/tmp/tmpp1xt_vlo/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpp1xt_vlo/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease  
Ign http://archive.ubuntu.com trusty-updates InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:2 http://ppa.launchpad.net trusty Release.gpg [316 B]
Hit http://archive.ubuntu.com trusty Release.gpg
Get:3 http://security.ubuntu.com trusty-security Release [63.5 kB]
Get:4 http://ppa.launchpad.net trusty Release [15.1 kB]                      
Get:5 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Hit http://archive.ubuntu.com trusty Release                                   
Get:6 http://ppa.launchpad.net trusty/main amd64 Packages [1,970 B]            
Get:7 http://archive.ubuntu.com trusty-updates Release [63.5 kB]               
Get:8 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]            
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [251 kB]  
Hit http://archive.ubuntu.com trusty/main amd64 Packages          
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                 
Get:11 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,459 B]
Get:12 http://security.ubuntu.com trusty-security/universe amd64 Packages [91.6 kB]
Hit http://archive.ubuntu.com trusty/main Translation-en                
Get:13 http://security.ubuntu.com trusty-security/main Translation-en [126 kB]
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en      
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Get:14 http://security.ubuntu.com trusty-security/universe Translation-en [50.8 kB]
Hit http://archive.ubuntu.com trusty/universe Translation-en     
Get:15 http://archive.ubuntu.com trusty-updates/main amd64 Packages [490 kB]
Get:16 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [9,238 B]
Get:17 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.7 kB]
Get:18 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [263 kB]
Get:19 http://archive.ubuntu.com trusty-updates/main Translation-en [232 kB]
Get:20 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [6,076 B]
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Get:21 http://archive.ubuntu.com trusty-updates/universe Translation-en [135 kB]
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Fetched 1,827 kB in 4s (389 kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install --y boot-repair && boot-repair
E: Command line option --y is not understood
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-extra efibootmgr gawk gksu glade2script libgksu2-0
  libsigsegv2 pastebinit
Suggested packages:
  mbr mdadm clean-ubiquity boot-info os-uninstaller gawk-doc
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra efibootmgr gawk gksu glade2script
  libgksu2-0 libsigsegv2 pastebinit
0 upgraded, 10 newly installed, 0 to remove and 395 not upgraded.
Need to get 1,500 kB/1,529 kB of archives.
After this operation, 6,110 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main libsigsegv2 amd64 2.10-2 [15.0 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main gawk amd64 1:4.0.1+dfsg-2.1ubuntu2 [781 kB]
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main glade2script all 3.2.2~ppa47~saucy [42.3 kB]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav all 4ppa33 [392 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty/universe libgksu2-0 amd64 2.0.13~pre1-6ubuntu4 [71.8 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-repair all 4ppa33 [11.6 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty/universe gksu amd64 2.0.2-6ubuntu2 [27.8 kB]
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav-extra all 4ppa33 [143 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty/main pastebinit all 1.4-3 [14.9 kB]
Fetched 1,500 kB in 1s (1,023 kB/s)                                         
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 170866 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-2) ...
Setting up libsigsegv2:amd64 (2.10-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Selecting previously unselected package gawk.
(Reading database ... 170874 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.0.1+dfsg-2.1ubuntu2_amd64.deb ...
Unpacking gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../glade2script_3.2.2~ppa47~saucy_all.deb ...
Unpacking glade2script (3.2.2~ppa47~saucy) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../boot-sav_4ppa33_all.deb ...
Unpacking boot-sav (4ppa33) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../boot-repair_4ppa33_all.deb ...
Unpacking boot-repair (4ppa33) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../boot-sav-extra_4ppa33_all.deb ...
Unpacking boot-sav-extra (4ppa33) ...
Selecting previously unselected package efibootmgr.
Preparing to unpack .../efibootmgr_0.5.4-7ubuntu1_amd64.deb ...
Unpacking efibootmgr (0.5.4-7ubuntu1) ...
Selecting previously unselected package libgksu2-0.
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu4_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-6ubuntu2_amd64.deb ...
Unpacking gksu (2.0.2-6ubuntu2) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../pastebinit_1.4-3_all.deb ...
Unpacking pastebinit (1.4-3) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Setting up glade2script (3.2.2~ppa47~saucy) ...
Setting up boot-sav (4ppa33) ...
Setting up boot-repair (4ppa33) ...
Setting up boot-sav-extra (4ppa33) ...
Setting up efibootmgr (0.5.4-7ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Setting up pastebinit (1.4-3) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gksu (2.0.2-6ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
ubuntu@ubuntu:~$ 
(gksudo:29387): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: https://launchpad.net/boot-repair
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpp1xt_vlo/secring.gpg' created
gpg: keyring `/tmp/tmpp1xt_vlo/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpp1xt_vlo/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease  
Ign http://archive.ubuntu.com trusty-updates InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:2 http://ppa.launchpad.net trusty Release.gpg [316 B]
Hit http://archive.ubuntu.com trusty Release.gpg
Get:3 http://security.ubuntu.com trusty-security Release [63.5 kB]
Get:4 http://ppa.launchpad.net trusty Release [15.1 kB]                      
Get:5 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Hit http://archive.ubuntu.com trusty Release                                   
Get:6 http://ppa.launchpad.net trusty/main amd64 Packages [1,970 B]            
Get:7 http://archive.ubuntu.com trusty-updates Release [63.5 kB]               
Get:8 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]            
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [251 kB]  
Hit http://archive.ubuntu.com trusty/main amd64 Packages          
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                 
Get:11 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,459 B]
Get:12 http://security.ubuntu.com trusty-security/universe amd64 Packages [91.6 kB]
Hit http://archive.ubuntu.com trusty/main Translation-en                
Get:13 http://security.ubuntu.com trusty-security/main Translation-en [126 kB]
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en      
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Get:14 http://security.ubuntu.com trusty-security/universe Translation-en [50.8 kB]
Hit http://archive.ubuntu.com trusty/universe Translation-en     
Get:15 http://archive.ubuntu.com trusty-updates/main amd64 Packages [490 kB]
Get:16 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [9,238 B]
Get:17 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.7 kB]
Get:18 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [263 kB]
Get:19 http://archive.ubuntu.com trusty-updates/main Translation-en [232 kB]
Get:20 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [6,076 B]
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Get:21 http://archive.ubuntu.com trusty-updates/universe Translation-en [135 kB]
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Fetched 1,827 kB in 4s (389 kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install --y boot-repair && boot-repair
E: Command line option --y is not understood
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-extra efibootmgr gawk gksu glade2script libgksu2-0
  libsigsegv2 pastebinit
Suggested packages:
  mbr mdadm clean-ubiquity boot-info os-uninstaller gawk-doc
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra efibootmgr gawk gksu glade2script
  libgksu2-0 libsigsegv2 pastebinit
0 upgraded, 10 newly installed, 0 to remove and 395 not upgraded.
Need to get 1,500 kB/1,529 kB of archives.
After this operation, 6,110 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main libsigsegv2 amd64 2.10-2 [15.0 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main gawk amd64 1:4.0.1+dfsg-2.1ubuntu2 [781 kB]
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main glade2script all 3.2.2~ppa47~saucy [42.3 kB]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav all 4ppa33 [392 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty/universe libgksu2-0 amd64 2.0.13~pre1-6ubuntu4 [71.8 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-repair all 4ppa33 [11.6 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty/universe gksu amd64 2.0.2-6ubuntu2 [27.8 kB]
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav-extra all 4ppa33 [143 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty/main pastebinit all 1.4-3 [14.9 kB]
Fetched 1,500 kB in 1s (1,023 kB/s)                                         
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 170866 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-2) ...
Setting up libsigsegv2:amd64 (2.10-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Selecting previously unselected package gawk.
(Reading database ... 170874 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.0.1+dfsg-2.1ubuntu2_amd64.deb ...
Unpacking gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../glade2script_3.2.2~ppa47~saucy_all.deb ...
Unpacking glade2script (3.2.2~ppa47~saucy) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../boot-sav_4ppa33_all.deb ...
Unpacking boot-sav (4ppa33) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../boot-repair_4ppa33_all.deb ...
Unpacking boot-repair (4ppa33) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../boot-sav-extra_4ppa33_all.deb ...
Unpacking boot-sav-extra (4ppa33) ...
Selecting previously unselected package efibootmgr.
Preparing to unpack .../efibootmgr_0.5.4-7ubuntu1_amd64.deb ...
Unpacking efibootmgr (0.5.4-7ubuntu1) ...
Selecting previously unselected package libgksu2-0.
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu4_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-6ubuntu2_amd64.deb ...
Unpacking gksu (2.0.2-6ubuntu2) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../pastebinit_1.4-3_all.deb ...
Unpacking pastebinit (1.4-3) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Setting up glade2script (3.2.2~ppa47~saucy) ...
Setting up boot-sav (4ppa33) ...
Setting up boot-repair (4ppa33) ...
Setting up boot-sav-extra (4ppa33) ...
Setting up efibootmgr (0.5.4-7ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Setting up pastebinit (1.4-3) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gksu (2.0.2-6ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
ubuntu@ubuntu:~$ 
(gksudo:29387): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: https://launchpad.net/boot-repair
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpp1xt_vlo/secring.gpg' created
gpg: keyring `/tmp/tmpp1xt_vlo/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpp1xt_vlo/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease  
Ign http://archive.ubuntu.com trusty-updates InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:2 http://ppa.launchpad.net trusty Release.gpg [316 B]
Hit http://archive.ubuntu.com trusty Release.gpg
Get:3 http://security.ubuntu.com trusty-security Release [63.5 kB]
Get:4 http://ppa.launchpad.net trusty Release [15.1 kB]                      
Get:5 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Hit http://archive.ubuntu.com trusty Release                                   
Get:6 http://ppa.launchpad.net trusty/main amd64 Packages [1,970 B]            
Get:7 http://archive.ubuntu.com trusty-updates Release [63.5 kB]               
Get:8 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]            
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [251 kB]  
Hit http://archive.ubuntu.com trusty/main amd64 Packages          
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                 
Get:11 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,459 B]
Get:12 http://security.ubuntu.com trusty-security/universe amd64 Packages [91.6 kB]
Hit http://archive.ubuntu.com trusty/main Translation-en                
Get:13 http://security.ubuntu.com trusty-security/main Translation-en [126 kB]
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en      
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Get:14 http://security.ubuntu.com trusty-security/universe Translation-en [50.8 kB]
Hit http://archive.ubuntu.com trusty/universe Translation-en     
Get:15 http://archive.ubuntu.com trusty-updates/main amd64 Packages [490 kB]
Get:16 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [9,238 B]
Get:17 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.7 kB]
Get:18 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [263 kB]
Get:19 http://archive.ubuntu.com trusty-updates/main Translation-en [232 kB]
Get:20 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [6,076 B]
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Get:21 http://archive.ubuntu.com trusty-updates/universe Translation-en [135 kB]
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Fetched 1,827 kB in 4s (389 kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install --y boot-repair && boot-repair
E: Command line option --y is not understood
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-extra efibootmgr gawk gksu glade2script libgksu2-0
  libsigsegv2 pastebinit
Suggested packages:
  mbr mdadm clean-ubiquity boot-info os-uninstaller gawk-doc
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra efibootmgr gawk gksu glade2script
  libgksu2-0 libsigsegv2 pastebinit
0 upgraded, 10 newly installed, 0 to remove and 395 not upgraded.
Need to get 1,500 kB/1,529 kB of archives.
After this operation, 6,110 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main libsigsegv2 amd64 2.10-2 [15.0 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main gawk amd64 1:4.0.1+dfsg-2.1ubuntu2 [781 kB]
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main glade2script all 3.2.2~ppa47~saucy [42.3 kB]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav all 4ppa33 [392 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty/universe libgksu2-0 amd64 2.0.13~pre1-6ubuntu4 [71.8 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-repair all 4ppa33 [11.6 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty/universe gksu amd64 2.0.2-6ubuntu2 [27.8 kB]
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav-extra all 4ppa33 [143 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty/main pastebinit all 1.4-3 [14.9 kB]
Fetched 1,500 kB in 1s (1,023 kB/s)                                         
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 170866 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-2) ...
Setting up libsigsegv2:amd64 (2.10-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Selecting previously unselected package gawk.
(Reading database ... 170874 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.0.1+dfsg-2.1ubuntu2_amd64.deb ...
Unpacking gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../glade2script_3.2.2~ppa47~saucy_all.deb ...
Unpacking glade2script (3.2.2~ppa47~saucy) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../boot-sav_4ppa33_all.deb ...
Unpacking boot-sav (4ppa33) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../boot-repair_4ppa33_all.deb ...
Unpacking boot-repair (4ppa33) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../boot-sav-extra_4ppa33_all.deb ...
Unpacking boot-sav-extra (4ppa33) ...
Selecting previously unselected package efibootmgr.
Preparing to unpack .../efibootmgr_0.5.4-7ubuntu1_amd64.deb ...
Unpacking efibootmgr (0.5.4-7ubuntu1) ...
Selecting previously unselected package libgksu2-0.
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu4_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-6ubuntu2_amd64.deb ...
Unpacking gksu (2.0.2-6ubuntu2) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../pastebinit_1.4-3_all.deb ...
Unpacking pastebinit (1.4-3) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) .../media/ubuntu/KINGSTON/Untitled Document 2boot-repair
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Setting up glade2script (3.2.2~ppa47~saucy) ...
Setting up boot-sav (4ppa33) ...
Setting up boot-repair (4ppa33) ...
Setting up boot-sav-extra (4ppa33) ...
Setting up efibootmgr (0.5.4-7ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Setting up pastebinit (1.4-3) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gksu (2.0.2-6ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
ubuntu@ubuntu:~$ 
(gksudo:29387): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: https://launchpad.net/boot-repair
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpp1xt_vlo/secring.gpg' created
gpg: keyring `/tmp/tmpp1xt_vlo/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpp1xt_vlo/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get update/media/ubuntu/KINGSTON/Untitled Document 2boot-repair
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease  
Ign http://archive.ubuntu.com trusty-updates InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:2 http://ppa.launchpad.net trusty Release.gpg [316 B]
Hit http://archive.ubuntu.com trusty Release.gpg
Get:3 http://security.ubuntu.com trusty-security Release [63.5 kB]
Get:4 http://ppa.launchpad.net trusty Release [15.1 kB]                      
Get:5 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Hit http://archive.ubuntu.com trusty Release                                   
Get:6 http://ppa.launchpad.net trusty/main amd64 Packages [1,970 B]            
Get:7 http://archive.ubuntu.com trusty-updates Release [63.5 kB]               
Get:8 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]            
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [251 kB]  
Hit http://archive.ubuntu.com trusty/main amd64 Packages          
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                 
Get:11 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,459 B]
Get:12 http://security.ubuntu.com trusty-security/universe amd64 Packages [91.6 kB]
Hit http://archive.ubuntu.com trusty/main Translation-en                
Get:13 http://security.ubuntu.com trusty-security/main Translation-en [126 kB]
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en      
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Get:14 http://security.ubuntu.com trusty-security/universe Translation-en [50.8 kB]
Hit http://archive.ubuntu.com trusty/universe Translation-en     
Get:15 http://archive.ubuntu.com trusty-updates/main amd64 Packages [490 kB]
Get:16 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [9,238 B]
Get:17 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.7 kB]
Get:18 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [263 kB]
Get:19 http://archive.ubuntu.com trusty-updates/main Translation-en [232 kB]
Get:20 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [6,076 B]
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Get:21 http://archive.ubuntu.com trusty-updates/universe Translation-en [135 kB]
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US/media/ubuntu/KINGSTON/Untitled Document 2boot-repair
Fetched 1,827 kB in 4s (389 kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install --y boot-repair && boot-repair
E: Command line option --y is not understood
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-extra efibootmgr gawk gksu glade2script libgksu2-0
  libsigsegv2 pastebinit
Suggested packages:
  mbr mdadm clean-ubiquity boot-info os-uninstaller gawk-doc
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra efibootmgr gawk gksu glade2script
  libgksu2-0 libsigsegv2 pastebinit
0 upgraded, 10 newly installed, 0 to remove and 395 not upgraded.
Need to get 1,500 kB/1,529 kB of archives.
After this operation, 6,110 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main libsigsegv2 amd64 2.10-2 [15.0 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main gawk amd64 1:4.0.1+dfsg-2.1ubuntu2 [781 kB]
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main glade2script all 3.2.2~ppa47~saucy [42.3 kB]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav all 4ppa33 [392 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty/universe libgksu2-0 amd64 2.0.13~pre1-6ubuntu4 [71.8 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-repair all 4ppa33 [11.6 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty/universe gksu amd64 2.0.2-6ubuntu2 [27.8 kB]
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav-extra all 4ppa33 [143 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty/main pastebinit all 1.4-3 [14.9 kB]
Fetched 1,500 kB in 1s (1,023 kB/s)                                         
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 170866 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-2) ...
Setting up libsigsegv2:amd64 (2.10-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Selecting previously unselected package gawk.
(Reading database ... 170874 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.0.1+dfsg-2.1ubuntu2_amd64.deb ...
Unpacking gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../glade2script_3.2.2~ppa47~saucy_all.deb ...
Unpacking glade2script (3.2.2~ppa47~saucy) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../boot-sav_4ppa33_all.deb ...
Unpacking boot-sav (4ppa33) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../boot-repair_4ppa33_all.deb ...
Unpacking boot-repair (4ppa33) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../boot-sav-extra_4ppa33_all.deb ...
Unpacking boot-sav-extra (4ppa33) ...
Selecting previously unselected package efibootmgr.
Preparing to unpack .../efibootmgr_0.5.4-7ubuntu1_amd64.deb ...
Unpacking efibootmgr (0.5.4-7ubuntu1) ...
Selecting previously unselected package libgksu2-0./media/ubuntu/KINGSTON/Untitled Document 2boot-repair
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu4_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-6ubuntu2_amd64.deb ...
Unpacking gksu (2.0.2-6ubuntu2) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../pastebinit_1.4-3_all.deb ...
Unpacking pastebinit (1.4-3) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Setting up glade2script (3.2.2~ppa47~saucy) ...
Setting up boot-sav (4ppa33) ...
Setting up boot-repair (4ppa33) ...
Setting up boot-sav-extra (4ppa33) ...
Setting up efibootmgr (0.5.4-7ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Setting up pastebinit (1.4-3) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gksu (2.0.2-6ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
ubuntu@ubuntu:~$ 
(gksudo:29387): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: https://launchpad.net/boot-repair
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpp1xt_vlo/secring.gpg' created
gpg: keyring `/tmp/tmpp1xt_vlo/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpp1xt_vlo/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease  
Ign http://archive.ubuntu.com trusty-updates InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:2 http://ppa.launchpad.net trusty Release.gpg [316 B]
Hit http://archive.ubuntu.com trusty Release.gpg
Get:3 http://security.ubuntu.com trusty-security Release [63.5 kB]
Get:4 http://ppa.launchpad.net trusty Release [15.1 kB]                      
Get:5 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Hit http://archive.ubuntu.com trusty Release                                   
Get:6 http://ppa.launchpad.net trusty/main amd64 Packages [1,970 B]            
Get:7 http://archive.ubuntu.com trusty-updates Release [63.5 kB]               
Get:8 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]            
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [251 kB]  
Hit http://archive.ubuntu.com trusty/main amd64 Packages          
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                 
Get:11 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,459 B]
Get:12 http://security.ubuntu.com trusty-security/universe amd64 Packages [91.6 kB]
Hit http://archive.ubuntu.com trusty/main Translation-en                
Get:13 http://security.ubuntu.com trusty-security/main Translation-en [126 kB]
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en      
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Get:14 http://security.ubuntu.com trusty-security/universe Translation-en [50.8 kB]
Hit http://archive.ubuntu.com trusty/universe Translation-en     
Get:15 http://archive.ubuntu.com trusty-updates/main amd64 Packages [490 kB]
Get:16 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [9,238 B]
Get:17 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.7 kB]
Get:18 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [263 kB]
Get:19 http://archive.ubuntu.com trusty-updates/main Translation-en [232 kB]
Get:20 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [6,076 B]
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Get:21 http://archive.ubuntu.com trusty-updates/universe Translation-en [135 kB]
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Fetched 1,827 kB in 4s (389 kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install --y boot-repair && boot-repair
E: Command line option --y is not understood
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-extra efibootmgr gawk gksu glade2script libgksu2-0
  libsigsegv2 pastebinit
Suggested packages:
  mbr mdadm clean-ubiquity boot-info os-uninstaller gawk-doc
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra efibootmgr gawk gksu glade2script
  libgksu2-0 libsigsegv2 pastebinit
0 upgraded, 10 newly installed, 0 to remove and 395 not upgraded.
Need to get 1,500 kB/1,529 kB of archives.
After this operation, 6,110 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main libsigsegv2 amd64 2.10-2 [15.0 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main gawk amd64 1:4.0.1+dfsg-2.1ubuntu2 [781 kB]
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main glade2script all 3.2.2~ppa47~saucy [42.3 kB]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav all 4ppa33 [392 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty/universe libgksu2-0 amd64 2.0.13~pre1-6ubuntu4 [71.8 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-repair all 4ppa33 [11.6 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty/universe gksu amd64 2.0.2-6ubuntu2 [27.8 kB]
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav-extra all 4ppa33 [143 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty/main pastebinit all 1.4-3 [14.9 kB]
Fetched 1,500 kB in 1s (1,023 kB/s)                                         
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 170866 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-2) ...
Setting up libsigsegv2:amd64 (2.10-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Selecting previously unselected package gawk.
(Reading database ... 170874 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.0.1+dfsg-2.1ubuntu2_amd64.deb ...
Unpacking gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../glade2script_3.2.2~ppa47~saucy_all.deb ...
Unpacking glade2script (3.2.2~ppa47~saucy) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../boot-sav_4ppa33_all.deb ...
Unpacking boot-sav (4ppa33) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../boot-repair_4ppa33_all.deb ...
Unpacking boot-repair (4ppa33) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../boot-sav-extra_4ppa33_all.deb ...
Unpacking boot-sav-extra (4ppa33) ...
Selecting previously unselected package efibootmgr.
Preparing to unpack .../efibootmgr_0.5.4-7ubuntu1_amd64.deb ...
Unpacking efibootmgr (0.5.4-7ubuntu1) ...
Selecting previously unselected package libgksu2-0.
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu4_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-6ubuntu2_amd64.deb ...
Unpacking gksu (2.0.2-6ubuntu2) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../pastebinit_1.4-3_all.deb ...
Unpacking pastebinit (1.4-3) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Setting up glade2script (3.2.2~ppa47~saucy) ...
Setting up boot-sav (4ppa33) ...
Setting up boot-repair (4ppa33) ...
Setting up boot-sav-extra (4ppa33) ...
Setting up efibootmgr (0.5.4-7ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Setting up pastebinit (1.4-3) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gksu (2.0.2-6ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
ubuntu@ubuntu:~$ 
(gksudo:29387): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: https://launchpad.net/boot-repair
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpp1xt_vlo/secring.gpg' created
gpg: keyring `/tmp/tmpp1xt_vlo/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpp1xt_vlo/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease  
Ign http://archive.ubuntu.com trusty-updates InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:2 http://ppa.launchpad.net trusty Release.gpg [316 B]
Hit http://archive.ubuntu.com trusty Release.gpg
Get:3 http://security.ubuntu.com trusty-security Release [63.5 kB]
Get:4 http://ppa.launchpad.net trusty Release [15.1 kB]                      
Get:5 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Hit http://archive.ubuntu.com trusty Release                                   
Get:6 http://ppa.launchpad.net trusty/main amd64 Packages [1,970 B]            
Get:7 http://archive.ubuntu.com trusty-updates Release [63.5 kB]               
Get:8 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]            
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [251 kB]  
Hit http://archive.ubuntu.com trusty/main amd64 Packages          
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                 
Get:11 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,459 B]
Get:12 http://security.ubuntu.com trusty-security/universe amd64 Packages [91.6 kB]
Hit http://archive.ubuntu.com trusty/main Translation-en                
Get:13 http://security.ubuntu.com trusty-security/main Translation-en [126 kB]
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en      
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Get:14 http://security.ubuntu.com trusty-security/universe Translation-en [50.8 kB]
Hit http://archive.ubuntu.com trusty/universe Translation-en     
Get:15 http://archive.ubuntu.com trusty-updates/main amd64 Packages [490 kB]
Get:16 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [9,238 B]
Get:17 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.7 kB]
Get:18 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [263 kB]
Get:19 http://archive.ubuntu.com trusty-updates/main Translation-en [232 kB]
Get:20 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [6,076 B]
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Get:21 http://archive.ubuntu.com trusty-updates/universe Translation-en [135 kB]
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Fetched 1,827 kB in 4s (389 kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install --y boot-repair && boot-repair
E: Command line option --y is not understood
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-extra efibootmgr gawk gksu glade2script libgksu2-0
  libsigsegv2 pastebinit
Suggested packages:
  mbr mdadm clean-ubiquity boot-info os-uninstaller gawk-doc
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra efibootmgr gawk gksu glade2script
  libgksu2-0 libsigsegv2 pastebinit
0 upgraded, 10 newly installed, 0 to remove and 395 not upgraded.
Need to get 1,500 kB/1,529 kB of archives.
After this operation, 6,110 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main libsigsegv2 amd64 2.10-2 [15.0 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main gawk amd64 1:4.0.1+dfsg-2.1ubuntu2 [781 kB]
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main glade2script all 3.2.2~ppa47~saucy [42.3 kB]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav all 4ppa33 [392 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty/universe libgksu2-0 amd64 2.0.13~pre1-6ubuntu4 [71.8 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-repair all 4ppa33 [11.6 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty/universe gksu amd64 2.0.2-6ubuntu2 [27.8 kB]
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav-extra all 4ppa33 [143 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty/main pastebinit all 1.4-3 [14.9 kB]
Fetched 1,500 kB in 1s (1,023 kB/s)                                         
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 170866 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-2) ...
Setting up libsigsegv2:amd64 (2.10-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Selecting previously unselected package gawk.
(Reading database ... 170874 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.0.1+dfsg-2.1ubuntu2_amd64.deb ...
Unpacking gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../glade2script_3.2.2~ppa47~saucy_all.deb ...
Unpacking glade2script (3.2.2~ppa47~saucy) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../boot-sav_4ppa33_all.deb ...
Unpacking boot-sav (4ppa33) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../boot-repair_4ppa33_all.deb ...
Unpacking boot-repair (4ppa33) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../boot-sav-extra_4ppa33_all.deb ...
Unpacking boot-sav-extra (4ppa33) ...
Selecting previously unselected package efibootmgr.
Preparing to unpack .../efibootmgr_0.5.4-7ubuntu1_amd64.deb ...
Unpacking efibootmgr (0.5.4-7ubuntu1) ...
Selecting previously unselected package libgksu2-0.
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu4_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-6ubuntu2_amd64.deb ...
Unpacking gksu (2.0.2-6ubuntu2) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../pastebinit_1.4-3_all.deb ...
Unpacking pastebinit (1.4-3) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Setting up glade2script (3.2.2~ppa47~saucy) ...
Setting up boot-sav (4ppa33) ...
Setting up boot-repair (4ppa33) ...
Setting up boot-sav-extra (4ppa33) ...
Setting up efibootmgr (0.5.4-7ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Setting up pastebinit (1.4-3) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gksu (2.0.2-6ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
ubuntu@ubuntu:~$ 
(gksudo:29387): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: https://launchpad.net/boot-repair
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpp1xt_vlo/secring.gpg' created
gpg: keyring `/tmp/tmpp1xt_vlo/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpp1xt_vlo/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2) trusty/restricted Translation-en
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease  
Ign http://archive.ubuntu.com trusty-updates InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:2 http://ppa.launchpad.net trusty Release.gpg [316 B]
Hit http://archive.ubuntu.com trusty Release.gpg
Get:3 http://security.ubuntu.com trusty-security Release [63.5 kB]
Get:4 http://ppa.launchpad.net trusty Release [15.1 kB]                      
Get:5 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Hit http://archive.ubuntu.com trusty Release                                   
Get:6 http://ppa.launchpad.net trusty/main amd64 Packages [1,970 B]            
Get:7 http://archive.ubuntu.com trusty-updates Release [63.5 kB]               
Get:8 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]            
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [251 kB]  
Hit http://archive.ubuntu.com trusty/main amd64 Packages          
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                 
Get:11 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,459 B]
Get:12 http://security.ubuntu.com trusty-security/universe amd64 Packages [91.6 kB]
Hit http://archive.ubuntu.com trusty/main Translation-en                
Get:13 http://security.ubuntu.com trusty-security/main Translation-en [126 kB]
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en      
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://archive.ubuntu.com trusty/restricted Translation-en
Get:14 http://security.ubuntu.com trusty-security/universe Translation-en [50.8 kB]
Hit http://archive.ubuntu.com trusty/universe Translation-en     
Get:15 http://archive.ubuntu.com trusty-updates/main amd64 Packages [490 kB]
Get:16 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [9,238 B]
Get:17 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.7 kB]
Get:18 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [263 kB]
Get:19 http://archive.ubuntu.com trusty-updates/main Translation-en [232 kB]
Get:20 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [6,076 B]
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Get:21 http://archive.ubuntu.com trusty-updates/universe Translation-en [135 kB]
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Fetched 1,827 kB in 4s (389 kB/s)
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install --y boot-repair && boot-repair
E: Command line option --y is not understood
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-extra efibootmgr gawk gksu glade2script libgksu2-0
  libsigsegv2 pastebinit
Suggested packages:
  mbr mdadm clean-ubiquity boot-info os-uninstaller gawk-doc
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra efibootmgr gawk gksu glade2script
  libgksu2-0 libsigsegv2 pastebinit
0 upgraded, 10 newly installed, 0 to remove and 395 not upgraded.
Need to get 1,500 kB/1,529 kB of archives.
After this operation, 6,110 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main libsigsegv2 amd64 2.10-2 [15.0 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main gawk amd64 1:4.0.1+dfsg-2.1ubuntu2 [781 kB]
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main glade2script all 3.2.2~ppa47~saucy [42.3 kB]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav all 4ppa33 [392 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty/universe libgksu2-0 amd64 2.0.13~pre1-6ubuntu4 [71.8 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-repair all 4ppa33 [11.6 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty/universe gksu amd64 2.0.2-6ubuntu2 [27.8 kB]
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ trusty/main boot-sav-extra all 4ppa33 [143 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty/main pastebinit all 1.4-3 [14.9 kB]
Fetched 1,500 kB in 1s (1,023 kB/s)                                         
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 170866 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-2) ...
Setting up libsigsegv2:amd64 (2.10-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Selecting previously unselected package gawk.
(Reading database ... 170874 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.0.1+dfsg-2.1ubuntu2_amd64.deb ...
Unpacking gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../glade2script_3.2.2~ppa47~saucy_all.deb ...
Unpacking glade2script (3.2.2~ppa47~saucy) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../boot-sav_4ppa33_all.deb ...
Unpacking boot-sav (4ppa33) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../boot-repair_4ppa33_all.deb ...
Unpacking boot-repair (4ppa33) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../boot-sav-extra_4ppa33_all.deb ...
Unpacking boot-sav-extra (4ppa33) ...
Selecting previously unselected package efibootmgr.
Preparing to unpack .../efibootmgr_0.5.4-7ubuntu1_amd64.deb ...
Unpacking efibootmgr (0.5.4-7ubuntu1) ...
Selecting previously unselected package libgksu2-0.
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu4_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-6ubuntu2_amd64.deb ...
Unpacking gksu (2.0.2-6ubuntu2) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../pastebinit_1.4-3_all.deb ...
Unpacking pastebinit (1.4-3) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Setting up glade2script (3.2.2~ppa47~saucy) ...
Setting up boot-sav (4ppa33) ...
Setting up boot-repair (4ppa33) ...
Setting up boot-sav-extra (4ppa33) ...
Setting up efibootmgr (0.5.4-7ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Setting up pastebinit (1.4-3) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gksu (2.0.2-6ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
ubuntu@ubuntu:~$ 
(gksudo:29387): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed


```

---

### Post by Vladlenin5000 on 2015-05-18
Did you actually used Boot-Repair and applied the recommend correction?

---

