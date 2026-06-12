---
title: "A problem with display size"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by onlytim2 on 2014-01-14
Hi all, I'm having a problem with my display using 13.04. I'm using an Insignia 27" flat as a monitor with a NVIDIA GF119 GeForce GF610 as my video display. The launcher and top screen cannot be seen. I followed a few ideas on the forum without success. I tried using the updater to change the driver. It shows me using (NVIDIA binary Xorg driver-nvidia-304. I tried the-307-310 with no luck. When I checked the display to attempt changing the monitor type in settings it only shows my monitor options as  (Privia Hortimation BV32) 

I would appreciate anyone who has a idea how to adjust my display.

Thanks!

Tim

---

### Post by DuckHook on 2014-01-14
> **onlytim2 said:**
> I'm using an Insignia 27" flat as a monitorI take it this is a HDTV. Please confirm.> The launcher and top screen cannot be seen.Do you mean the global menu bar and system panel? If so, is it only these or do all four edges of screen run outside of monitor? Again, if so, this is likely due to overscan on your TV and has nothing to do with Ubuntu or drivers. Must be fixed on TV. Most TVs have a setting to turn off overscan. There is so much variation among TVs that no single set of instructions exist. You must look in the documentation for your TV or search online for instructions.

If problem is not overscan, then give us following details:
What is your computer? Make, model, desktop or laptop?
How is it hooked up to TV? HDMI? DVI? VGA?
Is it connected directly? Through KVM switch? Receiver?
Post results of:```
xrandr
```

---

### Post by onlytim2 on 2014-01-14
Thanks for the come-back! Yes. It's an Insignia 27 flat with an HDMI cable from the NVIDIA video card to the TV.

 I disabled the overscan on the NVIDIA control which is on my Windows 7 on the A hard drive. I use the second drive, B for Ubuntu. Not sure if changing one will effect the results on the Ubuntu drive. 
My system is a home built desktop. MSI mother board running two Seagate 500 gig drives.

Here are the results from xrandr:
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1280x720+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1280x720       60.0*+
   1920x1080i     30.0  
   1360x768       59.8  
   1024x768       75.1     75.0     70.1     60.0  
   1440x480i      30.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   720x480        59.9  
   640x480        72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
VGA-1 disconnected (normal left inverted right x axis y axis)

---

### Post by DuckHook on 2014-01-14
I'm afraid the steps you took are very confusing to me. Overscan is a TV setting, not a NVIDIA control setting. You have to go into your TV controls to disable it, and not touch your computer at all. Once this is done, no further action is needed in either the OS or the driver.

*xrandr* shows that your TV resolution is 1280x720. Is this correct?

Also, answer all questions in previous post.> **DuckHook said:**
> Do you mean the global menu bar and system panel? If so, is it only these or do all four edges of screen run outside of monitor?

---

### Post by onlytim2 on 2014-01-14
My NVIDA control panel in Windows allows me to adjust size or allow me the option to use overscan, underscan or not reported; similar to the display function in Windows. I guess that's why I won't change.  I'll take your advice and check the TV serttings. 

Thanks for the help! I appreciate it much!

---

