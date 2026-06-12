---
title: "HOWTO: setup all 12 buttons on your mx1000"
date: 2005-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by jrib on 2005-12-02
Well it took a few weeks of scouring the internet for clues before I finally got my mx1000 to work just like I expected it to, but I finally did it. The howto is available on the wiki at the following url: 

[https://wiki.ubuntu.com/MX1000Mouse](https://wiki.ubuntu.com/MX1000Mouse) .

Let me know if it works for you.  I welcome any and all questions and comments.  Even if you don't like the way a particular sentence sounds, let me know :D

The howto is a product of several small changes I made over several weeks as I tried to get all 12 buttons to function correctly during my spare time so I may have forgotten to include a detail or two (I hope not).  Sorry if I did, but I'm sure we can figure it out.  Just post any problems you are having.

---

### Post by ZAKhan on 2005-12-08
[QUOTE=_jason]Well it took a few weeks of scouring the internet for clues before I finally got my mx1000 to work just like I expected it to, but I finally did it. The howto is available on the wiki at the following url: 

[https://wiki.ubuntu.com/mx1000mouse](https://wiki.ubuntu.com/mx1000mouse) .

Let me know if it works for you.  I welcome any and all questions and comments.  Even if you don't like the way a particular sentence sounds, let me know :D

The howto is a product of several small changes I made over several weeks as I tried to get all 12 buttons to function correctly during my spare time so I may have forgotten to inlude a detail or two (I hope not).  Sorry if I did, but I'm sure we can figure it out.  Just post any problems you are having.[/QUOTE]
When run the following command in the terminal window 

sudo apt-get install xvkbd xbindkeys xmacro

I get the following errors:


abcd@LINUX:~$ sudo apt-get install xvkbd xbindkeys xmacro
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package xvkbd

---

### Post by madjinx on 2005-12-08
excelent, i never bothered to check out how to get them all to work, thansk for donig my legwork.

---

### Post by jrib on 2005-12-08
[QUOTE=ZAKhan]When run the following command in the terminal window 

sudo apt-get install xvkbd xbindkeys xmacro

I get the following errors:
...
[/QUOTE]

First, you may want to create a new sources.list.  Some of the repositories that you are failing to connect to no longer exist iirc (for example mirrormax).  Visit [http://ubuntulinux.nl/source-o-matic](http://ubuntulinux.nl/source-o-matic) and generate a new sources.list that contains the repositories you want (you will need universe enabled for the packages in this howto).  Then run ```
sudo apt-get update
```.  Let me know if that solves your problems.

[QUOTE=madjinx]excelent, i never bothered to check out how to get them all to work, thansk for donig my legwork.[/QUOTE]
Great! Glad it worked for you.

---

### Post by Heliode on 2005-12-08
Hey, I've got an MX1000 so I thought I'd try this, but where you have this line:
```

 *H: Handlers=mouse0 event1 ts0

```

But I miss the 'event*' part. (the rest is there though)
there is no 'event' in my '/dev/input' either.
I tried it without this option, but that just killed my Xserver. 

Any thoughts?

---

### Post by jrib on 2005-12-08
[QUOTE=Heliode]Hey, I've got an MX1000 so I thought I'd try this, but where you have this line:
```

 *H: Handlers=mouse0 event1 ts0

```

But I miss the 'event*' part. (the rest is there though)
there is no 'event' in my '/dev/input' either.
I tried it without this option, but that just killed my Xserver. 

Any thoughts?[/QUOTE]

Does ```
lsmod | grep evdev
``` return anything?  What version of ubuntu are you running?

---

### Post by Heliode on 2005-12-08
[QUOTE=_jason]Does ```
lsmod | grep evdev
``` return anything?  What version of ubuntu are you running?[/QUOTE]

No, it doesn't show anything... so I modprobed evdev, and now it shows 'event1'. (there is now also an 'event1' in /dev/...) But it still crashes the Xserver on restart, with the message that it couldn't open the device. 
I made sure I got the 'Dev Phys' part right.

Any more ideas?
Tnx for your help so far btw.

---

### Post by jrib on 2005-12-08
[QUOTE=Heliode]No, it doesn't show anything... so I modprobed evdev, and now it shows 'event1'. (there is now also an 'event1' in /dev/...) But it still crashes the Xserver on restart, with the message that it couldn't open the device. 
I made sure I got the 'Dev Phys' part right.

Any more ideas?
Tnx for your help so far btw.[/QUOTE]

My guess would be a syntax error.  It happened to me a few times.  Can you post your xorg.conf so we can make sure that isn't the problem?

---

### Post by Heliode on 2005-12-08
[QUOTE=_jason]My guess would be a syntax error.[/QUOTE]

Indeed it was... although a very minor one... to get it to work I had to change this:
```

        Option          "Device"                "/dev/input/event1 "

```
to this:
```

        Option          "Device"                "/dev/input/event1"

```
(notice the space)

In case anyone else has the same problem: add 'evdev' to '/etc/modules' to have the evdev module load on startup, and be careful with your syntax!

Thanks for your help and very quick replies!


Edit: 

Some more things I've noticed after fully completing the howto:
The side-scroll buttons do the same thing as the page-forward/backward ones, (i.e. don't side scroll) and the 'middle mouse button' function is gone... I use this function quite a lot to open new tabs in firefox and to paste things I have selected, so it would be great if that could be made to work.

Great job on the other stuff though.

---

### Post by jrib on 2005-12-08
[QUOTE=Heliode]Indeed it was... although a very minor one... to get it to work I had to change this:
```

        Option          "Device"                "/dev/input/event1 "

```
to this:
```

        Option          "Device"                "/dev/input/event1"

```
(notice the space)

In case anyone else has the same problem: add 'evdev' to '/etc/modules' to have the evdev module load on startup, and be careful with your syntax!

Thanks for your help and very quick replies!


Edit: 

Some more things I've noticed after fully completing the howto:
The side-scroll buttons do the same thing as the page-forward/backward ones, (i.e. don't side scroll) and the 'middle mouse button' function is gone... I use this function quite a lot to open new tabs in firefox and to paste things I have selected, so it would be great if that could be made to work.

Great job on the other stuff though.[/QUOTE]

Are the cruise control buttons allowing you to scroll down to a page by holding it down?  

The missing middle button is very strange.  Open a terminal.  Do "killall xbindkeys" and run "xev".  Put your mouse over the box and click each of your buttons to see what button they are generating.  What button number does it generate for the middle button? and the side scrolls?

---

### Post by Heliode on 2005-12-08
[QUOTE=_jason]Are the cruise control buttons allowing you to scroll down to a page by holding it down?  

The missing middle button is very strange.  Open a terminal.  Do "killall xbindkeys" and run "xev".  Put your mouse over the box and click each of your buttons to see what button they are generating.  What button number does it generate for the middle button? and the side scrolls?[/QUOTE]

Cruise control works very well.

However, middle mouse button generates no event in xev. All the other buttons do:

4, 5, 6 & 7 for the scroll wheel, 1 and 3 for left- and right-click, 11 and 12 for cruise control, 8 & 9 for forward and backward, and 10 for the small button between those two.

So I seem to be missing button 2..

---

### Post by jrib on 2005-12-08
[QUOTE=Heliode]Cruise control works very well.

However, middle mouse button generates no event in xev. All the other buttons do:

4, 5, 6 & 7 for the scroll wheel, 1 and 3 for left- and right-click, 11 and 12 for cruise control, 8 & 9 for forward and backward, and 10 for the small button between those two.

So I seem to be missing button 2..[/QUOTE]

Ah!  The first thing I forgot, thanks.

You'll need to set mousewheel.horizscroll.withnokey.action to 0, after entering about:config in the address bar of firefox.  That should get sidescroll to work.  I'll update the wiki.  Thanks :D

Not too sure about the middle mouse button, restart X just to see what happens.

[edit] Meant "0", not "TRUE".

---

### Post by sniper85 on 2005-12-08
I am having trouble restarting X after editing xorg.conf. Here is my xorg.conf file. I get the error:

Configured Mouse: cannot open input device
No core pointer

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Nov 22 18:04:42 PST 2005

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Protocol"              "evdev"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Dev Phys"              "usb-*/input1"
        Option          "Device"                "/dev/input/event1"
        Option          "Buttons"               "12"
        Option          "ZAxisMapping"          "4 5 7 6"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       31.0 - 80.0
    VertRefresh     59.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

Here is my output from cat /proc/bus/input/devices

```
I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-7/input0
H: Handlers=kbd event0
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-7/input1
H: Handlers=kbd mouse0 event1 ts0
B: EV=f
B: KEY=7fffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=143
B: ABS=100 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event2
B: EV=40001
B: SND=6


```

---

### Post by berserker on 2005-12-08
[QUOTE=Heliode]Cruise control works very well.

However, middle mouse button generates no event in xev. All the other buttons do:

4, 5, 6 & 7 for the scroll wheel, 1 and 3 for left- and right-click, 11 and 12 for cruise control, 8 & 9 for forward and backward, and 10 for the small button between those two.

So I seem to be missing button 2..[/QUOTE]

All my buttons are recognized by replacing 

```
Option          "ZAxisMapping"          "4 5 7 6"
```

with

```
Option          "ZAxisMapping"          "11 12 10 9"
```

---

### Post by jrib on 2005-12-08
[QUOTE=sniper85]I am having trouble restarting X after editing xorg.conf. Here is my xorg.conf file. I get the error:
[/QUOTE]

Reread the part explaing the "Device" line again.  It seems you may not have completed that step correctly.  It should involve event[NUMBER] in it, you'll see in the wiki:
```

        Option          "Device"                "/dev/input/event1"

```

[edit] after seeing the output of "cat /proc/bus/input/devices", I can tell you it should be exactly like the example above since your Handlers says "event1"

---

### Post by jrib on 2005-12-08
[QUOTE=berserker]All my buttons are recognized by replacing 

```
Option          "ZAxisMapping"          "4 5 7 6"
```

with

```
Option          "ZAxisMapping"          "11 12 10 9"
```[/QUOTE]

Do the mouse buttons work correctly after that?  Or do you need to also have a .Xmodmap file?  I was originally using that setup with a .Xmodmap, but this setup (with z-axis 4 5 7 6) seems to work without requiring a .Xmodmap file.

---

### Post by sniper85 on 2005-12-08
I tried it with /dev/input/event1 and got the same result

---

### Post by berserker on 2005-12-08
[QUOTE=_jason]Do the mouse buttons work correctly after that?  Or do you need to also have a .Xmodmap file?  I was originally using that setup with a .Xmodmap, but this setup (with z-axis 4 5 7 6) seems to work without requiring a .Xmodmap file.[/QUOTE]

Doh!  Thanks, Jason.  All buttons work with z-axis 4 5 7 6 when I disabled Xmodmap.

---

### Post by jrib on 2005-12-08
[QUOTE=sniper85]I tried it with /dev/input/event1 and got the same result[/QUOTE]

Get rid of the CorePointer line, you shouldn't need it unless you use multiple mice.  Let me know if it stops throwing errors.

[edit]Are you using both a wireless logitech keyboard and mouse?

---

### Post by sniper85 on 2005-12-08
I tried to remove that line and got the same result. And yes i am using a logitech wireless mouse and keyboard

---

### Post by berserker on 2005-12-08
Jason,

How would you bind the middle thumb button (button 10) to close the current application?

TIA

---

### Post by jrib on 2005-12-08
[QUOTE=sniper85]I tried to remove that line and got the same result. And yes i am using a logitech wireless mouse and keyboard[/QUOTE]

okay, I think that we're going to have to look into this line:  "H: Handlers=kbd mouse0 event1 ts0"

I googled for "Handlers=kdb mouse" and didn't get any hits (got 1 but it was strange code).  I don't understand too much about what these things actually mean.  I'll try to google and understand more about what exactly it means.  In the meantime, let me know if you figure anything out yourself.  Thanks and sorry it didn't work out right away.

---

### Post by berserker on 2005-12-08
[QUOTE=berserker]Jason,

How would you bind the middle thumb button (button 10) to close the current application?

TIA[/QUOTE]

This works with mixed results (closes tabs in Konqueror and Firefox completely) in ~/.xbindkeysrc:

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\CW""
   b:10
```

Jason, thanks for this howto.  Disabling xmodmap has enabled me to use the thumb buttons in CoD under Wine.

---

### Post by jrib on 2005-12-09
[QUOTE=berserker]This works with mixed results (closes tabs in Konqueror and Firefox completely) in ~/.xbindkeysrc:

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\CW""
   b:10
```

Jason, thanks for this howto.  Disabling xmodmap has enabled me to use the thumb buttons in CoD under Wine.[/QUOTE]

Interesting, I was trying to figure out what xsendevent text would allow you to do F4 so that you could have it send ALT+F4 but I couldn't figure it out.  You could always change the shortcut key in "keyboard shortcuts" to something like ALT+w (I don't know if that's used for something else) and then make xbindkeys send that.  Current;y, I have my button sending "Delete" so that I can delete text quickly with the mouse.


If anyone knows more about these xsendevents text commands, please share.  I've been searching google but most of my hits are actually mouse related and I don't find a good reference!

---

### Post by berserker on 2005-12-09
[QUOTE=_jason]You could always change the shortcut key in "keyboard shortcuts" to something like ALT+w (I don't know if that's used for something else) and then make xbindkeys send that.[/QUOTE]

Thanks!  That did the trick.  I can now close the current app by pressing the middle thumb button.  Here's what it looks like in ~/.xbindkeysrc:

```
"/usr/X11R6/bin/xvkbd -text "\[Alt_L]\[w]""
   b:10
```

---

### Post by XQC on 2005-12-10
[quote=_jason]
You'll need to set mousewheel.horizscroll.withnokey.action to 0, after entering about:config in the address bar of firefox.  That should get sidescroll to work.  I'll update the wiki.  Thanks :D

[edit] Meant "0", not "TRUE".[/quote]
I did this, but the horizontal wheel also goes up and down... what do I have to change?

Otherwise, I followed the How-to step by step correctly and all other buttons are working well!

---

### Post by jrib on 2005-12-10
[QUOTE=XQC]I did this, but the horizontal wheel also goes up and down... what do I have to change?

Otherwise, I followed the How-to step by step correctly and all other buttons are working well![/QUOTE]

In a terminal: killall xbindkeys
See if the sidescroll works correctly now.  If it does, post the contents of ~/.xbindkeysrc

If it's still doing both side scroll and vertical scroll:
In a terminal: xev
Put your mouse over the box and see what button numbers it is producing when you hold down the side scroll.  Let me know what it says.

---

### Post by XQC on 2005-12-10
[quote=_jason]In a terminal: killall xbindkeys
See if the sidescroll works correctly now.  If it does, post the contents of ~/.xbindkeysrc

If it's still doing both side scroll and vertical scroll:
In a terminal: xev
Put your mouse over the box and see what button numbers it is producing when you hold down the side scroll.  Let me know what it says.[/quote] I have to correct my problem:
In other applications the horizontal scroll works fine as it was configured to begin with with your how-to, it's just a problem with Firefox.

---

### Post by jrib on 2005-12-10
[QUOTE=XQC]I have to correct my problem:
In other applications the horizontal scroll works fine as it was configured to begin with with your how-to, it's just a problem with Firefox.[/QUOTE]

hrmm... you can make sure it's not an extension or preference that's interfering by running firefox in safe mode: ```
firefox -safe-mode
```

---

### Post by poley on 2005-12-15
[QUOTE=berserker]Jason,

How would you bind the middle thumb button (button 10) to close the current application?

TIA[/QUOTE]

hope this doesn't sound too much like a newb question....i've only been using ubuntu for about 10 hours in total...

anyways.

I'm looking to do the same thing, i've followed the guide on wiki and I have all 12 buttons mapped, (edited xorg.conf made Xmodmap file) scroll wheel works, forward button works, scroll buttons works yadda yadda, everything as standard is working fine.

what i've done differently to wiki (doubt it makes too much difference) is left the mouse in the PS/2 port as I use it in windows (I'm quite an avid gamer) and I get issues if the mouse runs through the USB port, I like said though I can see this making any difference.

I've made the file ~/.xbindkeysrc heres a copy of it

```
###########################
# xbindkeys configuration #
###########################
#
# Version: 0.1.3
#
# If you edit this, do not forget to uncomment any lines that you change.
# The pound(#) symbol may be used anywhere for comments.
#
# A list of keys is in /usr/include/X11/keysym.h and in
# /usr/include/X11/keysymdef.h 
# The XK_ is not needed. 
#
# List of modifier (on my keyboard): 
#   Control, Shift, Mod1 (Alt), Mod2 (NumLock), 
#   Mod3 (CapsLock), Mod4, Mod5 (Scroll). 
#
# Another way to specifie a key is to use 'xev' and set the 
# keycode with c:nnn or the modifier with m:nnn where nnn is 
# the keycode or the state returned by xev 
#
# This file is created by xbindkey_config 
# The structure is : 
# # Remark 
# "command" 
# m:xxx + c:xxx 
# Shift+... 

#keystate_numlock = enable
#keystate_scrolllock = enable
#keystate_capslock = enable

"/usr/X11R6/bin/xvkbd -xsendevent -text "\CW""
   b:9

#
# End of xbindkeys configuration

```

and as you can hopefully see I've assigned the close program button to one of the side keys, the "back" button, i've also added xbindkeys to the startup session and tried running it through console and I've also restarted quite a few times. I haven't tried mapping the keyboard function alt+f4 to anything yet, I just want to get this version of it working first and see what its like.

however it doesn't work....

am I being a newb and missing something???

I'm trying to setup linux because next year I hope to start my phd and there is a very good chance my computer in the lab will be running a form of linux, I'm just trying to get used to it before I start.

any help would be greatly appreicated.

---

### Post by berserker on 2005-12-15
Try this:

```
"/usr/X11R6/bin/xvkbd -text "\CW""
   b:9
```

Notice "-xsendevent" is missing.

---

### Post by poley on 2005-12-15
thanks for the response, tried the above, doesn't seem to want to work either, the button still works as a "back" button....

not sure if this will help but this is what is going on in event tester when I click...(with the new code)

```
ButtonRelease event, serial 29, synthetic NO, window 0x2c00001,
    root 0x133, subw 0x2c00002, time 139608, (29,39), root:(34,85),
    state 0x0, button 6, same_screen YES

LeaveNotify event, serial 29, synthetic NO, window 0x2c00001,
    root 0x133, subw 0x0, time 139608, (29,39), root:(34,85),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0
```

and with the old code (still works as a "back" button).

```
ButtonRelease event, serial 29, synthetic NO, window 0x2e00001,
    root 0x133, subw 0x2e00002, time 392347, (35,32), root:(40,78),
    state 0x0, button 6, same_screen YES

LeaveNotify event, serial 29, synthetic NO, window 0x2e00001,
    root 0x133, subw 0x0, time 392347, (35,32), root:(40,78),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0
```

no idea why it has it down as button 6...

if you want/need to see any other copies of things to make sure I've done stuff correct let me know...

[edit] heres a copy of the Xbindkeys entry (old entry)
[IMG]http://www.psistar.co.uk/news/data/upimages/Screenshot.png[/IMG]
[/edit]

---

### Post by berserker on 2005-12-15
Perhaps:

```
"/usr/X11R6/bin/xvkbd -text -xsendevent "\CW""
   b:6
```

---

### Post by poley on 2005-12-15
nope that doesn't work either, although it no longer works as a "back" button....

---

### Post by jrib on 2005-12-16
[QUOTE=poley]nope that doesn't work either, although it no longer works as a "back" button....[/QUOTE]

try:

```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Delete]""
  b:6

```

See if you can highlight text with your mouse and then delete it using your side button.  At least this way we can see if it is actually sending some command.

---

### Post by poley on 2005-12-16
thanks for that idea, turns out the button was mapped to 8 not 9....interesting...took a bit of trail and error before I found out what it was but at least with the delete function I could see it working, nice idea.

here's the final code

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
   b:9
"/usr/X11R6/bin/xvkbd -xsendevent -text "\CW""
   b:8
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
   b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
   b:12
```

only thing now is that I get a beep when I close a program, how'd I get rid of that?

[edit]

something else too, the forward "cruise" button closes programs too....interesting....any ideas? (might be the source of the beep too, two buttons working at once...

thinking about it (and I really need to go to bed [5.45am]) would the Xmodmap file have any lingering effect, i used the following mapping 1 2 3 6 7 8 9 10 11 12 4 5 given from another website (seems to be the problem with linux, one person does it one way another does it different), this is the best yet, actually got it working :)

I've removed the file from Home but other than that I wouldn't know how to "disable" it otherwise
[/edit]

---

### Post by jrib on 2005-12-16
[QUOTE=poley]thanks for that idea, turns out the button was mapped to 8 not 9....interesting...took a bit of trail and error before I found out what it was but at least with the delete function I could see it working, nice idea.

here's the final code

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
   b:9
"/usr/X11R6/bin/xvkbd -xsendevent -text "\CW""
   b:8
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
   b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
   b:12
```

only thing now is that I get a beep when I close a program, how'd I get rid of that?

[edit]

something else too, the forward "cruise" button closes programs too....interesting....any ideas? (might be the source of the beep too, two buttons working at once...

thinking about it (and I really need to go to bed [5.45am]) would the Xmodmap file have any lingering effect, i used the following mapping 1 2 3 6 7 8 9 10 11 12 4 5 given from another website (seems to be the problem with linux, one person does it one way another does it different), this is the best yet, actually got it working :)

I've removed the file from Home but other than that I wouldn't know how to "disable" it otherwise
[/edit][/QUOTE]

Yeah, maybe I should add something to the wiki stating that you should not have a .xmodmap enabled.  That would explain why your buttons were showing different  numbers.  Restarting X after removing the .Xmodmap file should do it.  You may have to mess with xbindkeys again though since the button numbers will change :)

When I read about evdev, the authors all recommended usb.  That's why I put it in the wiki.  Let me know if it works out for you with the PS/2.  If it's still giving you trouble after getting rid of the .Xmodmap, try the usb port.

---

### Post by sniper85 on 2005-12-18
hey _jason I was wondering if you found out anuthing about why I could get mine working after editing xorg.conf. I haven't been able to find anything. Thanks

---

### Post by jrib on 2005-12-18
[QUOTE=sniper85]hey _jason I was wondering if you found out anuthing about why I could get mine working after editing xorg.conf. I haven't been able to find anything. Thanks[/QUOTE]

Haven't had a chance to look to be honest, busy with finals atm.  I'll be done in 3 days and then I'll do some more googling on the matter.

Try backing up your xorg.conf and playing with the settings.  The fact that I found no hits on google for that line I mentioned before makes me suspect something is wrong and it should be changed.  See if you can find some tutorials on setting up the keyboard and mouse combo and see what the xorg.conf looks like in the tutorials.  That's what I would think of doing anyway if I were in your shoes.  Good luck.  I'll post back here with anything I might find in a few days.

---

### Post by Killerdackel on 2005-12-23
OK so far nearly everything fine, scrolling horizontal and vertical no problem.

But I'am used to have the buttons next to wheel scroll a little bit faster than the wheel. Like one click scrolling 4 or 5 lines. Do you know what I have to change to get this results by clicking?

And then I have a problem with the side buttons sometimes one click triggers nearly 100x the event I assigned to that key so that I am at the beginning or end of my history or my Amarok runs trough many files. 

I have assigned Alt_L+n to the middle thumb button to switch to the next track. 

```

  "/usr/X11R6/bin/xvkbd -text "\[Alt_L]n""
   b:10

```

Although the pointer of the mouse jumps to the top left point of the active window and then back to the point where i clicked.

The same things is to be noticed when I press the keys directly on the keyboard for a longer time is there a possibility to say xvkbd how often the key should be pressed?

Do you have the same problem? Or did I miss something?

---

### Post by jrib on 2005-12-25
[QUOTE=Killerdackel]OK so far nearly everything fine, scrolling horizontal and vertical no problem.

But I'am used to have the buttons next to wheel scroll a little bit faster than the wheel. Like one click scrolling 4 or 5 lines. Do you know what I have to change to get this results by clicking?
[/QUOTE]

I think you can set mousewheel.horizscroll.withnokey.sysnumlines to false and  mousewheel.horizscroll.withnokey.numlines to 4 or 5.

[QUOTE=Killerdackel]And then I have a problem with the side buttons sometimes one click triggers nearly 100x the event I assigned to that key so that I am at the beginning or end of my history or my Amarok runs trough many files. 

I have assigned Alt_L+n to the middle thumb button to switch to the next track. 

```

  "/usr/X11R6/bin/xvkbd -text "\[Alt_L]n""
   b:10

```

Although the pointer of the mouse jumps to the top left point of the active window and then back to the point where i clicked.

The same things is to be noticed when I press the keys directly on the keyboard for a longer time is there a possibility to say xvkbd how often the key should be pressed?

Do you have the same problem? Or did I miss something?[/QUOTE]

As far as the jumping pointer effect, I haven't experienced this.  But you may want to try adding the '-no-jump-pointer' switch to the command.  The man page is on: [http://homepage3.nifty.com/tsato/xvkbd/](http://homepage3.nifty.com/tsato/xvkbd/) .  

I'm not sure why it would perform the event multiple times.  Try using the '-no-repeat' switch as well (see the link above).  If that doesn't work:  Maybe the syntax for the letter 'n' is incorrect?  Just guessing.  You can try using left+up as a new shortcut and see if the behavior persists (since we know for sure that the syntax for the direction keys is correct).  If it works properly with the new shortcut then try to see if you can figure out how to properly set the shortcut to use the letter 'n'.  And if it persists even with using alt+up, I don't know.

[edit] I also just noticed that your command is missing the 'xsendevent' switch.  See the example from the wiki:

```

 "/usr/X11R6/bin/xvkbd **-xsendevent** -text "\[Alt_L]\[Left]""
   b:8

```

---

### Post by graveman on 2005-12-30
got it working  :) 
my only problem is it does'nt load at start up...
any help????

---

### Post by jrib on 2005-12-30
[QUOTE=graveman]got it working  :) 
my only problem is it does'nt load at start up...
any help????[/QUOTE]

did you add xbindkeys to your startup programs in the System -> Preferences -> Sessions -> Startup Programs ?

---

### Post by geearf on 2005-12-31
Hello,

all was working in hoary before, and today I realised that it does not work with breezy.
This was my setup : 
Section "InputDevice"
        Identifier      "MX1000"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/event1"
        Option          "Dev Name"              "PS2++ Logitech MX Mouse"
        Option          "Dev Phys"              "isa0060/serio1/input0"
        Option          "Protocol"              "evdev"
        Option          "Buttons"               "12"
        Option          "ZAxisMapping"          "11 12 10 9"
        Option          "Resolution"            "800"
        Option          "Emulate3Buttons"       "false"
EndSection


pointer = 1 2 3 8 9 10 11 12 7 6 4 5


But now I cannot get all to work, even with
Option          "ZAxisMapping"          "11 12"
Option         "ZAxisMapping"          "4 5 7 6"

I cannot get every button under xev.

If you have any idea on this,
Thanks,

edit : well strangely today, I have everything but the left and right wheel with : 
Option          "ZAxisMapping"          "4 5 7 6"
and no xmodmap.

If anyone know how to get the wheel fully back please do :)

---

### Post by jrib on 2006-01-01
[QUOTE=geearf]Hello,

all was working in hoary before, and today I realised that it does not work with breezy.
This was my setup : 
Section "InputDevice"
        Identifier      "MX1000"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/event1"
        Option          "Dev Name"              "PS2++ Logitech MX Mouse"
        Option          "Dev Phys"              "isa0060/serio1/input0"
        Option          "Protocol"              "evdev"
        Option          "Buttons"               "12"
        Option          "ZAxisMapping"          "11 12 10 9"
        Option          "Resolution"            "800"
        Option          "Emulate3Buttons"       "false"
EndSection


pointer = 1 2 3 8 9 10 11 12 7 6 4 5


But now I cannot get all to work, even with
Option          "ZAxisMapping"          "11 12"
Option         "ZAxisMapping"          "4 5 7 6"

I cannot get every button under xev.

If you have any idea on this,
Thanks,

edit : well strangely today, I have everything but the left and right wheel with : 
Option          "ZAxisMapping"          "4 5 7 6"
and no xmodmap.

If anyone know how to get the wheel fully back please do :)[/QUOTE]

Is your mouse connected to a usb port?

---

### Post by geearf on 2006-01-01
no ps/2.

---

### Post by jrib on 2006-01-01
[QUOTE=geearf]no ps/2.[/QUOTE]

See if connecting it to a usb port will resolve the problem.

---

### Post by geearf on 2006-01-01
Hello,

in hoary it used to work in ps2, I don't see why it should not in Breezy, plus I'd like to use USB the least possible :)

I'll investigate this later maybe :)

---

### Post by jrib on 2006-01-01
I only suggest it because evvery guide I have read insists that the only way to get all of the buttons to function properly is to use a usb port.  One more question though:  is smart scroll enabled?  When you hold down the scroll down button does it generate a 11 (maybe 12 can't remember) and then repeat 4's (maybe 5's) using xev?

---

### Post by geearf on 2006-01-01
Hello,

I've seen the same for the ps2 but as I have got it once, I guess I can still got it :)

About xev, I get first button 10 and then button 5 for the down scroll, 11 and 4 for up scroll

---

### Post by Freddy on 2006-01-15
Hi all. Think it was a glorius guide, but what to do in a KDE setup. I came as far as created a .xbindkeysrc, but what to do with it. I tried to find the ~/.autostart, that should be within my home directory but sorry to say I didn't find one hmm.

Is there any way to make konqueror use all of this afterwards?

Thanks for any answers.   /// Freddan

Edit: I started xbindkeys manually and it seems that some buttons works with Konqueror (back n' fourth, but not tilt), needs some help to automate this to.

---

### Post by berserker on 2006-01-15
[QUOTE=Freddy]I tried to find the ~/.autostart, that should be within my home directory but sorry to say I didn't find one hmm.[/QUOTE]

```
~/.kde/Autostart
```

---

### Post by Freddy on 2006-01-15
Haha that's right, I'm so freaking dumb :) thanks dude. 
If anyone out there knows how to get all the buttons working in Konqueror, plz let me know.   /// Freddan

---

### Post by jrib on 2006-01-15
[QUOTE=Freddy]Haha that's right, I'm so freaking dumb :) thanks dude. 
If anyone out there knows how to get all the buttons working in Konqueror, plz let me know.   /// Freddan[/QUOTE]

Make sure the mouse generates button 6 and button 7 for side scroll using the 'xev' command in a terminal.  I loaded up konqueror (on gnome) and they are working for me.  I don't use konqueror so it seems to be working without any modification.  If you can't figure it out, a temporary way around it may be to use xbindkeys to map those keys to whatever keyboard key makes konqueror side scroll (probably left and right arrow keys like in firefox).

---

### Post by Freddy on 2006-01-15
[QUOTE=_jason]Make sure the mouse generates button 6 and button 7 for side scroll using the 'xev' command in a terminal.  I loaded up konqueror (on gnome) and they are working for me.  I don't use konqueror so it seems to be working without any modification.  If you can't figure it out, a temporary way around it may be to use xbindkeys to map those keys to whatever keyboard key makes konqueror side scroll (probably left and right arrow keys like in firefox).[/QUOTE]
Thanks I'll try that. Do you even know how to activate xbindkeys when booting KDE, I symliked the xbindkeys created in the homedirectory to ~/.kde/autostart but that didn't go as well as I hoped, I still needed to activate it manually.

Thanks for any answers.   /// Freddan

---

### Post by jrib on 2006-01-15
[QUOTE=Freddy]Thanks I'll try that. Do you even know how to activate xbindkeys when booting KDE, I symliked the xbindkeys created in the homedirectory to ~/.kde/autostart but that didn't go as well as I hoped, I still needed to activate it manually.

Thanks for any answers.   /// Freddan[/QUOTE]

I don't, you might want to try to post in the specific kubuntu section about starting up the program.  Feel free to update the wiki with your kde experience notes if you solve this :)

---

### Post by Myrkul23 on 2006-02-04
I've followed all the directions and everything went smoothly, but for some reason the cruise control will not work in firefox.  From xev I know that the button numbers are 11 and 12, in case this helps solve the problem.

---

### Post by jrib on 2006-02-04
[QUOTE=Myrkul23]I've followed all the directions and everything went smoothly, but for some reason the cruise control will not work in firefox.  From xev I know that the button numbers are 11 and 12, in case this helps solve the problem.[/QUOTE]

in xev, when you hold down the cruise control buttons, do the 4 and 5 button events repeat (after the initial 11 or 12)?

---

### Post by Myrkul23 on 2006-02-04
It doesn't repeat.  Also, when I initially press down on the down cruise control, it comes up as button 5.  When I release, it comes up as button 12.  For the up cruise control, the numbers are 4 and 11.

---

### Post by jrib on 2006-02-04
Okay that means smart scroll has been disabled on your mouse.  There is a program that will let you enable it but it is not in the repositories.  How comfortable are you with compiling?

---

### Post by Myrkul23 on 2006-02-04
I used to be a slack user, so since I had to compile EVERYTHING in slack, it shouldn't be too bad  :)

---

### Post by jrib on 2006-02-04
ah okay, go ahead and compile this [http://www.bedroomlan.org/~alexios/coding_lmctl.html](http://www.bedroomlan.org/~alexios/coding_lmctl.html), the link is hidden in the last paragraph right before the manual page.

I don't know if you are familiar with checkinstall.  Basically instead of the usual ./configure, make, sudo make install routine, you do ./configure, make, sudo checkinstall.  But checkinstall will create a deb for you and keep track of what gets installed so you can easily remove it using a package manager.  You'll need to 'sudo apt-get install checkinstall' first so that you can use it.

using lmctl...
```

jasonr@luso:~$ sudo lmctl -s #lists usb devices
002.001: 0000:0000 Not a Logitech device
001.002: 046d:c50e Receiver for MX1000 Laser (C-BN34) Caps: CSR SMS
001.001: 0000:0000 Not a Logitech device

#you want to find the 001 in ``001.002...'' above
#once you know that, just do:
jasonr@luso:~$ sudo lmctl -b 001 --sms
001.002: 046d:c50e Receiver for MX1000 Laser (C-BN34) Caps: CSR SMS
        SmartScroll enabled

```
Then try xev again and see if it is repeating the 4's and 5's with the smart scroll buttons.

---

### Post by Myrkul23 on 2006-02-04
I installed the program, but when I scan for devices it only sees an unrecognized Logitech device.  If I try to apply any options, it says it is unsupported.

---

### Post by jrib on 2006-02-04
you've got it hooked up to a usb port?  is this one of those keyboard mouse combos?

I think you can also enable this using the windows drivers if you dual boot (although i don't know where that setting would be located).

[edit]also, i used lmctl-0.3.1

---

### Post by Myrkul23 on 2006-02-05
I have the receiver hooked up to a USB port, but that program doesn't recognize it for some reason.  Do you have any ideas or know of other programs?  Now that I've read up on this program, it seems like another problem is the face I need it to read at 800 cpi rather than 400.  Any ideas?  Thanks again for all your help.

---

### Post by jrib on 2006-02-05
From what I have read, the mx1000, unlike previous logitech mice, keeps its resolution at the max so you won't/shouldn't need to change it with any software.

As for other programs that will allow you to do this, I only know of the windows software that came with the mouse.  A quick google search gave me some hits on a linux patch (which I didn't really understand) and some kde support:  [http://www.cs.helsinki.fi/linux/linux-kernel/2003-12/0929.html](http://www.cs.helsinki.fi/linux/linux-kernel/2003-12/0929.html) [http://www.kdedevelopers.org/node/677](http://www.kdedevelopers.org/node/677)

Try hitting the reset buttons on your mouse and receiver (just a shot in the dark).  If all else fails, maybe you can email logitech and ask them if there is a way to do it without software.  Maybe a certain key combination?

---

### Post by geearf on 2006-02-05
Hello,
I still cannot do better than 10 buttons don't know really why, when I used to have them all this summer ..

Anyway why does all those programs work only with USB, I really don't get it .. :(

---

### Post by jrib on 2006-02-05
[QUOTE=geearf]Hello,
I still cannot do better than 10 buttons don't know really why, when I used to have them all this summer ..

Anyway why does all those programs work only with USB, I really don't get it .. :([/QUOTE]


Did you follow the guide?  Which two are not working?

---

### Post by FlakJacket on 2006-02-05
Thanks alot for the guide! Made my Logitech G5's sidescroll work very nicely.  I was wondering though the G5 only has one side button so it may be different number than the MX1000 so how do I find out what number X sees it as?

Thanks,

Flak

---

### Post by jrib on 2006-02-05
[QUOTE=FlakJacket]Thanks alot for the guide! Made my Logitech G5's sidescroll work very nicely.  I was wondering though the G5 only has one side button so it may be different number than the MX1000 so how do I find out what number X sees it as?

Thanks,

Flak[/QUOTE]

run xev in a terminal and click in the box that shows up.  You'll see a bunch of info.  The easiest place to find it is in the paragraph that begins with ``ButtonRelease event''.  The second to last thing in that paragraph should be ``button x'' where x is a number.  Try to keep your mouse still since moving it will also generate output.

[edit] If you see stuff like KeymapNotify event it means xbindkeys caught it.  So you may want to kill xbindkeys beforehand

---

### Post by FlakJacket on 2006-02-05
Messing with the xkeys config i accidently made my scroll down the back alt-l command but when i deleted that line it won't go back to normal scroll what do i do?

thanks,
Flak

---

### Post by jrib on 2006-02-05
kill xbindkeys and start it again, or just restart X

---

### Post by geearf on 2006-02-05
Hello,
well the two for the thumb, back and forth.
We already discussed this a few weeks ago, and I tried again today, but still no luck :)

---

### Post by FlakJacket on 2006-02-05
Thank you I restarted X and it is back to normal.  How do you use the kill command?  Xev doesn't show a click for the side button does that mean i have too few buttons listed in my .conf? i'll try and add the two dpi buttons to the number maybe.

Thanks,
Flak

Edit: can xbindkeys also be used to configure say a gamepad?

---

### Post by jrib on 2006-02-05
[QUOTE=geearf]Hello,
well the two for the thumb, back and forth.
We already discussed this a few weeks ago, and I tried again today, but still no luck :)[/QUOTE]

oh you're the ps/2 guy :)  Did you at least try a usb port to see if that was the problem?

---

### Post by geearf on 2006-02-05
Yes I am :)

and nah, but I may give it a try tonight, but if it worked before, it should still (well I think).

Thanks,

---

### Post by geearf on 2006-02-11
Hello,
just to tell you that under dapper, it works without changing much, the driver, and the physical thing, then that's it :)

but still no back and forth buttons :(
I will try USB tomorrow I think.

---

### Post by FlakJacket on 2006-02-13
Is there something in xbindkeys i can assign the middle button so that I can autoscroll or maybe something else useful? Right now it goes to a url I've got in klipper and is useless and kind of annoying.

Flak

---

### Post by jrib on 2006-02-13
[QUOTE=FlakJacket]Is there something in xbindkeys i can assign the middle button so that I can autoscroll or maybe something else useful? Right now it goes to a url I've got in klipper and is useless and kind of annoying.

Flak[/QUOTE]

i don't know what clipper is but I'll assume it's the kde clipboard.  If you are using firefox, for linux the default action is to do what you just described.  You can change it by going to 'about:config' in your address bar and changing middlemouse.contentLoadURL to false

---

### Post by FlakJacket on 2006-02-14
Thank you very much.  Sorry forgot I wasn't in kubuntu forums anymore.  So is there anyway to get an autoscroll function?

Flak

---

### Post by jrib on 2006-02-16
[QUOTE=FlakJacket]Thank you very much.  Sorry forgot I wasn't in kubuntu forums anymore.  So is there anyway to get an autoscroll function?

Flak[/QUOTE]

It doesn't work after following the wiki guide?

---

### Post by FlakJacket on 2006-02-16
I don't have cruise control on my G5 i was wondering if I could make the middle button do scroll thing where if you move the mouse up it scrolls up and down down. If this is possible I would like to know please.

Flak

---

### Post by jrib on 2006-02-16
What browser are you using?

You want something like what is in the screenshot?

---

### Post by FlakJacket on 2006-02-16
Yes please and I'm using Firefox.

Flak

---

### Post by berserker on 2006-02-16
Open a new tab in Firefox and type in "about:config"

Set "middlemouse.contentLoadURL" to "false".

Set "general.autoScroll" to "true".

---

### Post by FlakJacket on 2006-02-17
Sweet!! Thank you very much.

Flak

---

### Post by eXCeSS on 2006-02-21
Ive done everything in the guide, and my back and forward buttons dont work.

But the left and right tilt on the scroll wheel do the whole back and forward thing, but the back and forward buttons do nothing.

Any help?

---

### Post by jrib on 2006-02-21
[QUOTE=eXCeSS]Ive done everything in the guide, and my back and forward buttons dont work.

But the left and right tilt on the scroll wheel do the whole back and forward thing, but the back and forward buttons do nothing.

Any help?[/QUOTE]

Hey, excess.  I see it's you first post, so welcome to the forums.  Let's see if we can figure out what's going on.

Here's what I need you to do,
[LIST]
[*]Applications Menu -> Accessories -> Terminal
[*]```
$ killall xbindkeys
```
[*]```
$ xev
```
[*]click the forward, back, left scroll, and right scroll and record what button number  they produce.  You'll have to look at the paragraphs that begin with ``ButtonRelease''.  Try to keep the mouse still as this will make it easier to identify the correct section of the output.
[*]please also post the relevant section of /etc/X11/xorg.conf
[/LIST]

---

### Post by FlakJacket on 2006-02-23
How do you use xbindkeys to bind a keyboard key to a shortcut?

Flak

EDIT: ok i've figured it out but how do you get shift and those keys to work?

---

### Post by jrib on 2006-02-23
[QUOTE=FlakJacket]How do you use xbindkeys to bind a keyboard key to a shortcut?

Flak

EDIT: ok i've figured it out but how do you get shift and those keys to work?[/QUOTE]

if you look at ```
man xbindkeys
``` there are a few examples that use shift

---

### Post by stoffe on 2006-03-02
Hello! I'm not 100% sure that this should work, but I figure it can't hurt to ask. 

I'm running Dapper on a Fujitsu Siemens Amilo laptop, with the latest updates. I've just gotten a DiNovo media keyboard + mouse set, that uses an MX Laser mouse (I think it's a MX 1000 but it doesn't really say). It connects via bluetooth via a USB stick, so that may or may not be a problem. Everything works just fine apart from the buttons, as they all think they are one of the 3 first buttons...

Anyway, I try to follow the guide and modify it after my needs, and I get an error about the protocol evdev.

Xorg.0.log relevant part:```
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "evdev"
(EE) Configured Mouse: Unknown protocol "evdev"
(EE) PreInit failed for input device "Configured Mouse"
(II) UnloadModule: "mouse"
(II) Synaptics touchpad driver version 0.14.3
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) No core pointer registered
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel Input Handler" (type: Other)
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found
No core pointer

Fatal server error:
failed to initialize core devices
```
A look at the devices looks like this:
```
stoffe@homer:~$ cat /proc/bus/input/devices
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio2/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse1 event2 ts1
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0003 Vendor=046d Product=c70b Version=4001
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1d.3-2.2/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70c Version=4001
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1d.3-2.3/input0
S: Sysfs=/class/input/input4
H: Handlers=kbd mouse2 event4 ts2
B: EV=f
B: KEY=c0002 400 0 0 fff0001 f80 78000 6039fa d841d7ad 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0
```
Which resulted in this Xorg.conf:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Protocol"              "evdev"
        Option          "Dev Name"              "Logitech Logitech BT Mini-Receiver"
        Option          "Dev Phys"              "usb-0000:00:1d.3-2.3/input0"
        Option          "Device"                "/dev/input/event4"
        Option          "Buttons"               "12"
        Option          "ZAxisMapping"          "4 5 7 6"
EndSection
```

So what do you think? Could this be made to work somehow? Thankful for any clues. :)

