---
title: "where did my installed app go?"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by greyk9 on 2014-04-26
I posted the following in network section but haven't received any advice. Maybe I posted the wrong question. So I installed an app from Ubuntu software center it says its installed no errors, so where did it go? How do I open it?  

I did a clean stand alone install of 14.04 on an old xp machine. With no problems I installed ndiswrapper opened it from dash installed drivers and my usb wireless dongle worked perfectly. After playing with Ubuntu for days and messing Ubuntu up completely I decided to do another clean install and start over. This time after loading ndiswrapper from software center windows wireless drivers does not show up in dash. What did I do wrong this time?  Update: I have reinstalled 14.04 3 times now still not able to get windows wireless drivers to show up.
Thank for any help

---

### Post by TheFu on 2014-04-26
Not everything installable is an end-user program. Sometimes they are just libraries or startup system tools, so there won't be any point-n-click way to access those tools. They are usually managed from the CLI via shell scripts or configuration files.

I've never use ndiswrappers ... It is easier to just select natively supported hardware, support will be much, much, much better, and buying hardware from companies who actually work WITH Linux sends a better message than using other hardware, IMHO.  We've all been _burned_ by purchases only to find they lack Linux support.  Printers, webcams, scanners are where I've had the most issues, but even RAID cards which claimed to support Linux have burned me.  The RAID card provided a binary blob file for a 2-yr-old kernel with ZERO updates or ways to work on any current kernel.  Now I only buy natively supported devices where the support is built-into the kernels with source code.  This makes for a much happier Linux life.

---

### Post by 3rdalbum on 2014-04-26
Did you install the 'ndiswrapper' package or the 'ndis-gtk' package?

The former is a command-line utility, the latter is the "Windows Wireless Networks" utility you mention. Installing ndis-gtk will install ndiswrapper too, but the reverse is not true.

Try this: sudo apt-get install ndis-gtk

---

### Post by greyk9 on 2014-04-26
When I installed the ndisgtk and it auto loaded under optional add-ons: source for the nidiswrapper Linux kernel module (DKMS) (ndiswrapper-dkms) Synaptic package manager shows the following installed
Ndisgtk
Ndiswrapper-dkms
Ndiswrapper-utils-1.9
Ndiswrapper-common

UPDATE:[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=61044") 3rdalbum got me thinking from terminal a tried "sudo ndisgtk" the graphical interface came up and I was able to load the drivers. Guess I'm learning! It is wierd that it didn't put and icon on dash like it did the first time. And I guess I have lots more to learn.

---

### Post by 3rdalbum on 2014-04-26
> **greyk9 said:**
> When I installed the ndisgtk and it auto loaded under optional add-ons: source for the nidiswrapper Linux kernel module (DKMS) (ndiswrapper-dkms) Synaptic package manager shows the following installed
Ndisgtk
Ndiswrapper-dkms
Ndiswrapper-utils-1.9
Ndiswrapper-common

UPDATE:[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=61044") 3rdalbum got me thinking from terminal a tried "sudo ndisgtk" the graphical interface came up and I was able to load the drivers. Guess I'm learning! It is wierd that it didn't put and icon on dash like it did the first time. And I guess I have lots more to learn.

That is weird, I might take a look at the ndis-gtk package and see if it is missing a .desktop file.

Just a note: For graphical programs that need to be run as root, please use gksudo instead of sudo. So:

gksudo ndisgtk

is preferable. Occasionally, using 'sudo' for graphical apps will screw things up.

---

### Post by greyk9 on 2014-04-27
> **3rdalbum said:**
> That is weird, I might take a look at the ndis-gtk package and see if it is missing a .desktop file.

Just a note: For graphical programs that need to be run as root, please use gksudo instead of sudo. So:

gksudo ndisgtk

is preferable. Occasionally, using 'sudo' for graphical apps will screw things up.


Thanks for the heads up I will use the gksudo in the future. So much to learn, so little brain.

---

