---
title: "[SOLVED] Dual Boot on Dual Hard Drives?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by E.T.Smith on 2008-09-02
Two hard drives, one machine. How do I go about setting things up so one HD keeps its WinXP install, the other gets Ubuntu, and I can switch between the two? I've searched for a how-to, but all I can find are instructionals on partitioning a single hard drive.

---

### Post by anewguy on 2008-09-02
I did the same on my machine.  Basically, with Windows already installed, just put in the LiveCD and do the install.  In the installation process where it asks about partitioning, just choose manual and in the process for that switch to your other hard drive.  Ubuntu should install to it, and if your Windows drive is your "boot" drive, it should put the grub boot loader there with an option for Windows.

This is all I did - perhaps others have other ideas.

Dave :)

---

### Post by E.T.Smith on 2008-09-02
I first have to attach the prospective-ubuntu HD as slave to the Win one, correct?

> ...if your Windows drive is your "boot" drive, it should put the grub boot loader there with an option for Windows.

I'm a little unclear on this. The installation will automatically add an option that lets me choose which op system to load on start-up, is that it?

---

### Post by anewguy on 2008-09-02
Yes, you'll need the drive you want to use for ubuntu connected - mine is slave on the IDE bus where the Windows drive is the master.

It will add grub to the mbr, which means it will boot up using a Linux process that has a configurable menu for booting - in your case it should provide choices for Windows and Ubuntu when you finish the install.

Dave :)

---

### Post by E.T.Smith on 2008-09-02
Will this install keep the Win and Ub' drives isolated? That is, Win, won't use space on the Ub' drive and vice versa?

---

### Post by MasterSander on 2008-09-02
yeah, the only thin added on your win drive is the boot loader, which is about 40 mb

---

### Post by E.T.Smith on 2008-09-02
> **anewguy said:**
> In the installation process where it asks about partitioning, just choose manual and in the process for that switch to your other hard drive.  Ubuntu should install to it, and if your Windows drive is your "boot" drive, it should put the grub boot loader there with an option for Windows.

Going back to this part, will the option be presented in clear language like "installer detects two Hard Drives, 20GB and 40GB. Install Ubuntu to which?" or some crazy linux code I need to know beforehand?

---

### Post by philinux on 2008-09-02
Top right on this screen shot. You can toggle the drives.

You want Windows on sda  and then linux on sdb.

I've got Ubuntu on sda and intrepid on sdb

---

### Post by bumanie on 2008-09-02
No there is not any 'crazy' codes to know - you will be presented with a GUI that's fairly simple to follow and understand, although all this is a bit daunting the first time - but we were all there once. The windows drive should be designated sda and the (slave) ubuntu drive will be sdb. As long as you ensure anything you do is done to sdb, nothing will happen to windows on sda. It is a good idea to setup 3 partitions, two are mandatory  - / and swap the third you should setup is /home. / should be 8-10gb swap 1-2gb and /home as large as you like. Having a separate /home is advantageous if anything ever goes wrong with / you can reinstall to / and all your data is safe in /home. If your slave drive is 20gb - cut / down to 5-6gb.

---

### Post by E.T.Smith on 2008-09-02
> **philinux said:**
> Top right on this screen shot. You can toggle the drives.

You want Windows on sda  and then linux on sdb.

I've got Ubuntu on sda and intrepid on sdb

The image is the installation screen I'll be presented with? It doesn't show an "sdb", but I assume mine will?

> **bumanie said:**
> The windows drive should be designated sda and the (slave) ubuntu drive will be sdb. As long as you ensure anything you do is done to sdb, nothing will happen to windows on sda. 
To clarify, are the sda/sdb designations something I'll have to define during the process, or will they be automatically recognized and thus I'll only need to highlight them (or whatever) when I see them?

> It is a good idea to setup 3 partitions, two are mandatory  - / and swap the third you should setup is /home. / should be 8-10gb swap 1-2gb and /home as large as you like. Having a separate /home is advantageous if anything ever goes wrong with / you can reinstall to / and all your data is safe in /home. If your slave drive is 20gb - cut / down to 5-6gb.
I'm afraid you've slipped too deeply into code-speak. I get the jist, but the process is unclear.

---

### Post by gary0 on 2008-09-02
The easiest way I found to do this whilst keeping both installs seperate (including the grub loader), is to firstly disconnect your windows drive, set the second drive up as a master, install ubuntu on that, reconnect the windows drive and set the ubuntu drive as a slave. During boot up, you press F11 (in my case - yours may differ), this brings up a boot menu from the computers BIOS, select which drive you want to boot from.

The advantage here is that grub is _NOT_ loaded onto your windows drive, so if you ever need to re do windows, you can do it with gay abandon and it will not affect the ubuntu install as it wont over write the grub loader (which is on the second drive).

