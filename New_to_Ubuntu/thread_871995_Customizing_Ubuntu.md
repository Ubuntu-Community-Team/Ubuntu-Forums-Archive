---
title: "Customizing Ubuntu"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by SunThief on 2008-07-27
I just got Ubuntu Hardy Heron yesterday.  What can I do to customize it?

---

### Post by tamoneya on 2008-07-27
take a look at [www.gnome-look.org](www.gnome-look.org)

also take a look into a program called conky.

---

### Post by gjoellee on 2008-07-27
it is MANY ways to customize Ubuntu in, you can use Emerld > sudo apt-get emerald, you can download loads of stuff from: [http://wwww.gnome-look.org/](http://wwww.gnome-look.org/) [http://wwww.compiz-themes.org/](http://wwww.compiz-themes.org/) and get compiz fusion > sudo apt-get install compizconfig-settings-manager!!!! so many ways!!!

---

### Post by UbuntuNerd on 2008-07-27
for some reason I have posted this guide about 3 or 4 times today but I guess Thats a good thing follow this link

[http://hacktivision.com/index.php/2008/06/07/how-to-enhance-ubuntu-8-04-hardy-heron-e?blog=2]("http://hacktivision.com/index.php/2008/06/07/how-to-enhance-ubuntu-8-04-hardy-heron-e?blog=2")

also follow this guide to install compiz fusion so you can enjoy the cube 


[http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/](http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/)

---

### Post by SunThief on 2008-07-27
I installed Compiz, and it's not working.  What's wrong?

---

### Post by jamesrfla on 2008-07-27
> **SunThief said:**
> I installed Compiz, and it's not working.  What's wrong?

Maybe providing what is wrong or if you get a error message might help us fix your problem.

---

### Post by UbuntuNerd on 2008-07-27
did you make sure to enable the 3d drivers also what kind of graphic card do you have if don't know type this (lspci) in the terminal and post the output so that someone can help you 

applications>accessories>terminal type lspci

also in the bottom right of your screen how many workspaces do you have? you should have 4 to be able to use the cube

---

### Post by SunThief on 2008-07-27
This is what I got when I typed lspci.

crystal@crystal-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
crystal@crystal-laptop:~$ 

I have two workspaces.  How do I get more workspaces, so I can use the cube?

---

### Post by ramjet_1953 on 2008-07-27
If you go here:

[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

It will tell you how to set-up your nVidia graphics, download codecs for multi-media, etc.

Regards,
Roger :cool:

---

### Post by tamoneya on 2008-07-27
right click on the workspaces and select "preferences".  Also you should play around in System -> preferences -> Advanced desktop effects settings

---

### Post by steveneddy on 2008-07-27
Compiz is already installed in hardy.

I see you have Nvidia graphics.

Have you enabled the restricted driver for Nvidia?

After you get the driver issue settled, you will want to install the configuration manager for Compiz:

```
sudo apt-get install compizconfig-settings-manager
```

and to play DVD's and .mp3's you will need the restricted extras.

First go to

System --> Adminstration --> Software Sources

and check all of the boxes on the first page.

Then in terminal

```
sudo apt-get install ubuntu-restricted-extras

```

and then

```
sudo apt-get update
```

then
```

sudo apt-get upgrade
```

and you will want the medibintu repos also:

link here:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support)

For nvidia:

Go to 

System > Administration > Restricted Drivers Manager 

and turn on the driver and reboot.

**The first two links in my sig should show you most of everything else you will need to keep going.**

---

### Post by SunThief on 2008-07-27
> **tamoneya said:**
> right click on the workspaces and select "preferences".  Also you should play around in System -> preferences -> Advanced desktop effects settings


I played around in Advanced desktop settings, and nothing looks any different than it did before.  I don't have any of the effects that I selected.

---

### Post by steveneddy on 2008-07-27
> **SunThief said:**
> I played around in Advanced desktop settings, and nothing looks any different than it did before.  I don't have any of the effects that I selected.

To turn on compiz, go to:

System --> Preferences --> Appearance

and go to the last Tab (Visual Effects)

and select "Extra"

---

### Post by adamogardner on 2008-07-27
Go to system>preferences>sound. click sounds tab.  This is where you customize sound effects.  For cool (I mean real neat) sound effects, you can go here: [http://www.soundsnap.com/browse](http://www.soundsnap.com/browse)  Choose to download the .wav files.  the mp3 require trickery.

---

### Post by SunThief on 2008-07-28
> **steveneddy said:**
> To turn on compiz, go to:

System --> Preferences --> Appearance

and go to the last Tab (Visual Effects)

and select "Extra"

I did that, and Compiz still isn't working.  Now, Firefox is completely black.  So, I rebooted into Windows.  How do I fix Firefox, and why won't Compiz work?  I've already enabled the driver, installed Compiz, and selected Extra from the Visual Effects tab.

---

### Post by Diabolis on 2008-07-28
There are TONS of things that you can change, that is the essence of linux.

I just finished my new desktop today:
[[IMG]http://farm4.static.flickr.com/3223/2707637070_f893a83424_m.jpg[/IMG]]("http://www.flickr.com/photos/silvag/2707637070/")

---

### Post by SunThief on 2008-07-28
> **Diabolis said:**
> There are TONS of things that you can change, that is the essence of linux.

I just finished my new desktop today:
[[IMG]http://farm4.static.flickr.com/3223/2707637070_f893a83424_m.jpg[/IMG]]("http://www.flickr.com/photos/silvag/2707637070/")

That's awesome.  What is Conky?

---

### Post by Diabolis on 2008-07-28
If you click the image you'll find the links to all the sources.

The yellow bar on top is [dmenu]("http://www.suckless.org/programs/dmenu.html").
The green terminal on the right side is [tilda]("http://tilda.sourceforge.net/wiki/index.php/Main_Page").
The orange letters and the graphs is [conky]("http://conky.sourceforge.net/").
The window manager is [fluxbox]("http://fluxbox.sourceforge.net/").

Everything is in the repositories and you can install any package with this command:
```
sudo apt-get install *"name of the package"*
```

More info:

[tons of conky examples]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+gui")

[fluxbox how to]("http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+screenshots")

[how to set a key binding for dmenu in gnome]("http://ubuntuforums.org/showpost.php?p=5465966&postcount=6")

---

### Post by billgoldberg on 2008-07-28
I think I have one of the better/easy to understand customization guides. 

[http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)

Also should you go with fluxbox, this should help you:

[http://linuxowns.wordpress.com/2008/07/22/fluxbox_on_ubuntu_guide/](http://linuxowns.wordpress.com/2008/07/22/fluxbox_on_ubuntu_guide/)

---

### Post by billgoldberg on 2008-07-28
> **SunThief said:**
> That's awesome.  What is Conky?

A lightweight system monitor.

You install it by using 

*sudo apt-get install conky*

You modify it by editing /hoom/username/.conkyrc

It's all in the guide I posted.

---

### Post by SunThief on 2008-07-28
> **billgoldberg said:**
> I think I have one of the better/easy to understand customization guides. 

[http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)

Also should you go with fluxbox, this should help you:

[http://linuxowns.wordpress.com/2008/07/22/fluxbox_on_ubuntu_guide/](http://linuxowns.wordpress.com/2008/07/22/fluxbox_on_ubuntu_guide/)


Where is the General Options plugin?  When I enable the plugins for the Desktop Cube, my computer freezes.  My computer is a few years old; is it too old to use Compiz?

---

### Post by Diabolis on 2008-07-28
It might. Which graphics card and how much ram do you have.

In my laptop compiz runs ok and I mean just OK. Actually sometimes when I rotate the cube, it looks a bit slow.

cpu: centrino 1.7 ghz
ram: 1.25 GB
graphics: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics

---

### Post by SunThief on 2008-07-28
I have 512 mb RAM and Nvidia graphics card.

---

### Post by Diabolis on 2008-07-28
"nvidia" does not say anything, as they manufacture many different cards. You can find which one you have by typing this in a terminal:
```
lspci
```

---

