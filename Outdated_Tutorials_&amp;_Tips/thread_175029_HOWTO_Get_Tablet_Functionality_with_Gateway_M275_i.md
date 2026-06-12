---
title: "HOWTO Get Tablet Functionality with Gateway M275 in Dapper"
date: 2006-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by brutimus on 2006-05-12
Getting tablet functionality on a Gateway M275 tablet pc with Dapper is actually really easy.  All you have to do is go into your xorg.conf (/etc/X11/xorg.conf) and find the input device sections for the tablet (Driver   "wacom") (theres 3 of them) and change the Option  "Device" from /dev/wacom to match the device ID of your tablet.  Mine (and a number of other people that I've read about) have been /dev/ttyS1.  That may sound a little confusing, so here is the corresponding section of my xorg.conf file---

```

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS1"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS1"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS1"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

```

Hope this helps anyone trying to get this working on Dapper.

**UPDATE:** I've also figured out how to get the tablet functionality of the M275 working in SuSE Linux Enterprise Desktop 10.  I'm posting a link to that here just in case anyone is still having problems, they can read over that thread and maybe get some ideas of how to fix their problem. [HERE]("http://www.linuxforums.org/forum/suse-linux-help/65054-sled-10-gateway-m275-tablet-enabling-wacom-tablet.html")

---

### Post by tukster on 2006-07-20
nice howto, i got my toshiba tecra working in no time.
only problem was to find out the port for input devices. but it can be found  in device manager,

---

### Post by brutimus on 2006-08-23
I'm glad it worked for you.  I guess I had forgotten about the dev manager telling what port.  I just had the basic idea that it was somewhere around ttyS*, so I just tried 0 then 1, and 1 worked for me.

---

