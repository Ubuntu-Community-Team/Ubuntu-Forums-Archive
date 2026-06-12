---
title: "Screen brightness control on Gateway NV57H13h"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by Kegeg on 2011-11-17
I just bought a new laptop (Gateway NV57H13h) and completely formated it to reinstall Ubuntu 11.10 on, but I can not dim the light on the screen causing my battery to die very fast... Can someone help me with this? Tell me the command output that you would need

Thank you

---

### Post by prookie on 2011-11-17
> **Kegeg said:**
> I just bought a new laptop (Gateway NV57H13h) and completely formated it to reinstall Ubuntu 11.10 on, but I can not dim the light on the screen causing my battery to die very fast... Can someone help me with this?u

Hi Kegeg,

Great computer you've got there.

What do you mean by dim the light?

Ubuntu 11.10 (with Unity) is using a lot of resources, but this can not be the cause in your case. :)
Another problem can be that you have a brand new HW, and Ubuntu kernel does not have support for it.

If you want to try Ubuntu, my suggestion is that you try it from USB drive. Check ...
[www.pendrivelinux.com](www.pendrivelinux.com)

Best regards,
pRookie

---

### Post by Kegeg on 2011-11-19
The problem is that I can't adjust the brightness of my screen using the keyboard shortcut and even from the terminal. I've been using Ubuntu for 4 years now and I can't just go back to windows because of that! The hardware is new so the kernel not supporting it fully might be an option, any ideas on how long could it take to be supported or how to temporarily fix this?  

Thanks

---

### Post by Toz on 2011-11-19
I believe this notebook has an nvidia video card. Are you using the proprietary drivers? If so, try adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the DEVICE section of /etc/X11/xorg.conf.

You might also want to try the **acpi_backlight=vendor** kernel parameter. You can test it via this procedure: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot").

---

### Post by prookie on 2011-11-20
> **Kegeg said:**
> The hardware is new so the kernel not supporting it fully might be an option, any ideas on how long could it take to be supported or how to temporarily fix this?

It's hard to tell that for me. Maybe it's not a kernel problem in you case.

Now, I'm investigating how to report my problem as a bug to development  team. I experience crashes in 11.10 which are related with my mobile  broadband USB modem. I guess that the problem is with new kernel 3.x.x.  My modem is not supported in a rigth way in kernel and that is causing  instability of the whole system.

This is a bad side of Linux. Manufacturers of the hardware are not  giving support and drivers for Linux users so everything is on the Linux  community themselves. And that is  a great problem if you want to use your brand new hardware with all features.

In your case, you can wait a long time that your specific piece of  hardware could be covered in Linux (that even means indefinetly like in the case of old modem I have). Or you can try to speed up things by  contacting development team somehow. If I succeed in my case, I'll let  you know. :)

---

### Post by Kegeg on 2011-11-20
> **Toz said:**
> I believe this notebook has an nvidia video card. Are you using the proprietary drivers? If so, try adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the DEVICE section of /etc/X11/xorg.conf.

You might also want to try the **acpi_backlight=vendor** kernel parameter. You can test it via this procedure: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot").

I tried both your solution but it didn't seem to work... I also had trouble installing the NVIDIA driver and never got it to work, I'm only using the Intel card for now but it still do the job. I also tried to dim it with xbacklight -set 0, but it didn't work either

---

### Post by Toz on 2011-11-20
What is the result of the following command:
```
lspci | grep VGA
```

You should get 2 lines returned, one for the nvidia card and one for the Intel card. The first field is the device id. Then try this:
```
sudo setpci -s <device_id> F4.B=<value>
```
...where device_id is the results from the previous command and value is a hexidecimal value between 0 and 255. Try the following values to test: 0, 7F, FF.

Examples:
> sudo setpci -s 01:00.0 F4.B=0
sudo setpci -s 01:00.0 F4.B=7F
sudo setpci -s 01:00.0 F4.B=FF

Does this command change the brightness?

If not, what is the contents of your /sys/class/backlight directory:
```
ls /sys/class/backlight
```

---

### Post by Kegeg on 2011-11-21
> **Toz said:**
> What is the result of the following command:
```
lspci | grep VGA
```

