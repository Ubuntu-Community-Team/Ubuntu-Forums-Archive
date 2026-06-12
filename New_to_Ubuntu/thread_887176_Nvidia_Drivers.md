---
title: "Nvidia Drivers"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by pepaman on 2008-08-11
Hi 
iv just installed ubuntu with wudi.I want to know how to install nVidia 9500m gs drivers. I went to the nvidia home page downloaded the lynux drivers. went to install but. no go.

---

### Post by tuxxy on 2008-08-11
system > admin > hardware drivers,  enable it here

---

### Post by alienexplorers on 2008-08-11
You could also load Envy-ng from the repositories and load your driver using that program.

---

### Post by pepaman on 2008-08-11
iv done that. there is a red light and it says (not in use). how do i get into the nvidia control panel?

---

### Post by Crafty Kisses on 2008-08-11
> **pepaman said:**
> iv done that. there is a red light and it says (not in use). how do i get into the nvidia control panel?

You can also install that through Synaptic.

---

### Post by Sinkingships7 on 2008-08-11
> **pepaman said:**
> iv done that. there is a red light and it says (not in use). how do i get into the nvidia control panel?

Check the square box next to the red light, under the column that says "Enabled".

---

### Post by pepaman on 2008-08-11
Ya i was after where you change the resolution in the nvidia control panel. (where can i find the nvidia control panel) its on like 800x600 and that's the highest setting.

---

### Post by tech0007 on 2008-08-11
> **pepaman said:**
> Ya i was after where you change the resolution in the nvidia control panel. (where can i find the nvidia control panel) its on like 800x600 and that's the highest setting.

Run 'nvidia-settings'. If it didn't find the command, run 'sudo apt-get install nvidia-settings'

---

### Post by pepaman on 2008-08-11
> **tech0007 said:**
> Run 'nvidia-settings'. If it didn't find the command, run 'sudo apt-get install nvidia-settings'

sorry dont understand what you mean. In laymens terms please

---

### Post by erickghint on 2008-08-11
I may be wrong here, but I think that the 9 series isn't yet supported by the open source drivers... You may have to DL the drivers from nvidia's web site.

---

### Post by tuxxy on 2008-08-11
If compiz effects work at **system > prefs > appearance > desktop effects** then it is likely to be working.

**nvidia-settings** is the control panel open **system > admin > synaptic **and search for it to install.

---

### Post by johnlvs2run on 2008-08-11
This got my nvidia driver and resolution adjusted.
[http://ubuntuforums.org/showthread.php?t=826152&page=5](http://ubuntuforums.org/showthread.php?t=826152&page=5)

---

### Post by tinker312 on 2008-08-11
Hey Pepaman, 

If you want to install the nvidia drivers for you gfx card open a terminal and switch to the directory they are downloaded.  Issue: 

sudo -s 
apt-get install build-essential
sh NVIDIA-Linux-x86-173.14.12.pkg1.run

The nvidia installer will come up.  It will ask if you want to download a precompiled kernel. Say no.  

Then it will try to compile a custom kernel to run the driver. After it's done you'll be ask if you want nvidia-settings to configure you xorg.conf , say yes, then your done.  

When you reboot you should see an nvidia splash screen on bootup.  To test your 3d acceleration open up a terminal again and type glxgears if everything is working right you should have framerates in the 3000-5000 range and 200-400 range with the window maximized.  

Good Luck and I hope this touches upon what you were looking for, 
Tinker

---

### Post by tuxxy on 2008-08-12
You could also check the help documentation 

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by erickghint on 2008-08-12
> **tinker312 said:**
> 

When you reboot you should see an nvidia splash screen on bootup.  To test your 3d acceleration open up a terminal again and type glxgears if everything is working right you should have framerates in the 3000-5000 range and 200-400 range with the window maximized.  



Don't forget to edit the restricted modules. 

sudo nano /etc/default/linux-restricted-modules-common

just put nv in the quotes.... should look like this :
DISABLED MODULES - "nv"

---