---

### Post by geearf on 2006-03-02
protocol evdev does not exist anymore it has been 'replaced' by driver evdev.

---

### Post by stoffe on 2006-03-02
[QUOTE=geearf]protocol evdev does not exist anymore it has been 'replaced' by driver evdev.[/QUOTE]
Ok, so what do I need to do to get that up and running? I see that there is a package xserver-xorg-evdev in the repos, I suppose I should start with that?

---

### Post by stoffe on 2006-03-02
Ok, got it to work. Commented out the protocol line, and changed the driver to "evdev". Installed xserver-xorg-evdev and restarted X - and it worked. So did the rest of the tips.

Thanks a lot for this help!

---

### Post by stoffe on 2006-03-02
Now for the next interesting problem then... it seems the event # may change between boots. Is there any way to predict or set this manually? Or does anyone has any other ideas about this? As it is now, every boot is either complete success or hard lockup. ;):mrgreen:

---

### Post by jrib on 2006-03-02
[QUOTE=stoffe]Now for the next interesting problem then... it seems the event # may change between boots. Is there any way to predict or set this manually? Or does anyone has any other ideas about this? As it is now, every boot is either complete success or hard lockup. ;):mrgreen:[/QUOTE]

[http://floam.sh.nu/?page=guides&section=mx1000](http://floam.sh.nu/?page=guides&section=mx1000) goes into how to do that.  I considered including the procedure in the guide but since my event # seemed to remain the same, I thought it wouldn't be necessary.  Maybe when I have some time, I'll try to find a way to include without complicating things anymore (or if anyone else has the time and verifies it works... :)).

[edit] that link actually uses evdev as a driver and seems to have simpler instructions, so maybe once dapper arrives setting up the mouse will be a little simpler

---

### Post by stoffe on 2006-03-03
[QUOTE=_jason][http://floam.sh.nu/?page=guides&section=mx1000](http://floam.sh.nu/?page=guides&section=mx1000) goes into how to do that.  I considered including the procedure in the guide but since my event # seemed to remain the same, I thought it wouldn't be necessary.  Maybe when I have some time, I'll try to find a way to include without complicating things anymore (or if anyone else has the time and verifies it works... :)).

[edit] that link actually uses evdev as a driver and seems to have simpler instructions, so maybe once dapper arrives setting up the mouse will be a little simpler[/QUOTE]
The info in that link worked perfectly, real easy to setup and works perfectly! There's a bug (unrelated to this, really) where the evdev driver makes gnome-settings-daemon crash though, so it may not be for everyone until that gets fixed. [https://launchpad.net/distros/ubuntu/+source/control-center/+bug/27143](https://launchpad.net/distros/ubuntu/+source/control-center/+bug/27143)

---

### Post by phux on 2006-03-14
Hi,

i have trouble, getting my MX1000 to work as i want.

Vertical-Scrolling does not work at all an the output of 
```
sudo logitech_applet -s 800
``` is
```
001/003     046D/C50E   M-RAG97         MX1000 Laser Mouse
   Channel 1    Battery: 7    Single channel   No 800cpi support   No Horiz Roller   No Vert Roller   2 butt.
```

How can i enable 800cpi and cruise control?

Buttonmapping: (Button-xevNumber)
Left-1, Right-3, Middle-2, Scrollup-4, Scrolldown-5, ThumbForward-9, ThumbBackward-8, ThumbMiddle-10, WheelClickUpper-11, WheelClickLower-12

thx

---

### Post by jrib on 2006-03-14
[QUOTE=phux]
How can i enable 800cpi and cruise control?
[/QUOTE]
afaik the mx1000 uses the max resolution all the time and there is no need to use a program to increase it.

to enable cruise control I do this:
[http://ubuntuforums.org/showthread.php?p=706981&highlight=lmctl#post706981](http://ubuntuforums.org/showthread.php?p=706981&highlight=lmctl#post706981)

---

### Post by hed on 2006-03-14
All my buttons work fine now, but I've a problem.
If I disconnect my mouse from the USB port, and then I reconnect it, then my mouse don't works 'till I restart de X server. I don't need to restart the computer, only the X server.
¿Any ideas?

---

### Post by rantak on 2006-03-15
Just upgraded to Dapper, my mx1000 was working perfectly in Breezy.

I had multiple problems with the how-to, first the evdev protocol problem, then the
bug in gnome-control-center that has been mentioned in this thread. Now the mouse is working basically ok, xev recognizes all the buttons but my sidescroll still doesn't work in firefox. I changed the options in about:config. 

Also somebody said that to increase the speed of cruise control you should change the variables at about:config again, but that didn't change the speed for me at all. Anyone tried this with success?

Third problem is that I'd want to use the b10 button to change between windows (i.e.  
alt+tab) I haven't succeeded in that. The gnome keyboard shortcuts doesn't recognize the keys I have set in .xbindkeysrc. This also worked in Breezy if i remember correctly.

---

### Post by phux on 2006-03-15
Well, i tried lmctl but it does not change my state.

Horizontal scrolling is still impossible.
If i try to, both buttons work as Left_Mouse-Button.
I tried all buttons, and none works as horizontal scrolling.

My xorg.conf-entry:
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Protocol"              "evdev"
        Option          "Dev Name"              "Logitech USB RECEIVER"
	Option          "Dev Phys"		"usb-*/input0"
	Option		"Device"		"/dev/input/event0"
        Option          "Buttons"               "12"
        Option          "ZAxisMapping"          "4 5 9 8"
EndSection

---

### Post by jrib on 2006-03-15
[QUOTE=phux]Well, i tried lmctl but it does not change my state.

Horizontal scrolling is still impossible.
If i try to, both buttons work as Left_Mouse-Button.
I tried all buttons, and none works as horizontal scrolling.

My xorg.conf-entry:
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Protocol"              "evdev"
        Option          "Dev Name"              "Logitech USB RECEIVER"
	Option          "Dev Phys"		"usb-*/input0"
	Option		"Device"		"/dev/input/event0"
        Option          "Buttons"               "12"
        Option          "ZAxisMapping"          "4 5 9 8"
EndSection[/QUOTE]

```
        Option          "ZAxisMapping"          "4 5 9 8"
```
should be 
```
        Option          "ZAxisMapping"          "4 5 7 6"
```
but I don't know if that will help.

---

### Post by jrib on 2006-03-15
[QUOTE=rantak]Just upgraded to Dapper, my mx1000 was working perfectly in Breezy.

I had multiple problems with the how-to, first the evdev protocol problem, then the
bug in gnome-control-center that has been mentioned in this thread. Now the mouse is working basically ok, xev recognizes all the buttons but my sidescroll still doesn't work in firefox. I changed the options in about:config. 

Also somebody said that to increase the speed of cruise control you should change the variables at about:config again, but that didn't change the speed for me at all. Anyone tried this with success?

Third problem is that I'd want to use the b10 button to change between windows (i.e.  
alt+tab) I haven't succeeded in that. The gnome keyboard shortcuts doesn't recognize the keys I have set in .xbindkeysrc. This also worked in Breezy if i remember correctly.[/QUOTE]

I'll be sure to make a note on the guide about it not working properly in dapper.  See page 10 of this thread to see how stoffe got it to work

---

### Post by phux on 2006-03-16
[QUOTE=_jason]```
        Option          "ZAxisMapping"          "4 5 9 8"
```
should be 
```
        Option          "ZAxisMapping"          "4 5 7 6"
```
but I don't know if that will help.[/QUOTE]

No strangely it doesnt.
It just changes the forward/backward function to work with the Y-axis of the wheel instead of the thumbbuttons.

---

### Post by morwyn on 2006-03-23
Well, I got excited when I saw this thread..... then I ran into a problem. When I typed  cat proc/bus/input/devices, the list showed up, but for some reason, my keyboard (Logitech G15) is showing up three times. I can only see PC speakers and the three instances of the keyboard and nothing for the mouse, since it scrolled off screen. Is there someway for me to go into this file to edit it, just so that I can see what is listed for my mouse? I sure would appreciate some help...

---

### Post by jrib on 2006-03-23
[QUOTE=morwyn]Well, I got excited when I saw this thread..... then I ran into a problem. When I typed  cat proc/bus/input/devices, the list showed up, but for some reason, my keyboard (Logitech G15) is showing up three times. I can only see PC speakers and the three instances of the keyboard and nothing for the mouse, since it scrolled off screen. Is there someway for me to go into this file to edit it, just so that I can see what is listed for my mouse? I sure would appreciate some help...[/QUOTE]

try 'less' instead of 'cat'

---

### Post by morwyn on 2006-03-26
well, I got it working... thanks for the tutorial! just one more question. I don't know how to add xbindkeys to my startup programs now that I have switched to kde. Could someone help out this n00b?

---

### Post by jrib on 2006-03-26
[QUOTE=morwyn]well, I got it working... thanks for the tutorial! just one more question. I don't know how to add xbindkeys to my startup programs now that I have switched to kde. Could someone help out this n00b?[/QUOTE]

checkout page 6 of this thread

---

### Post by morwyn on 2006-03-26
[QUOTE=_jason]checkout page 6 of this thread[/QUOTE]

I read about ~/.kde/Autostart, but unfortunately, it's not working. I copied (cp) xbindkeysrc  to that directory. I had it list in that directory and it shows it is there, but i still have to manually start it. do you have any suggestions?

---

### Post by jrib on 2006-03-27
[QUOTE=morwyn]I read about ~/.kde/Autostart, but unfortunately, it's not working. I copied (cp) xbindkeysrc  to that directory. I had it list in that directory and it shows it is there, but i still have to manually start it. do you have any suggestions?[/QUOTE]

I don't use kde but it might be best to just symlink it there instead of copying it

---

### Post by TheSage on 2006-03-27
Hey.

I've now got my mouse working perfectly in firefox. In windows, I had the middle side button (button 10) bound to F5, in order to refresh the page. So far, I haven't worked out how to do this; could anyone help? 

Thanks,

Sage

---

### Post by berserker on 2006-03-27
[QUOTE=TheSage]Hey.

In windows, I had the middle side button (button 10) bound to F5, in order to refresh the page. So far, I haven't worked out how to do this; could anyone help?[/QUOTE]

In your ~/.xbindkeysrc add this:

```
"xvkbd -xsendevent -text "\[Control_L]\[r]""
  b:10
```

---

### Post by TheSage on 2006-03-27
Thanks! Now I feel even more at home in Kubuntu :)

Sage

---

### Post by PowerLlama on 2006-03-28
I can't seem to get this to work properly on mine. I'm using Dapper drake, and so far everything seems to run properly, but my buttons are different or something.

My xconfig looks like this:

 Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Dev Phys"              "usb-*/input0"
        Option          "Device"                "/dev/input/event1"
        Option          "Buttons"               "12"
        Option          "ZAxisMapping"          "4 5 7 6"
 EndSection

I'm not getting any X crashes (which is an improvement) but I also can't seem to use the thumb buttons at all.

If I run xev it lists my button 8 as button 49, and buttons 9 and 10 don't show up at all. It also lists button 11 and 12 as 4 and 5, without xbindkeys running. Well actually it lists the down button as button 5 upon press, and button 33 upon release.

I have no idea what's going on. ](*,)


Oh, but scrolling side to side does work.

---

### Post by PowerLlama on 2006-03-30
Anyone at all?

*edit after reading another thread, it's an XGL error. Nevermind.

---

### Post by tkite on 2006-04-05
[QUOTE=_jason]Well it took a few weeks of scouring the internet for clues before I finally got my mx1000 to work just like I expected it to, but I finally did it. The howto is available on the wiki at the following url: 

