---
title: "Unknow Monitor is display properties"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by spydrs on 2012-01-18
Hi. I have installed Ubuntu 11.10 in Vmware workstation. The problems that I am facing are that when I click on display properties it shows Unknown monitor. I can change the resolution though but the monitor is not detected. 

Plus after login I get a window which says "couldn't apply the stored configuration for monitors".

Also, I am unable to install Nvidia drivers. I have searched over some forums and followed some steps but when I go into Additional drivers and check it says no proprietary drivers are installed. 

I have also tried to install the drivers through synaptics but no luck. 

I installed Gnome3 but that too isn't working properly. After installing it I have no additional windows, just a black bar at the top which has 2 tabs applications and places.

I am guessing that Gnome is not working because the display drivers are not installed correctly?

any help will be appreciated. Thanks.

---

### Post by jerrrys on 2012-01-20
Is the pic below what your talking about? _If so;_ not a worry

How many monitors are you running?  At this point Im assuming just one.

As for drivers, check here.  [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nvidia+8400+gs+driver&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nvidia+8400+gs+driver&sa=Search&cof=FORID:9)

You did not install gnome3.  Thats part of the default install and ubuntu will not work without it.  That black bar that your getting sounds like gnome-shell to me and your right.  Got to get your video card working first.  A work-a-round would be to install gnome-classic to get you up and running for now.  It does not have the video requirements that gShell has and a chance it will work out of the box.  If you wish to do this; open a terminal and enter:  sudo apt-get install gnome-session-fallback

---

