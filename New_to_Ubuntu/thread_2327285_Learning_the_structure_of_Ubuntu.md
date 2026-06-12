---
title: "Learning the structure of Ubuntu"
date: 2016-06-09
forum: New to Ubuntu
---

### Post by dannymcgill on 2016-06-09
Probably not the best title for a thread, but it's all I could think of. I'm extremely curious as to how a Linux OS ( or any OS for that matter ) is structured and handles basic yet essential tasks. I'm fairly certain when I boot my computer the bios runs the bootloader such as GRUB or WindowsBootLoader ( if that's what it's called ) if I don't have Linux, and when you select the OS partition to boot from that's about where my knowledge starts to cut off. I run Ubuntu 16.04 with the default Unity environment, but I don't know how and when the Unity environment is loaded. If I decided to switch to Xfce yet still had Unity installed to swap between them, where is the file that stores the startup information such as the desktop environment? I'm also not understanding when hardware drivers are started and where they are located. I'm also confused as to the filesystem structure of Ubuntu specifically, although I have been looking around inside "Computer/". 

Basically I'm wanting to learn how the various Linux distros build off of the Linux kernel and where the kernel fits into them, as well as equip myself with information on the overall workflow a Linux distro takes to do things like load hardware drivers, load desktop environments, add/remove terminal commands, install software, startup application data, etc. My question in short is "Is there a book or series of books that would teach me this, or perhaps a wiki or site that I can learn these things from that anyone would recommend?". I have tried to learn them individually to an extent, the filesystem being possibly the only slight success I've had. It just seems that everytime I find a resource to learn something it ends up building off of another bit of information that I don't know and I end up traveling down what feels like a rabbit hole of information just to understand the thing I set out to learn. Which is fine if I felt like the rabbit hole would end...

Sorry if this is long-winded or too vague. I keep running into troubles with my Ubuntu setup and have done so for several years, uninstalling each time as I thought I was just inept at using it. I'm about to get into college for computer science and with Linux being such an important ecosystem to understand and develop on and for that I just want to get a running start on it ( even more so since I don't think the college I'm attending uses it at all in the curriculum so exposure would only be self-inflicted ) as to both aid in my future computer science endeavors and more easily debug problems I come across while using Ubuntu for general use ( which happens a lot ).

**Edit:** I'd also like to mention that I have checked out "Linux Kernel Newbies" in the past, but it seems to predominantly aim towards documenting the inner-workings of the Linux kernel itself and aiding those who are working on it. While it might have valuable information that I want to know, it just seems like there's an overflow of documentation but the only needlepoint of entry to understanding that information is to just hack away at the source code directly...unless I'm missing something there too.

---

### Post by ajgreeny on 2016-06-09
That is such a huge question that it is almost impossible to answer properly without writing a long treatise about the whole system, however, as a start, have a read through the Linux filesystem hierarchy info at [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview) and go to some of the links in that and you may find the whole thing starts to look a bit more comprehensible.

---

### Post by egeezer on 2016-06-09
You said: "Which is fine if I felt like the rabbit hole would end..."  It will never end.  If you finish learning all you can handle about the Linux kernel, you will still find you need to learn something about the architecture of computer systems, the information transfer characteristics of silicon chips, Boolean algebra, mathematics...

You are staring down the length of an endless road - take delight in the journey!

---

### Post by Geoffrey_Arndt on 2016-06-09
+1 for AJ & egeezers's posts.   You will find out very quickly (if you go the university CompSci route), whether or not this whole area of technology is "for you" . . . The PACE & complexity can be daunting unless one learns how to manage all that info.   Look into the concepts of Mind_Mapping so you can learn how to organize and structure information.   Learn the distinction between Inductive and Deductive methods of thinking . . (e.g., organizing info).   A person tends to prefer one of the methods over the other (a bit like "left brain .. right brain").    In other words, "learn how to learn" . . . that's what uni or college success depends on.

