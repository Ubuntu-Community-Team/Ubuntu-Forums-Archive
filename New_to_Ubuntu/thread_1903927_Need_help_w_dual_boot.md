---
title: "Need help w/ dual boot"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by ClientAlive on 2012-01-03
Hi,

I have a computer with a Linux system on it that I built, basically from the ground up - took me a long, long time and lots of frustration to do it. That system also has some free space on one of it's disks (roughly 20 Gb) and it happens that I need to have a Windows installation for one of my college courses. I have Win XP available to install there. There are two things I've picked up in my experience on the forums regarding dual booting with Windows: (1) That you should install Windows first then Linux; and (2) that Windows likes to be on the first partition of the first disk.

Because my current Linux installation is not something I could just redo easily I must find a way to install Windows now (as in, second) and install it to a partition it may not normally want to be on (sda4). I have a couple specific questions and I also wonder - are there any things I should know that would make this easier?


Some of my specific questions and concerns are:

* Windows has a boot loader and Linux has a boot loader - right?
* Is it that a person is to choose one or the other?
* If so, I would choose grub (which is what my Linux insall uses now)
* Can someone give me a general sketch as to how to approach this?
* One of my concerns is that even if I select that partion
  (corresponding   to sda4) duruing the Windows installation - could
  Windows not do what I expect it to and still whipe out my current
  install anyway? I mean, could it end up formatting some other area even
  if I tell it that partion?
* The part about tweaking in the boot loader is a smaller concern.


Bottom line is - I can't afford to have anything happen to that Linux install. It's fairly complicated - RAID, lvm2, 3 disks, directories under root broken into about 6 parts in lvm; and, in general, a distro that you don't just pop a disk in and click "install" you build it yourself from the ground up.


My general partition structure is:

```

sd[a - c]1: 100 Mb (each)  /boot  raid 1
  sd[a - c]2: 6 Gb (each)  (Extended)
  sd[a - c]5: 4 Gb (each)  /root  raid 1
  sd[a - c]6: 2 Gb (each)  /swap  raid 1
sd[a - c]3 68.43 Gb  (each)  ** lvm under raid 5 is here **

```


That's the Linux system. Now...

There is an sda4. What's going on is that my disk sda is larger than the other two by roughly 20 Gb. What I did was carve out 80 Gb from that disk and run my Linux system across the other two 80 Gb disks plus 80 Gb from that larger disk. Now I want to put windows on that extra space (sda4).

What should I expect? Most especially, how can I pull this off successfully? Any ideas?
-------------------

Edit:

I was thinking about it and I think what I'd like to do, if it's possible, is use grub to boot both o/s. What I'm uncertain about with that is if I would need to chain boot (so grub points to the windows boot loader then the windows boot loader takes over and boots windows) or if I can just eliminate the windows boot loader from the system altogether.

---

### Post by arpanaut on 2012-01-03
Just an off the wall suggestion...
Considering the complicated partitioning scheme you have, why not buy another HDD and install windows to that drive,
and either use bios to select which OS to boot or after installation, switch back to your original boot selection in the bios and then rum update-grub from there.

Grub would then pick up the windows disc and should boot from the grub menu.
You may want to disconnect your other drives while installing to prevent windows from screwing with your present system.

There may be some other hoops to jump through to make sure things end up well...

Just a suggestion.  Not sure it would be all that easy, but I think it would be doable if done carefully.
I don't trust the Windows installer to do exactly what you tell it to.

---

### Post by ClientAlive on 2012-01-03
> **arpanaut said:**
> Just an off the wall suggestion...
Considering the complicated partitioning scheme you have, why not buy another HDD and install windows to that drive,
and either use bios to select which OS to boot or after installation, switch back to your original boot selection in the bios and then rum update-grub from there.


