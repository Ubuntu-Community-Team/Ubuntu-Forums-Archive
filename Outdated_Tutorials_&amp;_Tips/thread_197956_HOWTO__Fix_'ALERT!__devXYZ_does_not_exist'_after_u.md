---
title: "HOWTO : Fix 'ALERT! : dev/XYZ does not exist' after upgrade to Dapper Drake"
date: 2006-06-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Ted_Smith on 2006-06-16
I will begin by saying that I am still new to Linux and learning myself every day. This HOWTO is the result of several failed installations attempts of Dapper (and upgrading to it from Breezy). I am documenting my experiences in the hope that someone else won't spend an entire week trying to fix the problems I had. 

**Scenario**

You have Breezy Badger installed on your PC. You have an IDE disk connected to your IDE0 channel on the motherboard with, for arguments sake, a Windows partition and an Ubuntu partition on your disk. On your other IDE channel, IDE1, you have a CDROM\DVD Drive. You also have some other drives connected to an IDE adaptor (the number is insignificant but it could be several). 

You decide to upgrade from Breezy Badger to Dapper Drake. You do the necessary upgrade steps, and everything seems to run without a hitch. You reboot. And your faced with a tragedy that looks something similar to the following : 

```
 [b]
[COLOR="SandyBrown"]Ubuntu Logo Here

Loading Essential Drivers :                 [OK]
Mounting Root File System :                blank
Waiting for root filesystem :              blank
[/COLOR] [/b]

```

It sits there for 3 or 4 minutes until eventually your faced with a black screen and a terminal shell with a message along the lines of 

```

[b]Begin: Waiting for root file system... ...
Cannot find /dev/hda2
ALERT : dev/hda2 does not exist[/b]

BusyBox Built In Shell
#_

```

If you're new to Linux, or just uneasy about what you're doing, this is without doubt an absolute show stopper!! And no, doing a fresh install (so wiping your earlier attempts and re-trying) will not get round the problem either. And no, installing from the CD won't help you either (trust me, it won't - been there, tried that, cried in my cup of English tea, and re-tried again!). It's a big fat mess (at least it seems to be). So what the cause, and how do you fix it? Read on.  

**The Cause**

Ubuntu Dapper Drake (and I think it&#8217;s related to the 2.16 Kernel generally) re-assigns drive letter assignments very badly when your PC has multiple IDE devices installed. It was known as a bug prior to release but was only considered 'low priority'. Let me explain. You may have a disk set-up like this  : 

In Breezy Badger :
- hda 20Gb HDD
- hdc CD\DVD
- hde 160GB HDD
- hdf 160GB HDD

But on Dapper it becomes :
- hda 160GB HDD
- hdc 160Gb HDD
- hde 20Gb HDD
- hdf CD\DVD

So, your Breezy installation that was on hda get upgraded to Dapper, but after the upgrade something happens so that when you reboot Dapper thinks the root filesystem is on hda but 'hda' (the value 'hda' I mean) has been assigned to a different drive all together, But Dapper doesn&#8217;t know that. 

**OK. Well how the hell do I fix it?**

1) Download the Dapper Install Live install CD and burn the ISO to CD : [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

2) Test it works. 

3) Using your current installation (not live CD) temporaily remove all the mount references to your **additional drives** from etc/fstab and copy them to a text file in your home folder (or better still an external storage medium) for use later on. Leave your standard root partition and the swap partition as they are. 

```

Sudo gedit //etc/fstab

```

For example, change : 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> 		  <type>  <options>       <dump>  <pass>
proc            /proc        		   proc    defaults        0       0
/dev/hde2       /           		   ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none       		   swap    sw              0       0
[b]/dev/hdd5	/home/ted/Mounts/ext3	   ext3    rw,user,auto	   0       0
/dev/hda1	/home/ted/Mounts/reiser    reiserfs  rw,user,auto  0       0[/b] &#8211; Take these out
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

