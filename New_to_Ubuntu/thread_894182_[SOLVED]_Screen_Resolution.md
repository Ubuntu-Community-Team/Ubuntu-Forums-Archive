---
title: "[SOLVED] Screen Resolution"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by LeetSpeak on 2008-08-19
This is not for me, it's for my friend, he recently got a graphic card ( GeForce 8800GTS Nvidia ) And his screen resolution won't go any higher then 640 x 480. His hardware drivers are in use and enabled but I don't know what else I can do to help him, any advice? Thanks in advance!

---

### Post by AjBaz100 on 2008-08-19
Have you tried changing the settings in /etc/X11/xorg.conf.

Look for something like this and modify:
Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon X800 (R430 UO)"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

---

### Post by aman.agx on 2008-08-19
Hi, 
You can download the drivers for linux from the NVIDIA site. 
for more details you can see the below post.

[http://ubuntuforums.org/showthread.php?t=893329](http://ubuntuforums.org/showthread.php?t=893329)

hope it helps

---

### Post by LeetSpeak on 2008-08-19
and that is were?

---

### Post by aman.agx on 2008-08-19
I had the same problem with my NVIDIA drivers. The restricted drivers from NVIDIA site installed fine the system also ran fine. But when I rebooted it it didnt work. but a small change solved the problem.

What I would suggest is install the restricted drivers. for this follow below steps.
1. Go to NVIDIA website. 
2. download latest linux drivers for your graphics card and configuration. (64 bit or 386 architecture). The instuction to run these are there on the site.
3. you might need to install some development libraries when you run the driver file. I think it is libc development package. This can be easily installed from Synaptic.
To install drivers : 
    i) save the .run file from NVIDIA site on your desktop.
   ii) log off and press ctrl+alt+F1
  iii) run the following commands
       sudo killall gdm
       cd /home/<user>/Desktop
       <NVIDIA Driver Filename>
If any of these commands dont work you can try using sudo.
   iv) If the drivers are installed successfully, run gdm on console. Log in as your user and follow the below mentioned steps.

4. After you have installed drivers open /etc/default/linux-restricted-modules-common

it should look like this 

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""
```


make it DISABLED_MODULES="nv"

And reboot.


This should work. Hope it helps. 

Regards
Aman

---

### Post by LeetSpeak on 2008-08-19
> **aman.agx said:**
> I had the same problem with my NVIDIA drivers. The restricted drivers from NVIDIA site installed fine the system also ran fine. But when I rebooted it it didnt work. but a small change solved the problem.

What I would suggest is install the restricted drivers. for this follow below steps.
1. Go to NVIDIA website. 
2. download latest linux drivers for your graphics card and configuration. (64 bit or 386 architecture). The instuction to run these are there on the site.
3. you might need to install some development libraries when you run the driver file. I think it is libc development package. This can be easily installed from Synaptic.
To install drivers : 
    i) save the .run file from NVIDIA site on your desktop.
   ii) log off and press ctrl+alt+F1
  iii) run the following commands
       sudo killall gdm
       cd /home/<user>/Desktop
       <NVIDIA Driver Filename>
If any of these commands dont work you can try using sudo.
   iv) If the drivers are installed successfully, run gdm on console. Log in as your user and follow the below mentioned steps.

4. After you have installed drivers open /etc/default/linux-restricted-modules-common

it should look like this 

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""
```


make it DISABLED_MODULES="nv"

And reboot.


This should work. Hope it helps. 

Regards
Aman

It says Login incorrect when I type that sudo killall thing, can u tell me what the code is that I have to type in the black screen?

---

### Post by aman.agx on 2008-08-19
Ok, after pressing ctrl+alt+F1 you have to login again using your username password.
after that you can run the follwing commands.
i)  sudo killall gdm
ii) cd /home/<user>/Desktop
iii)  <NVIDIA Driver Filename>

Could you download the drivers from NVIDIA website?

---

### Post by LeetSpeak on 2008-08-19
yea, i downloaded it, and its on my desktop, and when i get to the black screen, I do that killall thing, and it does something and after that it just shows me the username@desktop thing, do i have to come back to the desktop after that or what?

---

### Post by LeetSpeak on 2008-08-19
^^^

Just to make it clear, when i type that thing in the black screen, a bunch of words come up but nothing happens after it.

---

### Post by HittingSmoke on 2008-08-19
Same thing happened to me when I tried to install the drivers for my 7600 GT using the Hardware Drivers Manager. I had to "sudo apt-get remove nvidia-glx-new" and use Envy to reinstall them. After that everything is working great.

---

### Post by LeetSpeak on 2008-08-19
Wow thanks to all of you, finally worked. That's Why I Love these forums, thanks guys!

---

### Post by aman.agx on 2008-08-19
Post the output.
Oh!!! Didnt see  the last post... How did it work. It would be nice if you could post the solution :)

---

