---
title: "How do I set up Geany?"
date: 2007-08-24
forum: Programming Talk
---

### Post by MobileDev on 2007-08-24
Hello everyone! I recently discovered Geany. The great thing about it is that it just pops up, while Anjuta has to take a couple minutes to load. The bad part about it is that the default settings don't work for some weird reason. It can't seem to find the compiler and I don't know the correct paths or options to set so that it will compile programs. I am running Xubuntu 7.04 Feisty and I have already installed G++, GCC, libstdc++6, and all of the required dependencies. Am I missing something here? Do I need automake and it's associated packages too? Sorry I don't have any screenshots, should have brought some with me to the library. Right now, I am programming with Code::Blocks through Wine, which works quite well for some reason, but I'm not learning C++ to make MS Crapware programs! I want to write programs for LINUX!   OTSN (Off Topic Side Note): Has anyone gotten one of those new Autopackages to install on their system without crashing the X server?

---

### Post by moma on 2007-08-24
Ubuntu has a meta-package (named: build-esssential) that contains compilers for C and C++ programming.  You will also need the [Autotools...]("http://en.wikipedia.org/wiki/GNU_build_system") because Geany generates a Makefile pr. project.

So, get these packages:

$ [COLOR="SeaGreen"]sudo apt-get install build-esssential[/COLOR]
$ [COLOR="SeaGreen"]sudo apt-get install automake1.9 autoconf libtool[/COLOR]

I assume that **X**ubuntu has access to the normal Ubuntu repositories where you can install from.
------------------------------------------------------------------------

Are you running Code::Blocks via Wine?  That's awesome. 

If your machine has enough CPU horses, put in a native version of Code::Blocks IDE.  Follow this guide: [http://ubuntuforums.org/showthread.php?p=2816470#post2816470](http://ubuntuforums.org/showthread.php?p=2816470#post2816470)
-------------------------------------------------------------------------

Autopackages: 
Do you mean [http://www.autopackage.org](http://www.autopackage.org) ?

I never use Autopackages because Debian's and Ubuntu's repos provide all necessary software and the packages are cleverly accounted by the Apt. I also prefer compiling from source over using the Autopackage.
-------------------------------------------------------------------------

PS-1. In Geany, compile your projects by pressing the F9 key or use the menu selection  Build -> Build.   Menu selection Project -> New creates a new project.

PS-2: 
* A new TEST version of Gutsy Gibbon (Ubuntu 7.10) just shipped: [http://www.ubuntu.com/testing/tribe5](http://www.ubuntu.com/testing/tribe5)
* A rather new version of Linux MCE (Multi Media Edition + Smart House solution) released. [Watch t'demo....]("http://video.google.com/videoplay?docid=2176025602905109829&q=linuxmce&total=4&start=0&num=10&so=0&type=search&plindex=1")  It is an excelLent demo of clearly spoken english too for us foreigners. Isn't it?

---

### Post by Smygis on 2007-08-24
You do know that Code::Blocks can be run native in Linux?
[http://ubuntuforums.org/showthread.php?p=2816470#post2816470](http://ubuntuforums.org/showthread.php?p=2816470#post2816470)
I know there is some debs out thete aswell but i culd not find them.

---

### Post by moma on 2007-08-24
> **Smygis said:**
> You do know that Code::Blocks can be run native in Linux?
[http://ubuntuforums.org/showthread.php?p=2816470#post2816470](http://ubuntuforums.org/showthread.php?p=2816470#post2816470)
I know there is some debs out thete aswell but i culd not find them.

Ahh, 
The .deb packages for Ubuntu are now compressed and included in a tar.gz ball.

Download the latest tar.gz file you can find on the BerliOS' site. 
E.g for the date 2007-08-22 there is file 
[http://prdownload.berlios.de/codeblocks/CB_20070822_rev4405_Ubuntu6.10+7.04_wx2.8.4.tar.gz](http://prdownload.berlios.de/codeblocks/CB_20070822_rev4405_Ubuntu6.10+7.04_wx2.8.4.tar.gz)

Open and unzip the .deb files into an empty directory. This command will install the .deb files:
$ [COLOR="SeaGreen"]sudo dpkg -i *deb[/COLOR]

I need to fix the above mensioned guide.
[COLOR="Red"]EDIT:[/COLOR] It's fixed. At least did my best :-)

---

### Post by MobileDev on 2007-08-25
Running Code::Blocks with Wine is pretty cool. The thing that I find scary is that the system I'm running Xubuntu on doesn't even have a 1Ghz processor and only 128 MB of ram, but when I try to run something like Unreal Tournament Game Of The Year Edition, it comes up twice as fast as it did on Windows WITH NO LAGGING! I don't know what the dev team did to wine, but I didn't have to change anything to get programs to work (except for copying all program DLLs to system 32 folder). In the Dapper version of (X or K)Ubuntu, I had to play with Wine for quite a while just get a GBA emulator to work. Nice job Wine team! 

Also, I tried to use Code::Blocks under Dapper, but I didn't find a package for it in the Ubuntu repos, so I compiled it from source. That caused me a lot of headaches and system problems. I might try the link you guys posted. Thanks. 

In conclusion, I figured out what I did wrong. I never actually had G++ installed on my system. The package I installed was some kind of data or system package that the actual compiler needed in order to run. Now I have the compiler installed and it works great. I also decided to install the autotools thing, meaning that I now have a lightning fast IDE that generates full-blown make files, project files, and even .deb packages that actually work! (of course I was following a tutorial at the time, but it still worked).

Thanks for the help guys. As always, this forum has a relatively speedy response time. I will never use another Linux distro (except maybe pure Debian). ***Long live Ubuntu, the most functional Linux Live-CD period!***

---

### Post by tmshih on 2007-10-02
I've been having a problem using Geany under Xubuntu Edgy to run simple C++ code. After I hit build and try to execute a program xterm pops up for just a second before vanishing. I would like to the terminal to stay up. Any suggestions?

---

### Post by zero-9376 on 2007-10-04
maybe the program is doing its thing and then exiting, this happend when i leant C for uni, the hello world program would pop up in console and then exit staight away, adding a "press enter to exit" prompt stopped that

---

### Post by tmshih on 2007-10-04
Thanks but I found another solution. I added the "-hold" command to the xterm launcher under Preferences - Tools. That blocks the window from exiting until you exit.

---

### Post by michaelzap on 2007-10-04
I love Geany and use it every day, but I wish there were a way to integrate plug-ins into it (I'd like a multi-line search and replace)...

---

### Post by zero-9376 on 2007-10-04
actually the new version is going to have some sort of plugin system, there is a pre-release of 0.12 available from the project website

---

### Post by michaelzap on 2007-10-04
> **zero-9376 said:**
> actually the new version is going to have some sort of plugin system, there is a pre-release of 0.12 available from the project website

Hey, you're right! I hadn't read the list of new features in the beta. That makes my day.

---

