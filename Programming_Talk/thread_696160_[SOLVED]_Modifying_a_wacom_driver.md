---
title: "[SOLVED] Modifying a wacom driver"
date: 2008-02-13
forum: Programming Talk
---

### Post by Robynsveil on 2008-02-13
Hi,
I have a problem I actually share with a number of other users, and that is: my Wacom Bamboo tablet doesn't work properly in the GIMP. The issue manifests itself as an offset between the cursor (the arrow thingie) and the drawpoint (brush).
First, a bit of background.
I have the Wacom Bamboo MTE-450. I downloaded and installed the most recent driver -- as per recommendation by [this howto]("http://ubuntuforums.org/showpost.php?p=4253232&postcount=133") -- from the [LinuxWacom Project]("http://linuxwacom.sourceforge.net/index.php/main") site. The driver is 0.7.9-7, said to work on a variety of Wacom tablets, including the Bamboo series.
Another Bamboo owner with a bit of programming experience has tracked the problem down to a statement in the wcmCommon.c file. He made a modification which he said resolved the issue for him. However, he was rather cryptic in his explanation and seems to have since dropped from the boards, as I am unable to discuss this issue with him.

Before I launch into a description and discussion on how best to resolve this problem, am I in the right forum?
Thanks so much for replying...

---

### Post by anindya_m on 2008-02-13
Hi I have a bamboo fun and am using driver version 0.7.9-7 compiled from source. The alignment is correct in my case, exactly the same as the normal mouse.

However the reversed mouse wheel bug is still there it seems. I have modified the driver source (it is coded well, so is relatively easy to understand) and fixed the wheel issue for my tablet. It works perfectly now :)

---

### Post by Robynsveil on 2008-02-14
> **anindya_m said:**
> Hi I have a bamboo fun and am using driver version 0.7.9-7 compiled from source. The alignment is correct in my case, exactly the same as the normal mouse.

However the reversed mouse wheel bug is still there it seems. I have modified the driver source (it is coded well, so is relatively easy to understand) and fixed the wheel issue for my tablet. It works perfectly now :)

Good on ya - so you understand the code enough to understand what's doing what, may I assume? My tablet is simply the Wacom Bamboo (not the fun). I wish I could figure out how to best address this issue, but it seems that the code is doing clever geometry maths which is a bit beyond me.

In [this post]("http://ubuntuforums.org/showpost.php?p=3059775&postcount=220") AlumaSqrl suggests changing this:
```
totalWidth += screenInfo.screens[i]->width;

```
in the xf86WcmSetScreen() function to this:
```
totalWidth = screenInfo.screens[priv->currentScreen]->width;
```

I was a bit uncomfortable with that, since the operator had changed. I'll grant you I don't really know what it does, really, but I left the operator the same:
```
totalWidth += screenInfo.screens[priv->currentScreen]->width;
```
and recompiled. However, I still have the same offset problem. I've left a Bug report on the Wacom Bug tracker site, but haven't heard back from them as yet. With as many people as seem to have this problem with this tablet and the GIMP, I'm surprised not more has been said about it.

So, what do *you* think of this change? DO you think it has any bearing on the problem, or do you think something else might be causing it?

Thanks in advance for your reply...

---

### Post by anindya_m on 2008-02-14
Okay so in your case the problem is that the drawing point is not exactly at the tip of the arrow? I assume you are not referring to the offset to the brush icon which is displayed a few pixels away (towards south-east) from the mouse arrow. 

I have a few questions about your setup:

1. Are you using multiple monitors? My Feisty and Gutsy computers both have one monitor each.

2. Are you sure you are using the X driver from the wacom project package? I ask this because I am not. The X part of the driver (wacom_drv.so) I am using is the one that came with ubuntu, and I just compiled and installed the kernel part wacom.ko, replacing the ubuntu supplied file. The modifications I made are in the kernel driver.

---

### Post by Robynsveil on 2008-02-15
> **anindya_m said:**
> Okay so in your case the problem is that the drawing point is not exactly at the tip of the arrow? I assume you are not referring to the offset to the brush icon which is displayed a few pixels away (towards south-east) from the mouse arrow. 

I have a few questions about your setup:

1. Are you using multiple monitors? My Feisty and Gutsy computers both have one monitor each.

