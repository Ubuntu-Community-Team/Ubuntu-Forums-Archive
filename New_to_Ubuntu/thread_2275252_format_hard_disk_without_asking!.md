---
title: "format hard disk without asking!"
date: 2015-04-25
forum: New to Ubuntu
---

### Post by aleeomran on 2015-04-25
Hi, i'm new to Ubuntu 14.04 , i installed it using USB stick. but after installation i found the hard disk is clean! all my stuff on it has been lost. 
i didn't give permission to that, i wasn't asked for it. also i found that the hard drive is a one large partition now, before i install Ubuntu i there were 5 partitions!
while installation it asked me wether to install Ubuntu with Windows 7 or remove win 7 , i chose to remove win 7. and also check the box for installing LVM, that's all.

may be getting the Data back is impossible but i just want to understand, what this is.

thanks in advance

[IMG]https://www.dropbox.com/s/5n4ccg3c8np6ukq/Screenshot%20from%202015-04-25%2008%3A34%3A42.png?dl=0[/IMG]

---

### Post by coldraven on 2015-04-25
AFAIR the installer gives you three options.
1) Install alongside Windows. For this to work you would have to previously made some space on the disk which is best done using while Windows.
2) Use the whole disk. This will delete everything and unfortunately this seems to be what you did.
3) Something else. This takes you to the disk partitioner screen where you can manually select or modify the partitions. You would need to be confident that you knew how to do this or have searched online for a tutorial.

Installing any OS is potentially dangerous and can lead to data loss. You should always backup your data to an external device before doing a major alteration to your computer.
Sorry about that. I hope that in the future you will look back and see this as a useful experience in data management.

---

### Post by Bucky Ball on 2015-04-25
Welcome. Stop using the disk immediately and see these two links:

Testdisk description:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Photorec description:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

And as above: ALWAYS backup any valuable data before an install or resize of partitions. But I guess no-one ever needs to tell you that again! ;)

Good luck and let us know how it goes or if you need some further pointers.

---

### Post by user_of_gnomes on 2015-04-25
> but i just want to understand, what this is.


[IMG]http://i.stack.imgur.com/xaQ3N.png[/IMG]

Are you saying you didn't get to see that menu? Because it has clear warnings and a clear explanation of what is going to happen. Did you install it through some other means?

Alternatively, it might have looked like [this]("http://pad3.whstatic.com/images/thumb/e/ec/Install-Ubuntu-Linux-Step-7Bullet1.jpg/670px-Install-Ubuntu-Linux-Step-7Bullet1.jpg").

---

### Post by aleeomran on 2015-04-25
> **user_of_gnomes said:**
> [IMG]http://i.stack.imgur.com/xaQ3N.png[/IMG]

Are you saying you didn't get to see that menu? Because it has clear warnings and a clear explanation of what is going to happen. Did you install it through some other means?

Alternatively, it might have looked like [this]("http://pad3.whstatic.com/images/thumb/e/ec/Install-Ubuntu-Linux-Step-7Bullet1.jpg/670px-Install-Ubuntu-Linux-Step-7Bullet1.jpg").

i understood that it will remove all data only on the (C:) system partition, like i used to with windows
it is a hard lesson anyway, thanks

---

### Post by aleeomran on 2015-04-25
> **Bucky Ball said:**
> Welcome. Stop using the disk immediately and see these two links:

Testdisk description:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Photorec description:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

And as above: ALWAYS backup any valuable data before an install or resize of partitions. But I guess no-one ever needs to tell you that again! ;)

Good luck and let us know how it goes or if you need some further pointers.

I extracted testdisk and photorec successfully but they don't open
I click on their icons with no response!

---

### Post by coffeecat on 2015-04-25
@aleeomran, just to clarify what went wrong for you, the important thing is that you installed using LVM. The installer would have presented you with the alternative screen that user_of_gnomes linked, not the one you've quoted from their post. Have a look at user_of_gnomes link and compare it to this:


[img]http://ubuntuforums.org/attachment.php?attachmentid=261516&d=1429955668[/img]


Rather than "multiple operating systems" or XP Professional as in user_of_gnomes link you would have had "Windows 7" or similar. The installer scans your system and describes it according to what it finds, but it gives you the same 5 radio button choices with two greyed out and "Install Ubuntu alongside..." ticked as default. To choose LVM you would first have had to tick the "Erase disk and install Ubuntu" button to get a screen like this with the Encrypt and LVM choices now available:


[img]http://ubuntuforums.org/attachment.php?attachmentid=261517&d=1429955686[/img]


Finally you would have ticked the LVM button:


[img]http://ubuntuforums.org/attachment.php?attachmentid=261518&d=1429955694[/img]


You may have ticked the encrypt button as well, but that would have made no difference to what you experienced. What is important is that you ticked a button that said "Erase disk..." and which also had a more detailed warning. As you say, it is a hard lesson learnt, and most of us have done something similar at some time.

I'm sorry you've had to learn this lesson and you may still be able to save some data from the links that Bucky Ball posted. Best of luck.

[ATTACH=CONFIG]261516[/ATTACH] [ATTACH=CONFIG]261517[/ATTACH] [ATTACH=CONFIG]261518[/ATTACH]

