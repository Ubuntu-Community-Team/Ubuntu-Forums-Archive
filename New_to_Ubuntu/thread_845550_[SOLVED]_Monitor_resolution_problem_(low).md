---
title: "[SOLVED] Monitor resolution problem (low)"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by GkProf on 2008-06-30
Just upgraded from Feisty to Hardy. Came up in 640 x 480 only mode. Managed to get to 800 x 600 so it's usable. From what I've been reading, this is an xorg.config problem. Tried using:

sudo dpkg-reconfigure xserver-xorg

but that never gave any monitor-related options (only kybrd & mouse).

I also read that Gutsy (at least) had a GUI interface that should do this, referred to as "Screen and Graphics GUI admin tool," but I haven't been able to find anything like that in Hardy.

I've read about adding info to the Display section of xorg.config, but the info there doesn't match what's in mine--and there appear to be multiple sections in that file related to the monitor. That specific section in my file reads:

Section "Monitor"
  Identifier  "Configured Monitor"
  Vendorname  "Plug 'n' Play"
  Modelname   "Plug 'n' Play"
 modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525  -vsynch  -hssync
  Gamma  1.0
EndSection

But there are other sections the specifically mention NVIDIA (my graphics card)...? 

How much do I change?

My system: Dell Dimen 4600 2.4GHz, Dell 1704FPV 17" monitor (horiz: 30-81 kHz, vert: 56-76 Hz; optimal: 1280x1024 @ 60 Hz)
NVIDIA GeForce MX440 with AGP8x
I run a dual boot system with WinXP.

I'm not the most proficient, but if I have instructions, I can usually follow them if they don't assume too much. An automated or GUI-based solution would be nice, but I can type in terminal if I have to. Any help appreciated.

---

### Post by phidia on 2008-06-30
From the top panel menu System>Admin>Hardware Drivers do you get an option to enable your nvidia card?
Because your card is fairly old you probably have to use nvidia-legacy. If you can't get the card working from the 1st step I outlined open synaptic (package manager) and search for nvidia-legacy. Install that and reboot if that's an option. Sometime doing a distribution upgrade can cause problems while other times it works fine.

---

### Post by avtolle on 2008-06-30
To add "Screens and Graphics" to the Applications Menu: right click on Applications, select Edit Menu. Then, scroll down under Applications to "Other", in the right panel should be several options, Screens and Graphics being one of them. Select it, close out, and it should appear under Applications>>Other; or
From the terminal (Applications>>Accessories>>Terminal)```
gksudo displayconfig-gtk
```which puts you straight into the same application.

---

### Post by GkProf on 2008-06-30
Bingo! Simple solution to what seemed a complicated problem. Thanks!

- - -
To clarify, Phidia's post got me to the key solution (enabling the driver--why in the world did that not get passed on from my previous install?!), and avtalle's post (which came up while I was jotting the one-liner above) helped me find the Screens & Graphics tool that enabled me to get the settings optimized. Thanks to both of you.

---

### Post by ChaoticMike on 2008-07-09
When I use the displayconfig-gtk tool, the settings don't stick from one session to the next.  Any guesses?

I am trying to run a Compaq D510SFF without a monitor; I access it through VNC and have been trying a variety of approaches to persuade it to present 1024x768 via VNC.  A recent success was getting the machine to boot all the way through to an automated login without complaining about the lack of a connected monitor.

Now that I have mucked about with the displayconfig-gtk tool, I can at least change the settings once I have established a session.  But I know the final answer is out there somewhere...

All help appreciated by this Windows bod attempting to learn the labyrinthine ways of Linux...

Oh, I forgot to say that it defaults to 800 x 600.  Hence the desire to persuade it otherwise.

---

### Post by jwlittle on 2008-07-15
I am an absolute newbie to Ubuntu.  I have a Dell Dimmension 3000 with a built in video card.  When I first cleared off the hard drive and put Ubuntu on it--no problems!  My screen resolution was great!  About 2 weeks ago I downloaded the updates and my screen resolution is stuck in low resolution mode. I tried the terminal procedure and used "gksudo displayconfig-gtk"  I really don't know what I'm doing with it.  I tried changing the display options and the graphics options in Administration but there is nothing there.  This low res stuff is terrible.  Can I remove the last two updates and go back to where this worked?  My monitor is a HPw2207 LCD.  Any help would be greatly appreciated.  Thanks!

---

