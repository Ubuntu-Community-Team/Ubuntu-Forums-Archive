---
title: "Can ubuntu be deleted in a dual boot?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Rukaru on 2008-05-10
I want to uninstall/delete ubuntu (so I can reinstall it fresh), but I have XP dual booted on the computer.  I had ubuntu partition it for me.  Now, how do I do this?

One reason i want to reinstall is because I screwed some things up, and it'd just be easier to start over.  Also, I was kinda dumb and I tested out ubuntu's virus resistance by going to a known bad site.  Nothing seemed to happen.  Then later, while watching youtube, my cursor started moving by itself and the keyboard wouldn't work.  yeah....not good.  I looked and there seems to be some malicious files.  With words that I find suspicious like seahorse and tracker.  Yes...tracker!  That's not good. Oh yeah...and then there's "virtual-[my name here].3lfeiw.  So, I just want to resinstall.  I'll feel better.  Can I do that without hurting XP?

---

### Post by sharks on 2008-05-10
Open a formatting software or insert the live and go to Gparted and format the partition where u have installed ubuntu. Dont forget to back up ur important files.

---

### Post by Rukaru on 2008-05-10
> **sharks said:**
> Open a formatting software or insert the live and go to Gparted and format the partition where u have installed ubuntu. Dont forget to back up ur important files.

Sorry...I have no idea what you just said.  i just got ubuntu and I'm a complete noob.  What is live, Gparted, and how can I find the partition?  Ubuntu did all that.

---

### Post by thisiam on 2008-05-10
when you installed ubuntu you used a live cd right? well from there you can use gparted and format your ext partition and reinstall ubuntu from that same live cd. 
always remember to back up.

---

### Post by Rukaru on 2008-05-10
> **thisiam said:**
> when you installed ubuntu you used a live cd right? well from there you can use gparted and format your ext partition and reinstall ubuntu from that same live cd. 
always remember to back up.

i used a cd that i made by getting a blank one and burning the installer on it.  that one right?  so what is gparted?  and are you sure i have an external partition?  i can access my windows hdd (c) from ubuntu by going to 'computer' and selected that drive.  doesn't this mean they are connected and it is also internal?  now to clarify...i did choose the full version when i installed hardy heron.  i did not choose to run it as an app within xp.

---

### Post by thisiam on 2008-05-10
yah that same cd you should be able to go to System/Administration/Partition Editor and from there you can format your ext partition, then go back to the desktop and install. When you get the partition section select to install to your ext partition that you just formatted.
or you can check out wubi and install it from windows, this seems to be the easier way at the moment.

---

### Post by Rukaru on 2008-05-10
> **thisiam said:**
> yah that same cd you should be able to go to System/Administration/Partition Editor and from there you can format your ext partition, then go back to the desktop and install. When you get the partition section select to install to your ext partition that you just formatted.
or you can check out wubi and install it from windows, this seems to be the easier way at the moment.

will the process you described her completey erase the partition and give xp all the space back?  i might not want to reinstall ubuntu, but in any case i just want it gone for now.  so, could you walk me through the steps to do this?

---

### Post by inportb on 2008-05-10
It should be trivial to reinstall Ubuntu fresh -- just select manual partitioning, select the original Ubuntu partition for formatting, mount it as /, and proceed as usual.

If you don't want Ubuntu anymore, you can format the partition to something that XP can read; it would appear as a separate volume in XP. You can also delete the partition and resize the XP partition.

---

### Post by Sef on 2008-05-10
> so what is gparted?

[GParted]("http://gparted.sourceforge.net/") is an open source partitioner.

---

### Post by thisiam on 2008-05-10
> **Rukaru said:**
> will the process you described her completey erase the partition and give xp all the space back?  i might not want to reinstall ubuntu, but in any case i just want it gone for now.  so, could you walk me through the steps to do this?

no, it will delete your linux partition which is what i thought you were trying to do so you can reinstall ubuntu.
If you want to give the space back to windoze you should delete the ext and swap if you have it and leave it unallocated so that you can re size your windows and take over the remaining space.

Edit: if you are looking to get back to windows only you should look into fixing your MBR before you delete the Linux partitions, will make the transition back to windows allot easier.

---

### Post by Rukaru on 2008-05-10
> **thisiam said:**
> no, it will delete your linux partition which is what i thought you were trying to do so you can reinstall ubuntu.
If you want to give the space back to windoze you should delete the ext and swap if you have it and leave it unallocated so that you can re size your windows and take over the remaining space.

