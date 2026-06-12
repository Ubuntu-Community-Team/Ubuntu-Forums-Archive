---
title: "Installation Disaster"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Kellow on 2008-05-04
I am an absolute novice.  I have tried to install Ubuntu 8.04 onto an external hard drive - I cannot boot in Ubuntu, although I am given the option between it and Microsoft Windows - all I get when I choose to boot in Ubuntu is a DOS screen.  Worse still, if I try, via Windows, to access the external hard drive onto which I 'installed' Ubuntu, it now gives me two drive letters, and if I try to expand either of those folder trees, I am told I have to format them - this of course I do not want to do.  HELP!!!!

---

### Post by Thingymebob on 2008-05-04
The external drive has 2 letters because it will be formatted as ext3 for the install and a swap partition (so you have 2 partitions) Windows can read neither of these file system which is why it is telling you they need formatting.

Where did you install Grub?

---

### Post by Kellow on 2008-05-04
> **Thingymebob said:**
> The external drive has 2 letters because it will be formatted as ext3 for the install and a swap partition (so you have 2 partitions) Windows can read neither of these file system which is why it is telling you they need formatting.

Where did you install Grub?

Wghat is GRUB?

---

### Post by seshomaru samma on 2008-05-04
grub is the bootloader that gives you the option of booting into windows or linux,
the last stage of installation it asks you where you want to install it,
the default in the MBR (master boot record) , so if you don't remember you probably installed it there.
the reason you can't see Linux in Windows is because Windows is unable to see ext3 format, Windows can only see Fat32 or NTFS (as far as I know)  , don't worry about it - it doesn't mean the disc is broken or something.

not a Grub expert myself , I cannot offer you a solution , hopefully someone smarter than me will be able to assist. In the meantime you can use the forums' search function to look for people who had a similar problem. try "grub external hard drive" or something similar

---

### Post by Thingymebob on 2008-05-04
Grub is the bootloader, without it Ubuntu won't boot

start from scratch,
insert the live cd. and click the install icon.
when you are asked where to install GRUB make sure you select the MBR of your external HDD drive.
you will then need to set your bios to boot from this device or at least display a boot menu fo you to select the boot device.

You do however appear to be making your first steps into Linux difficult for yourself. I am assuming your external HDD is usb (The bandwidth on which sucks for trying to run an OS from).

If I were you i'd partition the main drive and stick Ubuntu on there, or crack open the case and stick in another drive.

---

### Post by Kellow on 2008-05-04
> **seshomaru samma said:**
> grub is the bootloader that gives you the option of booting into windows or linux,
the last stage of installation it asks you where you want to install it,
the default in the MBR (master boot record) , so if you don't remember you probably installed it there.
the reason you can't see Linux in Windows is because Windows is unable to see ext3 format, Windows can only see Fat32 or NTFS (as far as I know)  , don't worry about it - it doesn't mean the disc is broken or something.

not a Grub expert myself , I cannot offer you a solution , hopefully someone smarter than me will be able to assist. In the meantime you can use the forums' search function to look for people who had a similar problem. try "grub external hard drive" or something similar


Windows wants me to format my dis so that it can 'see' it - doesn't formatting erase all data?  I can't afford to do that.

---

### Post by HunterThomson on 2008-05-04
> **Thingymebob said:**
> 

You do however appear to be making your first steps into Linux difficult for yourself. I am assuming your external HDD is usb (The bandwidth on which sucks for trying to run an OS from).

If I were you i'd partition the main drive and stick Ubuntu on there, or crack open the case and stick in another drive.

I aggree. It would be best to partition your main harddrive and install Ubuntu on that. Then Format the external as Fat32 so both window$ and Ubuntu can read it. Then you can store all your music/vids/documents and stuff on it and you can read it from both OS's.

---

### Post by HunterThomson on 2008-05-04
> **Kellow said:**
> Windows wants me to format my dis so that it can 'see' it - doesn't formatting erase all data?  I can't afford to do that.

YES, Don't formatting erases everything and will not solve your problems.

---

### Post by HunterThomson on 2008-05-04
Maybe do it like this;

1- format the external haddrive in windows to fat32
2- move all your important files and moves to the extral hardrive
3- defragmet windows
4- boot into the live ubuntu cd and use Gparted to shrink the windwos partition down so you have like 20GB (OR how big is your harddrive?) at lest 8GB free.
5- unmount and unplug the external harddrive
6- reboot into the live CD
7- install ubuntu and in the partitioning section of ubuntu click the option to install to the longest continues free space and use 100% of it.

You should be rocking then....

---

### Post by Kellow on 2008-05-04
Ok – let me expand.  I CANNOT (will not) format my external HDD – it contains all my data (word docs etc).  It is to this drive that I (unsuccessfully) tried to install Ubuntu.

If I boot up in Ubuntu, it tries to install itself.  First I go through the time zone stuff, and then on the next step, a dialogue box says “Partman failed with Exit Code 10.  Further information may be found in /var/log/syslog”.  If I then choose ‘Quit’, the Ubuntu Desktop screen comes up.  If I look at “My Computer” it shows a partition of 3.1 GIG labeled “media”.  If I try to look at the other partition (that is labeled with the drive’s default name ‘Free Agent’), I get the error message “Cannot mount the volume”.

Where do I want to get to?  I want to undo everything that I have done, without reformatting the external HDD.

Please please come to my rescue.

---

### Post by seshomaru samma on 2008-05-05
If I understand correctly you try to boot from the Ubuntu Live Cd and browse the external drive but it won't mount it?
Am i correct?
In that case I would download [Knoppix ]("http://www.knoppix.org/")(click on the American/British flag for English) which is sort of a rescue CD.
Boot from Knoppix and it should (if everything is okay) see your external HD, browse it , create a back-up etc. You can then use Gparted (an application within Knoppix- look for it in the start menu) to format the ext3 partition into FAT32.

HOWEVER - you are aware that when you install an operating system (be it Linux or Windows) on a partition it needs to wipe all previous information. If you haven't parted your external hard disc into several partitions before installing , it is unlikely that any of your documents were left intact. Sorry.

---

### Post by Bartender on 2008-05-05
> **Kellow said:**
> Ok – let me expand.  I CANNOT (will not) format my external HDD – it contains all my data (word docs etc).  It is to this drive that I (unsuccessfully) tried to install Ubuntu.

Well, you've boxed yourself in here and need to figure out what it is you want to do.  I think everyone was assuming you used an external specifically because it was freed up.  Now you're saying it's not.
Ubuntu uses two file systems (ext3 and linuxswap) that are incompatible with Windows and you need to let it do that somewhere.  How did you think it was going to go onto that external?

---

### Post by zot171 on 2008-05-13
OK, I did something similar, but I did resize my IPod (which I use as an external drive) first.  Using an Ubuntu 7.10 LiveCD, I copied all of my files over to the local disk, so they wouldn't be lost forever, and then used fdisk to set up to 14 cylinders to RAW (bootable), up to 18538 cylinders to FAT32 (bootable, up to  28515 as EXT3 (bootable), and up to 28615 as SWAP. Then, I went through the installer (remembering to change the GRUB installation location to the IPod) and let it go. It worked, and I put back all my files, better then new.

Unfortunately, this was the second time around... the first time I did this I didn't change the GRUB location, so it wrote over my MBR with a misinformed GRUB, and can't boot Windows (GRUB error 21). DON'T Make the same mistake!

---