[https://wiki.ubuntu.com/MX1000Mouse](https://wiki.ubuntu.com/MX1000Mouse) .

Let me know if it works for you.  I welcome any and all questions and comments.  Even if you don't like the way a particular sentence sounds, let me know :D

The howto is a product of several small changes I made over several weeks as I tried to get all 12 buttons to function correctly during my spare time so I may have forgotten to include a detail or two (I hope not).  Sorry if I did, but I'm sure we can figure it out.  Just post any problems you are having.[/QUOTE]
I have the MX3100 keyboard/mouse combo connected via a PS/2 KVM with a Windows XP machine as well.  Everything works on mouse and keyboard on the XP machine, so I know the KVM and the PS/2 don't interfere with anything.  I followed your instructions, which got the back/forward thumb buttons working in addition to the already working left click, right click, middle click, and scroll up/down.  Unfortunately cruise control, horizontal scrolling, and the middle thumb button don't do anything.  In xev they don't even register as events, only the buttons that work do.  Here's the relevent section of my xorg.config:
----
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Protocol"				"evdev"
	Option		"Dev Name"			"ImExPS/2 Logitech Explorer Mouse"
	Option		"Dev Phys"			"isa0060/serio1/input0"
	Option		"Device"				"/dev/input/event1"	#works also with /dev/input/mice
	Option		"Buttons"				"12"
	Option		"ZAxisMapping"	"4 5 7 6"
	Option		"Resolution"			"800"
EndSection
----
Additionally, my .xbindkeysrc is:
----
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
   b:8
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
   b:9
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
   b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
   b:12
----
I've looked and looked for how to fix this.  I had SuSE 10 on this machine before I switched to Ubuntu and didn't have any luck beyond what I have now then either.  Any ideas besides spamming Logitech until they release official Linux drivers?

---

### Post by PowerLlama on 2006-04-05
Alright, I have a new question.

I'm back on Breezy, and I got most of this stuff working. The only thing that seems to be weird are my buttons 11 and 12 (the cruise control ones), and middle click.

I can't use my middle click to close tabs in firefox, instead whenever I press it, it loads up whatever I just copied, like if I copied a URL and middle-click, it will load up the URL.

Also, in xev, before xbindkeys, xev saw my cruise control buttons as 4 and 5 whenever they were held down, but 11 and 12 on release.

Now what I want to do is set my button 12 to middle click (because I hate middle-clicking with the 1000, and I need the function), but I can't do that. It just won't work. It just keeps scrolling instead of middle-clicking.

My xbindkeysrc looks like this:

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
   b:8
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
   b:9
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
   b:11
"echo ButtonPress 2 ButtonRelease 2 | xmacroplay -d 0 :0.0"
   b:12
```

Any help?

---

### Post by jrib on 2006-04-05
For your firefox problem, enter 'about:config' in the address bar and change middlemouse.contentLoadURL to false.

As for changing the auto-scroll down button to middle click, you will probably want to disable cruise control.  Otherwise, when you middle click, your pages are going to scroll.  mx1000 seems to send a button press 11 then repeat button 4 (mouse scroll) then a button release 11 when you let go.  I only know how to disable cruise control with lmctl (a program that you will have to compile yourself).  Instructions are somewhere in this thread if you search the thread for lmctl, you should find it.  If not, just let me know and I'll give you the instructions again.  If you aren't comfortable compiling, feel free to ask for advice, it's an easy compile.  A problem with disabling cruise control is that your horizontal scroll, won't automatically repeat, it will just scroll once (like tapping the left and right arrow keys).

---

### Post by rantak on 2006-04-07
I reported some problems few weeks ago with the guide & dapper flight 4. 

I installed a clean flight 6 kubuntu yesterday, followed the guide when installing the mx1000 and everything is now working correctly. I guess the problems earlier where caused by me dist-upgrading from breezy.

---

### Post by morwyn on 2006-04-09
Following your instructions I was able to get my mouse up and running. Thank You. However, I do like to configure my mouse keys for different funtions. Can I edit xbindkeys to get it to work, and if so, what do i put? I did figured out how to put delete as button 10 and enter as button 7. But I would like to put button 6 as backspace, button 11 as copy, and button 12 as paste. I'm not sure how to do these three. I'd appreciate your input.

---

### Post by SilvereX on 2006-04-22
Hello,

I've got Logitech MX400 with Dapper Flight 6.
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/event1"
        Option          "Name"                  "Logitech MX400"
        Option          "Buttons"               "9"
        Option          "ZAxisMapping"          "4 5"
EndSection
```

xev recognizes all buttons:
1 - left click
2 - middle click
3 - right click
4 - scroll up
5 - scoll down
6 - scroll left (works as back in Firefox)
7 - scroll right (works as forward in Firefox)
8, 9 - as "Back" and "Forward" buttons on mouse, which I want to map as doubleclick and middleclick.

/home/silverex/.middlekey:
```
ButtonPress 2
ButtonRelease 2
```

/home/silverex/.doublekey:
```
ButtonPress 1
ButtonRelease 1
ButtonPress 1
ButtonRelease 1
```

/home/silverex/.xbindkeysrc:
```
"xmacroplay :0 < ~/bin/.middlekey"
b:8
"xmacroplay :0 < ~/bin/.doublekey"
b:9
```

Now, if I call these commands from command line, they work (middle-click and double-click). However, they do not work when xbindkeys call them. Here's an example output of xbindkeys -v -n:

```
displayName = :0.0
rc file = /home/silverex/.xbindkeysrc
rc guile file = /home/silverex/.xbindkeysrc.scm
getting rc guile file /home/silverex/.xbindkeysrc.scm.
WARNING : /home/silverex/.xbindkeysrc.scm not found or reading not allowed.
2 keys in /home/silverex/.xbindkeysrc

min_keycode=8     max_keycode=255 (ie: know keycodes)
"xmacroplay :0 < ~/bin/.middlekey"
    m:0x0 + b:8   (mouse)
"xmacroplay :0 < ~/bin/.doublekey"
    m:0x0 + b:9   (mouse)
starting loop...
Button press !
e.xbutton.button=8
e.xbutton.state=16
"xmacroplay :0 < ~/bin/.middlekey"
    m:0x0 + b:8   (mouse)
Start program with fork+exec call
XTest for server ":0.0" is version 2.2.

ButtonPress: 2
ButtonRelease: 2
ButtonRelease: 2
Button press !
e.xbutton.button=2
e.xbutton.state=16
Button release !
e.xbutton.button=2
e.xbutton.state=528
xmacroplay: pointer and keyboard released.
Catch CHLD signal -> pid 11408 terminated
Button press !
e.xbutton.button=9
e.xbutton.state=16
"xmacroplay :0 < ~/bin/.doublekey"
    m:0x0 + b:9   (mouse)
Start program with fork+exec call
XTest for server ":0.0" is version 2.2.

ButtonPress: 1
ButtonRelease: 1
ButtonPress: 1
ButtonRelease: 1
ButtonRelease: 1
Button press !
e.xbutton.button=1
e.xbutton.state=16
Button release !
e.xbutton.button=1
e.xbutton.state=272
xmacroplay: pointer and keyboard released.
Catch CHLD signal -> pid 11412 terminated

```

Looks like no errors, but it just doesn't work - I don't get the effect of either middle-click or doule-click in Firefox or in terminal.

Any ideas?

---

### Post by jrib on 2006-04-26
[QUOTE=SilvereX]Hello,
/home/silverex/.xbindkeysrc:
```
"xmacroplay :0 < ~/bin/.middlekey"
b:8
"xmacroplay :0 < ~/bin/.doublekey"
b:9
```
[/QUOTE]

try giving the full path to the middlekey and doublekey files not using the tilde:

```
"xmacroplay :0 < /home/username/bin/.middlekey"
b:8
"xmacroplay :0 < /home/username/bin/.doublekey"
b:9
```

---

### Post by SilvereX on 2006-04-27
[QUOTE=_jason]try giving the full path to the middlekey and doublekey files not using the tilde:

```
"xmacroplay :0 < /home/username/bin/.middlekey"
b:8
"xmacroplay :0 < /home/username/bin/.doublekey"
b:9
```[/QUOTE]

yes, I have already tried that, effect is also the same, Anyway, command _is_ being executed, as seen from xbindkeys output. But it just doesn't work.

---

### Post by jrib on 2006-04-27
does it matter that you are using :0 instead of :0.0?  Also, does it work if you echo and pipe to it?  do other commands work (like delete maybe)?

---

### Post by acidphex on 2006-05-10
My mx1000 is detected as ImPS/2, how would I go about configuring that?

---

### Post by Pugaciov on 2006-05-12
Hi all
I followed the wiki for the MX1000, now back and forward buttons work in Firefox, but everything else does not. Left and right scroll work as zoom in and out when viewing an image, and the wheel-middle button seem to open the last link copied in the clipboard.

---

### Post by Pugaciov on 2006-05-12
[QUOTE=_jason]For your firefox problem, enter 'about:config' in the address bar and change middlemouse.contentLoadURL to false.

As for changing the auto-scroll down button to middle click, you will probably want to disable cruise control.  Otherwise, when you middle click, your pages are going to scroll.  mx1000 seems to send a button press 11 then repeat button 4 (mouse scroll) then a button release 11 when you let go.  I only know how to disable cruise control with lmctl (a program that you will have to compile yourself).  Instructions are somewhere in this thread if you search the thread for lmctl, you should find it.  If not, just let me know and I'll give you the instructions again.  If you aren't comfortable compiling, feel free to ask for advice, it's an easy compile.  A problem with disabling cruise control is that your horizontal scroll, won't automatically repeat, it will just scroll once (like tapping the left and right arrow keys).[/QUOTE]

Ok this post was helpful for what concerning the middle click loading URLs, but I didn't understand very well...cruise control doesn't work at all here, if I press the cruise control down button, it's like scrolling the wheel...is it normal and I have to configure lmctl as you said or not?

Thanks.

edit: ok, I'm still searching and reading the thread; using "general.autoScroll" to "true" makes the fast scroll appear after middle click. Now I think the last thing missing is the horizontal scroll.

---

### Post by GregaS on 2006-05-23
I have dapper drake and after changing xorg.conf, x does not boot up anymore. It says something about Kernel panic. Help me please.

---

### Post by sorrow777 on 2006-05-24
fyi.. i'm using dapper and i got my mx1000 to work.  In my .xbindkeysrc i had to change the location of xvkbd to usr/bin/xvkbd instead of the x11r6 location

Files are here.

```
 .xbindkeysrc
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
   b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
   b:9
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[r]""
  b:10
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
   b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
   b:12

```

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "CorePointer"
    #Option         "Protocol"     "evdev"
    Option         "Dev Name"     "Logitech USB Reciever"
    Option         "Dev Phys"     "usb-*/input0"
    Option         "Device"       "/dev/input/event0"
    Option         "Buttons"      "12"
    Option         "ZAxisMapping" "4 5 7 6"
EndSection

```

---

### Post by GregaS on 2006-05-24
That doesn't help me, because I'm stuck at xorg.conf :(

---

### Post by GregaS on 2006-05-27
I got it to work on Dapper.

> Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "evdev"
    Option          "CorePointer"
    Option        "Dev Name"    "Logitech USB RECIEVER"
    Option        "Device"        "/dev/input/event1"
    Option        "Buttons"        "12"
    Option        "ZAxisMapping"    "4 5 13 14"
EndSection

All the buttons work now, but all buttons have a function of left click :(

---

### Post by adam.tropics on 2006-05-29
Excellent, all working, but did anyone ever manage to get the cruise/scroll thing to speed up?

---

### Post by GregaS on 2006-05-29
Help me anyone?

---

### Post by adam.tropics on 2006-05-29
GregaS, I believe your xorg.conf should have,

```
Option         "ZAxisMapping" "4 5 7 6"

```

---

### Post by catfarm on 2006-06-05
[QUOTE=sorrow777]fyi.. i'm using dapper and i got my mx1000 to work.  In my .xbindkeysrc i had to change the location of xvkbd to usr/bin/xvkbd instead of the x11r6 location[/QUOTE]

Thank you so much for this, it stumped me for a while, well, until I got to your post... now all is well in Dapper land.

---

### Post by czhu on 2006-06-12
[QUOTE=sniper85]I am having trouble restarting X after editing xorg.conf. Here is my xorg.conf file. I get the error:

Configured Mouse: cannot open input device
No core pointer

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Nov 22 18:04:42 PST 2005

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Protocol"              "evdev"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Dev Phys"              "usb-*/input1"
        Option          "Device"                "/dev/input/event1"
        Option          "Buttons"               "12"
        Option          "ZAxisMapping"          "4 5 7 6"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       31.0 - 80.0
    VertRefresh     59.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

Here is my output from cat /proc/bus/input/devices

```
I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-7/input0
H: Handlers=kbd event0
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-7/input1
H: Handlers=kbd mouse0 event1 ts0
B: EV=f
B: KEY=7fffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=143
B: ABS=100 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd event2
B: EV=40001
B: SND=6


```[/QUOTE]

I got the exact problem as sniper85, I also have the mx3100 (wireless keyboard +mx1000) i think that's the problem. Anyhelp in getting this to work will be greatly appreciated :)

---

### Post by geearf on 2006-06-12
Hello,

just to tell you that everything is fine now under dapper, but don't ask me why.
Strange thing is that the 2 buttons on the side are still not that well seen by xev but as they seem to do just fine I don't really care.
Now I just have to get used to it again :)

---

### Post by jrib on 2006-06-22
I've updated the wiki with instructions that work for me on dapper.  Let me know if they work ok for you

---

### Post by jrib on 2006-06-22
[QUOTE=adam.tropics]Excellent, all working, but did anyone ever manage to get the cruise/scroll thing to speed up?[/QUOTE]

Yeah, I wish I could find a way to do that as well

---

### Post by tempo500 on 2006-06-22
worked!!! thanx... maybee you should rename the title of the wiki... was not shure if i should try it with my logitech click plus mouse.:rolleyes: phil

---

### Post by bekok on 2006-06-24
I have a Mx 700, but does this guido also work for that one? Caus i'd like to active my back/forward buttons :)

---

### Post by jrib on 2006-06-24
[QUOTE=tempo500]worked!!! thanx... maybee you should rename the title of the wiki... was not shure if i should try it with my logitech click plus mouse.:rolleyes: phil[/QUOTE]

Great to hear.  The procedure should be very similar for other mice.  The only thing that could be unique is the line that maps buttons 6 and 7 correctly.  Without that line the Horizontal Scroll is backwards.  I'll see if I can write something more general and then people may be able to post the individual quirks for each mouse if there are any.  Thanks for the idea.  Did you have to make any modifications?

[QUOTE=bekok]I have a Mx 700, but does this guido also work for that one? Caus i'd like to active my back/forward buttons :)[/QUOTE]

Here are the basic steps you should follow, if this doesn't work it's as simple as restoring your /etc/X11/Xorg.conf.  You might want to look through the mx1000 tutorial too to see the basic steps:

1.  First we need to get the "Name" for your mouse:
```

cat /proc/bus/input/devices
```
Mine shows up as:
```
I: Bus=0003 Vendor=046d Product=c50e Version=2500
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

```

Mine was "Logitech USB Receiver" as you can see.

2.  Now modify your Xorg.conf (make a backup first), remove the "Configured Mouse" section (see the wiki) and replace it with:
```

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
EndSection

```

You should replace "Logitech USB Reciever" with whatever you got.  Notice I left out the HWHEEL line since we aren't sure you need it.

3.  Read the wiki part about setting the CorePointer in the ServerLayout section
4.  Ok now restart X with ctrl+alt+backspace
5.  See what works on your mouse and what doesn't
6.  Run xev in a terminal and press the buttons that are giving you trouble.
-If something is switched you can either use a line similar to HWHEEL I used (see man evdev or ask here) or you can use xmodmap
-if something isn't happening, like back and forward don't work but they generate buttons 8 and 9 for example, than you can use an xbindkeys like I did.


If we have good results with this I'll definitely clean this up and put something on the wiki so everyone can post up their xorg.conf section and xbindkerys/xmodmaps for their mouse on the wiki.  Wouldn't be hard to write a nice little script either...

---

### Post by geearf on 2006-06-24
Hello,

thanks for the tip about the "name", I was having problems with the device changing, and the udev rules working for me but not for xorg ... now it works flawlessly (or it seems) thanks.

---

### Post by jrib on 2006-06-24
[QUOTE=geearf]Hello,

thanks for the tip about the "name", I was having problems with the device changing, and the udev rules working for me but not for xorg ... now it works flawlessly (or it seems) thanks.[/QUOTE]

Yeah, man evdev is what clued me in on that.  It seems to happen with the adoption of udev that the event#'s don't stay constant after reboots and such.  I was writing udev rules that matched the Name to give the mouse a consistent event# but I realized that that was the same as just having X match the name directly.

The only problem I see with it is if someone has a Logitech mouse and keyboard that give the same Name.  Not really sure how X will handle that scenario...

---

### Post by geearf on 2006-06-25
I guess yes, with a pack it might failed, but I don't have one of those, so I'm ok :)

---

### Post by geearf on 2006-06-25
by the way, I'm still using it on an ps/2 input, not USB.

Also do you think it would be possible to get a higher speed for b10 and b11? cause it's still quite slow ...

Thanks

---

### Post by Giga on 2006-06-25
Jason, do you know if Logitech keyboard dinovo Laser (bluetooth 2.0)
works as well as MX1000 in Linux?

Thanks

---

### Post by Hypoxiacion on 2006-06-25
I've got my buttons setup, now could someone please tell how to bind one of my side buttons to a keyboard key for example: Insert, Delete etc.

Thanks in advance!

---

### Post by geearf on 2006-06-25
@Hypoxiacion : look at the xbindkeys thing at the end of the wiki, that should do it.

---

### Post by jrib on 2006-06-26
[QUOTE=geearf]by the way, I'm still using it on an ps/2 input, not USB.

Also do you think it would be possible to get a higher speed for b10 and b11? cause it's still quite slow ...

Thanks[/QUOTE]

Interesting, I might try freeing up a usb port over here too.  Though the action for my forward and back seem to happen as soon as I press the buttons, I'll let you know if I get the same delay as you on PS/2 or if it's something else.  You could try using something other than xbindkeys, I think imwheel will let you bind actions too.

[QUOTE=Giga]Jason, do you know if Logitech keyboard dinovo Laser (bluetooth 2.0)
works as well as MX1000 in Linux?

Thanks[/QUOTE]

No sorry, I don't know about the keyboards

---

### Post by Hypoxiacion on 2006-06-26
[QUOTE=geearf]@Hypoxiacion : look at the xbindkeys thing at the end of the wiki, that should do it.[/QUOTE]
Yeah I saw that part, just unsure where I'd need to inseRt the information.

I want to bind the top side button to the delete key and the button above the scrollwheel to the insert key.

I need those keys mostly for gaming, I.E bind delete key to side button = weapon reload..

Just like setpoint does in windows.

---

### Post by jrib on 2006-06-26
[QUOTE=Hypoxiacion]Yeah I saw that part, just unsure where I'd need to inseRt the information.

I want to bind the top side button to the delete key and the button above the scrollwheel to the insert key.

I need those keys mostly for gaming, I.E bind delete key to side button = weapon reload..

Just like setpoint does in windows.[/QUOTE]

```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"/usr/bin/xvkbd -xsendevent -text "\[Delete]""
  b:10
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14

```

I have "delete" bound to the middle side button.  You can figure out the numbers, by running 'xev'.

You may have a problem using the button above the scroll for "insert" since after that button is pressed, the mouse starts sending 4's over and over, so it will be like you are scrolling up.  You could disable cruise control but then the side scroll becomes pretty much useless imo.  If you want to disable it anyway, just google for 'lmctl' and search for 'lmctl' in this forum thread, there are pretty decent use instructions somewhere.  If you have any problems with it, don't hesitate to post

---

### Post by geearf on 2006-06-27
[quote=_jason]Interesting, I might try freeing up a usb port over here too.  Though the action for my forward and back seem to happen as soon as I press the buttons, I'll let you know if I get the same delay as you on PS/2 or if it's something else.  You could try using something other than xbindkeys, I think imwheel will let you bind actions too.
[/quote]

it's not that there is a delay, it's just that button 10 and 11 don't scroll the page as quickly as they would under Windows. So it's way faster to just drag the little thing and scroll it down the good old way.

PS/2 works great though ;)

---

### Post by jrib on 2006-06-27
[QUOTE=geearf]it's not that there is a delay, it's just that button 10 and 11 don't scroll the page as quickly as they would under Windows. So it's way faster to just drag the little thing and scroll it down the good old way.

PS/2 works great though ;)[/QUOTE]

oh, yes I know what you are referring to now.  I agree with you too and wish I could control its speed.

The one thought I have had is to turn off smart scroll and just have something catch the button press event, and start sending out scroll signals itself until the button is released.

---

### Post by geearf on 2006-06-29
Maybe that would work, the problem is that once we press the buttons they 'transform' themselves into the wheel ones ... hmm I'm trying something, let's see how it works.

---

### Post by jrib on 2006-06-29
[QUOTE=geearf]Maybe that would work, the problem is that once we press the buttons they 'transform' themselves into the wheel ones ... hmm I'm trying something, let's see how it works.[/QUOTE]

After I disable smart scroll using the lmctl program it only generates an 11 press and an 11 release, and the same for 12,13,14.  The mouse doens't send in the real events anymore in between the press and release.  But let me know if you have any progress with your idea

---

### Post by geearf on 2006-06-30
nothing on my side, except that there seems that the xbindkey file is not really needed anymore except for the back and forth thing for firefox.

lmctl, so it's a no-go for me if I want to still use a ps/2 port like I'm doing, but I'm still interested because my laptop has no ps/2 port, only usb ...

---

### Post by jrib on 2006-06-30
[QUOTE=geearf]nothing on my side, except that there seems that the xbindkey file is not really needed anymore except for the back and forth thing for firefox.
[/QUOTE]

The other entries in the xbindkeys are so that text doesn't get highlighted when you use the smart scroll, it's a bit of a hack

---

### Post by geearf on 2006-07-01
I never use that, I don't like it.

---

### Post by saax on 2006-07-02
How to add xbindkeys to startup programs in Kubuntu 6.06

---

### Post by stonefeet on 2006-07-05
i've read all over this board for solutions to my mx1000 problem and i've tried all of the stuff and i still cannot get my mx1000 bluetooth mouse to function 100% (it wouldn't have been a huge deal until the scroll wheel randomly stopped working)
so i'm hoping you guys can give me some help

when i follow the wiki howto i can't even boot back into X

here's my cat /proc/bus/input/devices
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c70e Version=4001
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1d.7-3.3.2/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70a Version=4001
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1d.7-3.3.3/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse0 event3 ts0
B: EV=f
B: KEY=c0002 400 0 0 fff0001 f80 78000 6039fa d841d7ad 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0

I: Bus=0003 Vendor=0a5c Product=3502 Version=0100
N: Name="HID 0a5c:3502"
P: Phys=usb-0000:00:1d.7-3.4.2/input0
S: Sysfs=/class/input/input4
H: Handlers=kbd event4
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: LED=7

I: Bus=0003 Vendor=0a5c Product=3503 Version=0100
N: Name="HID 0a5c:3503"
P: Phys=usb-0000:00:1d.7-3.4.3/input0
S: Sysfs=/class/input/input5
H: Handlers=mouse1 event5 ts1
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```

and my xorg.conf

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 2005FPW"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Monitor		"DELL 2005FPW"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by bbzidane on 2006-07-08
just wanna say thanks for the guide
one thing though,
im having probs getting the back/forward buttons working
i followed the instructions for dapper on the wiki and the mouse works, but the back/forward does what it did with the old drivers

is there something im missing?

thanks

---

### Post by jrib on 2006-07-08
saax, this seems to have some info for you: [http://www.ubuntuforums.org/showthread.php?t=163859](http://www.ubuntuforums.org/showthread.php?t=163859) but I don't use kde so I can't tell you myself how to add porgrams to startup.


stonefeet, do you have just an mx1000 or did you purchase some kind of combo?  I ask because as you can see, your mouse does not use the "Logitech USB Receiver" name.


> **bbzidane said:**
> just wanna say thanks for the guide
one thing though,
im having probs getting the back/forward buttons working
i followed the instructions for dapper on the wiki and the mouse works, but the back/forward does what it did with the old drivers

is there something im missing?

thanks

xbindkeys should be taking care of the back and forward.  Kill xbindkeys and start xev in a terminal.  What button numbers are the back and forward buttons generating?

---

### Post by stonefeet on 2006-07-09
> **_jason said:**
> saax, this seems to have some info for you: [http://www.ubuntuforums.org/showthread.php?t=163859](http://www.ubuntuforums.org/showthread.php?t=163859) but I don't use kde so I can't tell you myself how to add porgrams to startup.


stonefeet, do you have just an mx1000 or did you purchase some kind of combo?  I ask because as you can see, your mouse does not use the "Logitech USB Receiver" name.




xbindkeys should be taking care of the back and forward.  Kill xbindkeys and start xev in a terminal.  What button numbers are the back and forward buttons generating?

yea i've got the desktop package
bluetooth only, getting this mouse to work is the only thing that's stopping me from canning windows altogether

---

### Post by stonefeet on 2006-07-11
after a fresh install

i'm going to give this another shot when i get home, from the wiki

btw
the keyboard works 100% straight out of the box, volume controls and zoom and such

---

### Post by stonefeet on 2006-07-11
maybe i'm just talking to myself here but i figured out after a fresh install that my keyboard is connected to the BT mini-receiver and the mouse for some reason connects to my other bluetooth adapter

```
I: Bus=0003 Vendor=0a5c Product=3503 Version=0100
N: Name="HID 0a5c:3503"
P: Phys=usb-0000:00:1d.7-3.4.3/input0
S: Sysfs=/class/input/input5
H: Handlers=mouse1 event5 ts1
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3
```

that one, so i was able to mess around with the xorg.conf and get it so that x would come back up but none of the extra buttons would work

xev returned nothing when the buttons were pressed

---

### Post by stonefeet on 2006-07-11
that was the solution

removed the kensington bluetooth adapter and rebooted with just the logitech one and it worked 100% with the default xorg.conf

thanks for steering me in the right direction

---

### Post by Bourlotieris on 2006-07-16
What do you mean? Didn't you change ANYTHING at all at the default xorg.conf file? I am having the diNovo bluetooth set (mouse + keyboard + mediapad).
The command cat /proc/bus/input/devices gives me:
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c70b Version=4002
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:03.0-1.2/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70c Version=4002
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:03.0-1.3/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse0 event3 ts0
B: EV=f
B: KEY=c0002 400 0 0 fff0001 f80 78000 6039fa d841d7ad 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0

As you can see I have 2 "Logitech Logitech BT Mini-Receiver" and with the default wiki instructions I can't restart X if I use that as a name. With the default xorg.conf back and forward works but no sidescroll.
Any suggestions?

---

### Post by jrib on 2006-07-17
> **Bourlotieris said:**
> What do you mean? Didn't you change ANYTHING at all at the default xorg.conf file? I am having the diNovo bluetooth set (mouse + keyboard + mediapad).
The command cat /proc/bus/input/devices gives me:

[snip]

As you can see I have 2 "Logitech Logitech BT Mini-Receiver" and with the default wiki instructions I can't restart X if I use that as a name. With the default xorg.conf back and forward works but no sidescroll.
Any suggestions?

See if you can figure out how to write a udev rule to give the mouse a consistent event#.  Maybe this can help [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html) .  I haven't had a chance to do this myself, but I'd be glad to hear how it goes.

I used to use this as /etc/udev/rules.d/10-local.rules:
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"

But as you can see that is only matching the name, which is meaningles.

If you can get that to work, then just use the event# instead of the name in your xorg.conf

---

### Post by Bourlotieris on 2006-07-17
> **_jason said:**
> See if you can figure out how to write a udev rule to give the mouse a consistent event#.  Maybe this can help [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html) .  I haven't had a chance to do this myself, but I'd be glad to hear how it goes.

I used to use this as /etc/udev/rules.d/10-local.rules:
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"

But as you can see that is only matching the name, which is meaningles.

If you can get that to work, then just use the event# instead of the name in your xorg.conf

Thanx _jason. I shall look this through and come back (hopefully with a solution).

---

### Post by kpolice on 2006-07-18
It's perfect and easy. I only needed 4 minutes to do it.

Thanks

---

### Post by rsk on 2006-07-23
Jason just found your tutorial while trying to make Ubuntu feel more like home, worked like a freaking charm. Thanks bud!

---

### Post by HBK on 2006-07-25
Hi,
Thx for the great tutorial, some parts seem to work for me, some don't ;): I did everything according to the text and it leaves me with the mouse wheel working vertically but not horizontally. Back and forward works in FF, cruise control doesn't... where could the problem be? I'm using dapper and if I can get my MX1000 to work fully that'd be another step towards scrapping XP totally :).

Any help would be very appreciated,
HBK

---

### Post by jrib on 2006-07-25
> **HBK said:**
> Hi,
Thx for the great tutorial, some parts seem to work for me, some don't ;): I did everything according to the text and it leaves me with the mouse wheel working vertically but not horizontally. Back and forward works in FF, cruise control doesn't... where could the problem be? I'm using dapper and if I can get my MX1000 to work fully that'd be another step towards scrapping XP totally :).

Any help would be very appreciated,
HBK

What you described happens to me if I disable smart scroll on the mouse.  The only program in linux that I know of to control this, is lmctl.  It isn't packaged, so you will have to compile it.

There are some basic instructions in some posts I made earlier in this thread, just search inside this thread for 'lmctl'.

If you need some help with compiling, just ask and we'll walk you through it.

---

### Post by HBK on 2006-07-25
Works like a charm, thank you very much :). Is there a way of setting the autocruise speed or is it fixed?

Thanks a lot again for the fast and friendly help :),
HBK

---

### Post by jrib on 2006-07-25
> **HBK said:**
> Works like a charm, thank you very much :). Is there a way of setting the autocruise speed or is it fixed?

Thanks a lot again for the fast and friendly help :),
HBK

In windows, the logitech application allows one to change the scroll speed.  However, I believe this does not actual change a setting on the mouse itself, it may just be the application doing all the work to make it scroll faster.

I agree with you that it would be nice to change the speed a bit.  grearf also expressed interest in this as well.  I don't know of a way to do this.  Although it may be possible to write something similar to the logitech app...

---

### Post by adam.tropics on 2006-07-30
What version of evdev are you all using? I have an older version , as previously the newer packages were broken, but following recent updates the mouse has been freezing pretty randomly. Is there a current but working package in the repos now?

---

### Post by geearf on 2006-07-30
I'm using dapper's one and it's fine.

---

### Post by inlivingcolour on 2006-08-13
Thank you for the great tutorial.  I do have one minor problem.  Sorry if this came up.  I can't get my thumb buttons to start when the system boots up.  I have to do it manually through terminal.  How go I get it to start automatically.  And I tried adding the xbindkeys to Sessions.

---

### Post by jrib on 2006-08-13
> **inlivingcolour said:**
> Thank you for the great tutorial.  I do have one minor problem.  Sorry if this came up.  I can't get my thumb buttons to start when the system boots up.  I have to do it manually through terminal.  How go I get it to start automatically.  And I tried adding the xbindkeys to Sessions.

So it seems that the problem is xbindkeys isn't getting started.  Can you make sure that xbindkeys isn't getting run after login by running 'ps -ef | grep xbindkeys'?  

Also, what version of Ubuntu are you using?

If you put 'gedit' in sessions -> startup, does it work?

What is in your ~/.config/autostart directory? (Paste the contents of xbindkeys.desktop if it is there)

---

### Post by dahamsta on 2006-08-15
Very useful HOWTO, thank you.

---

### Post by Eckstona on 2006-08-21
I have all the buttons set up, but i can't bind them in the games that I play. Does anyone know how to bind mouse buttons to keyboard buttons?:confused:

---

### Post by sque on 2006-08-29
> We are only identifying the device using it's "Name". If this is a problem for you because other devices also identify themselves this way, post at the forum link found at the bottom of this page.

So here I am.. I am on dapper drake and I have the logitech wireless keyboard/mouse(MX700) package. The receiver is connected through 1 usb on the computer and both works from it.

this is the /proc/bus/input/devices
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c50b Version=2100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.0-1/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c50b Version=2100
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.0-1/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse0 event2 ts0
B: EV=7
B: KEY=ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0  0 1878 d800d100 1e0000 0 0 0
B: REL=103

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=40001
B: SND=6

```

So... what can I do for this occasion?

---

### Post by jrib on 2006-08-29
> **Eckstona said:**
> I have all the buttons set up, but i can't bind them in the games that I play. Does anyone know how to bind mouse buttons to keyboard buttons?:confused:

You can use xbindkeys to do this.  In a terminal, try 'xbindkeys -d'.  That should give you a sample rc file you can use with a lot of examples.  To have the command play a mouse button, you can use something similar to what we used to get the mx1000 scroll keys to work correctly.  For example this makes button 14 on the mouse play button 7, but you can change "b:14" to a key on your keyboard instead if you wish.

```
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14

```

Also, in detyabozhye's guide,  [HOWTO: Configuring Logitech mice in Ubuntu 6.06: New Guide]("http://ubuntuforums.org/showthread.php?t=219894"), he introduces a "click" program which seems to allow you to play a mouse button as well.

---

### Post by jrib on 2006-08-29
> **sque said:**
> 
So... what can I do for this occasion?

I don't know of a working solution for this scenario.  
Bourlotieris had a similar situation, and this was my advice, hope it helps:

[http://ubuntuforums.org/showthread.php?p=1267334#post1267334](http://ubuntuforums.org/showthread.php?p=1267334#post1267334)

---

### Post by Nojatron on 2006-08-30
.

---

### Post by bjorkiii on 2006-09-05
I have followed instructions correctly but my back and forward side buttons are not doing anything :( thems the 2 buttons i only wanted to get going as well im on dapper drake 64 bit version .

---

### Post by harryc on 2006-09-13
I have (2) Logitech receivers. (1 for an MX1000 and another for an MX3000 keyboard and mouse combo). What changes do I have to make to the wiki instructions to identify just the MX1000?

harryc@harryc-desktop:~$ cat /proc/bus/input/devices
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c513 Version=3200
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1.1/input0
S: Sysfs=/class/input/input26
H: Handlers=kbd event2
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c513 Version=3200
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1.1/input1
S: Sysfs=/class/input/input27
H: Handlers=kbd mouse0 event3 ts0
B: EV=f
B: KEY=c0002 400 0 0 ff0001 f80 78000 6039fa d841d7ad 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0

I: Bus=0003 Vendor=046d Product=c50e Version=2500
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-1.2/input0
S: Sysfs=/class/input/input28
H: Handlers=mouse1 event4 ts1
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

---

### Post by kayrune on 2006-09-24
I'm trying to get this working on Edgy with a MX3100 mouse/keyboard combo, so far I've run into big problems.

WARNING DO NOT FOLLOW THE INSTRUCTIONS ON THE WIKI! This resulted in loss off keyboard and mouse functions as soon as X started. Meaning I had to get hold of a wired keyboard to fix the problem (ctrl+alt+F1 didn't work)

[I]$cat /proc/bus/input/devices 
I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-4/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c512 Version=3007
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.1-4/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse0 event2 ts0 
B: EV=7
B: KEY=7fffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=143
[/I]


I've tried using every combination of the following lines in the xorg.conf but none would get the mouse working, when I use the "device" option I get the keyboard working again.

[I]	Driver		"evdev"
	Option          "Name"          "Logitech USB Receiver"
	Option          "HWHEELRelativeAxisButtons" "7 6"
	Option		"Device"  "/dev/input/event2"[/I]

Any tips are welcome!

EDIT:

I wrote a udev rule
*sudo gedit /etc/udev/rules.d/19-local.rules*
And added the following line:
*KERNEL=="event[0-9]*", SYSFS{../device/bInterfaceNumber}=="01", NAME="input/mxmouse"*

changed my xorg.conf to the following:
[I]     Driver		"evdev"
	Option		"Device"  "/dev/input/mxmouse"
	Option          "HWHEELRelativeAxisButtons" "7 6"[/I]

And rebootet, now both my keyboard and mouse are working. But xev doesn't output anything on the wheel-sideways, and the thumb buttons are all whacky now !!

---

### Post by mac57 on 2006-09-24
Hi, I have just loaded up Ubuntu 6.06, and followed the instructions at the start of this thread to get my MX1000 working fully. The instructions work great, but I wanted to make one change that I just can't figure out how to get working. 

Right now, the two buttons along the side of the mouse that are used for Forward and Back work like this: the frontmost button does Forward and the backmost button does Back. This is sensible but for whatever reason, I have always done this the other way. How do I reverse these two, so that the frontmost button does Back and the backmost button does Forward?

I have tried changing the mapping in xorg.conf to no good end. I have tried messing with the settings in ~/.xbindkeysrc to no good end. There must be some magic combination I haven't tried yet. Can anyone help?

BTW, I am running Unbuntu 6.06, pretty much standard off the install disk (booted up the LiveCD, selected the install option and used it). All I have done to it since install is to use easyubuntu to load up the nvidia driver, codecs, and fonts. Thanks!

---

### Post by kayrune on 2006-09-25
If I understand correct...

in .xbindkeysrc change

[I]"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9[/I]


to 

[I]"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:9[/I]

---

### Post by doc_holiday on 2006-10-18
I tried the how to, but X doesn't start any more

Here my xorg.conf

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV20 [GeForce3 Ti 500]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"HM903D/DT"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV20 [GeForce3 Ti 500]"
	Monitor		"HM903D/DT"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice     "Logitech MX1000" "CorePointer"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by cudaman73 on 2006-10-20
Ergh.

I get an error to the effect of "PreInit returned NULL For <mouse device>"

relevant xorg.conf section is

```

Section "InputDevice"
    Identifier     "Logitech MX1000"
    Driver         "evdev"
    Option         "Name" "Logitech USB Receiver"
    Option         "HWHEELRelativeAxisButtons" "7 6"
#    Option         "Resolution" "800"
EndSection

```

Quite frustrating. I've been playing with a combination of evdev and mouse all night.

---

### Post by kubi on 2006-10-24
Hi,
 I want to switch 3rd button with my thumb button, eventualy give it the same functionality. How can i do that ?

---

### Post by jrib on 2006-10-24
> **kubi said:**
> Hi,
 I want to switch 3rd button with my thumb button, eventualy give it the same functionality. How can i do that ?

You can use xmodmap,
something like 
```
pointer = 3 2 1
```

would make the first button act like button 3 and the third button act like button 1.  But in your ~/.xmodmap you should have more numbers (12? iirc) and you would just switch whatever corresponds to middle (2) and your thumb button (I can't remember, but use xev to figure it out).

Instead of editing ~/.xmodmap and restarting X to test things you can just do:
[/code]xmodmap -e "pointer = 3 2 1"[/code]
in your terminal.

---

### Post by kubi on 2006-10-25
I did that before evan posting :)
```

"echo ButtonPress 2 ButtonRelease 2 | xmacroplay -d 0 :0.0"
   b:10

```
in xev it looks like it's good, but in firefox b10 deas nothing ;(

---

### Post by doc_holiday on 2006-10-25
> **doc_holiday said:**
> I tried the how to, but X doesn't start any more

Here my xorg.conf

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV20 [GeForce3 Ti 500]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"HM903D/DT"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV20 [GeForce3 Ti 500]"
	Monitor		"HM903D/DT"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice     "Logitech MX1000" "CorePointer"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Can somebody help me?

---

### Post by jrib on 2006-10-25
> **kubi said:**
> I did that before evan posting :)
```

"echo ButtonPress 2 ButtonRelease 2 | xmacroplay -d 0 :0.0"
   b:10

```
in xev it looks like it's good, but in firefox b10 deas nothing ;(

but that's not what I suggested :/

Did you mean you tried using xmodmap but it didn't work?

---

### Post by jrib on 2006-10-25
> **doc_holiday said:**
> Can somebody help me?

Can you show us /var/log/Xorg.0.log as well as the output of:
```
cat /proc/bus/input/devices
```

---

### Post by doc_holiday on 2006-10-25
> **_jason said:**
> Can you show us /var/log/Xorg.0.log as well as the output of:
```
cat /proc/bus/input/devices
```

/var/log/Xorg.0.log
[http://users.skynet.be/fa004801/Xorg.0.log](http://users.skynet.be/fa004801/Xorg.0.log)

cat /proc/bus/input/devices:
I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=40001
B: SND=6

---

### Post by jrib on 2006-10-25
> **doc_holiday said:**
> /var/log/Xorg.0.log
[http://users.skynet.be/fa004801/Xorg.0.log](http://users.skynet.be/fa004801/Xorg.0.log)

cat /proc/bus/input/devices:
I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3
B: EV=40001
B: SND=6

hmm I'm not sure why /proc/bus/input/devices wouldn't include your mouse.  Can you try after using a vanilla xorg.conf (generate one with dpkg-reconfigure xserver-xorg).

---

### Post by kubi on 2006-10-26
here is the result:)
```