Edit: if you are looking to get back to windows only you should look into fixing your MBR before you delete the Linux partitions, will make the transition back to windows allot easier.

ude i don't know what these things are.  i just want windows....no more partition...no more dual boot.  just windows.

---

### Post by thisiam on 2008-05-10
did you install windows on the computer? if you did you should that same cd to do a clean install of windows and save all the trouble.
if you don't have a windows cd you should have some sort of back up disc that came with the computer, those should do aswell.

but you should give ubuntu more of a chance, its really user friendly and you can learn alot more.

---

### Post by Thingymebob on 2008-05-10
How you remove depends on how you installed

If you used wubi (Installed ubuntu from within windows) then you can simply go to add/remove programs in windows and remove ubuntu from there.

If you installed by inserting a CD into your machine and booted from it to a Linux desktop, then this is the Live CD. To remove Ubuntu you will again need to boot from this CD to the Linux desktop.
*Open Applications->System Tools->Gparted (It just like partition magic)
*Remove any partition that is either ext2 ext3 or swap don't remove anything labelled ntfs as this is where windows is.
*You can now, if you like resize the ntfs partition to fill your drive again.

*Now insert your windows install CD
*Press R at the setup screen,
*select you windows installation  and enter the admin password
*type FIXMBR
*confirm with Y
*remove the CD and Reboot

---

### Post by Rukaru on 2008-05-10
> **thisiam said:**
> did you install windows on the computer? if you did you should that same cd to do a clean install of windows and save all the trouble.
if you don't have a windows cd you should have some sort of back up disc that came with the computer, those should do aswell.

but you should give ubuntu more of a chance, its really user friendly and you can learn alot more.

I think it'd make life more complicated having an extra opperating system.  I'll stick with XP>  it works so well, and I love all the free security you can get.  Yes, I know ubuntu doesn't need it, but I want to feel secure.  

Now, I'd rather not do this since I have a lot on there, but I can always get it back.  So, will the hard drive be partitioned once i erase everything?  And how do I erase everything?

---

### Post by thisiam on 2008-05-10
> **Rukaru said:**
> I think it'd make life more complicated having an extra opperating system.  I'll stick with XP>  it works so well, and I love all the free security you can get.  Yes, I know ubuntu doesn't need it, but I want to feel secure.  

Now, I'd rather not do this since I have a lot on there, but I can always get it back.  So, will the hard drive be partitioned once i erase everything?  And how do I erase everything?

Do you have windows cd to install once you erase everything?

---

### Post by Xiong Chiamiov on 2008-05-10
> **thisiam said:**
> Do you have windows cd to install once you erase everything?
He doesn't need to erase anything.  As Thingmebob said, all he needs to do is erase his linux partition and resize the windows partition to take over the newly freed space.  Don't go making the poor kid reinstall things he doesn't have to.

---

### Post by Rukaru on 2008-05-10
> **thisiam said:**
> Do you have windows cd to install once you erase everything?

yeah I do.  I'd like to avoid that...but if it's the only option, then ok.  I backed the most important stuff up.  Now, Can someone please just walk me through the steps to get my entire windows XP hard drive back to where it was, and the hard drive partition gone.  I did use the CD and I chose full installation...not inside windows.

---

### Post by Rukaru on 2008-05-10
> **Xiong Chiamiov said:**
> He doesn't need to erase anything.  As Thingmebob said, all he needs to do is erase his linux partition and resize the windows partition to take over the newly freed space.  Don't go making the poor kid reinstall things he doesn't have to.

Thanks man.  How did you know I was a kid?  Well......18...so I'm a kid and adult. I probably sound like a kid because I'm so lost and bewildered! Now, how do I erase the linux partition?

---

### Post by Xiong Chiamiov on 2008-05-10
> **Xiong Chiamiov said:**
> He doesn't need to erase anything.  As Thingmebob said, all he needs to do is erase his linux partition and resize the windows partition to take over the newly freed space.  Don't go making the poor kid reinstall things he doesn't have to.
Now, let's see if I can clarify a few things I saw in this that you had questions about.

