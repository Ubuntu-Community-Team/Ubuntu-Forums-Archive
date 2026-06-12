---
title: "Few questions 16.04"
date: 2018-04-23
forum: New to Ubuntu
---

### Post by seguhi87 on 2018-04-23
So I've come to Ubuntu from Windows - landed on 16.04 very new to Linux - this is a re-install - I broke the last one reverted drivers back to Nvidia-304 from 390.48 in error and couldn't boot or get into tty :-(

Few questions

I have a Nvidia GTX560 Ti Card and in Windows I could set  my monitor (Bush TV) to 1920 x 1080 with ease via DVI to VGA - I've toyed around with additional drivers and running Nvidia-384 installed via Software -  max resolution I get in 1368x768 - I do have HDMI output via the graphics card but it seems stretched and cuts parts of the screen off - another thing is it show multiple monitors DVI-1 and VGA-1 and merges them together 

I've googled (quite a lot) and tried xrandr but I get Bad Match output error - a few sources say xrandr doesn't work with Nvidia proprietary drivers and to stick with nouveau - I don't game so tempted aslong as I get 1080p for watch videos/youtube and general usage

Is there an easy fix?

Thanks

---

### Post by sevendogsbsd on 2018-04-24
So, just running "xrandr" in a terminal produces what? This command will show all supported resolutions. Here is mine as an example:

```

[paul@bigzbox ~]$ xrandr
Screen 0: minimum 8 x 8, current 3440 x 1440, maximum 32767 x 32767
DP-0.8 connected primary 3440x1440+0+0 (normal left inverted right x axis y axis) 798mm x 335mm
   3440x1440     59.97*+  49.99  
   2560x1440     59.95  
   2560x1080     60.00  
   1920x1080     60.00    60.00    59.94    50.00  
   1720x1440     60.00  
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    59.94    59.93  
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by oldfred on 2018-04-24
you have to install the correct nVidia driver for your model card. It looks like the newest series of drivers is correct, so the 304 legacy driver for old cards would not support many of the new features of your newer card.

 nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 

The Ubuntu repository should have a current version driver that works.
If you want very newest driver which is mostly required for the very new cards you can add the ppa. Your 560 may not need very newest driver.
If you install incorrect nVidia driver you must totally purge old driver. Installing new driver does not delete old driver and then you have issues.


 nVidia install, purge if needed.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336) 
   #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 
      
 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 
      
 Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 
    
       If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by SeijiSensei on 2018-04-25
Have you tried to set the resolution using the NVIDIA Settings application?  You might have better success with that.  It's under "Settings" in my Kubuntu menu.

---

