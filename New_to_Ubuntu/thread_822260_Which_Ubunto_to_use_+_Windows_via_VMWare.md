---
title: "Which Ubunto to use + Windows via VMWare?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by HiddledyPiggledy on 2008-06-08
Hello Penguins!

I am thinking about switching completely over to Ubuntu as my main OS/shell. I have to have some windows apps for my CAD work.
I have VMware workstation (I can install it inside windows to run linux/ubunto, etc, and also a linux version to install windows inside of linux, etc)


I am slightly familiar with the VERY basics- some of my friends are linux users for many many years and I've watched them typing a lot of code overe the years (12-15 years of use, and they all swear by it); I made a firewall many years ago (10), out of our old 486dx, but it has worked so well (it has never crashed, and only needed to be restarted perhaps 3 times in 10 years due to some kind of cleaning out the cache? I forget) that I have even forgotten how to do that- we used a floppy and ran some commands as "root" and that's mostly all I remember -some switches and settings we just estimated and it was done- one edit a week or two later for the swap file or something (I think we changed a setting so that it would dump the log files on it's own after a certain amount of time or something)....It's run flawlessly since. 

Of course I've had probably 10,000 windows crashes and maybe 1000 re-ghostings and 300 HD reformats for my windows versions- LOL!

I know how to partition HD's and even edit HPA's and use DOS tools and I'm quite familiar with windows stuff, but NOT linux programming or editing- I don't even know what syntax to use- totally new in this arena. I'm guessing I need a fresh unpartition HD, and install my Linux flavor FIRST, (grub?) for possible dual-booting and then install my ubunto on the 1st partition... make it bootable (is that automated inside the install? I'll find out?)....

so...

Again, 
-I want to run Ubunto (I have the various install CD's I've DL'd) or some flavor of linux as my shell/main OS, and -use my VMware ("Virtual Machine Ware"-or something similar, I've got the windows and Linux workstation versions-) to
-run windows inside of it for now (I absolutely need some windows specific CAD apps for work),

....until I get more familiar with the Linux based apps to replace most of my typical windows user ones. 

* I must have windows on the machine with high-graphics capability for CAD stuff (does it matter if they have openGL versions? Is that relevant?). And ...
* I must use the windows based programs simply because of my professional work, and the software firms have not gotten savy enough to make a linux version yet it seems. 









