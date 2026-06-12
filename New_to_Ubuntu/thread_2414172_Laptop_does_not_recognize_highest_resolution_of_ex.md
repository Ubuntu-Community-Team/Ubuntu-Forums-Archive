---
title: "Laptop does not recognize highest resolution of external Monitor (LG Ultra)"
date: 2019-03-06
forum: New to Ubuntu
---

### Post by limnoluke on 2019-03-06
Dear Ubuntu Community,  I have a MSI GP62 laptop with Ubuntu 18.04 and I recently bought a external monitor (LG 27UD58B 27inch UHD 4K Monitor). After connecting it with an HDMI cable to my laptop it worked fine. Then, when looking at the settings I realized that the resolution was set at 1920x1080. The resolution that the monitor is capabel of is 3840x2160. However in settings>devices>displays the highest resolution is only 1920x1080.  My GPU is a NVIDIA GeForce GTX 950M. I looked up the necessary drivers with the following command:  ```
 $ ubuntu-drivers devices == /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 == modalias : pci:v000010DEd0000139Asv00001462sd0000114Cbc03sc02i00 vendor   : NVIDIA Corporation model    : GM107M [GeForce GTX 950M] driver   : nvidia-driver-390 - distro non-free recommended driver   : xserver-xorg-video-nouveau - distro free builtin 
```  Then I did this (it is most likely saying that "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded" becasue I've already installed them before):   ```
 $ sudo ubuntu-drivers autoinstall Reading package lists... Done Building dependency tree        Reading state information... Done The following packages were automatically installed and are no longer required:   linux-headers-4.15.0-29 linux-headers-4.15.0-29-generic   linux-image-4.15.0-29-generic linux-modules-4.15.0-29-generic   linux-modules-extra-4.15.0-29-generic Use 'sudo apt autoremove' to remove them. 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
```  And after restarting the resolution settings in settings>devices>displays still don't show a higher resolution than 1920x1080.   If I enter the nvidia setting like this in the menu X server Display Configuration it shows 2 displays: 1) Prime: eDP-1-1, 1920x1080 and 2) Prime: HDMI-1-2, 1920x1080  ```
 nvidia-settings 
```   However, in this menu I can't change any settings whatsoever. It just displays the resoluitons that I mentioned before.  After a bit of searching I found xrandr which returned this:  ```
 $ xrandr Screen 0: minimum 8 x 8, current 3840 x 1100, maximum 16384 x 16384 eDP-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm    1920x1080     60.01 +  60.01*   59.97    59.96    59.93      1680x1050     59.95    59.88      1600x1024     60.17      1400x1050     59.98      1600x900      59.99    59.94    59.95    59.82      1280x1024     60.02      1440x900      59.89      1400x900      59.96    59.88      1280x960      60.00      1440x810      60.00    59.97      1368x768      59.88    59.85      1360x768      59.80    59.96      1280x800      59.99    59.97    59.81    59.91      1152x864      60.00      1280x720      60.00    59.99    59.86    59.74      1024x768      60.04    60.00      960x720       60.00      928x696       60.05      896x672       60.01      1024x576      59.95    59.96    59.90    59.82      960x600       59.93    60.00      960x540       59.96    59.99    59.63    59.82      800x600       60.00    60.32    56.25      840x525       60.01    59.88      864x486       59.92    59.57      800x512       60.17      700x525       59.98      800x450       59.95    59.82      640x512       60.02      720x450       59.89      700x450       59.96    59.88      640x480       60.00    59.94      720x405       59.51    58.99      684x384       59.88    59.85      680x384       59.80    59.96      640x400       59.88    59.98      576x432       60.06      640x360       59.86    59.83    59.84    59.32      512x384       60.00      512x288       60.00    59.92      480x270       59.63    59.82      400x300       60.32    56.34      432x243       59.92    59.57      320x240       60.05      360x202       59.51    59.13      320x180       59.84    59.32   DP-1-1 disconnected (normal left inverted right x axis y axis) HDMI-1-1 disconnected (normal left inverted right x axis y axis) HDMI-1-2 connected 1920x1080+1920+20 (normal left inverted right x axis y axis) 600mm x 340mm    1920x1080     60.00*   60.00    59.94    30.00    24.00    29.97    23.98      1920x1080i    60.00    59.94      1600x900      60.00      1280x1024     60.02      1280x800      59.91      1152x864      59.97      1280x720      60.00    59.94      1024x768      60.00      800x600       60.32      720x480       60.00    59.94      640x480       60.00    59.94 
```  Then I tried to add a new resolution manually doing this: ```
  cvt 3840 2160 # 3840x2160 59.98 Hz (CVT 8.29M9) hsync: 134.18 kHz; pclk: 712.75 MHz Modeline "3840x2160_60.00"  712.75  3840 4160 4576 5312  2160 2163 2168 2237 -hsync +vsyn  xrandr --newmode "3840x2160_60.00"  712.75  3840 4160 4576 5312  2160 2163 2168 2237 -hsync +vsync  xrandr --addmode HDMI-1-2 3840x2160_60.00  xrandr --output HDMI-1-2 --mode 3840x2160_60.00 xrandr: Configure crtc 1 failed 
```  But I always get this error message at the end that xrandr failed.  I also tried arandr but there the same thing happens. After I ran this line:  ```
 xrandr --addmode HDMI-1-2 3840x2160_60.00 
```  The desired resolution shows up in settings>devices>displays and in arandr. But if I select it in arandr after a short black screen the same error message as in the terminal pops up. And if I try to set it in settings>devices>displays there is a black screen of 1 second or so and then it goes back to how it was before.  Is there anyone who already had a similiar problem and solved it or anyone that might know how to get the resolution set at 3840x2160?  I'd really appreciate some helpe here :)  Cheers, Lukas

---

### Post by limnoluke on 2019-03-06
Sorry, it seems like the way I inserted code chunks is not very nice. Is it not supposed to "square brackets open, code, square brackets closed" here the code that I want to share "square brackets open, slash, code, square brackets closed"  I guess I'll do it better next time if I find out what the right way is :)

---

### Post by QIII on 2019-03-06
That is how it is supposed to be done and that is how you appear to have done it.

Do you copy directly from the terminal or did you temporarily paste in a text editor?

---

### Post by limnoluke on 2019-03-07
I copied the code directly from the terminal. I mean, it's not like the world will end if I don't manage to get the monitor up and running with 3840x2160... But still, I bouth it for that reason :) And such a large monitor does look a bit pixely with 1920x1080...  So if anyone has any other suggestions I'd be really happy about it.  All the best and thanks

---

### Post by him610 on 2019-03-08
FWIW, I have a Nvidia GeForce GTX 760 (a generation older than yours) installed in a desktop computer. I usually download the Nvidia drivers from Additional Drivers. With those Nvidia drivers comes a package, nvidia-settings that is a Nvidia utility where one can set the resolution. It's the simplest way to set the resolution.
You can check if it is installed on your system by running from the command line,
```
apt list -a nvidia-settings
```
and you can run it by running it from the command line
```
nvidia-settings
```

---

### Post by limnoluke on 2019-03-27
Thanks a lot for this information :) However, I already tried that right after I figured out that the resoluiton is not working as planned... In my case the setting in NVIDIA don't allow any changes whatsoever. That's the reason why I started the in my opinion more complicated stuff :D   But still, thanks for helping.  Cheers

---

