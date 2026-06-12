---
title: "screen res problem, third install .."
date: 2008-08-02
forum: New to Ubuntu
---

### Post by nommo777 on 2008-08-02
Greetings everyone!
This is my first post here. This is truly an amazing community.Now on to my problem.I am a complete noob here and i had my ubuntu cd sent by mail.I had it dual booted with xp and it worked fine, except for the screen resolution.i know this question has been asked to many  times in this forum, but all of them require to change values in the xorg.conf file, .This is what is contained in my xorg.conf:(skipped some parts from the top)

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

I am also not able to edit this file using the sudo  commands, it sows oostint overwrite warning. I had all the updates installed. PLS help me out here. 
waiting patiently for your replies..:)

---

### Post by collinp on 2008-08-02
To change your resolution go to System - Preferences - Screen Resolution. Sorry if i misunderstood your problem.

---

### Post by nommo777 on 2008-08-02
Hellow Hellow!
Thanks for the reply..My problem is that i have only two options in the screen res dialog box, namely 640x480 and 320x240, and i want it set to 1024x768.. any suggestions??

---

### Post by collinp on 2008-08-02
What kind of graphics card do you have?

---

### Post by perlluver on 2008-08-02
> **nommo777 said:**
> Hellow Hellow!
Thanks for the reply..My problem is that i have only two options in the screen res dialog box, namely 640x480 and 320x240, and i want it set to 1024x768.. any suggestions??

Do you have the proper drivers installed?  System>Administration>Hardware Drivers.

---

### Post by nommo777 on 2008-08-02
graphics card: NVIDIA Geforce4MX, i already have installed the drivers by enabling it.. is this where the problem lies..

---

### Post by perlluver on 2008-08-02
> **nommo777 said:**
> graphics card: NVIDIA Geforce4MX, i already have installed the drivers by enabling it.. is this where the problem lies..

That is a bit of an older card.  I am going to look for the code give a minute.

Ok, type this in to the terminal ```
sudo apt-get install nvidia-settings
```  Then once that is installed type in ```
sudo nvidia-settings
``` and see if you can change the resolution in there.

---

### Post by nommo777 on 2008-08-02
Thanks a lot.. i am going to give it a try..

---

### Post by nommo777 on 2008-08-02
ok small problem, i cant get to the desired settings because the display is huge..i tried alt-drag , but when i try to change anything it reverts back to its orginal position

---

### Post by perlluver on 2008-08-02
> **nommo777 said:**
> ok small problem, i cant get to the desired settings because the display is huge..i tried alt-drag , but when i try to change anything it reverts back to its orginal position

When I had that problem, I had to click on the box a couple of times, then hit enter.  Also try with the alt+drag method.

---

### Post by nommo777 on 2008-08-02
ya. that works!!the resolution button seems to be stuck at auto.. caanot enter any values nor can i choose from any options.. below thta there is a field called panning, should i change that.?pls forgive me if this seems stupid..

---

### Post by perlluver on 2008-08-02
> **nommo777 said:**
> ya. that works!!the resolution button seems to be stuck at auto.. caanot enter any values nor can i choose from any options.. below thta there is a field called panning, should i change that.?pls forgive me if this seems stupid..

I don't think panning will help, I can't remember the new code for changing the X Server, I wish I could.  What type of monitor do you have?

---

### Post by nommo777 on 2008-08-02
> **perlluver said:**
> When I had that problem, I had to click on the box a couple of times, then hit enter.  Also try with the alt+drag method.
ok guys... i cannot se any options to change the resolution, it seems to be stuck at auto.. pls help

---

### Post by nommo777 on 2008-08-02
> **perlluver said:**
> I don't think panning will help, I can't remember the new code for changing the X Server, I wish I could.  What type of monitor do you have?
ya , monitor specs: samsung samtron 4Bi.. bit outdated isn't it..

---

### Post by nommo777 on 2008-08-02
> **perlluver said:**
> I don't think panning will help, I can't remember the new code for changing the X Server, I wish I could.  What type of monitor do you have?
one more thing perlluver, i restarted the system, and was greetded with a message that my video card was not recognised..

---

### Post by mohammadrizki on 2008-08-02
nommo777, do you use nvidia instead of nv in the Driver section of /etc/X11/xorg.conf?

---

### Post by nommo777 on 2008-08-02
> **mohammadrizki said:**
> nommo777, do you use nvidia instead of nv in the Driver section of /etc/X11/xorg.conf?
hi mohammed let  me just check it out..

---

### Post by nommo777 on 2008-08-02
> **nommo777 said:**
> hi mohammed let  me just check it out..
hi there mohammed, the following are the contents of my xorg.conf:

# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"	"true"
	Option		"NoLogo"	"True"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by mohammadrizki on 2008-08-02
i use gforce2mx and old acer monitor, i had same problem on my 6.06 ubuntu, but not in my 8.04.  in my 6.06 i change "nv" to "nvidia" and set the monitor setting like this: (both in /etc/X11/xorg.conf)

SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection

---

### Post by nommo777 on 2008-08-02
> **mohammadrizki said:**
> i use gforce2mx and old acer monitor, i had same problem on my 6.06 ubuntu, but not in my 8.04.  in my 6.06 i change "nv" to "nvidia" and set the monitor setting like this: (both in /etc/X11/xorg.conf)

SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
thanks mohammed i will try it out..:-)

---

### Post by Lexicon101 on 2008-08-02
Sir, you should definitely go to the official nVidia website and download the official linux drivers. Of course nv's nice and all.. but I wouldn't use it over the real thing. Once you download the driver file (into your home folder), right click on it in nautilus (file browser), click properties, then permissions, checking the box that says "allow executing the file", then type into a terminal (applications -> accessories -> terminal) or hit ctrl+alt+f1-f3 (ctrl+alt+f7 to get back to GUI) and type in ```
sudo /etc/init.d/gdm stop
``` Which will stop your x-server.. (DON'T DO ANY OF THIS UNTIL YOU KNOW THE WHOLE PROCESS, BECAUSE TURNING BACK ON YOUR GRAPHICS COMES AT THE END!) then hit ```
ls
``` to list the files in your home folder. Find the one with "nvidia" in it, and hit "sudo ./*nvidia filename*" it should install the "nvidia" driver on your computer. when it asks you whether or not you want to replace the existing "xorg.conf" file, let it do so. once that's done, type in "sudo /etc/init.d/gdm start" which will turn back on the graphical interface, allowing you to login again. (sorry. it logs you out of everything but the commandline part of ubuntu. save everything before you turn off gdm.) If your controls work perfectly in regards to the mouse and keyboard, rejoice, you're done! if your mouse isn't scrolling, or it's behaving funny.. you may have to hit alt+f2 (You'll still be in graphical mode after hitting this one. it's a nice little tool.), and type in ```
gksu gedit
``` then open your xorg.conf file, looking somewhere other than me about how to fix that, if copying your "pointer" section doesn't fix it.

So, in essence,
1: Download driver. Set as executable.
2: turn off graphics, going into only command line.
3: list files, execute driver installer.
4: follow installer's instructions, allowing it to replace your xorg.conf.
5: restart gdm. Hope everything goes smoothly.
6: *contingent upon condition in last step being met* DANCE! YOU WIN!
:lolflag:

---

### Post by Lexicon101 on 2008-08-02
> **mohammadrizki said:**
> i use gforce2mx and old acer monitor, i had same problem on my 6.06 ubuntu, but not in my 8.04.  in my 6.06 i change "nv" to "nvidia" and set the monitor setting like this: (both in /etc/X11/xorg.conf)

SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection

That's just a name for the resolution... Anyway, I'd say use the nvidia installer's auto-xorg-fixer.

(sorry for the double post.)

---

### Post by nommo777 on 2008-08-02
man u rock..:-)

---

### Post by mohammadrizki on 2008-08-02
oh, and nommo777 i also had to set the monitor refresh rate manually.  My xorg.conf was like:

```

Section "Monitor"
    Identifier    "Acer AC501"
    Option        "DPMS"
    HorizSync    30-75
    VertRefresh    50-85
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA [GeForce 2MX 400]"
    Monitor        "Acer AC501"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

You can get the manual monitor refresh rate setting through modeline generator.  I followed guide from here [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973).

---

### Post by nommo777 on 2008-08-02
> **Lexicon101 said:**
> That's just a name for the resolution... Anyway, I'd say use the nvidia installer's auto-xorg-fixer.

(sorry for the double post.)
does that mean i have to uninstall any existing drivers, how do i do that??

---

### Post by nommo777 on 2008-08-04
well guys, it seems that old nvidia cards and ubuntu just dont go well together, so i decided to install ubuntu in another system with a new VIA graphics and AMD 64, and now it works like a charm. i didn't even have to set anything by myself, the screen res was detected correctly.i am now downloading the required updates.Thank u all for your support..

---

### Post by Lexicon101 on 2008-08-04
No problem. And sorry, I just remembered about this thread. You wouldn't have to uninstall old drivers. Just change xorg.conf to point to the nvidia driver, not NV. The old drivers can sit there and pout. (Of course, if you constantly find yourself low on disk space, uninstalling things when you don't need them is a good practice. (of course.. it can also lead to problems. Just do so whenever you feel you don't need it and it won't cause problems to remove it.))

---