to : 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> 		  <type>  <options>       <dump>  <pass>
proc            /proc        		   proc    defaults        0       0
/dev/hde2       /           		   ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none       		   swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Save, and exit. 

4) Install or upgrade your installation from Breezy to Dapper (this step is beyond the scope of this HOWTO). 

5) Reboot. You will almost certainly find the problem will occur, but you never know, you might be OK in which case you don't need to read this :-). Otherwise, read on. 

6) Turn off your PC and unplug the power to your additional drives leaving only the one with your operating system on plugged in (you must make sure this step is done accurately in light of your adjustments to fstab). In my example, this is the disk recognised as dev/hda2 in fstab.

7) Reboot using the live CD you downloaded and created earlier in step 1. 

8) You should now be in the Live CD environment. Go to System, Administration,  Disk Information, and look at how Dapper has assigned your single IDE drive and partitions. Most likely, it will be something like &#8216;/dev/hde2&#8217; (instead of hda2). Make a note of that (in my case, hd**a**2 had been changed to hd**e**2).

9) Then you need to edit the boot loader of your main installation on your disk drive because it&#8217;s here where the confusion lies because entries are made that do not match what Dapper has assigns. To do that, we have to mount the partition with your main installation on with write access using the Live CD environment. So, while still in System Administration, Disk Information, navigate to your HDD with the install of Dapper on it, click the 'Partitions' tab and select the partition where it's actually installed. Then create a temporary mount point in the home folder of your Live CD session, and then click 'Enable'. You will see that if you then click Browse your main install files will be listed. [See this Screenshot for an example]("http://www.lost-doggies.com/temp_graphics/Screenshot.png").

10 ```
sudo edit Your_Temporary_Mount_Point/boot/grub/menu.lst
```

Near the bottom, for each entry you should see lines relating to the various Linux Kernels you&#8217;ve had installed on your machine and the partitions that they reside. For example : 

```

kernel /boot/vmlinuz-2.6.15-1-686 root=/dev/hd**a**5 ro 

```

where it says /dev/hda5 change it to the drive assignments that you noted earlier in step 8. For example, 

```

kernel /boot/vmlinuz-2.6.15-1-686 root=/dev/hd**e**5 ro 

```

If you want, change all the other values for your Recovery Mode entries and earlier Kernel entries too because otherwise they won&#8217;t work later on when you need them. Alternatively, wait to see if it works at all first. 

 Save the file, and reboot. 

11) With any luck, your new Ubuntu Dapper Drake system will now boot. Expect the usual graphics drivers problems especially if you&#8217;ve performed an upgrade (as opposed to fresh install) and if you used a specific driver for your graphics card such as Nvidia. Correcting that is another issue and beyond the scope of this HOWTO. It all depends on your graphics cards. 

12) Shut-down, re-connect your additional drives, and reboot back into Ubuntu. 

13) Go to System, Administration, Disk Information again and set new mount points for your additional drives. If you make them the same as before you can just copy and paste your mount entries that you removed earlier in step 3 back into fstab just as before except obviously you'll need to change the drive assignments in light of how Dapper has now decided to assign them. So whereas you may have had 

```

/dev/hdd5	/home/ted/Mounts/ext3	   ext3    rw,user,auto	   0       0. look at how Dapper 

```

Under Dapper it may now be 

```

/dev/hde5	/home/ted/Mounts/ext3	   ext3    rw,user,auto	   0       0

```

I hope that helps. 

**PLEASE NOTE : It seems that every time your Linux kernal is upgraded, the re-assignment back to the wrong partitions occur so you have to edit the menu.lst file again using the Live CD environment. So keep this HOW TO in your favourites!!**

Lastly, while this may seem infinately annoying at the time, it's no different to Windows assigning 'Drive C:' during installation to a drive other than what you intended when you have several disks present. On several occasions I've had to disconnect disks before re-installing a fresh copy of Windows for the very same reason. The only difference is that Windows copes with it whereas Linux doesn't like it. Like most things, this is why Windows is a bit messy whereas Linux is stricter and the by the book and rather than putting it up with it it wants you to fix it.  

