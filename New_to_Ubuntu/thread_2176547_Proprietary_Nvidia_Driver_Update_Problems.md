---
title: "Proprietary Nvidia Driver Update Problems"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by Kanuckies on 2013-09-24
Running Ubuntu 3.2.0-53-generic, and attempted to upgrade the proprietary Nvidia drivers from 304 to 319.  It failed to reboot, hanging with a blinking cursor and the "could not write bytes: Broken pipe" error at random.  

This was resolved by logging into tty and running the following:  
sudo apt-get update 
sudo apt-get purge nvidia-* 
sudo apt-get install-nvidia-current-updates  

It now boots to the desktop (Cinnamon 1.8.8), but when checking the Additional Drivers tool, it states the 304 Driver is activated, but not currently in use.  The glgears tool results in 10,000fps and there are no 3d Unity issues.  

I found the following page for instructions about resolving, but would like to confirm the appropriate steps forward to resolve.  This is my second Ubuntu installation; the first attempt was wrecked by installing a new graphics card (different brand) and breaking several dependancies trying random "fixes" found on the various support forums.  I learned to stick with Synaptic for installing/upgrading packages after that exercise.  [URL="https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"]
https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia[/URL]  

I abandoned Windows XP on my latest build earlier this year to avoid Win7/8.  The linux command structure/usage is still new, so baby steps would be greatly appreciated.  Thanks in advance.

---

### Post by newb85 on 2013-09-25
Which release of Ubuntu are you using? 12.04?  Which section(s) on that page are you specifically looking at?

Jockey-text has been removed by default in the latest Ubuntu.

---

### Post by Kanuckies on 2013-09-25
Using Ubuntu 12.04LTS

Looking at the instructions pasted below.  Installation worked, however the system is not using the proprietary drivers.

**[SIZE=2][FONT=arial]Installation Fails[/FONT][/SIZE]**
[SIZE=2][FONT=arial]1. If the restricted driver remains unactivated after attempting to activate it in the *Additional Drivers* dialog, you may not have the appropriate linux headers installed to compile the driver. Ensure that the linux-headers-XXX and linux-restricted-modules-XXX packages are installed, where XXX matches the version of the kernel you are using. 
2. If the activation hangs on download/install dialog, you can install the driver using **System -> Administration -> Synaptic Package Manager**, make sure you pick the latest driver version recommended by the **Additional Drivers** tool and all its dependencies. Then go to the **Additional Drivers** tool and activate the driver you just installed. 
[/FONT][/SIZE]
[B][SIZE=2][FONT=arial]Driver Not Active
[/FONT][/SIZE][/B][SIZE=2][FONT=arial]1. X has not been configured to use the new driver. Open a terminal, run sudo nvidia-xconfig, and restart X (reboot works).



Below is terminal output of the current drivers in use:
sudo lspci -k
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 440] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 838a
    Kernel driver in use: nvidia
    Kernel modules: nvidia_304_updates, nouveau, nvidiafb

[/FONT][/SIZE]How do I correct without corrupting the system?

---

### Post by Kanuckies on 2013-09-25
I think the issue is the Additional Drivers module is broken.  Before this started, nvidia 319 was the recommended driver in the list.  After executing the lines in the first post, 304 is the newest driver in the list.  I don't want to perform the manual install, and I tried installing the 319 version from Synaptic, but ran into an API conflict on reboot.  What file must be modified to get the system to recognize version 319 after reboot?

---

### Post by Kanuckies on 2013-09-26
Found an article detailing exactly the same "problem" I am experiencing which goes on to state that there isn't an issue.  The Additional Drivers module seems to be broken.  The problem this causes for me is the most recent proprietary graphics driver doesn't appear as an option to install.  Also, Steam seems to be referencing the same status source as it reports needing to update drivers.  The Steam update application fails after launch though.  I will continue to update this post as I dig deeper and appreciate everyones' help on these forums.

[http://www.dedoimedo.com/computers/ubuntu-natty-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-natty-nvidia.html)

---

### Post by f4bm4n on 2013-09-27
[SIZE=2][FONT=arial]I'm in the same boat. Upgrading from 304 to 319 messed up my installation. "purge" left me in your situation. 

sudo lspci -k[/FONT][/SIZE]
> 01:00.0 VGA compatible controller: NVIDIA Corporation GT218M [GeForce 310M] (rev a2)
    Subsystem: Lenovo Device 392d
    Kernel driver in use: nvidia
    Kernel modules: nvidia_304, nouveau, nvidiafb

[SIZE=2][FONT=arial]Do you have any problems with the solution provided in the binarydriverhowto - besides not working? I would like to try it myself, but am afraid of the trouble it may cause...[/FONT][/SIZE]

---

### Post by Kanuckies on 2013-09-27
I didn't try the solution at the first link; I wrecked my first install by arbitrarily runing terminal commands which broke several dependencies.  I wanted to confirm here first if that was a good approach.

I did try again to install the 319 driver from Synaptic (Proprietary Drivers module doesn't show it anymore).  I  am unclear on the way linux handles driver removal via Synaptic; is it effective immediately after remove, or on the next restart?  While the 304 driver was still installed, I also installed the 319 driver.  The next reboot resulted in the same hang, but I let it time out to give an error message like the one at this link regarding API Mismatch:
[http://askubuntu.com/questions/145195/nvidia-driver-problem-after-updating-to-12-04](http://askubuntu.com/questions/145195/nvidia-driver-problem-after-updating-to-12-04)
I was able to recover again, but it wasn't so easy.  I ran the three sudo commands from the first post, but upon reboot, it would only go into a 2D desktop; the proprietary driver wasn't loaded.  I went into the Proprietary Drivers module, selected the 304 driver (it wasn't activated), then activated and restarted.  All was well after this.  I tried  removing and reinstalling the Proprietary Drivers (jockey-gtk) module, but same issue.

I wish there were concise directions for how to completely change video drivers in Ubuntu; as if you were changing to a different brand of card.  Are you supposed to remove the existing driver first, then install new driver?  Do you install a generic driver before shutting down?  Do you rename appropriate configuration files so they don't attempt to load the wrong driver version?  What happens if the current card fails, then a replacement is re-inserted?  Will default 2D drivers load, or do you have to execute terminal commands?  There are several iterations of what to do on the internet, an no two instructions are the same.

Since nothing is malfunctioning, I haven't tried again; it is just an annoyance.  Games are running fine in Steam; HL2 based games anyway.

If I attempt again, I will use Synaptic by:

[INDENT]1.  Remove current driver; nvidia-304-updates
2.  Install new driver; nvidia-319-updates
3.  Restart

[/INDENT]
 Hopefully the Xorg.conf file doesn't need any attention (possibly rename so a new version has to be created).  
Note that method needs input from a more experienced user.

---

