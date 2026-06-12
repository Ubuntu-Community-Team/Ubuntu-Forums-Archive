---
title: "Noob in Trouble who wants to be my hero"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by dazedwhiteboy on 2008-09-25
my english is horrible so bare with me.

i just installed kumbutu 8.04.

im having trouble with getting my screen resoultion above 800x600
i think it could be that it doesnt regonize my video cards but i could be wrong.

im also having trouble hooking up to the internet.

i have a eth 0 and a eth 1 which are both disabled and do not want to enable 
 
i have just popped my cherry with linux so if anyone can send me links to linux sites so i can have little activites to do to understand linux that would be great. but thats after i get this working first.


nvidia 780i
4gb dominator ram 1066mhz
intel x6800 dual core extreme 
2x 150 western digital raptors
all water cooled by koolanc exos 2 
xfi

---

### Post by pytheas22 on 2008-09-25
For the video, yes, with nvidia cards, you need to install the proprietary driver to get full resolution.  Try using [envy]("http://albertomilone.com/nvidia_scripts1.html"); it will try to auto-detect the right driver for you and install it automatically.  Sometimes it does not work; if that happens to you, we can figure out how to install the driver manually.

For the Internet cards: are they wired or wireless?  Does it help if you type:

```
sudo ifconfig eth0 up
sudo ifconfig eth1 up
```

If that does not fix it, what is the output of these commands:

```
lshw -C Network
lspci -nn
lsusb
```

---

### Post by dazedwhiteboy on 2008-09-25
some how i got the internet to work 

as for the video i went into hardware and enabled 3d acceleration which i think auto detected my drivers i checked  glx gears and it seamed to be working also i changed the settings for the monitor to this but i still gett to options for resolution size 

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Unknown"
HorizSync 30.0 - 110.0
VertRefresh 50.0 - 150.0
Option "DPMS"
Modeline "1920x1200_60.00" 154.0 1920 1968 2000 2080 1200 1203 1209 1235 +Hsync -Vsync
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
Option "ModeValidation" "NoMaxPClkCheck"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1920x1200_60.00" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

---

### Post by eddietours on 2008-09-25
did you use envy for drivers

---

### Post by tuxxy on 2008-09-25
Try chaning the res in nvidia-settings

---

### Post by dazedwhiteboy on 2008-09-26
After taking a look at the screen after the changes i belive the resulotion has changed but under system settings it still gives me the option 0f 800x600 even though its beyond those settings. 

i dont know how to get into the nvidia settings if you can tell me i will check it.

no i did not use envy but now nvidia comes on just before the gui so i think its working 

after further inspection of my computer i have found that i have no sound i am currently using xfi fatlty sound card is there any support for that? 

P.S. Thanks alot you guys

---

### Post by pytheas22 on 2008-09-26
You can start nvidia-settings by opening a terminal and typing:
```

sudo nvidia-settings
```

Can you change the resolution there?

As for the sound, it should work out-of-the-box in Ubuntu, but with newer sound cards that's not always the case.  A good place to start troubleshooting is [this guide]("https://help.ubuntu.com/community/SoundTroubleshooting").

---

### Post by dazedwhiteboy on 2008-09-26
ok everyone monitor is good videocards are working now its just sound after searching for help online ifound out that the creative labs xfi (emu20k1 chipset)is not supported does anyone know where to find out if a developer has created a driver for it yet

---

### Post by pytheas22 on 2008-09-27
I'm glad you figured out the video issues.

As for the sound, [Wikipedia]("http://en.wikipedia.org/wiki/Sound_Blaster_X-Fi") says this about your card:
> 
    * Linux support

On September 24, 2007 Creative Labs released a closed source unsupported beta driver providing Linux 64-bit OS support for the following Sound Blaster X-Fi series sound cards:[6]

    * Creative Sound Blaster X-Fi Elite Pro
    * Creative Sound Blaster X-Fi Platinum
    * Creative Sound Blaster X-Fi Fatal1ty
    * Creative Sound Blaster X-Fi XtremeGamer
    * Creative Sound Blaster X-Fi XtremeMusic

An open source driver is available with OSS v4 build 1013 and above[7]. As of July 2008, ALSA does not support the X-Fi series. However, datasheets were provided to the ALSA team and drivers are now in development.

So apparently ALSA drivers are not available yet, but you have the option of using either an OSS driver or Creative's closed-source driver.  Please google around and see if you can figure out how to apply either of those solutions; if not, let us know and we can advise (I don't know anything about OSS myself or I'd provide more specific instructions).

---

