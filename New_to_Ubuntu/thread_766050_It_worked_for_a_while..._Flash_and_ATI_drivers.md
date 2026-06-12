---
title: "It worked for a while... Flash and ATI drivers"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by slavetothesound on 2008-04-25
I downloaded and installed Hardy Heron x86_64 this morning. Pretty much the first time I've used Linux on a computer of my own. And I liked it, except that I couldn't get flash to install. Apparently there is no flash for 64 bit hardy heron? not cool.. so I moved on to installing video drivers. went the the amd/ati site and downloaded the proprietary linux drivers for my Radeon x850, figure out how to install a .run file, then restart the computer. Now everything is so ungodly slow I can't use the computer. The desktop effects are horrible about making things lag after that. I was expecting an improvement with the new video drivers..

Anyone want to help me out a bit? Is there a non-proprietary driver for Radeon x850 and how the heck to I get flash to work. I've seen about 10 different suggestions for flash, all involving quite a few linux or command line terms that I'm not familiar with and after already spending several hours on this I'm not up to going through each one of them.

Sorry to say it, but i don't think that Bug #1 is going away anytime soon...  I'll be on my laptop running XP until I figure something out here...

---

### Post by MikeMLP on 2008-04-25
You are correct, there is no flash for x64 versions because Adobe refuses to package it.  Try Gnash -[http://www.gnu.org/software/gnash/]("http://www.gnu.org/software/gnash/") instead.  Search for it in Synaptic for easiest installation.  

As far as the video driver goes:  What driver was in use before you installed the proprietary driver?  If your experience on the proprietary driver is worse than on the free driver (assuming that the free driver was installed by default), try reverting back to the free driver by uninstalling the proprietary driver.  If Gnash does not suit your needs, you can always get full flash support by installing a x32 version of Ubuntu.


Note that all of your issues so far have to do with proprietary 3rd party programs and drivers.  Unfortunately, Ubuntu cannot control the quality of proprietary programs as they are not open source.  Try harassing ATI and Adobe for better x64 Ubuntu support.  Until then, weigh proprietary solutions against open source solutions and choose the better one.

---

### Post by slavetothesound on 2008-04-25
How would I go about rolling back the driver?
I went to System>Administration>Hardware Drivers and the window showed only one driver, an ATI driver, greyed out, and the window currently says no proprietary drivers are currently in use. I clicked the check box to enable it and it tries to download the driver, which doesn't do anything other than freeze the program. The servers are probably waaay too busy to be of any use for a few days until people are done downloading hardy heron.. I managed to cancel out of the download window, but now the hardware drivers window is stuck open for a good 5 minutes without responding which brings me to another question: What is the ctrl-alt-del equivalent in ubuntu? How to I force the window to close?

---

### Post by MikeMLP on 2008-04-25
For the video driver first try typing "glxinfo" at the gnome terminal and post the output here. That'll tell me what vid driver you are running.

To my knowledge, there is no Ctrl+alt+del equivalent (directly) under Ubuntu.  You can right-click on the upper or lower panel (the two bars at the top and bottom of the screen) and select "add to panel" and then select "force quit"  Whenever you click the applet button that will appear, a little window pops up, telling you to click on the misbehaving application.  Do so and it will close.

You can also use system monitor to end and kill processes.

Alternatively, you can open the gnome terminal, type "xkill" and click on the window of the offending program with the cursor.

If none of the above methods work because your machine is just too frozen, switch to a virtual terminal (alt+F1-F6), log in, type $pidof "insert program name here"  The output will be the program's process id (if you have multiple instances of the program open, sometimes you will get several process ids)  Then you can type: $kill "insert process id number here."  Press ctrl+F7 to get back to your desktop.  Save this last method for really difficult and complex situations (unless you enjoy complexity).

---

### Post by ABX323 on 2008-04-25
I could not get gnash to function properly with flash objects. I had to remove gnash and install 32 bit non-free adobe. There is a how-to and bash script on this board somewhere.

---

### Post by MikeMLP on 2008-04-25
I recently installed Gnash on a friend's new computer.  It worked, but I noticed that there were some strange flickering artifacts on YouTube.  Results might depend on the configuration.  But yes, my opinion of Gnash isn't exactly that high right now.  Though I do appreciate the effort that went into making something like that possible.

To be fair, I've noticed bugs with certain flash objects being displayed over other flash objects, when they should be displayed under instead... with the proprietary Adobe 32-bit driver.

Still trying various things - always worth a shot.

---

### Post by Michael.Godawski on 2008-04-25
For he Flash issue, did you try this out?

[http://ubuntuforums.org/showthread.php?t=765780](http://ubuntuforums.org/showthread.php?t=765780)

---

### Post by slavetothesound on 2008-04-25
I've seen that, Godawski, but I quit reading when it said it was not designed to work with Hardy Heron. Gumby now seems to disagree though so I'll try that out in the morning. I like to let the people who are in their own familiar environment try to get things working first before I go off exploring into the nethers of Ubuntu on a quest for flash.

And as for the video problem, I took the easy way out. Given that reinstalling takes about 20 minutes vs endless troubleshooting and that horrible horrible lag on everything I click on, it just wasn't worth the effort this time. When I've got unbacked up files at risk, then the troubleshooting will be worth it, and probably easier too when updates have been released and people have more experience with Heron. Thanks for your help guys, see ya tomorrow when I try to fix Flash!

---

