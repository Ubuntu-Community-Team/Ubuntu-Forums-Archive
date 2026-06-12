---
title: "Cd/DVD burner"
date: 2015-02-14
forum: New to Ubuntu
---

### Post by rod52 on 2015-02-14
Question, is brasero what I would use to burn files to.  I ask, because every time I try to put in a disk to copy jpg files, Brasero defaults to wanting to burn iso files.  Its as if Ubuntu does not see the disk.  I tried both DVD and CD disks. So how do I know if Ubuntu sees the disk?  Also tried in settings to set application defaults to know what to do when a blank disk is installed.

---

### Post by deadflowr on 2015-02-15
A blank disk will show up in the launcher if it can be accessed.
Also, brasero should allow you to toggle the disk to burn.
(typically where it says the location "/home/you/brasero.iso, you should be able to toggle it to the disk, if the disk is burnable.)

But, yep brasero is the default burner program for Ubuntu.
It's fine when it comes to burning data files and iso's, but that is about it.

If you find it lacking, you might try k3b,
Though, like all kde apps, it'll bring in a bunch of kde dependencies.
But that's really just a bunch of hard drive space bloat, and besides, it's a really great burner program.

---

### Post by Bucky Ball on 2015-02-15
Or try xfburn, which doesn't drag in a heap of KDE dependencies. Works for me.

---

### Post by SayakBiswas on 2015-02-15
Try the softwares k3b and acetoneISO, together they will solve all your CD/DVD/ISO/imaging problems............I have found brasero to be pretty buggy.

---

### Post by rod52 on 2015-02-15
Thanks for all the replies.  I will try all to see what works.  But I am starting to believe Ubuntu is just not seeing the disks.  No popups etc to ask what to do with the disks etc.  Tried putting in both a disk with data and a music cd...nada.  The disks are not being seen, or its the cd drive which is fairly new.

---

### Post by deadflowr on 2015-02-15
> **rod52 said:**
> Thanks for all the replies.  I will try all to see what works.  But I am starting to believe Ubuntu is just not seeing the disks.  No popups etc to ask what to do with the disks etc.  Tried putting in both a disk with data and a music cd...nada.  The disks are not being seen, or its the cd drive which is fairly new.

Well, several things you can try would be to open up the Files program and look at the Devices section in the left pane area.
when you put a CD in the drive, if the disk can be read, it'll show in this section.

You can also look at what it shows in the program called Disks (or sometimes called Disk Utility)
It should have few items listed in it's left pane, one being the CD drive. If you click it the contents will show in the main window.

Either may or may not give you some good info about why it's not working like you think it should.

---

### Post by rod52 on 2015-02-16
Have not tried other burners yet. I wanted to perform some tests.  The disk utility does see the disk.  But there is no popup when I insert the disk. The only option in the disk utility seems to be erasing disks.  Could this be a permissions setting?  When I go to dev/cdrom, permissions are set to root. Or am I even looking in the right area?

---

### Post by rod52 on 2015-02-28
Burner software is not the problem. To verify, I booted using a live disk. When running from the live disk, I put in a dvd in another drive, I get the popup message asking what to do with it.  I tell it what to do such as open in file manager, and it does. I get the same message when installing an SD card.  So all is good from the live cd. I have two cd/dvd drives.  Both work when running from a live cd.  When running Ubuntu normally, nada, no popup messages asking what to do with cd's or SD cards. Anyone have any ideas, permissions, settings etc?  I hate to try and fix it re-installing the OS not knowing what the issues was.  There are no guest accounts.

---

### Post by deadflowr on 2015-02-28
Open up the program called "Details"
Go to removable media and see what they are set at.
Normal would be Ask, but it can be set to any of the others.
I think if at one time you clicked on a check box when it came up with a notify, it might have set it to Do Nothing.
You can try re-setting it here, if that was ever the case.

---

### Post by rod52 on 2015-03-01
No go. Thats not it.  Is it possible the system, meaning mother-board etc could be failing?  This was a Win XP machine that was having boot up and time keeping problems. If the machine was shutdown. Sometimes when started up, it forgot the time and year.  Sometimes it would not start. I would have to leave shutdown and unpludded over night before it would start. Because XP was no longer supported, I installed Lubuntu then switch hed Ubuntu.  The time keeping issue seemed to be resolved, but not the start up problem. I tracked it down to what I think was the power supply.  I had one, so I switched power supplies. That so far seems to have resolved the startup issues.  I know was able to burn cd's etc.  But after the switch, none of the peripherals work. I know the I seen by the OS.  I just don't get the popup messages I should.  So, could it be the processor etc.?

---

### Post by rod52 on 2015-03-20
This is my last shot at this. Running from Mint 17 KDE live cd resolves the problem. No matter what I insert, I get the expected popup. Running from Ubuntu live cd, exactly the same problem as if I was running Ubuntu normally. No popup. This is not a brasero problem. Does this give anyone an idea?

---