It's an older (about 5 yrs old) computer that I resurrected from parts I gathered. I'm fresh out of busses to plug things into or I would (there's two busses = 4 channels and they all have a drive connected). I do have another different hard drive with a working windows install on it but I wasn't sure it's safe to swap disks in a raid system and run that other disk like that - seems dangerous (to the raided disks I mean). I may do a new desktop build soon; but, unfortunatly, it won't be soon enough since I need a working windows intall before next week Wednesday.

> **arpanaut said:**
> 
Grub would then pick up the windows disc and should boot from the grub menu.
You may want to disconnect your other drives while installing to prevent windows from screwing with your present system.

There may be some other hoops to jump through to make sure things end up well...

Just a suggestion.  Not sure it would be all that easy, but I think it would be doable if done carefully.
I don't trust the Windows installer to do exactly what you tell it to.

I'm a little leary of how Windows will behave during installation myself. Ultimately I think I'm forced to make due with the situation as it is somehow.
---------------------

Edit:

As a side note - and not that this is a healthy way to think about it - I condsidered that if that Linux system is raided, and I'm trying to install windows to just the one disk, that if something did go wrong I could just rebuild the raid. Uck! That's just an ugly way to look at things.

---

### Post by arpanaut on 2012-01-03
I have never tried to install windows on a system as an afterthought...
So I would not know where to begin, especially onto a raid set as you have.
Maybe some of the more knowledgeable members will show up to help.

Sorry I wasn't of more help.

---

### Post by cortman on 2012-01-03
If possible I think I'd like the idea of a separate HD as well... But instead, why don't you pop in a Win7 disk and see what kind of options you get under the "manually edit partitions". Unless you've tried it already. I don't think you have to make any changes to the computer to get that far. It might turn out easier than you think.

---

### Post by ClientAlive on 2012-01-03
> **cortman said:**
> If possible I think I'd like the idea of a separate HD as well... But instead, why don't you pop in a Win7 disk and see what kind of options you get under the "manually edit partitions". Unless you've tried it already. I don't think you have to make any changes to the computer to get that far. It might turn out easier than you think.

Well, I don't have Win7, I have XP. I'm not sure what all the differences are but I don't think XP has those options. Now I did find an old post where I was given some infomation by which I learned how to trick windoz into installing on a different partition. Problem is it involved reformatting the disk in order to trick it. At that time, I could do that because I didn't have anything else on the disk anyhow. Now that has changed.

That thread is here: [http://ubuntuforums.org/showthread.php?t=1838093&page=2](http://ubuntuforums.org/showthread.php?t=1838093&page=2)  (notice posts #11  and #eighteen - stupid smileys).

The gist of it is you can make the other partitions (the ones you don't want Windows on) into extended partitions and then Windows doesn't even see them. It just sees the one you left as primary (even if it isn't the first one) and it installs there. Then you have to go in and manually edit it's boot.ini file to change the entry for what partition it's on.

That being said, I wonder what Windows looks at to deterimine which partions are primary or not. If I knew that, perhaps there's some way to boot into my Linux system, edit some file to make it appear that the other partitions are extended even when they arent, reboot into the Windows installation, do the install, reboot into a live linux disc of some variety and use it to go change that file back, reboot and edit the boot.ini file for windows, reboot and test the installations - hoping it all worked...  right?

In a nutshell, what I'm wondering is if there's a way to make partition appear to be extended when they really aren't (avoiding actually doing any formatting - which I could not do). If I could do that I think I could hack it out somehow.

Any thoughts?

---

### Post by arpanaut on 2012-01-03
Got a question, what are the specs of your rig?
If you have a decent amount of Ram you might be able to set up a VM and run windows there.

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by ClientAlive on 2012-01-03
> **arpanaut said:**
> Got a question, what are the specs of your rig?
If you have a decent amount of Ram you might be able to set up a VM and run windows there.

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)



It started as an hp pavilion a1253w media center, now with a couple extras/ upgrades. The list goes something like this:

~ General specs:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00610113&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00610113&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604)

~  A8AE-LE (AmberineM)

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604)

~ Added: 2 X 1 Gb PC 3200 + the original 2 X 256 Mb of the same for a whopping 2.5 Gb random access memory  :D

~ The original Maxtor 100 Gb hard drive + 2 X Western Digital @ 80 Gb ea
~ The card reader it had in it
~ Some used cd/ dvd multi drive w/ lightscribe that I bought from the used computer shop a month ago for $12.00
~ Original Athlon 3400+

And that's pretty much it. No expansion cards (using the onboard graphics and whatnot)

Periferals are just old stuff someone gave me: big ol' crt monitor, ps2 keyboard and mouse - real basic system.

---

### Post by Matt 6:27 on 2012-01-03
I'm certainly no expert on this, but I dual-booted back in the 5.10 and 6.04 Dapper days.  I seem to recall having to load Win first due to some MBR issue, which would be a problem for you in this case and you probably already know this.

Have you considered loading XP using VirtualBox?  I've done this quite successfully inside Lucid, and it's actually better for me than a dual-boot system as I can run both OS's simultaneously and go back 'n forth b/t them on the fly.  I support folks using Win XP all the time and never have to log out of linux to do so.  Just a thought.

---

### Post by LinuxFan999 on 2012-01-03
> **ClientAlive said:**
> It started as an hp pavilion a1253w media center, now with a couple extras/ upgrades. The list goes something like this:

~ General specs:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00610113&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00610113&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604)