Live CD - a live cd allows you to run an operating system completely off of a CD, without installing it onto your hard drive.  If you get the standard Ubuntu CD, that is a live CD.  Although most people use it merely as a starting point for installing, it is fully functional on its own.
MBR - The master boot record is at the very beginning of your hard drive, and it's what controls where to look for an Operating System.  For most dual-boot installs, the MBR points to GRUB, which then allows you to choose from Windows and Ubuntu (or whatever)
GParted - an excellent partition editor included with Ubuntu on the CD.  For much of your partitioning work, you will need to use it off of the Live CD.  It allows you to do pretty much anything fairly easily with your partitions.
Ext3 - a filesystem (like NTFS or FAT32) for harddrives.  It's the standard for Linux, just like NTFS is the standard for Windows.

---

### Post by Xiong Chiamiov on 2008-05-10
> **Rukaru said:**
> Thanks man.  How did you know I was a kid?  Well......18...so I'm a kid and adult. I probably sound like a kid because I'm so lost and bewildered! Now, how do I erase the linux partition?
I'm 18 as well (actually, almost 19 - I forgot!); I just refer to poor souls as kids, just like I refer to many other people as dear.

You'll have to boot off of the CD, but you can try the first part of this right now if you want to make sure you got it before you go ahead and actually do it.  You'll find GParted in Applications->System Tools->Gparted.  It'll show a graphical representation of your partitions, like [this]("http://gparted.sourceforge.net/larry/resize/resizing.htm").  You'll need to select the one that Linux is on (if in doubt, look below for the one that says it is ext3.  Then press delete (this you won't be able to do unless on the Live CD!).  Do the same for the partition labelled swap (it's probably pretty small).  After that, select the windows partition (again, underneath listed as ntfs) and click resize, then drag it to fill in the whole space.  Then proceed with the rest of the directions Thingmebob said.

---

### Post by Rukaru on 2008-05-10
> **Xiong Chiamiov said:**
> Now, let's see if I can clarify a few things I saw in this that you had questions about.

Live CD - a live cd allows you to run an operating system completely off of a CD, without installing it onto your hard drive.  If you get the standard Ubuntu CD, that is a live CD.  Although most people use it merely as a starting point for installing, it is fully functional on its own.
MBR - The master boot record is at the very beginning of your hard drive, and it's what controls where to look for an Operating System.  For most dual-boot installs, the MBR points to GRUB, which then allows you to choose from Windows and Ubuntu (or whatever)
GParted - an excellent partition editor included with Ubuntu on the CD.  For much of your partitioning work, you will need to use it off of the Live CD.  It allows you to do pretty much anything fairly easily with your partitions.
Ext3 - a filesystem (like NTFS or FAT32) for harddrives.  It's the standard for Linux, just like NTFS is the standard for Windows.
Ok, I think I understand.  I just downloaded ubuntu onto a blank CD, chose full installation, made a half XP/half ubuntu partition, took out the CD, tried Ubuntu, thought ubuntu was interesting, realized that although it may be the best OS it is just not for me, posted here with questions, you answered the questions, and I'm replying to your answers now.  

So, do I put the CD in while I'm on ubuntu or XP?  And...will ubuntu be completely erased? Right now, it gives me the option when I boot up to choose the OS....I want it to just have XP like it used to.  So yeah...it's important that I completely get rid of ubuntu.

---

### Post by thisiam on 2008-05-10
Doesn't sound like you want to go through the steps to delete ubuntu, thats why i suggested just backing up and doing a clean install of windows but if you follow the steps that Thingymebob wrote you should be able to fix your MBR  then re size your windows partition to take over the whole drive.

---

### Post by Xiong Chiamiov on 2008-05-10
It doesn't matter when you put in the CD; it won't take effect until you reboot, and then you'll choose the option "Start or install Ubuntu" (or something similar, if the changed the wording).  The method I described to you will erase Ubuntu completely from your hard drive, and Fixmebob's last part will set everything back how it was.  His thing will require that you have an actual XP cd, not one of those crap reinstall-with-all-our-software cds from most pc manufacturers.  If you only have one of those, then we can deal with that, let me think for a moment.

---

### Post by Rukaru on 2008-05-10
> **Xiong Chiamiov said:**
> It doesn't matter when you put in the CD; it won't take effect until you reboot, and then you'll choose the option "Start or install Ubuntu" (or something similar, if the changed the wording).  The method I described to you will erase Ubuntu completely from your hard drive, and Fixmebob's last part will set everything back how it was.  His thing will require that you have an actual XP cd, not one of those crap reinstall-with-all-our-software cds from most pc manufacturers.  If you only have one of those, then we can deal with that, let me think for a moment.

Yep I just have the reinstall cd from the pc manufacturer.  Man, this is just a nightmare for me.  it's so stressful. I want everything back to the way it was so badly....

---

### Post by Xiong Chiamiov on 2008-05-10
Ok, 2 things:
You may need to run fdisk /mbr instead of fixmbr.  Don't know why, but some people have had trouble with one or the other.

Just to be safe, I'd download a copy of [Super Grub Disk]("http://supergrubdisk.org/") in case you get stuck not being able to boot into Windows.  If you burn that to a CD, you can boot any partition from it.  It comes with directions and lots of smiley faces!

EDIT: Oh, and for others viewing this thread, you might want to try out Wubi instead.  It installs *buntu from inside Windows, so you can uninstall it like any Windows program.

---

### Post by Rukaru on 2008-05-10
> **thisiam said:**
> Doesn't sound like you want to go through the steps to delete ubuntu, thats why i suggested just backing up and doing a clean install of windows but if you follow the steps that Thingymebob wrote you should be able to fix your MBR  then re size your windows partition to take over the whole drive.

I'll go through the steps, I just need to have a good understanding, and i need to keep XP as it is because I have no xp install CD...just the PC manufacturer XP reinstaller.

---

### Post by Rukaru on 2008-05-10
> **Xiong Chiamiov said:**
> Ok, 2 things:
You may need to run fdisk /mbr instead of fixmbr.  Don't know why, but some people have had trouble with one or the other.

Just to be safe, I'd download a copy of [Super Grub Disk]("http://supergrubdisk.org/") in case you get stuck not being able to boot into Windows.  If you burn that to a CD, you can boot any partition from it.  It comes with directions and lots of smiley faces!

EDIT: Oh, and for others viewing this thread, you might want to try out Wubi instead.  It installs *buntu from inside Windows, so you can uninstall it like any Windows program.

So how do I use fdisk/mbr or fixmbr?

---

### Post by Xiong Chiamiov on 2008-05-10
> **Rukaru said:**
> So how do I use fdisk/mbr or fixmbr?
Since you don't have a real XP cd, you'll probably have to use Super GRUB disk to get into Windows.  Once you're in (it'll boot just like normal), go to start -> run and type 
```

cmd

```
From the command prompt that comes up, type 
```

fixmbr

```

