---
title: "Black screen after changing resolution"
date: 2012-09-24
forum: New to Ubuntu
---

### Post by Valdis1 on 2012-09-24
Hi,
i have Dell Latitude E5430 laptop with Intel GMA HD 4000 graphics. Ubuntu 11.10 unrecognizes graphics and system info shows it as "Unknown". My external monitor ViewSonic VG730m is also listed as "Unknown". Maximum resolution i can take is 1024x768. Optimal resolution for monitor is 1280x1024. So i did this:

root@Latitude-E5430:~# xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
LVDS1 connected (normal left inverted right x axis y axis)
   1600x900       60.0 +   40.0  
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)

root@Latitude-E5430:~# cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

root@Latitude-E5430:~# xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

root@Latitude-E5430:~# xrandr --addmode VGA1 1280x1024_60.00

Now i can select 1280x1024 resolution in display settings, but after that i get black screen. Not "No signal", but black screen. What i should do?

---

### Post by bogan on 2012-09-25
Hi!, **valdis1,**

One thing you could try, with the hybrid Intel graphics working, is to  edit the Grub menu Script [ press 'e' with Ubuntu highlighted ] and add  to the Linux Boot line: "video=1280x1024-24@60" {without quotes}, &  press 'Crt+x' to boot.

It is reported that this can force the recognition of the Intel i915  driver.

You do not say if you also have another video card, if so there could be a conflict with the drivers.

Please Post:```
 lspci -nnk | grep -iA3 VGA
```

Chao!, **bogan**.

---

### Post by Valdis1 on 2012-09-25
Hi,
sorry, but i can't get to Grub menu. After posting to terminal i get:

root@Latitude-E5430:~# lspci -nnk | grep -iA3 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0166] (rev 09)
    Subsystem: Dell Device [1028:053c]
    Kernel driver in use: i915
    Kernel modules: i915

---

### Post by bogan on 2012-09-26
Hi!, **valdis1**,

Have you tried pressing 'Shift' whilst booting, directly after the Bios boot screen; that should force the Grub Menu to be displayed, even if you only have one OS and not a dual boot with Windows.

Chao!, **bogan.**

---

### Post by Valdis1 on 2012-09-26
Hi,
i installed mesa-utils. Now system info recognizes graphics and shows "Intel Ivybridge Mobile".
Also i entered into Grub menu,  added "video=1280x1024-24@60" line to commands, pressed F10 to boot but no results.
Do you have more ideas?

---

### Post by bogan on 2012-09-27
Hi!, **valdis,**

When does the black screen occur, before or after login?

Do you get a tty Terminal prompt if, from the black screen, you press 'Crtl+Alt+F1'? ['Crtl+Alt+F7, will/should return you to where you were before {GUI screen?}.]

If you do, login and enter Password and run ```
sudo service lightdm start
```What do you get.? - any error messages?

Alternative ideas:
1. Try editing the grub Menu script adding: "i915modeset=0" to the Linux boot line, & press 'Crtl+x'. If that does not work, try: "i915modeset=0 xforcevesa",  or: "xforcevesa" on its own.

2. There are other things you could  try in the same way, but it is rather clutching at straws, though editing out the 'quiet' and adding "verbose text" may give some clues as to what is going wrong, if the black screen is before login. eg. "acpi_osi=", acpi_osi=[COLOR=Red]\"[/COLOR]Linux[COLOR=Red]\",[/COLOR] or "vcmalloc=xxxM", { try '196' for 'xxx'}
See Post #1 in: [http://ubuntuforums.org/showthread.php?t=1613132&page=9](http://ubuntuforums.org/showthread.php?t=1613132&page=9)

3. Try booting via recovery to failsafe, low res.

4. Peruse the log files and .xsession-errors, in your home/user folder [Press 'Crtl+h' to show hidden files] Search for 'EE' & 'WW'. errors & warnings.

5+ etc, etc.....

Chao!, **bogan.**

---

