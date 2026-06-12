---
title: "[SOLVED] titlebar disappears in compiz"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by jtclicker on 2008-11-18
I've searched the forums and done what I can find there, checked the Xconfig, switched to metacity and back again, window decoration is enabled, downlaoded fusion-icon, but in compiz my window borderss have disappeared and I can't shut apps down from the icons as they aren't there. It worked at first, I then did a reboot and they went! Any offers??

---

### Post by shifty_powers on 2008-11-18
what graphics adapter are you using, and are the restricted drivers being used for it?

---

### Post by jtclicker on 2008-11-18
the current updated driver (updated today) for the nvidia-glx 96 are in use

---

### Post by Helios1276 on 2008-11-18
Have you used Emerald to manage things ?

sudo apt-get install emerald

emerald --replace 

If you still get the issue, you could then add Emerald to your sessions.

---

### Post by jenkinbr on 2008-11-18
> **lduplantie said:**
> Eureka!

I had another look at my xorg.conf file, and for some reason a line went missing (I guess by my mistake)

I added in the Screen section
Option   "AddARGBGLXVisuals"  "True"

and window decoration is now functional. 

Emerald is also working.

Thank you all for your help.

Does this line exsist in your xorg.conf?```
Option   "AddARGBGLXVisuals"  "True"
```
It solved the same issue for another user.

---

### Post by Crafty Kisses on 2008-11-18
That's one of the fixes a lot of people are finding that works, there is a great HOWTO I made over a tutorials to fix it temporarily.

---

### Post by jtclicker on 2008-11-18
> **jenkinbr said:**
> Does this line exsist in your xorg.conf?```
Option   "AddARGBGLXVisuals"  "True"
```
It solved the same issue for another user.

Yeah I checked that and it is there

---

### Post by jtclicker on 2008-11-18
> **Helios1276 said:**
> Have you used Emerald to manage things ?

sudo apt-get install emerald

emerald --replace 

If you still get the issue, you could then add Emerald to your sessions.

I'll try that, thanks

---

### Post by jtclicker on 2008-11-18
> **jtclicker said:**
> I'll try that, thanks

how do i get the cube to work in emerald?

---

### Post by jtclicker on 2008-11-19
```
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Info: Couldn't bind redirected window 0x1000046 to texture
```

I get this error in compiz when the terminal is open and I switch to compiz - any ideas?

---

### Post by jtclicker on 2008-11-19
added this to the xorg.conf
```
Option         "DisableGLXRootClipping" "True"
```

restarted X solved the problem then rebooted and had the problem back

---

