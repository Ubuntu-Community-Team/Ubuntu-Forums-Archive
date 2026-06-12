---
title: "A few startup issues with 8.04"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Totalchaos02 on 2008-04-26
I finally installed Ubuntu on my desktop when 8.04 released and am having 2 issues that have pretty much kept this OS from being perfect. I am new to Ubuntu so if you need to get any information from logs and such just tell me how and I will get it. Anyway here are the problems.

I have an ATI radeon x1300 graphics card. I installed the proprietary driver because I had read that the open source driver does not work with this card. Now before doing so I had some control over my two screens in the screen resolution menu however if I unchecked clone output it did nothing and I could not get a proper resoultion on my primary screen.

After installing the driver I have two issues with it. One, both my screens have to be the same resolution, which is fine for my primary screen but my secondary cannot run at 1440 x 900. The second is that during login my primary screen goes back to a very odd resolution and then loads only after logging in (a minor problem but still worth mentioning). And with all that I cannot extend my desktop onto the second screen, and I have no control in the screen resolution menu anymore.

My second problem is flash. When Firefox gave me the plug in options for flash I downloaded the free version rather than flashes proprietary version (which was probably stupid because the latter worked great on my laptop). Now when anything flash shows up I have to click on it to initiate it (which is actually kind of nice but I have noscript anyway) and when I do I have no sound. I have tried manually installing the flash plug in but despite it telling me that it worked it has not. 

I know I had a lot in there but any help is appreciated. Thank you in advance.

---

### Post by Totalchaos02 on 2008-04-26
bump

---

### Post by Totalchaos02 on 2008-04-26
wow this forum moves fast

---

### Post by seamustry on 2008-04-26
i don't know about your ati problem but for flash you should get "ubuntu restricted extras" and that will give you a bunch of other more commonly used software...you can get it in synaptics package manager

---

### Post by Totalchaos02 on 2008-04-26
Thanks for the advice but I disabled the other plug in and it didn't work.

---

### Post by Totalchaos02 on 2008-04-26
So I think I managed to switch to the nonfree flash plugin but I still have no sound. Any one else have issues with flash not having sound?

---

### Post by Totalchaos02 on 2008-04-26
Nevermind on that last post, I have flash fully working. Anyone had advice on my other problem?

---

### Post by madjr on 2008-04-26
> **Totalchaos02 said:**
> wow this forum moves fast

the first week after a release the forums are like this...

not too many experts around in "Absolute Beginner Talk" forum since they're busy solving their own issues and that of probably a family member.

---

### Post by madjr on 2008-04-26
> **Totalchaos02 said:**
> Nevermind on that last post, I have flash fully working. Anyone had advice on my other problem?

where did you get your Ati driver from? the repos?

envyNG?

or did you download from the ati website?

---

### Post by Totalchaos02 on 2008-04-26
As soon as I had booted up 8.04 I had a message saying that restricted drivers needed to be used, so I activated it and restarted. As soon as I did that my primary screen was at the native resolution (1440 x 900), but my secondary screen matched that resolution. If I disable it they both run at 1280 x 1024 (which is native to my second screen).

---

### Post by Totalchaos02 on 2008-04-26
bump

---

### Post by ugm6hr on 2008-04-26
I don't use dual monitors, but the most recent ATI drivers are available direct from ATI - or using envy.

See the link in my signature - Graphics cards.

---

### Post by Totalchaos02 on 2008-04-26
I used envy to get the latest driver but it hasn't fixed any of my issues. Thanks anyway.

---