xmodmap -e "pointer = 3 2 1"
xmodmap:  commandline:1:  bad number of buttons, must have 20 instead of 3
xmodmap:  1 error encountered, aborting.

```
damn i didn't evan know i have so much :)

---

### Post by jrib on 2006-10-26
> **kubi said:**
> here is the result:)
```

xmodmap -e "pointer = 3 2 1"
xmodmap:  commandline:1:  bad number of buttons, must have 20 instead of 3
xmodmap:  1 error encountered, aborting.

```
damn i didn't evan know i have so much :)

don't just copy the code, read what I said too :)  You have to modify it to the proper number of buttons and switch the right numbers

---

### Post by xiaoxin on 2006-10-27
How to make the wheel button minize active window?
and the middle button on the left alt-tab?

:-k

---

### Post by novakry on 2006-11-01
hi people,

i tried your guide out and followed it to the "T"

after updating my xorg.conf file i got the following message when x tried to restart.

[[IMG]http://show.imagehosting.us/show/1718262/0/nouser_1718/T1_-1_1718262.jpg[/IMG]](http://www.imagehosting.us/index.php?action=show&ident=1718262)

all i can say is i'm pretty new to linux, but if there is any more information you need let me know.

TYIA

NovaKry

---

### Post by jrib on 2006-11-02
> **novakry said:**
> hi people,

i tried your guide out and followed it to the "T"

after updating my xorg.conf file i got the following message when x tried to restart.

[[IMG]http://show.imagehosting.us/show/1718262/0/nouser_1718/T1_-1_1718262.jpg[/IMG]](http://www.imagehosting.us/index.php?action=show&ident=1718262)

all i can say is i'm pretty new to linux, but if there is any more information you need let me know.

TYIA

NovaKry

Hi, can you show us /etc/X11/xorg.conf and /var/log/Xorg.0.log ?

Also, were you able to restore the backup so you can get back to X?

---

### Post by novakry on 2006-11-02
> **_jason said:**
> Hi, can you show us /etc/X11/xorg.conf and /var/log/Xorg.0.log ?

Xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Aug  1 21:11:12 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Logitech MX1000" "CorePointer"
#   InputDevice    "stylus" "SendCoreEvents"
#   InputDevice    "cursor" "SendCoreEvents"
#   InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

#Section "InputDevice"

                                                      # /dev/#input/event
                                                      # for #USB
#    Identifier     "stylus"
#    Driver         "wacom"
#   Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"               # #Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /#dev/input/event
#                                                      # for #USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change #to 
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # #Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /#dev/input/event
#                                                      # for #USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change #to 
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # #Tablet PC ONLY
#EndSection

Section "Monitor"
    Identifier     "L1715S"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
    Option         "hwcursor" "on"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "L1715S"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

Xorg.0.log
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux main 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  2 08:40:31 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Philips 170S"
(**) |   |-->Device "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 0000,0000 rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 10de,0c11 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 10de,0c11 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 10de,0c11 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 10de,0c11 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 10de,0c11 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 10de,0c11 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 10de,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,00f1 card 107d,2011 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:08:0: chip 1102,0002 card 1102,100a rev 0a class 04,01,00 hdr 80
(II) PCI: 02:08:1: chip 1102,7002 card 1102,0020 rev 0a class 09,80,00 hdr 80
(II) PCI: 02:09:0: chip 11ab,1faa card 1385,6b00 rev 03 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe6ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe7000000 - 0xe7ffffff (0x1000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] rev 162, Mem @ 0xe4000000/24, 0xd0000000/28, 0xe5000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe7010000 - 0xe701ffff (0x10000) MX[B]
	[1] -1	0	0xe7000000 - 0xe700ffff (0x10000) MX[B]
	[2] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[3] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[4] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[5] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[11] -1	0	0x0000d100 - 0x0000d11f (0x20) IX[B]
	[12] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[13] -1	0	0x0000e200 - 0x0000e207 (0x8) IX[B]
	[14] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[15] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[16] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe7010000 - 0xe701ffff (0x10000) MX[B]
	[1] -1	0	0xe7000000 - 0xe700ffff (0x10000) MX[B]
	[2] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[3] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[4] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[5] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[11] -1	0	0x0000d100 - 0x0000d11f (0x20) IX[B]
	[12] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[13] -1	0	0x0000e200 - 0x0000e207 (0x8) IX[B]
	[14] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[15] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[16] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe7010000 - 0xe701ffff (0x10000) MX[B]
	[5] -1	0	0xe7000000 - 0xe700ffff (0x10000) MX[B]
	[6] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[7] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[8] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[9] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[17] -1	0	0x0000d100 - 0x0000d11f (0x20) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000e200 - 0x0000e207 (0x8) IX[B]
	[20] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[21] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[22] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8774
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8774
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA X Driver  1.0-8774  Tue Aug  1 20:56:50 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe7010000 - 0xe701ffff (0x10000) MX[B]
	[5] -1	0	0xe7000000 - 0xe700ffff (0x10000) MX[B]
	[6] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[7] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[8] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[9] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[17] -1	0	0x0000d100 - 0x0000d11f (0x20) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000e200 - 0x0000e207 (0x8) IX[B]
	[20] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[21] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[22] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe7010000 - 0xe701ffff (0x10000) MX[B]
	[5] -1	0	0xe7000000 - 0xe700ffff (0x10000) MX[B]
	[6] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[7] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[8] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[9] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[20] -1	0	0x0000d100 - 0x0000d11f (0x20) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x0000e200 - 0x0000e207 (0x8) IX[B]
	[23] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[24] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[25] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 GT at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.46.68
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 GT at PCI:1:0:0:
(--) NVIDIA(0):     Philips 170S (CRT-0)
(--) NVIDIA(0): Philips 170S (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe7010000 - 0xe701ffff (0x10000) MX[B]
	[8] -1	0	0xe7000000 - 0xe700ffff (0x10000) MX[B]
	[9] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[10] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[11] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[12] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xe5000000 - 0xe5ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d200 - 0x0000d207 (0x8) IX[B]
	[23] -1	0	0x0000d100 - 0x0000d11f (0x20) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x0000e200 - 0x0000e207 (0x8) IX[B]
	[26] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[27] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[28] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+gb" };
    xkb_geometry             { include "pc(pc105)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

> **_jason said:**
> Also, were you able to restore the backup so you can get back to X?

yep just a simply case of using cp with the backup i made of xorg.conf and reloading x from the command line.

hope that helps you guys, to help me.

Regards,

NovaKry

---

### Post by machia on 2006-11-07
This post is a reminder to me (just battled an hour to get my MX1000 to work again; i installed edgy again and forgot to take backup :/) and hopefully someone finds it usefully.. 


My input on 
```
cat /proc/bus/input/devices
```

```
I: Bus=0003 Vendor=046d Product=c50e Version=2510
N: Name="Logitech USB RECEIVER"
P: Phys=usb-0000:00:10.1-1/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0 
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
```

My xorg.conf:
```
Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Dev Name" "Logitech USB Receiver"
        Option          "Dev Phys" "usb-*/input0"
        Option          "Device" "/dev/input/event1"
        Option          "Buttons" "10"
        Option          "ZAxisMapping" "4 5 7 6"
EndSection

```

Plus, I have the .xbindscr-thing in my ~ so that the side-buttons work in mozilla etc. 

The weird thing was that I'm sure that I tried that xorg-config earlier and wasn't able to startX. Maybe I'm too confused or something :???: Well the mouse works :D

---

### Post by Freddy on 2006-11-18
Hi I tried this HOWTO and X didn't crash :-). To bad nothing worked though. I made all steps in the wiki but none of the x-tra buttons work at all in Kubuntu Edgy. Xbindkeys made my 2 side buttons work in both konqueror and firefox though.

These are the sectons I altered in xorg.conf
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Logitech MX1000" "CorePointer"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection
```
and
```
Section "InputDevice"
    Identifier      "Logitech MX1000"
    Driver          "evdev"
    Option          "Name"          "Logitech USB Receiver"
    Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection
```

Hoping someone can help.   /// Freddan

---

### Post by jrib on 2006-11-19
> **Freddy said:**
> Hi I tried this HOWTO and X didn't crash :-). To bad nothing worked though. I made all steps in the wiki but none of the x-tra buttons work at all in Kubuntu Edgy. Xbindkeys made my 2 side buttons work in both konqueror and firefox though.

[snip]

Hoping someone can help.   /// Freddan

Hi, can you run 'xev' in a terminal and see if clicking on the window it creates, makes all the buttons show up?  (killall xbindkeys  beforehand might help)

---

### Post by Freddy on 2006-11-19
> Hi, can you run 'xev' in a terminal and see if clicking on the window it creates, makes all the buttons show up? (killall xbindkeys beforehand might help)
Yeah, all of my buttons rendered some kind of action of "xev". Nothing still works though.

Another question to, how to make "xbindkeys" start with KDE, now I need to start up it every time I log in.

Thx for any help I can get.   / Freddan

---

### Post by jrib on 2006-11-27
> **Freddy said:**
> Yeah, all of my buttons rendered some kind of action of "xev". Nothing still works though.

If you hold down "scroll down" button, does it emit a button (maybe 12) and then start repeating another button many times (maybe 5; should be the same as when you scroll your wheel down).

If it doesn't, search this thread for instructions on compiling the program called "lmctl" and run ```
lmctl -i
```.

> **Freddy said:**
> 
Another question to, how to make "xbindkeys" start with KDE, now I need to start up it every time I log in.


I don't use kde, but it seems you have to place a symlink in ~/.kde/Autostart .  
```

mkdir -p ~/.kde/Autostart; ln -s $(which xbindkeys) ~/.kde/Autostart

```

should do it

---

### Post by Sonic Reducer on 2006-12-03
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
        Load    "dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice     "Logitech MX1000" "CorePointer"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

just to make things easier i am posting my edited xorg.conf file so any errors can be fixed. i had a spot of trouble last time i tried this (basically i lost the GUI, and had to command line it until somone came to my rescue)

i'm restarting X now. wish me luck!

---

### Post by reticencias on 2006-12-03
OK!!!!!!!!!!!! this worked LIKE A CHARM!!!! you are the man!!!! great "howto", easy to follow trough and working :)

the only button that doesn't work is that "menu" button (the one between the forward and backword buttons) but who needs it :) :) :)

oh, btw, I'm using the MX1000, of course :)

---

### Post by jrib on 2006-12-04
> **reticencias said:**
> OK!!!!!!!!!!!! this worked LIKE A CHARM!!!! you are the man!!!! great "howto", easy to follow trough and working :)

the only button that doesn't work is that "menu" button (the one between the forward and backword buttons) but who needs it :) :) :)

oh, btw, I'm using the MX1000, of course :)

Glad it works for you.  I haven't found a good use for that third side button but you can setup a bind for it with xbindkeys (it should be "b:10").

---

### Post by Sonic Reducer on 2006-12-05
ok, i've tried this twice and it hasn't worked either time. i'm using dapper 64-Bit.

heres the output, could someone show me what i'm doing wrong?

**Terminal:** sudo apt-get install xvkbd xbindkeys xmacro
```
ryan@ryan-desktop:~$ sudo apt-get install xvkbd xbindkeys xmacro
Password:
Reading package lists... Done
Building dependency tree... Done
xvkbd is already the newest version.
xbindkeys is already the newest version.
xmacro is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

**Terminal:** sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```
ryan@ryan-desktop:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
ryan@ryan-desktop:~$ gksudo gedit /etc/X11/xorg.conf

(gedit:6132): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

**Terminal:** cat /proc/bus/input/devices
```
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=402000000 3802078f840d001 f2ffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c041 Version=4600
N: Name="Logitech USB Gaming Mouse"
P: Phys=usb-0000:00:0b.0-4/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=ffff0000 0 0 0 0
B: REL=143

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2
B: EV=40001
B: SND=6
```

and here is the unaltered contents of my xorg.conf file:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
        Load    "dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

could someone edit the xorg.conf file for me? i keep making errors that let me experience what linux without a GUI is like

---

### Post by lazyd2 on 2006-12-15
Excellent "How To"!

Thank you!

---

### Post by gurgle on 2006-12-15
I know I am going to sound incredibly lazy, but a GUI interface to modify the buttons would be awesome :)

---

### Post by Daxie on 2007-01-06
Thank you for the great HOWTO works like a charm!! ;) 

Oh and i use that "menu" button to open new Tab windows in Firefox...

Here's my *.xbindsrc* file:

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[t]""
  b:10
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14
```

---

### Post by unabatedshagie on 2007-01-13
Excellent tutorial, I have managed to get everything working :)

I had an idea for the unused button, I would like to make it activate the rotate cube feature in beryl.

How would I go about doing this?

---

### Post by weichafe on 2007-01-31
HI.

I follow this tutorial in ubuntu 6.10 but, i can't configure the buttons. If I scrool down or scroll up with the wheel it moves the "horizontal" scrool, and If I move the wheel to left or right it moves the vertical scrool....

Any Idea?

Here is my Xorg.conf 

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice     "Logitech MX1000" "CorePointer"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection
..
...
.
BLABLABLABAL
...
...

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"    "Logitech USB RECEIVER"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

```

And here is the xbindkeysrc

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14
```

I try to determine what button I press with xev, but if I change the xbindkeysrc changue the buttons everytime...so, in conclusion, I'm confused...

---

### Post by jrib on 2007-01-31
> **weichafe said:**
> HI.

I follow this tutorial in ubuntu 6.10 but, i can't configure the buttons. If I scrool down or scroll up with the wheel it moves the "horizontal" scrool, and If I move the wheel to left or right it moves the vertical scrool....

Any Idea?

Here is my Xorg.conf 

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice     "Logitech MX1000" "CorePointer"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection
..
...
.
BLABLABLABAL
...
...

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"    "Logitech USB RECEIVER"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

```

And here is the xbindkeysrc

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14
```

I try to determine what button I press with xev, but if I change the xbindkeysrc changue the buttons everytime...so, in conclusion, I'm confused...

did you check for an xmodmap?  (usually it ends up in ~/.xmodmaprc).  If you don't have one, then you could use xmodmap to fix your issue.  Post here again if you aren't sure how xmodmap works.

---

### Post by weichafe on 2007-01-31
> **_jason said:**
> did you check for an xmodmap?  (usually it ends up in ~/.xmodmaprc).  If you don't have one, then you could use xmodmap to fix your issue.  Post here again if you aren't sure how xmodmap works.

There is no file for xmodmap... so with xmodmap I could fixit? how, can you guide me?:D

---

### Post by jrib on 2007-01-31
> **weichafe said:**
> There is no file for xmodmap... so with xmodmap I could fixit? how, can you guide me?:D

Sure, first thing, kill xbindkeys ```
 killall xbindkeys 
```.  Then run ```
xev
``` and figure out the numbers for the buttons that are switched.

It's easiest to explain how xmodmap works with an example.  Here is how i switch button 2 with button 12:

```
pointer = 1 12 3 4 5 6 7 8 9 10 11 2 13 14 15 16 17 18 19 20
```

I keep that in my ~/.xmodmaprc.  But to test, you can send the expression straight into the xmodmap command like so:

```
xmodmap -e "pointer = 1 12 3 4 5 6 7 8 9 10 11 2 13 14 15 16 17 18 19 20"
```

Does that make sense?

[edit]  You could also play with the "7 6" part in your xorg.conf if you are curious...

---

### Post by weichafe on 2007-02-01
I try with xmodmap but it doesn't works...

Also I play with "7 6" in the xorg.con and the result was worse than before. 

The problem is with the horizontal and vertical scroll that are changed. Vertical scroll move horizontal bar, and viceversa... Tonight i will try new configurations... i must to work now.

---

### Post by jrib on 2007-02-01
> **weichafe said:**
> I try with xmodmap but it doesn't works...

Also I play with "7 6" in the xorg.con and the result was worse than before. 

The problem is with the horizontal and vertical scroll that are changed. Vertical scroll move horizontal bar, and viceversa... Tonight i will try new configurations... i must to work now.

What are the numbers of the buttons that aren't working?  And what configuration did you try?

---

### Post by Migs on 2007-02-04
Yesterday I followed this guide and was really happy to see that mouse worked like it should. This morning I booted my laptop without the mx1000 connected and X did not start. After 3 cycles it came with an blueish error screen that X server could not start. Only message i could find was on the terminal: ```
hostname miguel@vaio-laptop: tty1 
```

Does anybody have a clue what is happening right now? When i reconnect the mouse and reboot, X starts again.

---

### Post by jrib on 2007-02-04
> **Migs said:**
> Yesterday I followed this guide and was really happy to see that mouse worked like it should. This morning I booted my laptop without the mx1000 connected and X did not start. After 3 cycles it came with an blueish error screen that X server could not start. Only message i could find was on the terminal: ```
hostname miguel@vaio-laptop: tty1 
```

Does anybody have a clue what is happening right now? When i reconnect the mouse and reboot, X starts again.

X will fail to start if it can't get a pointer device.

We should be able to make it so that it falls back to your touchpad when it can't find the mouse.  If your old xorg.conf worked in this way, then try posting the old one and the new one so we can compare it.

---

### Post by Migs on 2007-02-04
> **_jason said:**
> X will fail to start if it can't get a pointer device.

We should be able to make it so that it falls back to your touchpad when it can't find the mouse.  If your old xorg.conf worked in this way, then try posting the old one and the new one so we can compare it.

