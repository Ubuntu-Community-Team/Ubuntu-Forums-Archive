---
title: "Is Ubuntu something for me?"
date: 2023-03-19
forum: New to Ubuntu
---

### Post by truij on 2023-03-19
Hey, I'm getting real tired of all the issues Windows gives me (I'm starting to hate it), so I am wanting to use Ubuntu as my primary OS. 
But how good is program support (see paste bin) and hardware support (see pastebin)?
And I'm still wanting to keep the Windows installation - I'm not the only user - so are there important things to note when dualbooting with Windows 11?
/ EDIT The pastebin: [https://pastebin.com/2VSdssbT](https://pastebin.com/2VSdssbT)

Is this a good tutorial? [Ubuntu Complete Beginner's Guide: Download & Installing Ubuntu - YouTube]("https://www.youtube.com/watch?v=W-RFY4LQ6oE&list=PLrW4kXWyzgoJgN3Ebo3LGoyJvNZiDMWi9")?

---

### Post by Autodave on 2023-03-19
Your simulator programs will probably only work in Windows.  There is a program called WINE that will allow some Win programs to run in Linux, but it is hit or miss as to whether they will work and how well.  I dual boot....and the only program that I run in Win is the trains simulator.  Everything else is done in Ubuntu.

---

### Post by ajgreeny on 2023-03-19
Another possibility to avoid dual-booting is to use a virtual install of Windows using your Ubuntu as the host OS.

I am not sure how exactly one deals with the Windows Licensing requirements when using a VM but I suspect that an OEM install, ie, Windows that came ready installed with your computer will not be possible as a registered install in your virtual install.  I have no idea about the use of a separately installed purchased license but back in the days of XP I think it was possible to move from machine to machine as long as the original installed version was uninstalled from the original machine; don't take this as absolute truth however, as I've not actually used Windows since those XP days, and have used Ubuntu versions since 2005.

Virtualbox is what many find the easiest way to run virtual installs, but that is bettered in my opinion by KVM/QEMU which is worth investigating further by you.
Here is a good link about installing and using KVM/QEMU mentioned by another forum member at [https://linuxhint.com/install-kvm-ubuntu-22-04/](https://linuxhint.com/install-kvm-ubuntu-22-04/)
There is also a Ubuntu wiki page on the same subject at [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by lucant on 2023-03-19
I recently created a virtual machine using gnome boxes, with Windows 10.
I downloaded the microsoft iso and it provided me with a trial version.
I gave up when it came to updating the system... It took forever, and I had no patience.
In this case, I made 4 GiB of ram available.

---

### Post by truij on 2023-03-20
So, maybe I didn't clearly point it out, but I do have to dualboot because other users probably won't be using Ubuntu.
But probably the most part of things I do om my PC, Ubuntu is unsupported?

---

### Post by MAFoElffen on 2023-03-20
I do dual boot on most all of my machines here...
> **truij said:**
> But probably the most part of things I do om my PC, Ubuntu is unsupported?
Could you please reword this question so I can answer it clearly? What will you hope to do on it? What will be it's job for you?

I ask these, because I've been doing Dual-boots since 2005. At first I was seeing what I could do on UNIX and Linux to do things that I was doing on Windows. At first, I tried to be open minded, bur found myself a bit biased on "I can't run this specific program", but there were other programs in Linux that had the same function... Some of those specific programs, I later ran on Wine. Then dropped those, as I found other native Linux programs that I liked better. 

The first thing I liked about Linux, over Windows, was that the Windows system itself, kept getting more and more shielded from the user, to make their own customization and tweaks. It got to the point where that turned around, at the perspective, of, I can do this on Linux, but not on Windows... That is now, to the point where I can do almost anything I want on Linux, and but not on Windows. Until now, where I rarely use Windows at all (except on some specific "games" that I play.

Somewhat similar to your PC, one of mine that is dual-boot with Win 11 & Ubuntu 22.04.2 LTS, is on a Gigabyte B460 board...

---

### Post by truij on 2023-03-20
> **MAFoElffen said:**
> 

Could you please reword this question so I can answer it clearly? What will you hope to do on it? What will be it's job for you?

Well, I'm wanting to use Ubuntu as placeholder for Windows. But I'm unsure if it's really supports my games and software. (I do know that Blender works luckily)
And I want to know how well Ubuntu supports my hardware and if it is possible to run  Windows games on Ubuntu. 
Those are the most important questions for now.

---

### Post by MAFoElffen on 2023-03-20
Here is your list of Games:
```

Euro Truck Simulator 2 

Farming Simulator 22 

Train Simulator Classic

SimCity for Windows (1989) 

```
1. Euro Truck Simulator. If the Steam Version, you just run the Linux Steam Application and all your purshaed agmes will show up in the Loader. Most Steam Games can run on Windows and Linux. There are exceptions, but ETS runs on Linux. In fact, there is a stand-alone version of ETS that runs on Linux.

2. Farming Simulator 22 is on Steam... See above.

3. Train Simulator Classic runs on Proton/Steam Play, and also is a Linux standalone version.

4. SimCity For Windows, version 1.1 will run on Wine. There is also a Steam Version of newer SimCity Sequels.

Those games will run on Linux. Many can play on Proton, or PlayOnLinux. Both are compatibility layers to Wine.

What else were you wondering about?

---

### Post by truij on 2023-03-20
Is this a good way for getting the gpu drivers?
[https://www.nvidia.com/download/driverResults.aspx/199656/en-us/](https://www.nvidia.com/download/driverResults.aspx/199656/en-us/)

---

### Post by ajgreeny on 2023-03-20
> **truij said:**
> Is this a good way for getting the gpu drivers?
[https://www.nvidia.com/download/driverResults.aspx/199656/en-us/](https://www.nvidia.com/download/driverResults.aspx/199656/en-us/)
No, it's not the way, and if you try doing that you may end up with more problems.

Go to Additional Drivers from your menu system or simply use terminal command ```
/usr/bin/software-properties-gtk --open-tab=4
``` and see what is offered.

---

### Post by #&amp;thj^% on 2023-03-20
> **truij said:**
> Is this a good way for getting the gpu drivers?
[https://www.nvidia.com/download/driverResults.aspx/199656/en-us/](https://www.nvidia.com/download/driverResults.aspx/199656/en-us/)

Not really the best way for Ubuntu, it will work but with kernel upgrades it will break your system:
Ubuntu has GUI for that in the additional drivers tab  of your software manager, and please choose the correct driver for your card.
Apt has a search tool to help as well:
```
 apt search nvidia-driver

```

---

### Post by TheFu on 2023-03-20
> **truij said:**
> Is this a good way for getting the gpu drivers?
[https://www.nvidia.com/download/driverResults.aspx/199656/en-us/](https://www.nvidia.com/download/driverResults.aspx/199656/en-us/)

For people new to Linux, only get programs from the official repositories. That goes for all drivers too. Most of the time, drivers will be installed with the kernel and we don't need to do anything.  nVidia is one of the least "Linux-friendly" vendors out there. AMD and Intel both have their GPU drivers distributed with the kernel. Intel has been doing that over a decade - probably over 15  yrs.  

nvidia GPUs have caused me, a 30 yr Linux user, enough trouble that I specifically replaced a Ryzen CPU to have the onboard APU from AMD and removed a discrete nvideo 10xx series GPU from the system.  It wasn't a high-end GPU. The APU included in the Ryzen is actually faster.  If you are spending $1500 on a GPU, then perhaps nvideo makes sense, but for the mid-range GPU buyers of $600 and less GPUs, just stick with AMD to avoid hassles, assuming you don't get bleeding edge.  Driver support comes with new kernels and typically it takes about a year for GPU drivers to be included with LTS kernel releases of LTS Ubuntu releases under the HWE driver update program.  Really new kernels often come with bugs and downsides, which is one reason that I stick with older kernels when possible.  But I don't have **any** bleeding edge hardware. I avoid it.

LTT (youtuber) did a series about gaming on Linux last summer. Perhaps you should check that out. Not all games will work, but many of the most popular ones, usually through steam, will.  If you don't/refuse to use Steam, then things get a bit harder.  When I say "get a bit harder", expect multiple hours of tweaking configurations and settings, before a known-supported game will work. Of course, many games (about 20% is the estimate) won't work under Linux.

I'm not a fan of dual booting for a number of reasons.  But gaming is one of the reasons why I would dual boot, assuming I didn't have a 2nd gaming computer dedicated just for that purpose.

---

### Post by truij on 2023-03-21
OK, thanks for the reply. I'll watch the LTT serie that you mentioned, but I'm first gonna try to get Ubuntu installed properly :)

---

### Post by MAFoElffen on 2023-03-21
Since you have an NVidia GPU, please note that if you have video problems starting the LiveUSB, then put the Grub2 menu into an edit mode > Arrow-down to the line the starts with "linux. > Arrow -right to after where it says "quite splash" and add "nomodeset". > Boot via Control-X.

Then on one of the install options pages, look for where there is a checkbox to install third-party drivers. If you select that, it will install a graphics driver for your card during the installation process.

---

### Post by truij on 2023-03-21
OK, I got everything set up and running (do still have to install Steam), but how do I install programs (like Firefox) to a different drive?
Because now everything goes to the F: disk (slower HDD) (had to install Ubuntu there due to space limit), but how do I install/ move a program to my C: (faster SSD) drive?

---

### Post by Sunil_Daswani on 2023-03-21
Hi Truij it will automatically install on the drive that has the Ubuntu OS // (You can use terminal )
$ sudo snap install firefox     ////   or directly download from official Firefox website

If i understand correctly C:/ still has windows?

there is another way, you can mount /home to one drive and /root to another drive and have your programs on another drive than your OS (ubuntu) ... this is difficult and also has to be done on installation

---

### Post by MAFoElffen on 2023-03-21
But wait... You installed an Ubuntu Desktop Edition, right? Firefox "is" a default installed application. Isn't it already installed?

---

### Post by TheFu on 2023-03-21
> **truij said:**
> OK, I got everything set up and running (do still have to install Steam), but how do I install programs (like Firefox) to a different drive?
Because now everything goes to the F: disk (slower HDD) (had to install Ubuntu there due to space limit), but how do I install/ move a program to my C: (faster SSD) drive?

So, in Unix systems, programs are made up of different parts. These different parts are placed into different directories based on the package installer.  The Linux File System Hierarchy Standards explain what goes where.  There's a formal, industry group that produces that document.  There's also a wikipedia article with a good summary. [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

In short, programs go into /usr/bin/
System-wide settings go into /etc/
Program Data that is shared with others go into /var/lib/
Personal Data that is per-userid goes into $HOME/ for that user.

There are ways to change there personal data goes, usually through environment variables, so it is possible to have 20 different personal versions of the same program just by changing 1 variable.

But since Unix and Linux were meant to be multi-user from the start, programs have always been installed in a central way.
Other OSes keep all those different parts in a single place, which makes for a mess when multiple users become involved.

With all that said, the OS and programs don't care specifically where the storage used for and directory is really located.  There are a number of methods to redirect or just directly mount extra storage where it is needed.  For example, I mount extra storage where it is required on 1 of my systems:
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-var                        ext4   54G   33G   19G  64% **/var**
/dev/mapper/WDBLK_8T-jellyfin               ext4   20G  7.0G   12G  38% **/var/lib/jellyfin**

```
Forget **drive letters**. Those actually haven't existed in decades, even on MS-Windows.  With Linux/Unix, we can mount a file system exactly where it is needed.  See how I put 20G just for jellyfin?  Usually, I'd have /var/ be about 4GB, but with LXD and snap packages, Ubuntu/Canonical has decided to place linux containers under /var/lib/ which can use lots of storage, so I decided to make that storage much larger than I'd normally need.  Additionally, I created an area just for LXD managed LXC containers (50G) which are in an SSD inside a logical volume manager tool (LVM2). That storage isn't mounted. It is 100% managed through lxd for lxc container needs.

The easy way to redirect to different storage is to use symbolic links.  The harder way (only slightly) is to setup the /etc/fstab  to mount the extra storage where it is needed. An example line to mount that jellyfin storage:
```
/dev/WDBLK_8T/jellyfin /var/lib/jellyfin        ext4  nodev,nosuid 0 1
```
Yours **will** be different and the partition and file system have to be setup on the device BEFORE it can be mounted.

---

### Post by Impavidus on 2023-03-21
Drive letters (really partition letters) like C: and F: are a Windows thing. They don't get assigned to partitions that Windows doesn't understand, including native Linux partitions. So C: is always the main Windows partition and must have a native Windows filesystem, the root partition for Ubuntu must have a native Linux filesystem and won't get a drive letter.

I may be using partition and filesystem a bit loosely here. They're not the same, but closer to a 1:1 relation than drives and partitions. A drive may have multiple partitions, a partition normally has exactly one filesystem, sometimes none. We'll leave the complexities for some other time.

You can have your OS and applications on the SSD and your documents on the spinning drive. Best to set it up for that before you install the OS. You can create a root partition on the SSD, at least 30GB to be somewhat comfortable, and create other partitions on the spinner. Filesystems can be mounted on directories of other filesystems, so that the contents of the directory used as a mountpoint are stored on a different partition. Moving individual applications to a different drive will likely end in an unpleasant (although instructive) experience. The OS with all the core applications is only about 10GB, so that's pretty small compared to Windows, but you need some additional room for logs, temporary storage for updates, additional applications etc. And with the new packaging method that's now standard for some applications like Firefox (i.e., snap), storage requirements have gone up quite a bit.

---

### Post by truij on 2023-03-22
OK, I read through everything above, and excuse me that I constantly use driveletters. But the thing is: I DO want to install Ubuntu to the SSD, but given the fact that Windows and a lot of programs is installed on there (and that it is a 256 GB drive) I can't install Ubuntu beside it because that's going to use too much storage (best would be to delete Windows, but other user probably wont like that :) ).
So thats why I want to move certain programs to the SSD.
But I am going to look if I can make some space, and otherwise try the above mentioned things..

---

### Post by TheFu on 2023-03-22
> **truij said:**
> OK, I read through everything above, and excuse me that I constantly use driveletters. But the thing is: I DO want to install Ubuntu to the SSD, but given the fact that Windows and a lot of programs is installed on there (and that it is a 256 GB drive) I can't install Ubuntu beside it because that's going to use too much storage (best would be to delete Windows, but other user probably wont like that :) ).
So thats why I want to move certain programs to the SSD.
But I am going to look if I can make some space, and otherwise try the above mentioned things..

The OS and applications typically use less than 35G even on bloated Gnome-Ubuntu.  Put everything else on the HDD, including the swap.  Swap really should be on a slow spinning HDD so the user can "feel" the slowdown when RAM gets tight.  That way, the user can close a bloated browser and free 50G of wasted RAM allocations from the browser bloat. 

Put your HOME directories and /var/ on the spinning HDD.  The installer has a "Do something else" option where that can be accomplished.  Or there are how-to guides [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) and [https://www.howtogeek.com/442101/how-to-move-your-linux-home-directory-to-another-hard-drive/](https://www.howtogeek.com/442101/how-to-move-your-linux-home-directory-to-another-hard-drive/) and [https://www.tecmint.com/move-home-directory-to-new-partition-disk-in-linux/](https://www.tecmint.com/move-home-directory-to-new-partition-disk-in-linux/) are all reputable sources.
[https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition) seems dated. I wouldn't use it, but it is there if you need it.

---

### Post by MAFoElffen on 2023-03-22
Is this a laptop or desktop? What brand/model of computer? 

Could you please post the output of these PowerShell commands from Windows?
```

Get-Volume
Get-ComputerInfo -Property "*version"

```
Paint us a picture please.

---

