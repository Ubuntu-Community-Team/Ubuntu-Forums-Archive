---
title: "NVidia 7200 Hardy Resolution issue"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by cschoeps on 2008-05-08
Hey everyone,

I just did a clean install of Hardy, but when I install the NVidia restricted drixver through the GUI that pops up, it limits my monitor resolution to 1080x1024. My monitor is capable of much higher resolutions, and they ran just fine when I had Gutsy installed. I tried to install EnvyNG to do the work for me, but I get this error:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root) and restart the X server. When I try to run that process, I get:

Using X configuration file: "/etc/X11/xorg.conf

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to determine CoreKeyboard; will rely on X server's built-in
         default configuration.

I've seen a few guides that tell me to stop the xserver and install a different driver from NVidia, but those always give me error messages when I try to install the driver.

---

### Post by cschoeps on 2008-05-08
Anybody know? I"m considering just going back to Gutsy, it's really aggravating. This is the 64-bit version, by the way.

---

### Post by tayhe on 2008-05-09
after installed the NVidia restricted driver,
use the fallowing code to enable it works;
```
sudo nvidia-glx-config enable
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```
and after all , you could install "nvidia-settings" which is nvidia's official configuration tool to config it in Gui.

---

### Post by cschoeps on 2008-05-09
Hmm..well when I try to run the nvidia-settings, I get the same error message as when trying to run nvidia-xconfig. Every time the computer starts, it boots int low-graphics mode. I hit 'configure' on the notification pop-up, and enter in my graphics card and monitor. After this, it starts up at 800x600 resolution max. Neither of the commands you give work, they just say the command is not found.

---

### Post by PmDematagoda on 2008-05-09
Let's just start from the beginning now:-

1) Remove the nvidia-glx-new package with:-
```
sudo apt-get remove --purge nvidia-glx-new
```

2) Install the Nvidia driver.

3) Open a modules file for editing with:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

4) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```
and save the file.

After all that is done, reboot the PC and see if the X-Server and the Nvidia driver now work properly.

---

### Post by cschoeps on 2008-05-09
I ended up just doing another clean install...I didn't trust my own tinkering :). 

Once I'd cleanly installed, I let the Restricted Drivers GUI install the driver and edited the restricted-modules file before rebooting. The system comes up in Low Graphics Mode again, and gives me the option to 'Configure', 'Shut Down', or 'Continue'.

If I continue, the only resolutions available to me are 800x600 and 640x480

Edit: I have not updated my system yet, so there are 61 updates available. In the past, installing these has not mattered, but let me know if I should do so.

---

### Post by brian3 on 2008-05-09
just reading your problem, if you ever get into the nvidia drivers,get the software ENVY this installs the correct drivers for you ,and restarts the xcerver for you

---

### Post by cschoeps on 2008-05-09
Hi, thanks for the reply!

I tried Envy before and got error messages, but this time it went through alright. It did it's thing and installed fine. When I restarted, It still comes up in Low-Graphics-Mode. The resolution options are still the same as before :(

Any other ideas?

---

### Post by cschoeps on 2008-05-09
I tried installing the updates, just for kicks. This had no effect. Still start up in Low Graphics Mode, still no other resolution options.

---

### Post by brigux on 2008-05-09
Method 2 always works for me. Needs to be completed each time your kernel is upgraded tho.. But worth the effort.. 
Oh and even if not specified, works for Hardy too.

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

---

### Post by cschoeps on 2008-05-09
Okay, I tried Method 2 with the latest AMD64 Nvidia driver from the page provided, 169.12.

The installation goes fine, but when I get to the step to run nvidia-xconfig, I get the same error I mentioned in the original post:


Using X configuration file: "/etc/X11/xorg.conf

WARNING: The CorePointer device was not specified explicitly in the layout;
using the first mouse device.


WARNING: Unable to determine CoreKeyboard; will rely on X server's built-in
default configuration.

I restart gdm, and my resolution is now capped at 1280x1024. This is much better than the Low-Graphics setting, but I was running Gutsy before at upwards of 1600x1200 (whatever the resolution is at 1700-some).

Edit: When installing the driver, I did get this warning message:

WARNING: Unable to perform the runtime configuration check for library 'libGL.so.1' ('/usr/lib32/libGL.so.169.12'); assuming successful installation.

---

### Post by cschoeps on 2008-05-09
In case anyone is wondering, I ended up completely reinstalling for a fourth time, installed the stock driver, and then installed and ran nvidia-settings. For some reason it decided to work this time, as it hasn't worked any other time. 

Either way, I'm not complaining. Thanks to everyone who helped.

---

### Post by tayhe on 2008-05-10
the ultimate method:
post your /etc/X11/xorg.conf ,
we could try to find is there some differents.

---

