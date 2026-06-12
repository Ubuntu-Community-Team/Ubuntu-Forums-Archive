---
title: "Need help with Display please"
date: 2020-04-30
forum: New to Ubuntu
---

### Post by gonmog on 2020-04-30
this is my screen resolution // Screen 0: minimum 8 x 8, current 2560 x 1440, maximum 32767 x 32767

no matter what distro i try out  it seems I am unable to switch from 600 or what ever it is to normal size 

any help please

---

### Post by dino99 on 2020-04-30
Usually user does not need to make tweaks as the system auto set the hardware config. Indeed that hardware has to be found and well identified (glance at System Settings)

---

### Post by sdsurfer on 2020-05-01
GPU information?
```

lspci | grep VGA

```
This will tell you what drivers are in use. You can then go To Software Updates and see if it's using the correct driver.

---

### Post by NM5TF on 2020-05-01
> **gonmog said:**
> this is my screen resolution[COLOR="#FF0000"] // Screen 0: minimum 8 x 8, current 2560 x 1440, maximum 32767 x 32767
[/COLOR]
no matter what distro i try out  it seems I am unable to switch from 600 or what ever it is to normal size 

any help please

that looks like a partial readout from xrandr.....is that what you are using to change your resolution ???

[https://xorg-team.pages.debian.net/xorg/howto/use-xrandr.html](https://xorg-team.pages.debian.net/xorg/howto/use-xrandr.html)

we need more info about your hardware....do you have inxi installed ?? if not then   [COLOR="#FF0000"]sudo apt-get install inxi[/COLOR] will install it

after install enter in a terminal 

```
inxi -G
```

this will tell us a lot about your system

tommy

---

### Post by gonmog on 2020-05-16
System-Product-Name:~$ inxi -G
Graphics:  Card: NVIDIA GP104 [GeForce GTX 1070]
           Display Server: x11 (X.Org 1.20.5 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 2560x1440@144.00hz
           OpenGL: renderer: GeForce GTX 1070/PCIe/SSE2
           version: 4.6.0 NVIDIA 440.82


Thank u

---

### Post by CelticWarrior on 2020-05-16
Please find out the monitor's native resolution which is the aim for the setup.
With Nvidia drivers properly installed the only reason for the system not to recognize and adjust itself automatically for the native resolution is the use of old analog VGA connections or some digital/analog converter to use an old monitor. Please describe the monitor itself and how is it connected.

---

### Post by NM5TF on 2020-05-17
@gonmog...

have you tried disabling the nvidia drivers and use nouveau to see if that fixes your display problem ???

to test it temporarily do this procedure...go here  [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

you would add the word [COLOR="#FF0000"]nouveau[/COLOR] to the end of the line after quiet splash...

if it fixes your problem, then continue with the 2nd procedure to make it permanent...

tommy

---