2. Are you sure you are using the X driver from the wacom project package? I ask this because I am not. The X part of the driver (wacom_drv.so) I am using is the one that came with ubuntu, and I just compiled and installed the kernel part wacom.ko, replacing the ubuntu supplied file. The modifications I made are in the kernel driver.
Excellent questions, both of them, and thank you again for taking an interest in my problem. First off, the offset to which I refer is the distance between the pointer-cursor that you use generally to click on things. I can accurately use my stylus as a mouse - there is no difference (offset) between the target area and the cursor pointer in any and all programs (including even the GIMP!!) *when* is use the stylus/tablet as a mouse. However, as soon as the cursor is over a drawing area, the offset magically appears. Here is a 600 x 800 image done in the GIMP to illustrate the issue:
[IMG]http://www.tightbytes.com/images/ubuntu/Cursor-stylus.jpg[/IMG]
A bit of a show-stopper.

Now, to your other questions. This PC uses only one monitor, an old Hitachi CM753ET CRT that I'm hoping to replace before too long with a 24 inch LCD.

As to question #2, I'm not exactly sure how to answer your question. I downloaded the development package 0.7.9-7 from the [LinuxWacom Project site]("http://linuxwacom.sourceforge.net/index.php") which, I assume, included the x driver? possibly? So are you suggesting that I copy over the one in the package bundle with the one installed on my system before I built it? Of course, that one would now be corrupted, but I suppose I should be able to find it again somewhere...

---

### Post by anindya_m on 2008-02-15
Okay I understand the offset problem. If you are up to it, can you run one more test? You see I use this program called gromit to paint on the screen (on top of displayed windows) during presentations etc.  It has a crosshair which indicates the drawing point. Can you install this (it's a small package in the repos) and find out if the offset problem is there for gromit also? Gromit can be started by typing
```
gromit -a
```
at the terminal. Press Alt+Pause to exit.

My second question was about your driver setup. The wacom driver is split into two parts: a USB kernel driver which sends signals to the linux input subsystem, and an Xorg driver which processes inputs for X. I did not run "make install" after compiling the driver, but simply overwrote the kernel driver file wacom.ko with my compiled version. This seems to be working on my Gutsy desktop and Feisty laptop. I  think running make install replaces both the drivers.

---

### Post by Robynsveil on 2008-02-15
> **anindya_m said:**
> If you are up to it, can you run one more test? You see I use this program called gromit to paint on the screen (on top of displayed windows) during presentations etc.  It has a crosshair which indicates the drawing point. Can you install this (it's a small package in the repos) and find out if the offset problem is there for gromit also?

I'm happy to run as many tests as you can think of... if we can get to the bottom of this! I installed Gromit and ran it - here's a screen capture of my results:
[IMG]http://www.tightbytes.com/images/ubuntu/Gromit.jpg[/IMG]
I feel we're getting somewhere now.

> **anindya_m said:**
> My second question was about your driver setup. The wacom driver is split into two parts: a USB kernel driver which sends signals to the linux input subsystem, and an Xorg driver which processes inputs for X. I did not run "make install" after compiling the driver, but simply overwrote the kernel driver file wacom.ko with my compiled version. This seems to be working on my Gutsy desktop and Feisty laptop. I  think running make install replaces both the drivers.
I'm going to summarize the instructions that were given on [this page]("http://ubuntuforums.org/showpost.php?p=4253232&postcount=133") (starting with item 6, since the other stuff I've already done):
```
./configure --enable-wacom
make
sudo make install

```
You're suggesting leaving out the last of these commands, then? I'm assuming this last command takes the compiled driver which was living somewhere in the /linuxwacom-0.7.9-7 folder and ... does *what* with it? installs it? and what does *install* involve? isn't it just a matter of copying over existing drivers?

I do have the questions, don't I?

Okay, so the approach I should be taking is:
```
./configure --enable-wacom
make
```
which then compiles the driver?

Then, find the existing driver in:
> /lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/wacom.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/usb/input/wacom.ko
/lib/modules/2.6.17-11-386/kernel/drivers/usb/input/wacom.ko
/lib/modules/2.6.17-10-386/kernel/drivers/usb/input/wacom.ko
/lib/modules/2.6.20-16-386/kernel/drivers/usb/input/wacom.ko
/lib/modules/2.6.22-14-386/kernel/drivers/input/tablet/wacom.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko

...and replace them all? for both -generic and -386?

This is the closest (I think) I've been to finding a solution to this! I'm so excited!

---

### Post by anindya_m on 2008-02-15
Hi. The install command basically takes the .ko and .so files corresponding to the  drivers and copies them into the appropriate system directories, sets permissions, runs ldconfig and/or depmod if necessary, etc.

It seems the gromit test is producing the same result as gimp. Okay.

I suggest you first restore the X driver. If you can find another feisty machine just copying over the file from there should work. You only need to replace the .ko driver file in your running kernel directory:

```
./configure --enable-wacom
make
sudo cp path/to/wacom.ko /lib/modules/`uname -r`/kernel/drivers/usb/input/wacom.ko
```

The wacom.ko should be in the src directory. Just use:
```
find . -name wakom.ko
```
from the linuxwacom package directory.

After the new driver is copied, exit X, and reload the kernel module from tty1 (accessible thru Ctrl+Alt+F1):

```
sudo /etc/init.d/gdm/stop
sudo rmmod wacom
sudo modprobe wacom
### plug in the tablet at this point  ###
sudo /etc/init.d/gdm start

```

Let's hope it works!

---

### Post by Robynsveil on 2008-02-16
Hi Anindya M. Hoping I did justice to your instructions, here's what I did:

1) I first restored the X driver. I have a laptop also running Gutsy, so it was just a matter of finding wacom.ko with the locate command. I copied this to my /home/robyn/wacom/linuxwacom-0.7.9-7/src/2.6.22 folder.
Correct so far?