You should get 2 lines returned, one for the nvidia card and one for the Intel card. The first field is the device id. Then try this:
```
sudo setpci -s <device_id> F4.B=<value>
```
...where device_id is the results from the previous command and value is a hexidecimal value between 0 and 255. Try the following values to test: 0, 7F, FF.

Examples:


Does this command change the brightness?

If not, what is the contents of your /sys/class/backlight directory:
```
ls /sys/class/backlight
```


The output of the first command is:
> :~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev a1)

As for the command **sudo setpci -s 00:02.0 F4.B=0 , 7F or FF** it didn't change anything

The output for >  :~$ ls /sys/class/backlight
acpi_video0  intel_backlight

---

### Post by Toz on 2011-11-21
You have 2 backlight interfaces. Lets try to find out which one is the valid one then remove the other one.

Look inside **/sys/class/backlight/intel_backlight** and you should see a number of files including **brightness**, **actual_brightness** and **max_brightness**. 

max_brightness contains the maximum brightness value that can be processed by the interface.

actual_brightness is the current brightness level

Try:
```
echo <value> | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...where <value> is a valid value between 0 and max_brightness. Does this change the screen brightness?

If not, try the same with the acpi_video0 interface.

If still nothing, boot with the **acpi_backlight=vendor** kernel parameter and try both again.

---

### Post by Kegeg on 2011-11-21
> **Toz said:**
> You have 2 backlight interfaces. Lets try to find out which one is the valid one then remove the other one.

Look inside **/sys/class/backlight/intel_backlight** and you should see a number of files including **brightness**, **actual_brightness** and **max_brightness**. 

max_brightness contains the maximum brightness value that can be processed by the interface.

actual_brightness is the current brightness level

Try:
```
echo <value> | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...where <value> is a valid value between 0 and max_brightness. Does this change the screen brightness?

If not, try the same with the acpi_video0 interface.

If still nothing, boot with the **acpi_backlight=vendor** kernel parameter and try both again.

Good, adjusting the brightness through **echo <value> | sudo tee /sys/class/backlight/intel_backlight/brightness** works, but I still can't use the keyboard's brightness key... This is a good temporary solution until the semester is over and I have more time to play with it! I've wrote the result of the brightness file here if that can give you more hint.  

> :~$ ls sys/class/backlight/intel_backlight
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type


Thank you

---

### Post by Toz on 2011-11-22
Good. Then try disabling the acpi_video0 interface to see if it will allow the hotkeys to work:
```
sudo modprobe -r video
```
If you get an error that doesn't allow it to happen (and/or to make it permanent), blacklist it and reboot:
```
sudo bash -c "echo 'blacklist video' >> /etc/modprobe.d/blacklist.conf"
```
...and reboot.

See if the hotkeys work then.

---

### Post by Kegeg on 2011-11-22
The first gave me this error message > :~$ sudo modprobe -r video
FATAL: Module video is in use.

And I'm not sure how to shut it down, I tried the second code but it still didn't work...

---

### Post by Toz on 2011-11-22
If you've run the second command, then just restart your computer for it to take effect.

---

### Post by Kegeg on 2011-11-22
> **Toz said:**
> If you've run the second command, then just restart your computer for it to take effect.

That's what I did, but it didn't work... Right now I can play with the brightness using 
```
echo 50 | sudo tee /sys/class/backlight/intel_backlight/brightness
``` But it doesn't give me longer battery life.

---

### Post by Toz on 2011-11-23
> **Kegeg said:**
> That's what I did, but it didn't work...
What is the result now of:
```
lsmod
```
...and
```
ls /sys/class/backlight
```
...and
```
cat /proc/cmdline
```

---

