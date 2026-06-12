---
title: "Linux Noob Questions - How do i change a directory?"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by balkrish999 on 2014-05-26
Hello, I need some help

I am trying to install a Driver, I have the file, i have the website instructions but they are too complex for a noob like me in Linux 



"Installation  instructions: Once you have downloaded the driver, change  to the directory  containing the driver package and install the driver  by running, as root, sh ./NVIDIA-Linux-x86_64-304.64.run


Installation  instructions:

Once you have downloaded the driver, DONE

change  to the directory  containing the driver package   - How do i do this?   (Currently the file is on my Desktop)

and install the driver  by running, as root, sh ./NVIDIA-Linux-x86_64-304.64.run        -  Cant do step 2 ^^^



Thank You very much!

---

### Post by claracc on 2014-05-26
Please, see [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

In Commands paragraph, are explained the "sudo" command to run as root and "cd" command to move in the directories.

Also, to open a terminal (xterm console) to introduce the commands you can run ```
ctrl+alt+t
```

---

### Post by LastDino on 2014-05-26
Open your file manager and navigate to the folder where you've that driver downloaded.

Then open your terminal and type/copy paste what you see in the address bar of that file manager ;

```
cd /where/that/file/is
```

Assuming that directory is download folder in your home directory; this should look like this;

```
cd /home/yourusername/Downloads/
```

Then click enter, your terminal will look like this;

```
[yourusername@localhost Downloads]$ 
```

I've a feeling that you'll be back to ask about step 3 as it is *probably* going to ask for execution permission, so why are you not installing proprietary drivers from software update manager in system settings?

---

### Post by balkrish999 on 2014-05-26
> **LastDino said:**
> Open your file manager and navigate to the folder where you've that driver downloaded.

Then open your terminal and type/copy paste what you see in the address bar of that file manager ;
t Downloads]$ [/code]

I've a feeling that you'll be back to ask about step 3 as it is *probably* going to ask for execution permission, so why are you not installing proprietor drivers from software update manager in system settings?


Hello, It would be sooo Gratefull if you could help me out and understand where i am comming from.

I am new to Linux, I used, 12 , 13 and they all worked fine and normal in my other PC/Laptop

I have install Dual Booted with Windows 7 on this ***** PC.        --  The PC Specs, are not bad, (average)   4GB RAM, 2.2ghz AMD CPU          ----   The Problem is with the Built in graphics card !!!!!  Name is :    nvidia geforce 7025 nforce 630a


This is the problem, which makes all my PC very very slow, and laggy, the animations on Unity take like 50 seconds just to minimise!!!! 

I changed it on settings, additional but same problem, i am using the one in the picture see attachment  and when i used the default open source, my PC Kept freezing even badly :(   and i had to hold the power button to turn it off

I then googled drivers on my other laptop and found this and am trying to install it -- [http://www.geforce.com/drivers/results/51453](http://www.geforce.com/drivers/results/51453)

Thank you very much :D

---

### Post by staticn0de on 2014-05-26
To make things a big easier,  maybe install the drivers via the additional drivers tab. 

Press the windows key on your keyboard, when unity search appears type in additional drivers. It should have an option to install proprietary nvidia drivers.

---

### Post by Vladlenin5000 on 2014-05-26
The one you already selected in additional drivers is your best option. Installing a newer one won't change a bit for you chipset. Newer driver versions are to add support for newer cards.

---

### Post by oldfred on 2014-05-26
And if you have installed one nVidia driver, you cannot easily install another without major conflicts. You have to be very careful to do a full purge of everything related to nVidia. Remove/backup current xorg.conf and boot with nomodeset. Then you can cleaning install a new driver.

I have an older system and on laptop find Unity just demands too much. So I install fastback/fallback which is the old menu system like gnome2. That needs less resources. If that is still too much then you may want Lubuntu.

 [https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback)
[http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)
Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487](http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487)
12.04 similar but not the same:

        On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