Okay here are mine xorg.conf files: (I've made txt files so that this topic stays readable)

---

### Post by Migs on 2007-02-05
Okay I've solved my problem, it had something to do with "AlwaysCore" and "CorePointer" in the serverlayout section. 

For reference here my fully working xorg.conf:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Logitech MX1000"	"AlwaysCore"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"	"CorePointer"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "lv3:ralt_switch"
    Option         "XkbVariant" "intl"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
   	Option		"LeftEdge" "130"
   	Option		"RightEdge" "840"
   	Option		"TopEdge" "130"
   	Option		"BottomEdge" "640"
   	Option		"FingerLow" "7"
   	Option		"FingerHigh" "8"
   	Option		"MaxTapTime" "180"
   	Option		"MaxTapMove" "110"
   	Option		"EmulateMidButtonTime" "75"
   	Option		"VertScrollDelta" "20"
   	Option		"HorizScrollDelta" "20"
   	Option		"MinSpeed" "0.60"
   	Option		"MaxSpeed" "1.10"
   	Option		"AccelFactor" "0.030"
   	Option		"EdgeMotionMinSpeed" "200"
   	Option		"EdgeMotionMaxSpeed" "200"
   	Option		"UpDownScrolling" "1"
   	Option		"CircularScrolling" "1"
   	Option		"CircScrollDelta" "0.1"
   	Option		"CircScrollTrigger" "2"
   	Option		"SHMConfig" "on"
 	Option		"Emulate3Buttons" "on"
 EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

```

---

### Post by jrib on 2007-02-05
Glad to hear you sorted it out Migs.  If you have the time, it would be great if you could add what you did to the wiki :)

---

### Post by bankie on 2007-02-05
Thanks for the guide. With it I've managed to get the buttons on a MX400 mouse working (It's basically a wired MX1000 without the task-switcher button.

I just have one question. Is there any way to switch tabs in firefox by tilting the wheel?

---

### Post by grantjohnston on 2007-02-14
Alright, I'm about to ram my head through a wall. I had it working less than 20 minutes ago.. I go to restart, and the keys reset themselves to the scroll wheel going back and forward in the browser history. I followed all the steps for Breezy/Edgy, and I just can't honestly think of anything else to do. Running Xubuntu Edgy. If anyone has any insight or needs any information, please don't fret to ask. I'm about to put a hatchet through the side of my machine.



Cheers


Grant

---

### Post by dremon on 2007-02-15
Hello,

I have MX5000 bluetooth desktop (MX1000 mouse + keyboard), connected to the Acer laptop (which also has synaptic touchpad). The OS is Edgy. There are some problems I would really like to solve with your help.

In the /proc/bus/input/devices, there are 2 "Logitech Logitech BT Mini-Receiver" names listed, one for the mouse (event4) and another for the keyboard (event3).
I've configured the mouse in xorg.conf via the {"Device" "/dev/input/event4"} parameter and it works, but....
Somehow, the keyboard started behaving very strangely. First of all, the extra buttons like "Email" and sliders like "Volume" do not work anymore. They were working perfectly before I added the evdev mouse device. Now, instead of doing any actions, these buttons cause X server to crash.
This crash does not occur however, if I disable the synaptic touchpad in the ServerLayout section, but the above mentioned buttons still do not work.
And another thing, the mouse stops working after suspending/resuming the laptop. I guess it is also a problem of evdev driver.

Thanks for any help.

---

### Post by grantjohnston on 2007-02-18
ttt. Anyone? It's rather irritating not having my scroll wheel anymore... :(

---

### Post by berserker on 2007-02-18
> **grantjohnston said:**
> ttt. Anyone? It's rather irritating not having my scroll wheel anymore... :(

Is xbindkeys running?

Here's my ~/.xbindkeysrc:

```
"xvkbd -xsendevent -text "\[Control_L]\[w]""
  b:8
"xvkbd -xsendevent -text "\[Control_L]\[t]""
  b:9
"xvkbd -xsendevent -text "\[Control_L]\[r]""
  b:10
"xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:13
"xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:14
```

---

### Post by Bourlotieris on 2007-02-19
> **_jason said:**
> See if you can figure out how to write a udev rule to give the mouse a consistent event#.  Maybe this can help [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html) .  I haven't had a chance to do this myself, but I'd be glad to hear how it goes.

I used to use this as /etc/udev/rules.d/10-local.rules:
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event9"

But as you can see that is only matching the name, which is meaningles.

If you can get that to work, then just use the event# instead of the name in your xorg.conf

After all this time I decided to give it a try once more. I wrote a udev rule which I placed in:
/etc/udev/rules.d/60-symlinks.rules
The rule was:
BUS=="usb", SYSFS{product}=="Logitech BT Mini-Receiver", SYSFS{idProduct}=="c70c", SYMLINK+="input/mx1000"

So a symlink was created in /dev/input. What is the next step? What should I enter in the xorg.conf instead of the name? I tried:
Option          "Name"          "input/mx1000"
but x couldn't start. Should I do something else?

---

### Post by grantjohnston on 2007-02-19
> **berserker said:**
> Is xbindkeys running?

Here's my ~/.xbindkeysrc:

```
"xvkbd -xsendevent -text "\[Control_L]\[w]""
  b:8
"xvkbd -xsendevent -text "\[Control_L]\[t]""
  b:9
"xvkbd -xsendevent -text "\[Control_L]\[r]""
  b:10
"xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:13
"xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:14
```

Yeah, xbindkeys is running, that's not what I had. I had..




```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14

```


Either way, I tried both, and neither worked.

---

### Post by jrib on 2007-02-19
> **Bourlotieris said:**
> After all this time I decided to give it a try once more. I wrote a udev rule which I placed in:
/etc/udev/rules.d/60-symlinks.rules
The rule was:
BUS=="usb", SYSFS{product}=="Logitech BT Mini-Receiver", SYSFS{idProduct}=="c70c", SYMLINK+="input/mx1000"

So a symlink was created in /dev/input. What is the next step? What should I enter in the xorg.conf instead of the name? I tried:
Option          "Name"          "input/mx1000"
but x couldn't start. Should I do something else?

I think it should be  Option "Device", not  Option "Name".  Also, I used to use "/dev/input/mx1000" but try your way too and see if it works.

---

### Post by jrib on 2007-02-19
> **bankie said:**
> Thanks for the guide. With it I've managed to get the buttons on a MX400 mouse working (It's basically a wired MX1000 without the task-switcher button.

I just have one question. Is there any way to switch tabs in firefox by tilting the wheel?

Sure, just use xbindkeys to catch button #(whatever it is for side scroll, use 'xev' to find out) and play the necessary keyboard shortcut like in the examples for "back" and "forward".

---

### Post by jrib on 2007-02-19
> **grantjohnston said:**
> Alright, I'm about to ram my head through a wall. I had it working less than 20 minutes ago.. I go to restart, and the keys reset themselves to the scroll wheel going back and forward in the browser history. I followed all the steps for Breezy/Edgy, and I just can't honestly think of anything else to do. Running Xubuntu Edgy. If anyone has any insight or needs any information, please don't fret to ask. I'm about to put a hatchet through the side of my machine.



Cheers


Grant

The steps are a little different for breezy vs. edgy.  Which one are you using?

kill xbindkeys and tell us what button numbers show up with the scroll wheel (use the 'xev' program for this).

Do you have an xmodmap pointer rule somewhere?  Maybe ~/.xmodmap?

---

### Post by grantjohnston on 2007-02-19
Okay, I just found an old .xbindkeysrc (not sure from which distro, I've had dapper and edgy on this desktop) and it says 



```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9

"~/.click/click 4"
  m:0x0 + b:9
"~/.click/click 5"
  m:0x0 + b:10

```


When I scroll down on the wheel, it scrolls up on the page. However, when I scroll up, it still goes back in the browser history. Anyone?


Cheers


Grant

---

### Post by grantjohnston on 2007-02-19
> **_jason said:**
> The steps are a little different for breezy vs. edgy.  Which one are you using?

kill xbindkeys and tell us what button numbers show up with the scroll wheel (use the 'xev' program for this).

Do you have an xmodmap pointer rule somewhere?  Maybe ~/.xmodmap?

edgy


scrolling up is 8


scrolling down is 9


not finding anything in ~/.xmodmap, however, did find


```
/var/lib/dpkg/info/xmodmap.list
/var/lib/dpkg/info/xmodmap.md5sums
/etc/X11/Xsession.d/80ubuntu-xmodmap
/usr/bin/xmodmap
/usr/share/apps/kxkb/ubuntu.xmodmap
/usr/share/doc/imwheel/examples/61imwheel_load-xmodmap
/usr/share/doc/xmodmap
/usr/share/doc/xmodmap/changelog.Debian.gz
/usr/share/doc/xmodmap/copyright
/usr/share/man/man1/xmodmap.1x.gz
/usr/share/vim/vim70/syntax/xmodmap.vim
/usr/share/vim/vim70/ftplugin/xmodmap.vim

```


Maybe there?? Thanks :)

---

### Post by jrib on 2007-02-19
> **grantjohnston said:**
> edgy


scrolling up is 8


scrolling down is 9


not finding anything in ~/.xmodmap, however, did find


```
/var/lib/dpkg/info/xmodmap.list
/var/lib/dpkg/info/xmodmap.md5sums
/etc/X11/Xsession.d/80ubuntu-xmodmap
/usr/bin/xmodmap
/usr/share/apps/kxkb/ubuntu.xmodmap
/usr/share/doc/imwheel/examples/61imwheel_load-xmodmap
/usr/share/doc/xmodmap
/usr/share/doc/xmodmap/changelog.Debian.gz
/usr/share/doc/xmodmap/copyright
/usr/share/man/man1/xmodmap.1x.gz
/usr/share/vim/vim70/syntax/xmodmap.vim
/usr/share/vim/vim70/ftplugin/xmodmap.vim

```


Maybe there?? Thanks :)

k, well my mouse has 4 for up and 5 for down.  What does this command return: ```
xmodmap -pp
```

What does your xorg.conf look like?

---

### Post by Bourlotieris on 2007-02-19
> **_jason said:**
> I think it should be  Option "Device", not  Option "Name".  Also, I used to use "/dev/input/mx1000" but try your way too and see if it works.

Tried that also (Option "Device" "/dev/input/mx1000") but X refuses to start. Any other ideas?

---

### Post by grantjohnston on 2007-02-19
> **_jason said:**
> k, well my mouse has 4 for up and 5 for down.  What does this command return: ```
xmodmap -pp
```

What does your xorg.conf look like?




xmodmap -pp returns

```

There are 20 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              8
        5              9
        6             10
        7             11
        8             12
        9              6
       10              7
       11              4
       12              5
       13             13
       14             14
       15             15
       16             16
       17             17
       18             18
       19             19
       20             20

```



xorg.conf looks like

```

Section "InputDevice"
    Identifier     "Logitech MX1000"
    Driver         "evdev"
    Option         "Name"       "Logitech USB RECEIVER"
    Option         "HWHEELRelativeAxisButtons" "7 6"
EndSection

```


in the mouse section, obviously. Any help?


Thanks again


Grant.

---

### Post by jrib on 2007-02-19
> **grantjohnston said:**
> xmodmap -pp returns
[snip]
Grant.

yep, you definitely have an xmodmap pointer rule somewhere.  I think I gave you the wrong location before.  How about: ~/.xmodmaprc?

---

### Post by jrib on 2007-02-19
> **Bourlotieris said:**
> Tried that also (Option "Device" "/dev/input/mx1000") but X refuses to start. Any other ideas?

paste the relevant xorg.conf section and I'll try it here.  That way it'll be easier to troubleshoot

---

### Post by Bourlotieris on 2007-02-20
> **_jason said:**
> paste the relevant xorg.conf section and I'll try it here.  That way it'll be easier to troubleshoot

```
Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Device"          "/dev/input/mx1000"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

...
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
        InputDevice     "Logitech MX1000" "CorePointer"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection
```

That is my xorg.conf after I make the changes and fails to start. The original one is:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5 6 7"
#	Option		"Emulate3Buttons"	"true"
	Option		"Resolution"		"2400"
EndSection

...


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection
```

I can't really understand what was the point of writing a udev rule. Couldn't I just use the 
```
	Option		"Device"		"/dev/input/mice"
```
of the original xorg.conf? Feels like I am missing something here.

---

### Post by grantjohnston on 2007-02-20
> **_jason said:**
> yep, you definitely have an xmodmap pointer rule somewhere.  I think I gave you the wrong location before.  How about: ~/.xmodmaprc?

Nope.. :( :confused: :confused:

---

### Post by jrib on 2007-02-20
> **grantjohnston said:**
> Nope.. :( :confused: :confused:

well here is what I would do (in order until something turns up though the last one is a bit extreme...):

1. find ~ -iname '*xmodmap*'
2. grep xmodmap ~/.*
3. grep -R xmodmap ~
4. grep -R xmodmap /


I'm hoping 2 will find something...
3 and 4 may take a bit longer, if you do decide to try those.

If we can't find anything, then we'll have to see if there is another explanation for your output from 'xmodmap -pp'

---

### Post by grantjohnston on 2007-02-20
> **_jason said:**
> well here is what I would do (in order until something turns up though the last one is a bit extreme...):

1. find ~ -iname '*xmodmap*'
2. grep xmodmap ~/.*
3. grep -R xmodmap ~
4. grep -R xmodmap /


I'm hoping 2 will find something...
3 and 4 may take a bit longer, if you do decide to try those.

If we can't find anything, then we'll have to see if there is another explanation for your output from 'xmodmap -pp'



Looks like it found something



```
grant@threeve:~$ grep xmodmap ~/.*
/home/grant/.bash_history:locate xmodmap
/home/grant/.bash_history:xmodmap -pp
grep: /home/grant/.nano_history: Permission denied
grant@threeve:~$ sudo grep xmodmap ~/.*
Password:
/home/grant/.bash_history:locate xmodmap
/home/grant/.bash_history:xmodmap -pp
grant@threeve:~$ 


```

That help?

---

### Post by jrib on 2007-02-20
> **grantjohnston said:**
> Looks like it found something



```
grant@threeve:~$ grep xmodmap ~/.*
/home/grant/.bash_history:locate xmodmap
/home/grant/.bash_history:xmodmap -pp
grep: /home/grant/.nano_history: Permission denied
grant@threeve:~$ sudo grep xmodmap ~/.*
Password:
/home/grant/.bash_history:locate xmodmap
/home/grant/.bash_history:xmodmap -pp
grant@threeve:~$ 


```

That help?

nope that's just the history from the commands I gave you :/

While we troubleshoot this, here's how to reset the pointer so you can use your system.

```
xmodmap -e 'pointer = default'
```

After that, ```
xmodmap -pp
``` should print out matching columns.

In addition to suggestions 3 and 4 above, a hackish way to find out where the xmodmap rule is could be to place an xmodmap script in /usr/local/bin that contains,
```

!#/bin/sh

echo $(pwd) >> /tmp/DEBUGGING_XMODMAP

```

or something similar...  This should work as long as xmodmap isn't called with its absolute path.  So if this fails you could proceed to actually temporarily replace /usr/bin/xmodmap.  If you understand what that suggestion is doing, great.  If not, I'd rather you ask here for more details before trying it.  This way we make sure we don't mess something up and leave you with an unusable system that you can't fix.

---

### Post by grantjohnston on 2007-02-20
> **_jason said:**
> nope that's just the history from the commands I gave you :/

While we troubleshoot this, here's how to reset the pointer so you can use your system.

```
xmodmap -e 'pointer = default'
```

After that, ```
xmodmap -pp
``` should print out matching columns.

In addition to suggestions 3 and 4 above, a hackish way to find out where the xmodmap rule is could be to place an xmodmap script in /usr/local/bin that contains,
```

!#/bin/sh

echo $(pwd) >> /tmp/DEBUGGING_XMODMAP

```

or something similar...  This should work as long as xmodmap isn't called with its absolute path.  So if this fails you could proceed to actually temporarily replace /usr/bin/xmodmap.  If you understand what that suggestion is doing, great.  If not, I'd rather you ask here for more details before trying it.  This way we make sure we don't mess something up and leave you with an unusable system that you can't fix.




The system is usable, as I'm posting from it right now, it's just my scroll wheel and the navigation buttons on the mouse don't work, which is, well, rather irritating. I never tried 3 and 4, should I try that? I somewhat understand what you're saying, but not fully. So, I guess I'm asking if I should try 3 and 4 first, or go ahead and try the other?


THanks


Grant

---

### Post by jrib on 2007-02-20
> **grantjohnston said:**
> The system is usable, as I'm posting from it right now, it's just my scroll wheel and the navigation buttons on the mouse don't work, which is, well, rather irritating. I never tried 3 and 4, should I try that? I somewhat understand what you're saying, but not fully. So, I guess I'm asking if I should try 3 and 4 first, or go ahead and try the other?


THanks


Grant

k, "more usable" then? :P 

I would try my last suggestion first since that would be quicker (but would require you to reboot).  Let me know which part below isn't clear:

1. xmodmap is getting called /somewhere/.  We need to find out where.
2. if we create /usr/local/bin/xmodmap, when 'xmodmap' is executed, it will execute /usr/local/bin/xmodmap instead of /usr/bin/xmodmap.
3. the stuff inside the new xmodmap we created will hopefully give us the location where it is being called from, or at least the directory.  Now that I think about it, this might not even work... but worth a try I guess
4. make sure you delete /usr/local/bin/xmodmap afterwards

---

### Post by grantjohnston on 2007-02-20
> **_jason said:**
> k, "more usable" then? :P 

I would try my last suggestion first since that would be quicker (but would require you to reboot).  Let me know which part below isn't clear:

1. xmodmap is getting called /somewhere/.  We need to find out where.
2. if we create /usr/local/bin/xmodmap, when 'xmodmap' is executed, it will execute /usr/local/bin/xmodmap instead of /usr/bin/xmodmap.
3. the stuff inside the new xmodmap we created will hopefully give us the location where it is being called from, or at least the directory.  Now that I think about it, this might not even work... but worth a try I guess
4. make sure you delete /usr/local/bin/xmodmap afterwards

Alright, neither of the previous ones worked. What you just stated there is about what all I understood. Just not all of the commands I would need to execute, haha. 


Thanks again!


Grant

---

### Post by jrib on 2007-02-21
> **grantjohnston said:**
> Alright, neither of the previous ones worked. What you just stated there is about what all I understood. Just not all of the commands I would need to execute, haha. 


Thanks again!


Grant

k, are you saying you tried all of 1,2,3,4 and had no results?

The commands to try my latest suggestion (replacing xmodmap), would be:

```
gksudo gedit /usr/local/bin/xmodmap
```

Then put in the script I said.  Then reboot and take a look at the file in /tmp

Afterwards, delete it with: ```
sudo rm /usr/local/bin/xmodmap
```

---

### Post by grantjohnston on 2007-02-22
> **_jason said:**
> k, are you saying you tried all of 1,2,3,4 and had no results?

The commands to try my latest suggestion (replacing xmodmap), would be:

```
gksudo gedit /usr/local/bin/xmodmap
```

Then put in the script I said.  Then reboot and take a look at the file in /tmp

Afterwards, delete it with: ```
sudo rm /usr/local/bin/xmodmap
```

Hmm, in trying to do that, it fails and says no file or directory... I'm not all here right now, have a terrible cold and all the medicine I'm taking isn't helping.. Am I just completely overlooking something? Thanks and sorry if it's a stupid question, haha.


Grant

---

### Post by Axio on 2007-02-25
Hello,

I am on feisty and I have an MX1000.
I tried to configure it but xorg crash if I enter :     Driver         "evdev"

Is there a solution ?

---

### Post by Vivix729 on 2007-02-25
Ok, I need quick help.  I have 2 devices named "Logitech USB Receiver,"  one for mouse and a different one for my keyboard.  How would I handle that situation?  I followed the guide, but X doesn't start in that situation.

---

### Post by grantjohnston on 2007-02-28
bump. Still not working :(.. Anyone?

---

### Post by jrib on 2007-02-28
> **grantjohnston said:**
> bump. Still not working :(.. Anyone?

See if it works with a fresh new user

---

### Post by jrib on 2007-02-28
> **Axio said:**
> Hello,

I am on feisty and I have an MX1000.
I tried to configure it but xorg crash if I enter :     Driver         "evdev"

Is there a solution ?

Is xserver-xorg-input-evdev installed?


Bourlotierus, I haven't forgotten that I promised to try your xorg.conf, I'll get around to it soon.

---

### Post by Bourlotieris on 2007-03-01
> **_jason said:**
> Is xserver-xorg-input-evdev installed?


Bourlotierus, I haven't forgotten that I promised to try your xorg.conf, I'll get around to it soon.

Ok pal, whenever you have extra time, this can wait. If only you could explain to me the point of writing a udev rule, as I asked in my previous post.

---

### Post by Axio on 2007-03-01
> **_jason said:**
> Is xserver-xorg-input-evdev installed?


Bourlotierus, I haven't forgotten that I promised to try your xorg.conf, I'll get around to it soon.

Yes it is installed, and I try to reinstall it. 
But it change nothing :(

---

### Post by jrib on 2007-03-01
> **Bourlotieris said:**
> Ok pal, whenever you have extra time, this can wait. If only you could explain to me the point of writing a udev rule, as I asked in my previous post.

Well, the keyboard and mouse both seem to have the same "name" so we can't match on that (in the sense that we tell evdev to take care of the device with that name) since we only want to work with the mouse.  I don't have one of these keyboard/mouse combos so I can't really say that this is how it works, but I would think that there must be a way for you to write a udev rule that matches only the mouse and creates a symlink (like yours does).  That way you can tell evdev exactly what device you want it to take care of.  It won't try to handle the keyboard instead of the mouse.

I hope that makes sense.

> **Axio said:**
> Yes it is installed, and I try to reinstall it. 
But it change nothing :(
Hmm, I'm on feisty and it seemed to just work (I only set it up now).  Here are the relevant sections in my xorg.conf:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Logitech MX1000" "SendCoreEvents"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

```
...
```

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

```

I am not up to date.  The packages on here are about a week old.  I'll pull in the X upgrades sometime today probably and let you know if it starts failing...

Can you pastebin your xorg.conf as well as /var/log/Xorg.0.log after X refuses to start?

---

### Post by Axio on 2007-03-02
Thanks a lot Jason it is working !!!

Edit : not perfectly :(:(:(

My keyboard ( mx3100 ) do strange things...

These buttons are not working :( 
For exemple, the up button do a screenshot

[[img]http://www.hiboox.com/vignettes/0907/edd6ce74.jpg[/img]](http://www.hiboox.com/image.php?img=edd6ce74.jpg)

Edit 2 : I solved the problem : I put my keyboard and my mouse on PS2

---

### Post by Bourlotieris on 2007-03-02
> Well, the keyboard and mouse both seem to have the same "name" so we can't match on that (in the sense that we tell evdev to take care of the device with that name) since we only want to work with the mouse.  I don't have one of these keyboard/mouse combos so I can't really say that this is how it works, but I would think that there must be a way for you to write a udev rule that matches only the mouse and creates a symlink (like yours does).  That way you can tell evdev exactly what device you want it to take care of.  It won't try to handle the keyboard instead of the mouse.

I hope that makes sense.

It does. What I don't get is why I can't use "/dev/input/mice" of my original xorg.conf and have to write a udev rule that creates a new symlink for "/dev/input/mx1000". Couldn't I just use the original one?

---

### Post by Big_Rog on 2007-03-03
Well, after pulling my hair out all week, i found a [guide]("http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons") that covered almost all the types of mice, how to configure xorg.conf, and the like.  I can't say for sure what part got my buttons working correctly, but i think that specifying "Dev Phys" as the actual USB location and event#.  I have a Cordless MX Duo (MX700 mouse and wireless internet keyboard).  Both were identified as the "Logitech USB Receiver" but they had different event numbers.  Simply linking the mouse by name"Logitech USB Receiver" or by input# resulted in a no-boot for X.  Currently I'm not using xmodmap, and i haven't had to mess with firefox to get the nav buttons working.  This also extends into World of Warcraft mouse button assignments, and presumably any other app.

[xubuntu 6.10]

---

### Post by jrib on 2007-03-04
> **Big_Rog said:**
> ...I can't say for sure what part got my buttons working correctly, but i think that specifying "Dev Phys" as the actual USB location and event#.  I have a Cordless MX Duo (MX700 mouse and wireless internet keyboard)....

[xubuntu 6.10]

Ah yes, that should work on edgy.  Bourlotierus, you should try this too.  

On dapper, the event #'s seemed to change after reboots so you couldn't reliably use it.  It seems to have become constant again on edgy. Sometimes, plugging in new devices used to change event #'s too.  That's why I think udev rules would be the best way to go.  But if it works for you, go with it :)

---

### Post by bankie on 2007-03-05
> **_jason said:**
> Sure, just use xbindkeys to catch button #(whatever it is for side scroll, use 'xev' to find out) and play the necessary keyboard shortcut like in the examples for "back" and "forward".

I'm having problems getting this to work.

xev reports the tilt wheel as buttons 6 & 7.


This is my xbindkeysrc file:

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Tab]""
  b:7
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Shift_L]\[Tab]""
  b:6
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14

```


Any ideas?

---

### Post by bankie on 2007-03-05
I've got the tilt wheel working in Firefox so you can disregard the previous post. I was editing xbindkeysrc and running **xbindkeys &** thinking that it would reload the xbindkeysrc. Evidently it doesn't work that way.  :P      After rebooting everything is working fine.


```
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Tab]""
  b:7
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Shift_L]\[Tab]""
  b:6

```

It might be helpful to add that little snippet to the Howto.

---

### Post by strikeback03 on 2007-03-06
OK, I followed the instructions in the Wiki and my forward/back buttons work now, both in FF and amongst folders.  However neither the cruise control buttons or horizontal scrolling works.  And is there any way to map the application switcher button to just be "Alt+Tab"?

---

### Post by bankie on 2007-03-07
> **strikeback03 said:**
> OK, I followed the instructions in the Wiki and my forward/back buttons work now, both in FF and amongst folders.  However neither the cruise control buttons or horizontal scrolling works.  And is there any way to map the application switcher button to just be "Alt+Tab"?

This *should* work for horizontal scrolling.

xbindkeysrc:
```
"/usr/bin/xvkbd -xsendevent -text "\[left]""
  b:7
"/usr/bin/xvkbd -xsendevent -text "\[right]""
  b:6
```

For the app switcher button you'll need to run xev in a terminal. Hit the app switch button in the white window and watch what button is listed in the terminal. Once you know that try adding the following line in xbindkeysrc replacing b:x with the button number xev gave you.

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Tab]""
  b:x

```

---

### Post by strikeback03 on 2007-03-07
the app switcher is button 10 acording to xev.  Here is what my xbindkeysrc looks like now:
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14
"/usr/bin/xvkbd -xsendevent -text "\[left]""
  b:7
"/usr/bin/xvkbd -xsendevent -text "\[right]""
  b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Tab]""
  b:10

```

app switch/cruise/horizontal scrolling still don't work though.

---

### Post by bankie on 2007-03-07
The "[left] & [right]" variables in my previous post need to be capitalized. For some reason the forum is removing capatilization.

```
"/usr/bin/xvkbd -xsendevent -text "\[Right]""
  b:7
"/usr/bin/xvkbd -xsendevent -text "\[Left]""
  b:6
```

I just tested it out and was able to get left and right scrolling to work.  
I haven't been able to get Alt+Tab to work yet.

---

### Post by strikeback03 on 2007-03-07
Hmm, I changed the Capitalization and still nothing.  Restarting X with ctrl+alt+backspace should be sufficient to reload the file, correct?

---

### Post by bankie on 2007-03-08
No. You'll have to 'killall xbindkeys' and then restart it with 'xbindkeys &'

---

### Post by strikeback03 on 2007-03-08
OK, other than having left and right flipped (which I fixed) the side scrolling works now.  Cruise and application switch don't work for now, but I guess I can live without those if no one knows how to get them working.  Thanks for your help.

---

### Post by grantjohnston on 2007-03-18
> **_jason said:**
> See if it works with a fresh new user

Jesus, I neglected to try and fix this for a while... No go on the new user.

---

### Post by grantjohnston on 2007-03-21
bumpy :(

---

### Post by jrib on 2007-03-21
> **grantjohnston said:**
> Jesus, I neglected to try and fix this for a while... No go on the new user.

ok, this narrows things down.  But it's a bit strange that a system-wide xmodmap rule is doing this.  I may be on the wrong track...

But, if you want to continue to humor me...

Do this:
```
xmodmap -pp
```

and record the output, and then:

```
xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20"
```

and then tell me the output of:
```
xmodmap -pp
```

---

### Post by Digitallysick on 2007-03-22
can someone post there xorg, i have my mx1000 plugged in through usb, really just want the forward and back buttons to work in gnome and firefox

---

### Post by grantjohnston on 2007-03-24
> **_jason said:**
> ok, this narrows things down.  But it's a bit strange that a system-wide xmodmap rule is doing this.  I may be on the wrong track...

But, if you want to continue to humor me...

Do this:
```
xmodmap -pp
```

and record the output, and then:

```
xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20"
```

and then tell me the output of:
```
xmodmap -pp
```

Before

```
grant@threeve:~$ xmodmap -pp
There are 20 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              8
        5              9
        6             10
        7             11
        8             12
        9              6
       10              7
       11              4
       12              5
       13             13
       14             14
       15             15
       16             16
       17             17
       18             18
       19             19
       20             20

grant@threeve:~$ 

```


after


```

grant@threeve:~$ xmodmap -pp
There are 20 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              4
        5              5
        6              6
        7              7
        8              8
        9              9
       10             10
       11             11
       12             12
       13             13
       14             14
       15             15
       16             16
       17             17
       18             18
       19             19
       20             20

grant@threeve:~$



```


After restarting X, it still doesn't work properly.

---

### Post by jrib on 2007-03-24
> **grantjohnston said:**
> Before
...
after
...


Are your buttons back to normal after doing that?

---

### Post by grantjohnston on 2007-03-27
> **_jason said:**
> Are your buttons back to normal after doing that?

Nope, still screwy :(

---

### Post by jrib on 2007-03-27
> **grantjohnston said:**
> Nope, still screwy :(

did anything change?  Did you button numbers change?

What exactly is not working now?

---

### Post by Digitallysick on 2007-03-27
finally got mine to work, yay! i just followed the guide for edgy , for some reason this time it worked. My ff buttons work and nautlius.

---

### Post by grantjohnston on 2007-03-29
> **_jason said:**
> did anything change?  Did you button numbers change?

What exactly is not working now?

Yeah, the numbers changed from how they were (the first one) to 1-20 accordingly (the second set, after I changed them). Nothing changed, however. Up and down on the wheel still move forward and back in the browser history.

Sorry if I'm not making much sense.. This mouse problem has been plaguing me since November, and it's driving me absolutely ******* nuts! :(

---

### Post by jsylvia007 on 2007-03-29
I have a Dell XPS M1210 with internal bluetooth.  I would love to get my MX1000 to work with it.  I have it connected, but only the left and right buttons work.  

output of "sudo cat /proc/bus/input/devices" [edited for only the mouse device]

```

I: Bus=0003 Vendor=0a5c Product=4503 Version=0100
N: Name="Broadcom Corp"
P: Phys=usb-0000:00:1d.1-1.3/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse0 event3 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```

How am i supposed to correctly set this up on my machine... all i really want is the scroll to work (which it currently does not) and the side buttons.  

Relevant section from xorg.conf:

```

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Protocol"              "evdev"
        Option          "Dev Phys"              "usb-*/input0"
        Option          "Device"                "/dev/input/event3"
        #Option          "Buttons"               "12"
        #Option          "ZAxisMapping"          "4 5 7 6"
EndSection

```

Note that even uncommented the BUTTONS and ZAXIS lines dont make a difference.

PLEASE HELP!!

~Jake

---

### Post by jsylvia007 on 2007-03-29
Ok...  I solved my first problem...  I ended up having to use:

hciconfig hci0 reset and then reconnect to the mouse.

Now, my X server crashes when it tries to load the mouse..  Any ideas?

~Jake

---

### Post by sudo_t43p on 2007-04-01
> **bankie said:**
> I've got the tilt wheel working in Firefox so you can disregard the previous post. I was editing xbindkeysrc and running **xbindkeys &** thinking that it would reload the xbindkeysrc. Evidently it doesn't work that way.  :P      After rebooting everything is working fine.


```
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Tab]""
  b:7
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Shift_L]\[Tab]""
  b:6

```

It might be helpful to add that little snippet to the Howto.

Thanx man! Just a FYI, on my laptop (StinkPad T43P) I have to use [Control_R]\[ISO_Left_Tab] instead of [Control_L]\[Shift_L]\[Tab]

---

### Post by jrib on 2007-04-01
> **jsylvia007 said:**
> 
Relevant section from xorg.conf:

```

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Protocol"              "evdev"
        Option          "Dev Phys"              "usb-*/input0"
        Option          "Device"                "/dev/input/event3"
        #Option          "Buttons"               "12"
        #Option          "ZAxisMapping"          "4 5 7 6"
EndSection

```

~Jake

get rid of         ```
    Option          "Protocol"              "evdev"
```

---

### Post by jrib on 2007-04-01
> **grantjohnston said:**
> Yeah, the numbers changed from how they were (the first one) to 1-20 accordingly (the second set, after I changed them). Nothing changed, however. Up and down on the wheel still move forward and back in the browser history.

Sorry if I'm not making much sense.. This mouse problem has been plaguing me since November, and it's driving me absolutely ******* nuts! :(

and what do the side buttons for back and forward do?

---

### Post by sudo_t43p on 2007-04-01
Btw, does anyone know how to alt\tab to change windows?

Following does not work:

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Tab]""
  b:10

---

### Post by sudo_t43p on 2007-04-01
> **jsylvia007 said:**
> I have a Dell XPS M1210 with internal bluetooth.  I would love to get my MX1000 to work with it.  I have it connected, but only the left and right buttons work.  

output of "sudo cat /proc/bus/input/devices" [edited for only the mouse device]

```

I: Bus=0003 Vendor=0a5c Product=4503 Version=0100
N: Name="Broadcom Corp"
P: Phys=usb-0000:00:1d.1-1.3/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse0 event3 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```

How am i supposed to correctly set this up on my machine... all i really want is the scroll to work (which it currently does not) and the side buttons.  

Relevant section from xorg.conf:

```

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Protocol"              "evdev"
        Option          "Dev Phys"              "usb-*/input0"
        Option          "Device"                "/dev/input/event3"
        #Option          "Buttons"               "12"
        #Option          "ZAxisMapping"          "4 5 7 6"
EndSection

```

Note that even uncommented the BUTTONS and ZAXIS lines dont make a difference.

PLEASE HELP!!

~Jake

Well, I think you should use "Logitech Bluetooth Mouse" instead (try to scroll down an see if it appears in your list). Works for me on Fiesty.

I think Broadcom Corp is your bluetooth or wifi card (?)

Try lookin for somethin like this:
```

I: Bus=0005 Vendor=046d Product=b003 Version=4310
N: Name="Logitech Bluetooth Mouse"
P: Phys=00:16:CF:DE:2C:10
S: Sysfs=/class/input/input9
H: Handlers=mouse3 event9 ts3 
B: EV=7
B: KEY=7fff0000 0 0 0 0 0 0 0 0
B: REL=143

```

And add to your xorg:
```

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
**	Inputdevice	"Logitech MX1000" "SendCoreEvents"**
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

```
#I think SendCoreEvents is better to use if you use a laptop and do not allways travel with your bt mouse

and:

```

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
[B]        Option          "Name"          "Logitech Bluetooth Mouse"
[/B]        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection


```

and your .xbindingkeysrc should look something like this depending on how you would like your buttons on mx1000 to respond:
```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Tab]""
  b:7
"/usr/bin/xvkbd -xsendevent -text "\[Control_R]\[ISO_Left_Tab]""
  b:6
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[ISO_Left_Tab]""
  b:10
"/usr/bin/xvkbd -xsendevent -text "\[Control_R]\[w]""
  b:2
"echo ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14

```

remember to restart xbindingkeys for changes to take effect (I had problems to "remember" this part..)

If you figure out howto switch windows [alt+tab], please drop me a line.

---

### Post by mig10k on 2007-04-01
Works with Genius Ergo 525 too

But after going through the tutorial, volume buttons don't work anymore. Back and Forward buttons work on left and right scroll.

---

### Post by grantjohnston on 2007-04-01
> **_jason said:**
> and what do the side buttons for back and forward do?

Nothing at all

---

### Post by jsylvia007 on 2007-04-03
I'm still having issues.  I've changed my config to match yours exactly, because thats what mine shows when i cat the /proc.  My Xorg still Signal 11's though, on the evdev_drv.o

~Jake

---

### Post by gearshifter on 2007-04-03
> **dremon said:**
> Hello,

I have MX5000 bluetooth desktop (MX1000 mouse + keyboard), connected to the Acer laptop (which also has synaptic touchpad). The OS is Edgy. There are some problems I would really like to solve with your help.

In the /proc/bus/input/devices, there are 2 "Logitech Logitech BT Mini-Receiver" names listed, one for the mouse (event4) and another for the keyboard (event3).
I've configured the mouse in xorg.conf via the {"Device" "/dev/input/event4"} parameter and it works, but....
Somehow, the keyboard started behaving very strangely. First of all, the extra buttons like "Email" and sliders like "Volume" do not work anymore. They were working perfectly before I added the evdev mouse device. Now, instead of doing any actions, these buttons cause X server to crash.
This crash does not occur however, if I disable the synaptic touchpad in the ServerLayout section, but the above mentioned buttons still do not work.
And another thing, the mouse stops working after suspending/resuming the laptop. I guess it is also a problem of evdev driver.

Thanks for any help.

I am at the same point as you.  I can get the buttons on my bluetooth mouse to work successfully but i then lose support for my volume and other extra buttons on the mx5000

---

### Post by grantjohnston on 2007-04-06
bump.. Anyone have any clues?

---

### Post by xsnslaine on 2007-04-10
I have read through but i cant see what i is going wrong.

at the moment in world of warcraft, no thumb buttons are still working and the buttons above and below the scroll wheel read as scroll up and scroll down.

any ideas?

xorg.conf file: 
```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB RECEIVER"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	# /dev/input/event
	# for USB
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	# /dev/input/event
	# for USB
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	# /dev/input/event
	# for USB
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7800 GTX]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"L1740B"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7800 GTX]"
	Monitor		"L1740B"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	InputDevice     "Logitech MX1000" "CorePointer"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by xsnslaine on 2007-04-10
i think i may have got round most of the problems ... one issue i have thought, if i hold shift, none of the mapped buttons work.

also the middle thumb button not doing anything, and the buttons above and below the scroll are still recording the mouse scroll event

---

### Post by xsnslaine on 2007-04-13
shameless bump.

basically my main issue at the moment is if i hold shift and press any mouse button the button isnt picked up, for example hold shift and press the middle mouse button to use the cube on beryl doesnt work, release shift it does.

---

### Post by grantjohnston on 2007-04-13
Mine are still FUBARD, the mousewheel controls navigation in Firefox and thunar.

---

### Post by grantjohnston on 2007-04-19
Hmm, updating to Feisty fixed it! Thank god, only 6 months of it not working!

---

### Post by Storm32 on 2007-04-20
I'm having a really odd problem. I was using 6.10 before and back and forward buttons worked fine. After upgrading to Feisty though, the back and forward buttons don't work unless I hold shift. Anyone know how I can get it back so I don't need to press shift?

EDIT:
Okay, I don't know what in the world just happened, but 2 hours later and suddenly my mouse is working fine without the shift button. I didn't restart my comp or anything, I just downloaded a manual for my motherboard. Kinda bizarre, but I'll take the magical fairy fix anyday.

---

### Post by acorn22 on 2007-04-21
I have an MX 600 (10 button) And I would like to know what to enter into the .xbindkeyrc file to make:

B:2 = right click
B:3 = middle click
B:8 = scroll right
B:9 = scroll left

thanks!

---

### Post by kayrune on 2007-04-21
I'm using 7.04 and cannot get this working, it seems whatever settings I put in xorg.conf it works, but it doesn't work correctly. I have the MX3100/MX1000 mouse/kbd combo.

this is xorg.conf , as you can see by the lines commented out I've tried a few alternatives

```
Section "InputDevice"
	Identifier	"Configured Mouse"
#	Driver		"mouse"
	Driver		"evdev"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mice"
	Option		"Device" 	"/dev/input/event3"
	Option          "Buttons"               "12"
	Option          "HWHEELRelativeAxisButtons" "7 6"
#	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5 7 6"
#	Option		"Emulate3Buttons"	"true"
###	Option      "evBits"        "+1-2"
###     Option      "keyBits"       "~272-287"
###     Option      "relBits"       "~0-2 ~6 ~8"
###     Option      "Pass"          "3"
```

xmodmap -pp reports 9 buttons.

xev reports the following
left = 1
right = 3
wheel click = 2
wheel down = 5
wheel up = 4
scroll down = 5
scroll up = 4+8
tilt left =  DEAD
tilt right = DEAD
back = 8
forward = 9
app switch = 2


I can live withouth the tilt, but I'm really missing the app switcher, that is being able to use it for something else than middleclick.

---

### Post by unabatedshagie on 2007-04-24
Has anyone updated this tutorial for feisty, I have followed it exactly but it's not working the same for me in feisty as it did in edgy.

For instance using the tilt function changes the volume.

Also the application switcher button (button 10) doesn't work.

---

### Post by jrib on 2007-04-24
> **unabatedshagie said:**
> Has anyone updated this tutorial for feisty, I have followed it exactly but it's not working the same for me in feisty as it did in edgy.

For instance using the tilt function changes the volume.

Also the application switcher button (button 10) doesn't work.

hmm, it worked the same for me in edgy as it did in feisty.  Try killing xbindkeys and see what button the tilt generates.  Check system > preferences > keyboard shorts to see what is bound to change the volume.

---

### Post by jrib on 2007-04-24
> **acorn22 said:**
> I have an MX 600 (10 button) And I would like to know what to enter into the .xbindkeyrc file to make:

B:2 = right click
B:3 = middle click
B:8 = scroll right
B:9 = scroll left

thanks!

You can use xmodmap to change what button# each button gets set as.
example, to switch button 2 with button 3 do something like:

xmodmap -e "pointer = 1 3 2 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20"

---

### Post by inlivingcolour on 2007-04-24
Now, how do I added xbindkeys to start up, but its not starting.  I cant use my side buttons unless i type in "xbindkeys &" in terminal.  Am I using the right xbindkeys by using the one in /usr/bin?  Im on Feisty Fawn now.  I did have this problem on 6.06, but I put it off.  :(  But, other than that, it works great.

---

### Post by boostjunki3 on 2007-04-24
I finally got my mx1000 working under feisty! First thing I did was follow the edgy instructions on the wiki page. Next, I did a few extra things to get it working.

Create a new file for a udev rule...

sudo nano /etc/udev/rules.d/010-local.rules

copy this into new file (name is same output from 'cat /proc/bus/input/devices')

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB RECEIVER", NAME="input/mx1000"

...save the new file.
Restart your udev service and disconnect/reconnect your mouse. If all went well, you should see an 'mx1000' listed under /dev/input/. If you don't see this, make sure that your spelling and caps of the name are all correct in the udev rule.

After you see the mx1000 under /dev/input, edit your xorg.conf to make it look like this:

Section "ServerLayout"
...
     InputDevice   "Logitech MX1000" "SendCoreEvents"
...
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Device" "/dev/input/mx1000"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

Under the ServerLayout section, I had to change 
InputDevice   "Logitech MX1000" "CorePointer"
to
InputDevice   "Logitech MX1000" "SendCoreEvents"
to allow X to startup. Without the change, I was receiving a no core pointer found error.

Restart your X session and everything should run just fine as long as you made these changes after following the wiki page. Just as a note, I restarted my computer also, so you may want to try that if it doesn't work for you.

---

### Post by nisukka on 2007-04-26
The previous guide didn't help me. The button 10 is still not properly recognized.
I did try rebooting.:(

---

### Post by jrib on 2007-04-26
> **nisukka said:**
> The previous guide didn't help me. The button 10 is still not properly recognized.
I did try rebooting.:(

Button 10 is the middle side one right?

Button 10 isn't bound to anything in the guide, you need to set something up yourself in the ~/.xbindkeysrc.  I don't know of something standard to bind it to so I left the guide like that.

---

### Post by Maybelline on 2007-04-27
> **unabatedshagie said:**
> Has anyone updated this tutorial for feisty, I have followed it exactly but it's not working the same for me in feisty as it did in edgy.

For instance using the tilt function changes the volume.

Also the application switcher button (button 10) doesn't work.

I'm in the same boat -- I would be happy to just disable the horizontal scroll buttons from ever firing, but I can't seem to figure out how to do that!

So, for now, it's generating the same keycode 174/176 as my keyboard.  Very annoying.

---

### Post by Blairboy on 2007-04-27
Ok, I had to fenagle the guide a bit because I had 2 logitech usb's listed from cat, but I got the mouse working perfectly.  The only problem is, now the none of the multimedia keys (volume, play/pause, etc) work on my keyboard.  I checked under xev, and when I press those buttons, they don't even register as keystrokes.  Help please!

---

### Post by Maybelline on 2007-04-27
> **Blairboy said:**
> Ok, I had to fenagle the guide a bit because I had 2 logitech usb's listed from cat, but I got the mouse working perfectly.  The only problem is, now the none of the multimedia keys (volume, play/pause, etc) work on my keyboard.  I checked under xev, and when I press those buttons, they don't even register as keystrokes.  Help please!

So, if you're in feisty, does xev give you a keycode 174/176 when you horizontal scroll (push the mousewheel left or right)?

Are you using the kbd driver or evdev in xorg.conf for your keyboard?  I tried the evdev driver (I have a Microsoft Natural Ergonomic Keyboard 4000) and couldn't get it to work.  I would recommend using the kbd driver, and see if that works for you.  Mind you, I'm no expert.

---

### Post by jrib on 2007-04-27
> **Blairboy said:**
> Ok, I had to fenagle the guide a bit because I had 2 logitech usb's listed from cat, but I got the mouse working perfectly.  The only problem is, now the none of the multimedia keys (volume, play/pause, etc) work on my keyboard.  I checked under xev, and when I press those buttons, they don't even register as keystrokes.  Help please!

Is everyone who is having keyboard button issues using a usb keyboard?

I have a keyboard with extra keys but have no issues.  It isn't connected as usb though.

---

### Post by Blairboy on 2007-04-27
I'm currently using kbd, which worked before I fixed the mouse.  And yeah, I'm using feisty.

---

### Post by nisukka on 2007-04-28
> **_jason said:**
> Button 10 is the middle side one right?

Button 10 isn't bound to anything in the guide, you need to set something up yourself in the ~/.xbindkeysrc.  I don't know of something standard to bind it to so I left the guide like that.

Yes, button 10 is the middle thumb button.
I understand that it is not bound to anything in the guide so I modified xbindkeys to this:
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:10
"echo ButtonRelease 11 ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonRelease 12 ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonRelease 13 ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonRelease 14 ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14
```

So button 10 should do the same as button 9 (forward) but it doesn't work.
Using xev-command, I get this as the result for pressing the middle thumb button:
```
KeyPress event, serial 33, synthetic NO, window 0x3a00001,
    root 0x168, subw 0x0, time 4806452, (259,164), root:(266,215),
    state 0x10, keycode 168 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3a00001,
    root 0x168, subw 0x0, time 4806452, (259,164), root:(266,215),
    state 0x10, keycode 168 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Any ideas?

---

### Post by jrib on 2007-04-28
> **nisukka said:**
> 
Using xev-command, I get this as the result for pressing the middle thumb button:


What do you get if you kill xbindkeys first?

---

### Post by nisukka on 2007-04-28
> **_jason said:**
> What do you get if you kill xbindkeys first?

I killed xbindkeys and got this as the result of xev:
```
KeyPress event, serial 33, synthetic NO, window 0x1e00001,
    root 0x168, subw 0x0, time 8892387, (318,124), root:(325,175),
    state 0x10, keycode 168 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x1e00001,
    root 0x168, subw 0x0, time 8892387, (318,124), root:(325,175),
    state 0x10, keycode 168 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```
I didn't notice any significant difference to the previous one.

---

### Post by bluehue on 2007-04-28
> **Storm32 said:**
> I'm having a really odd problem. I was using 6.10 before and back and forward buttons worked fine. After upgrading to Feisty though, the back and forward buttons don't work unless I hold shift. Anyone know how I can get it back so I don't need to press shift?

EDIT:
Okay, I don't know what in the world just happened, but 2 hours later and suddenly my mouse is working fine without the shift button. I didn't restart my comp or anything, I just downloaded a manual for my motherboard. Kinda bizarre, but I'll take the magical fairy fix anyday.I'm having this very same problem. I think the last round of updates made it stop working somehow as now I need to press shift in order to use the back and forward thumb buttons.  System Monitor shows that xbindkeys is indeed running. Has anyone figured out a fix?

My xorg.conf:```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Logitech MX1000" "CorePointer"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV40 [GeForce 6800 Ultra]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV40 [GeForce 6800 Ultra]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```
And .xbindkeysrc:
```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"echo ButtonRelease 11 ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonRelease 12 ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonRelease 13 ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonRelease 14 ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14
```It seems like everything is as it should be according to the wiki guide :confused:

Edit: Wow, just as in the case of the poster I quoted, mine started to work back on its own again. It must have been working for days before I tried it after getting used to the upper left back button on Firefox.

---

### Post by Bazirker on 2007-05-02
I also have an MX1000 that I can't get to work.  I followed the guide and rebooted and got this message:

> The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc105", layout "us" and option "lv3	lv3:ralt_switch", but the the following settings were found: model "evdev", layout "us" and option "lv3	lv3:ralt_switch".

Which set would you like to use?

I didn't change the keyboard settings in xorg.conf, only the mouse settings.  Here's my xorg.conf (edited to show only serverlayout, keyboard, and mouse settings):

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Logitech MX1000" "SendCoreEvents"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection
```

Now, the forward/back buttons work in firefox only if I hold shift,  but it doesn't seem to be magically fixing itself like it has for others; its behavior has been the same for days.  I ultimately want to map almost every button to a keystroke, but proper forward/back buttons would be a nice start.  At the moment, my xbindkeysrc is identical to nisukka's.  Any ideas?

---

### Post by nem75 on 2007-05-05
I'm having the same problem as reported in the last two post above this one. Same configuration, too. I can't imagine which update should have cause this, but I'm absolutely positive that I didn't change anything myself.

Anyway, xev now reports the back/forward button as 6 and 7 instead of 8 and 9. Change the .xbindkeysrc accordingly and you will at least have those working again until this issue is worked out.

For side scrolling you're out of luck, as the wheel tilting isn't detected by xev at all right now.

Anyone got an idea on how to proceed with this or what could have caused this sudden change?

---

### Post by RockDoctor on 2007-05-05
A bit OT, but when I saw  MX1000, my first thought was, "12 buttons on a dot-matrix printer?" FWIW, the Epson MX1000 was a fairly popular printer back in the early 80s

---

### Post by bluehue on 2007-05-06
> **nem75 said:**
> I'm having the same problem as reported in the last two post above this one. Same configuration, too. I can't imagine which update should have cause this, but I'm absolutely positive that I didn't change anything myself.

Anyway, xev now reports the back/forward button as 6 and 7 instead of 8 and 9. Change the .xbindkeysrc accordingly and you will at least have those working again until this issue is worked out.

For side scrolling you're out of luck, as the wheel tilting isn't detected by xev at all right now.

Anyone got an idea on how to proceed with this or what could have caused this sudden change?Thank you for your post. I lost the back/forward buttons, regained them, and lost them again just recently and it seems to happen every time I update the system. Changing my buttons to 6/7 fixed the issue, but I fear I may have to change them back to 8/9 to get them working again if I lose them after another update. :)

---

### Post by nem75 on 2007-05-06
> **bluehue said:**
> Thank you for your post. I lost the back/forward buttons, regained them, and lost them again just recently and it seems to happen every time I update the system. Changing my buttons to 6/7 fixed the issue, but I fear I may have to change them back to 8/9 to get them working again if I lose them after another update. :)

Yep, exactly what happened here last evening. Buttons stopped working again although mapped to 6 and 7. Remapped to 8 and 9 - worked. Plus the tilt wheel. Booted this morning: not working again. Remapped to 6 and 7 - working.

This really is annoying. Any help would be very much appreciated.

---

### Post by unabatedshagie on 2007-05-07
I'm just wondering if it would be possible to map the tilt left/right to switch desktops with beryl?

Also what would the line I need to add into xbindkeys to map the windows key + e to it?

---

### Post by hashstat on 2007-05-08
Following the mx1000 howto worked for me in Dapper, but I'm having no luck with it in Feisty.  However, after reading this thread and experimenting a bit, I now have all 12 buttons working correctly.  Here is how I did it.

I created a new udev rule to always map my mouse to */dev/input/mx1000* by creating **/etc/udev/rules.d/10-local.rules** with the following contents:
```

KERNEL=="mouse[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYMLINK="input/mx1000"

```
Unplugging the mouse receiver and then plugging it back in caused the symlink */dev/input/mx1000* to point to the auto-named device /dev/input/mouse1.

Then I modified the InputDevice section for the mx1000 in **/etc/X11/xorg.conf**:
```

Section "InputDevice"
        Identifier  "Logitech MX1000"
        Driver          "mouse"
        Option          "Device"                "/dev/input/mx1000"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
EndSection

```

And I added the following to the ServerLayout section:
```

Section "ServerLayout"
        ...
        InputDevice "Logitech MX1000" "SendCoreEvents"
        ...
EndSection

```

Restarting X caused 9 buttons on the mouse t be detected: left, middle, right, scroll up, scroll down, cruise up, cruise down, browser forward, and browser backward.  The scroll left, scroll right, and task switch buttons were detected as keystrokes 176, 174 and 168, respectively (detected using xev).  So I created **~/.xbindkeysrc** with the following contents:
```

#Browser Forward (Mouse)
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
   b:8

#Browser Back (Mouse)
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
   b:9

#Task Switch (Mouse)
"/usr/bin/xvkbd -text "\C\Ad""
   m:0x0 + c:168

#Scroll Left (Mouse)
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
   m:0x0 + c:176

#Scroll Right (Mouse)
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
   m:0x0 + c:174

```
I mapped the task switch button to <Ctrl>+<Alt>+D so that I can quickly toggle showing my desktop.

I started xbindkeys to test the setup and then added it to my session startup programs.

That's it.


Note: I had an issue with the horizontal scroll buttons being mapped to the volume controls.  I fixed the problem by disabling the keyboard shortcuts for the volume controls in the keyboard shortcuts preferences.

---

### Post by jrib on 2007-05-08
hashstat, great.  I can't replicate the issue myself, but it seems to happen to several people.  We should at least link to your post in the guide and if it works better for the others in this thread that were having trouble in feisty, we can just add straight into the guide and replace what is there.

[edit] I like your way because it should work for users who have more than one device attached to the receiver (keyboard/mouse combos).  Though the evdev man page says you can't match anything other than "/dev/input/event<N>, where <N>  is an integer" and I know this was an issue previously (in edgy I think), they must have forgotten to update the documentation.

---

### Post by Bazirker on 2007-05-09
HOLY MOTHER OF GOD MY MOUSE FINALLY WORKS!!!!!!!!!!!!  I'm a linux newb and have spent sooooo much time fighting with this, it's great to finally have it working.

hashstat, I used your method, although I had to capitalize "left" and "right" for the forward and back buttons, so in my xbindkeys, those two entries look like:

```
#Browser Forward (Mouse)
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
   b:8

#Browser Back (Mouse)
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
   b:9
```

However, I'm on a laptop, and the changes seem to have disabled my touchpad.  I have everything set to SendCoreEvents in xorg.conf, so I don't really understand why my touchpad can't still function...any ideas?

EDIT: OK, dunno why, but it won't let me capitalize the "Left" and "Right" in the code, or at least when I do and it posts, it goes back to lower case.  Forum bug report?

---

### Post by jrib on 2007-05-18
Hello everyone,

If you were having keyboard troubles, can you check what GNOME says for your keyboard model in systems > preferences > keyboard.  I added another mouse and it seems to have changed the model to "evdev managed" though my keyboard is not supposed to be using evdev.

---

### Post by jrocket on 2007-05-19
i did everything as suggested  my mouse is a lot faster, my forward and back side keys still dont work in WoW, and they dont work in firefox now.  this is after i changed the settings as per hashstat's post and rebooted.
any ideas?  all i want is for cruise control to work in WoW.

---

### Post by jrib on 2007-05-19
> **jrocket said:**
> i did everything as suggested  my mouse is a lot faster, my forward and back side keys still dont work in WoW, and they dont work in firefox now.  this is after i changed the settings as per hashstat's post and rebooted.
any ideas?  all i want is for cruise control to work in WoW.

did you see bazirker's comment about capitalizing "Left" and "Right"?

---

### Post by jrocket on 2007-05-19
> **_jason said:**
> did you see bazirker's comment about capitalizing "Left" and "Right"?

I saw it, but I read it wrong last night.  After I capitalized "left" and "right" it now works in my browser, but not in WoW.  In WoW the center side button makes you run if you hold it down, but when you let go you stop running, and the forward and back side buttons don't do anything.

---

### Post by jrib on 2007-05-19
> **jrocket said:**
> I saw it, but I read it wrong last night.  After I capitalized "left" and "right" it now works in my browser, but not in WoW.  In WoW the center side button makes you run if you hold it down, but when you let go you stop running, and the forward and back side buttons don't do anything.

And alt-left and alt-right on the keyboard work fine and do something in wow?

---

### Post by jrocket on 2007-05-19
> **_jason said:**
> And alt-left and alt-right on the keyboard work fine and do something in wow?

Yes.  alt-left and alt-right on the keyboard are both bound to autorun.  With Left and Right capitalized, the buttons don't work in WoW but they do work in my web browser, but with them left uncapitalized they still don't work in WoW but also don't work in the web browser.

---

### Post by Al_maverick on 2007-05-29
I have a genius ergo 520. I followed this guide but I couldnt make the extra buttons work. I checked with xev and only the 2 standard, the wheel and the wheel click are recognized as buttons. The other 4 (back and forward, and the side ones) are not appearing at all.
Has anyone made a genius 520 work? I know that the 525 works and the logitech MX 518 too, that is pretty similar in chipset.
One thing, I am using it with the PS/2 adapter, not via USB. Could that have something to do with it?

---

### Post by tweedledee on 2007-05-30
> **Al_maverick said:**
> One thing, I am using it with the PS/2 adapter, not via USB. Could that have something to do with it?

Yes.  While I've not used your mouse, my experience with those adapters is that they discard all information except the events you are reporting as being detected; all extra button functionality is lost.

---

### Post by Al_maverick on 2007-05-30
> **tweedledee said:**
> Yes.  While I've not used your mouse, my experience with those adapters is that they discard all information except the events you are reporting as being detected; all extra button functionality is lost.
That was it, but I got some weird results when connecting it via USB.

Using the method in this guide, I had normal buttons, plus horizontal scroll.

Using ExplorerPS/2 protocol, I have all buttons, but horizontal scroll :D

I will keep the latter one for the moment. So much rebooting, im starting to feel windoze :D

---

### Post by Bazirker on 2007-06-01
So, haststat's method works, although I'm on a laptop and using it disables my touchpad.  Anyone have any tips about how to modify the method such that it still allows usage of the touchpad?

---

### Post by rogun on 2007-06-03
> **Bazirker said:**
> I also have an MX1000 that I can't get to work.  I followed the guide and rebooted and got this message:



I didn't change the keyboard settings in xorg.conf, only the mouse settings.  ... 


I'm having the same problem, even though everything matches in xorg.conf, gconf and the keyboard settings window. It seems to think that I've changed my keyboard settings, even though it was the mouse.

---

### Post by Braedley on 2007-06-03
I followed all the steps that were laid out, but still couldn't get X to start after I made the changes.  I have an MX5000 that also communicates through the same bluetooth receiver, so could that be what's causing my problems, and if so, how should I go about fixing it?

EDIT: after following the steps in a previous post, I have the back and forward buttons, but the cruise buttons are still mapped to the scroll wheel, and the side scroll buttons aren't mapped.  That's still considerably better than what I had before, but I would like full functionality.

---

### Post by jbj on 2007-06-08
I got my MX1000 working perfectly at 1st, however, once I re-booted it no longer worked. I have xbindkeys running at startup and I've checked everything else is ok.

Confused...

---

### Post by gene74 on 2007-06-08
how do i get back to restore the back up file?

---

### Post by jrib on 2007-06-10
> **gene74 said:**
> how do i get back to restore the back up file?

After X fails to start you should end up at tty1, if not, press ctrl-alt-f1.  If that still doesn't work for whatever reason, reboot and choose "recovery mode" from the grub menu.

Then just copy the backup to /etc/X11/xorg.conf

---

### Post by jusmurph on 2007-06-11
Will installation of evdev get rid of the random erratic cursor movements?

---

### Post by isecore on 2007-06-16
Hi all. I'm just wondering if anyone has a solution to the fact that Ubuntu reassigns the buttons after every reboot when using the evdev driver?

Before following this guide I had most of the things working on my own, but felt that I needed the tilt-scrollerthing and followed the guide. Now, every time (admittedly not that often, but it happens) I reboot the buttons get shuffled around, and some things end up not even being buttons!

Any hints and pointers?

**EDIT: Never mind, I was just being stupid.**

---

### Post by tjbk_tjb on 2007-06-24
I'm having a problem.
When I run anything, it doesn't respond to the side scroll or the switch application buttons. And only 7 buttons are being reported by xmodmap.
I executed "cat /dev/input/mouse1| hexdump" on tty1 and saw a bunch of hexadecimal come out when I moved the mouse or pressed the buttons. But nothing came out when I pressed the side scroll or switch application buttons.

My mouse configuration section in xorg.conf (after a lot of messing around):
```
Section "InputDevice"
 Identifier "Logitech MX1000"
 Driver     "evdev"
Option "Buttons" "12"
# Option     "CorePointer"
# Option     "Device"    "/dev/input/mx1000"
Option      "Name" "Logitech USB Receiver"
Option          "ZAxisMapping"          "11 12 10 9"
EndSection
```

---

### Post by strikeback03 on 2007-06-28
anyone know why sometimes it works fine, and sometimes the side buttons don't work?

---

### Post by Bazirker on 2007-07-31
> **hashstat said:**
> Following the mx1000 howto worked for me in Dapper, but I'm having no luck with it in Feisty.  However, after reading this thread and experimenting a bit, I now have all 12 buttons working correctly.  Here is how I did it.

I created a new udev rule to always map my mouse to */dev/input/mx1000* by creating **/etc/udev/rules.d/10-local.rules** with the following contents:
```

KERNEL=="mouse[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYMLINK="input/mx1000"

```
Unplugging the mouse receiver and then plugging it back in caused the symlink */dev/input/mx1000* to point to the auto-named device /dev/input/mouse1.

Then I modified the InputDevice section for the mx1000 in **/etc/X11/xorg.conf**:
```

Section "InputDevice"
        Identifier  "Logitech MX1000"
        Driver          "mouse"
        Option          "Device"                "/dev/input/mx1000"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
EndSection

```

And I added the following to the ServerLayout section:
```

Section "ServerLayout"
        ...
        InputDevice "Logitech MX1000" "SendCoreEvents"
        ...
EndSection

```

Restarting X caused 9 buttons on the mouse t be detected: left, middle, right, scroll up, scroll down, cruise up, cruise down, browser forward, and browser backward.  The scroll left, scroll right, and task switch buttons were detected as keystrokes 176, 174 and 168, respectively (detected using xev).  So I created **~/.xbindkeysrc** with the following contents:
```

#Browser Forward (Mouse)
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
   b:8

#Browser Back (Mouse)
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
   b:9

#Task Switch (Mouse)
"/usr/bin/xvkbd -text "\C\Ad""
   m:0x0 + c:168

#Scroll Left (Mouse)
"echo ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
   m:0x0 + c:176

#Scroll Right (Mouse)
"echo ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
   m:0x0 + c:174

```
I mapped the task switch button to <Ctrl>+<Alt>+D so that I can quickly toggle showing my desktop.

I started xbindkeys to test the setup and then added it to my session startup programs.

That's it.


Note: I had an issue with the horizontal scroll buttons being mapped to the volume controls.  I fixed the problem by disabling the keyboard shortcuts for the volume controls in the keyboard shortcuts preferences.

This method works for me, but I'm on a laptop, and if I boot without the mouse attached, the system freaks.  Does anyone have any tips on how to modify this method so I can boot without the mouse attached?

---

### Post by mrojas73 on 2007-08-24
> **Bazirker said:**
> This method works for me, but I'm on a laptop, and if I boot without the mouse attached, the system freaks.  Does anyone have any tips on how to modify this method so I can boot without the mouse attached?

After hours and hours of trying different methods I decided to give this one a try and for my surprise it worked like a charm even though my mouse is not the mx1000.  My mouse is came with my MX3000 keyboard so I am guessing it is an MX3000.

I only made the changes to the xorg and it works after rebooting, I haven't tried unplugin the mouse off yet.

Thank you for the help.

---

### Post by isecore on 2007-08-24
> **Bazirker said:**
> This method works for me, but I'm on a laptop, and if I boot without the mouse attached, the system freaks.  Does anyone have any tips on how to modify this method so I can boot without the mouse attached?

I would make sure that the builtin trackpad/trackpoint (whichever your laptop is equipped with) is configured and set to "CorePointer" since that dictates which pointer device is the default for X.

As for the mouse that is included with the MX3000 package it's identical to the MX1000, only difference is that it shares the receiver with the keyboard.

---

### Post by thefutoneng on 2007-08-27
I just bought the mx3200 combo and both the keyboard and mouse are identified by the same name.  Any thoughts?

---

### Post by jrib on 2007-08-27
> **thefutoneng said:**
> I just bought the mx3200 combo and both the keyboard and mouse are identified by the same name.  Any thoughts?

I've been meaning to update the wiki but don't have a mouse lying around.

If you read 'man evdev', the "BASIC CONFIGURATION" section has a mouse sample with some extra options which narrow it down to only select mice and not keyboards.  I've been using this lately for my mice, but I do not have a keyboard combo so I can't test that this works.  I believe that this should work  and have been planning on updating the wiki with these further options soon, however.  Please let us know if it works for you.

Your other option is to use a method like someone posted a little while ago here where you use a udev rule to create a link to the mouse and create a new link.  Then you use the link in in your xorg.conf.

---

### Post by thefutoneng on 2007-08-28
I tried adding the "Basic Configuration" parts from the man page of evdev but no luck.  

Udev rule:

```

KERNEL=="mouse[0-9]*", SYSFS{../name}=="Logitech USB Receiver", SYMLINK="input/mx1000"

```

Xorg.conf file:

```

Section "ServerLayout"
    ...
    InputDevice     "Logitech MX1000" "CorePointer"
    ...l
EndSection
...
...
...
Section "InputDevice"
    Identifier      "Logitech MX1000"
    Driver          "evdev"
    Option          "Name"          "Logitech USB Receiver"
    Option 	       "evBits"  "+1-2"
    Option         "keyBits" "~272-287"
    Option         "relBits" "~0-2 ~6 ~8"
    Option         "Pass"    "3"
    Option         "Device" "/dev/input/mx1000"
EndSection

```

X error generated:

```

(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) evdev brain: Rescanning devices (2).
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
No core pointer

Fatal server error:
failed to initialize core devices

```

I'm hope this is a really simple fix.  I don't have a lot of experience with modifying X for keyboards / mice.

Out of the box, some of the extra keys on the keyboard work (none of the FN hotkeys work but I really dont care about that).  

On the mouse, horizontal scrolling works but not the forward / back buttons.  xev shows that the forward and back buttons are buttons 2 and 3.

---

### Post by jrib on 2007-08-28
> **thefutoneng said:**
> I tried adding the "Basic Configuration" parts from the man page of evdev but no luck.  



I think you should try each suggestion separately (I see that what you pasted has both the extra evdev stuff and the /dev/input/mx1000 stuff).

If the extra evdev stuff isn't working, you can try making sure that those are indeed the correct bits for your mouse (the evdev man page tells you how to verify this).

If you use udev instead then make sure you reboot after you create the rule and ensure that /dev/input/mx1000 does indeed get created.

---

### Post by thefutoneng on 2007-08-28
I was able to determine that the mouse was getting mapped to /dev/input/mouse1

```

username@underwearless:~$ cat /proc/bus/input/devices 
...
...
I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:0b.0-3/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd mouse1 event2 ts1 

username@underwearless:~$ udevinfo -a -p $(udevinfo -q path -n /dev/input/mouse1)

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/class/input/input2/mouse1':
    KERNEL=="mouse1"
    SUBSYSTEM=="input"
    DRIVER==""
    ATTR{dev}=="13:33"

  looking at parent device '/class/input/input2':
    KERNELS=="input2"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{uniq}==""
    ATTRS{phys}=="usb-0000:00:0b.0-3/input1"
    ATTRS{name}=="Logitech USB Receiver"


```

So I changed my xorg.conf file to the following:

```

Section "InputDevice"
    Identifier      "Configured Mouse"
    Driver          "evdev"
    Option         "Device" "/dev/input/mouse1"
    Option	   "Buttons" "12"
    Option         "ZAxisMapping" "4 5 7 6"
    Option         "Emulate3Buttons" "true"
EndSection


```

With this configuration, xev mapped the forward back buttons to eight and nine but they don't work in firefox or nautilus and the cruise buttons don't work at all

I also tried to get evdev to recognize the mouse a few other ways without success:

```

Option		"Phys" "usb-0000:00:0b.0-3/input1"

```

After all this, I could still not get the forward / back buttons to work so i tried xbindkeys to no avail.

~/.xbindkeys:

```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]""
   b:8
   
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]""
   b:9

```

---

### Post by jrib on 2007-08-28
when you run 'xev' and press your buttons in the box does xev notice (you get output with a button #)?

---

### Post by thefutoneng on 2007-08-29
For the side buttons yes, 8 and 9

---

### Post by Lapino on 2007-09-02
> **isecore said:**
> Hi all. I'm just wondering if anyone has a solution to the fact that Ubuntu reassigns the buttons after every reboot when using the evdev driver?

Before following this guide I had most of the things working on my own, but felt that I needed the tilt-scrollerthing and followed the guide. Now, every time (admittedly not that often, but it happens) I reboot the buttons get shuffled around, and some things end up not even being buttons!

Any hints and pointers?

**EDIT: Never mind, I was just being stupid.**

Well, then I'm being stupid too, because I have the same problem. How did you fix it?

---

### Post by isecore on 2007-09-02
> **Lapino said:**
> Well, then I'm being stupid too, because I have the same problem. How did you fix it?

I didn't really fix it. I still have the issue that buttons get shuffled around at each boot. I just accepted that I'd have to do a small edit of my xbindkeysrc file. But as for the random buttons, I have no idea. My tilt-scroller doesn't work either, but I accept that since I hardly ever use it.

---

### Post by Lapino on 2007-09-02
> **isecore said:**
> I didn't really fix it. I still have the issue that buttons get shuffled around at each boot. I just accepted that I'd have to do a small edit of my xbindkeysrc file. But as for the random buttons, I have no idea. My tilt-scroller doesn't work either, but I accept that since I hardly ever use it.

I'll start fiddling with my xbindkeysrc to then :)
Although I'm not sure if it's entirely the same issue I have: sometimes, the tiltwheel works, and the sidebuttons are 8 and 9; sometimes the tiltwheel doesn't work, and then the side buttons are 6 and 7. So the part of the side buttons getting remapped seems logic, since there are less buttons in the second case. So the problem is actually why the tiltwheel is detected sometimes and sometimes not. Any ideas?

---

### Post by isecore on 2007-09-02
> **Lapino said:**
> I'll start fiddling with my xbindkeysrc to then :)
Although I'm not sure if it's entirely the same issue I have: sometimes, the tiltwheel works, and the sidebuttons are 8 and 9; sometimes the tiltwheel doesn't work, and then the side buttons are 6 and 7. So the part of the side buttons getting remapped seems logic, since there are less buttons in the second case. So the problem is actually why the tiltwheel is detected sometimes and sometimes not. Any ideas?

Nope, sorry. No ideas how to remedy it. What you describe is exactly what happens to me. I just re-edit the .xbindkeysrc file after each reboot (if it doesn't work) and this is semi-okay since I rarely reboot.

---

### Post by quicksilver1024 on 2007-09-06
Hi,

My side buttons don't work! When I run 'xev' to see what button numbers are the side buttons, it doesn't give me any button number. Instead it gives me this:

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  4294967291 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

Also, my sensitivity level changed. I try to change it back in Preferences>Mouse but the effect isn't taking place.

Help?

EDIT: I take it all back. After restarting Firefox it works!
Except for the sensitivity issue. Can anyone help?

---

### Post by Lapino on 2007-09-29
This tutorial worked mostly for me while I had a Cordless Click! Plus mouse. Now I had to change and I now have a MX1000, but I have some problems with the tilt wheel. When I press it, xev returns that "button 14" is pressed while I hold the tilt wheel in the left or right button, and when I release it, it first sends "button 13" and then "button 14" again. With xbindkeys turned off, horizontal scrolling doesn't work at all. When xbindkeys is running, it results in some small movement, but mostly erratic and in different directions (not consistent in the direction I push the button). When checking in xev with xbindkeys running, it reports "button 6", "button 13" and then "button 14" or "button 7", "button 13" and "button 14", dependent on direction.

My settings are as described in the tutorial. 

Anyone recognise this behaviour or know how to solve it? Maybe it's related to gutsy, although I doubt it, as my Cordless Click did work in gusty with the same settings.

---

### Post by Bazirker on 2007-09-29
Speaking of Gutsy, what are people's experiences with this mouse using Gutsy?  I recall a lot of people saying they started having a bunch of problems with their MX1000 when they upgraded to Feisty from Edgy.  Why in hell is mapping input as simple as mouse buttons so difficult?

---

### Post by Lapino on 2007-09-30
Well, except from the problem I described above, the mouse works perfectly in gutsy for me, with modifications from the tutorial made.

---

### Post by NobeyamaGP on 2007-10-01
Ok, I've been using Kubuntu Feisty with my MX1000 for a while now and I have all the buttons working except the tilt-wheel. At first I thought it was a problem with firefox, but it doesn't work anywhere on the system. I have tried the tutorial as posted and that got all buttons working except side scroll. However, according to xev, my left and right scroll buttons are buttons 13 and 14 respectively. And the xorg.conf line ```
Option          "HWHEELRelativeAxisButtons" "7 6"
``` apparently doesn't work. I've even tried changing it to read ```
Option          "HWHEELRelativeAxisButtons" "14 13"
``` but that maps the side scroll buttons to what i have my "cruise control" buttons doing and those buttons no longer do anything. However, my cruise control buttons are mapped to 11 and 12, not 13 and 14. Also when I change this line, my browser left and right buttons are mapped to 6 and 7, my up cruise control is mapped to  10 which is by browser back button and my cruise down is mapped to my application switcher button which is button 8. In other words, everything gets messed up. Any ideas? Thanks.

---

### Post by SlowRedFox on 2007-10-02
I've read through a good deal of this thread, but I'm still struggling to get my mouse to work... I'm a relatively new user to linux so a lot of this is beyond me. I have the mx1000/mx5000 bluetooth combo. I've read that many people have troubles with their keyboard after setting up the mouse, but I'm not worried at this stage, as I can't get even that far.

On Feisty, cat /proc/bus/input/devices outputs two devices connected by the bluetooth receiver:

```
I: Bus=0003 Vendor=046d Product=c70e Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:0a.0-1.2/input0
S: Sysfs=/class/input/input7
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70a Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:0a.0-1.3/input0
S: Sysfs=/class/input/input8
H: Handlers=kbd mouse1 ts1 event3 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 fff0001 f80 8807c000 667bfa d941dfed 9e0000 0 0 0
B: REL=143
B: ABS=1 0

```

I'm assuming that the mouse is the second device because it has mouse1 listed as a handler... Is this right?

I followed the instructions in the wiki, but X will not start because of the identically named devices.

So then I added a udev rule to /etc/udev/rules.d/60-symlinks.rules:

> **Bourlotieris said:**
> 
```
BUS=="usb", SYSFS{product}=="Logitech BT Mini-Receiver", SYSFS{idProduct}=="c70c", SYMLINK+="input/mx1000"
```


I changed the rule to address the device I suspect is the mouse (c70a), then changed the mx1000 section in xorg.conf with
```
Option "Device" /dev/input/mx1000
``` as was suggested:
> **_jason said:**
> I think it should be  Option "Device", not  Option "Name".  Also, I used to use "/dev/input/mx1000" but try your way too and see if it works.

After restarting udev, the symlink in /dev/input is created. However, X crashes when it is restarted with a "Preinit returned NULL for "Logitech MX1000" error. Also, in the detailed output, it has "No default mouse found. Adding one."

I notice that while the udev rule has "Logitech BT Mini-Receiver", cat /proc/bus/input/devices shows it as a"Logitech Logitech BT Mini-Receiver". Is this because cat /proc/bus/input/devices concatenates the manufacturer and the device name, and so the name of the device is actually "Logitech BT Mini-Receiver", or should the udev rule have "Logitech Logitech BT Mini-Receiver" instead?

---

### Post by Cris987 on 2007-10-02
Does this work for VX Revolution?

---

### Post by jhoe on 2007-10-09
Virgin post!

I am having difficulty with with a VX Revolution.
Hopefully you can bear with me, as Ubuntu was just installed 2 days ago and this would be my first time using Linux (since I was 12 and tried RedHat, failing miserably :) )

HP Pavilion dv2125nr
1gb Ram
Ubuntu FF 7.04 April Release


My problem is that I cannot get the 'Sideways Scroll' or 'Zoom' to be recognized.  
By using xev, I find:
button1 = left click
button2 = scroller click
button3 = right click
button4 = scroll up
button5 = scroll down
button8 = what would normally be 'page back'
button9 = what would normally be 'page forward'
key 122 = 'find' / 'magnifind glass' button
Xev will not pickup the zoom in or out.  Nor will it pick up the 'right' or 'left' 'sideways scroll'

I attempted to follow daou's walk though (thanks!), of "HOWTO: Logitech MX Revolution in Dapper".   (Thread 277388)

From this walk through I found:

cat /proc/bus/input/devices
```

I: Bus=0003 Vendor=046d Product=c521 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:0b.0-6/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse1 event2 ts1 
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c521 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:0b.0-6/input1
S: Sysfs=/class/input/input5
H: Handlers=kbd event3 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 1 f80 8807c000 667bfa d9415fed 8e0000 0 0 0
B: REL=40
B: ABS=1 0
```

gedit /etc/udev/rules.d/19-local.rules
```
KERNAL=="event2", SYSFS{../name}=="Logitech USB Receiver", SYSFS{../phys}=="usb-0000:00:0b.0-6/input0", NAME="input/VXR"
```

xorg.conf
```
Section "Module"
........
    Load           "evdev"
    Load	   "mouse"
EndSection

#Attempting to use evdev
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
#Attempting to fix a problem with no default mouse found, when CorePointer is added, X will not boot
#   Option         "CorePointer"
    Option         "Device" "/dev/input/VXR"
#Following this, was added to attempt to make side scrolling work, DIDN'T WORK!
    Option         "Protocol" "auto"
    Option         "Emulate3Buttons" "false"
    Option         "Buttons" "11"
    Option         "ButtonMapping" "1 2 3 9 8 6 7 13 14"
    Option         "ZAxisMapping" "4 5"
EndSection

#Section "InputDevice"  #attempt to use 'mouse' driver
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device" "/dev/input/VXR"
#	Option		"Protocol" "ExplorerPS/2"
#	Option		"Emulate3Buttons" "false"
#	Option		"Buttons" "11"
#	Option		"ButtonMapping" "1 2 3 9 8 6 7 13 14"
#	Option		"ZAxisMapping" "4 5"
#EndSection
```


I have found that some people are using Driver "mouse' instead of "evdev".  I am still unsure of which one to be using.  I just recently learned the use of nano (what a life saver if X won't load!).  Perhaps I am missing something simple?  I tried configuring the mouse to use the commented out 'attempt to use 'mouse driver'.

If something did not load properly, I have been using root then editting the error with nano, then /etc/init.d/udev restart /etc/init.d/gdm restart to attempt after I have tried to fix the error.  I think I have spent about 2 days on this now (running out of adderall!)

Steps followed
```
su
nano /etc/X11/xorg.conf
fix problem (or so I think)
(ctrl x in nano, overwrite with changes)
/etc/init.d/udev restart
/etc/init.d/gdm restart

```
The way I am editting would not effect this correct?

Any help is appreciated, thanks!

---

### Post by ktulu1115 on 2007-10-10
Hello,

First I must say excellent tutorial.  I initially set everything up for my Feisty install and had my scrollwheel tilt left and right working perfectly with firefox mapped to back & forward.  

However, I rebooted my machine the other day and now it doesn't seem to be working anymore.  Additoinally xmodmap -pp returns:

```
(ktulu@eternal:pts/0)-(8/15 @ 512k)-(05:16 PM)
~$ xmodmap -pp
There are 7 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              4
        5              5
        6              6
        7              7

```

I try running xev and get no output for the last 3 buttons (tilt wheel left, right, and that small middle application button on the left side of the mouse)

My relevant sections of xorg.conf:

```

(ktulu@eternal:pts/0)-(8/15 @ 512k)-(05:24 PM)
~$ cat /etc/X11/xorg.conf | grep -C 4 evdev
#EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Buttons"       "12"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection
```

I added the "Buttons" line in there for some trial & error debugging but to no avail.

Upon further investigation it looks like I have the same issue as tjbk_tjb is:

> **tjbk_tjb said:**
> I'm having a problem.
When I run anything, it doesn't respond to the side scroll or the switch application buttons. And only 7 buttons are being reported by xmodmap.
I executed "cat /dev/input/mouse1| hexdump" on tty1 and saw a bunch of hexadecimal come out when I moved the mouse or pressed the buttons. But nothing came out when I pressed the side scroll or switch application buttons.

My mouse configuration section in xorg.conf (after a lot of messing around):
```
Section "InputDevice"
 Identifier "Logitech MX1000"
 Driver     "evdev"
Option "Buttons" "12"
# Option     "CorePointer"
# Option     "Device"    "/dev/input/mx1000"
Option      "Name" "Logitech USB Receiver"
Option          "ZAxisMapping"          "11 12 10 9"
EndSection
```

Any suggestions?? :confused:

---

### Post by Aletheos on 2007-10-11
Same thing here. Only 7 buttons found.
No middle, scroll left/right, fast scroll up/down or application(I used as middle)

My /etc/X11/xorg.conf
```

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        # I tried the HWHEELRelativeAxisButtons-line already
	Option		"ZAxisMapping"	"11 12 10 9"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Albatron Geforce 4 Ti 4200 P Turbo "
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"LG Flatron L1715S"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Albatron Geforce 4 Ti 4200 P Turbo "
	Monitor		"LG Flatron L1715S"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice     "Logitech MX1000" "CorePointer"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

My ~/.xbindkeysrc
```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"echo ButtonRelease 10 ButtonPress 3 ButtonRelease 3 | xmacroplay -d 0 :0.0"
  b:10
"echo ButtonRelease 11 ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonRelease 12 ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonRelease 13 ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonRelease 14 ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14

```
What does all those numbers mean? How does this bind my mouse buttons?

---

### Post by oltr3m on 2007-10-21
I'm using Logitech MX3100 desktop set on Ubuntu GG 7.10
I have tried to configure the MX1000 mouse with evdev so I can use all my buttons but everytime X fails to start.
i followed the guide [https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)

the output of *cat /proc/bus/input/devices* is:
```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c512 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:0a.0-2/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=ff1f

I: Bus=0003 Vendor=046d Product=c512 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:0a.0-2/input1
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd mouse1 event3 
B: EV=20007
B: KEY=7fffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 0 1878 d800d100 1e0000 0 0 0
B: REL=143
B: LED=ff00

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

```

Any idea what is wrong, or what should be done different?

---

### Post by pwrstick on 2007-10-21
Any more user experience for Gutsy users?

Currently I have only the 1 and 3 buttons working.  After following the tutorial I lost my scroll wheel... Honestly all I want is the scroll wheel, buttons 1 and 3, and the thumb buttons for forward and back.

I don't _need_ all 12 buttons, but would certainly like more than 2!

EDIT: Also noticed a Macintosh Mouse from the cat:
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

Weird?

---

### Post by ktulu1115 on 2007-10-22
Havn't tried messing with this yet....  did fresh install of Gusty on release day and havn't had time to configure.  But I'll post my results as soon as I do.

---

### Post by sgleo87 on 2007-10-22
> **pwrstick said:**
> Any more user experience for Gutsy users?

Currently I have only the 1 and 3 buttons working.  After following the tutorial I lost my scroll wheel... Honestly all I want is the scroll wheel, buttons 1 and 3, and the thumb buttons for forward and back.

I don't _need_ all 12 buttons, but would certainly like more than 2!

EDIT: Also noticed a Macintosh Mouse from the cat:
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

Weird?
Yeah, I also noticed that it says Macintosh mouse button emulation now...
Some of my buttons of my MX1000 have stopped working in Gutsy also...my left and right button work as well as my back and forward buttons and the middle click and mousewheel scroll but the middle side button and the tilt wheel buttons do not work anymore; I just did an upgrade to gutsy, not a fresh install, so I my xorg.cong and .xbindkeysrc are still the same...anyone have a fix for this?

---

### Post by limplenny on 2007-10-28
I have a fresh install of gusty and managed to get it to work quite easily. I should note that I use my mx1000 through ps2. I'm not a very experienced user but I can post what i did:


basically i followed this thread:
[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

but added to the "InputDevice" section of xorg.conf:
```
Option		"HWHEELRelativeAxisButtons" "7 6" 
``` because the horizontal scroll buttons were switched


I did not have to install click since my cruiser buttons are working, just cruising at very low speeds.  (So i didn't have to follow *2. Fixing the cruise control buttons (MX500, MX510, MX700, MX1000)* in the thread linked above)

afterwards, all I had to do was set the three options in firefox' about:config:
**mousewheel.horizscroll.withnokey.action** to 0
**mousewheel.withcontrolkey.sysnumlines** to true
and becuase the middle button annoyed me:
**middlemouse.contentLoadURL** to false

hope it helps someone :) 
lennard

---

### Post by Chuchumm on 2007-10-29
First of all, I am new to linux and this is my first post.

 have the mouse/keyboard combo and when i run /proc/bus/input/devices, I get 

```

I: Bus=0003 Vendor=046d Product=c70e Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:02.0-4.2/input0
S: Sysfs=/class/input/input3
U: Uniq=0007617084B9
H: Handlers=kbd event3 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70a Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:02.0-4.3/input0
S: Sysfs=/class/input/input4
U: Uniq=0007617084B9
H: Handlers=kbd mouse2 event4 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 fff0001 f80 8837c000 667bfa d941dfed 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0
I: Bus=0003 Vendor=046d Product=c70e Version=0111

I: Bus=0005 Vendor=046d Product=b003 Version=4310
N: Name="Logitech Bluetooth Mouse"
P: Phys=00:07:61:70:84:B9
S: Sysfs=/class/input/input8
U: Uniq=00:07:61:64:D4:14
H: Handlers=mouse3 event8 
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0005 Vendor=046d Product=b305 Version=4502
N: Name="Logitech Bluetooth Keyboard"
P: Phys=00:07:61:70:84:B9
S: Sysfs=/class/input/input11
U: Uniq=00:07:61:66:19:2E
H: Handlers=kbd event9 
B: EV=12000f
B: KEY=7fff 2c3027 bf004440 0 0 1 10f80 8837c007 ffe67bfa d941dfff febeffdf ffefffff ffffffff fffffffe
B: REL=40
B: ABS=301 0
B: LED=1f

N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```



I gathered that my mouse was either the second or third section, and since the third one doesn't have the usb-xxxxxxxxxxxxx/input# i used the second one.  My problem is that after restarting, my screen resolution in 800x600 and i can only change it to 640x480.  Also the buttons don't change function at all.

Additionally, does anyone know how to change the display on the keyboard?

I should mention that I'm using Gutsy.

---

### Post by plush_cthulhu on 2007-11-02
I think i have the exact same problem as ktulu1115 and Aletheos.
Sometimes only 7 mouse buttons are found, and rebooting the PC a couple of times solves the problem !
Restarting udev or Xorg doesn't make any difference, only rebooting the PC entirely.

Of course, the next day, you have a very good chance of ending up with 7 buttons again.

I had this problem in Feisty and I was kind of hoping it was a bug and would go away in Gutsy, but it's still here :(


```
$ xmodmap -pp
There are 7 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              4
        5              5
        6              6
        7              7
```

```
I: Bus=0003 Vendor=046d Product=c50e Version=2500
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd mouse1 event3 
B: EV=7
B: KEY=1f0000 0 100 38 c0000000 c0000 0 0 0
B: REL=103
```

```
Section "InputDevice"
    Identifier     "Logitech MX1000"
    Driver         "evdev"
    Option         "Name" "Logitech USB Receiver"
EndSection
```

adding "buttons" in xorg.conf doesn't do anything to help.
As I said, after some system starts, everything works perfect with this config.
I reckon i have about a 50% chance when booting the PC, everything will be fine.

Edit: I have now rebooted, and i've got all mouse buttons again
/proc/input/devices now looks like this:
```
I: Bus=0003 Vendor=046d Product=c50e Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=20007
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: LED=ff00
```

all buttons seem to be working when the mouse is event2. they don't work when it is event3. The EV= line has also changed, but I don't know what that means.
xmodmap -pp reports 20 buttons (not all work, of course, but the ones physically on the mouse, do ;) )

---

### Post by plush_cthulhu on 2007-11-02
> **Chuchumm said:**
> my screen resolution in 800x600 and i can only change it to 640x480.  Also the buttons don't change function at all

....

I should mention that I'm using Gutsy.

Most likely you have an error in xorg.conf or you've misconfigured something so that Xorg can't start properly. What you're seeing now is Xorg 'Safe Mode' (a new feature in Gutsy) designed to show you a limited X server when otherwise you'd be in a terminal with no browser access to help fix your problem.

Try reverting back to your old xorg.conf. (You backed it up, right ;) )

---

### Post by TwiztidSinz on 2007-11-03
Recently I started playing with Linux, tried a few versions out and fell in love with Kubuntu.
I'm still new to Linux in general, but fairly competent with computers and can figure out most stuff on my own and typically what I cannot figure out on my own, I ask my good friend [www.Google.com](www.Google.com) to help me with.

I am using a Logitech MX5000 Keyboard and MX1000 Mouse bluetooth combo, aside from a somewhat minor connection issue (When I load the desktop, I have to unplug the bluetooth dongle for a few seconds then plug it back in, after that everything works fine and I'm able to type and move my mouse so that I can log in) and the problem mentioned here they work well enough.
I have no 'real' use of the Forward, Back or Document Flip buttons, they have incorrect functionality:
Forward: Same effect of Right Click.
Back: Vertical Scroll Icon (the Icon that stays on the screen and scrolls in the direction of the mouse)
Document Flip: Same as the Back button.

Both Google and the Kubuntu Wiki brought me to this page: [https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)
I followed the instructions exactly but it will not work for me.
As Kubuntu is loading, it stops at:```
* Running local boot scripts (/etc/rc.local)                 [ OK ]
```Rebooting and restoring the original copy of the file lets me into the desktop again.

Output from "cat /proc/bus/input/devices":```
I: Bus=0003 Vendor=046d Product=c70e Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1d.1-1.2/input0
S: Sysfs=/class/input/input7
U: Uniq=00076147D892
H: Handlers=kbd event3
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70a Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1d.1-1.3/input0
S: Sysfs=/class/input/input8
U: Uniq=00076147D892
H: Handlers=kbd mouse1 event4
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 fff0001 f80 8837c000 667bfa d941dfed 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0
```

EDITED FILE (Fails to load desktop):```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech Logitech BT Mini-Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
#        Option		"Dev Phys"	"usb-0000:00:1d.1-1.3/input0"
EndSection
================================================================================
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Logitech MX1000" "CorePointer"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```I added the line "**Option		"Dev Phys"	"usb-0000:00:1d.1-1.3/input0"**" from the Breezy Badger section in hopes of solving the failure to load problem and/or the connection problem, but there is no (visible) change between **not** having it, having it and having it commented out.

ORIGINAL FILE (Loads desktop with no issue):```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
================================================================================
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

One thing I noticed was my Edited code has spaces rather than tabs (from copy/pasting from the web), though replacing the spaces with tabs doesn't seem to change anything.

While reading I came across [this post](http://ubuntuforums.org/showpost.php?p=556733&postcount=15). The instructions to add the "**Option          "Device"                "/dev/input/event1"**" line are under the Breezy Badger section so I did not follow them initially. When I tried them just a moment ago, I saw that according to "**cat /proc/bus/input/devices**" my Handlers= had changed to:```
H: Handlers=kbd event2
H: Handlers=kbd mouse1 event3
``` for the Keyboard and Mouse respectively after reboot (they don't seem to change when I unplug/plug in the bluetooth dongle -while the desktop is loaded-)



Thanks in advance for any help/advice :-D
~Jeff

P.S.
I had originally been using 7.04 upgraded to the 7.10 test/beta a few weeks back under VMWare under Windows Vista. After the official release of 7.10 I tried it using a clean install (still under VMWare) and I had noticed some issues that were not present in the 7.04->7.10, though they were fairly minor and I didn't really think much of them, partially attributing them to the fact that it was running on a virtual machine. Now I am running Kubuntu as an install OS (Dual booting with Vista) and I'm still noticing the issues (e.g. run "**sudo dolphin**" or "**kdesu dolphin**", close it, then run a normal instance of dolphin and close it. You'll get a bookmark error and will have to change the permissions/ownership of the .xml file back to your user)
Would I be better off cutting my losses, stop progressing with this current install and formatting then installing 7.04 and upgrading to 7.10? or even just staying with 7.04?

---

### Post by b4t3m4n on 2007-11-04
I am having a little trouble here.  What I want to do is map one of the side buttons on my MX518 to just ALT (left or right, doesn't matter), or CNTRL.  In windows, I can do this using the logitech tools, and then I can use that to map an entire set of keys for WoW without having to actually hitting a modifier key on my keyboard, just hit the side mouse button which is cntrl or alt.  

I am using btnx, and binding just ALT to it seems to work in Gnome, but doesn't work quite right in WoW.  At first it doesn't register, and after I pound it a few times in anger, it registers, but sticks on, which is no good either.

Any suggestions?

---

### Post by tweedledee on 2007-11-05
> **b4t3m4n said:**
> I am having a little trouble here.  What I want to do is map one of the side buttons on my MX518 to just ALT (left or right, doesn't matter), or CNTRL.  In windows, I can do this using the logitech tools, and then I can use that to map an entire set of keys for WoW without having to actually hitting a modifier key on my keyboard, just hit the side mouse button which is cntrl or alt.  

I am using btnx, and binding just ALT to it seems to work in Gnome, but doesn't work quite right in WoW.  At first it doesn't register, and after I pound it a few times in anger, it registers, but sticks on, which is no good either.

Any suggestions?

Look in this thread: [http://ubuntuforums.org/showthread.php?t=316441](http://ubuntuforums.org/showthread.php?t=316441)
Especially this post: [http://ubuntuforums.org/showpost.php?p=1884420&postcount=6](http://ubuntuforums.org/showpost.php?p=1884420&postcount=6)
And to limit your changes to WoW only, you may want to look here: [http://ubuntuforums.org/showthread.php?t=380927](http://ubuntuforums.org/showthread.php?t=380927)

---

### Post by HessiaNerd on 2007-11-05
> **TwiztidSinz said:**
> 
I am using a Logitech ... MX1000 Mouse..., 

Both Google and the Kubuntu Wiki brought me to this page: [https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)
I followed the instructions exactly but it will not work for me.
As Kubuntu is loading, it stops at:```
* Running local boot scripts (/etc/rc.local)                 [ OK ]
```Rebooting and restoring the original copy of the file lets me into the desktop again.
....

same issue here.

Can someone update the howto for gutsy 7.10
TIA

---

### Post by grantjohnston on 2007-11-09
> **plush_cthulhu said:**
> I think i have the exact same problem as ktulu1115 and Aletheos.
Sometimes only 7 mouse buttons are found, and rebooting the PC a couple of times solves the problem !
Restarting udev or Xorg doesn't make any difference, only rebooting the PC entirely.

Of course, the next day, you have a very good chance of ending up with 7 buttons again.

I had this problem in Feisty and I was kind of hoping it was a bug and would go away in Gutsy, but it's still here :(


```
$ xmodmap -pp
There are 7 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              4
        5              5
        6              6
        7              7
```

```
I: Bus=0003 Vendor=046d Product=c50e Version=2500
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd mouse1 event3 
B: EV=7
B: KEY=1f0000 0 100 38 c0000000 c0000 0 0 0
B: REL=103
```

```
Section "InputDevice"
    Identifier     "Logitech MX1000"
    Driver         "evdev"
    Option         "Name" "Logitech USB Receiver"
EndSection
```

adding "buttons" in xorg.conf doesn't do anything to help.
As I said, after some system starts, everything works perfect with this config.
I reckon i have about a 50% chance when booting the PC, everything will be fine.

Edit: I have now rebooted, and i've got all mouse buttons again
/proc/input/devices now looks like this:
```
I: Bus=0003 Vendor=046d Product=c50e Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=20007
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: LED=ff00
```

all buttons seem to be working when the mouse is event2. they don't work when it is event3. The EV= line has also changed, but I don't know what that means.
xmodmap -pp reports 20 buttons (not all work, of course, but the ones physically on the mouse, do ;) )

My god, I thought I was the only person that had that problem. Sometimes it only has 7 buttons, and other times it actually has 20.

I fixed this by doing a fresh install and so far after a week of playing with it, it seems to work very well. 

What you need to do if you dont' want to do a re-install instead of rebooting, edit your ~.xbindkeysrc and instead of having buttons 8 & 9  doing your forward and back, it uses buttons 6 & 7.

Save your changes, then do:

```
killall xbindkeys && xbindkeys
```

and it should fix it for that reboot. Upon your next reboot, if you find that you have 20 buttons instead of 7, change 6 & 7 in your .xbindkeysrc from 6 & 7 to 8 & 9.

Hope that helps


Grant

> **plush_cthulhu said:**
> Most likely you have an error in xorg.conf or you've misconfigured something so that Xorg can't start properly. What you're seeing now is Xorg 'Safe Mode' (a new feature in Gutsy) designed to show you a limited X server when otherwise you'd be in a terminal with no browser access to help fix your problem.

Try reverting back to your old xorg.conf. (You backed it up, right ;) )


I dealt with that problem for over a year and to over 3 versions of Ubuntu, everything from after breezy, IIRC, there is no fixing it. I did a fresh install of Gutsy this time around and it works perfectly, other than my horiz. scroll being backwards. Anyone have any idea on how to fix that? I've tried messing with some settings and can't seem to get it to work

---

### Post by Bejje on 2007-11-10
Does anyone have a complete guide  on how to set up a MX1000 in Gutsy on a clean install? Would be much appreciated.

// Bejje

---

### Post by ktulu1115 on 2007-11-10
Well I managed to get mine working.  After the fresh Gutsy install, following the doc worked just fine for me (20 buttons detected, xev working, etc)

This is what I ended up using for .xbindkeysrc:

```
#"/usr/bin/xvkbd -xsendevent -text "\[Control]\[Prior]""
#m:0x0 + b:4
#"/usr/bin/xvkbd -xsendevent -text "\[Control]\[Next]""
#m:0x0 + b:5
#"/usr/bin/xvkbd -xsendevent -text "\[Page_Up]""
#  b:4
#"/usr/bin/xvkbd -xsendevent -text "\[Page_Down]""
#  b:5
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  b:9
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[w]""
  b:10
"echo ButtonRelease 11 ButtonPress 4 ButtonRelease 4 | xmacroplay -d 0 :0.0"
  b:11
"echo ButtonRelease 12 ButtonPress 5 ButtonRelease 5 | xmacroplay -d 0 :0.0"
  b:12
"echo ButtonRelease 13 ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
  b:13
"echo ButtonRelease 14 ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
  b:14
```

As you can see I was trying to get my buttons 4 & 5 to work as page up/down in firefox but couldn't get it working.  Either it acts just like the wheel scrolling one line per press, or doesn't work at all and all my other apps get screwy with the main scroll wheel.

Not a biggie, just wanted to let everyone know the stock instructions worked for me on Gusty.

---

### Post by Neverest on 2007-11-11
Thank you for this walkthrough! I love these cut-and-paste guides. =) 
I followed the wiki on my fresh Gutsy install and most buttons respond. Having trouble with the wheel button, but I think that's because of age and wear rather than software... 

I'm having trouble setting up the middle thumb button, though. It works as the cruise control down button... I tried 

Code:
"/usr/X11R6/bin/xvkbd -text "\[Enter]""
   b:10

and Code:
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Enter]""
   b:10

with and without /X11R6/ in the .xbindkeysrc, obviously wanting my middle thumb button to act as Enter key. Tried Delete also, but it continues to work as the cruise control down button, except it doesn't speed up if I hold it in. 

Any suggestions?
Couldn't we all send an email to Logitech and push them to support linux in their own software? :)

And about the wiki: It would be good to have some suggestions on codes to use if you want to set up your buttons in another way. For example setting a button as "Enter" or whatever. For us newbies that still get tired of all these lines of code that we don't understand. :) This was easy in windows with Logitech software...
Thanks again!

---

### Post by patsissons on 2007-11-13
Does anyone have a solution for the 7 button issue that doesn't require a fresh install?  

Here are some of my (possibly) relevant device nodes from /proc/bus/input/devices
```

I: Bus=0003 Vendor=046d Product=c50e Version=2500
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:0b.0-1/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd mouse1 event3
B: EV=7
B: KEY=1f0000 0 100 38 c0000000 c0000 0 0 0
B: REL=103

```

And then the list of handlers from /proc/bus/input/handlers

```

N: Number=0 Name=kbd
N: Number=1 Name=mousedev Minor=32
N: Number=2 Name=evdev Minor=64

```


EDIT: Restarted, got my 20 buttons back.  Before I restarted, I Installed lomoco package, then added lomoco -8 --no-sms to startup
Not sure if that made the diff, but it definitely didn't hurt.  used update-rc.d <script> defaults to add it to startup.

```

I: Bus=0003 Vendor=046d Product=c50e Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:0b.0-1/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=mouse1 event2
B: EV=20007
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: LED=ff00

```

```

N: Number=0 Name=kbd
N: Number=1 Name=mousedev Minor=32
N: Number=2 Name=evdev Minor=64

```

hopefully someone can shed some light on this problem, it is really annoying!

---

### Post by TalioGladius on 2007-11-16
Will this work for a fresh Gutsy install?

---

### Post by grantjohnston on 2007-11-19
> **patsissons said:**
> Does anyone have a solution for the 7 button issue that doesn't require a fresh install?  


hopefully someone can shed some light on this problem, it is really annoying!

Not that I can find. I will say, it was worth it, though.. However, I was having quite a few issues with my Feisty box. Random freezes, plenty of other issues as well.

> **TalioGladius said:**
> Will this work for a fresh Gutsy install?

Yes it will, and it works wonderfully :)

---

### Post by grantjohnston on 2007-11-19
Okay, disregard my posts about this being fixed with a fresh install.



[SIZE="7"]It doesn't.[/SIZE]



It would also appear that when it only finds 7 buttons instead of all 20 my keyboard map FUBARS. My arrow keys get screwed. When you hit the down arrow, it acts like I'm hitting enter. If my numlock is off, then the 8, 4, 6, and 2 keys act as arrow keys, and my return key on the number pad doesn't work. I kept rebooting until all of the buttons read. 



I **REALLY** don't want to have to deal with this again. Anyone know a fix for it? It also seems that the keymap doesn't mess up until I'm done logging in, and X loads, because I can type in my password and hit enter (The keypad one) and it will log me in, but once X loads it messes up.


Anyone have any clues?

---

### Post by bat266 on 2007-11-27
i've followed all instructions now and i have the problem that i have 2 devices with name logitech receiver. The tutorial said i should reply here so here i am ;)

Could someone help me with this problem

---

### Post by grantjohnston on 2007-11-27
> **bat266 said:**
> i've followed all instructions now and i have the problem that i have 2 devices with name logitech receiver. The tutorial said i should reply here so here i am ;)

Could someone help me with this problem


Do you have anything else that's wireless and Logitech? That's what I'm thinking it would be. Keyboard, etc.



Anyway, if you'd post your output of /proc/bus/input/devices it would give us a bit more help and more of an idea of which it might be.


Later


Grant

---

### Post by bat266 on 2007-11-27
> **grantjohnston said:**
> Do you have anything else that's wireless and Logitech? That's what I'm thinking it would be. Keyboard, etc.



Anyway, if you'd post your output of /proc/bus/input/devices it would give us a bit more help and more of an idea of which it might be.


Later


Grant
no nothing only the mx1000 mouse don't understand it either

---

### Post by NullHead on 2007-11-27
> **_jason said:**
> Well it took a few weeks of scouring the internet for clues before I finally got my mx1000 to work just like I expected it to, but I finally did it. The howto is available on the wiki at the following url: 

[https://wiki.ubuntu.com/MX1000Mouse](https://wiki.ubuntu.com/MX1000Mouse) .

Let me know if it works for you.  I welcome any and all questions and comments.  Even if you don't like the way a particular sentence sounds, let me know :D

The howto is a product of several small changes I made over several weeks as I tried to get all 12 buttons to function correctly during my spare time so I may have forgotten to include a detail or two (I hope not).  Sorry if I did, but I'm sure we can figure it out.  Just post any problems you are having.

Does this work for gutsy 7.10 ?

---

### Post by NullHead on 2007-11-27
:lolflag: Never mind I figured it out for myself! 

PS: Great guide!!!!!

---

### Post by grantjohnston on 2007-12-09
> **bat266 said:**
> no nothing only the mx1000 mouse don't understand it either

Sorry for the delay on the reply... Did you get it fixed.... If not...



That's odd... Just try both of them... Are they spelled and cased differently?



> **NullHead said:**
> :lolflag: Never mind I figured it out for myself! 

PS: Great guide!!!!!

Good to hear.. Glad you like it :) 



grant

---

### Post by plush_cthulhu on 2007-12-12
> **grantjohnston said:**
> My god, I thought I was the only person that had that problem. Sometimes it only has 7 buttons, and other times it actually has 20.

This obviously is a bug, and it's starting to annoy the hell out of me. Anyone know the right place to report this?

---

### Post by grantjohnston on 2007-12-12
> **plush_cthulhu said:**
> This obviously is a bug, and it's starting to annoy the hell out of me. Anyone know the right place to report this?

Indeed. I'm going to knock on wood here and say it hasn't happened in the past couple restarts.


When it happens to you, does your keyboard map change at all or anything else awkward happen?

My down arrow becomes return and return on the numpad is somehow disabled.


It doesn't do it at the log-in window, however; it's after xfce loads. 


After I type in my password, I hit the down arrow, and it doesn't do anything; when i use the return on the numpad, it logs me in.

---

### Post by Mysticle31 on 2007-12-16
Does it work on bluetooth MX1000s?  I've followed this guide exactly, and with varying degree of modification on different installs.  Still haven't gotten it.

Anyone have luck with their bluetooth MX1000?

---

### Post by plush_cthulhu on 2007-12-26
> **grantjohnston said:**
> 
When it happens to you, does your keyboard map change at all or anything else awkward happen?

No, but I don't have a Logitech keyboard/mouse combo, so my keyboard is connected to PS/2, and the MX1000 receiver is on USB.

Therefore I think my keyboard and mouse are kind of unrelated...

My hardware: Asus P5B/Core2 CPU

What's your hardware and how is your keyboard connected?
Is it one of those Logitech combo's or is it regular USB/PS/2?

PS. I've just inserted a USB 2.0 PCI card in the computer (maybe it's the USB chip on the MB that causes this issue) and i've connected the mouse to one of the ports on it. I'll see how that goes and i'll let you know

---

### Post by r3r3 on 2008-01-02
totally didn t work on Gusty, it messed up my xorg, and wouldn t recognize my video card anymore

---

### Post by Borbus on 2008-01-02
This worked for me in Gutsy. I didn't follow all of the guide because I don't use all of the buttons on my mouse, I mainly wanted the back/forward buttons. But the xorg.conf edit worked fine in Ubuntu 7.10 (using nvidia drivers if that makes any difference).

---

### Post by grantjohnston on 2008-01-03
> **Mysticle31 said:**
> Does it work on bluetooth MX1000s?  I've followed this guide exactly, and with varying degree of modification on different installs.  Still haven't gotten it.

Anyone have luck with their bluetooth MX1000?

Not a clue on that. I don't have a BT one.

> **plush_cthulhu said:**
> No, but I don't have a Logitech keyboard/mouse combo, so my keyboard is connected to PS/2, and the MX1000 receiver is on USB.

Therefore I think my keyboard and mouse are kind of unrelated...

My hardware: Asus P5B/Core2 CPU

What's your hardware and how is your keyboard connected?
Is it one of those Logitech combo's or is it regular USB/PS/2?

PS. I've just inserted a USB 2.0 PCI card in the computer (maybe it's the USB chip on the MB that causes this issue) and i've connected the mouse to one of the ports on it. I'll see how that goes and i'll let you know

I don't have a Logitech combo, either. I've got an HP a1250n 3800+ 64X2. My keyboard is PS/2 and my Mouse is setup via USB.

Did the PCI card work. If so, I'll steal one from one of my graveyard of PCs I have sitting next to me.

> **r3r3 said:**
> totally didn t work on Gusty, it messed up my xorg, and wouldn t recognize my video card anymore

Mind posting your xorg.conf and we can sort it out for ya?



Okay, I've got a new set of issues.


When my PC thinks that my mouse only has 7 buttons, my entire keymap changes on the keyboard (the arrow keys only work on the number pad, and that's ONLY if numlock is turned off, insert, home, delete, end, pg up, pg down, and none of the arrow keys work).

Not only does it only do that, but it seems the printer doesn't want to work half of the time when it has the correct button setup; however, when it has the 7 button setup, the printer always wants to work.


Does any of that make sense?



grant

---

### Post by Curtisc on 2008-01-04
> **Mysticle31]Does it work on bluetooth MX1000s? I've followed this guide exactly, and with varying degree of modification on different installs. Still haven't gotten it.

Anyone have luck with their bluetooth MX1000?[/QUOTE]

I've got mine working, but I didn't do anything special.  However, I tried it a week ago with an ATI card, and xorg wouldn't load.  I kind of forgot about it, and then I got an Nvidia card, and all of a sudden it works.  I'm not sure if that has anything to do with it, but it's the only thing I can think of that's changed.

[QUOTE=grantjohnston said:**
> 
Okay, I've got a new set of issues.


When my PC thinks that my mouse only has 7 buttons, my entire keymap changes on the keyboard (the arrow keys only work on the number pad, and that's ONLY if numlock is turned off, insert, home, delete, end, pg up, pg down, and none of the arrow keys work).

Not only does it only do that, but it seems the printer doesn't want to work half of the time when it has the correct button setup; however, when it has the 7 button setup, the printer always wants to work.


Does any of that make sense?



grant

I have the same weird keymapping thing going on - up arrow = print screen, print screen = delete, delete = nothing... it's pretty weird.  However, right in the middle of typing this post, it started working.  Even more confusing.

Has anyone filed a bug report for this sporadic behaviour?

---

### Post by Curtisc on 2008-01-05
Okay, so I shutdown the computer last night and when I rebooted this morning, the keymap was all off again.  Here's what I did to fix it (don't as why, but it's worked a couple times now)
System -> Preferences -> Keyboard, click on the Layouts tab, then "Choose".  Pick a keyboard layout like "Logitech Cordless Desktop".  Close the window, then go back to it and click on "Restore Defaults" (should be evdev managed keyboard).

---

### Post by tweedledee on 2008-01-05
As experiences with Gutsy seem to be mixed, I'll share what worked for me:

I found the name of the mouse (using cat proc/bus/input/deivces) to be "Logitech USB RECEIVER".  I removed the existing mouse section in xorg.conf and used as described in the guide, except that I did not add the "HWHEEL...." part.  I had 20 buttons, but the tilt wheel was set to back/forward, and the forward/back buttons did nothing, so I used xmodmap to swap the buttons:
xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7 10 11 12 13 14 15 16 17 18 19 20" (8 & 9 are the tilt wheel, 6 & 7 the forward/back).

At this point everything was working except the tilt wheel (horizontal scroll), which I don't use anyway and so didn't bother to configure.  Note that the cruise was working correctly, without highlighting text, and so were the forward/back buttons, so I did not need xmacro or xbindkeys.  (Well, I actually used xbindkeys to map double-left-click to the extra button, but that's not "standard" configuration.)

Those who have posted in the past about having various buttons reversed or "misplaced" may want to consider dropping parts of the guide as I did, as it appears that not all MX1000's are recognized identically in Gutsy.  If it helps explain the difference, mine is bluetooth.

EDIT:
Upon further investigation, while all that I said above is true, I did have to resort to a style closer to the original guide to get forward/back in programs other than Firefox, so used an xmodmap of "pointer = 1 2 3 4 5 7 6 8 9 10 11 12 13 14 15 16 17 18 19 20" (note the switch of 6 & 7, equivalent to the HWEEL command in xorg.conf) and xbindkeys for buttons 8 & 9 back and forward.  Still no need for xmacro because the cruise worked out of the box, and side scrolling now works everywhere by default (except maybe in Firefox, since I don't use it I've not tested).

---

### Post by gurth4ng on 2008-01-06
> **_jason said:**
> Well it took a few weeks of scouring the internet for clues before I finally got my mx1000 to work just like I expected it to, but I finally did it. The howto is available on the wiki at the following url: 

[https://wiki.ubuntu.com/MX1000Mouse](https://wiki.ubuntu.com/MX1000Mouse)

Thx so much for that guide, i finally got my mx1000 to work. i was just wondering, how can i configure the application switch button? i mean the middle round thumb button.

Also, i'm trying to speed up my mouse. Adding
```
Option    "Resolution" "2400"
```
in my etc/X11/xorg.conf didnt do much (it slightly improved the speed but not much iirc). I'm under the impresion that my mx1000 is working on 400cpi, any ideas how i can set it to work at 800cpi?

again thx a lot ;)

---

### Post by singingstars on 2008-01-11
> **grantjohnston said:**
> My god, I thought I was the only person that had that problem. Sometimes it only has 7 buttons, and other times it actually has 20.

I fixed this by doing a fresh install and so far after a week of playing with it, it seems to work very well. 

What you need to do if you dont' want to do a re-install instead of rebooting, edit your ~.xbindkeysrc and instead of having buttons 8 & 9  doing your forward and back, it uses buttons 6 & 7.

Save your changes, then do:

```
killall xbindkeys && xbindkeys
```

and it should fix it for that reboot. Upon your next reboot, if you find that you have 20 buttons instead of 7, change 6 & 7 in your .xbindkeysrc from 6 & 7 to 8 & 9.

Hope that helps


Grant




I dealt with that problem for over a year and to over 3 versions of Ubuntu, everything from after breezy, IIRC, there is no fixing it. I did a fresh install of Gutsy this time around and it works perfectly, other than my horiz. scroll being backwards. Anyone have any idea on how to fix that? I've tried messing with some settings and can't seem to get it to work

Thanks, I have the exact problem and fixed by killing xbindkeys and refresh the ~/.xbindkeysrc

---

### Post by grantjohnston on 2008-01-11
> **singingstars said:**
> Thanks, I have the exact problem and fixed by killing xbindkeys and refresh the ~/.xbindkeysrc

Not a problem!


Hopefully us mx1000 users will get this whole situation fixed so we don't have to go the big end around just to get our ****** mouse to work properly.



I guess we can hope...



grant

---

### Post by Curtisc on 2008-01-23
Just in case anyone is still looking at this thread... Bluetooth users, I figured out what made mine screw up so much: I wasn't actually using Bluetooth mode (I had Bluetooth services disabled in Ubuntu).  The keyboard and mouse were functioning in the legacy mode that allows you to use the keyboard in the bios.  As soon as I configured Bluetooth properly, my keymapping problem went away.

---

### Post by davideciarm on 2008-01-24
hi! i have this problem:
when at start ubuntu assign at mouse "event3" it don't work (xmodmap find only 7 button), but if assign "event2" work greatly (xmodmap find all 20 button!)!

with "cat /proc/bus/input/devices" it returns:

N: Name="Macintosh mouse button emulation"
H: Handlers=mouse0 event0 

N: Name="AT Translated Set 2 keyboard"
H: Handlers=kbd event1 

N: Name="PC Speaker"
H: Handlers=kbd event2 

N: Name="Logitech USB Receiver"
H: Handlers=kbd mouse1 event3 

N: Name="Power Button (FF)"
H: Handlers=kbd event4 

N: Name="Power Button (CM)"
H: Handlers=kbd event5

i have all this devices, but i don't know what are they! i know only keyboard and mouse!
what is pc speacker and macintosh mouse button emulation?

now:
it's possibile to delete an device? for example, remove "Macintosh mouse button emulation"....

or

it's possibile to assign at every boot event2 at "Logitech USB Receiver"

thanks very good at all!

---

### Post by davideciarm on 2008-01-24
hi. i had tryed to resolve...i not had found an very good solution! :mad:

why my evdev work only on event2??? :(

because, at boot my mouse swith event between event2 and event3, switch with PCspeaker.
now, i had disable pc speaker, and mouse go at every boot in event2!

You can stop it forever by simply blacklisting the module. Edit /etc/modprobe.d/blacklist and add this line:

blacklist pcspkr

if you know, how i can set my mouse, every time on event2...thanks! :popcorn::guitar:

---

### Post by davideciarm on 2008-01-24
another news! :(

now, my mouse have everytime event2...but isn't it!!!

if you view, Handlers of mouse contain "kbd"... when it contain kbd not work all button!

i don't know how i can do! please...help me!!!!

thanks very much at all users of this forum!!!:KS

---

### Post by tweedledee on 2008-01-24
> **davideciarm said:**
> another news! :(

now, my mouse have everytime event2...but isn't it!!!

if you view, Handlers of mouse contain "kbd"... when it contain kbd not work all button!

i don't know how i can do! please...help me!!!!

thanks very much at all users of this forum!!!:KS

I believe the "kbd" problem, the 7 vs 20 button problems, and a few other issues, all actually relate to this bug: [https://bugs.launchpad.net/ubuntu/+bug/159824](https://bugs.launchpad.net/ubuntu/+bug/159824).  I've found that when the lmpcm_usb driver is loaded for the mouse, I get 7 buttons, the "kbd" entry, my computer won't standby/hibernate, and various other stability issues.  When it chooses to use the usbhid driver, everything works.  Therefore, try blacklisting the lmpcm_usb driver (add to /etc/modprobe.d/blacklist).  If it works for you, please also post to the bug for launchpad, so that this issue gets addressed instead of ignored.

---

### Post by davideciarm on 2008-01-24
> **tweedledee said:**
> I believe the "kbd" problem, the 7 vs 20 button problems, and a few other issues, all actually relate to this bug: [https://bugs.launchpad.net/ubuntu/+bug/159824](https://bugs.launchpad.net/ubuntu/+bug/159824).  I've found that when the lmpcm_usb driver is loaded for the mouse, I get 7 buttons, the "kbd" entry, my computer won't standby/hibernate, and various other stability issues.  When it chooses to use the usbhid driver, everything works.  Therefore, try blacklisting the lmpcm_usb driver (add to /etc/modprobe.d/blacklist).  If it works for you, please also post to the bug for launchpad, so that this issue gets addressed instead of ignored.

wow!!!! :popcorn:
greatly!!! i had blacklisted it, and now isn't and header of mouse!
now it work very very good!!! i think that i don't need to blacklist pcspeaker. why not write an wiki installation manual this step? to blacklist lmpcm_usb!

what is the module lmpcm_usb?
(and now, what i do in launchpad?)

thanks again!!! greatly!!!! :popcorn::popcorn::lolflag:

---

### Post by tweedledee on 2008-01-24
> **davideciarm said:**
> wow!!!! :popcorn:
greatly!!! i had blacklisted it, and now isn't and header of mouse!
now it work very very good!!! i think that i don't need to blacklist pcspeaker. why not write an wiki installation manual this step? to blacklist lmpcm_usb!

what is the module lmpcm_usb?
(and now, what i do in launchpad?)

thanks again!!! greatly!!!! :popcorn::popcorn::lolflag:

You probably shouldn't need to blacklist the speaker.  Other people have also observed an apparent correlation between which event (2, 3, whatever) the mouse was assigned to and the function, but I believe that's just a side effect of which usb driver was being used.

As for the wiki, I'm reluctant to set up anything there because a) lmpcm_usb should work (it stands for Logitech MediaPlay Cordless Mouse USB (driver)), but I'm not sure why it's having an issue vs usbhid, and b) why this is only an issue in Gutsy (not sure if lmpcm_usb was available in prior versions, or if it just a buggy update, or something else).  Indeed, while the problem is more manifest in Gutsy, it's possible the issue has been around longer (in which case probably blacklisting the driver is the solution), but it may be that for different mice or circumstances it's actually helpful - although I'm inclined to think not, based on other problems I have with it.

Finally, if you go to the launchpad link above, create an account in launchpad, and just post to the bug confirming that blacklisting the driver solved your mouse problems, that will hopefully start to get the developers' attention, as the bug has been open since November but no developers have responded.

---

### Post by doerings-net on 2008-02-02
Thanks tweedledee!

Blacklisting lmpcm_usb seems to have solved the problem of not recognizing all 20 buttons of my MX1000.

:)

---

### Post by teaker1s on 2008-02-02
this is driving me nuts
Belkin F1DA108T OmniView PRO2 Series 8-Port USB/PS2 KVM with mx1000 attached by ps2 adapter.
USB connection to towers.

```
 cat /proc/bus/input/devices
```

I: Bus=0003 Vendor=050d Product=0119 Version=0120
N: Name="Belkin Components USB-PS2 Adapter "
P: Phys=usb-0000:00:03.0-1/input1
S: Sysfs=/class/input/input3
H: Handlers=mouse0 event3 ts0
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

have tried specifying  Phys=usb-0000:00:03.0-1/input1 as option in xorg.conf  which results in xserver starting to the point you see pointer and then crashes and display's splash screen
](*,)

---

### Post by prelude on 2008-02-03
I had to do some extra stuff to get my mouse "working"

Added evdev to /etc/modules

made a new file in /etc/udev/rules.d/ called '19-local.rules' where I added ```

KERNEL=="event[0-20]*", SYSFS{../name}=="Logitech USB RECEIVER", NAME="input/mx1000"
```

after I rebooted I made some slight alterations to my xorg.conf file
```

Section "InputDevice"
	Identifier	"Logitech MX1000"
	Driver		"evdev"
	Option		"Device"	"/dev/input/mx1000"
	Option		"Name"		"Logitech USB RECEIVER"
#	Option		"HWHEELRelativeAxisButtons"        "7 6"
	Option		"Buttons"	"20"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

Section "ServerLayout"
...
#	Inputdevice     "Configured Mouse"
        Inputdevice     "Logitech MX1000"      "SendCoreEvents"
...
EndSection

```

now my mouse works, sorta, side tilt on the wheel is dead and the middle thumb button reports and acts as a regular middle button but everything else works okay.

---

### Post by jrib on 2008-02-03
prelude,

try "SendCoreEvents" instead of "CorePointer"

---

### Post by Sonic Reducer on 2008-02-07
could you update this for gutsy? i'm always afraid to follow instructions that specifically say they are for a different version, doubly so when there are different instructions for the various versions listed

---

### Post by jrib on 2008-02-07
> **Sonic Reducer said:**
> could you update this for gutsy? i'm always afraid to follow instructions that specifically say they are for a different version, doubly so when there are different instructions for the various versions listed

I've been meaning to do that.  The instructions are the same as in feisty so you can safely use them.  The reason I have not just added "gutsy" is that I have found some extra options you can match against (in 'man evdev') that will help those users that have more than one "Logitech USB Device" and I wanted to force myself to update the page with these.  I'll try to do so in the next few days.

---

### Post by Durden on 2008-03-12
I can't get this to work for the life of me. Below is my xorg.conf

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice     "Logitech MX1000" "CorePointer"
#    InputDevice    "Configured Mouse"
EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

cat /proc/bus/input/devices gives me

I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1a.1-2.1.1/input1
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 1 f80 8837c000 667bfa d9415fed 8e0000 0 0 0
B: REL=40
B: ABS=1 0

I've done everything the wiki said but my x sever just flickers on and off again until I boot back up in safe mode and replace my xorg.conf with my backup.

Can anyone help? I'm really anxious to get my mouse working. Thanks.

-todd

---

### Post by tweedledee on 2008-03-12
> **Durden said:**
> I've done everything the wiki said but my x sever just flickers on and off again until I boot back up in safe mode and replace my xorg.conf with my backup.

Can anyone help? I'm really anxious to get my mouse working. Thanks.

-todd

Not sure if it matters, but is your mouse Section before the Server layout section?  Also, do you have multiple receivers?  That one is showing up as a keyboard handler, not a mouse, which could be the problem.  Try blacklisting lmpcm_usb if you can't get it recognized as a mouse.

---

### Post by jrib on 2008-03-12
> **Durden said:**
> I can't get this to work for the life of me.
...
-todd

try "SendCoreEvents" instead of "CorePointer"

---

### Post by Durden on 2008-03-12
> **_jason said:**
> try "SendCoreEvents" instead of "CorePointer"

That did it man, thank you so much.

---

### Post by lenpup on 2008-03-19
Hello all, my first post on the ubuntu forums!

I've been using ubuntu for a few days, terrific OS so far, only struggling with getting my MX1000 to operate as more than a 3-button mouse with scroll wheel. 
Followed the guide as directed, resulted in low-graphics mode at startup (which appears totally garbled and unusable). I understand this must mean that my xorg.conf file has failed to load because of the changes I made to it? The problem, as far as my limited knowledge can tell me, is because "Logitech USB Receiver" appears twice when I use  cat /proc/bus/input/devices

I: Bus=0003 Vendor=046d Product=c525 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-3/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c525 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.0-3/input1
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event3 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 1 f80 8837c000 667bfa d9415fed 8e0000 0 0 0
B: REL=40
B: ABS=1 0


I read that this may be a result of an bug with the lmpcm_usb driver, which I blacklisted as suggested. However, this still results in two instances of the "Logitech USB Receiver" device. I am only using one Logitech product, my MX1000, so I assume it cannot be as others experienced this error due to using a Logitech USB keyboard as well. 

I made an attempt to identify the correct device via its event handler as well, instead of by name, but this also caused xorg to fail to load.

I've searched the forums as much as my patience will allow, and tried several other guides, to no avail. Can anyone give me a nudge in the right direction? Please let me know if I need to post any other info.

Sincere thanks in advance for your time, to any responders.

EDIT: I've managed to get all the functionality I was looking for with btnx-0.4.6:[http://ubuntuforums.org/showthread.php?t=455656]("http://ubuntuforums.org/showthread.php?t=455656")
Thanks anyway ^^

---

### Post by isecore on 2008-03-27
So, I've tried setting my MX1000 up in Hardy, but it's not working.

Or well, it supposedly is working. I modified my xorg.conf, which is really simple since I know the procedure inside out. Restart GDM and everything seems peachy, except that the pointer won't move.

The only way for me to get it to work is to revert back to the default settings, and that means no sidescroll and barely any functionality.

---

### Post by tweedledee on 2008-03-28
> **isecore said:**
> So, I've tried setting my MX1000 up in Hardy, but it's not working.

Or well, it supposedly is working. I modified my xorg.conf, which is really simple since I know the procedure inside out. Restart GDM and everything seems peachy, except that the pointer won't move.

The only way for me to get it to work is to revert back to the default settings, and that means no sidescroll and barely any functionality.

Try looking at this bug thread, especially the lower half with various solutions proposed: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/173833](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/173833)

The basic issue appears to be that the hotplug/evdev interface was radically changed but is still poorly documented and implemented in Hardy.  The simplest solution, assuming you don't have any particularly unusual demands on your buttons, may be to install btnx:
[http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/)
[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

---

### Post by isecore on 2008-03-29
> **tweedledee said:**
> Try looking at this bug thread, especially the lower half with various solutions proposed: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/173833](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/173833)

The basic issue appears to be that the hotplug/evdev interface was radically changed but is still poorly documented and implemented in Hardy.  The simplest solution, assuming you don't have any particularly unusual demands on your buttons, may be to install btnx:
[http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/)
[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

btnx sorted my problems with assigning buttons. I was doing it the old-school way with xbindkeys. First I didn't feel like messing with it since btnx wasn't in the Hardy repos and not available for 64-bit, but after a quick compile it's working as well as can be expected.

---

### Post by DaveBG on 2008-05-04
Hello. I have problem. I have the MX1000 as well as another standard wired 2 button mouse no scroll.

Upon bootup both mouses work, and after 30 secs the MX1000 stops.

Here is my cat /proc/bus/input/devices:

```
dave@dave-desktop:~$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c50e Version=0111
N: Name="Logitech USB RECEIVER"
P: Phys=usb-0000:00:0b.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=20017
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10
B: LED=ff00

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0001 Version=0001
N: Name="PS/2 Logitech Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=7
B: KEY=30000 0 0 0 0 0 0 0 0
B: REL=3


```

When i do all mentioned here:
[https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)

both mouses no work and i have to restore the backup and reboot.
X is able to start though...

Any advise? Should i remove the other wired old mouse first?

---

### Post by tweedledee on 2008-05-04
> **DaveBG said:**
> Hello. I have problem. I have the MX1000 as well as another standard wired 2 button mouse no scroll.

Which version of Ubuntu are running?  If Hardy, evdev works differently with it, so the guide you are following will no longer work.  Instead of identifying devices by Name, you must look in /dev/input/by-path/ or /dev/input/by-id/ and identify the correct mouse there, then use "Device" instead of "Name" with the new identifier.  Once evdev is configured correctly in xorg.conf, you may still run into problems because evdev no longer outputs the same button codes for most people with the MX1000 (which is actually the fault of a different driver).  I've not upgraded my computer with my MX1000 attached yet (and in fact am not going to - I've found Debian to be a much better "upgrade" than going to Hardy, which essentially killed two of the three computers I've updated so far), so I can't be more specific at the moment.

---

### Post by DaveBG on 2008-05-05
Yes i have Ubuntu 8.04.

I do not need the extra buttons if i am able to use the mouse and the scroll only.

I try but i cant understand which it is :(

So i have:

Section "InputDevice"
    # generated from default
	Identifier	"Logitech MX1000"
	Driver		"evdev"
	Option		"Device"	"/dev/input/event8" 
	Option 		"RelHWHEELMapTo"	"Buttons 7 6"
EndSection


Bu see how many events* i have:

[[IMG]http://img176.imageshack.us/img176/7938/screenshotep1.th.png[/IMG]](http://img176.imageshack.us/my.php?image=screenshotep1.png)

How do i identify it?

---

### Post by tweedledee on 2008-05-06
> **DaveBG said:**
> How do i identify it?

Trial and error.  But based on comments in bug reports and other threads, I would guess that you want to use```

/dev/input/by-id/usb-Logitech_USB_RECIEVER-event-mouse
```
At least start with that one, then other in by-id, then the ones containing "mouse" in by-path if you still don't get it working.  The ones in /dev/input/ are not necessarily stable, so even if you get the correct one, it may change upon reboot.

---

### Post by fooman on 2008-05-07
haha,  after trying a few different configs from this thread and another...i have found the setup that works for me!  :)

all of my buttons now work except for the middle button on the side (which did nothing in feisty or gutsy either).  thanks for all the info...you guys rock.  :guitar:

heres how my *working* xorg looks:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Logitech MX1000" "SendCoreEvents"
EndSection

Section "InputDevice"
    Identifier     "Logitech MX1000"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
    Option         "HWHEELRelativeAxisButtons" "7 6"
EndSection
```

---

### Post by DLGandalf on 2008-05-14
With hardy the horizontal scroll buttons seem inversed, someone got a answer to that, and a way to get the middle thumb button to work in hardy?!

---

### Post by isecore on 2008-05-15
> **DLGandalf said:**
> With hardy the horizontal scroll buttons seem inversed, someone got a answer to that, and a way to get the middle thumb button to work in hardy?!

I don't care about the thumb-button, but it would be nice to have the horizontal scroll go in the right directions. They're inverted for me too.

Here's the relevant section that I have in my xorg.conf

```
Section "InputDevice"
        Identifier "MX1000"
        Driver "evdev"
        Option "Device" "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection
```

---

### Post by Curtisc on 2008-05-16
> **DLGandalf said:**
> With hardy the horizontal scroll buttons seem inversed, someone got a answer to that, and a way to get the middle thumb button to work in hardy?!

What do you want to do with the thumb button?  I have mine mapped to the scale plugin in compiz, it's Button10.  ccsm won't give you Button10 in the drop-down list, but if you type it in it works just fine.

---

### Post by isecore on 2008-05-16
> **Curtisc said:**
> What do you want to do with the thumb button?  I have mine mapped to the scale plugin in compiz, it's Button10.  ccsm won't give you Button10 in the drop-down list, but if you type it in it works just fine.

Wow, thanks! I finally found a good use for that dang button. Had this mouse for years, never thought that button was much use until five minutes ago :)

---

### Post by isecore on 2008-05-17
Does anyone else have problems when using evdev-driver in games? I just noticed it in Alien Arena and Xmoto. The mouse jerks around uncontrollably, but everythings fine when not using evdev.

Any ideas?

---

### Post by vagueblur on 2008-05-22
I have Ubuntu 8.04 and an mx1000... no matter what I try, I can't get the side buttons working in firefox (or any other program). 

I upgraded from version 7, and I remember it took quite a bit of work to get the side buttons working when I installed v7.

Would someone be nice enough to help me troubleshoot?

---

### Post by vagueblur on 2008-05-22
It's working now... I'm not sure why. Maybe uninstalling imwheel and reinstalling did it.

I've used many linux distros and ubuntu is the best... but it's so frustrating that getting something as simple as a working mouse is so complicated.

Thanks for letting me vent :-)

---

### Post by Kemper Boyd on 2008-05-28
Hello everybody. I followed the guide on how to set up my MX1000, and got *almost* everything working. Almost because the middle thumb button doesn't seem to do anything. Nothing appears on xev when I press it. I know it's supposed to be button10 but it really seems completely dead.

Got the other two thumb buttons working as back/forward in firefox, but I'd really like to have that button enabled to (if possible) bind it to button2 (pressing the wheel is very uncomfortable, it's hard and always scroll the wheel too while pressing it).

Thanks for any help!

---

### Post by Kemper Boyd on 2008-05-29
> **Kemper Boyd said:**
> Hello everybody. I followed the guide on how to set up my MX1000, and got *almost* everything working. Almost because the middle thumb button doesn't seem to do anything. Nothing appears on xev when I press it. I know it's supposed to be button10 but it really seems completely dead.

Got the other two thumb buttons working as back/forward in firefox, but I'd really like to have that button enabled to (if possible) bind it to button2 (pressing the wheel is very uncomfortable, it's hard and always scroll the wheel too while pressing it).

Thanks for any help!
Nevermind, turns out that restarting X wasn't enough (at least to make xev aware of the change). Needed a full system reboot.

---

### Post by Braedley on 2008-05-30
So that everyone knows, the middle thumb button will not work (according to the howto that I read), so there is little point mentioning that it doesn't work right now.  Be glad that you have 11 functioning actions instead of 5.

---

### Post by jrib on 2008-05-30
> **Braedley said:**
> So that everyone knows, the middle thumb button will not work (according to the howto that I read), so there is little point mentioning that it doesn't work right now.  Be glad that you have 11 functioning actions instead of 5.

I have all the buttons working for me with the following xorg.conf.  I haven't placed this in the tutorial because I am experiencing a strange issue where I get no extra buttons when you first log in, but if I log out and then back in everything works.  This happens everytime and I'm a bit baffled.  Here's my xorg.conf in any case in case someone else would like to try:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon Apr 16 20:39:15 PDT 2007

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
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier  "Default Layout"
    screen      "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	InputDevice "Logitech MX Revolution" "SendCoreEvents"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dvorak"
EndSection

Section "InputDevice"
	Identifier	"Logitech MX Revolution"
	Driver		"evdev"
    Option      "Device"    "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
    Option		"HWHEELRelativeAxisButtons"	"7 6"
EndSection

Section "Monitor"
	Identifier	"DELL 1707FP"
	Horizsync	30.0	-	70.0
	Vertrefresh	50.0	-	160.0
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	        "True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GT]"
	Monitor		"DELL 1707FP"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection


```

---

### Post by jrib on 2008-10-12
> **_jason said:**
> I have all the buttons working for me with the following xorg.conf.  I haven't placed this in the tutorial because I am experiencing a strange issue where I get no extra buttons when you first log in, but if I log out and then back in everything works.  This happens everytime and I'm a bit baffled.  Here's my xorg.conf in any case in case someone else would like to try:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon Apr 16 20:39:15 PDT 2007

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
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier  "Default Layout"
    screen      "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	InputDevice "Logitech MX Revolution" "SendCoreEvents"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dvorak"
EndSection

Section "InputDevice"
	Identifier	"Logitech MX Revolution"
	Driver		"evdev"
    Option      "Device"    "/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
    Option		"HWHEELRelativeAxisButtons"	"7 6"
EndSection

Section "Monitor"
	Identifier	"DELL 1707FP"
	Horizsync	30.0	-	70.0
	Vertrefresh	50.0	-	160.0
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	        "True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GT]"
	Monitor		"DELL 1707FP"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection


```

The strange issue was being caused by hotplug.  If you connect your mouse after X has started, then it won't use your xorg.conf settings for it.  In my case, this happened because my mouse is connected to a sub port on my monitor and it doesn't have power if the monitor is off.

---

### Post by eslin on 2008-11-03
So noone knows how to use hal and the tip is to revert and use xorg.conf instead?

can't the beardy person who thought ubuntu should use hal now in 8.10 just explain how hal should be configured.

I want my mouse wheel to work as the middle button and I would also like to configure it using the correct system ie HAL now in 8.10.

[https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)
this guide seems to describe something else.

---

### Post by jrib on 2008-11-04
> **eslin said:**
> So noone knows how to use hal and the tip is to revert and use xorg.conf instead?


What tip says that?

> **eslin said:**
> 
can't the beardy person who thought ubuntu should use hal now in 8.10 just explain how hal should be configured.


[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

> **eslin said:**
> 
I want my mouse wheel to work as the middle button and I would also like to configure it using the correct system ie HAL now in 8.10.

[https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)
this guide seems to describe something else.


I updated the wiki for 8.10, but I no longer use the mx1000.  I believe everything should just work, so please give feedback.

(If you read my previous edit about revoco, ignore it as that only applies to the mx revolution)

---

### Post by uksuperdude on 2008-11-11
Just thought I'd add my 2c to this thread, as it was one I referred to while fixing my problem. Also the wacom page on the Ubuntu wiki (note: I do not have a wacom, I just used the page as a reference.)

**What my problem was:**

I have a logitech mouse (V220 perhaps?). I hate clicking the scrollwheel as my middle mouse paste, so I used to use a "pointer=1 8 3 4 5 6 7 2 9 10" in a .Xmodmap file. This remapped my thumb button to be middle. This worked fine as long as I did not unplug and replug the mouse. The HAL would re-map the buttons. Since Intrepid now uses HAL only (not a bad thing, actually quite good once configured.) I had to find out how to make HAL write the correct button mapping.

**How I solved it (hopefully will work for you):**

Work out the correct button mapping for you using xmodmap, and xev. This is what you used to use in xorg.conf for the ButtonMapping parameter. If your buttons don't work, or you are not sure how to do the above, there are HEAPS of posts on the forums for xmodmap and xev.

Once you have your button mapping, you need to write a HAL rules file.

do the following:
```
sudo gedit /etc/hal/fdi/policy/cutsom_mouse.fdi
```

Now add something similar to the following (this is mine):
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="Logitech">
        <merge key="input.x11_driver" type="string">evdev</merge>
        <merge key="input.x11_options.ButtonMapping" type="string">1 8 3 4 5 6 7 2 9 10</merge>
        <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
        <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
      </match>
    </match>
  </device>

</deviceinfo>

```

You will notice most of it looks quite similar to the options you once had in xorg.conf (the same even!).

Now I know lots of you won't have a Logitech mouse.
Running the following command will show the devices for your system:
```
hal-device
```

There may be a lot of output from the above, (I had 167 devices!) but don't despair.
Pipe it into a text file ```
hal-device > devices.text
```
and open it in your text editor of choice. Look for a section similar to the following:
```

13: udi = '/org/freedesktop/Hal/devices/usb_device_46d_c51b_noserial_if0_logicaldev_input'
  input.device = '/dev/input/event12'  (string)
  input.product = 'Logitech USB Receiver'  (string)
  linux.device_file = '/dev/input/event12'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1.1/7-1.1.3/7-1.1.3:1.0/input/input18/event12'  (string)
  info.subsystem = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c51b_noserial_if0'  (string)
  info.product = 'Logitech USB Receiver'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c51b_noserial_if0_logicaldev_input'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c51b_noserial_if0'  (string)
  info.category = 'input'  (string)
  linux.subsystem = 'input'  (string)
  info.capabilities = { 'input', 'input.mouse' } (string list)
  input.x11_driver = 'evdev'  (string)

```

Note the input.x11_driver = evdev and the info.capabilities are input.mouse. Replace the line in your fdi file that describes your product(mouse) and see how you go.

When testing, if nothing happens make sure you have re-started HAL after changing the .fdi (sudo /etc/init.d/hal restart)

---