~  A8AE-LE (AmberineM)

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00496280&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=1843604)

~ Added: 2 X 1 Gb PC 3200 + the original 2 X 256 Mb of the same for a whopping 2.5 Gb random access memory  :D

~ The original Maxtor 100 Gb hard drive + 2 X Western Digital @ 80 Gb ea
~ The card reader it had in it
~ Some used cd/ dvd multi drive w/ lightscribe that I bought from the used computer shop a month ago for $12.00
~ Original Athlon 3400+

And that's pretty much it. No expansion cards (using the onboard graphics and whatnot)

Periferals are just old stuff someone gave me: big ol' crt monitor, ps2 keyboard and mouse - real basic system.

Windows XP would run very well in a virtual machine, even with your computer's specifications. You would need to only give it 512 Megabytes of RAM and a 10 Gigabyte virtual disk.

---

### Post by ClientAlive on 2012-01-03
I've use Virtual Box before and I like it. My only concern is that I may need to run something called Lock Down Browser for one of my classes. Lock Down Browser will not run in a virtual machine (I tried it before). It knows you're trying to run it in a vm and pukes up an error message when you try to run it. Some of my classes make me run that to takes tests through - since I take online classes.

I wish I could figure out how windows recognizes the partiions and partition types and try to hack it in there where I want it - it's a long shot but I doin't know how else to approach it.

---

### Post by arpanaut on 2012-01-03
Sure sounds like a viable option to get xp up and running on your rig.
The big plus is that you can windows up and running without jeopardizing your current set up.

Your specs seem more than adequate for general needs.
If I may ask, what are you going to be doing on the xp install?

Edit, just saw your latest post, that does put up a roadblock.
Negotiate with your professor?  But with the fear and distrust of Linux in the windows world,
that might not work.

---

### Post by ClientAlive on 2012-01-04
> **arpanaut said:**
> Sure sounds like a viable option to get xp up and running on your rig.
The big plus is that you can windows up and running without jeopardizing your current set up.

Your specs seem more than adequate for general needs.
If I may ask, what are you going to be doing on the xp install?

Edit, just saw your latest post, that does put up a roadblock.
Negotiate with your professor?  But with the fear and distrust of Linux in the windows world,
that might not work.


Errr... I'm not sure "negotiating" would go over so well, given the context. (The purpose of Lockdown Browser is to prevent cheating on tests - as if). They'd probably think you intend to cheat and that's why you're asking. Problem is Lockdown Browser is only avail for Windows or Mac - sux. Hopefully none of my classes will require it this semester, don't really know yet. Had to have it last semester and it really made things tough.

