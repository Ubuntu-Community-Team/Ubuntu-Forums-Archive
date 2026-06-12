---
title: "[SOLVED] abit AB9 + SATA II + GeForce 8600 GT"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by All the names were taken on 2008-06-20
I'm posting this because it took about 4 days of scouring the forums and other tech sites to get Ubuntu running without a hitch and want to solve the problems for others having similar issues with the same hardware.

**abit AB9:**
so apparently the BIOS and mobo can't make babies together. The problem I had was getting Ubuntu to recognize that there was an SATAII drive for partitioning. But it kept insisting only the IDE was connected. After messing around with BIOS updates and pin connections to no avail, i noticed how the SATA were setup on the mobo. it looks like:

```

[SATA 5]  [EMPTY 3]  [SATA 1]
[SATA 6]  [EMPTY 4]  [SATA 2]

```

The strange thing about the BIOS and mobo is that if you plug the SATA drive into [SATA 2] it reads as SATA 3, where the [EMPTY 3] is supposed to be. I have no idea if that has any real bearing on the installation, but when plugged in my hard drive to [SATA 6] Ubuntu recognized it immediately and installation went smoothly.  So apparently I can't get multiple SATA installed with the ab9, but it can recognize an IDE with the SATA.  I blame the BIOS.


**GeForce 8600 GT**

I originally messed around with Ubuntu's hardware drivers and modules to no avail. So I went to NVIDIA's site and they have an linux install (my version NVIDIA-Linux-x86_64-173.14.09-pkg2.run). However, their instructions are not so intuitive so just follow Compiz installation guide located [COLOR="Blue"]http://compiz.org/NVidia[/COLOR]. Their instruction says to run ```
/etc/default/linux-restricted-modules
``` but it should be ```
/etc/default/linux-restricted-modules-common
``` and change the bottom line ```
DISABLED_MODULES=""
``` to ```
DISABLED_MODULES="nv nvidia_new"
```. Following the instructions, I then hit a snag after renaming to nvidia-is.ko because I kept getting a message that terminal couldn't find nvidia-is module.  Also running ```
sudo apt-get remove --purge nvidia-glx
``` didn't completely remove old drivers because when i did the modprobe I got an error message.  But i restarted the system anyway and sure enough, Ubuntu had reverted to a default module or something and the Applications > System Tools > nvidia x server settings wasn't working. Then an imaginary gnome suggested I run the driver installation again without purging and this time don't allow nvidia to search for a kernal compiler (or something) from their site (it asks on the 2nd or 3rd [OK] screen).  When i ran the modprobe after installation, it recognized the drives plus something else with the numbers 0, 44, and 0660. Follow Compiz directions again on editing the xorg.conf file and make sure to ```
Option         "AddARGBGLXVisuals" "true"
Option         "DisableGLXRootClipping" "true"
``` and ```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
``` if they are not in there. Also note the Compiz configuration ```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        **Modes      "1440x900"**
    EndSubSection
EndSection

```

I think the bolded part is the resolution for the login screen. I changed to 1024x768 because of my crappy crt monitor.  

Now if you restart the installed driver module should be running but your screen resolution might be reset. Go to Terminal and run the line ```
gksudo nvidia-settings
``` and make the changes necessary.  MAKE SURE TO CLICK 'SAVE X CONFIGURATION FILE.' run sudo gedit /etc/X11/xorg.conf to double check that the lines added in Compiz instructions are in there, and if not add them in and the line in "subsection."  You might notice metamodes line says something like 1280x768_84 +0+0. Just delete the rest of the line except the resolution so it looks like 1280x668.  

This isn't a guide by someone experienced, I've been using Ubuntu for 1 day now and felt like sharing what I did in hopes others will avoid my headaches.

---

