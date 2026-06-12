---
title: "Guidance needed for reliable downloads for newbie to ubuntu"
date: 2016-04-05
forum: New to Ubuntu
---

### Post by colin47 on 2016-04-05
Hi everyone, fed up with windows everything...from 3.11 to 10 i have always wanted to take the plunge and use linux from the days when i would load dos 6 before even loading windows on a new pc.  
I used to build pc's but now im old and my brain is tired, so i have finally installed ubuntu 14 on two machines, one a dual boot with win 7pro, and one with just ubuntu.. ok now im a bit disappointed to find there are no mega lists of really good software to download!   First i need google earth,  so i downloaded that but it doesn't work, can't even find it after it's downloaded.... so it's a disappointing start to find there are downloading problems...
Also im used to the old dos commands, as i used them a lot in the old days but now im old and can't get my head around it all..
I love the fact that ubuntu just runs, and is fast, unlike winney chundering through every file on the hard disk spying on every bit of info or doing calculations for nasa behind my back !!!god knows what is really going on when you run windows....so im desperate to get up to speed with ubuntu, just im desperate to find a source of working usable downloads...

so to start, can anyone point me to a working 64  bit google earth that actually installs and works please...
and can i use any of the old DOS based programs in ubuntu ?? 
i still have some dos software from the 90's that i would love to use again..

---

### Post by yancek on 2016-04-05
You can use the apt-get command to install software or you can use the Software Center which should have an icon in the left panel of your Desktop.  Just type in google-earth in the Search box and it should download and install.   You should also probably see an icon in this panel for it.  Dos/windows programs don't run on Linux.

---

### Post by oldos2er on 2016-04-05
You may be able to get some of your old DOS programs working with *dosbox*, it's in the repositories.

[linuxcommand.org](linuxcommand.org) can help with learning shell commands.

---

### Post by colin47 on 2016-04-05
I have down loaded google earth,  and run the install from ctrl alt T  and it says it's installed .....but where ? i have no icon.

ok for the fact linux won't run dos...

i am assuming the "shell commands" are like lines of dos to set a command, so that's a new language i have to learn for running ubuntu or is this just for advanced users to change how things are presented or installed ?

under search your computer and online sources i find a envelope with a squiggle that says earth , but when i try to oppen it , it says this is run on a terminal... now im lost again...

ok i have just realised the "terminal" is a bit like the dos commands used long ago, but with a new set of commands...so im going to have to learn ubuntu like dos.....
Question   although i could find a path to an executable file and start that program, is there a command to create a desktop icon or shortcut path eg old dos   s = c:/ham/sstv/sstv.exe   this would have set a a shortcut key called "s" that would execute a file called sstv.exe in the c:/ham/sstv path,    he, he, im slowly remembering dos!!!!  Just hope ubuntu is as easy....i am 63 and suffering from some memory problems !!!

---

### Post by colin47 on 2016-04-05
OK  managed to get google earth up and running....by doing ctrl alt t and typing google-earth   
strange why the "terminal" is not a standard icon on the side of the screen, but has to be called up !!! is this not possible to have it there all the time ? 
but what a difference to not hear the HD crumping away with windows !!! the PC is only  doing what it is asked to do...
 
windows will soon be deleted forever from my machines...

---

### Post by buzzingrobot on 2016-04-05
The most reliable, and the recommended, source of software is the Ubuntu repositories.  These repositories -- repos -- host thousands of software packages.  A "package", in Linux, is an archive of software that contains scripts and data needed to allow for its automated installation.

Your Ubuntu system contains a 'package manager'  that is responsible for downloading, installing, removing, and updating these packages.  It also handles system updates by comparing its records of packages installed on a system against packages hosted on the repos, and then downloading and installing the appropriate updated packages.

The package manager also resolves dependencies: Packages usually require the installation of other packages upon which their correct behavior depends.

Tools like apt-get, apt, the Software Center, etc., all use the package manager. They are all essentially front ends of varying forms to accomplish the same task. That is, they're are different tools  to install, let's say, Package X, but they all, in the end, use the package manager.  The same packages are available.

The Software & Updates tools will show you the repos in use.

It is possible to download and install packages built for installation on Ubuntu from non-official unsupported sources.  The risk in that can range from nothing to severe. If you install a package from a nonofficial source, you are also taking on the responsibility of fixing any any breakage or compatibilities that arise, at that time or in the future.  

Don't transfer the common Windows habit of searching for software from random places on the net.  That is is least reliable, most dangerous, way to acquire Linux software. (Avoid "tar archives" of source code. While those often contain instructions -- good or bad -- for building and installing that code, they are intended for the distribution of source code among developers, not as a way for users to install softeare.)''

---

### Post by him610 on 2016-04-05
Hello colin47, welcome to Linux and the Ubuntu Forums. I also learned on DOS back in the '80s.