Other references : [http://www.ubuntuforums.org/showthread.php?t=186930&page=2](http://www.ubuntuforums.org/showthread.php?t=186930&page=2)

---

### Post by oppio on 2006-06-23
Hi,

I'm facing the problem addressed by this HOWTO after upgradind Dapper from kernel 2.6.15-23-386 to 2.6.15-25-386, together with other upgrades. I've tried everything but I still run into the problem without any solution.

The strange thing is that, after upgrading, my drives keep being mapped as they were before, but I get the "ALERT! /dev/hdb2 does not exist" message and get dropped to busybox. 

Here comes my drives mapping:

- hda 40Gb HDD (windows)
- hdb 40Gb HDD (Fedora 4 on hdb1 and Kubuntu 6.06 on hdb2)
- hdc CD\DVD
- hdd 200GB HDD

I can say for sure that mappings didn't change because I checked at boot without the quiet and splash parameters.
My mobo has SATA controllers aswell but no drives plugged to.

I tried everything I could find in the forums but helplessly. I wonder why the hell can't it mount hdb2 if it finds it while booting ?! 
And, how can I recover from this problem? I'd like avoiding reinstall from scratch.....


thanks in advance

---

### Post by Mzee nyuki mpya on 2006-06-23
Hi,

---

### Post by Mzee nyuki mpya on 2006-06-23
I'm not used to posting; this is my third time of typing this...

After 6 months of using Breezy, I found it easy to upgrade to Dapper, which I enjoyed for about 10 days. Then next time I tried to boot I had this problem!

When I tried the recovery option in Grub I got more information:

[4294674.903000] EXT3-fs error (device hdb1): ext3_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)!
[4294674.903000] EXT3-fs group descriptors corrupted!

I can now only use the PC with the Breezy Live CD. I can open System-Administration-Disks, but it doesn't allow me to enable access to it.
My plan is to have the Live CD in the DVD drive and a blank CD in the CD-RW drive and copy the files in my Home folder before wiping off Dapper and re-installing Breezy, as several people have suggested.
Does anyone know how to do this so I can avoid re-entering 6 months of Gnucash data?!

---

### Post by Ted_Smith on 2006-06-24
Oppio - have you done as I wrote in the HOW TO? You look to be having the same problem I had. If you follow the HOW TO, it should work. 

Mzee - your problem looks like a seperate issue from the issue that this HOW TO addresses. I would suggest starting a fresh thread - I am sorry, I do not know enough to help you.

---

### Post by MDesigner on 2006-06-25
Nice post, but unfortunately doesn't apply to those of us who are not coming from a previous version of Ubuntu, or Linux at all.  I'm doing a fresh install of Dapper Drake 6.06, and I'm getting this problem.  Any ideas on how to resolve this?  If I boot the live CD, /dev/sda3 is alive & well, and it is indeed the proper partition that I installed Ubuntu on (/dev/sda2 is swap).  So why would it not work when booting on the HD?

---

### Post by Halleck on 2006-06-26
[QUOTE=MDesigner]Nice post, but unfortunately doesn't apply to those of us who are not coming from a previous version of Ubuntu, or Linux at all.  I'm doing a fresh install of Dapper Drake 6.06, and I'm getting this problem.  Any ideas on how to resolve this?[/QUOTE]
Yes, information on what to do about a fresh install of Dapper would be greatly appreciated. I've been stuck for the past 12 hours or so trying to get my Ubuntu LiveCD and my Xubuntu alternate installation disc to work, but they continue to stall. My ubuntu cd freezes here:
```
Ubuntu Logo Here

Loading Essential Drivers :                 [OK]
Mounting Root File System :
```

Xubuntu prompts me for my language, location, and keyboard layout. After ostensibly detecting my CD-ROM drives, it freezes too.

