---
title: "Synaptics Touchpad and keyboard not working"
date: 2016-03-23
forum: New to Ubuntu
---

### Post by Desert_Outlaw on 2016-03-23
Trying desktop environment LXDE (Lubuntu) on older Dell Inspiron 4100; beside Windows XP. 

Present version is 15.10 32-bit with Linux 4.2.0-34-generic (i686) 

 GNU GRUB version 2/02 beta2-29ubuntu 0.3 allows selection using laptop keyboard if necessary, but neither Ctrl x or F10 will save changes made in edit mode. 

 System works fine except usb mouse and usb keyboard must be used after selecting lubuntu or allowing GRUB to automatically start lubuntu; laptop keyboard and mouse-pad works fine in XP.

 xinput list confirms SynPS/2 Synaptics Touchpad, keyboard and TPPS/2 IBM Trackpoint.

Have researched this forum in addition to others and searched the net, yet have been unsuccessful in locating a fix. 

Apparently issue has been reported as a bug for years and although it has not been resolved, users have been able to make or find a fix for their computer configuration.

Any and all suggestions appreciated.

=============================
FYI, Ubuntu 14.o4 LTS 64-bit works perfect on a HP Pavilion notebook beside Vista which always worked perfectly. However, when support ends for Vista, the M$ OS will be removed as I am becoming more of a Linux user on a daily basis..

 Would like to resolve issue with Dell before installing a Ubuntu system on my desktop beside Windows7 as I have no interest in Windows10. Linux works just fine.

---

