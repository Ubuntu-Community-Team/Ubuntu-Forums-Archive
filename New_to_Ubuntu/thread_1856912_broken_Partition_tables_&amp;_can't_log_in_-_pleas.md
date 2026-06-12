---
title: "broken Partition tables &amp; can't log in - please help"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by Logan Fife on 2011-10-09
Hi, any help is brilliant, but i should say i know very little about all of this. probably shouldn't have started in the first place...
:oops:
Background:

I had ubuntu 10.04 (lucid lynx?) installed from a live CD on my laptop, all set up and working fine.

then, i wanted to put xp on it, so i did this:

1. used the linux liveCD to start make a new partition on the hard drive, and aborted the install after it had made the partition.

2. used an xp install disc to attempt to install on the new partition, but got
"there is not a compatable section on this drive" I deleted and created that partition a few times using the xp install disk with no change.

! now windows has over written the bootsector? so i used the linux liveCD to re-install grub, and thats ok.

grub there are still versions of linux on there, and fdisk shows two partitions ending on the same location. a Gparted liveCD says that the whole disk is unallocated.
---------------------------------
the most immediate problem:
ubuntu wont let me log in to either version, saying " the configuration defaults for gnome power management have not been installed properly" or something, which i believe is a space issue as per [http://ubuntuforums.org/showthread.php?t=1813119](http://ubuntuforums.org/showthread.php?t=1813119) (when i made the partition, i cut the current one down, probably to the limit of the stuff on there). I tried using the liveCD to remove some files and make some space, but that didn't work, and the HDD properties look confusing ( see attatched screenshot)

from the recovery console:
fdisk -lu
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 7814-160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e8a48


Device       Boot      Start         End       Blocks    Id     System
/dev/sda1      *        2048    57462775     28730364    83     Linux
/dev/sda2           57462782    78139391     10338305     5     Extended
/dev/sda3           75163648    78139391      1487872    82     Linux swap / Solaris
/dev/sda5           57462845    74300624      8418890     e     W95 FAT16 (LBA)
/dev/sda6           74307584    75151359       421888    82     Linux swap / Solaris

```and df -h

```

Filesystem     Size   Used   Avail     Use%   Mounted on
/dev/sda1      27G     27G       0     100%   /
none           245M   264K    244M       1%   /dev
none           249M      0    249M       0%   /dev/shm
none           249M    28K    249M       1%   /var/run
none           249M      0    249M       0%   /var/lock
none           249M      0    249M       0%   /lib/init/rw

```Thanks very much

---

### Post by coffeecat on 2011-10-09
> **Logan Fife said:**
> fdisk shows two partitions ending on the same location. a Gparted liveCD says that the whole disk is unallocated.

Yes, that's the work of the Windows XP installer. It's tried to reconfigure a logical partition which spanned sectors 75163648 to 78139391 as a primary partition. Now the partition table says that you have a primary partition inside your extended (sda2) partition, which is an impossibility, and Gparted has thrown its figurative hands up in horror. :wink:

Windows needs to be in a primary partition. It looks as though you presented it with an impossible situation and the corrupted partition table is the result. Not your fault - the XP installer is known to do this. 

To be quite honest, I would start over afresh in your situation if you are looking to create a Windows/Ubuntu dual-boot. You have two swap partitions, a bad partition table to repair and nowhere to put Windows at the moment. Do you want any help with that?

---

### Post by Logan Fife on 2011-10-09
yes please, thanks CoffeeCat, well i just want to have a working machine again! dual booting if possible. I don't really know what a swap partition or a primary partition is.

Is there anyway to save my configuration for ubuntu? i spent a lot of time getting programs and wifi drivers etc set up, and i'm on pay per data internet.

---

### Post by coffeecat on 2011-10-09
Briefly, the mbr partition table scheme allows you a maximum of four primary partitions. To get around that limitation, you can have one extended partition (which is simply a specialised type of primary) whose sole function is to act as a container for logical partitions. Primary (and extended partitions) are numbered 1-4 - logicals 5 and upwards. If you look at your fdisk output, you'll see that sda5 and sda6 (logicals by definition) are inside the extended, which is correct, but that sda3 (#3 = primary) is also inside the extended.

You have two options.

1 - Use a live CD to backup and copy off all your personal files. Then completely reformat the drive, install XP first and then Ubuntu. You will lose all your configurations and have to start over.

2 - (Trickier):

[list=a]
[*]Run the fixparts app from the live CD (I can give you a link) to repair the partition table.
[*]See if you can repair your Ubuntu. That may or may not be possible depending on what has gone wrong.
[*]Edit /etc/fstab so that it is not referencing the swap partitions.
[*]Delete sda2 to sda6 partitions.
[*]Create a primary partition (new sda2) for Windows and install Windows.
[*]Re-install grub which Windows will have overwritten.
[*]Create a swap partition.
[*]Edit /etc/fstab again so that the new swap is mounted on bootup.
[*]Have a lie-down! :wink:
[/list]

That's all without the details. Which do you want to do? :)

---

### Post by Logan Fife on 2011-10-09
wow that looks complicated.
if your kind enough to walk me through the second one that would be great:D
I am guessing, but i think the problem with ubuntu is connected to the partition table, it thinks the drive is full to capacity. if its not that straight forward, I will call it quits and take the easy option. if i go into the recovery console, and then do "resume normal boot" it gives me a command line ubuntu which remembers the commands i was typing before all this happenned.

so, I've backed up personal files, and booted into "try ubuntu 10.04.2 LTS" from the live CD. is fixparts already on the CD or do i need to get it?
(google fixparts top hit is this thread)

thanks

---

### Post by coffeecat on 2011-10-09
The best thing is to see if you can repair the partition table with fixparts and then try to see what is wrong with your Ubuntu installation. If you find you can't repair Ubuntu, then you'll have to go the simpler start over again road.

Have a look here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Boot up an Ubuntu live CD and download the installer from here:

[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/)

You'll need either the i386.deb or amd64.deb package depending on whether you are running 32 or 64 bit. Simply double-click on it to install it and then run it from the terminal with:

```
sudo fixparts /dev/sda
```

Scroll down in the first link and you'll see that the directions are fairly straightforward. Once you've repaired the partition table, try to boot into Ubuntu on your hard drive and post any errors you get.

---

### Post by Logan Fife on 2011-10-09
hmm, so i loaded fixparts and ran it, though only the display and sort commands, which the tutorial says should auto adjust the table into a valid setup? I still cant log in

the output was 
```

ubuntu@ubuntu:~$ sudo fixparts /dev/sda

FixParts 0.7.1
Loading MBR data from /dev/sda

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!
** Extended partitions are not displayed, but will be generated as required.

Disk size is 78140160 sectors (37.3 GiB)
MBR disk identifier: 0x000E8A48
MBR 
partitions:
                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
1      *           2048     57462775   primary     Y        Y      0x83
3              75163648     78139391   primary     Y        Y      0x82
5              57462845     74300624   logical     Y        Y      0x0E
6              74307584     75151359   logical     Y        Y      0x82

MBR command (? for help): s

MBR command (? for help): p

Disk size is 78140160 sectors (37.3 GiB)
MBR disk identifier: 0x000E8A48
MBR 
partitions:
                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
1      *           2048     57462775   primary     Y        Y      0x83
2              57462845     74300624   logical     Y        Y      0x0E
3              74307584     75151359   logical     Y        Y      0x82
4              75163648     78139391   primary     Y        Y      0x82

MBR command (? for help): w
Final checks complete. About to write MBR data. 
THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
Done writing data!
Warning: The kernel is still using the old partition table.
The new table will be used at the next reboot.


```so i rebooted and fdisk -lu says

```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e8a48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    57462775    28730364   83  Linux
/dev/sda2        57462844    75151359     8844258    f  W95 Ext'd (LBA)
/dev/sda4        75163648    78139391     1487872   82  Linux swap / Solaris
/dev/sda5        57462845    74300624     8418890    e  W95 FAT16 (LBA)
/dev/sda6        74307584    75151359      421888   82  Linux swap / Solaris

note: also says partitions 1 and 4 don't end on cylinder boundary

```which looks ok, if sda5 and 6 are allowed to be inside 2 like that?
but df -h is still showing the same thing as before, with sda1 (27G) used 100%

did i use fixparts properly? what can i do now?
Thanks very much

---

### Post by coffeecat on 2011-10-09
> **Logan Fife said:**
> 
note: also says partitions 1 and 4 don't end on cylinder boundary
[/CODE]which looks ok, if sda5 and 6 are allowed to be inside 2 like that?
but df -h is still showing the same thing as before, with sda1 (27G) used 100%

did i use fixparts properly? what can i do now?
Thanks very much

Yup, that's fine. Fixparts has converted the errant partition into a proper primary outside of the extended. Yes sda5 and sda6 are allowed to be inside sda2; in fact they have to be. Remember what I explained about logical partitions being contained within an extended partition. 

Don't worry about cylinder boundaries. No one has since about the age of the dinosaurs!

OK. Next thing is to release some space in that 100% full sda1 Ubuntu partition. There is a thread with a comprehensive guide to this which I can't find at the moment. I'll post back as soon as I've found it.

---

### Post by shashalow on 2011-10-09
Hi there,
I sort of have similar problem with Ubuntu 11.04. I am running it on hp compaq, intel core duo, 3 GB with 32 bit OS along side Windows 7. initially I have the Windows then I install Ubuntu. it was not working initially fine because I can't install bison and flex. it kept telling me that a file
          ..archive\ubuntu.com\binary-64.log cant be parsed or opened
so try to uninstall ubunt11.04 and install ubuntu 10.08 but I don't know.
I deleted the mbr files and now ubuntu is not starting at all and is not uninstalled...
 
please help....

---

### Post by coffeecat on 2011-10-09
@Logan Fife, I've found the thread, but it has more than you need. Here it is for your bookmarks anyway:

ubuntuforums.org/showthread.php?t=1122670

How comfortable are you exploring the Ubuntu installation filesystem from the live CD? That's probably the quickest and easiest way to free up some space. What I would do is to boot up the live CD, mount the sda1 Ubuntu partition and delete all the *.deb files from /var/cache/apt/archives. Then I would look to see if there is anything in root's trash in /root/.local/share/Trash/ and if there is, delete it. For both of those you would need to use the terminal or a gksudo nautilus file browser. It would free enough room, hopefully, to get you booting into Ubuntu from where you could see what else is using so much room.

If you are not comfortable with that, or if it makes no sense (!), post back and we'll try another strategy.

By the way, when you were using Ubuntu from the hard drive, did you ever delete any files using a 'gksudo nautilus' root nautilus file browser?

---

### Post by Elfy on 2011-10-09
> **shashalow said:**
> Hi there,
I sort of have similar problem with Ubuntu 11.04. I am running it on hp compaq, intel core duo, 3 GB with 32 bit OS along side Windows 7. initially I have the Windows then I install Ubuntu. it was not working initially fine because I can't install bison and flex. it kept telling me that a file
          ..archive\ubuntu.com\binary-64.log cant be parsed or opened
so try to uninstall ubunt11.04 and install ubuntu 10.08 but I don't know.
I deleted the mbr files and now ubuntu is not starting at all and is not uninstalled...
 
please help....

Please start your own thread - hijacking a thread like this will lead to tears, your issue might appear the same - but it needs it's own thread.

[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

---

### Post by Logan Fife on 2011-10-09
thanks CoffeeCat, it sounds so easy but uh...

i typed "gksudo nautilus" which brought up a file browser, but the root folder is empty

/var/cache/apt/archives is also empty except for a file called lock and an empty folder called partial

now on the recovery mode available from grub, i can get into root/.local/share 
but the only thing in there is a directory called webkit
/var/cache/apt/archives is still the same contents (with ls -a)


I've deleted 5.5Gb of personal files, but dh -f is still claiming 100% usage on sda1
and i still can't log in:(

---

### Post by coffeecat on 2011-10-09
> **Logan Fife said:**
> i typed "gksudo nautilus" which brought up a file browser, but the root folder is empty

/var/cache/apt/archives is also empty except for a file called lock and an empty folder called partial

Is this from the live CD or were you able to boot into Ubuntu on the hard drive? If from the live CD, you are probably looking at the live CD's own filesystem, not that in your hard drive Ubuntu root partition.

Whichever, try booting into recovery mode and dropping to a root shell. Now run:

```
apt-get clean
```

Reboot and see if that helps.

---

### Post by Logan Fife on 2011-10-09
Hi CoffeeCat

I was on the liveCD, but looking at "29Gb file system" which is the hard drive (actually 40 Gb, why is it called 29?)

I also checked it in the root shell, with the same results.

apt-get clean didn't work. 
how much space do I need? why didn't the 5.5 Gb of files i have cleared from the home directory work?

thanks for your patience

---

### Post by coffeecat on 2011-10-09
> **Logan Fife said:**
> I was on the liveCD, but looking at "29Gb file system" which is the hard drive (actually 40 Gb, why is it called 29?)

No - the filesystem you were looking at is the sda1 partition, not the whole hard drive. Each partition has its own flesystem and the live CD has its own filesystem.

> **Logan Fife said:**
> 
how much space do I need? why didn't the 5.5 Gb of files i have cleared from the home directory work?

5.5GB should be more than enough. I'm mystified why you are not able to clear any space. There should have been several hundred megabytes of downloaded and cached package files which would have been cleared with "apt-get clean". By the way, if you mean it didn't work because you got no feedback in the console that doesn't mean it didn't work. With most commands, if they run successfully you get nothing echoed to the terminal.

How exactly did you clear the 5.5GB of files from your home directory?

---

### Post by Logan Fife on 2011-10-09
oh ok thanks. that makes sense.

when i say it didn't work, i mean i still can't log in.

I deleted the 5.5Gb by clicking move to trash while browsing with nautilus on the liveCD boot. incedentally it never appeared in trash, but its definately not there now.

the good news is that Gparted will now recognise the drive, it says /dev/sda5 is "unknown" file system, but otherwise matches fdisk -lu output.
 it also says sda1 is full:(

is there some record somewhere of how much data is on the drive? it seems like its not being updated or something.

---

### Post by coffeecat on 2011-10-09
> **Logan Fife said:**
> I deleted the 5.5Gb by clicking move to trash while browsing with nautilus on the liveCD boot. incedentally it never appeared in trash, but its definately not there now.

That *might* be the problem. You need to hard delete, not move to trash. It could be that the deleted files are sitting in a trash folder created by the live CD somewhere in the sda1 filesystem. Also the UID of the "ubuntu" account in the live session is 999, different from the 1000 UID of your account in your hard drive installation. Normally, one needs a root nautilus to move and delete personal files when using a live CD.

Boot up a live CD. Mount your sda1 partition from the Places menu. Close the nautilus window that opens. Now open a root nautilus with:

```
gksu nautilus /media
```

It will open in the /media folder of the live session filesystem, **not** the /media folder of your hard drive partition. You will see the mount point for your sda1 partition there - its name will either be a long string of alphanumeric characters (the UUID) or the partition label if there is one. Open it. You are now in the filesystem of sda1. Pres ctrl-H. Do you see a hidden folder called .Trash-something? If so, delete it by using the shift-delete key combination. Now open the home folder and then your account folder. Find some more personal files to delete. Hard-delete them with shift-delete. If you have managed to delete more than a few hundred megabytes of files with shift-delete, your filesystem should now show less than 100%.

---

### Post by Logan Fife on 2011-10-11
Hi, Sorry I abandonned this on monday, it got too late and i fell asleep.

anyway, I'm back on it now, and fantastically it worked!
whats the difference between gksudo and gksu?

so I'm back in ubuntu with it all set up as before, Thank you.:D
I'm currently making some space, I think i've got about 10Gb so far, is that enough to do the xp thing?

finally, Grub still lists two installations, with different numbers, but both load what looks to be the same ubuntu. is this a problem?

Thanks again, I cant tell you how relieved i am to get ubuntu back

---

### Post by coffeecat on 2011-10-11
> **Logan Fife said:**
> whats the difference between gksudo and gksu?

There is a difference, but the way a default installation of Ubuntu is set up, they both do the same.

> **Logan Fife said:**
> so I'm back in ubuntu with it all set up as before, Thank you.:D
I'm currently making some space, I think i've got about 10Gb so far, is that enough to do the xp thing?

It's enough to run Ubuntu, which is the main thing.

What you will need to do now is:

[list=1]
[*] edit /etc/fstab so that you don't get an error on bootup when you've deleted the swap partition(s).
[*] delete all the partitions except sda1.
[*] Create a partition for Windows.
[*] Install Windows
[*] Repair grub
[*] Create a new swap partition and edit /etc/fstab again so that it is used.
[*] Regenerate the grub menu so that Windows is seen.[/list]

> **Logan Fife said:**
> finally, Grub still lists two installations, with different numbers, but both load what looks to be the same ubuntu. is this a problem?

Would that be something like 2.6.32-x and 2.6.32-y? If so, they are different versions of the kernel.

First step. In Ubuntu, run this terminal command and post the output:

```
cat /etc/fstab
```

Highlight the output with the mouse, then right-click -> copy, and then paste it into your post. Once you;ve posted that I'll give you notes on how to achieve the rest.

---

### Post by Logan Fife on 2011-10-11
yes thats right, 32-31-generic and 32-28-generic.

cat /ect/fstab gives:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f51d0238-d81d-4b46-82f4-77fde6979876 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e93226ef-842a-4cf0-bbaa-6a89b872b0db none            swap    sw              0       0

```

thanks again!

---

### Post by coffeecat on 2011-10-11
@Logan Fife, I'll post some notes in the morning. It will be better when I'm fresh as there's some detail to attend to.

---

### Post by coffeecat on 2011-10-12
As promised, the next few steps. Before you do anything, double-check that you have backed-up all your personal files. You are about to delete partitions and anything that involves editing the partition table has the potential for going wrong. The risk is small, but worst-case scenario is that you lose your Ubuntu installation. 

In Ubuntu, open /etc/fstab with:

```
gksudo gedit /etc/fstab
```

"Comment" this line:

```
UUID=e93226ef-842a-4cf0-bbaa-6a89b872b0db none            swap    sw              0       0
```

So that it looks like this:

```
#UUID=e93226ef-842a-4cf0-bbaa-6a89b872b0db none            swap    sw              0       0
```

Save and close. Now you need to reboot into the live CD. The partition deletion is better done in the live session. I'm assuming that you don't have anything stored on the sda5 FAT16 partition. We've not mentioned this before and I've assumed that it was some curious side-effect of trying to install WinXP. What I am about to suggest will delete it, so if there is anything important on it, or if it is needed for any reason, stop here and post back.

If you are OK to proceed, in the live session open Gparted. Right-click on each of the two swap partitions, sda4 and sda6 in turn, and choose "swapoff". Now mark these partitions for deletion in this order: sda4, sda6, sda5, sda2. Click on apply and you will end up with just your Ubuntu partition and unallocated space. Now create a new NTFS primary partition. This will be numbered sda2. Make it large enough to fill all the space except for some space for a new swap partition at the end. When you have created the new NTFS partition, go to Partition -> Manage Flags and set the boot flag on sda2. You don't need the boot flag for Ubuntu (which it has at the moment). The Windows installer will probably set the boot flag anyway, but you might as well do it now to be sure.

You could create the swap partition now, but I think it would be best the leave things as simple as possible for the Windows installer (!) which is known to do some very strange things at times. :)

