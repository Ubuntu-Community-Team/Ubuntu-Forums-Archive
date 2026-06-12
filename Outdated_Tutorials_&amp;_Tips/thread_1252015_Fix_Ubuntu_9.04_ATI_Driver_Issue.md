---
title: "Fix Ubuntu 9.04 ATI Driver Issue"
date: 2009-08-28
forum: Outdated Tutorials &amp; Tips
---

### Post by gizmopower on 2009-08-28
**_UPDATED 06.10.09_**
 
This acctually works! 
I did it and got my raedon9800pro working in Ubuntu 9.04 
 
This tutorial is a bit different than the normal one on wiki ubuntu:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
 
_**[COLOR=black]All credits goes to Tyler how made this tutorial.[/COLOR]**_
**_Source:_** [http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)
 
Here is what I found:
 
Tutorial made by: Tyler
 
With the newest realease of Ubuntu (9.04 Jaunty Jackalope) came a major problem with support for older ATI graphics cards. Though these cards work with generic drivers, the ability to use dual heads and more advanced configurations has been lost. You may think that you can simply head over to AMD&#8217;s ATI driver page and get a driver, but the latest version of Catalyst does not support the older cards. &#8220;Maybe I can just download an older version of the driver,&#8221; might be what you are thinking, but the old driver is not compatible with the new version of xserver that is included with Ubuntu Jaunty.
The only way to use the old driver is to downgrade your xserver, which is actually not too hard. As long as you have an internet connection and some terminal skills, you are set.

**WARNING: Running commands as root (using sudo or su) can potentially damage your operating system. Be sure to CAREFULLY read EVERYTHING. Only proceed with these steps if you are confident with what you are doing.**
First off we will want to backup your current &#8220;sources.list&#8221; (the file that contains all of the repository information), so simply run the command:
> 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

Now, we will open up the original &#8220;sources.list&#8221; file and set it all back to the intrepid repositories. This can easily be done with Gedit&#8217;s replace tool. You can, of course, use any other text editor. To open the file in Gedit, just type the following into a terminal.
> 
sudo gedit /etc/apt/sources.list


In gedit, simply select the word &#8220;jaunty&#8221; anywhere in the file and click on &#8220;Replace&#8221; on the tool bar. When the dialogue box comes up, type &#8220;intrepid&#8221; into the box labeled &#8220;Replace With:&#8221; and click &#8220;Find&#8221; then &#8220;Replace All&#8221;
After replacing &#8220;jaunty&#8221;, save the file and close out of Gedit (or what ever text editor you used), and go back to a terminal and type:
sudo apt-get update
Once the repositories are updated, make sure all ATI drivers are uninstalled.
Now we will uninstall the current version of the xserver using the following command. (Note that gnome-session and fast-user-switcher-applet are specific to Ubuntu. Variants like Kubuntu and Xubuntu will not need to remove these because they are not installed)
> 
sudo apt-get autoremove xserver-xorg gnome-session fast-user-switch-applet

This may take a minute or so. After it completes, we will reinstall the xserver and also install the ATI drivers. (Note that gnome-session and fast-user-switcher-applet are specific to Ubuntu. Variants like Kubuntu and Xubuntu will not need to install them because they are not part of your desktop environment)
> 
sudo apt-get install xserver-xorg fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx libdrm2=2.3.1-0build1 gnome-session fast-user-switch-applet=2.24.0-0ubuntu6

When everything is finished installing, you will want to open up Synaptic Package Manager and lock all of the xserver-xorg*, fglrx*, xorg-driver-fglrx, libdrm2, gnome-session, and fast-user-switch-applet packages at their current version. This is done by selecting the package then going to the &#8220;Package&#8221; menu and clicking on &#8220;Lock Version&#8221;. You can also do this in the terminal by running:
> 
sudo su

then
> 
echo 'package-name hold' | dpkg --set-selections

Make sure to repeat the last command for each package that was installed by the previous commands. (This should total to about 47 packages or so.)
Once all of the xserver and ATI driver packages have been locked, run
> 
sudo cp /etc/apt/sources.list.bak /etc/apt/sources.list

