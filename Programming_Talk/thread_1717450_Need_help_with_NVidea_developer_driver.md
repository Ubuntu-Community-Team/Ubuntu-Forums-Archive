---
title: "Need help with NVidea developer driver"
date: 2011-03-29
forum: Programming Talk
---

### Post by MR.UNOWEN on 2011-03-29
Hello,

I've been trying to install the developer driver on [this]("http://developer.nvidia.com/object/cuda_3_2_downloads.html#downloads") page. Unfortunately I found out it's not quite that easy as just running the installer. Turns out you need to uninstall a number of things first. I'm using Ubuntu 10.10 on an EEE PC 1015PN and yes it does have CUDA (with 8 cores). Also I'm using the suggested NVIDIA driver by Ubuntu.

Has anyone installed the NVIDIA developer driver and if so, what needs to be changed for a successful install?

One thing I noticed in the installation process, the pre-installer script fails. Do I need to install something for that to work?

---

### Post by GenBattle on 2011-03-29
I got the Aspire One 522 over the Asus 1015PN prettymuch for this reason; Optimus (therefore dual intel/nvidia graphics cards) are not supported under linux. By default the Intel card is used. I think there are some complex hacks around to turn the Nvidia card on, but then both are active, and the Intel one still does all the drawing (so it kills battery life).

While hunting around a bit i found this launchpad group maintained for hybrid graphics users:
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

Other than that, I don't think there's much I can offer as far as advice goes.

---

### Post by mtron on 2011-03-30
> **MR.UNOWEN said:**
> Has anyone installed the NVIDIA developer driver and if so, what needs to be changed for a successful install?

Yes, i'm running it right now on my Eee 1015pn. Install is very easy:
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get install nvidia-current
```

thats it. see the wiki for more info [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201015PN](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201015PN)


Just to clarify some stuff "GenBattle" told you:
> **GenBattle said:**
> By default the Intel card is used. 

No, the 1015pn uses the nvidia card per default. 

> **GenBattle said:**
> I think there are some complex hacks around to turn the Nvidia card on
See above. You just need to install 2 deb packages from [this thread]("http://ubuntuforums.org/showpost.php?p=10556760&postcount=61") and you will get a gui script to switch between nvidia only mode, intel only mode and the not-working optimus mode. 

> **GenBattle said:**
> but then both are active, and the Intel one still does all the drawing 

Also not true. In intel mode, the nvidia chip is turned off completly. it does not draw any power in this mode. In nvidia mode the intel chip does nothing. The nvidia chip has it's own hardware mux to the display.

---

### Post by MR.UNOWEN on 2011-04-01
> **mtron said:**
> Yes, i'm running it right now on my Eee 1015pn. Install is very easy:
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get install nvidia-current
```

thats it. see the wiki for more info [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201015PN](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201015PN)


Just to clarify some stuff "GenBattle" told you:


No, the 1015pn uses the nvidia card per default. 


See above. You just need to install 2 deb packages from [this thread]("http://ubuntuforums.org/showpost.php?p=10556760&postcount=61") and you will get a gui script to switch between nvidia only mode, intel only mode and the not-working optimus mode. 



Also not true. In intel mode, the nvidia chip is turned off completly. it does not draw any power in this mode. In nvidia mode the intel chip does nothing. The nvidia chip has it's own hardware mux to the display.

Ummmmm....   isn't nvidia-current the standard version and not the developer version? Don't I need the developer version to make use of CUDA when coding?

---

### Post by SevenMachines on 2011-04-01
No, if you've got a new enough distribution, certainly in natty, i'm pretty sure in maverick too, the nvidia driver comes with cuda headers.
```
$ dpkg -L nvidia-current-dev | grep cuda
/usr/include/nvidia-current/cuda
/usr/include/nvidia-current/cuda/cuda.h
/usr/include/nvidia-current/cuda/cudaGL.h
/usr/include/nvidia-current/cuda/cudaVDPAU.h
```

it also comes with opencl support and headers too, which is what i use,  the c++ wrapper header files from kronos also work fine too if you download them

---