Now install Windows to partition 2. This will temporarily prevent you from booting into Ubuntu. Once you have made sure you have a working Windows system, boot into the Ubuntu live CD again. Open Gparted and create a swap partition in the unallocated space that you have left. You can either make it a primary partition, or create an extended partition in the space first and make a logical swap partition. In your situation there will be no practical difference. Once you have created the swap partition, run this code:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That will re-install grub so that you can boot into Ubuntu. Now reboot into Ubuntu. Your grub menu will be the old one without Windows - don't worry, we will fix that. Open a terminal and:

```
sudo swapon -a
```

... to activate the new swap partition for this session. Now:

```
sudo update-grub
```

To regenerate the grub menu.

Now some tidying up. You need to edit /etc/fstab again to include the new swap partition. Post the output of:

```
sudo blkid
```

And I'll help you with that. Also, boot into both Ubuntu and Windows and post back if there are any problems. Until you've re-edited /etc/fstab it would be a good idea to run "sudo swapon -a" each time you boot into Ubuntu.

---

### Post by Logan Fife on 2011-10-14
Hey CoffeCat, how've you been?

I've followed the steps up you have laid out, and everything seems to be working fine.

there is some issue with windows, it kept asking me for a CD containing SP2 during install, though i thought it was supposed to be on the CD. then it gave me a couple of errors like
```
Sub-component COM+ raised an exception while processing the OC_COMPLETE_INSTALLATION setup message

```
and it won't let me switch from windows classic theme, unless i mess around with the services section.

