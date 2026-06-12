---
title: "[SOLVED] Monitor/Screen Resolution Problem"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by acrousey on 2008-08-21
The monitor that I am using is older than dirt. It's a PACOM (if they still make thouse) 15" monitor. When I use 
```
sudo gksu displayconfig-gt
```
to detect a monitor, it detects plug'n'play. My monitor isn't even listed. Now, I remember there is a way to change the xorg.conf file using
```
sudo nano /etc/X11/xorg.conf
```
however, I don't remember what I need to add, nor where I need to add it.

Here's what it looks like in my xorg.conf:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
       Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

Also, while I'm at it, how can I tell what kind of video card I have on here? It's my family's old computer, and I haven't added anything onto it except for a little bit more RAM. I think the video card is integrated. But, how would I get around that kind of stuff? Thanks!

-acrousey

---

### Post by tuxxy on 2008-08-21
To find out system information just open applications > sys tools > sys info

Are there no drivers available at system > admin > hardware drivers

---

### Post by rockerphil on 2008-08-21
ok, to reconfigure your resolution run this code

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and to see what kind of video card you've got in the machine run this

```
lspci
```

hope this helps,

Phil

---

### Post by acrousey on 2008-08-21
Isn't there a way to give me more screen resolution options? Right now my only choices are 800x600 and 640x480. I know there's a way to get more because I've done it once, but since then I wiped-out the old drive and reinstalled Ubuntu and have forgotten how I did that about a month ago. I have had the screen resolution on this monitor at 1024x768. I just forgot how I did it and the location of the site that I used before.

---

### Post by mpjf01 on 2008-08-21
I have the same problem and the xorg.conf file looks the same as shown above. Rather than starting another thread I'll look for a reply here. Thanks.

---

### Post by acrousey on 2008-08-22
Would I be able to just change my monitor to a Generic 1024x768 monitor via
```
sudo gksu displayconfig-gt
```?

The real problem I was having was that the splash/login screen was too large. The box where I write in my name and password was in the bottom right hand corner of the screen. But to fix that, would I just be able to change my monitor's virtual screen resolution using
```
sudo nano /etc/X11/xorg.conf
```?


Also, how can I "refresh" my xorg.conf? I've kind of been playing around in there... Let's just say I'm not on that computer right now tonight. I kind of just gave up a little bit earlier. Tomorrow is a new day, I hope.

---

### Post by acrousey on 2008-08-25
After doing some guessing and testing with monitor options, I found out that my PACOM Data, Inc monitor is equivalent to a Korea Data Services one. I spent all of last week trying to find the HorizSync and VertRefresh online for my monitor, but it seems that this company must have fallen off the face of the earth. I guess a lot can happen in 10 years (this monitor was manufactured in 1995!).

---