If it's of any help, I'm installing this on my webserver, an old Pentium-II machine with 128mb of ram. That's why I thought xubuntu would be a good choice. It has two hard drives, a floppy drive, and two CD-ROM drives (the slave CD drive is actually a CD-RW.) Right now, Windows 98 is installed, but i'm running Mandrake 8.1 most of the time using lnx4win.

Wierd setup, I know. :) 

BTW, I checked both discs on my desktop PC. They both passed their self-checks for defects and I was able to boot off the LiveCD successfully, so it's not an issue with the media.

Anyway, any help with this would be greatly appreciated. Thanks!

---

### Post by MDesigner on 2006-06-26
Halleck, do us a favor.. boot up ubuntu, but choose recovery mode.  Watch the text fly by.. and when it hangs, just leave it for a while.  I'm betting eventually you'll get an error that says "ALERT! /dev/whatever does not exist. Dropping to a shell."

---

### Post by Halleck on 2006-06-26
[QUOTE=MDesigner]Halleck, do us a favor.. boot up ubuntu, but choose recovery mode.  Watch the text fly by.. and when it hangs, just leave it for a while.  I'm betting eventually you'll get an error that says "ALERT! /dev/whatever does not exist. Dropping to a shell."[/QUOTE]
Okay. My Ubuntu LiveCD does not have that option, but my Xubuntu CD does, so I tried that.

I left it for over half an hour, it's still hanging at the blue screen after the hardware detection.

---

### Post by MDesigner on 2006-06-26
[QUOTE=Halleck]Okay. My Ubuntu LiveCD does not have that option, but my Xubuntu CD does, so I tried that.

I left it for over half an hour, it's still hanging at the blue screen after the hardware detection.[/QUOTE]

OK, so much for that.  I figured it's similar to the prob after installing Ubuntu.  Sorry :(

---

### Post by Halleck on 2006-06-26
[QUOTE=MDesigner]OK, so much for that.  I figured it's similar to the prob after installing Ubuntu.  Sorry :([/QUOTE]
Hm, too bad.

Hopefully there is a workaround for my problem. I'm on a tight schedule here- If I can't find one quickly I'm probably going to have to find another distro, which would be too bad since I'm starting to like Ubuntu already. :)
What I need is a stable and easy-to-configure subversion/webserver. Maybe debian would work, I was looking forward to using apt.

---

### Post by MDesigner on 2006-06-26
Consider MEPIS.  It's Debian based.. and was pretty decent last time I tried it (a year or so ago).

---

### Post by Halleck on 2006-06-27
I talked with the MEPIS folks, who reccomended a vanilla install of Debian in my case (since I'm not going to be using it as a desktop.) That's what I decided to go with, it seems to fit my criteria and I still get to use apt.

Hopefully there is some sort of workaround for the Ubuntu LiveCD booting problem that future users with systems like mine will be able to take advantage of. I'd normally wait longer to see if there's a solution, but I have to get a subversion repository running ASAP.

Please raise the priority of this bug so it can be fixed in the next release!

---

### Post by Ted_Smith on 2006-06-28
Hi guys

Apologies for the delay. I've been away from home since the weekend and only just had chance to log in. 

In response to those that say that the HOW TO does not apply to fresh installs....it does, or at least I tried to make it so but perhaps it's not that clear. As I wrote in the first section, the issue of the wrong IDE assignments does apply regardless of whether it's a fresh install or an upgrade from an earlier install. 

If you're doing a fresh install on a blank disk (for example), disconnect all your other drives (physcially unplug them) and then let the installation finish on your single IDE drive so that your disk gets partitioned in line with however Dapper wants to do it. You then have to boot using the Live CD to actually see how Dapper has decided to assign your drive and partitions. Then obviously you mount your Ubuntu disk and partition, make the appropriate changes to menu.lst and then reboot it. That should work. 

MDesigner : 

> If I boot the live CD, /dev/sda3 is alive & well, and it is indeed the proper partition that I installed Ubuntu on (/dev/sda2 is swap). So why would it not work when booting on the HD?

When you get the 'ALERT!' message what partition does it say it cannot find? If it says it cannot find sda3 you need to make sure you mount it using the Live CD, edit menu.lst so that the entries point to sda3 (and not whatever else it is pointing to) and then reboot. BTW - you can edit the file by pressing ESC at boot up (it uses the GNOME boot loader editor I think) and then clicking 'e' on the individual entries to edit them. I only learnt that the other day. 

Apologies if I've mis-understood - I'm learning Linux myself still :-)