anyway, unless that sounds like a serious problem, i'm not too worried, as i had the program i wanted to use going on it today and it was running fine.:D

Ubuntu is nice and shiney, and no (new) problems exist there.

blkid output is:
```
/dev/sda2: LABEL="windows" UUID="52067E394567E5FA" TYPE="ntfs" 
/dev/sda3: LABEL="swap" UUID="4349394b-03af-404c-a3d4-da780fefe7c7" TYPE="swap" 
/dev/sda1: UUID="f51d0238-d81d-4b46-82f4-77fde6979876" TYPE="ext4" 
```

Thanks. is there any difference between fat and ntfs? the xp disc tried to make a fat system the 1st time.

notes for anyone possibly following this in the future. Gparted didn't like doing everything at once, but was happy when i asked for one thing at a time.
also, XP setup doesn't refer to your partitions as sdax, but will display the label tag which you can assign in Gparted. just to make sure you don't install windows on the wrong partition.

---

### Post by coffeecat on 2011-10-14
OK - you're almost there. Just to pick up a few small points first.

> **Logan Fife said:**
> Thanks. is there any difference between fat and ntfs? the xp disc tried to make a fat system the 1st time.

Yes - FAT is a much older filesystem and was used for Microsoft OSs in the 80s and 90s. It's still used for things like SD cards and pendrives. It's non-journalled whereas NTFS is journalled. You can install XP to a FAT partition, but I wouldn't.

