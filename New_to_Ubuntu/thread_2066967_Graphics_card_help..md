---
title: "Graphics card help."
date: 2012-10-05
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-10-05
Okay I have Ubuntu installed but am having one hell of a time trying to get it to recognize my Nvidia GeForce GT 525M graphis card. But my laptop also has intel 3000 graphics.

I am re-installing ubuntu and want to start fresh. I just want to use the intel 3000 for graphics, How can I do this? Does this happen automatically even if there is a dedicated graphics card?

If it does happen automatically, could anybody explain why my computer reverts to Unity 2d? I have another laptop with intel 3000 for graphics and it can handle unity just fine. Please Help!

---

### Post by TheMTtakeover on 2012-10-06
Hate to bump, but I could really use some help. I tried Nvidia current, I tried iron-hide. At this point I'm not sure there is any solution for it?

---

### Post by necromonger on 2012-10-06
go to the nvidia site and down load the new driver it should fix your problem.i don't know about the intel side post full system specs and i know some one will be able to help.

---

### Post by TheMTtakeover on 2012-10-06
Okay. I tried installing the driver from their website but it comes up with this in the terminal

```
  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com.

```then this comes up

```
 ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at www.nvidia.com.

```and the results of that log file are

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Oct  6 20:59:24 2012
installer version: 304.51

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '1047' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at www.nvidia.com.
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.
```

---

### Post by Mark Phelps on 2012-10-07
You can't install the video driver while the desktop is running.  You have to boot into a command line interface and install it from there.  Then, restart, and the desktop will then reappear.

To do that, press Crtl-Alt-F1 (all three keys at the same time).  That will boot you into a command line.

When done entering the commands, press Ctrl-Alt-F7 -- that will restart the graphics mode.

---

### Post by DuckHook on 2012-10-07
Don't quite understand your post. Do you want to use the Intel 3000 for your graphics or the NVidia?

> I just want to use the intel 3000 for graphics, How can I do this? Does  this happen automatically even if there is a dedicated graphics card?If you want to use the 3000, then pull out the NVidia card altogether, make sure the 3000 is enabled in BIOS and you are set. If you wish to use the NVidia, then its presence should either disable the Intel, or there should again be a BIOS switch that allows dual use or choice of video subsystem.

> could anybody explain why my computer reverts to Unity 2d? I have  another laptop with intel 3000 for graphics and it can handle unity just  fine.The Intel 3000 is a video system integrated into your CPU chip. Frankly, it isn't very powerful and it uses system memory as video memory. It is up to the motherboard manufacturer to decide how much system memory is dedicated to video. If the resources are insufficient, Unity 3D will not run. In some BIOSes, the amount of video memory can be increased. This memory will then not be available for main memory use.

In my opinion, you are better off not using the Intel 3000 video chip at all and just sticking with the NVidia. Don't know anything about your motherboard or your BIOS, but if you can turn it off, Ubuntu should install recognizing only the NVidia. Ubuntu installs with generic drivers, so initial video should be okay. You can then turn on restricted drivers if you wish, to get the proprietary binaries that will run the higher 3D functions of the NVidia card.

---

### Post by xiuix on 2013-02-13
> **DuckHook said:**
> Don't quite understand your post. Do you want to use the Intel 3000 for your graphics or the NVidia?

If you want to use the 3000, then pull out the NVidia card altogether, make sure the 3000 is enabled in BIOS and you are set. If you wish to use the NVidia, then its presence should either disable the Intel, or there should again be a BIOS switch that allows dual use or choice of video subsystem.

The Intel 3000 is a video system integrated into your CPU chip. Frankly, it isn't very powerful and it uses system memory as video memory. It is up to the motherboard manufacturer to decide how much system memory is dedicated to video. If the resources are insufficient, Unity 3D will not run. In some BIOSes, the amount of video memory can be increased. This memory will then not be available for main memory use.

In my opinion, you are better off not using the Intel 3000 video chip at all and just sticking with the NVidia. Don't know anything about your motherboard or your BIOS, but if you can turn it off, Ubuntu should install recognizing only the NVidia. Ubuntu installs with generic drivers, so initial video should be okay. You can then turn on restricted drivers if you wish, to get the proprietary binaries that will run the higher 3D functions of the NVidia card.

I am pretty sure he is asking about a laptop that has an intragraged Nvidia525m and a intel 3000 both on one chip.  You cannot "pull out" this chip.  I am having the same problem.

---

### Post by kurok on 2013-02-14
i think what you have is the nvidia optimus set up for laptops . I can't be positive since i don' have this set up, this might help tho [https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")

---

### Post by charlesDean on 2013-02-14
Ofcourse, it will use intel 3000 for graphic as default.As i am uderstanding, you want to use  the intel 3000 for graphics, so take off Nvidia GeForce GT 525M graphis card.
If You wan to use Nvidia GeForce GT 525M graphis card add it at place of old.

---

