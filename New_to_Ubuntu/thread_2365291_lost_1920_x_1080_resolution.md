---
title: "lost 1920 x 1080 resolution"
date: 2017-07-04
forum: New to Ubuntu
---

### Post by newblank25 on 2017-07-04
lost 1920 x 1080 resolution and it reverted to 1024 x 768. I checked system settings but there is no option to change it back. Is it a problem with video driver? ran xrand and this resolution isn't an option.any help would be appreciated

---

### Post by newblank25 on 2017-07-04
i ran this & here it is
xrandr -q
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
then i ran
cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
then i ran this
xrandr --newmode "1920x1080" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync

then ran this
[COLOR=#BF0000][FONT=&quot]xrandr --addmode VGA1 "1920x1080"
 but when i check display settings there still wasn't 1920 x 1080 option[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2017-07-04
If we had some info here maybe someone could help.
Run This in the terminal:
```
inxi -SG
```
Paste back the output here.
You may have to install inxi first.
```
sudo apt-get install inxi
```
This may help getting you more help here.

---

### Post by newblank25 on 2017-07-04
Rechecked display settings & it was there but got message input signal out of range change settings to 1600x900 60 hz. how can i change input signal?

---

### Post by newblank25 on 2017-07-04
Kernel: 4.4.0-83-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Graphics:  Card: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1280x720@59.86hz
           GLX Renderer: Mesa DRI Intel Ivybridge Desktop
           GLX Version: 3.0 Mesa 12.0.6

---

### Post by #&amp;thj^% on 2017-07-04
> **newblank25 said:**
> Kernel: 4.4.0-83-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Graphics:  Card: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1280x720@59.86hz
           GLX Renderer: Mesa DRI Intel Ivybridge Desktop
           GLX Version: 3.0 Mesa 12.0.6
Ok lets look here:
```
cvt 1920 1080 60
```
Again paste back the output.
I have to jet  for the evening...I'll check back tomorrow.

---

### Post by Autodave on 2017-07-05
This is just my way of thinking, but if I had a resolution that worked before and doesn't work now, I would be looking for a hardware issue.

How is monitor connected to PC: VGA, DVI, HDMI, ?  Whatever way, have we made sure that connections are secure? Have we tried another cable?

---

### Post by newblank25 on 2017-07-05
it is dvi to vga cable
cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
i thought it was adapter from dvi to vga  so i got another one but still no change.  It seems with either adapter it isn't very secure. maybe I should try another adapter.

---

### Post by #&amp;thj^% on 2017-07-06
> **newblank25 said:**
> it is dvi to vga cable
cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
i thought it was adapter from dvi to vga  so i got another one but still no change.  It seems with either adapter it isn't very secure. maybe I should try another adapter.

When you think all your "hardware and related" (Includeing Cords) is sound.
You may want to add this:
Suggested:
```
xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA-0 "1920x1080_60.00"
xrandr --output VGA-0 --mode "1920x1080_60.00"

```
However it should just set to the proper resolution with out user intervention.
And check the driver in use with:
```
lspci | grep VGA ; lsmod | grep "kms\|drm" ; find /dev -group video ; cat /proc/cmdline ; find /etc/modprobe.d/; glxinfo | grep -i "vendor\|rendering" ; grep LoadModule /var/log/Xorg.0.log
```

Mine Shows:
```
01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] (rev a1)
nvidia_drm             45056  1
nvidia_modeset        798720  4 nvidia_drm
drm_kms_helper        126976  2 i915,nvidia_drm
drm                   299008  5 i915,nvidia_drm,drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
/dev/fb1
/dev/dri/card0
/dev/dri/renderD128
/dev/dri/card1
/dev/dri/renderD129
/dev/fb0
BOOT_IMAGE=/boot/vmlinuz-linux root=UUID=68f9dde1-4e57-4a28-ae73-f38a0de6e84d rw quiet resume=UUID=c58b038b-7a51-48e9-8008-1f53fef7ad95
/etc/modprobe.d/
/etc/modprobe.d/nouveau_blacklist.conf
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
    GL_NV_path_rendering, GL_NV_pixel_data_range, GL_NV_point_sprite, 
    GL_NV_path_rendering, GL_NV_pixel_data_range, GL_NV_point_sprite, 
    GL_NV_packed_float_linear, GL_NV_path_rendering, 
[    14.949] (II) LoadModule: "glx"
[    16.753] (II) LoadModule: "nvidia"
[    17.136] (II) LoadModule: "fb"
[    17.148] (II) LoadModule: "wfb"
[    17.157] (II) LoadModule: "ramdac"
[    18.016] (II) LoadModule: "dri2"
[    18.941] (II) LoadModule: "libinput"


```

---