Some will say otherwise, but I find that keeping both OSes completely seperate in all respects lends itself to trouble free computing.

Gary.

---

### Post by BeccyBug on 2008-09-02
With my current 'grubby' problems that is the way I would do it too - then you can  change which drive to boot to in the boot menu

---

### Post by anewguy on 2008-09-02
For simplicity, just go with the dual boot option and with the install installing the menu.  You won't need to go into your setup each time to change boot order, and you can go to back to a Windows only boot very easily - I detail this in a how-to in this forum, but for simplicity just download a program call mbrfix.  It will quite simply overwrite the mbr (master boot record) back so it boots Windows only.  But for now, if you are just starting out and have the drive to spare (which you obviously seem to), just do as I mentioned previously.  You will like the boot selection screen - it is very simple and very clear to use.  Just take that jump for now - you won't be sorry.  If you decide in the future you want to go back to booting just Windows, just post back or private message me on this forum and we'll have you back very simply.

Dave:)

---

### Post by ajgreeny on 2008-09-02
Personally I think some of you are over-complicating things for a first timer in Ubuntu.
I would suggest you leave both disks attached to the computer and make the new Ubuntu one slave with the jumpers on it if needed.  I don't think sata drives have this extra requirement, but both my drives are ide so it's never bothered me to find out.  Go through the install to the partitioning point and choose guided.  Here you will see both disks listed as sda and sdb, and you should choose sdb.  Let the install set up partitions automatically.  Next time you install, and understand linux better you will be able to make new partitions as you wish, but I think for the moment it should be a case of "Keep it Simple"

---

### Post by anewguy on 2008-09-02
> **ajgreeny said:**
> Personally I think some of you are over-complicating things for a first timer in Ubuntu.
I would suggest you leave both disks attached to the computer and make the new Ubuntu one slave with the jumpers on it if needed.  I don't think sata drives have this extra requirement, but both my drives are ide so it's never bothered me to find out.  Go through the install to the partitioning point and choose guided.  Here you will see both disks listed as sda and sdb, and you should choose sdb.  Let the install set up partitions automatically.  Next time you install, and understand linux better you will be able to make new partitions as you wish, but I think for the moment it should be a case of "Keep it Simple"

That's exactly what some of us are trying to do with the install/manual partitioning.  Nothing special, no need to change anything at boot, etc..  I hope the user follows my initial advice - he won't be sorry and it's the simplest way to get there.

Dave :)

ajgreeny - we're of one mind -> keep the process as simple and error free as possible to make the new user's experience as nice as possible.  Other things can follow after more experience is gained, but the focus should indeed be on keeping things as simple as possible for the new user!  Dave

---

### Post by E.T.Smith on 2008-09-02
"Jumpers"?

---

### Post by anewguy on 2008-09-02
> **E.T.Smith said:**
> "Jumpers"?

Just a way of saying set the Windows disk to the IDE master and the Ubuntu drive to the IDE slave - jumpers may be a bit of a misnomer as it depends on the individual drives being used as to what is needed or not needed to set a drive as master and another as slave.  In particular, with cable select there shouldn't really be much need with today's drives.

Dave :)

---

### Post by E.T.Smith on 2008-09-02
> **anewguy said:**
> Just a way of saying set the Windows disk to the IDE master and the Ubuntu drive to the IDE slave - jumpers may be a bit of a misnomer as it depends on the individual drives being used as to what is needed or not needed to set a drive as master and another as slave.  In particular, with cable select there shouldn't really be much need with today's drives.
The hard-drives are what I think is called "Enhanced IDE". Older design, I've been told. The jumpers are apparently a couple of little white caps that have to be moved around to get one designated as Master, the other Slave. This is a problem, as I can't find the combination that works. Ether I get a boot error message telling me no hard drive was detected, or Windows loads without recognizing the slave. Any hints?

---

### Post by gary0 on 2008-09-02
You don't ned to go into setup - just hit F11 and a boot menu appears. This is keeping it simple, it doesn't get any simpler than this. Trying to explain to a newbie how to edit the grub list, move things about in it, only adds to the confusion. If it is done the way I outlined above, you'll never ever have to edit the grub list, for example if you reinstall windows, cos as we know, reinstalling windows overwrites the grub list, and then we have to explain how to restore it. The new user will complain after reinstalling windows that he cannot boot ubuntu. More explaining required. If the windows disk dies, so does grub, can't boot ubuntu anymore. Doing it this way won't matter if windows goes belly up, you'll still be able to boot ubuntu.

Really, the way I do it works fine. Not saying it's the right or best way to do it, it just keeps thing very simple.

Gary.

---

