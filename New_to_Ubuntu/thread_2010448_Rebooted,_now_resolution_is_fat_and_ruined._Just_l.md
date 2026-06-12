---
title: "Rebooted, now resolution is fat and ruined. Just like on Prom Night."
date: 2012-06-25
forum: New to Ubuntu
---

### Post by dresyn on 2012-06-25
Installed Lubuntu last night, after a nightmare of having installed Ubuntu 12.04 or whatever on my p.o.s 32bit PC.

Looked amazing! Here, I even have screen shots.
[IMG]https://p.twimg.com/AwNi8J0CIAAKi9U.jpg:large[/IMG]

Now its all fat, and the resolution has bloated out to 1024x678
It may not have been true 1080p, but it looked damn good last night.

I go to Display Settings, and it's not letting me choose anything else. I rebooted, and it's still all fat and unattractive.

Can someone please help me?

---

### Post by dresyn on 2012-06-25
and now its doing this on the desktop! right after i shut down and booted back up.

[IMG]http://tinypic.com/r/flhtux/6[/IMG]

---

### Post by dresyn on 2012-06-27
Please help?

---

### Post by marinara on 2012-06-28
i'm really not qualified to help, but you really need to add more info to the post:

model# of monitor and graphics card
build of lubuntu, current graphics drivers running the card,
output of xrandr, etc

---

### Post by dresyn on 2012-07-01
Lubuntu's latest 32bit version

Dell ST2420L 24-inch LED Full HD Widescreen Monitor(fully capable of 1920x1080 on this OS, it was doing it just fine before i rebooted. Runs "1080p" just fine on my PS3 and 360)

Its a Dell motherboard, so the graphics card is integrated. Whenever I bring up the Additional Drivers, NOTHING is displayed. It says no integrated drivers are being used, which is strange. Like I've said before, I've seen it do 1080 before. It was beautiful.

It's just saying Integrated VGA Controller, but again I'VE SEEN IT RUN HD. It wasn't sluggish or anything. It ran perfectly fine, and then reverted back to a bloated VGA display that would have looked like crap on Windows 2000.

I have absolutely no idea what xrandr is. I'll look into it, but please offer some insight if you have any.

I've talked to friends about this, and even the smartest seem baffled. At least they, like marianna took the time to help. I can clearly see the "help" section of this forum is populated by those who just want to cover the basics to act as though they have the slightest clue on what they;'re blabbering about.

It's been nearly a week, and ONE reply. Thats just sad.

---

### Post by vcrpex on 2012-07-01
I dunno if this will work for you. it work for me from 9.04 to 10.10, and now on Squeeze.
you can edit xorg.conf inside etc/x11
you need to issue:
sudo gedit etc/x11/xorg.conf

the below is xorg.conf file:
Section "Monitor"
    Identifier     "Monitor0"
    DisplaySize     1920 1080
    HorizSync       30-70
    VertRefresh     60-75
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
	Modes "1024x768"
    EndSubSection
EndSection

you can add under Modes other screen resolution.
make sure you need your horizonsync and vertsync of your own monitor. you probably can find it through the back of your monitor or on the internet.

---

