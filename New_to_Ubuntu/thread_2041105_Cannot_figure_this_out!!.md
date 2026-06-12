---
title: "Cannot figure this out!!"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by Newbie19380 on 2012-08-11
So, for my first post, I'm going to stump no one but myself.  My problem is this:

About a week ago, I installed Windows 8 -- I hate it and there are way too many bugs for my little netbook that I installed it on.  In the process, I formatted a hard drive that had all of the iTunes music and movies on it, along with my all of photos.

Needless to say, I'm so feed-up with Windows and Microsoft that I started researching Linux OS's -- I really like Ubuntu, except that for some reason, it is still running side-by-side with Windows 8.

My netbook doesn't have a DVD-drive, so I have to boot from a USB drive.

The problem is that no matter how many times I download the software, it is always the "Windows Installer" version and I cannot get rid of Windows 8 (which my ultimate goal).

Now, in layman's terms, how can I get rid of Windows 8 and please be gentle.  I'm new at all of this "back of the book" type of stuff.

Thanks!!

---

### Post by drudogg76 on 2012-08-11
Ok, so I'm a bit of a newbie too, but I've done this successfully on a netbook before... What you are going to need is a bootable USBStick with the Ubuntu LiveCD on it - then install Ubuntu from that. That will give you the option to wipe out Windows completely.
So, here's what I did:

1. Download and install UNetBootin' on your windows machine.

2. (this part I'm not 100% on) when you open up UNetBootin' you should be able to select the 'flavor' of Ubuntu you want and it will download and create the bootable USB stick for you... If this doesn't work, you'll have to download Ubuntu from the website first (will be a .iso file) then use UNetBootin' still to make the USBStick.  This process will take some time to complete.   MAKE SURE THE USB STICK YOU ARE USING IS BLANK - as everything will be overwritten during this process.

3. When you reboot your netbook, make sure you have USB boot BEFORE the HDD boot, so it will look there before it opens Windows.

4. Ubuntu LiveCD will load and give you an option to install..

Please remember though, that once you do this... ALL partitions on the harddrive will be gone, so your ability to get windows back from recovery partitions and things will be GONE.  

Hope this helps...

D

---

### Post by chadk5utc on 2012-08-11
In addition to the previous post when you are going through the install watch for a section that asks you where to install GRUB and install this to the Master Boot Record this is your boot loader also worth mention is during partitioning it will give you options to format/partion and use the entire disk I would do this if you are in fact getting rid of Winblows

---

### Post by sammiev on 2012-08-11
Make sure you have a backup or a copy of Win8 before you install Ubuntu. On boot up you should see your Bios screen for 5 seconds or so. It will give you a message to press (key) for boot options or go into your Bios and select USB to boot first. Also Welcome to the forums! :)

---

### Post by gavv on 2012-08-11
> **Newbie19380 said:**
> Cannot figure this out

One option is to completely erase your hard drive using DBAN, an open source solution. This will ultimately remove Windows, permanently.

If you don't want to go with the USB drive, it is possible to use a portable USB DVD-drive.

---

### Post by anewguy on 2012-08-11
> **gavv said:**
> One option to completely erase your hard drive is to use DBAN, an open source solution. This will ultimately remove Windows, permanently.

If you don't want to go with the USB drive, it is possible to use a portable USB DVD-drive.

The OP shouldn't need to wipe the disk - just the normal partioning when installing Linux will do what they need.

---

### Post by p3anoman on 2012-08-12
You can also try the [Ubuntu Windows installer]("http://www.ubuntu.com/download/desktop/windows-installer"). It works great. Used it last night and it worked flawlessly on WinXP. Definitely worth a try

---

### Post by vexorian on 2012-08-12
WUBI is not that good if you really want to get rid of windows.

I think the problem is that you can't boot the installer. Well, usually you have to setup the computer to boot from the USB disk. Usually pressing F12 constantly while the computer is being turned on will open a menu to select the boot device,.

---

### Post by Bashing-om on 2012-08-12
Don't forget to backup all the data (your pics and music and files) on the hard drive before installing installing and wiping out windows (good move) ... and yes ....welcome to our world
[INDENT]              BDQ
[/INDENT]

---

### Post by The Cog on 2012-08-12
I think vexorian has the right answer. To install Ubuntu to the hard disk, you must boot from the USB disk/stick. Booting windows and then looking at the stick contents will only ever show you the windows installer, that installs Ubuntu inside windows. You must boot directly from the stick, without booting windows at all.

---

