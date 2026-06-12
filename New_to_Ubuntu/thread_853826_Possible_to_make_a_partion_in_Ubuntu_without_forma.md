---
title: "Possible to make a partion in Ubuntu without formatting?"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by ImThatNerd on 2008-07-08
Well I have a lot of things under Ubuntu and really can't reformat and I need to install Windows for some applications that are required and they do not run under Wine. So I was wondering can I make a partion while in Ubuntu for Windows without reformatting?

---

### Post by 449 on 2008-07-08
Download the Gparted Live CD.

Oh, and if you install windows to a new partition your GRUB won't load properly. Your best bet, if possible, would be to store your files on an external harddrive and install windows first, then install Ubuntu. That way you won't have to worry about trying to reinstall GRUB.

---

### Post by ImThatNerd on 2008-07-08
So I basically have to reformatt everything? Ugh. What if I pick up an external HDD to install windows to or something?

---

### Post by 449 on 2008-07-08
> **ImThatNerd said:**
> So I basically have to reformatt everything? Ugh. What if I pick up an external HDD to install windows to or something?

Well you don't **have** to. I would try to find out how hard it would be to reinstall GRUB... And if you think it won't be too much of a hassle go for it.

---

### Post by Hooya on 2008-07-08
No, although that would be faster and more ideal.  But here's what you'd do anyway.

Clean your Windows installation.  Hardcore.  Remove extraneous programs you don't use anymore and delete temporary files.  Especially put any sound and video files on some external media (burn to DVD or use an external hard drive).  Then defrag your drive.

Then use the Gparted Live CD as suggested and resize your windows partition to a useable amount (varies depending on your programs and version of windows, etc).  This could take a VERY long time.

Then install Ubuntu from the Live CD using the manual partitioning options to use the empty space on the disk you just created with gparted.  Grub should take over your boot record and give you the choice of what to boot when you start your computer.

Edit:
Oh crap.... just realized you have your Ubuntu installation already, but not your Windows... I did directions the other way around...

Well, the fix for that is the [Super Grub Disk]("http://www.supergrubdisk.org").  It'll re-install grub for you after installing windows.  Everything else is actually surprisingly the same, just ignore the defrag and substitute "ubuntu" for "windows" in my directions.

---

### Post by ImThatNerd on 2008-07-08
I really didn't want to reformat, but could I use an external hard drive?

---

### Post by logos34 on 2008-07-09
> **ImThatNerd said:**
> I really didn't want to reformat, but could I use an external hard drive?

Windows on the external?  It's [possible]("http://www.ngine.de/article/id/8").  But I wouldn't recommend it.

You don't have to reformat ubuntu to dual boot windows.  And grub can easily be reinstalled after windows.

Or you could always run windows inside ubuntu on VMWare.

For the dual boot, you'll need to boot the ubuntu live cd and use Gparted (system>admin>partition editor) to shrink ubuntu down to make room.  (You have to work from the live cd because root cannot be mounted during resize).  Format the new space ntfs, or leave it unallocated and let the windows install cd format it--either way.