---

### Post by wildmanne39 on 2012-01-04
Hi, I did not read this whole thread word for word but I have a link that tells you how to install windows after linux and if that is not enough I would ask one of masters like oldfred.
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
This is a little old but should work, and I guess cloning your partition of linux is not possible?
Thanks

---

### Post by ClientAlive on 2012-01-05
> **wildmanne39 said:**
> Hi, I did not read this whole thread word for word but I have a link that tells you how to install windows after linux and if that is not enough I would ask one of masters like oldfred.
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
This is a little old but should work, and I guess cloning your partition of linux is not possible?
Thanks


I haven't had a chance to read that article completely but I'm going right back to it as soon as I type this. I had an interesting thought occur just now and wanted to get it down before I forget it.

The question, "what if I could make that one partition 'appear' to be a hard drive?" popped into my head. Then, this command popped into my head...

```

mknod

```

I wonder if I could somehow use mknod (and possibly some other thing come into play) to take that partition and make it 'as though' it were a block device of it's own. Then I could edit whatever boot files or whatever else to make it all fit together and work; and, ultimately, at the end of it all, go in and manually change that back to being just a partion (like it was at the start).

What about that as a possible solution?

As far as cloning my linux install, I'm not sure what you're getting at. For the purpose of having a backup before making drastic changes? For the purpose of manuiplation in order to reach my goal?

At any rate, I would need to find a way to do it that does not require the same amount of storage space as the partitions themselves. I've only exper clonezilla before and it requires the same amt of space as the partion for backup. I don't happen to have that much space avial to back up to. I think I do need to find a way to do a clone before I make any changes though --just in case  :)
----------------------

Edit:

Or another odd thought...  What if I intalled it to a .vdi (virtual machine disk/ virtual disk) just to isolate the installation off of the cd then take the whole stuff and copy/ paste it to that particular partition on that particular drive. Then go manually edit the boot.ini file to make it boot. Could that work?

---

### Post by Ms. Daisy on 2012-01-05
It seems like you're anxious to hack this, so here's a thought.  Why don't you create an iso of your Ubuntu installation?  That would preserve the customization that you don't want to lose.  I haven't tried it but I'm sure you can find some links to tutorials. I believe it involves compiling so it's far beyond my capabilities.
 
I know it's possible to install Windows after Ubuntu.  People in this forum have claimed it's not terribly difficult although I haven't tried it myself.

---

### Post by I_can_see_the_light on 2012-01-05
> **wildmanne39 said:**
> Hi, I did not read this whole thread word for word but I have a link that tells you how to install windows after linux and if that is not enough I would ask one of masters like oldfred.
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
This is a little old but should work, and I guess cloning your partition of linux is not possible?
Thanks

I don't think that link is going to help - it explains how to backup and restore GRUB legacy. 

For a backup of MBR (bootloader + partition table) I recommend reading this: [showthread.php?t=1459277]("http://ubuntuforums.org/showthread.php?t=1459277")
Post [no. 9]("http://ubuntuforums.org/showpost.php?p=10137166&postcount=9") from [Herman]("http://ubuntuforums.org/member.php?u=31861") also explains something about 'Disk Identifiers' which Windows uses to sense if something has been tampered with.

---

### Post by oldfred on 2012-01-05
I do not know RAID nor LVM. But I know you cannot use the regular tools to edit those partitions. But if your sda4 is outside the RAID it may work. Much better to have XP in a primary but I have seen where you can make XP work in a logical. XP will not see anything other than the NTFS partition, and will overwrite the MBR. But does RAID even use the MBR to boot?

Just for my own curiosity and documentation of your system which would be good to have before starting:

