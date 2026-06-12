---
title: "speed tweaks"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by bu2971x on 2008-06-24
For 7.10    Firefox    wildblue satellite ISP
any sure ones????????????/thanks

---

### Post by crimesaucer on 2008-06-24
When I was using xubuntu a few distro's back (7.04), I would use most of these tips from this debian sidux guide: [http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html](http://sidux.com/PNphpBB2-viewtopic-t-3484-start-0.html)


here are a few more from my old bookmarks:
[http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)
[http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
[http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html](http://www.debianadmin.com/local-dns-cache-for-faster-browsing-on-ubuntu-system.html)
[http://www.chinwong.com/index.php/site/article/ubuntu_speed_up_tips/](http://www.chinwong.com/index.php/site/article/ubuntu_speed_up_tips/)
[http://news.softpedia.com/news/Improve-Performance-in-Ubuntu-Edgy-47261.shtml](http://news.softpedia.com/news/Improve-Performance-in-Ubuntu-Edgy-47261.shtml)
[http://www.linuxmonitor.net/blog/2007/03/ultimate-ubuntu-performance-tweaking.html](http://www.linuxmonitor.net/blog/2007/03/ultimate-ubuntu-performance-tweaking.html)
[http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)


[COLOR="Red"]**...a lot of these might be a bit out-of-date**[/COLOR]


But there are still some good tips like OpenDNS, using less tty's, swappiness, ipv6, sysctl, concurrency mode, /etc/hosts, prelinking...

...just do some research to make sure it still is correct procedure for 7.10 and 8.04

---

### Post by JoshuaRL on 2008-06-24
Well, I would suggest a couple things.

First, you could try a lighter-weight Desktop Environment or Window Manager.  Fluxbox, Openbox, and Enlightenment come to mind.  However, if you want something simple and maintained by Canonical, try XFCE-based Xubuntu.  You don't need to reinstall, just run this command and change the session at login:
```

sudo aptitude install xubuntu-desktop

```

Another option is to run a faster browser.  Firefox 3 is not so much smaller, as it is built to be faster.  Benchmarking that I've read about says it is a lot faster than Firefox 2.  But you might try out Swiftfox and Dillo to see if those are quick enough for you.

Another thing you might try is changing some options on your computer.  I would suggest (in Gnome) going to System->Settings->Indexing Settings.  Then disable indexing.  It should free up some system resources, and make your computer seem snappier.  Also, open up Startup Manager in the same menu (I think, I'm on Hardy).  Then disable the things that obviously aren't meant for your computer.  For instance, if you don't have bluetooth, disable it.  That should help some.

But you also might check in System->Administration->Screens and Graphics.  Then make sure you have the right driver being used for your graphics card.  That, along with the right amount of RAM will make the biggest difference.  Since you're running Gutsy, could you post your type of video card and the output of the following command in the terminal (don't worry, you can't hurt anything with this):
```

gedit /etc/X11/xorg.conf

```

---

### Post by gtdaqua on 2008-06-25
> **JoshuaRL said:**
> .
.......

....could you post your type of video card and the output of the following command in the terminal (don't worry, you can't hurt anything with this):
```

gedit /etc/X11/xorg.conf

```

"gedit" is an editor. I think you wanted the output of the file contents. Use "cat" instead of "gedit":

```

cat /etc/X11/xorg.conf

```

That will list the contents of /etc/X11/xorg.conf file.

---

### Post by JoshuaRL on 2008-06-25
> **gtdaqua said:**
> "gedit" is an editor. I think you wanted the output of the file contents. Use "cat" instead of "gedit":

```

cat /etc/X11/xorg.conf

```

That will list the contents of /etc/X11/xorg.conf file.

You are correct that gedit is an editor.  But you can't hurt anything this way, since you need root priviledges to change anything in that file.  I merely use gedit here since it is the standard GUI text editor.  Much easier to maneuver in for new users not used to the command line yet.

But cat, vim, and nano are all excellent CLI tools.

---

### Post by bu2971x on 2008-06-29
My video card is an Intel 945,experimental modesetting driver
here is the output from gedit /etcX11/xorg.conf
running 7.10 for now on a Toshiba laptop... no dual boot..
what do you think as far as speed etc...


# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Modes "1280x800"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection
bu2971x is online now Report Post   	Edit/Delete Message

---

### Post by JoshuaRL on 2008-06-30
> **bu2971x said:**
> My video card is an Intel 945,experimental modesetting driver
here is the output from gedit /etcX11/xorg.conf
running 7.10 for now on a Toshiba laptop... no dual boot..
what do you think as far as speed etc...

Well, if that's true then you are probably doing the best you can for the video driver.  The only other thing I can suggest is maybe more RAM.

---