---

### Post by Rukaru on 2008-05-10
> **Xiong Chiamiov said:**
> Since you don't have a real XP cd, you'll probably have to use Super GRUB disk to get into Windows.  Once you're in (it'll boot just like normal), go to start -> run and type 
```

cmd

```
From the command prompt that comes up, type 
```

fixmbr

```

This seems too complicated.  How will the manufacturer CD be any different than the actual XP cd? I once reformated windows just by putting that disk in.  I really just want to find the safest and easiest way to do all this.  This is just a nightmare.  I never should have done the full installation of ubuntu!

---

### Post by Xiong Chiamiov on 2008-05-10
Real Windows CDs allow you to do many things other than a complete reinstall of Windows.  Manufacturer CDs, however, will only restore your computer to the state it was when it left the factory, which is not what you want (you want your data, right?).

It is by nature going to be somewhat complicated - you're dealing with booting multiple operating systems!  Despite what many say, linux is not for everyone, nor is it completely understandable [immediately by normal computer users]("http://contentconsumer.wordpress.com/2008/04/27/is-ubuntu-useable-enough-for-my-girlfriend/").  [Wubi]("http://wubi-installer.org/"), however, is an excellent (new) option that simplifies the whole process quite a bit.

That said, we'd love to help you, even if you are removing our operating system of choice!  I know I'll lose sleep over a problem someone's been having that I don't know the answer to, and I'm sure many others here are the same way.  We just want you to have a good computing experience.

---

### Post by inportb on 2008-05-10
You can do a backup using your live CD, which you can restore onto your fresh Windows setup.

---

### Post by Rukaru on 2008-05-10
> **Xiong Chiamiov said:**
> Real Windows CDs allow you to do many things other than a complete reinstall of Windows.  Manufacturer CDs, however, will only restore your computer to the state it was when it left the factory, which is not what you want (you want your data, right?).

It is by nature going to be somewhat complicated - you're dealing with booting multiple operating systems!  Despite what many say, linux is not for everyone, nor is it completely understandable [immediately by normal computer users]("http://contentconsumer.wordpress.com/2008/04/27/is-ubuntu-useable-enough-for-my-girlfriend/").  [Wubi]("http://wubi-installer.org/"), however, is an excellent (new) option that simplifies the whole process quite a bit.