> **Logan Fife said:**
> XP setup doesn't refer to your partitions as sdax

No, the sdXY naming convention is a Linux one.

Anyway, to your /etc/fstab. The last two lines should look like this at the moment:

```
# swap was on /dev/sda5 during installation
#UUID=e93226ef-842a-4cf0-bbaa-6a89b872b0db none            swap    sw              0       0
```

You need to open /etc/fstab with:

```
gksudo gedit /etc/fstab
```

And then you need to change the UUID, and for tidiness it would be a good idea to edit the first of those two lines, although that doesn't affect the functionality of it. This is what I suggest - the modified UUID is necessary:

```
# swap is now on /dev/sda3
#UUID=4349394b-03af-404c-a3d4-da780fefe7c7 none            swap    sw              0       0
```

Save and exit. Next time you boot-up, the new swap partition will be mounted and you won't have to "swapon".

As far as this is concerned:

> **Logan Fife said:**
> it kept asking me for a CD containing SP2 during install,

Frankly, I haven't a clue. If that's a pre-SP2 install CD, it wouldn't know about SP2 so that's curious you are getting that message. It used to be that you could download the XP SP2 disc ISO from the Microsoft site and then run it within XP. Or you could simply apply all updates, which will take a very long time if it has to install SP2, because there's been an SP3 since. But tbh, I'm not sure so don't take my word on that. It's been a long time since I've used or installed XP for myself.  

