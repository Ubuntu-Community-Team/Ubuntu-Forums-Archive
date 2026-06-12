---
title: "My Windows XP won't start after I installed Ubuntu!"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by pgtl10 on 2008-04-26
The Windows XP is shown on menu screen but when I try to load the OS, the computer just stalls. I only did a guided partition on my free space and only used 22% of my hard drive. Please help!!

---

### Post by pgtl10 on 2008-04-26
Anybody know what I should do?

---

### Post by chogoria on 2008-04-26
When you installed Ubuntu, (I'm assuming you used the Live CD) did you select to manually configure partitions? Could you please give some detail as to what you did around this stage to help us solve your problem.

---

### Post by JonUK76 on 2008-04-26
Do you get an error message? Anything about missing or corrupt .dll files?

Also might be helpful to help diagnose if you load Ubuntu, start the terminal (Applications, Accessories, Terminal) and run the following commands:

sudo fdisk -l
cat /boot/grub/menu.lst

And paste the output here

---

### Post by pgtl10 on 2008-04-26
I used a guided partition of my free space. Only 22% of my free space was used.

Here what was on the Terminal:

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0c4b2ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4321    34708401    7  HPFS/NTFS
/dev/sda2            4322       19741   123861150   83  Linux
/dev/sda3           19742       19929     1510110    5  Extended
/dev/sda5           19742       19929     1510078+  82  Linux swap / Solaris
peter@peter-desktop:~$ cat /boot/grub/menu.lst
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
default		6

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
# kopt=root=UUID=f10d3fb4-006b-4444-9094-9ebf90e7e1f0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f10d3fb4-006b-4444-9094-9ebf90e7e1f0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f10d3fb4-006b-4444-9094-9ebf90e7e1f0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f10d3fb4-006b-4444-9094-9ebf90e7e1f0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f10d3fb4-006b-4444-9094-9ebf90e7e1f0 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

peter@peter-desktop:~$

---

### Post by pgtl10 on 2008-04-26
Anything wrong with it?

---

### Post by JonUK76 on 2008-04-26
Not an expert myself but it looks like Windows is in your primary partition and the boot.lst file is correctly set up to start it. But for some reason its not working...

So, when you choose XP in the menu, how far does it get?

I had problems with one of my computers and whenever I tried to start XP it would give a message that ntoskrnl.exe was missing or corrupt. Is that what you get?

---

### Post by pgtl10 on 2008-04-26
> **JonUK76 said:**
> Not an expert myself but it looks like Windows is in your primary partition and the boot.lst file is correctly set up to start it. But for some reason its not working...

So, when you choose XP in the menu, how far does it get?

I had problems with one of my computers and whenever I tried to start XP it would give a message that ntoskrnl.exe was missing or corrupt. Is that what you get?

Nope the screen just says starting system...then just freezes. I don't get it.

---

### Post by JonUK76 on 2008-04-26
Hmm not sure. One thing I would try is downloading the Ultimate Boot CD - [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

This comes with various boot utilities including Supergrub. This may allow you to force Windows to start.

Just throwing out some ideas but if your HDD was very fragmented I suppose the partition resizing could have trashed some Windows files or something.

I managed to fix my issue. I did it by re-installing the Windows boot loader and using that to either start Grub (Grub is the boot loader you get with Ubuntu) or Windows. I posted about it here [http://ubuntuforums.org/showpost.php?p=4187629&postcount=11](http://ubuntuforums.org/showpost.php?p=4187629&postcount=11)

---

### Post by axor1337 on 2008-04-26
you need a winxp boot floppy  boot to the disk and type "fixboot "at command prompt this should fix  your win xp boot sector was corrupted during the Ubuntu install  i had same problem when i install from the live disks now i only use te text based installer

---

### Post by pgtl10 on 2008-04-26
> **axor1337 said:**
> you need a winxp boot floppy  boot to the disk and type "fixboot "at command prompt this should fix  your win xp boot sector was corrupted during the Ubuntu install  i had same problem when i install from the live disks now i only use te text based installer

How do I go about getting winXP boot disk?

---

### Post by GeekGirl1 on 2008-04-26
You should have a backup somewhere. Otherwise, you might want to borrow one. You're not going to install anything, just boot it and use the "recovery" option to get to the command line.

I thought the command was "FIXMBR" (Fix Master Boot Record) instead of FIXBOOT.

---

### Post by boomdiddly on 2008-04-26
1. Boot From the Windows XP CD
   2. Allow Windows XP to Begin the Setup Process
   3. Press R to Enter Recovery Console
   4. Choose the Windows Installation
   5. Enter the Administrator Password
   6. Make Necessary Changes in Windows XP Recovery Console

fixboot = Recovery Console command that writes a new partition boot sector to the system partition that you specify.

fixmbr = Recovery Console command that writes a new master boot record to the hard disk drive that you specify.

fixboot is what you need

---

### Post by nicedude on 2008-04-26
Did you use the live CD to resize your XP partition? If so I think thats what did it.

---

### Post by pgtl10 on 2008-04-26
Would this work? 

[http://www.microsoft.com/downloads/details.aspx?FamilyId=15491F07-99F7-4A2D-983D-81C2137FF464&displaylang=en]("http://www.microsoft.com/downloads/details.aspx?FamilyId=15491F07-99F7-4A2D-983D-81C2137FF464&displaylang=en")

---

### Post by boomdiddly on 2008-04-26
> **pgtl10 said:**
> Would this work? 

[http://www.microsoft.com/downloads/details.aspx?FamilyId=15491F07-99F7-4A2D-983D-81C2137FF464&displaylang=en]("http://www.microsoft.com/downloads/details.aspx?FamilyId=15491F07-99F7-4A2D-983D-81C2137FF464&displaylang=en")

It would prob create the disk need but it is a windows exe and unless you have wine installed it won't run and even then is not likely to do what it's ment to, the easiest way to boot to recovery console is to boot the machine with your win xp home CD like I explained above :)

Paul

---

### Post by pgtl10 on 2008-04-26
I don't have a Windows XP CD. Can I buy one?

---

### Post by boomdiddly on 2008-04-26
> **pgtl10 said:**
> I don't have a Windows XP CD. Can I buy one?

erm you could but thats abit expensive for fix a XP installation you could obtain one from another source if your installation is legal of course otherwise that would be piracy!

---

### Post by GeekGirl1 on 2008-04-26
Can you see the NTFS (Windows XP) partition from Linux? At least you would know your data is there. If not, you have a more serious problem.

Now would be a good time to copy that data to a flash drive or make a backup to CD-ROM. 

A USB flash drive should be FAT32 file type, so it's compatible with both Linux and Win XP.

---

### Post by pgtl10 on 2008-04-26
> **boomdiddly said:**
> erm you could but thats abit expensive for fix a XP installation you could obtain one from another source if your installation is legal of course otherwise that would be piracy!

Could you please explain? Also how do I look at my Windows partition?

---

### Post by Reg Editor on 2008-04-26
[http://ubuntuforums.org/showthread.php?t=758289](http://ubuntuforums.org/showthread.php?t=758289)


post number 4

---

### Post by jboy012000 on 2008-04-26
if you go for this idea you will lose everything on your hard drive but if you was smart you would have backed up all your files before you tried to install ubuntu, simply re-install windows from scratch (that's if you have got a copy), yes it will format your hard drive but you will get windows back and it will remove the grub loader that ubuntu uses, then if you want to try re-installing ubuntu as a dual boot then you can hopefully this time with no problems.

i would only use this idea as a last resort though and if i had everything backed up.

good luck.

---

### Post by pgtl10 on 2008-04-26
> **Reg Editor said:**
> [http://ubuntuforums.org/showthread.php?t=758289](http://ubuntuforums.org/showthread.php?t=758289)


post number 4

That might have been a big mistake. I used the recovery console but my now I can't even get a boot menu. How do I even know if programs are still in my computer?

---

### Post by pgtl10 on 2008-04-26
After using the recovery console nothing is working. The load screens completely stalls. The only reason I'm typing is because I'm using the Ubuntu live CD. I don't even my Windows or Ubuntu exists in my hard drive.

1. I went into recovery console.

2. I typed fixboot but the computer said it couldn't find a system directory.

3. I typed FIXMBR and said yes and now my system is not working at all.

Did I erase my hard drive?

---

### Post by kansasnoob on 2008-04-26
I doubt you hurt the info on the drive. You should be able to recover from the Ubuntu live CD.

Check here:

[http://ubuntuforums.org/showthread.php?p=4759429#post4759429](http://ubuntuforums.org/showthread.php?p=4759429#post4759429)

---

### Post by lswest on 2008-04-26
try adding "map (hd0)" after the line "root (hd0,0)" in the menu.lst file.

---

### Post by pgtl10 on 2008-04-26
> **kansasnoob said:**
> I doubt you hurt the info on the drive. You should be able to recover from the Ubuntu live CD.

Check here:

[http://ubuntuforums.org/showthread.php?p=4759429#post4759429](http://ubuntuforums.org/showthread.php?p=4759429#post4759429)

Which posts?

---

### Post by pgtl10 on 2008-04-26
> **lswest said:**
> try adding "map (hd0)" after the line "root (hd0,0)" in the menu.lst file.

Where do I find the menu.1st file?

---

### Post by kansasnoob on 2008-04-26
In this tutorial:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Skip down to the section that says, "Reinstall GRUB to the MBR".

(Note: you're just running off the live CD to use the Partition editor ...... System > Administration > Partition Editor, aka: GParted)

Stop when you get to the line: "Uninstalling Windows XP"

If you follow all the instructions you should be back to using GRUB for the MBR and have a bootable system.

---

### Post by pgtl10 on 2008-04-26
Okay I trashed my MBR. How do I fix it?

---

### Post by pgtl10 on 2008-04-26
> **kansasnoob said:**
> In this tutorial:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Skip down to the section that says, "Reinstall GRUB to the MBR".

(Note: you're just running off the live CD to use the Partition editor ...... System > Administration > Partition Editor, aka: GParted)

Stop when you get to the line: "Uninstalling Windows XP"

If you follow all the instructions you should be back to using GRUB for the MBR and have a bootable system.

It worked until I tried to "setup (hd0)". I get this error message:

Error 17: Cannot mount selected partition


Anyway to solve this?

---

### Post by kansasnoob on 2008-04-26
And you are running from the live CD?

Trying to make these changes in an active partition doesn't work.

I guess I'm stymied.

On one installation I had to wipe out everything but my windows partition and do a clean install of Ubuntu, but it was messy. I had to borrow an XP start up floppy and an external usb floppy drive (because floppies are no longer oem) to get it done.

I really think either GParted or the System Rescue CD can take care of this, I'm just at a loss for a solid answer.

I see the Dell forums have some ideas:

[http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&dl=false&l=en&s=gen&docid=321A8881FA4EC6DFE040A68F5B282E0D&doclang=EN&cs=](http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&dl=false&l=en&s=gen&docid=321A8881FA4EC6DFE040A68F5B282E0D&doclang=EN&cs=)

---

### Post by kansasnoob on 2008-04-26
Here's a "solved" issue in a previous Ubuntu forum:

[http://ubuntuforums.org/showthread.php?t=510567](http://ubuntuforums.org/showthread.php?t=510567)

---

### Post by pgtl10 on 2008-04-26
Here's my plan:

Reinstall Ubuntu from my live CD. That should get GRUB working again. From GRub I'll try to recover Windows and if any luck I will get my first Ubuntu installation as well. Right now I need the boot to work.

---

### Post by kansasnoob on 2008-04-26
Well, I think you'll first want to boot into the live CD and do all of your partitioning. In this case deleting all of the Ubuntu partitions and leaving that space open for your fresh Ubuntu install.

That way when you start GParted won't be confused. It'll make life easier for you. The only drawback is that you'll normally not be able to boot into Windows until you're all done .............. but, like that's a problem already.

Read thru all of these tutorials:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Slow down and take a deep breath.

And give me a few more minutes.

---

### Post by kansasnoob on 2008-04-26
Well, I can't find a "guide" for what I want you to do, but if you've decided to wipe out your old Ubuntu and replace it with a fresh install of any flavor Ubuntu, you want to start by using GParted.

You can do this either with the gparted live cd or any recent ubuntu live cd. You do want to take time to delete all ubuntu partitions including swap/extended. When you're ready to install you'll have nothing but your windows partition and one blank partition.

Other than NOT deleting the windows partition you'll be making no changes there because the Ubuntu installer will take care of GRUB, etc. But, before you try to install you want nothing but the windows partition and a blank partition showing in GParted.

You're much less likely to mess up your windows partition by deleting all ubuntu partitions before you begin the reinstall of ubuntu! And ubuntu/gparted is quite intuitive about creating a proper mbr.

If something is messed up in windows there's a fair chance that can be fixed simply by running "system restore" from the tool menu.

One thing I'll stress is that you can't just make these partition changes from a running system, they must be done from either a gparted live cd or an ubuntu live cd. I hope this is clear as mud.

---

### Post by pgtl10 on 2008-04-26
First of all thank you for all your patience and help. Second I'm a noob when it comes to partitions so I need to ask what is the name of my Windows partition? That way I can avoid erasing it.

---

### Post by kansasnoob on 2008-04-26
I'm a nOOb too. Scary huh!

I've been hoping someone with more tech experience would jump in.

But .......... on mine, since I use ntfs, that shows up in the "file system" column. The size of the partition is also a good indicator.

Do you remember what size the partitions were when you installed?

---

### Post by kansasnoob on 2008-04-26
I should add that the partition numbers will change just like drive letters change in windows. Whatever is there first takes the lowest number.

In GRUB the first number is 0.

Also, if you're using GParted from a Ubuntu live CD sometimes GParted just closes after you make one change, no problem, just open GParted again and continue until all changes have been made. Just be sure you're down to nothing but your windows partition and one free space for ubuntu. The ubuntu installer will create a new swap/extended file.

---

### Post by pgtl10 on 2008-04-26
I erased the right partition. Now it's time to reclaim my Windows. I got an idea. I'll tell you if it works.

---

### Post by pgtl10 on 2008-04-26
Sadly the method I tried didn't work but something unusual happened. The computer wanted to start Windows but computers. The screen there was error when loading operating system. There is something wrong with the Windows partition itself. Gparted tells me that. 

1. I manage to program the computer load up windows but since Windows isn't working, I need to set Ubuntu to start when the computer turns on. How do I do that?

2. If the Windows partition  isn't working, you have any idea how to get it to work?

---

### Post by louieb on 2008-04-26
> **pgtl10 said:**
> It worked until I tried to "setup (hd0)". I get this error message:Error 17: Cannot mount selected partition
Just wondering where your at? 
Does your fdisk still look like this? 

[LIST]
[*]XP is installed in /dev/sda1 or in grub speak (hd0,0)  I know this because the file system is NTFS and thats what XP uses.
[*]Ubuntu is installed in /dev/sda2 or in grub speak (hd0,1)
[/LIST]
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4321    34708401    7  HPFS/NTFS
/dev/sda2            4322       19741   123861150   83  Linux
/dev/sda3           19742       19929     1510110    5  Extended
/dev/sda5           19742       19929     1510078+  82  Linux swap / Solaris

```When you ran **fixmbr** it replace grub with the ipl code for the windows boot loader **ntldr**. To get grub and Ubuntu working again  boot to the live cd and open a terminal window and run grub from there.
```
sudo grub
```Now your at the **grub>** prompt. To  get grub back in the mbr  enter:
```
root (hd0,1)
``````
setup (hd0) 
``````
quit
```Now reboot your PC and Ubuntu should be working.
When you get Ubuntu working we will see what can be done to fix XP.
BTW: I've wrecked XP before so I have some experience trying to get it going again.

---

### Post by pgtl10 on 2008-04-26
My Ubuntu is back! Do I need to edit the flag of my Windows partition?

---

### Post by louieb on 2008-04-26
It can't hurt. To do that install gparted. then open system>administration> partition editor. 
Then right click on /dev/sda1 and choose manage flags. and check boot.
It might complain that there is a boot flag already set for /dev/sda2 thats ok. Ubuntu doesn't need the boot flag set in order to work. But XP does. 

Hope its that simple to get XP working again.

---

### Post by pgtl10 on 2008-04-26
Didn't work. Any other ideas?

---

### Post by pgtl10 on 2008-04-26
Can I boot windows using GRUB? Can I add windows to GRUB somehow?

---

### Post by louieb on 2008-04-27
You had a Windows entry in your GRUB menu earlier. Is it not there anymore? 
Also saw your other thread on this. Noticed you now have 2 swap partitions. Did you reinstall Ubuntu?
I'd like to help but you need to be clear about what you have done sofar.
Anyway if your windows entry is gone you need to add it back to /boot/grub/menu.lst Open the run dialog:  Press Alt+F2 and enter
```
gksudo gedit /boot/grub/menu.lst
```
You window entry will look like this 
```

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
If you need to know were to put it - it goes at the bottom. Just look at the menu.lst you put in post #5.

---

### Post by pgtl10 on 2008-04-27
My last action is to check the Windows flag to boot but I relize my Windows is no longer in the Grub menu. How do I get back to the menu?

Edit: Okay I get back into the menu but the when I try to load it, I get a screen saying 

Error reading disk...
Press Ctrl + Alt + Del

---

### Post by pgtl10 on 2008-04-27
Anybody?

> **pgtl10 said:**
> My last action is to check the Windows flag to boot but I relize my Windows is no longer in the Grub menu. How do I get back to the menu?

Edit: Okay I get back into the menu but the when I try to load it, I get a screen saying 

Error reading disk...
Press Ctrl + Alt + Del

---

### Post by daimaru on 2008-04-27
> **axor1337 said:**
> you need a winxp boot floppy  boot to the disk and type "fixboot "at command prompt this should fix  your win xp boot sector was corrupted during the Ubuntu install  i had same problem when i install from the live disks now i only use te text based installer
I think he meant "fixmbr" (or maybe not, I never heard of fixboot, but maybe it exists too) you can run it if you have a original windows cd. start from cd (as you would for install of windows) choose repair existing windows system or something from the menu ( might be called repair console) and once you get dropped to DOS prompt issue the fixmbr command which writes your master boot record. after this you won't have linux in your boot menu anymore, so you have to reinstall grub from live cd. search the forum for "reinstall grub after windows xp install" or google that. theres loads of answers for reinstalling grub after a windoze install.

---

### Post by pgtl10 on 2008-04-27
> **daimaru said:**
> I think he meant "fixmbr" (or maybe not, I never heard of fixboot, but maybe it exists too) you can run it if you have a original windows cd. start from cd (as you would for install of windows) choose repair existing windows system or something from the menu ( might be called repair console) and once you get dropped to DOS prompt issue the fixmbr command which writes your master boot record. after this you won't have linux in your boot menu anymore, so you have to reinstall grub from live cd. search the forum for "reinstall grub after windows xp install" or google that. theres loads of answers for reinstalling grub after a windoze install.

FIXMBR might have made my computer worse. It is after I typed FIXMBR that my windows starting getting errors.

---

### Post by louieb on 2008-04-28
Can you read the windows data from Ubuntu?

Since **fixboot and fixmbr **didn't solve the problem there is one last thing I know to try.
From the windows recovery console run **chkdisk /F **this will take some time so be patient  
If that doesn't work I'm out of things to try.
Good Luck
lou

---

