---
title: "a few probs"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by clt on 2008-11-10
I'm trying to set up a media server using kubuntu ibex, and I plan on adding mythTV to it later, to record TV also.

The PC is in our lounge-room and it is on the home network wirelessly, and I plan on it holding all of our files, movies, music, etc. and being able to play them and output this to the big CRT TV via s-video.

I've installed kubuntu now, and installed the restricted driver for my nvidia 6200 AGP video card, and the 3d was working. My next goal is to get output from the server to the TV. I went into 'nvidia-settings' and found that it would not detect my TV, after booting the PC with the cables all plugged in. I tried following this guide [http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456) but that lead to my PC hanging on 'checking battery'. 

Also, on this server I want 1 central location which can be accessed by linux and windows PCs.

So, I've got 2 questions for you guys:
1. How would I go about getting output via s-video to my TV?
2. How do I easily set up my /home folder to be shared with other computers?

---

### Post by clt on 2008-11-10
Does anyone know the answers!?!?!

---

### Post by clt on 2008-11-10
Anybody?

---

### Post by Bölvaður on 2008-11-10
> **clt said:**
> 2. How do I easily set up my /home folder to be shared with other computers?

Please elaborate.

There are two popular ways.

SAMBA or NFS

NFS is my choice because then I can mount foreign partitions (inside different computers) as if it was locally inside my box. But ofcourse, windows doesnt support anything so this wouldnt work with windows on the other computers.

---

### Post by clt on 2008-11-11
> **Bölvaður said:**
> Please elaborate.

There are two popular ways.

SAMBA or NFS

NFS is my choice because then I can mount foreign partitions (inside different computers) as if it was locally inside my box. But ofcourse, windows doesnt support anything so this wouldnt work with windows on the other computers.

Umm, either or both ways would be fine, I'm not sure. I just want the /home folder on the server to be accessible, and the files able to be modified, via windows and linux PC's.

---

### Post by lisati on 2008-11-11
For interconnecting with Windows, see here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by clt on 2008-11-11
> **lisati said:**
> For interconnecting with Windows, see here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

awesome, thanx mate!

can anyone point me in the right direction for question 1?

---

### Post by ugm6hr on 2008-11-11
Not sure if it is the same for NVidia, but ATI graphics cards require the latest proprietary driver for TV-out.

I'd suggest trying envyng (for KDE):
```
sudo aptitude install envyng-qt
```

---

### Post by clt on 2008-11-11
yea i tried using that, made no difference, but thanx :p

---

### Post by clt on 2008-11-13
Guys, my questions still remain;

1. How would I go about getting output via s-video to my TV? I've changed the graphics card to an nvidia 6800. I've tried different nvidia drivers, kubuntu recommends the latest (177.80.), but envyng recommends the second latest (173.14.12.). I've tried adding different scripts to my xorg.conf, but in nvidia-settings it just won't detect my TV or output to it. Any ideas?

2. I thought sharing a folder could be easily done through a GUI, so I right-click the home folder, go to the 'share' tab, but when I click 'configure file sharing', nothing at all happens! How do I simply share 1 folder to windows & linux PCs?

T.I.A.

---

### Post by ViceVirtue on 2008-11-13
Hey, I think there's a "ForceTV" type-of option that you can paste into your xorg.conf, you might need to google it or check the nvidia drivers readme.

I would presume that there's an easy way to share folders in KDE 4, but I'm not sure. KDE4 seemed a little unpolished last time I tried it. It's very much like Windows XP in Gnome, it even asks you if you want it to install the windows file sharing service for you. Otherwise you can add something to /etc/samba/smb.conf like so:
---------------------------------------------
[global]
   workgroup = <YOUR WORKGROUP>
   netbios name = <YOUR SERVERS NAME>
   security = share
   guest account = nobody
   guest ok = yes
   browseable = yes
   writable = yes
[public]
    path = /home/
    public = yes
    writable = yes
    printable = no
-----------------------------------------------

Or look up a guide, that config file probably isn't very secure or complete...

---

### Post by clt on 2008-12-05
I'm still stuck, but I've made progress! I installed samba and added a samba share using samba's GUI and that's got it on the network, so I've got one problem sorted, but I'm still having issues displaying it to the TV via s-video.

I'm playing around with my xorg.conf and nvidia-settings and using [https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut) too, but still can't get it right. I want my PC displaying 2 "separate x screens", in nvidia-settings I have it set on that option, but it's acting like twinview, with the TV just being a grey screen (different from the no response blue screen). Is there anyone out there who knows a bit about xorg.conf files that could help me get this right?

My xorg.conf atm is:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1024 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "IBM 6331 E54"
    HorizSync       30.0 - 69.0
    VertRefresh     50.0 - 120.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 LE"
    Option         "ConnectedMonitor" "CRT,TV"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 LE"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "PAL-B"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1024x768 +0+0; CRT: 720x450 +0+0; CRT: 640x480 +0+0"
        SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"


    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "TV-0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0; TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by clt on 2008-12-05
Are there any X-perts out there? :p 

I'm just going by trial and error and it's not getting me anywhere!

---

### Post by clt on 2008-12-05
When my TV's connected via s-video, why won't nvidia-settings 'detect displays'?

Does anyone know how I can specifically get 2 'separate x screens' set up and working?? (Bump!)

---

### Post by clt on 2008-12-06
Can anyone help me?? I've been at this for weeks!

---

### Post by clt on 2008-12-07
bump bump bump

---

### Post by Kareeser on 2008-12-07
Hi clt. I apologize for the delay. Keep in mind that we can't solve every problem, although we will try our darn hardest to try! :)

(This is all you can expect from a bunch of volunteers.)

Refresh my memory (ha! A little in-joke), are you trying to output ONLY through S-Video, or are you planning on outputting to both a monitor and the TV?

If so, are you planning on cloning the displays (default), or using an extended desktop?

and finally... a sympathy: The S-Video on my laptop fails to work correctly either (Intel 855GM). I have no clue why, as the LVDS/VGA outputs work great.

Don't give up, but don't bump too much, it looks bad :)

---

### Post by Crewsr3 on 2008-12-28
I'm having a similar problem and have not been able to find a solution in the forms.

I have a newly installed Mythbuntu 8.10 install and have 177.80 drivers installed.  I went to select the "twinview" option in the Nvidia settings menu and it is greyed out.  I have not been able to figure out why this is greyed out.

My video card is a Nvidia Geforce 7300 GT

---