### Post by Totalchaos02 on 2008-04-26
Ok so I have been searching google hardcore and found this xorg.conf which worked. I have both monitor working with my second an extension of my primary monitor. Both are running at 1280x1024. Now I am totally new to this kind of thing so I am curious if anyone would know how to modify it to change my primary screen to be 1440x900. Thanks for any help.
```

Section "ServerLayout"
Identifier "Server Layout"
Screen 0 "Screen0"
InputDevice "Mouse1" "CorePointer"
InputDevice "Keyboard1" "CoreKeyboard"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
RgbPath "/etc/X11/rgb"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"

SubSection "extmod"
Option "omit xfree86-dga" # don't initialise the DGA extension
EndSubSection
Load "glx"
Load "i2c"
Load "bitmap"
#Load "ddc" # this is probably safe to turn on
Load "dri"
Load "extmod"
Load "freetype"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Keyboard1"
Driver "kbd"
Option "AutoRepeat" "500 30"
# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
Option "XkbRules" "xfree86"
Option "XkbModel" "pc101"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Mouse1"
Driver "mouse"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Device" "/dev/input/mice"
EndSection

Section "Monitor"
Identifier "Monitor0"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Monitor1"
Option "DPMS"
EndSection

Section "Device"
Identifier "ATI Graphics Adapter"
Driver "fglrx"

# === disable PnP Monitor ===
Option "NoDDC" # this probably isn't necessary?


# vendor=1002, device=4e45
Option "no_accel" "no"
Option "no_dri" "no"


Option "mtrr" "off" # disable DRI mtrr mapper, driver has its own code for mtrr
#Option "TVHSizeAdj" "0"
#Option "TVVSizeAdj" "0"
#Option "TVHPosAdj" "0"
#Option "TVVPosAdj" "0"
#Option "TVHStartAdj" "0"
#Option "TVColorAdj" "0"
#Option "GammaCorrectionI" "0x00000000"
#Option "GammaCorrectionII" "0x00000000"
# === OpenGL specific profiles/settings ===

Option "Capabilities" "0x00008000"
# Note: When OpenGL Overlay is enabled, Video Overlay
# will be disabled automatically
# === Video Overlay for the Xv extension ===
Option "VideoOverlay" "on"
# === OpenGL Overlay ===
Option "OpenGLOverlay" "off"
# === Center Mode (Laptops only) ===

Option "CenterMode" "off"
# === Pseudo Color Visuals (8-bit visuals) ===
Option "PseudoColorVisuals" "off"
# === QBS Management ===
Option "Stereo" "off"
#Option "StereoSyncEnable" "1"
# === FSAA Management ===
Option "FSAAEnable" "no"
#Option "FSAAScale" "1"
#Option "FSAADisableGamma" "no"
#Option "FSAACustomizeMSPos" "no"
#Option "FSAAMSPosX0" "0.000000"
#Option "FSAAMSPosY0" "0.000000"
#Option "FSAAMSPosX1" "0.000000"
#Option "FSAAMSPosY1" "0.000000"
#Option "FSAAMSPosX2" "0.000000"
#Option "FSAAMSPosY2" "0.000000"
#Option "FSAAMSPosX3" "0.000000"
#Option "FSAAMSPosY3" "0.000000"
#Option "FSAAMSPosX4" "0.000000"
#Option "FSAAMSPosY4" "0.000000"
#Option "FSAAMSPosX5" "0.000000"
#Option "FSAAMSPosY5" "0.000000"
# === Misc Options ===
Option "UseFastTLS" "2"
Option "BlockSignalsOnLock" "on"
Option "OverlayOnCRTC2" "0"
Option "IgnoreEDID" "off"
Option "HSync2" "31.5-70" #Second monitor horizontal sync
Option "VRefresh2" "50-75" #Second monitor vertical sync
Option "ScreenOverlap" "100" # Pixels for Overlapping. Set to 0 to disable
Option "NoTV" "yes"
Option "TVStandard" "NTSC-M"
Option "UseInternalAGPGART" "no"
Option "ForceGenericCPU" "no"
Option "KernelModuleParm" "agplock=0" # AGP locked user pages: disabled
Option "DesktopSetup" "Horizontal,Reverse"
Option "ForceMonitors" "crt1,crt2,notv"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "ATI Graphics Adapter 2"
Driver "fglrx"
BusID "PCI:1:0:0"
Screen 1
EndSection

Section "Screen"
Identifier "Screen0"
Device "ATI Graphics Adapter"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x1024" "1024x768"
EndSubSection
EndSection

Section "Screen"
Identifier "Screen1"
Device "ATI Graphics Adapter 2"
Monitor "Monitor1"
DefaultDepth 24
SubSection "Display"
#Viewport 0 0
Depth 24
Modes "1280x1024" "1024x768"
EndSubSection
EndSection

Section "DRI"
# Access to OpenGL ICD is allowed for all users:
# Access to OpenGL ICD is restricted to a specific user group:
# Group 100 # users
# Mode 0660
Mode 0666
EndSection
```

---

### Post by madjr on 2008-04-26
> **Totalchaos02 said:**
> I used envy to get the latest driver but it hasn't fixed any of my issues. Thanks anyway.

i have an nvidia card. So instead of using the the monitor setup tool in ubuntu, i use the tool that official nvidia tool that comes with the drivers (nvidia-settings)

[IMG]http://www.ismprofessional.net/pascucci/wp-content/uploads/nvidia-settings.png[/IMG]

am not totally sure but there might be a similar Ati tool probably.

Also what you need is not to "clone". The tool in Ubuntu is a bit basic (but being worked on) and only works well with 2 monitors of same resolution.

---

### Post by madjr on 2008-04-26
i think it has to do with these lines:

> Section "Screen"
Identifier "Screen0"
Device "ATI Graphics Adapter"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x1024" "1024x768"
EndSubSection
EndSection

Section "Screen"
Identifier "Screen1"
Device "ATI Graphics Adapter 2"
Monitor "Monitor1"
DefaultDepth 24
SubSection "Display"
#Viewport 0 0
Depth 24
Modes "1280x1024" "1024x768"
EndSubSection
EndSection

but not totally sure.

Remember to back it up first.

leave the first monitor as is in the file, just change the second one to the resolution it can support.

---

### Post by Totalchaos02 on 2008-04-26
I have tried modifying it a few ways, its always extended at login but past that it reverts backed to clone with my primary at 1440x900 and my secondary at some very strange resolution.

---

### Post by Totalchaos02 on 2008-04-27
A quick update here, I managed to use aticonfig to setup everything but I still have one problem. My current resolution is 2560 x 1024 (1280 x 1024 + 1280 x 1024). If I use the command sudo aticonfig --mode2=1440x900,1280x1024 my resolution becomes 2880 x 900. Any ideas on why this might be happening?

---