---

### Post by coffeecat on 2015-04-25
> **aleeomran said:**
> I extracted testdisk and photorec successfully but they don't open
I click on their icons with no response!

You must run testdisk and photorec from the live USB session, not from your installation. Also, they are terminal apps - the instructions are in Bucky Ball's links. Here is a more user-friendly howto, but it is very dated. The method of installation of testdisk/photorec refers to Ubuntu versions from about 2010, but the way of using these apps in the terminal is still valid. Testdisk is still in the Ubuntu repositories, so you can install it in the live session. Don't download stuff. Use it in conjunction with Bucky Ball's links.

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by aleeomran on 2015-04-25
Really thank you for the help guys.

---

### Post by oldfred on 2015-04-25
Please always attach screen shots, not post in line. Not everyone has high speed Internet.

Fix really only in 15.04, but they still have not made it clear the the default LVM install is always a full drive install. And with Linux a drive is the entire physical drive not a partition as Windows "drive" may mean.

       Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions.
this bug was fixed in the package ubiquity - 2.18.8.3 jan 2015
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by bob.innes on 2015-05-12
Almost had same thing.  Whew. But now verrrry nervous about Ubuntu. 



I tried the sourceforge installer friend suggested. Didn't work - said 'modified or corrupt kernel image'. 
Poked around and found  14.04 release notes which said "Automatic install is broken on drives that contain partitions that either do not have an operating system installed (eg. a user data partition like /home on Linux or D: on Windows), or partitions that have Windows 8 installed. Selecting automatic install (or upgrade) on these systems will result in the whole drive being wiped and all existing data will be lost. " 
Since I do have a Windows drive D, that last bit got me very worried about losing everything- again!  
So I went back to ubuntu and found they have a newer release 15.04 which seemed to have solved this prob per release notes.
This time i downloaded the 15.04 iso (32 bit) and used their suggested installer (pendrivelinux.com). 
Worked but then I got worried again.  It only gave 8 seconds to read the menu (which included an install option - but on what? Didn't say). Fortunately the default is for trial/ not-install which got ubuntu up on the screen. Poking around, I noticed that there is an icon to install ubuntu but without any other words i could only assume they mean install OVER WINDOWS ON HARD DRIVE!!! Yikes.  
I also noticed that when I mounted the hard drive it did NOT detect a partition - I previously partitoned the drive in half so it should have shown two hard drives of 40 gb each.  I therefore have to conclude that the warning given for 14.04 will also apply to 15.04.  Yikes again.  

The screenshots above suggest that warnings are given but... I sometimes get sloppy/ hasty/ fat fingered and will definitely remove the desktop icon once I get the USB install working.  But I have to suggest that the icons and boot menu are reworded to state exactly what drives will be altered.  

Ultimately, I'd like to install ubuntu on the windows drive D with a bootloader menu so I can choose which to run, with auto default to ubuntu.  I don't want to get my XP screwed up so I hope to keep generated files separated by OS or on external drive only.  First I need to gain confidence by making / using USB only installation. 

Even better, I have a really old machine (Pentium 3 with 511k ram, Win98) I'd be willing to try - wouldn't matter if Ubuntu overwrote Windows, but it can't boot from USB. The Ubuntu page mentions starting from CD but following their link, it only mentions DVD, which the old machine doesn't have. 
Also, the installer asked how much room to allow for 'transferring stuff between sessions' or something like that, which I think i set to about 800mb (based on Puppy having a savefile and/or swap system of similar size).... which would have to be reset for the smaller older machine?

My apologies to moderator for adding this to an older thread so if you'd like it to be a new thread, please advise or just move. 
Thanks in advance
PS Running Dell Latitude E6500.  Experience: basically noob but did try Puppy a few years back.

---

### Post by coffeecat on 2015-05-12
@bob.innes, if you need help, please start your own thread, stating clearly what it is you want to achieve.

I have removed the startling number of font and font size changes from your post. They gave me eye strain. Please use the default font and colour except where you need to highlight something. And grey? The text defaults to black if you leave it alone, which is much more readable.

---

### Post by Geoffrey_Arndt on 2015-05-12
Well, just a few comments . . but also you should wait for additional feedback from other forum members:

a).   You've made a few incorrect assumptions about how the installer works.   In general, it's best to install with the "something else" option as then you can see exactly what drives and partitions are going to be modified based on YOUR selections.  The install "alongside" and the install "using whole disk" may seem simpler, but give you less control.

b).   Re the older PC - - good idea to start there, and no, you do not need a USB flash-stick or DVD.   A CD will work fine, BUT . . . . you'll need to install a lighter version of Ubuntu (namely Xubuntu or Lubuntu) which WILL fit on a standard CD.   I actually prefer Xubuntu on older hardware, and like it's defaults better than Lubuntu (although each can be highly modified).   Lubuntu might even be slightly faster.   Forget about Ubuntu on the older PC.

The Ubuntu wiki (user documentation) is pretty good about describing the various install methods - - bottom line, Ubuntu (and it's cousins) are very reliable and stable IF you do a little homework first.

---

