---
title: "S-video output to TV"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by linuxnoob53108 on 2008-09-28
I'm trying to hook my laptop up to my tv (to use my tv as a monitor with a wireless mouse and keyboard from couch, web surfing could take on a whole new life!) using an s-video cable. I am not sure how to check what video card I have so I'm no help there. I did run xrandr and here is the output:

jc@jc-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)

Any advice would be great!

---

### Post by sisco311 on 2008-09-28
post the output of:
```
lshw -C display
```

---

### Post by linuxnoob53108 on 2008-09-28
jc@jc-laptop:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon RV250 [Mobility FireGL 9000]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master vga_palette cap_list
       configuration: latency=32 mingnt=8

---

### Post by mikewhatever on 2008-09-28
<sudo lshw -C display> should show your video card info. Is there a problem with svideo?

---

### Post by linuxnoob53108 on 2008-09-28
jc@jc-laptop:~$ sudo lshw -C display
[sudo] password for jc: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon RV250 [Mobility FireGL 9000]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master vga_palette cap_list
       configuration: latency=32 mingnt=8


When I plug the s-video cable into the tv, I switch the the s-video source and no signal is seen on the tv, I've been searching the forums and can't quite seem to find what I'm looking for...Any advice on getting this working would be great.

---

### Post by robalcorn on 2008-09-28
Did you try rebooting with svga cable plugged into your computer and tv?

---

### Post by linuxnoob53108 on 2008-09-28
Still no luck after the reboot

---

### Post by robalcorn on 2008-09-28
Did you install the ati catalyst software from applications/add-remove/? if you didnt. Use it and set it to "all available sources" than search for "catalyst" that might help you out.

---

### Post by linuxnoob53108 on 2008-09-28
No, I'll give that a try and post back, thanks!

---

### Post by linuxnoob53108 on 2008-09-28
Alright, I have the catalyst installed but when I try to open the application it gives me the following error:

"No ATI graphics driver installed, or the ATI driver is not functioning properly. Please install the ATI driver appropriate for your ATI hardware, or configure using aticonfig"

How would I know if the driver is installed properly, or what kind of configuration would be down with aticonfig?

Thanks!!!

---

### Post by linuxnoob53108 on 2008-09-30
bump

---

### Post by robalcorn on 2008-09-30
Looks like your card is no longer supported by ATI the last driver is 8.28.8 on August 18, 2006. But here is the link if you want to try to install it. Maybe someone here can help out with that as I use Nvidia.

[http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html](http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html)

---

### Post by SavoyTruffle on 2008-10-03
I'm at work, so I can't verify this, but I believe I got that message before I realized I had to execute "sudo aticonfig --initial" (or something like that) when you first install the driver.  If you haven't done that yet, I think that might clear that error up. :)

---

