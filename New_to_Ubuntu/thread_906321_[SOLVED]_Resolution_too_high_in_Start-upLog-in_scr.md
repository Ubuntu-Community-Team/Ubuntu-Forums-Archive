---
title: "[SOLVED] Resolution too high in Start-up/Log-in screen"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by robert1325 on 2008-08-31
Hi,

I installed the dedicated video drivers for my Ati radeon 9800pro ,  and everything works fine on , I use a 1024/768 resolution.  But when I start my computer and want to log-in the resolution goes up to 1600/1200 which my CRT does not support (luckily my Projector did) .

  I wonder if I can change this or rid myself completely of the whole log-in thing.

This is all new for me as a long-time windows user.  I'm really loving ubuntu .

Robert

---

### Post by jemate18 on 2008-08-31
> **robert1325 said:**
> Hi,

I installed the dedicated video drivers for my Ati radeon 9800pro ,  and everything works fine on , I use a 1024/768 resolution.  But when I start my computer and want to log-in the resolution goes up to 1600/1200 which my CRT does not support (luckily my Projector did) .

  I wonder if I can change this or rid myself completely of the whole log-in thing.

This is all new for me as a long-time windows user.  I'm really loving ubuntu .

Robert

We need to see your xorg.conf

Try this.
1. Click Applications -> Accessories ->Terminal
2. Type
```
less /etc/X11/xorg.conf
```

Paste the contents here..

Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by drubin on 2008-08-31
> **jemate18 said:**
> We need to see your xorg.conf

Try this.
1. Click Applications -> Accessories ->Terminal
2. Type
```
less /etc/X11/xorg.conf
```

Paste the contents here..

Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post
jemate18

less might not show the full file. 

try this. ```
sudo cp /etc/X11/xorg.conf ~/Desktop/xorg.conf
```
This will create a file on your desktop upload that file.

**EDIT** Ps welcome to the forums!

---

### Post by jemate18 on 2008-08-31
> **rubinboy said:**
> less might not show the full file. 

try this. ```
sudo cp /etc/X11/xorg.conf ~/Desktop/xorg.conf
```
This will create a file on your desktop upload that file.

Thanks for the welcome.

Anyway, I always see a lot of threads which were solved, but yet the one who post it doesn't mark the thread as SOLVED. Well for me, if a thread is MARKED then users who search for answers may easily find what they are looking for.

---

### Post by drs305 on 2008-08-31
> **robert1325 said:**
> Hi,

I installed the dedicated video drivers for my Ati radeon 9800pro ,  and everything works fine on , I use a 1024/768 resolution.  But when I start my computer and want to log-in the resolution goes up to 1600/1200 which my CRT does not support (luckily my Projector did) .

  I wonder if I can change this or rid myself completely of the whole log-in thing.

This is all new for me as a long-time windows user.  I'm really loving ubuntu .

Robert

It may be a simple boot resolution setting that needs changing. 

Install startupmanager and then run it. In the first tab it will allow you to set your screen resolution.
```
sudo apt-get install startupmanager
```

To run: System, Administration, Startup-Manager. The set Boot Options, Display Options - Resolution.

---

### Post by alienexplorers on 2008-08-31
Use startupmanager found in the repo's to adjust the screen size.

---

### Post by robert1325 on 2008-08-31
> Section "InputDevice"
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
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection


Thanks for your help so far , I will follow the instructions pertaining to forum use.

---

### Post by jemate18 on 2008-08-31
> **robert1325 said:**
> Thanks for your help so far , I will follow the instructions pertaining to forum use.

Please try this
1. Application -> Accessories ->Terminal
2. type
```
sudo su [password]
```
3. type
```
dexconf
```
4. restart
```
shutdown -r now
```

 dexconf  generates Xorg X server configuration file from debconf data

_____________________________________________________________________
Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by drubin on 2008-08-31
> **jemate18 said:**
> 
```
sudo su [password]
```


Why do you need to be root? The prefered way of doing things in ubuntu is to prefix commands with sudo instead

---

### Post by jemate18 on 2008-08-31
> **rubinboy said:**
> Why do you need to be root? The prefered way of doing things in ubuntu is to prefix commands with sudo instead

I use sudo su so that running the command
```
shutdown -r now
```
wouldn't fail because of privileges. 


try this if you dont want to use sudo su
1. Application -> Accessories -> Terminal
2. Type
```
sudo dexconf
```
3. Click system, quit, restart

---

### Post by robert1325 on 2008-08-31
I followed your last suggestion , the log-in window showed up but the whole system was very slow , apps took some time to close and scrolling did not go smoothly. 

I checked my videocard drivers and they were disabled, enabling them has made everything  snappy/fast again but the problem with the resolution has returned.

Thanks for your welcome and support ,  I may have to live with this unease, I can log-in without picture .

---

### Post by drubin on 2008-08-31
> **jemate18 said:**
> I use sudo su so that running the command
```
shutdown -r now
```
wouldn't fail because of privileges. 


try this if you dont want to use sudo su
1. Application -> Accessories -> Terminal
2. Type
```
sudo dexconf
```
3. Click system, quit, restart

never used dexconf before.   But those instructions are a little bit simpler.

---

### Post by jemate18 on 2008-08-31
> **robert1325 said:**
> I followed your last suggestion , the log-in window showed up but the whole system was very slow , apps took some time to close and scrolling did not go smoothly. 

I checked my videocard drivers and they were disabled, enabling them has made everything  snappy/fast again but the problem with the resolution has returned.

Thanks for your welcome and support ,  I may have to live with this unease, I can log-in without picture .

Did you try my suggestion on using the command
dexconf?

---

### Post by Too Late on 2008-08-31
> **robert1325 said:**
> I wonder if I can change this or rid myself completely of the whole log-in thing.
Go to System -> Administration -> Login Window -> Security (tab) and check "Enable Automatic Login". This enables automatic login, but it doesn't however prevent your screen to temporarily going "out-of-range".

This works for me (xorg.conf file):
```

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "fglrx"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Defaultdepth 24
[color=red]SubSection "Display"
        Depth           24
        Modes           "1024x768"
EndSubSection[/color]
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen "Default Screen"
EndSection
Section "Module"
Load "glx"
EndSection

```

---

### Post by robert1325 on 2008-08-31
Yes Jemate18 , I followed your instructions , it seemed to disable my videocard driver .

I followed Too late's suggestion and my computer now starts without automatic login , thus solving the problem!

---

### Post by jemate18 on 2008-08-31
> **robert1325 said:**
> Yes Jemate18 , I followed your instructions , it seemed to disable my videocard driver .

I followed Too late's suggestion and my computer now starts without automatic login , thus solving the problem!

Yes thats how it works because it gets its configuration from debconf data which is by default the one created after your Ubuntu installation. It will disable it and load the defaults.

I gave that so that we could see if the problem was a misconfiguration of the xorg.conf (or some weird thing just happened/edited your xorg.conf), thus reloading defaults.

Too Late's suggestion is by far the BEST thing if you want your screen resolution to be adjusted in your desired resolution.

Thanks.....

---

