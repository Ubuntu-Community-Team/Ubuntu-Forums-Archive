---
title: "using DBAN on Windows 7/Ubuntu 12.04 prior to reloading 12:04"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by pine marten on 2012-11-17
I do not know if this belongs in the beginner section, but since this is my first use of the forum, that is where I assumed it would go

A while back I purchased a Dell Inspirion with Windows 7 installed.  I found a site which walked me through setting up dual operating systems and added Ubuntu 12.04.  I almost never use Windows.  I wanted it only for using the National Geographic map program.

Everything seems to have worked Ok, but a day or two ago I got a message indicating the boot partition was nearly full.  I ran Gparted and found the boot partition was over 90% full.  However, I do not know if it was 90% full when I set up the dual system.  I do not know if updates add to the boot partition.

Also when the dual system was set up the booting wound up being done with the Windows boot loader.  In addition I am no longer able to gain access to BIOS by pressing F2 or F12

Since I use the map program infrequently I want to simplify my computer by having it run only Ubuntu 12.04 so I'd like to use DBAN and then reload 12.04, but I do not know how to do this.

When I restart the computer I can hear the CD drive spin first so I'm fairly certain it will boot first from a CD.  Does this also mean it will boot from a stick in a USB?  Assuming a successful DBAN wipe, will 12.04 automatically partition itself?

I cannot operate from the terminal.  I only use the GUI.

Thanks for any advice.

---

### Post by Paqman on 2012-11-17
> **pine marten said:**
> 
Also when the dual system was set up the booting wound up being done with the Windows boot loader.


This means you installed using Wubi, which is the Windows installer for Ubuntu.

> I want to simplify my computer by having it run only Ubuntu 12.04 so I'd like to use DBAN and then reload 12.04, but I do not know how to do this.

No problem at all. Using DBAN isn't necessary. If you allow it to the Ubuntu installer can wipe your whole drive before installing Ubuntu over the top of everything.

Simple boot from an Ubuntu CD or USB and follow the prompts on screen. One of the options presented will be a full wipe, leaving only Ubuntu.

Obviously you'll need to back up your data before doing any of this.

> Does this also mean it will boot from a stick in a USB?

Not necessarily. Boot device priority is set in your BIOS, there will be separate settings for CD and USB.

> Assuming a successful DBAN wipe, will 12.04 automatically partition itself?

Yup.

> 
I cannot operate from the terminal.  I only use the GUI.


You'll be fine, the installer is totally GUI. The terminal is really only required when stuff is really broken. If you don't want to ever use it your probably won't ever have to.

---

### Post by pine marten on 2012-11-19
Paqman solved my problem by having me reload 12.04.  This removed Windows, the 12.04 on the disk, and any other data, and then gave me a hard drive with only 12.04.  I reloaded the date from a couple of sticks and now have a Windowless hard drive.

However, I still cannot access BIOS.  When the computer is turned on a Dell screen shows up indicating that pressing either F2 or F12 will get me to BIOS.  Instead when either of the keys is pressed a message shows up--keyboard failure--and the keyboard is inoperative until 12.04 is loaded.  Everything works as it should other than being unable to access BIOS.

---