Is it possible to do this? (I've got the ISO's on various CD's ready to go) 
What do I need to have and do to be ready to go outside of my fresh blank HD?

.......Were do I begin? Just stick the CD in, and make a partition, then install my VMware workstation for linux, right?



Thank you in advance.



p.s. I AM reading the FAQ's and combing the threads to learn what I can in the meantime, knowing penguins, all my questions have answers in the FAQ and other threads....
:popcorn:

---

### Post by abcuser on 2008-06-08
Hi,
there are several options you can use:
1. Use dual boot: Windows on one Windows partion and Ubuntu on another Linux partion. If you are used to installing it isn't too hard. Just insert Ubuntu CD and it will guide you through process - you don't need to create any partition, you don't need to make any room on Windows partition - all of this Ubuntu will make by itself, just insert CD and follow install process. If you are not 100% sure what you are doing at last install windows click "Cancel". ;)
2. You can use Wubi: Start Windows and insert CD. This will install Ubuntu under Windows as ordinary program it installs on Windows NTFS partion (install using one big file), but lets you give Windows/Ubuntu option at boot time - very similar to dual boot just install process is very very simple. Uninstall of Ubuntu is as simple as starting Windows and uninstall program from Add/Remove panel.
Disadvantage of first and second option is you can only run one OS by time. But you have full options like graphics will work the best this way.
3. Use virtual program like (VMware, VirtualBox etc). If you will have Windows as host and Linux as guest you need virtual program for Windows and vice versa. What option to use depends what will be time you will use Windows and Ubuntu. If you will use more Ubuntu, then install Ubuntu as host and vice versa. Just remember virtualization tools are not able to run some advanced graphics efects like Compiz in Linux.

If you would like to run Windows programs under Linux, you can use Wine. I suggest you to download wine-doors program from [www.wine-doors.org](www.wine-doors.org) which will simplify install of Wine programs. But don't forget installing Windows program under Linux is not a simple task, so you will probably need geek. ;)

If you are new to Linux and have valid license for Windows, I would suggest you to use Wubi (second option). It is easy to install and no trouble with Wine. But disadvantage is to use only one OS per time. So if you work with CAD program and DON'T need any other program at that time this Wubi option is probably the best one.

Regards,
Abcuser

---

### Post by xp2mac on 2008-06-08
I understand your hesitancy. I'm running VMWare on a Mac with Ubuntu and Windows - all at the same time. Really Great! And I'm getting ready to install Ubuntu on my Windows laptop in a dual boot mode, but might bite the bullet and install VMWare there as well (as my first choice).

To answer your question, I'm sure you don't need to create a new partition for VMWare. VMWare creates its own space in the Windows environment and increments it as needed. Separate partitions are only required for dual boot mode. But if you're picky and would prefer to keep VMWare separate from Windows, a separate partition would be useful, but I think WMWare is still going to use some space in Windows. After installing VMWare, you then start it up and add a new application, the application being your Ubuntu install disc. You will be prompted for the type of application and the source of the application. Should be that simple.

Installing Ubuntu in VMWare on Windows is the best way to go because you can take advantage of the data files in Windows through the VMWare shared folder.

But don't just take my word for all of this. Wait for a couple of other responses to get a confirmation - because I haven't done it yet myself!

All the best to you.

[QUOTE=HiddledyPiggledy;5139943]Hello Penguins!

Again, 
-I want to run Ubunto (I have the various install CD's I've DL'd) or some flavor of linux as my shell/main OS, and -use my VMware ("Virtual Machine Ware"-or something similar, I've got the windows and Linux workstation versions-) to
-run windows inside of it for now (I absolutely need some windows specific CAD apps for work),

---

### Post by drhpapagino on 2008-06-08
Greetings: Like you, I need Windows for various reasons and run Vista Ultimate.  (Don't tell anyone, but I actually like Vista).  I also have VMware installed and I love it.  VMware installs as a "normal" application in Vista, with some high level and sophisticated services.  Once installed I created a new virtual machine, following the wizard's advice for recommended settings.  After that it was a breeze to install an Ubuntu iso disk and run the Ubuntu installer.  Ubuntu loaded fine, opened with dhcp running (if you need that), and immediately needed dozens of patches, just like Windows! It was quite easy to learn my way around Ubuntu as it is well documented, and very friendly.  I also found Hagen's Ubuntu Linux Bible nicely written and useful.  This approach has given me an easy entrance to the world of Linux, without the grief of dual boot, and the necessary hardware issues linux would have to deal with.  VMware handles all the necessary hardware drivers, including graphic and sound quite nicely.  You will want to install VMware tools, however.  And that can be a challenge first time.  Vmware has a manual online you can download.  Consult the chapter on installing VMware tools using the command line.  Also, note that you do not use rpm installations in Ubuntu.  Use the tar approach.  This is spelled out in the manual.  The VMware tools make you transition back and forth between the two OS's quite transparent.  One final note, each time you updtae the kernel in Ubuntu you will need to reinstall VMware tools.  And each time you do your networking and mouse settings may get messed up. If you need advice there, just repost.  There is information available.  Good luck.

---

### Post by HiddledyPiggledy on 2008-06-09
Thank you for the quick responses!

I put in my unbutu 8 CD, after backing up my MBR and checking the ISO, and installed it. Totally simple. I did this on a HD that has 3 normal partitions and an HPA hidden at the end (thank you Dell, for helping me take on learning how to create and edit HPA's, something I always didn't want to know about- lol!). My windows root is the 2nd partition (C:) and the last partition is the restore DSR ("Goodell" is a great resource for windows partition information by the way)... the 3rd partition is an empty chunk on my drive. 

so far no issues, pending hardware.

I'm familiar with VMware's products and how they install and work. I already tried Ubunto 7 and 8 via that way, and that is what has prompted me to switch to Ubunto as my main OS. 

So I just got the latest linux version from them, and a new HD and I'm backing up my MBR and etc etc and I'll know by tomorrow how to do it and how simple (or not) it is and ought to be to install Ubunto on a Dell as the main OS (I didn't know till yesterday about the Dell linux resouces- check it out, anyone who is reading this thread : [http://www.dellcommunity.com/supportforums/board?board.id=sw_linux](http://www.dellcommunity.com/supportforums/board?board.id=sw_linux)
...)

So I'll use VMware to see if it is capable of coping with the my GPU load in 3dsMax and CAD apps... I heard that WINE isn't as good, but I'll try that out too, and sooner if necessary. 

Thank you for the help; hopefully this will go smooth!

:P

---

