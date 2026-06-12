---
title: "HOW TO: Install NVIDIA Drivers on Hardy"
date: 2008-07-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Kileli on 2008-07-17
**Special thanks to :KS[B]_Unix_Slayer_**:KS for providing this tutorial. 

I have made small changes for the aplication on ubuntu 8.04 lts
[/B]
[B]Download the latest driver from NVidia:
[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
[/B]
**[COLOR="Red"]Step 1[/COLOR]**
        **in terminal window**

```
sudo apt-get install build-essential
```

           **Then :**

```
sudo apt-get remove nvidia*
```


**[this should get rid of all unwanted NVidia drivers. please check /lib/linux-restricted-modules/2.6.24.xx-generic/video and make sure there's no nvidia directory in there. There shouldn't be.] [xx = kernel version]**


[COLOR="DarkOrange"]Step 2[/COLOR]
         **on your keyboard**

```
sudo /etc/init.d/gdm stop
```

**Wait for the drop out of X11.**

[COLOR="Blue"]Step 3[/COLOR]

**Login into terminal as yourself. Go to the directory where you downloaded the newest NVidia driver. **

**type :**

```
sudo chmod +x (/driver location/)NVIDIA-Linux-x86-173.14.09-pkg1.run
``` 

**NVIDIA-Linux-x86-173.14.09-pkg1.run = name of the file you downloaded. If it's different, then make corrections.**


[COLOR="LightBlue"]Step 4[/COLOR]

**type in :**

```
sudo sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
```


**Follow directions on the screen.**

[COLOR="Lime"]Step 5
[/COLOR]
**Reboot**, 

**Install the settings manager for NVIDIA graphics cards**  
```
sudo apt-get install NVIDIA-settings
```


**Open settings manager with**
```
sudo nvidia-settings
```

**Adjust you settings, apply changes, save xorg.conf, and reboot if necessary**
Good Luck

---

### Post by d0b33 on 2008-08-18
Cool, I'm a n00b to setting up nvidia cards so this was helpful thanks.

---

### Post by Afkpuz on 2009-10-14
Thank you for this solution.  I'm rolling back to hardy for mythtv compatibility (long story) and hardy didn't seem to detect my video card.  This solution fixed it.

---