### Post by jtclicker on 2008-11-19
And for completeness, here is my Xorg
```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-G420"
    HorizSync       30.0 - 110.0
    VertRefresh     48.0 - 170.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX 440 with AGP8X"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1600x1200_75 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Junkieman on 2008-11-19
I had a similiar problem with 8.4 where my window decorations would disappear, switching back to metacity would leave me with these broken windows that you cant move around or close.

ALT+Click and drag anywhere in a window to move it around. you can restore the decorations by running this command in a terminal window

```
metacity --replace
```

after the decorations are restored, enable compbiz again and see if it works. do a reboot and see if the decorations are still there.

---

### Post by lakersforce on 2008-11-19
Just a comment: on my old computer I had a Nvidia card and I frequently had the same problem. After switching to a Intel integrated card I don't have that problem anymore.

---

### Post by jtclicker on 2008-11-19
> **Junkieman said:**
> I had a similiar problem with 8.4 where my window decorations would disappear, switching back to metacity would leave me with these broken windows that you cant move around or close.

ALT+Click and drag anywhere in a window to move it around. you can restore the decorations by running this command in a terminal window

```
metacity --replace
```

after the decorations are restored, enable compbiz again and see if it works. do a reboot and see if the decorations are still there.
 Thanks I'm using Compiz fusion to play around with these sequences of changes. Metacity basically turns off the compiz settings, turning compiz back on brings the problem back!

---

### Post by philinux on 2008-11-19
In the past when this happens I untick then tick the windows decoration in the Effects section.

Other thing to try is delete or rename .compiz folder. This would loose your settings if you deleted it but would restore default.
[edit] There is another config folder for compiz in .config. That would need to go too.

---

### Post by jtclicker on 2008-11-19
> **philinux said:**
> In the past when this happens I untick then tick the windows decoration in the Effects section.

Other thing to try is delete or rename .compiz folder. This would loose your settings if you deleted it but would restore default.
[edit] There is another config folder for compiz in .config. That would need to go too.

thanks, can you give me locations for these files? I've just doen a search of the file system and come up blank. thanks for taking the time!

---

### Post by philinux on 2008-11-19
> **jtclicker said:**
> thanks, can you give me locations for these files? I've just doen a search of the file system and come up blank. thanks for taking the time!

Your home folder then press ctrl h to view hidden files. One is called .compiz the other is found within the .config folder

---

### Post by jtclicker on 2008-11-19
> **philinux said:**
> Your home folder then press ctrl h to view hidden files. One is called .compiz the other is found within the .config folder

Thanks tried that and rebooted and still the same problem It also came up with the same options as I had before, cube etc

---

### Post by philinux on 2008-11-19
Have a look at processes with system monitor.

Is gtk-window-decorator running?

---

### Post by jtclicker on 2008-11-19
> **philinux said:**
> Have a look at processes with system monitor.

Is gtk-window-decorator running?

it is listed as 'sleeping' when  compiz is turned off, when I turn compiz on I only see a blank white screen on anything from the system pref or admin menu, also the terminal

---

### Post by philinux on 2008-11-19
> **jtclicker said:**
> it is listed as 'sleeping' when  compiz is turned off, when I turn compiz on I only see a blank white screen on anything from the system pref or admin menu, also the terminal

Sounds like compiz need completely uninstalling and reinstalling.
You could try

gtk-window-decorator --replace

---

### Post by jtclicker on 2008-11-19
thanks did that with synaptic, then reinstalled and STILL sam eproblem! Again, interestingly, all my old compiz options came back up ticked

---

### Post by philinux on 2008-11-19
Well then thats means a full reinstall then.:lolflag:

I'm not joking really. I've got home on it's own partition and it takes about half an hour.
If I screw it up badly thats what I do.

---

### Post by jtclicker on 2008-11-19
> **philinux said:**
> Well then thats means a full reinstall then.:lolflag:

I'm not joking really. I've got home on it's own partition and it takes about half an hour.
If I screw it up badly thats what I do.

I've got ubuntu on its own drive. Do you mean format the drive and then do a clean install from the live cd? will I have problems with grub?

---

### Post by davidsrsb on 2008-11-19
I have two PCs with this problem, both using Nvidia 7300LE
I upgraded one of these to a 8600GT and it was solved

---

### Post by jtclicker on 2008-11-19
> **davidsrsb said:**
> I have two PCs with this problem, both using Nvidia 7300LE
I upgraded one of these to a 8600GT and it was solved

so does that mean it is a driver issue?

---

### Post by Junkieman on 2008-11-20
> **jtclicker said:**
> so does that mean it is a driver issue?

it could very well be, i had this problem on a GeForce FX 5200 card, but not with my current intel integrated card. 

have you tried changing the rendering mode? [This thread]("http://ubuntuforums.org/showthread.php?t=529665") explains enabling indirect rendering, it might be worth trying it out...

---

### Post by jtclicker on 2008-11-20
> **Junkieman said:**
> it could very well be, i had this problem on a GeForce FX 5200 card, but not with my current intel integrated card. 

have you tried changing the rendering mode? [This thread]("http://ubuntuforums.org/showthread.php?t=529665") explains enabling indirect rendering, it might be worth trying it out...
 Thanks for the tip. I used the controls in the compiz fusion icon to try that and got no change at all. I've gone through all the settings in the fusion icon to try different combinations and nothing seems to work. Maybe there will be an update to the driver that will fix this. I'll report it as a bug and hopefully someone will take a look

---

### Post by jtclicker on 2008-11-20
when I used the terminal to change the rendering I got the following error messages

```
julian@julian-desktop:~$ compiz --replace --indirect-rendering &
Checking for Xgl: [1] 6635
julian@julian-desktop:~$ not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Info: Couldn't bind redirected window 0x3c00046 to texture

/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (mag) - Warn: GL_ARB_fragment_program not supported. Fisheye mode will not work.
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Info: Couldn't bind redirected window 0x3c00046 to texture


```

---

### Post by jtclicker on 2008-11-24
finally got this sorted out, with help from another forum and searching around. here's the advice I was given from the compiz forum. I tried all the changes, edited out the stuff that caused the xserver to crash and then everything worked dunno why it happened, but folk can maybe try these and see if it works for them...

```
nvidia-xconfig --add-argb-glx-visuals
```

and adding this to the xorg.conf

```
Section "Files"
	ModulePath   "/usr/lib/xorg/modules/drivers"
	ModulePath   "/usr/lib/xorg/modules/extensions/nvidia"
	ModulePath   "/usr/lib/xorg/modules"
EndSection
```

current xorg.conf that works
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
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
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-G420"
    HorizSync       30.0 - 110.0
    VertRefresh     48.0 - 170.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX 440 with AGP8X"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1600x1200_75 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection


EndSection
```

---

### Post by Junkieman on 2008-11-24
Maybe its a driver issue specific to that card... Glad you got it working, Thanks for posting the answer.

---

### Post by jtclicker on 2008-11-24
another thing to try is adding ```
Option "RenderAccel" "0"
``` to the Device part in xorg.conf

---

### Post by Mitch on 2009-01-11
Had this problem too.  The most important bit of info here is

Warn: No GLXFBConfig for depth 32

Solved on #compiz-fusion channel on freenode.  The solution is to change default depth from 16 to 24.  

I have an integrated Intel card and I upgraded from hardy to intrepid.

---

### Post by Dr.Dixie on 2009-02-04
Thank you. This has solved numerous problems I had with Compiz. I personally think this is amazingly critical, because I've been searching for something that tells me how to get my decorations back, and, POW, I've got even more than decorations. Text works, the default "zooming icon" effect doesn't merely show a white square, and I don't really doubt that 3D windows, which hadn't been working, now does. Thanks.

Actually, nope, 3D windows still isn't working. I hope I find out why soon.


!Dr.Dixie!

---