Here is a good reference you might want to take a look at...
[http://linuxcommand.org/]("http://linuxcommand.org/")

The forums are a good place to learn something new. Just reading about the problems other folks have along the suggestions by the moderators and others who might have knowledge of a solution. Very friendly place with understanding people who have been there before.

---

### Post by crip720 on 2016-04-05
To place the terminal icon on the side, just click on the dash icon(top icon), type in terminal, and when you see the terminal icon click and hold on it and drag to the side.  Most software programs should be installed from the software centre, but for third party programs(like google earth) I would suggest installing them with gdebi(installed from software centre).  It should start after you downloaded a program.  Most times you do not need terminal, but it is nice to have.  Colin.

---

### Post by yancek on 2016-04-05
Getting Desktop icons or placing application icons in the left panel explained at the link below.

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

Shell commands are for people who know how to read and write and are willing to do so.  I think you'll be alright with that.  Many actions done in a terminal are faster than using a GUI.  Of course, you need to know the correct command.  There is a lot of good documentation for many Linux distributions available online, particularly Ubuntu.  Look first for something that says Official Documentation on a site.

---

### Post by light_yagami2 on 2016-04-05
For Google Earth, Wine seems to run it fine: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=28526](https://appdb.winehq.org/objectManager.php?sClass=version&iId=28526)

---

### Post by grahammechanical on 2016-04-05
> strange why the "terminal" is not a standard icon on the side of the screen,

It would seem a strange decision to you but not having the terminal in the launcher is sensible when you consider that the whole point of Ubuntu is that it is Linux for humans & not just for geeks.

It should be possible for people to use Ubuntu without needing to know commands. And by and large that is so. There are Linux distributions where almost everything has to be done with commands. Ubuntu server & Ubuntu core work like that. There are Linux distributions where the developers have a completely different idea of what a desktop environment should look and work like. And some distributions offer more options for customization than we get with Ubuntu.

Freedom of choice brings with it the freedom to be disappointed.

Regards.

---

### Post by Bucky Ball on 2016-04-06
> **light_yagami2 said:**
> For Google Earth, Wine seems to run it fine: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=28526](https://appdb.winehq.org/objectManager.php?sClass=version&iId=28526)

You don't need Wine to run Google Earth. Off-topic. If you are relying on Wine to run a heap of Windows programs (Skype and Google Earth) which don't need to be run in Wine or Windows, you'd be better off using Windows and saving yourself the hassle and the kludge that is Wine.

---

### Post by mastablasta on 2016-04-06
> **colin47 said:**
> 
ok for the fact linux won't run dos...


but do emulator DOSbox runs DOS programs well. if you need a gui for it try DBGL. if you know DOS commands there is no need for GUI. the only thing is you need to mount a folder first (or make a shortcut that will do that automatically)

FreeDOS might be able to run in virtualbox.

Playonlinux is a GUi fronend for wine. Wine can run a few windows programs.

I would instead try to find the Linux alternative for your beloved programs.

Bash shell is obviously different than MS-DOS shell. commands are different and are unix like. it's not just commands that are different. there are many differences.

---

### Post by pauljw on 2016-04-06
> **colin47 said:**
> OK  managed to get google earth up and running....by doing ctrl alt t and typing google-earth   
strange why the "terminal" is not a standard icon on the side of the screen, but has to be called up !!! is this not possible to have it there all the time ? 
but what a difference to not hear the HD crumping away with windows !!! the PC is only  doing what it is asked to do...
 
windows will soon be deleted forever from my machines...

Welcome to linux, you won't regret the move, but there is a large learning curve as this is not windows.

For the terminal and any software that you wish, just open the program from the dashboard and while it's open there will be an icon automatically placed on the launcher.  Go to that icon, rt click and select 'lock to launcher' and the icon will stay there.  You can then hold left click on that icon and drag it up or down to the desired location on the launch bar.

Super+A keys will open the dashboard with just applications rather than searching all files.  Hold the Super key (maybe the Win key on your keyboard) will display an onscreen list of keyboard shortcuts.

---

### Post by Topsiho on 2016-04-09
Hello colin47,

I react to your posts as you tell us that you want to have some guidance to downloading and installing programs, after having used Windows such a long time, especially considering you are now old, and the brain has slowed a bit.
Well, as long as you are wiling to take on new challenges, nothing is wrong with your brain! Being 77 myself I can tell you that :)

It IS a daunting task to change from one system (Windows) to another (Linux), and it takes some perseverance to do so.

If only you don't expect both systems should be the same. They are not, otherwise there would be no reason to change from one to the other.

The main advantage of Linux, and thus of Ubuntu, is that it is much more safe. I don't say safe, as that depends on you, the user, yourself. But safer.

One of the things you can do to maintain the safety of Ubuntu is to NOT download and install from any place on the internet, as you did in Windows, but only from places that you trust, such as the repositories of Ubuntu. Installing from the repositories is very easy. Try synaptic.

In Windows installing from download site here, download site there, is no problem: your Windows system is not safe anyway, but in Ubuntu it does matter.

But even in Ubuntu you can jeopardize your system by clicking on links, which may be false, or by installing antivirus (!) and other utilitarian programs you find in the wild on the internet. Never know what is inside, especially when there is no source code.

To recapitulate: Proficiat taking the plunge and change from one system to the other, and no: you are not too old, as you prove this by taking on this challenge.

I wish you all the best,

Topsiho

---

### Post by oldrocker99 on 2016-04-10
There is a .deb for 64-bit Google Earth at [https://www.google.com/earth/download/ge/agree.html](https://www.google.com/earth/download/ge/agree.html).

It is **not** in the current Ubuntu repos.

---

### Post by marc70 on 2016-04-15
colin47, I am in the same boat as you. If I were to start my first thread it would sound much the same. The terminology is about to kill me. I don't understand most of the directions I read concerning Ubuntu, but I understand more today than yesterday.  I'm committed to making this work. There's a lot of good stuff in your thread, thanks for starting it. If you find a good beginners "how to" book, please let me know.

---

### Post by Topsiho on 2016-04-16
if you want an introduction to Ubuntu, you can try the Ubuntu manual. Just download it from

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Learning how to use the command line, you might profit from:

[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

Topsiho

---

