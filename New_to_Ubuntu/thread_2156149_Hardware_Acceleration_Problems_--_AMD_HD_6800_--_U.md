---
title: "Hardware Acceleration Problems -- AMD HD 6800 -- Ubuntu 12.04"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by Gnawnsense on 2013-06-20
Greetings!

A few days ago I had issues with my Radeon HD 6800 and the proprietary drivers taking into effect. The thread for this issue can be found at [http://ubuntuforums.org/showthread.php?t=2155258](http://ubuntuforums.org/showthread.php?t=2155258) with all of the relevant information. For the sake of saving everyone the time of being required to completely review it, tho, basically what was happening is I was setting the driver, but it was saying "Driver is active, but not in use" on the additional drivers tool.

So after some review it was established that the*sudo lspci -v* command was turning up that the selected drivers were actually in use, and that the additional drivers tool was having a conflict, which wasn't a big deal. However, naturally, my next question was why my performance in some Steam titles was absolutely horrible. I've been aware of AMD difficulties on Linux systems for a while, but with my card, performance should of been better.

This is when I was informed that hardware acceleration had to be enabled after driver installation, separately. I was referred to [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Enabling_Video_Hardware_Acceleration](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Enabling_Video_Hardware_Acceleration) for instructions on how to properly install the required packages, which worked with no problems at all. I launched into Steam and Team Fortress 2, as well as a few other titles, and my performance was excellent.

After all of this, I tried upgrading to Ubuntu 13.04 and it didn't work out. So I reformatted and put Ubuntu 12.04 back on my machine. I figured I'd just run through the same steps as I did last time, and I'd have my drivers going in no time. However, it's turning out that isn't the case here.

After installing the proper drivers I went to enable the hardware acceleration. This is where the problems are starting. The hardware acceleration is removing my drivers packages this time around, when previously they weren't. So after I enable the hardware acceleration, if I go into additional drivers, nothing is set to in use. Running *sudo va info* after enabling confirms that the packages weren't installed properly. Below is what my *sudo va info* command displays directly after enable.

[IMG]http://screencloud.net//img/screenshots/75d25ffd2201ecfd8a400de37839b350.png[/IMG]

After reviewing the Wiki page further, I tried running the *sudo ln -s /usr/lib/va/drivers/fglrx_drv_video.so /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so* command afterwards, but received the message below:

[IMG]http://screencloud.net//img/screenshots/1b0454141c7e4ef00725573f424feafc.png[/IMG]

So my next step was going back to the additional drivers tool and seeing what it said was currently active and in use. To my surprise, nothing was set to active and in use, but 5 minutes ago prior to installing the hardware acceleration, the experimental driver was active. Below is a shot of the additional drivers tool afterwards.

[IMG]http://screencloud.net//img/screenshots/b20d9ccfe1b79bd19281392c60e4c379.png[/IMG]

I know the key to this whole thing is the fact that when I follow the instructions on the Wiki to enabling hardware acceleration, that command is now removing my driver (the experimental AMD). However, when I did this just a few days ago my experimental driver wasn't being affected, because it remained installed on the system and in use. When I use the command *sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo* I receive:

```
The following package was automatically installed and is no longer required:  libindicator-messages-status-provider1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fglrx fglrx-amdcccle
**The following packages will be REMOVED:**
**  fglrx-amdcccle-experimental-9 fglrx-experimental-9**
The following NEW packages will be installed:
  fglrx fglrx-amdcccle libva-egl1 libva-glx1 vainfo xvba-va-driver
0 upgraded, 6 newly installed, 2 to remove and 0 not upgraded.
Need to get 0 B/72.6 MB of archives.
After this operation, 36.0 MB disk space will be freed.
Do you want to continue [Y/n]?
```

I'm hoping there's something that I overlooked, or just a simple flaw that happened that can be fixed. But I've tried removing the packages installed above, reinstalling the driver, and enabling hardware acceleration again and still am getting the same results.

Any help would be greatly appreciated!

---

### Post by QIII on 2013-06-20
Hello!  Me again.

If you look carefully at the output, you'll find that the experimental driver is being removed, but the standard fglrx and fglrx-amdcccle are being installed.  The experimental driver is just that.  Experimental.  It may be incompatible with the acceleration packages, so it is being removed.

I don't recommend ***either ***the fglrx-updates version or the experimental.

To make this clean, I would first remove the experimental driver and reboot back into the default Radeon driver.

Then, install the fglrx and fglrx-amdcccle packages, initialize and reboot.

Then install the acceleration packages and reboot again.

Let me know if that works out.

Best wishes!

---