Ted

---

### Post by oppio on 2006-06-30
Ted_Smith: yes I followed your howto but no chance to get it working :(

(btw sorry for the delay but I've been busy with work....)

I'd like to point out that I got that problem with a working Dapper Drake installation, after getting some automatic updates (which caused a system crash)...
And the most odd part is that drive mappings didn't change at all. I guess the updates made dev not working in some way.... but I'm not so skilled to understand what isn't working :(

---

### Post by oppio on 2006-06-30
Hi all,

I've found something new that may help understanding why Ted's HOWTO doesn't work for my system.

I've tried using grub's CLI to investigate my filesystem and I found that it hangs on (hd1,1) (which is /dev/hdb2, where I've got my Dapper Drake). In particular, if I try

<code>
root (hd1,1)
cat /etc/fstab
</code>

it hangs and I have to reboot. If i try on (hd1,0) (where I've got Fedora) it works fine.

This may explain why kubuntu always fails mounting root filesystem from /dev/hdb2 even if drive mapping are fine.

I tried running e2fsck on /dev/hdb2 but it says it's clean. I tried with the -f option but it seems not to fix anything, just reports what is being checked and a inodes/blocks/files summary.

Any advice would be greatly appreciated at this point ;)

Valerio

---

### Post by ronly on 2006-07-03
Yet another user with the same problem. If I choose my previous kernel in grub (2.6.12-10-k7) the system loads as it should but once I try 2.6.15-23 or -25 I get this problem. Whilst I can use my computer with the old one I do have some other problems with it and think I should try the new one in case they've been fixed but can't do that due to this :(

---

### Post by Ted_Smith on 2006-07-04
It's been experienced by quite a lot of people and a bug was raised in Jan 06. I have added this HOW TO to it to assist users and developers. See here : 

[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/+index](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/+index)

---

### Post by keybuk on 2006-07-04
[QUOTE=Ted_Smith]Ubuntu Dapper Drake (and I think it’s related to the 2.16 Kernel generally) re-assigns drive letter assignments very badly when your PC has multiple IDE devices installed. It was known as a bug prior to release but was only considered 'low priority'.[/QUOTE]

This is not accurate.  The bug was considered HIGH priority, as anybody who looks at the bug tracking system can see.  However the fix for the bug was considered too dangerous to deploy close to the release.

The January bug filing time is misleading, as the bug did not contain sufficient useful information to explain the bug until only a matter of weeks away from dapper's release.

It's one of the truths of release management that sometimes it is better to ship with a known bug, than an unknown fix -- as at least you can explain to people how to work around the bug, rather than discover new problems.  This was one of those times, the fix for this bug causes other problems (usually the master soundcard changing, etc.)

---

### Post by Ted_Smith on 2006-07-04
> The bug was considered HIGH priority, as anybody who looks at the bug tracking system can see.

I can't recall which bit on the net it was that I read, but I am failry sure it was the actual bug record which I have given the link to and which I assume you are referring to. Initially it was low priority but has since been raised to high priority at some point in time since. It is not my intention to give misleading info (if it was definately wrong) - I was just going on what I read. 

Also, I gave a faulty link earlier. It's actually [https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367), bug reference is 6367

I entirely agree with you about the bug issues vs release dates etc. The point I was making about this particular issue is that potentially **anyone** with more than one IDE hard disk is going to be affected by this. In my humble opinion, I would have preferred the launch of Dapper to have been further delayed until it was fixed (I realise it was delayed by 6 weeks for further testing anyway) rather than trying to launch it in time with targets. Surely we're heading down the MS road by doing that and effectively releasing faulty software for the purpose of meeting deadlines? 

Ted

---

### Post by Fariam on 2006-07-12
> **Ted_Smith said:**
>  
3) Using your current installation (not live CD) temporaily remove all the mount references to your **additional drives** from etc/fstab and copy them to a text file in your home folder (or better still an external storage medium) for use later on. Leave your standard root partition and the swap partition as they are. 

```

Sudo gedit //etc/fstab

``` 

I'm sorry, I'm relatively new to Linux. At this step, am I to type the above command in the busybox shell? If so -- when I do, it tells me that it doesn't recognize the command sudo nor does it recognize gedit. 

Thank you for the how to.

---

### Post by ronly on 2006-07-13
No, you're not supposed to type that into the busybox shell. That's used to edit fstab but you won't be able to do that unless you can boot with some other kernel or CD so that you can access your files. And editing fstab only solves the problem in some cases - not e.g. mine :(

---

### Post by msemtd on 2006-07-13
I'm having a similar problem with udev but my machine only has one HDD. I've tried other kernels by booting to knoppix, chrooting back to /dev/hda1 (correctly enumerated under knoppix!) and running apt-get to select more kernels but they all fail the same. I don't know which drive I should be telling grub to get the initrd from - what else could it be other than hda1 on my simple setup?

---

### Post by Ted_Smith on 2006-07-14
Msemtd - soory, I am not good enough with Linux to help you there. This HOW TO was written purely with dual IDE controllers in mind. 

Fariam - The removal of the mount references is to be done BEFORE you upgrade to Dapper from Breezy using your current installation of Breezy. The idea being that you then shut Breezy down and re-boot using the Install CD. 

If you installing from scratch this step is not necessary - you just need to unplug your extra drive and boot up with the Install CD. 

I hope that helps

Ted

---

### Post by msemtd on 2006-07-14
OK, I have it fixed now: it was soem fallout from a suspected bug in initramfs-tools [https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/32123](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/32123)

I had to chroot to /dev/hda1 from a live cd and remove udev, initramfs-tools, and all kernels - then replace latest and add latest kernel that rebuilt initrd.

---

### Post by ubuntu_demon on 2006-07-14
**Everyone please test this general workaround :**

[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69)

[quote=Paul Sladen]
For those still wondering; The workaround for this issue involves specifying the partition to boot from by ID, rather than the transient location:

  1. Boot a desktop/LiveCD.
  2. Run sudo /sbin/dumpe2fs /dev/sdX | grep UUID
  3. tell 'grub' or 'lilo' to boot with that ID:

     linux ... root=UUID=d4c51a2a-d93f-4dc1-8717-9c3cdb4d41ce

and also adjust this in:

  /boot/grub/menu.lst
[/quote]

Replace sdX for sda, sdb, sdc, sdd, hda,hdb,hdc,hdd or whatever gparted on the livecd tells you it is.

You can post results either on launchpad here :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/)
Or in this thread :
[http://ubuntuforums.org/showthread.php?p=1257154](http://ubuntuforums.org/showthread.php?p=1257154)

---

### Post by jmbarbier on 2006-07-21
Workaround does not seem to work for me...

I had Breezy on hda1, and I can boot with my old breezy kernel. But with 2.6.15 of Dapper, I have

(..)
[17179573.004000] hda: HTS726060M9AT00, ATA DISK drive
[17179572.540000] hdc: QSI CR-RW/DVD-ROM SBW-241, ATAPI CD/DVD-ROM drive
................. ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
................. ide1 at 0x170-0x177,0x376 on irq 15
Done.
Begin: Waiting for root filesystem... ...
Done.
ALERT! /dev/hda1 does not exist. Dropping to a shell!

and back to busybox. 

This is exactly the same for root by UUID except that message ALERT! gives /dev/disk/by-uuid(...) does not exist.

Bad thing for ubuntu...

---

### Post by mod187 on 2006-07-26
After reading your post, and having problems trying to install 6.06 (new install), I tried to install 5.10 and upgrade to 6.06. 

Only problem (and it's a big one) is that after completing the install, and rebooting, I am getting the same error with 5.10 that I did with 6.06:

> ALERT! /dev/hda2 does not exist. Dropping to a shell!


Then I go to BusyBox. Any thoughts on this? I have another thread started on this, If you would not mind looking at it:
[http://www.ubuntuforums.org/showthread.php?t=212907](http://www.ubuntuforums.org/showthread.php?t=212907)

Thanks,
.\\

---

### Post by ubuntu_demon on 2006-08-17
From [https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/) :

[quote=Scott James Remnant]
Officially marking as Rejected for dapper.

Here is the reasoning:

- We applied the &#8220;fix&#8221;, as planned, to the udev in Edgy Eft.

- While the fix corrected the problem described here, it caused new problems. Because it was a fundamental change to device ordering, it changed the order of other devices where more than one existed in the system &#8212; including other disks

- For Edgy this was not a problem, as the upgrade makes other changes that make device order non-important anyway

- These changes are too invasive for backporting to dapper

- This bug has a known workaround, which can be applied by the minority of users affected by it

- That workaround is preferable to causing far more working systems to cease functioning.
[/quote]

---

### Post by mod187 on 2006-08-17
My problem I mentioned above (and linked to another thread) has been resolved. The problem was with my hard drive. There is other info on things I tried that did not work in that other thread

[http://www.ubuntuforums.org/showthread.php?t=212907](http://www.ubuntuforums.org/showthread.php?t=212907)

---

### Post by ubuntu_demon on 2006-08-22
Here are workarounds (which need testing) :
[http://ubuntuforums.org/showthread.php?p=1257154](http://ubuntuforums.org/showthread.php?p=1257154)
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83)

---

### Post by mrfuzzemz on 2006-09-16
I'm having the same problem with nothing after "Mounting root file system" and then "Waiting for root file system" followed eventually by ALERT! /dev/sda5 does not exist...etc..  I'm using a notebook with one SATA hard disk.  I have no problem booting from the LIVE/INSTALL CD and installing.  It's the reboot after the install where this occurs.  I've made sure Grub is set to the same sda5 the LIVE CD does and nothing changes.  Has anyone gotten this figured out?

---

### Post by sundarece on 2006-10-18
Hi all,

I got hit by the same crap about an hour ago. Is there a way to assign the correct addresses to partitions without having to open up my computer, like modifying the fstab? 

My situation:

I changed the sources.list "breezy" to dapper, and initiated the change to ubuntu 6.06 through my Syn.Package.Mgr.

All installations went fine and I was asked to reboot.. and BAM!](*,) 
"ALERT: dev/sda3 does not exist."

The older versions on my bootlist works (although with some problems with soundcard etc) and I can log into my system. But the newest version (i guess the one with the highest version number) does not work.

So, if I log into the older version and change the fstab would it work??

---

### Post by mrfuzzemz on 2006-10-18
If you'd like to boot up usually you can get by it editing your grub menu.list.  Just add acpi=off to the end of the boot line that specifies the root partition. That should allow you to boot up.  What I do after that is compile the latest kernel by following the kernel.orh HOW TO here in the forums.  I can then remove the acpi=off entry. Good luck

---

### Post by fopetesl on 2006-10-24
You also might like to note that if you swap IDE0 & IDE1 around you get the same error.  For some reason you get to boot OK but after loading the kernel the message "[COLOR="Red"]**/dev/hda1 does not exist**[/COLOR]" appears.
It took me a while to realise what I had done wrong.

---

### Post by mrfuzzemz on 2006-10-24
I would recommend upgrading to edgy--it uses kernel 2.6.17 and this problem does not exist in this kernel. The final release candidate is very stable, but you could also wait until the final release the 26th.

---

### Post by Ted_Smith on 2006-10-27
> **mrfuzzemz said:**
> I would recommend upgrading to edgy--it uses kernel 2.6.17 and this problem does not exist in this kernel. The final release candidate is very stable, but you could also wait until the final release the 26th.

Yep - the initial problem was specifically related to the kernel I believe, and not actually the Dapper release of Ubuntu. Other Linux distro's were also affected but somehow workarounds were built in I think. 

I'm sure that Edgy will be fine, although I have not installed that yet myself.

---

### Post by mrfuzzemz on 2006-10-27
I've installed edgy and no longer experience this problem.  Back when I had dapper installed I compiled a newer version of the kernel to get it working.  I had to boot dapper with acpi off while I compiled 2.6.18 and then I could boot edgy without the acpi=off bit in grub.

---

### Post by wavesound on 2007-01-24
> **Ted_Smith said:**
> Yep - the initial problem was specifically related to the kernel I believe, and not actually the Dapper release of Ubuntu. Other Linux distro's were also affected but somehow workarounds were built in I think. 

I'm sure that Edgy will be fine, although I have not installed that yet myself.

Hi
I have the same probs as stated in this long posting.

After SMART telling me my 150 gig was about to die (thank you) I upgraded to a SATA disk 250 gig.

I have installed Edgy EFT 6 10 from Linux magazine.

Here is my drive config:

************************************

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         522     4192933+   7  HPFS/NTFS
/dev/hda2             523        3741    25856617+   f  W95 Ext'd (LBA)
/dev/hda3            3742        7475    29993355    7  HPFS/NTFS
/dev/hda5             523        3741    25856586    7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9352    75119908+  83  Linux
/dev/hdc2            9353        9729     3028252+   5  Extended
/dev/hdc5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       30401   243947025    5  Extended
/dev/sda5              32         408     3028221   82  Linux swap / Solaris
/dev/sda6             409       30401   240918741   8e  Linux LVM
studio@studio-desktop:~$

************************************************

Here is the drive mapping:

***********************************************

(hd0)	/dev/hda
(hd1)	/dev/hdc
(hd2)	/dev/sda

***********************************************

And here is the menu list I use,
only the top kernal will boot
I can't boot the sda or windows on hd0

********************************************

title		Ubuntu,Studio, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title Windows XP
rootnoverify (hd0,0)
chainloader +1(hd0,0)

title		Ubuntu, kernel 2.6.17-10-generic
root		(sd0,0)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
savedefault
boot


title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:

title		Windows 2000 Professional
root		(hd0,1)
makeactive
chainloader	+1

*********************************************

What am I doing wrong here.
I have spent hours on this.


Is it this drive mapping causing the problem?

I have no primary slave anymore, it's the sata disk.

I note that my kubuntu is now on hd0 same as windows!

](*,) 

Cheers
Bob

---

### Post by mrfuzzemz on 2007-01-24
You say that only the Ubuntu Studio install boots properly?  What kind of messages does it spit out when not booting?

You may want to try different boot options that what you have.  Maybe check grubs manual.  Here is what my XP grub listing looking like

```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Also. sd0 may not be correct nomenclature. I only have a SATA drive and it is listed as hd0. Your drive may be hd1 or something similar.  Let me know what progress you make.

---

### Post by rocketero on 2010-08-11
Amazing, that after more than 3 and a half years of the last post on this thread I am experiencing the same problem posted here.

I upgraded from Ubuntu 8.10 to 9.04

Then from 9.04 to 9.10

And lastly from 9.10 to 10.04.

The issue showed up after the last upgrade and I have not been able to make it run. I can use the LiveCD and access the content of the disk but after reinstalling grub in that disk the problem persist.

What a bummer !!!

---

