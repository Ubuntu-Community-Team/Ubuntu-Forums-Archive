---
title: "display resolution"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by f6azm on 2012-09-07
Hello,
I have just installed UBUNTU 12.04 LTS on my laptop Fujitsu Siemens Amilo Si 1520.
I am very impressed, everything worked very well, Firefox connected to the WEB immediately without any configuration adjustement. I was able to install a lot of softwares without any problem. I was ready to use UBUNTU in place of windows but :

I use this laptop with an external display HP L2035 connected to the DVI-I output.
It's native resolution is 1600 x 1200 @ 60Hz. But the only resolution I can select with Ubuntu is 1024 x 768.

The VGA is Intel Mobile 945 GM Express Integrated Controller and the driver seems to be installed.

The HP display is not recognised.

I tried to find a solution on the forums, but there is no file xorg.conf in etc/x11. Data seem to be related to older versions.

Ubuntu seems to be too automated on this topic, it is much easier to choose any resolution in windows.

I'am afraid I will go back to windows if there is no easy solution.

Best regards

---

### Post by androssofer on 2012-09-07
> **f6azm said:**
> Hello,
I have just installed UBUNTU 12.04 LTS on my laptop Fujitsu Siemens Amilo Si 1520.
I am very impressed, everything worked very well, Firefox connected to the WEB immediately without any configuration adjustement. I was able to install a lot of softwares without any problem. I was ready to use UBUNTU in place of windows but :

I use this laptop with an external display HP L2035 connected to the DVI-I output.
It's native resolution is 1600 x 1200 @ 60Hz. But the only resolution I can select with Ubuntu is 1024 x 768.

The VGA is Intel Mobile 945 GM Express Integrated Controller and the driver seems to be installed.

The HP display is not recognised.

I tried to find a solution on the forums, but there is no file xorg.conf in etc/x11. Data seem to be related to older versions.

Ubuntu seems to be too automated on this topic, it is much easier to choose any resolution in windows.

I'am afraid I will go back to windows if there is no easy solution.

Best regards

did you open the Display system settings?

click the ubuntu logo on the top left of the desktop, this opens the dash, then search for displays.

It gives nice options..

or if you have a nvidia card and installed its drivers. search 'nvidia' in the dash and it has its own settings menu.. it will configure xorg.conf for you.

---

### Post by cortman on 2012-09-07
If there's no other options in Displays, please post the output of these commands (each line is a different command).

```
xrandr
lspci | grep -i vga
lshw -C video
```

---

### Post by f6azm on 2012-09-08
> **cortman said:**
> If there's no other options in Displays, please post the output of these commands (each line is a different command).

```
xrandr
lspci | grep -i vga
lshw -C video
```

thank you for your answer.
here are the data requested :

**_  xrandr_**
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS1 connected (normal left inverted right x axis y axis)
   1280x800       59.9 +
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)

_**lspci | grep -i vga**_

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

_**lshw -C video[/CODE][/QUOTE]**_

 does not output any data related to video but with lshw only I can extract these data :

        *-display:0
             description: VGA compatible controller
             produit: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             fabriquant: Intel Corporation
             identifiant matériel: 2
             information bus: pci@0000:00:02.0
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             ressources: irq:16 mémoire:dc100000-dc17ffff portE/S:1800(taille=8) mémoire:c0000000-cfffffff mémoire:dc200000-dc23ffff
        *-display:1 NON-RÉCLAMÉ
             description: Display controller
             produit: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             fabriquant: Intel Corporation
             identifiant matériel: 2.1
             information bus: pci@0000:00:02.1
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration: latency=0
             ressources: mémoire:dc180000-dc1fffff

Thank you for your help
Regards
 JM

---

### Post by cortman on 2012-09-08
This is strange- it shows that VGA is connected but not DVI. Are you sure you don't have it plugged into VGA?
Have a look at [this wiki page]("https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions") for info on how to add a resolution mode.

---

