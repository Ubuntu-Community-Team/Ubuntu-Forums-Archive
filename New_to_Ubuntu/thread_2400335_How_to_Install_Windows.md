---
title: "How to Install Windows"
date: 2018-09-05
forum: New to Ubuntu
---

### Post by bobgrey1997 on 2018-09-05
First, I am very new to all of this, so sorry if this has been done time-and-time again. I tried searching the web for this, but I got quickly lost...

I just installed Ubuntu a few hours ago, which I replaced my old Windows 10 with. I am not sure of the exact version, as I don't really know how to check...
Many games and programs that I have, however, only run on Windows, so I want to set up a Windows system with it. From my web searches, it seems that what I am trying to is called a "subsystem" that I can set up to run Windows. I found something called "Qemu" (I think it was called).
I really don't understand the whole "Terminal" system (I know how to get to it, and I understand *what* it is, I just have no idea what any of the commands are/mean).
So, my question here is;
Does anyone know of a good step-by-step guide on how to set up a Windows "system" on Ubuntu?

I have 8GB of RAM, 1TB hard drive, and an NVidia GT610 (not the best, I know) in case that information is useful, and I really don't know what else, so if more info is needed, please let me know (as well as how to find it)

For the record, Wine did not work as needed, I tried. Many programs require Windows, not just a program that act like Windows (for example; Paint.Net).

Thank you.
Any help/advice is greatly appreciated!

---