Use the ubuntu live cd to [reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351").

Then add a windows boot stanza to the bottom of /boot/grub/menu.lst, using the example provided at the top of that file.

---

### Post by ImThatNerd on 2008-07-09
> **logos34 said:**
> Windows on the external?  It's [possible]("http://www.ngine.de/article/id/8").  But I wouldn't recommend it.

You don't have to reformat ubuntu to dual boot windows.  And grub can easily be reinstalled after windows.

Or you could always run windows inside ubuntu on VMWare.

For the dual boot, you'll need to boot the ubuntu live cd and use Gparted (system>admin>partition editor) to shrink ubuntu down to make room.  (You have to work from the live cd because root cannot be mounted during resize).  Format the new space ntfs, or leave it unallocated and let the windows install cd format it--either way.

Use the ubuntu live cd to [reinstall grub]("http://ubuntuforums.org/showthread.php?t=224351").

Then add a windows boot stanza to the bottom of /boot/grub/menu.lst, using the example provided at the top of that file.

Is VMWare free and runs windows fine? See I only have a 40GB HDD, but have about 23GB+ of free space. I know I wont fill this HDD up anytime soon and I do not need a whole lot of space on Windows so yeah I guess I do not need an external.

Do you have a tutorial for what you mentioned about partion editor and all that? I am sort of confused.

So I just pop in the live cd and boot to it and go to the partion editor and give lets say 25GB to Ubuntu. So then after that I boot to the windows cd and just install it? I think I tried that before and it made me reformat or something.

---

### Post by RiceMonster on 2008-07-09
Yes, VMware is free and yes it does run Windows fine. Another option is to try Virtualbox, but that's up to you.

```
sudo apt-get install virtualbox
```

Personally, I would highly recommend you use a VM rather than creating a partition for Windows. It would be much easier to get rid of.

---

### Post by Victormd on 2008-07-09
As Logos34 mentioned, you don't have to reformat your HD. **[COLOR="Red"]However, it is strongly suggested that you backup all of your data![/COLOR]** Download the Gparted live CD from [here]("http://gparted.sourceforge.net/livecd.php"), and supergrub CD [here]("http://www.supergrubdisk.org/"). burn them and boot to the Gparted CD. Gparted will allow you to resize your HD to the desired size (i.e., 30GB ubuntu 10GB windows). What you have to be careful with is that windows install won't recognize your ubuntu partition and you will have to choose corectly not to format your ubuntu drive. Gparted will not be able to create the NTFS partition but will provide the free space - i.e. 10GB - that can be formatted as NTFS during your windows install.

Once you're done installing windows, insert he supergrub CD and boot and that will allow you to restore your grub with the windows installation included.

As for virtualization, it all depends on what you want windows for. I have windows virtualized and it runs fine.  However, if you want it for games, virtual machines are not an alternative as you don't have 3D graphics support - then dual boot is your only choice. Furthermore, keep in mind that your computer has to meet the minimum requirements for Ubuntu + Windows combined.

I use VirtualBox and everything works perfectly. If you want USB support, don't use the package from the repos, instead, download the PUEL version from [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI").

---

### Post by ImThatNerd on 2008-07-09
Hmm I will look into both VMWare and Virtual box, any recommendations? 

My specs:

768MB RAM
1.8GHz Pentium 4 Processor.

I do not plan on running games, but just photoshop and some applications that aren't heavy on resources.

---

### Post by ImThatNerd on 2008-07-09
nevermind

---

### Post by ImThatNerd on 2008-07-09
Okay I set it up fine I think and have the disc in and hit start. I am at the blue screen in windows and it is telling me to install. So...?

---

### Post by RiceMonster on 2008-07-09
You have that screen within VMware or Virtualbox? If so, then install as usual.

---

### Post by ImThatNerd on 2008-07-09
Virtual box, I am trying it out. If I don't like it I will try VMware.

It says it needs to format the 10GB I assigned to it. Will I be able to delete this 10GB later on? Also should I do a quick reformat NTSF file system?

---

### Post by RiceMonster on 2008-07-09
It creates a virtual harddisk that you can delete at any time you like. Just let the installer format it. It won't affect you're harddrive at all (other than the file for the harddisk taking up 10GB, of course).

---

### Post by ImThatNerd on 2008-07-09
Alright great, it is going through the installing now. I am just dreading setting up my internet on Windows. My router and internet seems to hate Windows, but loves Ubuntu, and it takes forever to set-up.

While I wait, is VMWare better? Faster? Is it free? I could only find server information on it.

Hmm seems like my wireless USB mouse is not working, but my wireless USB keyboard is.

---

### Post by ImThatNerd on 2008-07-09
I just got this error, and I didn't even touch the disc.

Would it be best to do this with .ISO?

---

### Post by ImThatNerd on 2008-07-09
Anyone? I am sort of stuck in this installation and do not know what to do.

---

### Post by Victormd on 2008-07-09
An error like that usually indicates that there's something wrong with the CD.

As for your previous questions, have you checked the [WineHQ database]("http://appdb.winehq.org/") to see if your progs will run under wine?

With the amount of RAM that you have, I don't think you'll be able to get much out of virtualization. You'll need to allocate a minimum 256MB for Windows and that's so it will run. Though photoshop is not a big resource hog, you'll need to check what the minimum requirements are (memory-wise) to get it working and see if that matches what you have.

The 10GB virtual HD created by virtualbox is a file inside ubuntu so you can delete it at any time, completetly removing your virtual windows.

---

