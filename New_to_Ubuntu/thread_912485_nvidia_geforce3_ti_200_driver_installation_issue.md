---
title: "nvidia geforce3 ti 200 driver installation issue"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by ranger5664 on 2008-09-06
I have an nvidia geforce3 ti 200 graphics card for my computer that is running xubuntu. I tried to install the driver file version 96.43.05 and it gives me this error in the installation process... ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

I have tried using ENVNG for the installation but i end up running in low graphics mode until i disable the driver. The graphics driver that i install through xubuntu crashes my wireless so i am in disparate need of help installing the graphics driver that i have downloaded through the nvidia archives. Any help with this would be AMAZING!!!!!!!!!!!!!!!!

---

### Post by korgman_gr on 2008-09-18
It can be done, but, with.. strange method.

First the data. You need to download from Nvidia, this file:
NVIDIA-Linux-x86-71.86.06-pkg1.run

And create a file (xorg.conf.ti200) with this stuff
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        SubSection "Display"
                Depth   16
                Modes           "1280x1024"     "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1024x768"      "800x600"       "640x480"
        EndSubSection
        Defaultdepth    24
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "vesa"
        #       Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Option          "RenderAccel"   "true"
        Option          "NvAGP" "3"
        Option          "AllowGLXWithComposite" "true"
        Screen  0
EndSection

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
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
EndSection

Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
        Horizsync       31.5-64
        Vertrefresh     60
        #       Option "UseEdidFreqs" "1"
        Option          "ReducedBlanking"
        Gamma   1.0
EndSection

Section "DRI"
        # Access to OpenGL ICD is allowed for all users:
        Mode    0666
        # Access to OpenGL ICD is restricted to a specific user group:
        #    Group 100    # users
EndSection

Section "Extensions"
        Option          "Composite"     "Disable"
EndSection


```

> **ranger5664 said:**
> 
I have tried using ENVNG for the installation but i end up running in low graphics mode until i disable the driver.

Good, reinstall the driver with envy (7series). This is not necessary but with envy you have all the neccessary files to compile your own driver ;)

Now. In the low graphics mode DON'T continue, DON'T press a thing :)

Instead press ctrl+alt+F2
Login
sudo su
sh /home/YourUser/Desktop/nvidia/NVIDIA-Linux-x86-71.86.06-pkg1.run --no-x-check -a --no-runlevel-check (I know, it's insane)
cp xorg.conf.ti200 /etc/X11/xorg.conf
reboot

I hope everything is ok now :)

Now you play enemy territory wolfstein ;)

---

### Post by ranger5664 on 2008-10-04
Thank you so much for all of your help. And how did you know that i like et?

---

### Post by geohei on 2009-08-29
> **korgman_gr said:**
> It can be done, but, with.. strange method.

First the data. You need to download from Nvidia, this file:
NVIDIA-Linux-x86-71.86.06-pkg1.run
...
How do you know which version to take?
I use a Pentium4 1.8 GHz on the computer I have a GeForce3 Ti200 installed.

Latest ones ...

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
> Linux IA32
Latest Version: 185.18.36
Latest Legacy GPU version (71.86.xx series): 71.86.11
Latest Legacy GPU version (96.43.xx series): 96.43.13
Latest Legacy GPU version (173.14.xx series): 173.14.20
...

---

### Post by Bachstelze on 2009-08-29
The cards supported by each version of the driver are listed in [Appendix A]("http://us.download.nvidia.com/XFree86/Linux-x86/96.43.13/README/appendix-a.html") of the README.

Anyway, the 96. version of the drivers is available in the repositories, so you shouldn't have to install them manually. Just open the restricted drivers manager, and it should do the trick.

---

### Post by geohei on 2009-08-30
You were right. Many thanks. I missed that part.

However I realized that the mistake I did was that I didn't change the /etc/X11/corg.conf file. I replaced my xorg.conf file with the one from korgman_gr (see above, second posting in this thread) and it worked!

Question 1 ... where do people get this xorg.conf from? It's not published on the NVIDIA site.

Question 2 ... I lost my Visual Effects. Neither Normal, nor Extra works any more. I get the message:
> The Composite extension is not available

Any ideas?

Thanks,

---

### Post by geohei on 2009-08-31
Some more testing ...

In the following, I use the xorg.cong filesize to show what the capabilities of the used graphics drivers are.

a. original graphics drivers
xorg.conf: 1037 bytes
Visual Effects: None
Resolutions: 800x600, 640x480, 400x300, 320x240

When I install the NVIDIA graphics driver, the installation also replaces the xorg.conf file.

b. NVIDIA drivers activated, installed xorg.conf
xorg.conf: 1172 bytes
Visual Effects: Extra
Resolutions: 640x480, 320x240

Only when I manually change the xorg.conf, I get access to higher resolutions, but I loose the Visual Effects.

c. NVIDIA drivers activated, manually xorg.conf (see 2nd posting in this thread)
xorg.conf: 2816 bytes
Visual Effects: None
Resolutions: 1280x1024, ... 320x240 (14 in total)

Question 3 ... why don't the NVIDIA drivers install the correct xorg.conf file right away during the installation process.

Regards,

---

### Post by Bachstelze on 2009-08-31
> **geohei said:**
> 
Question 3 ... why don't the NVIDIA drivers install the correct xorg.conf file right away during the installation process.

Because there is no "correct xorg.conf" for everyone. Do this:

```
sudo rm /etc/X11/xorg.conf
sudo touch /etc/X11/xorg.conf
sudo nvidia-xconfig

