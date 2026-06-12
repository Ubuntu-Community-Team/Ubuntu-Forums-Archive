---
title: "[SOLVED] I messed up GRUB."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by jingo811 on 2008-08-05
I installed Windows XP and tried to restore GRUB again.  I usually follow a procedure for Debian but this time I wanted to see if the Ubuntu method would work. (using Gutsy LiveCD)
It worked after some trial and error.  GRUB reappeared again but I couldn't boot any of my Linux distros like Ubuntu, Debian or SuSE only Windows XP.
Then I tried to save GRUB by using my Debian procedure GRUB appeared again but still only Windows XP will boot not the other Linux distros.

I think I messed up GRUB someway.  Because when I try to install a Linux distro from scratch.  The partition manager says there't nothing there :confused:  But I know there are at least 4 Operating systems in /hda 

How can I solve this?

[IMG]http://i35.tinypic.com/20p5xn8.png[/IMG]

---

### Post by sandysandy on 2008-08-05
u will have to update menu.lst file to list ur other linux distros.

code for opening menu.lst file is :  gksudo gedit /boot/grub/menu.lst

be careful and take BACKUP of menu.lst file


regards

---

### Post by bumanie on 2008-08-05
Post the output of > cat /boot/grub/menu.lst

---

### Post by sandysandy on 2008-08-05
have a look at this thread also for updating GRUB

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

regards

---

### Post by Bucky Ball on 2008-08-05
> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

All the advice sounds good. You could make a supergrub disk cd and boot from that. If there are OSs on there, it should find them.

---

### Post by caljohnsmith on 2008-08-05
jingo811, I just wanted to add that the reason that gparted thinks that hda is unallocated might be because you have one or more of the partitions mounted. Make sure everything on hda is unmounted before using gparted.

---

### Post by jingo811 on 2008-08-05
Well I managed to log into Ubuntu again by modifying it's partition numbers during the GRUB menu.  Finding out how to modify Debian's and SuSE's kernel lines will be difficult since they add so much cryptic serial number stuff.

The weird thing is I've kept over 10 menu.lst backups in total for both Ubuntu and Debian.  But none of the partition numbers checks with the current hard drive setup :confused: It's like everytime you do a new grub restore be it from Ubuntu or Debian the numbers for the partition table changes.

I've discovered previously that Ubuntu lists my Linux distros one way, Debian lists the distros in another order, and SuSE lists the distros in yet another order.  It's a mess managing multi boots.

I think I have to study GRUB deeper to understand what's going on. #-o
Best would be to just have Windows XP and 1 other Linux distro going on less headaches that way.

---

### Post by Bucky Ball on 2008-08-05
I think studying up on grub is a great idea, but as I mentioned in my last post, if you are really in trouble for the moment and don't want to lose all those installs you already have there, burn off a copy of supergrubdisk and boot from that. It will probably get you through a tight spot for now and you can work things out then. Just an XP and Ubuntu rig would leave you in the same position if the grub goes awry.

Your problem probably is this; Windoze! Don't mean that in a bad way, but when it writes the MBR, it *always* reconfigures itself as drive 1 (or sda1/hda1). Always. Makes itself the first partition or disk or wherever it is, regardless of what your grub might be saying. Therefore your grub may have had one of your other drives as numero uno, therefore you are booting and finding windoze there instead and the grub is trying to boot an ext3 ubuntu install! Non comprende, says the grub.

Run this command in a terminal:

> sudo fdisk -l

That should tell you where Windoze is cos it is probably on the NTFS drive. Good luck, and I would say before dumping all that hard work or installing and setting up, probe further my friend. Last resort. :)