New testing version of bootscript May still be called version 60.:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```Current version:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by ClientAlive on 2012-01-05
Below is some system info that I hope may be useful. Basically, I have that Linux system how I want it (where I want it on the disks and such) and don't want to change that (resize or anything like that). It's just that I happen to have that sliver of space (enough for windows and the light use I'll be making of it). If I can't find a way to dump windows in there where that space is I'll have to find another alternative (maybe try to resurrect a differnt machine or something). I'm prepared to get radical on it's...  :popcorn:  (and like it too!  :) ).

That left over space is outside of raid and lvm (outside of everything and by itself) and I think it's primary (I'll have to double check on that). Sorry about the way the formatting for the fstab file looks - I keep trying to fix it and nothing seems to work.

You'll notice this info is from about a month ago. THe system has not changed since that time. In fact, that was the last time I fired it up since yesterday and I didn't make any changes yesterday. It's just a base system now wich I hope to build on.

--------------

**md0 is /boot (RAID 1); md1 is / (RAID 1); md2 is swap (also RAID 1); and md2 (RAID 5) is where my logical volumes reside (using lvm2).**

------------


**=> Output of mdadm --query --examine:**

```

/sbin/mdadm --query --examine /dev/md1
mdadm: No md superblock detected on /dev/md1.

```



**=> Output of mdadm --query --detail:**

```