For the short term . . . this resource can help:   [https://linuxjourney.com/?utm_source=omgubuntu](https://linuxjourney.com/?utm_source=omgubuntu)

---

### Post by dannymcgill on 2016-06-09
Thank you all for the replies!

Checking out that first link that ajgreeny linked to along with the Filesystem Hierarchy Standard .pdf were invaluable and I've bookmarked them both. Much of my initial confusion seemed to stem from simply not knowing where terminal commands were being executed from and how new ones are installed. That along with not knowing where storage devices were being mounted and where the Linux kernel was located were all solved ( and then some ) by reading through those two links. There's of course tons of commands and their descriptions in the .pdf so I'll be referencing it as I go.

I'm right now on a website that talks about mind mapping and I'll be reading it throughout the day. If the technique helps me maximize what I learn more efficiently and retain/recall it better I'll be one happy guy. Also...that linux journey link seems simply amazing! I'll also be going through that as the days go by. Thank you two for giving me some amazing resources to start off with.

The next few months before uni will be filled with getting up to speed with the entire Linux ecosystem and anything else I can cram into my head before I begin classes. I'm obviously excited to start and this is yet another large chunk of the unknown I get to tackle.

---

### Post by Bashing-om on 2016-06-09
dannymcgilll Hello;

Here is my knowledge base:

During boot, a few things happen in order.
1) The BIOS/EFI finds the correct (read-only) drive to boot from
2) The BIOS/EFI reads GRUB from the correct drive, which explains the correct partition and file to discover the kernel and initramfs.
3) The BIOS/EFI loads the kernel and initramfs into RAM, and (effectively) turns control over to the bootstrap 'init' program in initramfs.
4) Bootstrap Init unmounts all (read-only) drives, creates the filesystem, remounts all drives read-write, and turns control over to the real /sbin/init.
5) /sbin/init begins probing hardware and starting the system we know.

Usually, a busybox prompt means that steps 1-3 were successful, but something in step 4 has failed. It may be unrelated to fsck or anything boot-repair can fix.
For example, a different OS on the same system may have overwritten /sbin/init. Or The hard drive may be failing. Or many other possible causes.
---------------
Here's an abbreviated version of what happens when you turn the power on after the machine has been shut down for a while:

First, code in the BIOS chip on the motherboard gets loaded into memory automatically and begins running. Next, the Power-On Self Test (POST) code checks all of the hardware to make certain it's working. In the process it clears all of the RAM space except the very small part it's using to run the POST.