2) Then I issued a:
```
./configure --enable-wacom
make

```
3) and finally a:
```

sudo cp /home/robyn/wacom/linuxwacom-0.7.9-7/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-386/kernel/drivers/input/tablet/wacom.ko
```
...since I'm running Gutsy, and the folders where stuff lives is slightly different in Gutsy.

4)After the new driver was copied, I exited X, and reloaded the kernel module from tty1 using the following code:

```

sudo /etc/init.d/gdm stop
### unplugged the tablet  ###
sudo rmmod wacom
sudo modprobe wacom
### plugged in the tablet  ###
sudo /etc/init.d/gdm start

```

I actually rebooted, just to be sure. However, no joy. The offset is still there.

I'm sure I did something wrong, however. From what I've outlined, can you see where I might have gone astray?

---

### Post by anindya_m on 2008-02-16
Hi there. I think the X driver is not replaced yet. The file is /usr/lib/xorg/modules/input/wacom_drv.so. This also got replaced when you installed the wacom package, and needs to be restored. Just check the md5sum of this file on both machines to confirm that the file was indeed modified.

---

### Post by Robynsveil on 2008-02-16
Anindya, that did it! It now works! No more offset. You are brilliant. This is going to make a lot of people very, very happy, let me tell you. I believe that those threads that explain how to install a wacom tablet need this key information.

So, I'm afraid I still don't understand *why* it works, Anindya. The sudo make install, as you said, did what sounded to me like crucial things: copying the .ko and .so files corresponding to the drivers into the appropriate system directories, setting permissions, running ldconfig and/or depmod if necessary, etc... all critically important stuff, as I see it. Do I deduce from this, then, that the re-built .so and .ko files from[ this process]("http://ubuntuforums.org/showpost.php?p=4253232&postcount=133") are invalid?

What I've ended up with is a modified wacom.ko file in:
> /lib/modules/2.6.22-14-386/kernel/drivers/input/tablet

yet the original wacom_drv.so file in:
>  /usr/lib/xorg/modules/input


Does this sound right to you?

In any event, it works, thanks to you, Anindya. You're a legend!

---

### Post by anindya_m on 2008-02-16
Hi. My take is that the linux wacom guys messed up a little in the X driver. There are changes in the coordinate formulae in few places. I did not read the code thoroughly yet to identify exactly what went wrong, but it seems to me that the screen coordinates for the stylus device are being incorrectly calculated by X, even when the kernel driver is sending the right coordinates; this is why your normal mouse pointer was working, while the brush wasn't. However note that this is the beta version of the driver. I am sure it will be fixed soon.

I am happy that you got it to work, congratulations and thanks for the kind words :) Enjoy your Bamboo!

---

### Post by Jholen on 2008-03-03
Hi,
this guide look very promising... I have the same problems, my cursor, in gimp and in Inkscape, has and terrible offset and my tablet work fine like mouse in any type of application (work in a wrong way, with the offset, when I use the input device option in gimp or inkscape for enable the pressure level). The difference, for me, is about the wacom tablet: I use a Intuos 3 tablet, and I install  this in a different way from baboo, so I cannot use the guide here explained. It work fine like mouse, but I cannot use pressure (I must activate it in gimp option, when active this I have offset issue) and I don't know how configure the tablet keys. 
Anyone as a solution?

Thanks, sorry for my bad English

PS I'm a very noob linux user...

---