```

Then restart X and tell me what gives.

---

### Post by geohei on 2009-09-10
> **HymnToLife said:**
> ...
```
sudo rm /etc/X11/xorg.conf
sudo touch /etc/X11/xorg.conf
sudo nvidia-xconfig

```...
This works indeed, but it doesn't spit out the same xorg.conf as above (2nd posting in this thread).

"My" /etc/X11/xorg.conf looks like this:
```
root@ubuntu904hol:/home/geohei# cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Sat Jan 24 20:04:42 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
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
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```
Be advised that Visual Effects "Normal" and "Extra" are selectable with this xorg.conf file, but create partially corrupt window output (e.g. requester windows appear blank). The effects seem to work however.

Why the corrupt windows?

The xorg.conf file from the 2nd article in this thread doesn't allow Visual Effects "Normal" and "Extra". Only "None". Trying "Normal" or "Extra" generates the error message:
> The Composite extension is not available
How can I make the effects work properly?

Thanks!

---

### Post by Bachstelze on 2009-09-10
Look at the bottom of your xorg.conf:

```
Section "Extensions"
        Option          "Composite"     "Disable"
EndSection
```

That should tell you something.

---

### Post by geohei on 2009-09-10
... which means that "Normal" and "Extra" Visual Effects are disabled?

Can you confirm.

Thanks,

---

### Post by korgman_gr on 2010-12-12
Sorry, for the late "answer".

Just wanted to clarify that I was unable to work with the 9x series driver from nvidia. For that reason I purposed the 7x series driver (that worked with Slackware and an old - now - version ubuntu).

Now I try to work with this card with ubuntu-10.04 without success, so as I searched I bumped to my self :)

I will try this solution though.
[http://ubuntuforums.org/archive/index.php/t-1467153.html](http://ubuntuforums.org/archive/index.php/t-1467153.html)

---

### Post by geohei on 2010-12-31
> **Bachstelze said:**
> ...
```
Section "Extensions"
        Option          "Composite"     "Disable"
EndSection
```
...
This option doesn't allow "Normal" and "Extra". That's all.

I was looking for the actual drivers which permit to properly use "Normal" and "Extra" features. This option doesn't help making things working.

Thanks,

---