### Post by sporksrule on 2018-09-05
Try VirtualBox: [https://itsfoss.com/install-windows-10-virtualbox-linux/](https://itsfoss.com/install-windows-10-virtualbox-linux/)

If you need guidance on commandline usage feel free to private message me, or see this intro to commandline: [https://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything](https://lifehacker.com/5633909/who-needs-a-mouse-learn-to-use-the-command-line-for-almost-anything)

---

### Post by yancek on 2018-09-05
The link below explains how to  first download and install VirtualBox on Ubuntu and then install windows, specifically 10 but the process should be the same for any version of windows.  If you don't understand the process you can always post a specific question here.

[https://itsfoss.com/install-windows-10-virtualbox-linux/](https://itsfoss.com/install-windows-10-virtualbox-linux/)

---

### Post by oldfred on 2018-09-05
Most that game want dual boot, as vitualbox works, but just is not quite as fast.
If new system, you probably have to buy a new license for Windows a virtual installs are not allowed by Microsoft using your OEM license. 
       Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key) 

If dual booting.
You first need to know if UEFI or BIOS system and then if you installed Ubuntu in UEFI or BIOS boot mode?
And Windows only boots from MBR partitioned drive with BIOS and only from gpt partitioned drive with UEFI.
How you boot install media, UEFI or BIOS, is then how it installs. If system newer (last 5 years) & UEFI, then it should offer to boot install media in both modes.

Post this which will show partitioning:
sudo parted -l

---

### Post by oldrocker99 on 2018-09-05
Or, you can back up your /home folder, and reinstall Windows. Then, install Ubuntu besides Windows. Either one then runs with the full power of the computer, unlike using VirtualBox (which definitely is a fantastic tool) . You do **have to** install Windows first. Once that is done, when you boot, Ubuntu will be the default OS. Windows is selectable from that menu. If you don't select Windows, Ubuntu will boot in about 10 seconds, or when you hit Return.

Good luck. I really do think that this would be a pretty good solution to your problem. 

Good luck!

---

### Post by bobgrey1997 on 2018-09-05
Okay, so I just came back to check up on this thread, and was quite surprised with the amount of responses already! Thank you all for responding.
So, if I understand correctly, my best option would be rather than install Windows on a virtual system (which is like a system INSIDE a system, right?), I should rather set up a dual-boot-system where I can choose which one to use upon booting the PC?

Two questions;
1: How do I actually go about doing that?
2: What about that Windows 10 bug? The entire reason I actually switched to Ubuntu was because Windows 10 has this bug (from what I can figure was first reported in the April 'Creator's Update') that would cause random background processes to hog disc usage, making the computer lock up and become unusable, sometimes for hours at a time. My hope with Ubuntu was that I can install Windows or a Windows "emulator" that would only affect it's specific files. If it has that bug, then it can only use "100%" of it's specified "disc", leaving the rest of my Ubuntu system perfectly usable. My worry is that if I set up a dual-boot, then I will always choose Windows upon boot as all of my currently used programs require it, then if I have that issue, my system will be locked up entirely.

---

### Post by yancek on 2018-09-05
If you want to install windows alongside a currently installed Ubuntu system, you should first make sure that you have either unallocated space on the drive or an ntfs filesystem partition on which to install windows.  When you install windows, you need to select the "Custom" install option so you can install to the unallocated space or the ntfs partition.  If you don't do that, it will overwrite everything.

Don't know what "bug" you are referring to but I expect you would get a lot more information on it at a windows forum.

---

### Post by bobgrey1997 on 2018-09-05
I explained what "bug" in my posts.
"[COLOR=#000000]Windows 10 has this bug (from what I can figure was first reported in the April 'Creator's Update') that would cause random background processes to hog disc usage, making the computer lock up and become unusable, sometimes for hours at a time.[/COLOR]"
And, no, the Windows forums do not help. All they do is offer solutions that don't work or are only temporary. It is a known bug that Microsoft refuses to fix (there have been thousands of of reports on it, all with no permanent solution).

About the "ntfs filesystem partition", what is an ntfs and how do I set it up?

---

### Post by oldos2er on 2018-09-05
NTFS is Windows' default file system, I imagine when Windows is installed it will create this for you automatically.

If there are any files on the Ubuntu partition(s) you wish to keep, be sure you have an external backup medium to save them to, because when Windows is installed it will at a minimum destroy grub, Ubuntu's bootloader.

---

### Post by bobgrey1997 on 2018-09-05
Well, I have no idea how to create a partition or how to actually set up Windows on it. I also have no idea how to do anything using this... "terminal".

---

### Post by oldfred on 2018-09-05
Is your system less than 5 years old? If so then hardware is UEFI.
But you still can install in the now 35 year old BIOS boot mode.

Microsoft has very particular partition requirements for BIOS using MBR partitioning & if UEFI using gpt partitioning. 
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 
    
If you do not know what gpt, MBR, UEFI & BIOS are best to do some research first. Many links in link in my signature, but little about Windows.

---

### Post by deanr2 on 2018-09-06
I'd back another poster here and go with the dual boot.

1. Reinstall windows on the whole disk drive (deleting everything on it)
2. Install Ubuntu 'alongside' windows (the installation of Ubuntu offers this option whereas the installation of windows does not)

This is by far the easiest way to have both operating systems fully functioning on your computer without the need to access any terminal or other programming.

---

### Post by mastablasta on 2018-09-06
> **bobgrey1997 said:**
> . Many programs require Windows, not just a program that act like Windows (for example; Paint.Net).


which programs do you need? have you tried searching for and using alternatives to them?

do you game? What exactly do you use the PC for? is it just web browsing or office work?

setting up dual boot is easy but requires some knowledge. same goes for virtualbox install.

---

### Post by bobgrey1997 on 2018-09-06
Alright, my issue with dual boot is can I run the computer with both system ACTIVE at the same time, or do I have to choose which system to use when booting?
I don't want that. Windows has that disk usage bug I'm pretty sure I explained here that locks up the system, so I don't EVER want to run Windows as the primary.

As for which programs; there are no good alternatives to Paint.Net. The only thing similar I found on Ubuntu was Pinta, but it doesn't work (it crashes every time I open an image). I am currently using a program called "krita", but it doesn't have hardly any of the same functionality (it feels more like Gimp, which I hate).
Another program that requires Windows is a software released by SCS Software with some of their games. The games themselves run on Linux just fine, but the Editor that comes with it does not operate on any system other than Windows.

I primarily use my PC for game and game modding (I spend more time tearing the games apart and attempting to mod them then I do playing them).

What I want is a method to install Windows on my Ubuntu system (not the other way around) in such a way that I boot up the computer as Ubuntu, but can use Windows on it.

The most promising suggestions I had seen so far are a virtual machine or a partitioned disk, but I honestly have no idea how to either.
And no, I have absolutely no programming experience other than rerouting files in games.

It turns out, I do need a new hard drive (Ubuntu has this nice diagnostic thing that is telling my 1TB hard drive "is likely to fail soon"), so I will try to use Windows 10 on my new hard drive with the hope that this bug won't be as severe (whenever I manage to afford it).
Thank you for any help/advice

[EDIT]:
I had seen someone ask about system age.
I got the computer in December 2015, new (to my knowledge).

---

### Post by Mark Phelps on 2018-09-06
In terms of your latest post, with dual-boot, only only run ONE system at a time;  You have to reboot to run the other system.

In terms of the virtual solution, you still have to install Win10 to run it, so if your PC is victim to this "bug", that will be the same after you reinstall Win10 using Virtualbox -- because it's the same hardware underneath.

Also, as pointed out, your preinstalled Win10 OEM license will not work to activate a new copy of Win10 installed in Virtualbox.

---

### Post by mastablasta on 2018-09-07
> **bobgrey1997 said:**
> 
As for which programs; there are no good alternatives to Paint.Net. The only thing similar I found on Ubuntu was Pinta, but it doesn't work (it crashes every time I open an image). I am currently using a program called "krita", but it doesn't have hardly any of the same functionality (it feels more like Gimp, which I hate).
Another program that requires Windows is a software released by SCS Software with some of their games. The games themselves run on Linux just fine, but the Editor that comes with it does not operate on any system other than Windows.

I primarily use my PC for game and game modding (I spend more time tearing the games apart and attempting to mod them then I do playing them).


GIMP is image manipulating program it is not made for drawing. depends on what you are doing it might or might not be too complex. there are plenty of image manipulating programs available for professional and home use.

gaming and games are a different matter. they are usually made to work in specific operating system. usually that means only windows, but lately linux versions of some games are out there as well. so usually various hacks are needed to make them work under linux.  like tricking the software into thinking it's running on windows by providing it reverse engineered libraries (wine).

this means that for PC gaming or game editing the best operating system to use is still Windows. It will cause the least issues. with the proper version of the OS the upgrades can easily be postponed until a fix is available. it's bad that home version uses forced upgrade, but on the other hand most home users never upgraded their OS before and were recruited into botnets.

virtualbox is usually not a solution for gaming or running editors.

---

### Post by yancek on 2018-09-07
> The most promising suggestions I had seen so far are a virtual machine  or a partitioned disk, but I honestly have no idea how to either.

Based on this statement of yours, the best thing for you to do is to use virtual software.  Installing virtualbox and then installing windows 10 is explained in detail in the link I posted above in post # 3.  Not sure what more you would need.  As has been explained by others, using a partitioned disk with both systems on separate partitions will always require a reboot to access the other system.

---

### Post by Geoffrey_Arndt on 2018-09-08
Just to be clear Mr. Gray . . . . partitioning a disk is just creating a reserved place for an Operating System or its supporting files. This is also the basic first step of setting up a Dual-Boot PC Operating Systems (Windows 7, 10, Linux or BSD (Unix)). All require their own partitions with a file system that is compatible with each OS.   You cannot run OS's simultaneously unless you use virtualization (Qemu, KVM, Virtual Box, VMWare, Boxes, etc.).   

With your hardware, running a game machine using Virtualization is not going to be a good experience.   By the way, an easier way to learn about these things for many folks who are not prolific readers, is to use sites like youtube to search for tutorials on "dual-boot linux and windows" or "how to use gparted to partition a disk" , , etc. etc.

Bottom line - - there is no magic pill to remedy your situation.   Only work and much planning will do it.

---

### Post by bobgrey1997 on 2018-09-08
> **Mark Phelps said:**
> In terms of your latest post, with dual-boot, only only run ONE system at a time;  You have to reboot to run the other system.

In terms of the virtual solution, you still have to install Win10 to run it, so if your PC is victim to this "bug", that will be the same after you reinstall Win10 using Virtualbox -- because it's the same hardware underneath.

Also, as pointed out, your preinstalled Win10 OEM license will not work to activate a new copy of Win10 installed in Virtualbox.
Well, I am attempting to follow that tutorial, and I got to the point where I "add new optical drive" and select my Windows 10 iso, then click "Start", but it gives me this error
[img]https://i.imgur.com/GMPiU0ol.png[/img]
I think I broke it.

---

### Post by bobgrey1997 on 2018-09-09
...so, there is no solution to this...?

---

### Post by yetimon_64 on 2018-09-09
> **bobgrey1997 said:**
> ...so, there is no solution to this...?
Going by the error you posted in post #19 .... Have you tried rebooting into the BIOS settings screen and turning on (or confirming the status of) the AMD-V settings?

I had this problem many years ago when using virtualbox and got pretty much the same error you posted in post #19. It was easily fixed by booting into the BIOS screen and enabling the AMD-V setting (can also sometimes be called "Intel-VT" depending on your hardware supplier).

---

### Post by bobgrey1997 on 2018-09-09
I got it working.
Took me a while, and several restarts, to find the "Virtualization" setting, but I finally found it and enabled it.
Thank you all for the help.

---

