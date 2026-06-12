---
title: "Need help with Migration from Windows 8"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by Regan_Lu on 2014-03-23
Hello everyone,

I am contemplating how, if I chose to, migrate my current system to a install of Linux.  I know very limited about the Linux and have no idea how the guts of the OS actually works. Problems that I encountered  during the planning stages for migration were the following:

[LIST]
[*]Security problems  with the WINE layer as I need a windows layer or sandbox to able to run  certain program that exclusive to windows. The fact that malware or problematic bat  code can be run or inserted themselves into existing is troubling to me. As countermeasure, I heard that you must not run this as root but it is unknown how would it affect the legitimate programs I need to run. Will there be errors or corrupts with my working files? 
[*]Certain Windows programs only such as RISA, Augustus, Formworks, AutoCAD, Rociscience suites, and other engineering software packages. I am aware of alternative to some of these problems but again I am fearful that they may not be as sufficient. Although, this stems from experience of using windows based open source software that were at best underdeveloped by programmer. 
[*][COLOR=#a9a9a9]My lack of knowledge with navigating and properly configuring the system to be secure environment and a usable environment. For example, bring up the home directories and using commands on the command line for other configurations. Essentially, I can't fully utilized the power this OS will give me without spending considerable amount of time to learn the system more. Time is something I have not enough of. [/COLOR]**Semi-Solved, Any suggestion for more resources?**[COLOR=#a9a9a9]
[/COLOR] 
[*]Integrating [COLOR=#a9a9a9]my outlook(+multiple other) account(s) and other[/COLOR] (**Semi-Solved**)  existing Cloud Storage (DROPBOX, COPY, GOOGLE DRIVE, ONEDRIVE, ADRIVE) with LINUX. 
[*]The transferring files and data. What preparations must do in the transfer and securing these files for migration? 
[/LIST]
 Thank you in advance.

- Linux Noob

P.S: WOW, did not read the top threads.

---

### Post by Korkel on 2014-03-23
Hello and welcome to the Ubuntu forums,

About the Windows programs that you need to run, you can use Wine. I don't know what programs it are, but if you use it safe nothing will happen? I'm not sure how Wine works, so someone else must provide that answer for you.

> **Regan_Lu said:**
> Certain Windows programs only such as RISA, Augustus, Formworks, AutoCAD, Rociscience suites, and other engineering software packages. I am aware of alternative to some of these problems but again I am fearful that they may not be as sufficient. Although, this stems from experience of using windows based open source software that were at best underdeveloped by programmer.
You can run these programs using Wine(?) or install VirtualBox, where you install Windows to install the Windows programs.

About the Outlook problem, I don't have a solution, you can install Dropbox on Linux (got a script for it if you want). Not sure about Google Drive etc, but I will chek it for you.
**Edit: **There Google Drive isn't available for Linux on this moment, best way is to use: [https://drive.google.com](https://drive.google.com)

You can install Ubuntu and keep your data if I'm right, otherwise put it on a extern hard disk so you can put it later on Linux.

Hope this helped you.

Regards,
Korkel

---

### Post by Mark Phelps on 2014-03-23
> Certain Windows programs only such as RISA, Augustus, Formworks, AutoCAD, Rociscience suites, and other engineering software packages. 

If I had to guess, I would say that it's more likely that these apps will NOT work in Wine.

BEFORE you take this leap, you should go to the WineHQ website, the application compatibility tool, and check the apps and versions you want to use.  Anything not found, or shown with a rating lower than Gold is going to be a waste of your time trying to get it to work in Wine.

You're also NOT going to be able to integrate Outlook with Linux in any way.  It doesn't work in Wine, and the best you would be able to do is export some of the contents into Linux apps.

Sorry, but migrating to Linux and then continuing to depend heavily on MS Windows apps guarantees an unhappy experience.

---

### Post by buzzingrobot on 2014-03-23
Research Wine carefully to determine if it can handle the Windows programs you wish to run.  Wine is not a panacea and does not allow any and all Windows programs to run on Linux.

You *can* run Windows in  VirtualBox or another virtual environment on Linux, and run Windows apps that way. You'll need to decide if you see a reason to switch to Linux only to use it as a platform to run Windows in a VM.

Command line use is not a basic requirement of a Linux distribution like Ubuntu. Posts here and articles and blog entries usually resort to copy-and-paste command line instructions because that is a baseline capability we know exists on every user's machine, regardless of the GUI they use or how they may have configured their system.  And, of course, it is difficult in words to provide instructions for using a GUI tool.  That said, there is, inevitably, a learning curve moving from one platform to another. (Also, problems that prevent the Linux GUI from launching must be addressed from the command line.)

Files and data you must preserve are, ideally, copied elsewhere until you have the new system working, then brought back.

Whether or not Linux programs are available that can directly replace the Windows programs you know is an open question.  If you find, or fear, that they cannot, I would recommend staying with Windows rather than making the attempt to find something in Linux that is not there.  (Running Ubuntu in a VM in Windows and sampling potential Linux replacement programs might be a way of finding out.)

---

### Post by Impavidus on 2014-03-23
Wine can run some Windows programs on Linux, but not all. Have a look at [http://appdb.winehq.org/](http://appdb.winehq.org/) to see whether other people had success running the programs you want. If not mentioned, chances are it doesn't work. If you rely on much software that has been designed to run only on Windows, Linux won't work for you. This seems to occur rather often with CAD software and things like that.

Moving to Linux can be difficult, as it's very different from Windows. It's best to make the transition gradually, dual booting or using two separate machines.

You don't (at least, shouln't) run any software as root, except tools for system maintenance. If you want your data to be safe, create backups on external drives. Best to do so anyway.

---

### Post by JKyleOKC on 2014-03-23
> **Regan_Lu said:**
> Security problems  with the WINE layer as I need a windows layer or sandbox to able to run  certain program that exclusive to windows. The fact that malware or problematic bat  code can be run or inserted themselves into existing is troubling to me. As countermeasure, I heard that you must not run this as root but it is unknown how would it affect the legitimate programs I need to run. Will there be errors or corrupts with my working files?Others have mentioned the possibility of running a virtualization program such as VirtualBox, and installing Windows into a "virtual machine" there so that you can run the native Windows programs you need, while retaining the features of Linux for use when you don't need those special proigrams.

However I don't see that anyone has mentioned one of the huge advantages of doing so: the ease of doing backup of your Windows systems when they are on "virtual disks." While achieving a backup of a native Windows system that you can restore almost instantly is an extremely difficult task, doing so for a virtual machine is simply a matter of copying a single Linux directory to an external disk, and copying it back if need be.

I have a situation similar to yours; I have a "database recovery" service with worldwide customers thanks to the web, and all of those customers use Windows. Consequently I must have Windows systems available on which to run the repair tools and test the results. However for the past six years my actual native systems have run the Xubuntu variant of Ubuntu (same underlying system but far less eye candy and easier to customize). I have more than a dozen "virtual machines" running, most with WinXP but a few with Windows2000Pro (to deal with older customer systems) and one with Win7 (to test for customers with more recent systems). Most of them are dormant, in "saved" state which is equivalent to the "sleep" state of Windows, but can be brought up in a few seconds when I need them. Each VM is configured for just one task; that is, one handles data recovery, another does data conversion between formats, a third contains my development tools for Delphi, a fourth has the same for Visual Basic, and so on. Each has a small "virtual drive" with just enough space to do what it needs, and in their dormant states that's all the resources they occupy.

To do this, my host hardware needs a minimum of 3 GB of RAM, and my actual hard drives are 500 GB on each of the two boxes of my little LAN. The Windows programs get no more than 1 GB of RAM each, which is used only when they are active, and they are as responsive as they would be if running on actual hardware since my CPUs are dual-core. Both boxes are low-end consumer items, and cost only about $300 USD each.

I even have one VM set up that's isolated from the rest of my system so that any virus-laden customer file brought into it cannot infect anything else. That's something that would be difficult to do without using this approach, but was relatively simple using virtualization.

Others may tell you that using VMs reduces performance; that's quite true if you are a hard-core game player. The virtualization does introduce latency which can be a killer when playing games on line. However for uses such as mine, and the applications you've listed, the reduction may not be visible at all.

Since each VM is simply a small collection of files, and its virtual disk is a single large file, doing backups is simply a matter of copying those files to external storage. To restore, copy them back to the original locations. It can be done automagically via scheduled background tasks if you like.

This is an alternative worth examining, I believe. I'll be happy to provide more detail if it brings up any questions.

---

