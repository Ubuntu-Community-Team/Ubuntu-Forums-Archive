---
title: "Blank Screen / no GRUB access after installing Ubuntu 15.04 on Dell PowerEdge 2650"
date: 2016-08-14
forum: New to Ubuntu
---

### Post by eagletalontim on 2016-08-14
Hello all!  I am new to this and am hoping to get some help if possible.  I have downloaded the 32 bit version of Ubuntu 15.04 and have installed it on my Dell PowerEdge 2650.  The system is set up with 4 hard drives, one as the boot drive and the other 4 as RAID.  The install seems to go perfectly, but once the system requires reboot, the screen always goes blank and my monitor says "Input Not Supported".  The graphics is running from the on board controller.

I have tried to hold the Left Shift Key, Right Shift Key, ESC, Arrow Down, CTRL+Alt+F1 and still cannot access the GRUB screen I keep reading about.  I can see the words "Starting GRUB" or something like that right before the screen goes blank.  I have even tried letting the screen go blank, then pressing the arrow down key, then "Enter" and still nothing.  Using the install disk, I tried using "nomodeset" as a boot option on the "first disk" which did not work either.  With all ideas gone, I am forced to ask for help :)  Anyone have any suggestions on what to try now?

---

### Post by eagletalontim on 2016-08-15
Anyone?  Do I need to go to an older Ubuntu installation? Is there anything I can try?

---

### Post by grahammechanical on 2016-08-15
Ubuntu 15.04 reached the end of its support life the beginning of February 2016. So, you should be using either 14.04.5 (support until April 2019) or 16.04.1 (support until April 2021)

[URL="https://wiki.ubuntu.com/Releases"]https://wiki.ubuntu.com/Releases

[/URL]Did the live session work alright without any blank screen? The live session uses the open source video driver. When installing if we tick the box "Install third party software" as well as getting some third party audio & video codecs we also get a proprietary video driver. So, if the live session does not have any video display problems but the install session does have them it is worth installing without ticking that box.

The latest proprietary video drivers often drop support for older video adapters. We can get the third party audio & video codecs after installation by installing Ubuntu Restricted Extras. We can install a proprietary video driver after installation by going to System Settings>Software & Updates>Additional Drivers tab. We need to be connected to the internet and to allow the utility time to find the drivers on the internet. You might get the option of a legacy driver.

Do you have hybrid graphics? An onboard Intel graphics adapter and a discrete Nvidia or AMD graphic adapter? 

Regards

---

### Post by eagletalontim on 2016-08-15
The poweredge does not have a DVD reader so I cannot use a live CD and the system cannot boot from USB unfortunately.  I am looking into the network installer, but am not sure it will work.

After doing more research, I found that this machine has ATI Rage chipset.  Here is what I found :

"Next I extracted the Kubuntu version of Ubuntu 14.04 ISO to my USB Thumbdrive.
The reason I chose Kubuntu as it works well with the ATI video chipset on
these older [Dell]("http://accessories.us.dell.com/sna/default.aspx") servers.  The ATI Rage chipset in these PowerEdge servers
will crash and burn if you try and load the normal Ubuntu desktop."

This is from here : [http://www.dslreports.com/forum/r30449426-Install-Kubuntu-and-Boinc-on-a-legacy-PowerEdge-2650](http://www.dslreports.com/forum/r30449426-Install-Kubuntu-and-Boinc-on-a-legacy-PowerEdge-2650)

I can't keep burning CD's and the system's floppy is useless :(  I would really like to install Ubuntu on this system so I can use it for a network storage.

---

### Post by yancek on 2016-08-15
I had that error in earlier versions of Ubuntu and what fixed it for me was changing the line below in the /etc/default/grub file.

> #GRUB_GFXMODE=640x480 

Remove the hash mark ( # ) from the beginning of the line.  If you can boot in recovery mode or get to a command prompt, you should be able to make that change with a text editor such as vi.  You would then need to run:  sudo updat-grub.  If you can't boot to a prompt, you would have to chroot to make the change and run sudo update-grub.

---

### Post by eagletalontim on 2016-08-15
I have no access to anything since I can't see the screen :(  I have 2 "live" CD's.... one is a very old Ubuntu Netbook Remix 9.10 and the "Ultimate Boot CD".  I only have 1 more blank CD left which I want to save if possible.  I am quite new to setting up Ubuntu and working with any of the commands

Since I can't boot to recovery mode or get to a command prompt, how can I change that file?  I have tried to edit it while using a live CD, but it mounts as read only and I am not sure if running "sudo update-grub" will affect the actual filesystem.

Ok, so I have finally gotten to a TTYL terminal and that is as far as I know how to get to.  If I hit CTRL + Alt + F7 to switch back to the Ubuntu Desktop, the monitor goes back into the "unsupported" mode and nothing...  If I switch back to the TTYL, I can see the screen.  How can I fix the desktop mode?

---

### Post by eagletalontim on 2016-08-16
After hours of playing with this system and using the Ultimate Boot CD, I finally got Ubuntu 16.04 Desktop version installed on the PowerEdge and I can login to the server via the graphical display, but that is as far as it goes.  The screen just shows the background image and the mouse pointer... nothing else.  Should I install something else?

I am also having an "aacraid" SCSI hang error while in the TTYL screen.  It pops up randomly.  Is there a fix for that?

---

### Post by gordintoronto on 2016-08-16
How much memory on this computer? Have you considered Ubuntu Server, the command-line version?

Good for you, trying to get some use out of a 14-year-old computer, but really...

Where I live, there are dealers selling five-year-old off-lease computers for just a bit more than $100 (US) and they will run any version of Linux very nicely.

---

### Post by eagletalontim on 2016-08-16
I have not tried to install the 16.04 Server version, only the 15.04 which did the same thing.  This server was given to me and I was hoping it could easily accept some kind of linux OS and I could use the RAID 5 setup for network storage.  I have installed Linux before on desktop systems without a problem, but this server is being a PITA!

The server has 2G of RAM and 5 hard drives.  One drive is setup as the "Boot" drive, and the other 4 are set in a RAID 5 configuration.

The whole reason I am trying to use this server is because of the RAID and it was free :)

---