### Post by bumanie on 2008-09-02
Should be marked on the hard drive or else look up the manufacturers site and it will be on there as to where to place the jumper/s. 
I'm at work so have to do things at times - sorry I left before - so to answer the sda/sdb question; Yes the GUI clearly differentiates the two for you and will have them designated that way. 
The thread has started getting a bit confusing with various ideas re set up. Suggest you look at all the information here and then google for some information and then decide how to proceed -stick with it, it will work out in the end. There are a number of tuorials on the internet. There is no right or wrong way to do things. The right way is the way you feel happy with.:)

---

### Post by anewguy on 2008-09-02
> **gary0 said:**
> You don't ned to go into setup - just hit F11 and a boot menu appears. This is keeping it simple, it doesn't get any simpler than this. Trying to explain to a newbie how to edit the grub list, move things about in it, only adds to the confusion. If it is done the way I outlined above, you'll never ever have to edit the grub list, for example if you reinstall windows, cos as we know, reinstalling windows overwrites the grub list, and then we have to explain how to restore it. The new user will complain after reinstalling windows that he cannot boot ubuntu. More explaining required. If the windows disk dies, so does grub, can't boot ubuntu anymore. Doing it this way won't matter if windows goes belly up, you'll still be able to boot ubuntu.

Really, the way I do it works fine. Not saying it's the right or best way to do it, it just keeps thing very simple.

Gary.

You're completely missing the point - just plain install, the grub menu is generated AUTOMATICALLY.  Let's quit arguing about this and let this guy get his installation DONE without throwing junk into the equation.

As a clarification to you, the grub list is NOT in the MBR - only a bootloading routine to get it started loading from a disk - in this case the Linux disk.  The actual grub menu is in your linux /boot folder.  

This whole thing has gotten WAY out of hand - let the person install using the LiveCD and the install process, just selecting the manual option so he can specify the drive he wants to install to.  Let's leave ALL this other stuff out of it because all anyone is doing is distracting from a straight-forward install and causing confusion.  Please, contribute to the direct train of this thread for a newbie and leave EVERYTHING else out - he doesn't need to worry about F11 or anything - just install and select either Windows or Ubuntu from the boot menu.  IF he has problems and needs to go back to stand alone Windows, information has already been posted - and HELP offered for a simple process.

---

### Post by ajgreeny on 2008-09-03
> You're completely missing the point - just plain install, the grub menu is generated AUTOMATICALLY. Let's quit arguing about this and let this guy get his installation DONE without throwing junk into the equation.

As a clarification to you, the grub list is NOT in the MBR - only a bootloading routine to get it started loading from a disk - in this case the Linux disk. The actual grub menu is in your linux /boot folder. 

This whole thing has gotten WAY out of hand - let the person install using the LiveCD and the install process, just selecting the manual option so he can specify the drive he wants to install to. Let's leave ALL this other stuff out of it because all anyone is doing is distracting from a straight-forward install and causing confusion. Please, contribute to the direct train of this thread for a newbie and leave EVERYTHING else out - he doesn't need to worry about F11 or anything - just install and select either Windows or Ubuntu from the boot menu. IF he has problems and needs to go back to stand alone Windows, information has already been posted - and HELP offered for a simple process.Thank goodness!  I thought I was the only one who was trying to make it simple and straightforward.  I remember back to my first install, when I knew little if anything about partitions etc etc.  I just popped in the liveCD and let the system do it all automatically.  If I'd tried to do then what I can do now without much worry or trouble, I would have ended up in a huge pile of mess.

As I said, "Keep it simple" and leave a separate /home, /boot, and so on to experts.

---

### Post by E.T.Smith on 2008-09-03
Installation completed, all works fine. Thanks to all for the help.

---

### Post by anewguy on 2008-09-03
You're very welcome.  I hope you find Ubuntu fun for you.  Sure, there are things that can be a challenge, but that's the case with anything new.

If you have any problems, questions, etc., please post back to these forums.  Also, don't be afraid to private message me through this forum.  I can promise you that if I don't know the answer and can't find one for you I will let you know so you can seek help elsewhere.

I'm no "expert", just someone who has had his own share of questions and learned a little along the way. 

You will find this community very willing to help as best they can - it's a great group of people who provide their time here!

Hoping you find Ubuntu fun and the right kind of fun challenge!

Dave :)

EDIT:  Please also use the "Thread Tools" selection and mark this thread as closed if things went ok.

---

### Post by anewguy on 2008-09-03
> **ajgreeny said:**
> Thank goodness!  I thought I was the only one who was trying to make it simple and straightforward.  I remember back to my first install, when I knew little if anything about partitions etc etc.  I just popped in the liveCD and let the system do it all automatically.  If I'd tried to do then what I can do now without much worry or trouble, I would have ended up in a huge pile of mess.

As I said, "Keep it simple" and leave a separate /home, /boot, and so on to experts.

I noticed the originator of the thread thanked me and has everything going.  I wanted to "spread the thanks" because you also were pointing out that my first posting covered what the user needed to do without all the side-tracking provided by others!

Dave :)

---