### Post by Desert_Outlaw on 2016-03-24
FYI, [http://www.linux-on-laptops.com/components.html](http://www.linux-on-laptops.com/components.html)  has dead links, links that are no longer maintained, or lead to different pages.

The Synaptics TouchPad is a pointing device used in notebooks by Acer, Compaq, Dell, Gateway, Olivetti, TI, Winbook, and others. 

Synaptics at [http://www.synaptics.com/](http://www.synaptics.com/) only has drivers for Windows OS, not Linux.

The latest driver at [http://cscott.net/Synaptics/](http://cscott.net/Synaptics/) is identified as version 0.1.1. However, it it is not actually a driver, but a set of instructions for making the pad work and is over ten years old. 

Being a newbie with Linux, the instructions are over my head.

Is there an experienced Linux user that can offer some assistance?

Thank you in advance.

---

### Post by Geoffrey_Arndt on 2016-03-25
Here's a youtube video of a possible fix.

Note, user is running Ubuntu 14.10 on an Acer Laptop - - but the fix (via firmware settings) may also apply in your situation.    Also, the user is speaking German, but if you have the same or similar firmware type, it's worth a try (fairly intuitive in spite of language diff.)  [https://www.youtube.com/watch?v=E2POD-TElRw](https://www.youtube.com/watch?v=E2POD-TElRw)

---

### Post by Geoffrey_Arndt on 2016-03-25
Here's another version of fix via youtube  [https://www.youtube.com/watch?v=4-cGqVLXyrA](https://www.youtube.com/watch?v=4-cGqVLXyrA)

---

### Post by Desert_Outlaw on 2016-03-26
Thanks Geoffrey. Although the fix in the video did not work, it was not a total loss. Discovered that the gedit package was not installed so it was added. The procedure in the video then went smooth.

Also checked out the other videos and tried a couple other fixes including the nano fix.

 Looking more like its just a Dell/ubuntu/synaptics incompatibility issue.

---

### Post by robartist on 2016-03-26
Hi. Was interested in this thread. I am having problems with my HP Stream which has a Synaptics touchpad. Can't get it working in Lubuntu. Though, mysteriously, some people claim it works ok under straight Ubuntu????? Which presumably means there are some working 'drivers' somewhere?? Or have I got that wrong?

---

### Post by Geoffrey_Arndt on 2016-03-26
The easy way to check that out is by running  a "Live" media disk or usb-flash-stick.    Usually, the thing that makes the difference is the version of the kernel, and what's built into it.   Trackpad incompatibility is a relatively minor issue in linux - - probably happens in about 1 of 200 or so installs . . . Personally, I would try the very latest 16.04 version (beta2) of either Ubuntu or Xubuntu (for non-3d accel. hw).

---

### Post by Desert_Outlaw on 2016-03-26
Believe you are correct. However, since Synaptics does make make a driver for Linux, its a matter of how to manipulate the "open" code so it will. It's frustrating but its only a matter of time. :)

---

### Post by Desert_Outlaw on 2016-03-26
Geoffrey, when you say "live", do you mean placing lbuntu on a usb flash stick and running the operating system from it rather than from the hard-drive? I assume the same would work if the OS was placed on a CD if there is no option in the boot sequence for a usb port. Good feature about lubuntu is it will fit on a CD which is normally limited to 650 or 700mb.

---

### Post by pauljw on 2016-03-26
> **Desert_Outlaw said:**
> Believe you are correct. However, since Synaptics does make make a driver for Linux, its a matter of how to manipulate the "open" code so it will. It's frustrating but its only a matter of time. :)

The synaptics drivers are in the repos, just install from there.  I would install Synaptic Package Manager (not related to synaptics touchpad) then you can easily search for synaptics and select and install the driver.

My System76 is using the "xserver-xorg-input-synaptics"  version:1.7.4.

---

### Post by robartist on 2016-03-26
Thanks pauljw. I did what you suggested but it didn't work on my HP Stream with Synaptics touchpad.

It's still not working properly :(

---

### Post by Desert_Outlaw on 2016-03-26
The laptop keyboard & mousepad do not work using a "live" cd, still requires the usb keyboard and mouse. Gonna try the Synaptic Package Manager.

---

### Post by robartist on 2016-03-26
I think that's what I installed an hour or two ago and it didn't work for me.

---

### Post by Geoffrey_Arndt on 2016-03-26
Yes Desert_Outlaw . . . "Live OS's" are something pioneered by Linux many years ago;  Microsoft is even now starting to get into the act (although I don't know how many restrictions they have hooked to their Live images).

A Live OS is a multi-purpose medium in that it is used to test & demo a system (OS), to be a rescue system, and to provide the means to install the OS.   Perhaps the 1st Live OS was Knoppix, way back around 2001/2002.

Regarding synaptics, much of the install by OEM/ODM is focused only on MS-Windows or Mac - - - it's then often a case of tweaking the "config" text files associated with the drivers (or modules as known is Linux).   As I've never had even a minor issue with track or touchpads, I can't offer much personal advice, but I've seen many links to threads about detailed config options to look at in the Linux version of a registry (e.g., the /etc directory).

Again - - suggest to use Ubuntu Xenial Xerus asap - latest kernel (4.4) has much better support for certain synaptics hardware.

---

### Post by Geoffrey_Arndt on 2016-03-28
OK guys, . . . has anyone tried the beta2 Xenial release (16.04) with kernel 4.4.?

---

### Post by Desert_Outlaw on 2016-03-29
> **Geoffrey_Arndt said:**
> OK guys, . . . has anyone tried the beta2 Xenial release (16.04) with kernel 4.4.?

Just performed some searching and there appears to be 7 different flavors, each without identification of the minimum requirements. Therefore, it is unknown whether it would work on an older system, especially while in beta mode. Therefore, I'm gonna continue trying to resolve the issue of the keyboard and touchpad not responding after working in the grub. It has to be something simple that is being overlooked otherwise the keyboard and touchpad would not work at all.

---

### Post by Geoffrey_Arndt on 2016-03-30
Re the "7 different flavors" . . . Ubuntu Unity (the default flavor) and Ubuntu Gnome use higher end graphic modes and require mostly modern, or up to date PC's (unless using Intel graphics - - those machines work even if cicra 2005).    The rest like Xubuntu, Ubuntu Mate, Lubuntu etc. are lighter and work without needing Intel or Proprietary nVidia or AMD graphics drivers.   Hope that clears things up somewhat.

Re the configuration - - it's likely there's a couple files in the /etc directory that would have to be modified (after making a backup of original) - - -  (/etc or "etcee") is similar in function to the Windows registry (but not similar in design).

If I were dealing with your situation, I would start with "askUbuntu" - - as their Q & A is a bit more technical & detailed (not necessarily newbie friendly) - - - just my opinion for what it's worth.    But also, I would try every link on general Google searches including youtube linux channels to search for answers.    Lastly, there are many good answers at other forums for other distros (it's all Linux) such as Fedora, Mint, and especially the _Arch Linux forums and Wiki's_.

---

### Post by Desert_Outlaw on 2016-04-17
Thanks Geof. I tried to post in askUbuntu but was denied. Appears to be a board that requires special membership. Regardless, the reason I was wanting to use lubuntu on the Dell 4100 is because of the limited memory, processor, etc in the machine  A regular ubuntu version taxes the puter and performance is anything but decent and acceptable, unlike lubuntu which zips right along. What amazes me is the laptop keyboard will work during the installation but after the OS is installed it will not. I ran the commands to learn what hardware was detected and all three pieces, the keyboard, touchpad and roller are displayed along with their assigned numbers. I also tried removing the grub and XP but was a wasted & worthless effort. So using an external keyboard and mouse are my only options should I want to use it. The other option is the trash bin outside. 

Did spoke with Dell who informed me the problem I am experiencing is pretty common. Only suggestion that was given, other than to have the author correct the installation files was to disconnect the power adapter, remove the battery, and depress the power button for 30 seconds. Then re-install the battery, connect the power and boot the machine. It did not work. 

Did learn something that was very kool though. Although I am an old Opera fan, version 12.17 and below, Opera makes downloading of their new version (which is basically a Chrome clone) fast and simple. Would be great if more sites were like Opera for Linux.  Having to use the Software Center (which is limited)  or enter a line of code to perform a download, and then hopefully performing an actual valid install, can be very frustrating and time consuming. BTW, the original engineers of Opera have a new browser called Vivaidi, which shows promise of becoming the best browser available and works just fine on Ubuntu. It is also a fast and simple download. Old Opera fans will recognize and appreciate many of the features and improvements. 

In some ways, Linux is still in their infancy stage when compared to Windows other than for surfing the net. Have noticed an increase in updates for Linux systems although they are faster to download and install than Windows. 

Thinking about purchasing the software that makes some software for Windows work on Linux but the reviews I have heard have not been that great. However, there is still a great feature about software for Linux. Almost all software created for Linux is backward compatible and will work on the newer versions and/or the flavor of the day. With Windows, a person can expect to spend a small fortune on software with each new release; From 3.1 to 95, 98, 2000, XP, 7, 8 and now the disastrous 10, seems like most software is not backward compatible, except for the browsers. Gotta tip your hat to the creators of most browsers.

So in closing, this post can be closed because this is an issue that is not going to be solved.

---

### Post by wilfried3 on 2016-04-25
> **Geoffrey_Arndt said:**
> 
Again - - suggest to use Ubuntu Xenial Xerus asap - latest kernel (4.4) has much better support for certain synaptics hardware.

I just installed Xenial... problem still exists.

What irritates most is that it's not working on the live CD.

BTW anyone who is trying to install 16.04 on a Aspire One ZG5 take the Lubuntu Alternate i368 iso  
The other gives kernel panic and has other issues...

The Aspire One doesn't have the bios setting like suggested in first video.
the suggestion in the second video also gave no joy.

sudo leafpad /etc/default/grub

then added
psmouse.proto=bare  o the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash psmouse.proto=bare"

sudo update-grub

after reboot the atheros wifi no longer seemed to work... not sure if this is related...?

---

