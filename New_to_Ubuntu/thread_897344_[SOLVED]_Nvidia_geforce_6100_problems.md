---
title: "[SOLVED] Nvidia geforce 6100 problems"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Ewingo401 on 2008-08-22
hey guys.  I'm trying to do a fresh Ubuntu 8.04 install for a friend and everything is going smooth except for getting the screen resolution correct.  I've tried the restriced driver and still can only get 600x800, in face I think it looks a little better without the restricted driver.  I've tried several tips on this site including downloading the restricted driver and then running "gksu nivida-settings" but that doesn't even launch anything.  I've also tried these steps:

Print out this guide, you will be in pure CLI for part of the install.
1)  Download the driver for your Nvidia Card from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
        1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.
2) Open a terminal: Applications--> Accessories--> Terminal
3) sudo apt-get install build-essential
4) gksudo gedit /etc/modules
        4.a) Add "nvidia" without quotes to the list.
        4.b) Save and Exit
5) gksudo gedit /etc/default/linux-restricted-modules-common
        5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"

        5.b) Save and Exit
6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup
7) sudo rm /etc/X11/xorg.conf
        7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
        7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
                -------------------------------------------------------------------------------------------------------
                If you used Envy to attempt a previous nvidia install please run this command now before you go on:
               sudo envy --uninstall-all 
                sudo dpkg -P envy 
                -------------------------------------------------------------------------------------------------------
                If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:
                sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*
        
        -------------------------------------------------------------------------------------------------------
                If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:
                sudo nvidia-installer --uninstall
                -------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################
8) CTRL-ALT-F1
        8.a) Okay were in Command Line only now, we have a little left to do in here.
        8.b)login:
        8.c)Password:
9) sudo
 /etc/init.d/gdm stop
        9.a) This step shuts down the x-server and gnome desktop manager
10) sudo chmod a+x ./NVIDIA*.run
        10.a) We made the nvidia installer executable.
11) sudo ./NVIDIA*.run
        11.a) Answer to the affirmative for all questions.
        11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
        11.c) If you somehow answered incorrectly on the last question in the installer then:
                c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.
12) sudo /etc/init.d/gdm start
        12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

After step 12 the only thing I get is a message on my monitor saying input not supported...any other ideas guys?  This one is driving me batty!

---

### Post by tangibleorange on 2008-08-22
when using the open-source driver, could you try and get to a terminal and post the output of:

```
xrandr -q
```

if the screen is simply too horrible, try pressing Ctrl+Alt+F1 to get you to a terminal, and then type the command.

---

### Post by Ewingo401 on 2008-08-22
> **tangibleorange said:**
> when using the open-source driver, could you try and get to a terminal and post the output of:

```
xrandr -q
```

if the screen is simply too horrible, try pressing Ctrl+Alt+F1 to get you to a terminal, and then type the command.

Thanks for trying to help this is what I got when entering that:

Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0*
   320x240        51.0

---

### Post by tangibleorange on 2008-08-22
> **Ewingo401 said:**
> Thanks for trying to help this is what I got when entering that:

Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0*
   320x240        51.0

hmm. and you say you have tried to install the restricted driver through the restricted drivers manager, envy, and the guide you posted above?

---

### Post by Ewingo401 on 2008-08-22
I have tried with the restricted driver manager and the guide I posted above...I'm not familiar with envy.  Any chance you could provide a link for info on that if you think it will help?

---

### Post by natirips on 2008-08-22
> **Ewingo401 said:**
> ... the only thing I get is a message on my monitor saying input not supported...

My brother is getting the same problem on his computer after trying to "fix" xorg.conf from nvidia-settings, he got picture ut not compiz by going into recovery mode and fixing the X server.

He is right now doing a fresh (re-)installation of Ubuntu, and I recommend you do the same unless you have any unbackupable important data in your computer.

If you like to expiriment you might also TRY the "sudo dpkg-reconfigure xorg" from the console (my brother got very bad results by this, but at least the display worked in 800x600 or so). See "man dpkg-reconfigure" to see the usage. Navigate the manual with arrow keys and quit with Q key.

P.S.: If you can't see a whole window due to low resolution, hold down ALT key and move (drag) the window around with left mouse button (you may click in the middle of it).

---

### Post by Ewingo401 on 2008-08-22
> **natirips said:**
> My brother is getting the same problem on his computer after trying to "fix" xorg.conf from nvidia-settings, he got picture ut not compiz by going into recovery mode and fixing the X server.

He is right now doing a fresh (re-)installation of Ubuntu, and I recommend you do the same unless you have any unbackupable important data in your computer.

If you like to expiriment you might also TRY the "sudo dpkg-reconfigure xorg" from the console (my brother got very bad results by this, but at least the display worked in 800x600 or so). See "man dpkg-reconfigure" to see the usage. Navigate the manual with arrow keys and quit with Q key.

Thanks for the input.  I have already done two fresh installs since when i get the "input not supported" message I'm pretty much stuck and have to reinstall, and so far the reinstalls have not helped.  As for the "sudo dpkg-reconfigure xorg" I wouldn't know what do with it once I pulled it up.

---

### Post by natirips on 2008-08-22
> **Ewingo401 said:**
> As for the "sudo dpkg-reconfigure xorg" I wouldn't know what do with it once I pulled it up.

You type it at the terminal (i.e. CTRL+ALT+F1 - CTRL+ALT+F6 (CTRL+ALT+F7 is the GUI)). It gives the effect close to reinstalling a package, whereas the "xorg" is the package which controls the display.

P.S.: You might want to try and manually edit the xorg.conf:
(at the terminal)```
sudo nano /etc/X11/xorg.conf
```Mind the capitalisation (that X11 is a capital X and eleven). I think the nano uses CTRL+O (O is not zero but the letter) to Save (Write Out), and CTRL+X to exit. Anyway see the bottom lines. If "nano" turns out not to exist try "pico" instead, or "vi" (see "man vi" because I can't remeber it's controls). Anyway, scroll through the xorg.conf if you're doing this and see if you can find anything that catches your eye). Also you might wish to see "man xorg.conf".

Remeber that you are able to be logged in at the CTRL+ALT+F1 and CTRL+ALT+F2 and CTRL+ALT+F3 ... and CTRL+ALT+F6 at the same time if you wish and switch between them at any time.

Also remember to restart the computer after you're finished with the xorg.conf (press CTRL+ALT+PrintScreen+R (or CTRL+ALT+SysRq+R on some keyboards)).


Edit (just for the record): My brother solved the problem after clean install, full update, and by installing the drivers from Add/Remove programs. He's got NVidia 8600 GT 512MB.

---

### Post by Ewingo401 on 2008-08-22
Update:  Disabling the restricted driver and downloading the driver through envy has got me the screen resolution I desire!  Yay!  The screen is still a little "jumpy" for lack of a better term but its not a huge deal.  Thank you so much to everyone that helped.  The ubuntu forums come through again!

---