and restart your computer.
Once your computer restarts, all you should be able to use all of the features provided by the ATI drivers that were just installed.
EDIT 06/05/09: After you restart, make sure to go to the Hardware Drivers manager under the &#8220;System&#8221; menu: Administration > Hardware Drivers and enable that ATI driver and reboot again. (Thanks Nicholas)
EDIT 07/15/09: I have added the 3D fix suggested in the comments. (Thanks Dario)
EDIT 07/25/09: I have also added the fix for the CPU problem that was suggested. (Thanks Flávio)
EDIT 08/04/09: I have once again added a user submitted fix for the Fast User Switcher. (Thanks Shaun)
EDIT 09/23/09: An important comment from Mark:
[INDENT]I did run into one issue- after activating the ATI driver and rebooting, I got a great big watermark in the bottom right corner of my screen with an AMD/ATI logo warning me of &#8220;Unsupported Hardware&#8221;.  If anybody else runs into this, this is how I fixed it:
1. Download the 9.3 legacy driver package from ati at this page:
[[COLOR=#00758f]http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&amp;product=2.7.4.3.3.3.1&amp;lang=English[/COLOR]]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&amp;product=2.7.4.3.3.3.1&amp;lang=English")
2.  Extract (don&#8217;t install!) the files from the 9.3 package to a folder with a command like:
sh ati-driver-installer-9-3-x86.
x86_64 &#8211;extract driverfiles 
3.  Replace your ATI &#8216;control&#8217; file with the one from this 9.3 package:
First back up your existing file just in case:
> 
sudo cp /etc/ati/control /etc/ati/control.backup

Then copy the new file in place:
> 
sudo cp driverfiles/common/etc/ati/control /etc/ati

4.  Reboot and profit!  No more watermark.

[/INDENT]**** 
**_Source:_** [http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

### Post by Impact9 on 2009-08-29
Fantastic! Got my 800XT working like a champ once again. One question though, can I unlock everything now that the driver is up to date?

---

### Post by gizmopower on 2009-08-30
To be honest, I don´t know! If you find out please post!

---

### Post by gizmopower on 2009-09-03
I have tried to unlock files but it is not possible! At least not on my Ubuntu!

I did a fresh install and reverted again without upgrading driver any further. 

It worked like a charm again, my Raedon 9800pro gives now about: 25000 5/sek - 5000 fps in gfxgears and Nexuis runs really smooth!

****

---

### Post by Derek3x on 2009-09-03
I tried this, but it did not work for me.  I am running a 9000pro card, and it just comes up to using the lowered graphical interface screen.  

I can unlock the files that were locked though, so I am going to undo all this and go back to the generic drivers.  

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by ssri on 2009-09-08
you should bracket the CLI commands using code/, so that others can easily copy and paste them in their terminal.

I would rather set my package preferences/pinning in /etc/apt/preferences, here's mine:

```

Package: xserver-xorg
Pin: version 7.4~5ubuntu3
Pin-Priority: 1001

Package: xserver-xorg-video-all
Pin: version 7.4~5ubuntu3
Pin-Priority: 1001

Package: xserver-xorg-input-all
Pin: version 7.4~5ubuntu3
Pin-Priority: 1001

Package: xorg-driver-fglrx
Pin: version 8.593-0ubuntu1
Pin-Priority: 1001

Package: fglrx-amdcccle
Pin: version 8.593-0ubuntu1
Pin-Priority: 1001

Package: fglrx-kernel-source
Pin: version 8.593-0ubuntu1
Pin-Priority: 1001

Package: libamdxvba1
Pin: version 8.593-0ubuntu1
Pin-Priority: 1001

Package: libgl1-mesa-dri
Pin: version 7.2*
Pin-Priority: 1001

Package: libdrm2
Pin: version 2.3.1-0build1
Pin-Priority: 1001

```

Now I can upgrade away without feeling guilty.  Unfortunately, synaptic does not read from preferences which is strange, but it is easy to lock the downgraded packages in synaptic (tools->) after searching for fglrx and xserver.  Also, people, keep them locked, as the moment you unlock and upgrade (ie kernel security update), your video packages (fglrx) will upgrade to 9.4, giving you a black screen on reboot, nice huh?  It does not affect me, as I use apt in CLI for managing my packages

---

### Post by TangoRom on 2009-09-11
ref: radeon 9800 pro with ubuntu 9.04 posted by Gizmo
Did everything step by step and got to the restart. I was just ready to activate driver under Hardware Drives and I’ve noticed my box is EMPTY: “No proprietary drivers are in use on this system”, so there’s nothing I can Enable.

Any thoughts/Advice plz !?

PS: I’m very green with linux :-? (but so much in Love with it =P~) at the moment being in process of learning. [linux process :P ]

THX to all of you!

---

### Post by tuxattack80 on 2009-09-11
Wow thanks this worked wonders for me. Have a dell e1505 and had some dusting and artifact effect when going to 9.04. Now it runs artifact free!!!!!

---

### Post by gizmopower on 2009-09-21
> **ssri said:**
> you should bracket the CLI commands using code/, so that others can easily copy and paste them in their terminal.
 
I would rather set my package preferences/pinning in /etc/apt/preferences, here's mine:
 
```

Package: xserver-xorg
Pin: version 7.4~5ubuntu3
Pin-Priority: 1001
 
Package: xserver-xorg-video-all
Pin: version 7.4~5ubuntu3
Pin-Priority: 1001
 
Package: xserver-xorg-input-all
Pin: version 7.4~5ubuntu3
Pin-Priority: 1001
 
Package: xorg-driver-fglrx
Pin: version 8.593-0ubuntu1
Pin-Priority: 1001
 
Package: fglrx-amdcccle
Pin: version 8.593-0ubuntu1
Pin-Priority: 1001
 
Package: fglrx-kernel-source
Pin: version 8.593-0ubuntu1
Pin-Priority: 1001
 
Package: libamdxvba1
Pin: version 8.593-0ubuntu1
Pin-Priority: 1001
 
Package: libgl1-mesa-dri
Pin: version 7.2*
Pin-Priority: 1001
 
Package: libdrm2
Pin: version 2.3.1-0build1
Pin-Priority: 1001

```
 
Now I can upgrade away without feeling guilty. Unfortunately, synaptic does not read from preferences which is strange, but it is easy to lock the downgraded packages in synaptic (tools->) after searching for fglrx and xserver. Also, people, keep them locked, as the moment you unlock and upgrade (ie kernel security update), your video packages (fglrx) will upgrade to 9.4, giving you a black screen on reboot, nice huh? It does not affect me, as I use apt in CLI for managing my packages
 
 
Tanx for youre input!
 
TangoRom:
I dont know what could be wrong if you followed step by step! Maybe try again?

---

### Post by romeu.romeo on 2009-09-26
> **TangoRom said:**
> ref: radeon 9800 pro with ubuntu 9.04 posted by Gizmo
Did everything step by step and got to the restart. I was just ready to activate driver under Hardware Drives and I’ve noticed my box is EMPTY: “No proprietary drivers are in use on this system”, so there’s nothing I can Enable.

Any thoughts/Advice plz !?

PS: I’m very green with linux :-? (but so much in Love with it =P~) at the moment being in process of learning. [linux process :P ]

THX to all of you!


Hi all, i'm on the same boat as TangoRom,
did all the steps but no driver to enable.
i have a mobility 9700 
(ATI Technologies RV350 (Mobility Radeon 9600 M10) 64MB VRAM)

Any ideas what to do?

Thanks.

---

### Post by jstierman on 2009-09-28
Thanks, got my X700 Mobility running the ATI proprietary driver now.  Haven't tested any video, games, etc yet, but just booting to the GUI is already a step in the right direction!  Followed your directions on a fresh install of Jaunty and no problems yet.

---

### Post by corl45 on 2009-10-01
I have an Ati Radeon x1650 (pcie) and the x-server works with accelerated gfx but it wont fully unlock its capabilities.  When i tried this, i restarted and once the ubuntu loading bar was done, the screen went black... and stayed black. i had to reinstall ubuntu.  any ideas?

---

### Post by gizmopower on 2009-10-06
The tutorial has been updated **_06.10.09 _**
 
Tanx again to Tyler and comunity at TanCom

---

### Post by romeu.romeo on 2009-10-19
"make sure all ATI drivers are uninstalled."

Thats the only step that i'm not sure,
i am going to try again with a fresh install, with gdm stoped and all in F2 mode.

by command line how can i confirme this?

thanks

---

### Post by maddogz420 on 2009-10-20
I'd like to thank you a **ton** for this tutorial, I finally have my 9600 pro working in ubuntu and can run ubuntu full time now for my dev work.

Of course, I really wish I had a better video card and not had to do this in the first place ;-)

---

### Post by jstierman on 2009-11-16
Anyone try this on Karmic yet?

When I upgraded, I had the "flickering prompt" screen problem.  Solved it by going back to my old xorg backup file (before installing this ATI driver).

But I will probably try the same steps as Jaunty on Karmic to try to get the old ATI driver to work.  Will post results (though I may not try it for a few days or a week... just whenever I get free time).

---

### Post by ssri on 2009-11-17
ATI's legacy driver only supports kernels up to 2.6.28 and xserver 1.5.x.  So, to get it working in karmic, you would have to downgrade both the kernel and xserver, something most people are not too keen to do.

---

### Post by Erised on 2009-11-24
Tried this tutorial on Karmic and it doesn't work at all.
Nothing that it is on any forum or any tutorial doesn't work for me... Which means I have to switch back to Windows... Pfff, and I was starting to like it a lot, but can't stay like this, without my videocard...

---

### Post by w-sky on 2009-12-16
> **Erised said:**
> Tried this tutorial on Karmic and it doesn't work at all.

Bad news... that was my first question, when I found this tutorial and started reading.

I have been using Gutsy on a notebook with ATI onboard graphics, ATI proprietary driver installed and enabled, and now I did a new install with 9.10.

Hope anyone did find a solution...?!?

---

### Post by YosefKaro on 2009-12-17
And this was beginning to look good until the last few comments.  I also need some guidance in how to do this for karmic.  Anyone have any luck with this on karmic?

-Yos

---

### Post by w-sky on 2009-12-19
Right. But here is another thought: Do you really have some **good, fast 3D** ATI chipset? If you don't, do not bother any more. The latest video driver from X.Org works very well and fully satisfactory with simple ATI cards, like on my notebook with its "Radeon Xpress 200" chipset. Even with the "extra" setting for Compiz effects it's all nice to look at - and 100% open source. ;)

---