### Post by Kegeg on 2011-11-23
Here's the results:
```
:~$ lsmod
Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
nvidia              11713772  0 
arc4                   12529  2 
snd_hda_intel          33390  2 
i915                  566711  3 
iwlagn                314213  0 
uvcvideo               72711  0 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
videodev               93004  1 uvcvideo
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
v4l2_compat_ioctl32    17083  1 videodev
psmouse                73882  0 
mac80211              462092  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13423  1 i915
serio_raw              13166  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
mei                    41480  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mxm_wmi                12979  0 
sparse_keymap          13890  0 
video                  19412  1 i915
wmi                    19256  1 mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
xhci_hcd               82772  0 
tg3                   147729  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci

```
```
:~$ ls /sys/class/backlight
acpi_video0  intel_backlight

```
```
:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=66f233b0-29a1-46ed-b1af-392d1e7cb117 ro quiet splash vt.handoff=7

```

---

### Post by Toz on 2011-11-23
Hmmmm. The video module is still loaded. What does the following command return?
```
cat /etc/modprobe.d/blacklist.conf
```

You might also want to try booting with the **acpi_backlight=vendor** kernel parameter to see if that helps.

---

### Post by Kegeg on 2011-11-23
Booting with the **acpi_backlight=vendor** command didn't change anything and here's the result of the other one:
```
:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist video

```

---

### Post by s1baker on 2011-11-24
You might check out this thread, specifically post #9:

[http://ubuntuforums.org/showthread.php?t=1283622]("http://ubuntuforums.org/showthread.php?t=1283622")

---

### Post by Kegeg on 2011-11-24
> **s1baker said:**
> You might check out this thread, specifically post #9:

[http://ubuntuforums.org/showthread.php?t=1283622]("http://ubuntuforums.org/showthread.php?t=1283622")

I already saw that post and tried it, but it doesn't increase my battery life which is the main reason why I want to reduce the brightness... But thank you for the proposition anyway

---

### Post by Gato303co on 2011-11-27
> **Toz said:**
> You have 2 backlight interfaces. Lets try to find out which one is the valid one then remove the other one.

Look inside **/sys/class/backlight/intel_backlight** and you should see a number of files including **brightness**, **actual_brightness** and **max_brightness**. 

max_brightness contains the maximum brightness value that can be processed by the interface.

actual_brightness is the current brightness level

Try:
```
echo <value> | sudo tee /sys/class/backlight/intel_backlight/brightness
```...where <value> is a valid value between 0 and max_brightness. Does this change the screen brightness?


Thanks a lot Toz, it did work for my Dell Inspiron N5110 :D :D

---

### Post by Gato303co on 2011-11-27
Sorry, It's me again.

How can add the line you told

Option "RegistryDwords" "EnableBrightnessControl=1"
To the xorg.conf file?

I don't have actually a xorg.conf, I haven't created it and I also haven't install the propietary drivers of Nvidia, cause everytime I do that my linux literally "dies" (I already tried Ubuntu11.04, Xubuntu11.10, Fedora 16, with the same result to all of them) , I am using the default video driver, I guess it's named "Nouveau".

In the Nvidia drivers download page I found this [http://www.nvidia.com/object/linux-display-amd64-290.10-driver.html](http://www.nvidia.com/object/linux-display-amd64-290.10-driver.html)

Check the "Additional information" tab, they say the Nvidia Linux driver may not be compatible with "hybrid" systems or Optimus graphics.

Ehm... another point... the "echo <value> | sudo tee ...." worked on my laptop (i put brightness in 2000, with valid values from 0 till 4882), but when I hit the "Fn+F4 or F5" for adjusting brightness, the brightness level goes back to maximum.
-------------
By the way my system configuration is this:
Dell Inspiron 15R N5110
Processor intel core i7 2630QM 4 cores/8 threads
RAM 8GB DDR3
Video Intel Graphics HD 3000 64MB/ Nvidia Gforce gt525m 1GB
Hard Drive 640GB
Xubuntu Linux 11.10 64 bits
-------------
Thanks a lot for providing information about this subject

---

### Post by Kegeg on 2011-11-28
> **Gato303co said:**
> Thanks a lot Toz, it did work for my Dell Inspiron N5110 :D :D

Hey Gato303co, is it giving you more battery time? Because it also change my brightness, but my computer still have a very short battery life...

---

### Post by Toz on 2011-11-28
> **Gato303co said:**
> Sorry, It's me again.

How can add the line you told

Option "RegistryDwords" "EnableBrightnessControl=1"
To the xorg.conf file?

I don't have actually a xorg.conf, I haven't created it and I also haven't install the propietary drivers of Nvidia, cause everytime I do that my linux literally "dies" (I already tried Ubuntu11.04, Xubuntu11.10, Fedora 16, with the same result to all of them) , I am using the default video driver, I guess it's named "Nouveau".
I believe this option only works if you are using the proprietary drivers.

> Ehm... another point... the "echo <value> | sudo tee ...." worked on my laptop (i put brightness in 2000, with valid values from 0 till 4882), but when I hit the "Fn+F4 or F5" for adjusting brightness, the brightness level goes back to maximum.
Try creating this script:
```
gksudo gedit /usr/local/bin/brightness
```
...and copy and paste this information into the window that opens:
```

#!/bin/bash
# /usr/local/bin/br
# wrapper script to change brightness values
# make script executable

# constants - edit as required
[COLOR="Red"]INTERFACE="/sys/class/backlight/toshiba/brightness"[/COLOR]
UPPER=4882
LOWER=0
INCREMENT=488
DECREMENT=488
doit=false

# current value
CURRENT=`cat $INTERFACE`
NEW=$CURRENT

case $1 in
	up)
		if [ $(($CURRENT+$INCREMENT)) -le $UPPER ]; then
			NEW=$(($CURRENT+$INCREMENT))
			doit=true
		fi
	;;
	down)
		if [ $(($CURRENT-$DECREMENT)) -ge $LOWER ]; then
			NEW=$(($CURRENT-$DECREMENT))
			doit=true
		fi
	;;
	*)
	;;
esac

if [ $doit == true ]; then
	# set the new brightness value 
	echo $NEW > $INTERFACE

	# fix for my old crappy toshiba
	#chvt 1 && chvt 7
fi

#echo "$doit - $NEW"
exit 0

```
...make sure you set the value of $INTERFACE (in red above) to your actual interface file and make the file executable:
```
sudo chmod +x /usr/local/bin/brightness
```

To test it, first:
```
sudo chmod 666 $INTERFACE
```
...(to grant your regular user account access to the interface file - [COLOR="Red"]make sure you replace $INTERFACE with the full path to your interface file[/COLOR])

..then...

```
brightness up
```to increase the brightness and
```
brightness down
```to decrease the brightness

If it works, try assigning the hotkeys to run his script.

---

### Post by cmcanulty on 2011-12-03
got it see this post
[http://ubuntuforums.org/showthread.php?p=11510086#post11510086]("http://ubuntuforums.org/showthread.php?p=11510086#post11510086")

---

### Post by Gato303co on 2011-12-03
> **Kegeg said:**
> Hey Gato303co, is it giving you more battery time? Because it also change my brightness, but my computer still have a very short battery life...

Ah yeah... about that... I guess it only controls the brightness, but not the laptop performance, so no, I haven't gotten my battery last longer by using that code.

I guess it doesn't have to do with the brightness, may it be an issue of the "hybrid system" graphics?  I have the impression is better handled by Window$ and Linux doesn't have good support for that.

I am using Xubuntu, I don't know if the menu will be the same for you, but have you checked the option in Menu>Configuration>Configuration Manager>Power manager> check the field "With battery" if the option "I prefer to save energy over performance" I have it enabled but it seems not to make a difference... maybe you could try it to see if your system supporst that funcion.

---

### Post by Gato303co on 2011-12-03
> **Toz said:**
> 

```
brightness up
```to increase the brightness and
```
brightness down
```to decrease the brightness

If it works, try assigning the hotkeys to run his script.
 

Wow! it works, thanks a lot :D:D!

Though it solve the brightness adjusting level, still have the same problem of Kegeg, the power comsuption seems to be the same even decreasing brightness.

Thanks again man

---

### Post by Gato303co on 2011-12-05
> **Toz said:**
> 
```
sudo chmod 666 $INTERFACE
```...(to grant your regular user account access to the interface file - [COLOR=Red]make sure you replace $INTERFACE with the full path to your interface file[/COLOR])


Uhm... it works for one session only, when I reboot, i don't know why, the permissions are lost and I have to execute this command everytime I boot into Xubuntu.  How may I do to make that permissions permanent?  Thank you

---

### Post by Toz on 2011-12-05
Add to **/etc/rc.local** above the *exit 0* command, the following:
```
chmod 666 $INTERFACE
```

(no need for sudo here because the file is executed with root privileges). It will be executed every time at boot.

---

### Post by Gato303co on 2011-12-23
> **Kegeg said:**
> Hey Gato303co, is it giving you more battery time? Because it also change my brightness, but my computer still have a very short battery life...

I think it doesn't have to do with screen brightness, my Inspiron has most of the time the fan on, maybe meaning an overuse of the system?

And without the NVIDIA linux driver, looks that only uses the Intel integrated graphics from the processor.

---

### Post by cmcanulty on 2011-12-23
**** no matter how much I tweak 11.10 problems come back. Now at the library they go black and we have to open and close lid to get it back.

---

### Post by Gato303co on 2011-12-26
> **Kegeg said:**
> Hey Gato303co, is it giving you more battery time? Because it also change my brightness, but my computer still have a very short battery life...

I found this at Ubuntu Help.  I tried, but it didn't work for me, for some reason the nvidia drivers installed via Jockey-gtk delete the switcheroo, used for changing between the integrated graphics on the processor and the discrete nvidia graphics chip.

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Give it a try, and let me know it if works for you

---

### Post by jdurand on 2011-12-29
I just wanted to add a data point that the kernel parameter of
**[CENTER]acpi_backlight=vendor[/CENTER]**
fixed my Acer 5733Z which also uses the Intel embedded video hardware.

---

### Post by Gato303co on 2012-01-04
> **Toz said:**
> Add to **/etc/rc.local** above the *exit 0* command, the following:
```
chmod 666 $INTERFACE
```(no need for sudo here because the file is executed with root privileges). It will be executed every time at boot.

Hello again Toz, there is one thing I really wonder about the OS...

Why, when I execute the Xubuntu Live CD, it gives me support for the "Fn + F4 or F5" to increase or reduce brightness, but after installation, that support no longer works?

Same happen with other "Fn+ F#" shortcuts on my Dell 15R Inspiron N5110, even the webcam has support on the Live CD session, but once I boot into the installated OS in my PC, many of those supports become useles.

Thank you

---

### Post by jdurand on 2012-01-04
> **jdurand said:**
> I just wanted to add a data point that the kernel parameter of
**[CENTER]acpi_backlight=vendor[/CENTER]**
fixed my Acer 5733Z which also uses the Intel embedded video hardware.

Well, nothing is perfect.  Now when the screen auto dims it doesn't come back unless I use the function key to increase brightness.  Not a disaster, but it would be nice if it worked like 10.04 did.

---

### Post by Toz on 2012-01-04
> **Gato303co said:**
> Hello again Toz, there is one thing I really wonder about the OS...

Why, when I execute the Xubuntu Live CD, it gives me support for the "Fn + F4 or F5" to increase or reduce brightness, but after installation, that support no longer works?

Same happen with other "Fn+ F#" shortcuts on my Dell 15R Inspiron N5110, even the webcam has support on the Live CD session, but once I boot into the installated OS in my PC, many of those supports become useles.

Thank you

Interesting. It might be worth comparing the two boots to see what differences there are. Look at things like:
- kernel version (uname -a)
- command line parameters (cat /proc/cmdline)
- loaded modules (lsmod)
- video card driver (sudo lspci -k | grep -A3 VGA)
- boot messages (dmesg)
See if you can identify the differences.

---

### Post by Kegeg on 2012-03-25
> **Gato303co said:**
> Wow! it works, thanks a lot :D:D!

Though it solve the brightness adjusting level, still have the same problem of Kegeg, the power comsuption seems to be the same even decreasing brightness.

Thanks again man

I finally got the power issue (the brightness still is always at its max...) with bumblebee see this link: [http://geek.co.il/wp/2012/02/19/nvidia-optimus-on-ubuntu-12-04]("http://geek.co.il/wp/2012/02/19/nvidia-optimus-on-ubuntu-12-04")

Thanks for the help

---