/sbin/mdadm --query --detail /dev/md1
/dev/md1:
        Version : 0.90
  Creation Time : Mon Nov  7 23:38:41 2011
     Raid Level : raid1
     Array Size : 4194240 (4.00 GiB 4.29 GB)
  Used Dev Size : 4194240 (4.00 GiB 4.29 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon Nov 28 18:44:27 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

           UUID : e846c432:ea00aa1b:cb201669:f728008a
         Events : 0.18

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5
       2       8       37        2      active sync   /dev/sdc5


```

**But when I created the nodes for the raid devices I thought I chose minor number 9**



**=> Some more info on devices:**

```


ls -al /dev | grep md
drwxr-xr-x  2 root root        60 Nov 28 18:43 .mdadm
drwxr-xr-x  2 root root        80 Nov 28 18:43 md
brw-rw----  1 root disk    9,   0 Nov 28 18:43 md0
brw-rw----  1 root disk    9,   1 Nov 28 18:43 md1
brw-rw----  1 root disk    9,   2 Nov 28 18:43 md2
brw-rw----  1 root disk    9,   3 Nov 28 18:43 md3
lrwxrwxrwx  1 root root         3 Nov 28 18:43 root -> md1


```

=========================================================================


**/*System Information*/**


**=> File: /var/log/rc.log:**

```


rc shutdown logging started at Thu Nov 24 06:24:13 2011

 * Stopping local
 [ ok ]
 * Stopping vixie-cron ...
 [ ok ]
 * Saving random seed ...
 [ ok ]
 * Deactivating swap devices ...
 [ ok ]
 * Stopping sshd ...
 [ ok ]
 * Unmounting network filesystems ...
 [ ok ]
 * Stopping syslog-ng ...
 [ ok ]
 * Bringing down interface eth0
 *   Stopping dhcpcd on eth0 ...
 [ ok ]
 *   Removing addresses
* Bringing down interface lo
 *   Removing addresses
 * Unmounting loop devices
 * Unmounting filesystems
 *   Unmounting /var/tmp ...
 [ ok ]
 *   Unmounting /var ...
 [ ok ]
 *   Unmounting /tmp ...
 [ ok ]
 *   Unmounting /opt ...
 [ ok ]
 *   Unmounting /home ...
 [ ok ]
 *   Unmounting /usr ...
 [ ok ]
 * Shutting down the Logical Volume Manager
 *   Shutting Down logical volumes  ...
 [ ok ]
 *   Shutting Down volume groups  ...
  0 logical volume(s) in volume group "sysgrp" now active
[ ok ]
 * Finished Shutting down the Logical Volume Manager
 * Shutting down RAID devices (mdadm) ...
mdadm: stopped /dev/md3
mdadm: stopped /dev/md2
mdadm: stopped /dev/md0
mdadm: failed to stop array /dev/md1: Device or resource busy
Perhaps a running process, mounted filesystem or active volume group?
 [ !! ]
 * ERROR: mdraid failed to stop
 * Stopping udevd ...
 [ ok ]

rc shutdown logging stopped at Thu Nov 24 06:24:17 2011


rc boot logging started at Mon Nov 28 00:47:43 2011

 * Setting system clock using the hardware clock [Local Time] ...
 [ ok ]
 * Autoloaded 0 module(s)
 * Starting up RAID devices ...

 [ !! ]
 * Setting up the Logical Volume Manager ...
 [ ok ]
 * Checking local filesystems  ...
/dev/md1: clean, 1690/262144 files, 77015/1048560 blocks
/dev/md0: clean, 33/25584 files, 10229/102336 blocks
/dev/mapper/sysgrp-usr: clean, 225130/524288 files, 576351/2097152 blocks
/dev/mapper/sysgrp-portage: clean, 149008/200704 files, 353962/2097152 blocks
/dev/mapper/sysgrp-distfiles: clean, 41/4096 files, 25578/1048576 blocks
/dev/mapper/sysgrp-home: clean, 18/6742016 files, 471210/26959872 blocks
/dev/mapper/sysgrp-opt: clean, 12/262144 files, 51311/1048576 blocks
/dev/mapper/sysgrp-tmp: clean, 13/393216 files, 27760/1572864 blocks
/dev/mapper/sysgrp-var: clean, 4175/393216 files, 68563/1572864 blocks
/dev/mapper/sysgrp-vtmp: clean, 14/262144 files, 18512/1048576 blocks
 [ ok ]
 * Remounting root filesystem read/write ...
 [ ok ]
 * Updating /etc/mtab ...
 [ ok ]
 * Mounting local filesystems ...
 [ ok ]
 * Configuring kernel parameters ...
 [ ok ]
 * Creating user login records ...
 [ ok ]
 * Cleaning /var/run ...
 [ ok ]
 * Wiping /tmp directory ...
 [ ok ]
 * Setting hostname to shine ...
 [ ok ]
 * Setting terminal encoding [UTF-8] ...
 [ ok ]
 * Setting keyboard mode [UTF-8] ...
[ ok ]
 * Loading key mappings [us] ...
 [ ok ]
 * Bringing up interface lo
 *   127.0.0.1/8 ...
 [ ok ]
 *   Adding routes
 *     127.0.0.0/8 via 127.0.0.1 ...
 [ ok ]
 * Mounting USB device filesystem [usbfs] ...
 [ ok ]
 * Mounting misc binary format filesystem ...
 [ ok ]
 * Activating swap devices ...
 [ ok ]
 * Initializing random number generator ...
 [ ok ]

rc boot logging stopped at Mon Nov 28 00:47:51 2011


rc default logging started at Mon Nov 28 00:47:51 2011

 * Bringing up interface eth0
 *   dhcp ...
 *     Running dhcpcd ...
dhcpcd[1936]: version 5.2.12 starting
dhcpcd[1936]: eth0: rebinding lease of 192.168.0.11
dhcpcd[1936]: eth0: acknowledged 192.168.0.11 from 192.168.0.1
dhcpcd[1936]: eth0: checking for 192.168.0.11
dhcpcd[1936]: eth0: leased 192.168.0.11 for 604800 seconds
dhcpcd[1936]: forked to background, child pid 1968
 [ ok ]
 *     received address 192.168.0.11/24
 [ ok ]
 * Mounting network filesystems ...
 [ ok ]
 * Starting syslog-ng ...
 [ ok ]
 * Starting sshd ...
 [ ok ]
 * Doing udev cleanups
 * Starting vixie-cron ...
 [ ok ]
 * Starting local
 [ ok ]

rc default logging stopped at Mon Nov 28 00:47:57 2011


```



**=> Output of cat /proc/mdstat:**

```


Personalities : [raid1] [raid6] [raid5] [raid4] 
md3 : active raid5 sdc3[2] sdb3[1] sda3[0]
      143510528 blocks level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
md1 : active raid1 sdc5[2] sdb5[1] sda5[0]
      4194240 blocks [3/3] [UUU]
      
md2 : active raid1 sdc6[2] sdb6[1] sda6[0]
      2095040 blocks [3/3] [UUU]
      
md0 : active raid1 sdc1[2] sdb1[1] sda1[0]
      102336 blocks [3/3] [UUU]
      
unused devices: <none>


```



**=> Output of pvscan:**

```


 PV /dev/md3   VG sysgrp   lvm2 [136.86 GiB / 16.00 MiB free]
  Total: 1 [136.86 GiB] / in use: 1 [136.86 GiB] / in no VG: 0 [0   ]

```



**=> Output pf vgscan:**

```


 Reading all physical volumes.  This may take a while...
  Found volume group "sysgrp" using metadata type lvm2


```



**=> Output of lvscan:**

```


 ACTIVE            '/dev/sysgrp/usr' [8.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/portage' [2.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/distfiles' [4.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/opt' [4.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/var' [6.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/vtmp' [4.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/tmp' [6.00 GiB] inherit
  ACTIVE            '/dev/sysgrp/home' [102.84 GiB] inherit


```



**=> File: /etc/fstab:**

```


# <fs>       <mountpoint>    <type>                 <opts>        <dump/pass>

# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
/dev/md0        /boot        ext2                    noauto,noatime   1 2
/dev/md1        /            ext3                    noatime          0 1
/dev/md2        swap         swap                    sw,pri=1         0 0
/dev/cdrom      /mnt/cdrom   auto                    noauto,ro        0 0
/dev/sysgrp/usr    /usr      ext3                    noatime          1 2
/dev/sysgrp/portage   /usr/portage    ext2           noatime          1 2
/dev/sysgrp/distfiles   /usr/portage/distfiles   ext2   noatime       1 2
/dev/sysgrp/home   /home     ext3                    noatime          1 2
/dev/sysgrp/opt    /opt      ext3                    noatime          1 2
/dev/sysgrp/tmp    /tmp      ext2                    noatime          1 2
/dev/sysgrp/var    /var      ext3                    noatime          1 2
/dev/sysgrp/vtmp   /var/tmp           ext2           noatime          1 2

```

---

### Post by ClientAlive on 2012-01-05
**Forgot to offer up my fdisk output:**


```


 ~ # fdisk /dev/sda

Command (m for help): u
Changing display/entry units to cylinders (DEPRECATED!)

Command (m for help): p

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00037ab1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400   fd  Linux raid autodetect
/dev/sda2              13         797     6291456    5  Extended
/dev/sda3             797        9730    71755776   fd  Linux raid autodetect
/dev/sda4            9730       12162    19534848   83  Linux
/dev/sda5              14         536     4194304   fd  Linux raid autodetect
/dev/sda6             536         797     2095104   fd  Linux raid autodetect

Command (m for help): 



 ~ # fdisk /dev/sdb

Command (m for help): u
Changing display/entry units to cylinders (DEPRECATED!)

Command (m for help): p

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00072fd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400   fd  Linux raid autodetect
/dev/sdb2              13         797     6291456    5  Extended
/dev/sdb3             797        9730    71755776   fd  Linux raid autodetect
/dev/sdb5              14         536     4194304   fd  Linux raid autodetect
/dev/sdb6             536         797     2095104   fd  Linux raid autodetect

Command (m for help): 



 ~ # fdisk /dev/sdc

Command (m for help): u
Changing display/entry units to cylinders (DEPRECATED!)

Command (m for help): p

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005fe8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      102400   fd  Linux raid autodetect
/dev/sdc2              13         797     6291456    5  Extended
/dev/sdc3             797        9730    71755776   fd  Linux raid autodetect
/dev/sdc5              14         536     4194304   fd  Linux raid autodetect
/dev/sdc6             536         797     2095104   fd  Linux raid autodetect

Command (m for help): 



```

---

### Post by oldfred on 2012-01-05
I know with RAID you do not use gparted, but if the sda4 will be outside the RAID can you make it a NTFS partiton with the boot flag? Then XP should install just to that partition. It will overwrite MBR and may rewrite partition table, so have backups of just boot & full first sector with partition table.

I normally do not suggest dd as it is easy to reinstall grub, grub2 or Windows boot loader, but in your case it may be worthwhile to have this backed up.

Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1
Zero out MBR only of sda Use 440 if windows as serial number is between 440 & 446.
dd if=/dev/zero of=/dev/sda bs=446 count=1
Erase - Make double sure you have correct drive & partition
sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C

---

### Post by ClientAlive on 2012-01-05
> **oldfred said:**
> I know with RAID you do not use gparted, but if the sda4 will be outside the RAID can you make it a NTFS partiton with the boot flag? Then XP should install just to that partition. It will overwrite MBR and may rewrite partition table, so have backups of just boot & full first sector with partition table.

I normally do not suggest dd as it is easy to reinstall grub, grub2 or Windows boot loader, but in your case it may be worthwhile to have this backed up.

Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1
Zero out MBR only of sda Use 440 if windows as serial number is between 440 & 446.
dd if=/dev/zero of=/dev/sda bs=446 count=1
Erase - Make double sure you have correct drive & partition
sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C


Thanks oldfred. That makes good sense and is simple. I'm gonna spend this afternoon/ evening reading up on a couple more things and tackle this in the morning.

I was wondering about something though. If I have the kind of raid system set up that I do; then, if I were to bugger up somthing on the linux system, the machine should still boot and I should be able to rebuild the raid (the whole shebang I mean) by running the appropriate commands to do so --right? Is that right? Regardless, I'll still get my backups before making any changes and a clone of the entire system. I was just wondering if I understand that raid thing right.


Thanks
-------------------

Edit:

Oh, just that I found this link that's so cool I felt compelled to share it. That's all.

[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)

Excellent, ellegant, and concise explanation of a lot of pretty critical things to do with all this.
---------------------

Edit:

So, in the end, does both sda1 and sda4 need to be flagged bootable?

---

### Post by oldfred on 2012-01-05
No. But again I am not exactly sure how RAID boots.

If fact only one primary partition can (have seen exceptions) be flagged as bootable or the active partition in Windows. Lilo also uses boot flag but will also boot from a logical partition.

You can and usually have one boot flag per drive.

Grub does not use boot flag, a few BIOS need a boot flag or they will not let you start to boot (seems to assume Windows) and Windows has to have a boot flag (active partition) on a primary NTFS partition.

Note that dd is very dangerous as if you reverse command it will do exactly what you have told it. It is also know as Data Destroyer as we do may typos and then huge problems.

If just reinstalling a boot loader this is much safer:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
or either of these:
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by Alphamonkey on 2012-01-05
Well I know this wont be much help to you but a few years ago before I new anything about linux really I installed fedora 9 on my computer and wiped windows completely. I came to realize that some of my programs didn't work and I was unaware of wine and VM at the time so I installed windows on a left over partition. Only problem is I don't remember exactly how I set up the partitioning scheme or anything. Couldn't have been too difficult though because as I said at the time I was barely starting to play with linux. I am sure there is a way to do it though.

---

### Post by ClientAlive on 2012-01-06
> **Alphamonkey said:**
> Well I know this wont be much help to you but a few years ago before I new anything about linux really I installed fedora 9 on my computer and wiped windows completely. I came to realize that some of my programs didn't work and I was unaware of wine and VM at the time so I installed windows on a left over partition. Only problem is I don't remember exactly how I set up the partitioning scheme or anything. Couldn't have been too difficult though because as I said at the time I was barely starting to play with linux. I am sure there is a way to do it though.


Omigosh!  Well if you recall, please do tell. Sounds interesting.

PS: I'll let y'all know how it goes  :P

---