Good luck!

---

### Post by Logan Fife on 2011-10-14
thanks CoffeeCat.
the XP cd was an iso file i downloaded from microsoft called 
"windows xp with service pack 2"
I could have chosen a different service pack, so you would have thought it would actually come with the service pack I chose. anyway, the programme I needed to run is running, so I'm happy.

anyway, just to be sure, did you mean

```
# swap is now on /dev/sda3
UUID=4349394b-03af-404c-a3d4-da780fefe7c7 none            swap    sw              0       0
```

without the #?

is swap the ubuntu equivalent of virtual memory? or is there more to it than that
Thanks

---

### Post by coffeecat on 2011-10-14
> **Logan Fife said:**
> 
anyway, just to be sure, did you mean

```
# swap is now on /dev/sda3
UUID=4349394b-03af-404c-a3d4-da780fefe7c7 none            swap    sw              0       0
```

without the #?

You're quite right. You found the deliberate error! :-\"

:wink: 

> **Logan Fife said:**
> is swap the ubuntu equivalent of virtual memory? 

Yes. Windows uses a swap file called pagefile.sys. You can set up a swap file in Linux, but a dedicated partition has certain advantages.

---

### Post by Logan Fife on 2011-10-14
excellent. thank you for your time effort and patience

I'm guessing that if I need to reinstall windows I will have to do the same procedure again

one final question...
... how do I mark the thread [solved]?

---

### Post by coffeecat on 2011-10-14
Thread tools near top of page. There's a drop-down and as OP you should be able to see "mark thread as solved".

If you have to re-install Windows I would hope that with 3 primary partitions, it wouldn't do anything odd. It gets confused when there are logical partitions (with an extended) and fewer than 3 primary partitions.

---