When the POST completes, the BIOS code then begins loading the operating system code into memory. 1st stage boot loader (generally located in the hard disk's MBR) is loaded into ram; It's only job is to load stage 1.5 ->which is file system specific code used to find the operating system image on the "boot" file system <- into ram. This becomes a "chicken-or-egg" situation, since loading the code requires code to already be there and the BIOS chip isn't large enough to hold all of the necessary code. The solution, in most Linux distributions, is to create a pseudo-disk in RAM - through stages (1, 1.5 and stage 2), and load it with an abbreviated copy of the system that has all the things needed to load the full system, but nothing else (such as a normal user interface or keyboard drivers).

Thee core image modules know about the boot file system and can open the file system on the specified (at install time) partition. It looks for and loads modules there, including normal.mod; normal.mod loads the grub.cfg file and executes the statements, usually providing a menu to the user etc.

GRUB locates ALL of the operating systems installed on the drive and gives the user a screen to select which operating system is to be loaded. Once the user selects the operating system GRUB will pass control to the kernel of that operating system. Thus Stage 2 reads the configuration file, displays the menu, and loads and starts the selected OS.

When all the stages are loaded into ram and executing -> linux image and the initial ram disk (Temporary root file system) are loaded into memory. When the images are loaded, the 2nd stage boot loader passes control to the kernel image and the kernel is de-compressed and initialized. At this stage, the 2nd stage boot loader checks the system hardware, inumerates the attached hardware devices, mounts the root device and then loads the necessary kernel modules.
Once a boot option has been selected (grub's boot menu), grub loads the selected kernel into memory and passes control to the kernel.
Building grub:
GRUB 2 places its files in three core locations:
 /boot/grub/grub.cfg - This is the main configuration file, this file shouldnot be edited by hand!
    00_header is the script that loads GRUB settings from /etc/default/   grub, including timeout, default boot entry, and others.
    05_debian_theme defines the background, colors and themes.
    10_linux loads the menu entries for the installed distribution.
    20_memtest86+ loads the memtest utility.
    30_os-prober is the script that will scan the hard disks for other operating systems and add them to the boot menu.
    40_custom is a template that you can use to create additional entries to be added to the boot menu.

/etc/grub.d/ - This directory contains GRUB scripts (those listed above). These scripts are building blocks from which the grub.cfg file is built. When the relevant GRUB command is executed, the scripts are read in a certain sequence and grub.cfg is created.
 /etc/default/grub - This file contains the GRUB menu settings that are read by the GRUB scripts and written into grub.cfg. It is the customization part of the GRUB. The grub file is a text file that is parsed by the 00_header script. You can make your changes here, if you want.

--------------------
Back to the story:
That abbreviated copy is the "initrd.img" file, the INITial RamDisk IMaGe -that was loaded into memory by the stage 2 boot loader; having been copied into ram and mounted. initial RAM disk (initrd) is a temporary root file system that is mounted during system boot to support the two-state boot process. The initrd contains various executables and drivers that permit the real root file system to be mounted, after which the initrd RAM disk is unmounted and its memory freed. 
[[http://en.wikipedia.org/wiki/Initrd]](http://en.wikipedia.org/wiki/Initrd]) Good description.
 The initial RAM disk (initrd) is an initial root file system that is mounted prior to when the real root file system is available. The initrd is bound to the kernel and loaded as part of the kernel boot procedure. The kernel then mounts this initrd as part of the two-stage boot process to load the modules to make the real file systems available and get at the real root file system.Back to the story:
That abbreviated copy is the "initrd.img" file, the INITial RamDisk IMaGe -that was loaded into memory by the stage 2 boot loader; having been copied into ram and mounted. initial RAM disk (initrd) is a temporary root file system that is mounted during system boot to support the two-state boot process. The initrd contains various executables and drivers that permit the real root file system to be mounted, after which the initrd RAM disk is unmounted and its memory freed. 
[[http://en.wikipedia.org/wiki/Initrd]](http://en.wikipedia.org/wiki/Initrd]) Good description.
 The initial RAM disk (initrd) is an initial root file system that is mounted prior to when the real root file system is available. The initrd is bound to the kernel and loaded as part of the kernel boot procedure. The kernel then mounts this initrd as part of the two-stage boot process to load the modules to make the real file systems available and get at the real root file system.

The initrd contains a minimal set of directories and executables to achieve this, such as the insmod tool to install kernel modules into the kernel.
 In the case of desktop or server Linux systems, the initrd is a transient file system. Its lifetime is short, only serving as a bridge to the real root file system.
Once it's loaded, control goes over to it, and it begins loading the actual full system from the "vmlinuz" file. While all this is going on, you see only the splash screen (but you can edit GRUB's actions to see play-by-play reports of it all, if you want to).

When the full system is all loaded, and all complete,  control goes to the "init" process, which sets up the console and virtual terminals, loads the window manager and display code, and completes the high level initialization, and lets you log in. It is init's job to get everthing running the way it should be. It checks that the file systems are ok and mounts them. It starts up ``daemons'' to log system messages, do networking, serve web pages, listen to your mouse and so on. It also starts the getty processes that put the login prompts on your virtual terminals. The init process continues to run in the background until you shut down the machine, allowing the system to do its work more or less invisibly.

You can view the log of all this by firing up a text editor and looking at /var/log/syslog. This file records each significant event -- and gets huge in a hurry.
On Ubuntu 14.04.2, I have /etc/logrotate.d/rsyslog. This file handles many of the base log files such as syslog, mail, auth, etc; to control the rotation of most default system logs. 

I hope this helps answer your question, but it will probably prompt many more. Welcome to this wild and wonderful world!
More info:
[http://linoxide.com/booting/boot-process-of-linux-in-detail/](http://linoxide.com/booting/boot-process-of-linux-in-detail/)
[http://www.ibm.com/developerworks/aix/library/au-speakingunix_unixboot/index.html](http://www.ibm.com/developerworks/aix/library/au-speakingunix_unixboot/index.html) <-Speaking UNIX: Booting up
-------------------------

&&
Several things have to happen before we get to a desktop user interface in any Linux distribution. Different components have to over control and then hand over control to other components. And this is what you are seeing. At certain points the video signal to the monitor is stopped and then started again as one component handed over control to another component.

1) The motherboard Basic Input Output System (BIOS) does its tests and then l&#959;oks for an operating system to load. It finds the Boot Loader (Grub) and loads it.
2) The Grub boot loader reads its configuration files and looks for Linux kernel image to load. When it finds a Linux kernel image Grub stops working.
3) The Linux kernel image starts to load and looks for a video display server to load. It finds XServer and runs that and then continues to load Linux.
4) The XServer looks for a Display Manager to take the operating system from a Linux command line OS to a Graphical User Interface OS.
5) The Display Manager (Gnome Display Manager for Kubuntu. Light Display Manager for Ububntu and the other flavours) presents a graphic log in screen and hands over to the Desktop Environment with its User Interface.
6) The Desktop Environment is Gnome for Ubuntu; KDE for Kubuntu; Xfce for Xubuntu and LXDE for Lubuntu.
So there is a lot of handing of control from one component to another. This can be hidden by splash screens but not always. Oh, at some point a video driver compatible with the video adapter has to be used instead of the XServer's basic video display.

I am amazed that with all these components that are separate software projects the OS works as good as it does. And at a very agreeable price.

Regards (grahammechanical)

-----------------------

All this said ... This is a constant evolve-ing Sysystem. What was true yesterday may no longer apply. Case in point is the move now to the systemd initiate  system. A whole new ball game .

==================

By the way .. My introduction to Unix (linux has it's base from Uninx) was in college .

[INDENT][INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-06-09
With all due respect Bashing-om you have failed to convince me that it is not all done by magic. :)  It is all done automagically. That is all this user needs to know.

Linux distributions are special. They are not made by one monolithic, controlling organisation. A distribution is crafted from software components from many software projects. The method for developing Free & Open Source Software (FOSS) allows programmers to add code to other projects to improve (possibly) the project and to allow their own software project to integrate more efficiently with the other components. Such is the nature of FOSS development that programmers can always take the software source code and modify it into something similar but different according to their own vision.

And then there is the hardware to take into consideration. Linux developers have no control of the computer hardware that is being manufactured. And Linux developers do not limit themselves to one computer architecture or one product line. Linux runs on many types of computer architectures in many different computer devices. Any explanation of the processes involved in loading a Linux distribution on machines with Intel/AMD x86 CPU architecture would not necessarily be accurate in describing the processes for loading a Linux distribution on a mobile device with an ARM designed CPU.

If it not magic then why do explanations of the processes read like a magic incantation?  :)

Regards.

---

### Post by Bashing-om on 2016-06-09
grahammechanical; Agreed ...

The magic is that it happens at all .

[INDENT][INDENT]what a Wonder - full
[INDENT][INDENT][INDENT]thing we have here
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2016-06-09
"*Any sufficiently advanced technology* is indistinguishable from magic." - Arthur C. Clarke

---

### Post by dannymcgill on 2016-06-09
Wow...simply TONS of info right there Bashing. Thank you! Though you are right that now I'm just full of other questions that I'll have to make threads for. You've opened the flood gates!

I was getting a bit confused as to what was swapping with what in that order after a while, but the link titled "Linux Boot Process in Detail" that you posted had a visual and additional information that helped patch it all up for me. Knowing this though how does the flash memory's data on the motherboard not just vanish after system shutdown? Wouldn't that just ruin the whole boot process as the BIOS would no longer be accessible? Is there a special way that this is handled?

**Edit:** Also how does BIOS updates fit into this? I've heard of "flashing" before and I may have done a BIOS update at some point or another when it was suggested to do so to solve an issue I was having, but does this just wipe the previous BIOS from flash memory and install a newer version for the motherboard? I've updated firmware on my router before and it changed/added some features for me to utilize in the router menu, would this be very similar to performing a BIOS update? If you just wipe the BIOS off the flash memory and forget to install a new BIOS version, could you still get around to booting or is that motherboard done for?

---

### Post by Bashing-om on 2016-06-09
dannymcgill; Welp ....


[https://iam.tj/kb/pc/boot/#a_bootloader](https://iam.tj/kb/pc/boot/#a_bootloader)

Now think ... What is the primary function of bios ?

[INDENT][INDENT]it all starts, somewhere
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-06-09
You are back to hardware which was not your original quest. Do you know what RAM is? Well, have you ever heard of a ROM or an EPROM?

In the old days the integrated circuit or chip that hold the BIOS (Basic Input Output System) used to be a Read Only Memory chip. Once the chip had the information set in it no changes could be made. Then we got Erasable Programmable Read Only Memory chips. And the settings in them could be changed to a limited degrees and an updated program "flashed" on to it.

Please don't ask how transistors work.

Regards.

---

### Post by dannymcgill on 2016-06-10
Thanks, and I won't ask :).

---

### Post by Topsiho on 2016-06-11
I did not read through all of the very lengthy answers, and maybe is what I propose here not what the OP asks (I think it is), but here comes:

Download the manual for Ubuntu from here: [http://ubuntu-manual.org/](http://ubuntu-manual.org/), possibly in your own language.

Topsiho

---

