---
title: "video drivers for HP Pavilion g6 2011 sq / Intel® HD Graphics 4000 + AMD Radeon HD 76"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by ltkleir on 2013-01-30
Hello,
I am a beginner in Ubuntu, so be please be patient with me. I even don&#8217;t know the Linux/Ubuntu terminology.
I installed Ubuntu 12.04 64 bit version, Unity interface. I&#8217;m not able to make Compiz Fusion to function, probably because I was unable to install the video drivers.
I have a HP Pavilion g6 2011 sq laptop, with graphical card Intel® HD Graphics 4000 + AMD Radeon HD 7670M.
I selected the proprietary drivers to install (there are 2, seems both from AMD), one is installing OK, but the other (the same but with **post-release updates**) cannot -> an error appears at installation, and is uninstalling the first driver. At the end, I finally installed the second driver, but only activated without being used by the system, and uninstalling the first driver automatically. Even if I am having a proprietary driver installed and used by the system, the effects are not working. Thinking it&#8217;s a problem of the Unity interface (I don&#8217;t know how to verify if it is Unity 2D or 3D), I installed the KDE interface, which announced me very clearly that the drivers are not installed for the video card, so there cannot be effects, even if one of the proprietary AMD drivers was installed and used by the system.
After that, I tried to take the drivers AMD Radeon HD 7670M from AMD site, so I installed AMD Catalyst (no other solution found) -> it was a disaster, but finally I managed to restart Ubuntu (seems the version without AMD Catalyst).
I searched for the Intel® HD Graphics 4000 drivers on Intel site, but found nothing for Linux. 
Also I downloaded a beta version for those proprietary drivers, but with no positive result.
I&#8217;m sure that a solution exists, has to exist, because I booted also with a live version of Knoppix, and Compiz Fusion functioned perfectly.
For information: at the installation of Win XP I had some similar problems, I found the drivers, but I was unable to run the AMD driver, even with AMD installed as well as Intel drivers. Switching feature between AMD and Intel is dependent on the Intel GPU, is not the function of Radeon. That seems because the used built in Intel software side of switching graphics on the Intel GPU needs Vista or higher. And even if Win XP has switchable graphics, those require a reboot and either had a physical switch (like a wireless switch that I don&#8217;t have) or an option to change in the BIOS (that I don&#8217;t have). What about Ubuntu ? Can it manage this problem, as Knoppix seems it can?
In conclusion, I have a good reliable laptop, and I cannot start Compiz on it, probably because I don&#8217;t have the Intel drivers, and AMD proprietary drivers offered by Ubuntu are useless because Ubuntu cannot switch from Intel to AMD. Or probably Ubuntu does not offer the Intel drivers, because it discovers only the AMD card. I don&#8217;t know. 
Can you help me please?
Thank you
[FONT=&quot]Gabriel[/FONT]

---

### Post by Mark Phelps on 2013-01-30
Switchable graphics, in general, do not work well in Linux because they require special drivers, which generally are not available. These drivers are provided by the OEMs that provide the laptops, but they don't provide Linux drivers, only MS Windows.

Laptops use special versions of the drivers, so forcing an install of a driver from the AMD site is most likely NOT going to work -- as I think you found out. In  some cases, you might be able to use a Mobile Radeon driver, but when you have switchable graphics, even that is likely NOT to work.

What I would suggest is that you do a search in the Video forum section on switchable graphics -- and see what results others have had in this.

---

### Post by gordintoronto on 2013-01-30
You might find this thread helpful:
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

Also see this page:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

and this one:
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

---