Update: ah, yes. Sorry, my oversight. In your gparted screenshot, it clearly shows Windoze as being on /dev/hda1, exactly what I meant. That can screw up the grub bad (well, doesn't change anything there, just puts unexpected OS in the wrong place). The convention and easiest is to install Windoze first, then our exotic blends! The purpose of this is only to make MS happy of course, as it will always claim that spot regardless, as mentioned. I have had some really strange things happen with this! Linux is fine going anywhere as you would know. I could be off the mark here, but I am guessing this could be the original cause of your problems. :)

ps: nice pic! Took awhile to make the connection , lol

---

### Post by jingo811 on 2008-08-05
Well actually my Windows XP partition is the only thing that is certain for both myself and GRUB.  I always keep it in /dev/hda1 at all times even when there's no Windows present.

The trouble makers so far has been all the Linux partitions that follows.  I've recently resized a logical partition and re-installed 1 distro.  That seems to have rearranged a lot of Linux partition numbers somehow.

If things could only be absolute and not relatively ordered then this kind of mess wouldn't come up every time you change your partition sizes.

---

### Post by Bucky Ball on 2008-08-05
Damn! Yo kidding jingo811? That sounds odd. I'll re-read and have more of a think. What distro did you install last? Was it 8.04, cos that usually manages to take care of the grub where as Gutsy didn't seem to at all (in my experience). I ran supergrubdisk or tinkered around then.

---

### Post by Bucky Ball on 2008-08-05
This is the result of fdisk -l on my machine;


>  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3814    30630880+   7  HPFS/NTFS
/dev/sda2            3815        9729    47512237+   5  Extended
/dev/sda5            9365        9729     2931862+  82  Linux swap / Solaris
/dev/sda6            3815        5029     9759424+  83  Linux
/dev/sda7            6246        9363    25045303+  83  Linux
/dev/sda8            5030        6245     9767488+   b  W95 FAT32

I notice one difference: I have an 'Extended' partition, whilst you have your linux distros in a 'W95 Ext'd' partition which has been setup in Windoze ... is this going to be a problem? Maybe Windoze is looking at its extended partition at boot and seeing something it doesn't recognise or understand.

---

### Post by estyles on 2008-08-05
If you posted your menu.lst, I missed it, but I'm guessing that your drives are being accessed by UUID in the menu.lst - I'm pretty sure that's how OpenSUSE does it by default.  UUID changes everytime you resize a partition, so that will cause you problems.  I would edit the menu.lst to use labels like sda1, etc...  If you don't know how to do that, then post your menu.lst, I'm sure someone (possibly me, though I'm no expert) can tell you how to edit it.

---

### Post by baggins on 2008-08-05
Yep like estyles said it would be good to see the menu.lst, and as you seem to have more then one disk in the machine could you please also post /boot/grub/device.map for reference as well.

As for the UUIDs they are assigned attributes of the file system, and will indeed usually be changed if you resize a partition. In this case however, the most likely thing to have happened is that the installer generated new uuids, rather than use those already assigned. (at least that happened to me :) )

You can get the UUID of a specific partition by using the following command
```
sudo vol_id --uuid /dev/hdaX
```
replace hdaX as needed

Then make sure that the entries in the grub menu have something like
```
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=
```
followed by the UUID.

Btw dont forget that /etc/fstab also use uuids.

-- Jon

---

### Post by jingo811 on 2008-08-07
No sweat people I erased the entire harddrive.  It seems like my harddrive is getting old GPARTED detects physical errors.  GPARTED can't see partitions.
Windows detects hard drives in a whacky way G: is Windows C: is Pagefile D: is DVD.  I've done fresh installs on this PC some 20 times before.  This must be some hardware troubles involved.

I just barely managed to install Windows and Ubuntu fresh through pure stubborness.  I encountered errors just by trying to partition a simple ext3 filesystem.

Anyways tnx for your help.  I'm good now.  Not wiser but still good :)

---

### Post by JoshuaRL on 2008-08-07
In the future if you have massive GRUB errors that aren't hardware related, you might try out kgrubeditor.  It's in the repos, and it is very nice for editing GRUB from a GUI.  Really slick, like most K-apps.

---

