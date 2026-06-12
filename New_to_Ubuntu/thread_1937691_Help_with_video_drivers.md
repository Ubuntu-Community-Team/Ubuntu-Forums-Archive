---
title: "Help with video drivers"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by masterman934 on 2012-03-08
Hi there!

I have just installed Ubuntu and I'm trying to set everything up and running. I'm pretty much new to Linux so I'm asking for your help :)

Lets start with drivers:

I have been offered by Ubuntu to install fglrx driver for my video and I did. After that I restarted OS and then was offered to install some post-release updates for fglrx but the installation failed and the fglrx then got disabled (or at least thats what I think has happened). Is this normal? It seems to me that my video drivers are not working properly:

When I drag windows around the screen they are not moving smoothly but rather freezy. 
Also in the system information it says that my graphics is VESA: MADISON - its ATI Mobility HD 5650
Also I have the feeling that my resolution is very low - it says its 1366:768 but the icons on the left side of the screen seems to me pretty large. And I can't get the frequency higher than 60Hz. Here is a screenshot of my desktop:

[http://i174.photobucket.com/albums/w94/dzhigarov/Screenshotat2012-03-08170210.png](http://i174.photobucket.com/albums/w94/dzhigarov/Screenshotat2012-03-08170210.png)

Please, help me out with my video drivers :)
Thanks in advance!

P.S. If it helps, my laptop is:

Intel i3-380M (2.53GHz) Mobile CPU
Chipset: Mobile Intel® 5 Series Express Chipset (HM57)
Memory: 4GB 1333MHz DDR3 Dual Channel memory
Video: 1GB ATI Mobility Radeon HD 5650 Graphics
Screen: 15.6" High Definition WLED display with True Life technology
Resolution: 1366 x 768
Hard disk: 640GB Serial ATA (5400RPM) HDD
Optical device: 8X DVD+/-RW Drive
Network/interfaces:
Bluetooth: Dell Bluetooth 365
Network: Integrated network connector 10/100 LAN (RJ45)
Interfaces: (3) USB 2.0 compliant ports (1) eSATA/USB2.0 HDMITM Port VGA Port AC adapter connector Audio jacks (1 line-out, 1 Mic-in); RJ45
Wireless: Dell Wireless 1501 (802.11g/n)
Multimedia
Sound card: integrated

---

### Post by Diametric on 2012-03-08
Not sure about the driver installation, but the desktop resolution looks right to me.  Maybe others can comment about whether or not the Unity (the desktopn manager) icons can be changed in size.

Glad you made the switch to Linux - good luck and enjoy!

---

### Post by masterman934 on 2012-03-08
Thank you about the response!

Anyway, any ideas on how to update my graphic drivers? My eyes are really starting to hurt because of the low frequency...

---

### Post by anewguy on 2012-03-08
Indeed, your screen capture looks normal to me.

Keep in mind that normally the Catalyst control center will only present the resolutions and timings that your monitor reports back.  If you don't feel it's correct just check the documentation for your monitor and see if it offers any other resolutions and timings.

Dave ;)

---

### Post by grahammechanical on 2012-03-08
Large icons in the Launcher are standard. They can be adjusted.

You need to install Compiz Configuration Settings Manager (CCSM). Use the Software Centre by searching for Compiz and select CompizConfig Settings Manager.

When it is installed you will find it in the Dash by searching for Compiz

When it loads look for Ubuntu Unity Plugin. click on that Label and under the Experimental tab you will see an option for Launcher icon size.

Why do you want to change the refresh rate? The monitor settings are taken directly from a configuration file in the monitor so that we are always using the manufacturer's specified optimum settings.

Try using Additional Drivers again to activate the driver or to change to another one.

Regards.

---

### Post by bronquel on 2012-03-08
Your screen shot looks normal to me as well, and the refresh rate (60hz) is fairly standard.  I don't think I've seen higher than that since I had a CRT monitor (I could be wrong).

If you want to shrink the unity buttons on the left side, you can do something like this (I just googled this):
[http://askubuntu.com/questions/39550/how-do-i-shrink-the-unity-launcher-icons-to-make-them-smaller](http://askubuntu.com/questions/39550/how-do-i-shrink-the-unity-launcher-icons-to-make-them-smaller)

One other option I have seen is to set your screen resolution higher than your monitor can physically display.  This is usually used to get a netbook to be more usable, and i have friend who swears by this:
[http://www.omgubuntu.co.uk/2010/11/set-your-screen-resolution-higher-than-you-should-with-newrez/](http://www.omgubuntu.co.uk/2010/11/set-your-screen-resolution-higher-than-you-should-with-newrez/)

---

### Post by bronquel on 2012-03-08
> **grahammechanical said:**
> Large icons in the Launcher are standard. They can be adjusted.

You need to install Compiz Configuration Settings Manager (CCSM). Use the Software Centre by searching for Compiz and select CompizConfig Settings Manager.

When it is installed you will find it in the Dash by searching for Compiz

When it loads look for Ubuntu Unity Plugin. click on that Label and under the Experimental tab you will see an option for Launcher icon size.

Why do you want to change the refresh rate? The monitor settings are taken directly from a configuration file in the monitor so that we are always using the manufacturer's specified optimum settings.

Try using Additional Drivers again to activate the driver or to change to another one.

Regards.

You beat me to the punch!  good to know I wasn't the only one thinking to shrink the button sizes with compiz.

---

### Post by masterman934 on 2012-03-08
60 Hz is standard? I'm pretty sure I work on a higher frequency under windows. I will surely check this out next time I reboot...

But what about the 'little freezing' dragging of windows under unity? Is this a problem in the GUI or is it my graphic drivers? 

I'm pretty sure something is wrong with these drivers because i followed this guide [http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/](http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/) and got Gnome Shell but its even worse than unity - a lot of freezes, glitches etc... 
The gnome classic works smooth though...

---

### Post by bronquel on 2012-03-15
> **masterman934 said:**
> 60 Hz is standard? I'm pretty sure I work on a higher frequency under windows. I will surely check this out next time I reboot...

But what about the 'little freezing' dragging of windows under unity? Is this a problem in the GUI or is it my graphic drivers? 

I'm pretty sure something is wrong with these drivers because i followed this guide [http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/](http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/) and got Gnome Shell but its even worse than unity - a lot of freezes, glitches etc... 
The gnome classic works smooth though...

If i'm wrong about 60hz being standard let me know - i just haven't seen higher than that on LCD/LED monitors (from the computer side - I have seen LCD/LED monitors that can do 120hz).  

As for the freezing of dragging windows around, it sounds like it is the GUI (aka desktop environment), as the drivers would be the same between gnome shell (I assume gnome 3?), unity, and gnome classic(gnome 2).  I would try disabling compiz to see if that helps - I assume that is where the problem is.  I did find a bug that seems to describe your problem: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/891744](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/891744)

Depending on how new your laptop is, it takes a little bit for new graphics cards (and other things like wireless cards) to be supported in my experience.  When i started using ubuntu I had to use ndswrapper and my windows drivers to get my wireless card working.  The next distro did it automatically.  Next version of ubuntu comes out in a month (april 26th) and you may find everything works out of the box.

---