That said, we'd love to help you, even if you are removing our operating system of choice!  I know I'll lose sleep over a problem someone's been having that I don't know the answer to, and I'm sure many others here are the same way.  We just want you to have a good computing experience.
 Well I really appreciate that man.  I never expected to find this kind of compassion over the internet of all places! Anyway, I don't mind losing my data that I've put on XP.  I just want to be able to continue using xp...but with all its hard drive space.  Actually, if it somehow made it easier to just have a small partition...like an empty 10GB hard drive...I wouldn't mind that so much.  I wasn't using much of my hard drive.  Basically, I want to erase all traces of ubuntu.  Can I do what I want to do using the manufacturers CD and the ubuntu installation CD? Again, I don't mind losing data like documents, pictures, music, installed programs, etc.  I just want to be able to get it all back.  I made backups of most of it, so it will probably only take about 6 hours to get everything else back.  I'm willing to sacrifice that.  Now I just need someone to tell me how to do it.

---

### Post by Rukaru on 2008-05-10
> **inportb said:**
> You can do a backup using your live CD, which you can restore onto your fresh Windows setup.

Well I need to be walked through this.  Like I said, I don't mind losing my data on XP since I cab get it back.  I don't need any backups of anything since I have the manufacturer XP CD.

---

### Post by sailor2001 on 2008-05-10
if I remember correctly, xp has a partioner built in. Right click 'mycomputer' "hard drives' 'manage' or something like  that. I don't have xp to check.    but regardless, download and burn 'supergrub'

---

### Post by jerrallan on 2008-05-11
Okay. you want to completely delete your Linux from your machine? If you have an internet connection this will probably work. It is work and requires some reading, your time, and downloading. There is no getting around that.

Before you do anything, make sure your Windows XP partition is defragmented. Start>Accessoriries>System Tools>Defragment  . Since you are resizing your XP partition UP this may not be necessary,but.....

Then read this whole post before doing anything else.

**Step 1**. You can delete partitions and resize using the partition editor in your **Ubuntu Live CD**. I believe that is discussed in previous posts. System>Administration>Partition Editor. Follow the general instructions I give for **Parted Magic**. I think you will need to restore your Windows XP boot by using **Super Grub **disk CD. 

An alternate way to delete and and resize your partition, other than using the **Unbuntu Live CD**, is to use **Parted Magic**. [see below]

to download  **Parted Magic** go to this website"
[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

Go to the download page. Then go to the mirror page to download the iso file pmagic-2.2.iso
Burn it onto a cd.

You would do well to read the instructions on the above web site under documents.

You can download the iso  file for **Super Grub** Disk at
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Download the latest file supergrubdisk_0.9677.iso and burn it to cd.

Now you may have to change your settings as to what the computer boots first. change it to boot cd first.

**Step 2**. Install the **Parted Magic CD** and boot it. You will come to a desktop.
Then you will get a menu press enter on default settings. You will then get another menu. At the bottom the first colored box[left to right]  is marked visparted in small letters. click on it.

You will then get a display of your partitions. **DO NOT** go near the one marked **ntfs**. Go down to ext3 and delete it. Go down to swap and delete it. You may or may not have to delete the partition called extension. It won't hurt to try it.

Now that you have deleted the Linux part of your hard drive, you can resize your Windows XP partition[ntfs]. 

You want to resize it all, I guess. The Linux partitions are now listed as unallocated. And you will resize Windows XP from  that unallocated space.

Now you have lost your ability to boot Windows XP! You can try to reboot but I am sure you will get a grub 22 error!

NOTE:If you can get your hands on a Windows XP CD,  it does have a repair option. If you choose the repair option, you will get a command line. From it you can enter "fixmbr", and that should restore your Windows XP boot.   If you can't get a copy follow step 3.




**Step 3**.From the **Super Grub Disk** boot. choose super grub disk in your language. You will get some text instruction. I would read through it. Eventually you will get to another window. Choose Windows XP. You will get a choice of restoring the mbr to Windows XP and choose that. Get out the cd after you have done that. remove the cd. You may have to reset your boot up options. Boot your computer and you should have Windows XP back.

You can also boot Windows XP by using** Super Grub Disk**. You will see that option in there.  


Best of Luck

Keep those two disks that you created. They can come in handy later on.

---

