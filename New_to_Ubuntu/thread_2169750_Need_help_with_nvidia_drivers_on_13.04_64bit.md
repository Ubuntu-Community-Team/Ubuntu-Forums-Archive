---
title: "Need help with nvidia drivers on 13.04 64bit"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by velocityskater17 on 2013-08-23
I am new to ubuntu and having a hard time installing drivers for my GTX 660. With the video card installed i get a black screen followed by my display going to sleep. For now i am using the  on board video to get around.  When downloading from nvidia's site i get an error after the driver is downloaded. If someone could please help it would be greatly appreciated. Thanks!

---

### Post by r_avital on 2013-08-23
Hi,

I would avoid downloading from the nVidia site.  There are  genuine nVidia drivers available within the Ubuntu software sources, already compiled and ready to install.   Since you say you're new to Ubuntu, I'll give you the path to follow,  apologies in advance if you already knew or have tried some of this.

Go  into the Ubuntu Software Center, and in the search-box at the  top-right, enter "Synaptic"  (no quotes, of course).  This will bring up  a package called "Synaptic Package Manager" -- which is a better tool  than the "software center" for managing the installation and removal of  software on your system.

Once that's installed, go to your  dashboard and enter "synaptic" and it should bring up the Synaptic  Package Manager that was just installed on your system.  Run it, you'll  be prompted for your password,click on the search button, and enter nvidia in the search box that pops up.  You'll get a list of packages (not all drivers) related to nVidia.

I'm running with a GeForce GT 640, I've selected the package "nvidia-310-updates" from the list (scroll down a bit, you should see it).  Click on the check-box to the left of the package name, and select "mark for installation"  -- you'll get a message listing a few other packages that must be installed, one of them being the nVidia Settings manager for this specific driver version.

You probably also want to install the packages called "mesa-utils" and "mesa-utils-extra."  When you select them, you can read the description of these packages and what they provide.

When ready, click on the Apply button on the toolbar at the top of the screen, you'll be asked to confirm, and the installation will start.  You'll need to reboot (not simply log off/on), and that should install hopefully the correct driver for your card.

Note, that if there are problems, glitches, bugs with that driver, nobody can help you, because that is proprietary software, nobody but nVidia has access to the source-code.  These drivers are tested by the Ubuntu development teams and provided as is.  If there are issues, you might want to try different drivers, versions 304 and 313 are also available.

Good luck, and let us know how you make out.

---

### Post by velocityskater17 on 2013-08-23
I will try that when I get home tonight and let you know if it was successful or not. Thank you for the help!

---

### Post by velocityskater17 on 2013-08-23
After installing everything and then restarting it now boots up to a blank desktop with no dock

---

### Post by The Cog on 2013-08-24
That's a nuisance. 
If you press Ctrl-Alt-F1, do you get to a console login prompt? If so, can you log in and run the command **[FONT=Courier New][COLOR="#FF0000"]lspci -v[/COLOR][/FONT]** and look for your nvidia adapter. The last line is  "Kernel driver in use: " - which driver is in use?

---

### Post by oldfred on 2013-08-24
You mentioned on board video. Is this Optimus?

 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

### Post by velocityskater17 on 2013-08-25
I will look into the things said above and respond after i am home and able to do so.

Could it be that optimus is the issue? My cpu also has integrated graphics. If i read correctly optimus is what switches between integrated and the independent card?

---

