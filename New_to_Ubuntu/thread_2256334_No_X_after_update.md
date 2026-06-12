---
title: "No X after update"
date: 2014-12-11
forum: New to Ubuntu
---

### Post by ray9 on 2014-12-11
Ubuntu 14.04 LTS.  An update appeared so I clicked the update, one that required my password and restart, then no Ubuntu.  How can I restore my system?  A password  and restart required update usually means a new kernel which can mean trouble I've found out.  I do get grub, then nothing.

---

### Post by JeQhdMD on 2014-12-11
[http://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version](http://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version)

try above procedure, but then I would again try the update process, making sure it completes with no errors (expand display of update - check logs in var, etc.)

Oh & by the way, 99.9% of kernel updates cause no problems whatsoever.  I've only had one failure since 2003.

---

### Post by grahammechanical on 2014-12-11
You say that you get the Grub boot menu. So, at the menu select Advanced Options for Ubuntu and then select Recovery Mode. At the Recovery menu select Resume. That will try to load Ubuntu without using a proprietary video driver. Instead an open source video driver called llvmpipe will be used. If you get to a desktop you will notice that llvmpipe is not as fast as the normal video driver, even the Nouveau open source video driver. But now that you are at the desktop (hopefully) you can change video drivers. System Settings>Software and Updates>Additional Drivers tab.

Oh, by the way, Advance Options will allow us to load the previous kernel. If that works we can continue to use it until an update fixes the issue with the new kernel. Or not as the case may be.

Regards.

---

### Post by ray9 on 2014-12-11
Thanks for the reply.  I'm assuming there was a kernel change, from 3.13.0-40-generic to 43.  So I got into grub and clicked on the advanced line and then recovery.  Then I booted into a shell and typed restart and got it up again but the resolution is off and I'm afraid to change it because I  am pretty sure this isn't fixed.  I'll go to the link you provided now.

---

### Post by ray9 on 2014-12-11
> **grahammechanical said:**
> You say that you get the Grub boot menu. So, at the menu select Advanced Options for Ubuntu and then select Recovery Mode. At the Recovery menu select Resume. That will try to load Ubuntu without using a proprietary video driver. Instead an open source video driver called llvmpipe will be used. If you get to a desktop you will notice that llvmpipe is not as fast as the normal video driver, even the Nouveau open source video driver. But now that you are at the desktop (hopefully) you can change video drivers. System Settings>Software and Updates>Additional Drivers tab.

Oh, by the way, Advance Options will allow us to load the previous kernel. If that works we can continue to use it until an update fixes the issue with the new kernel. Or not as the case may be.

Regards.
So I did what you suggested.  This is what "additional drivers" shows:  green dot>Advanced Micro Devices Inc AMD/ATI Cedar Radeon 5000/6000/7350, this is the recommended driver.
brown dot>using X org x server AMD/ATI driver wrapper from x server x org video ati open source
Then it shows two other options, Using AMD graphics accelerators from fglrx(proprietory) and amd graphics fglrx-updates.
Wow, slow I guess.  How can I go back to the other kernel, the post above?  Sudo apt-get install linux-image-3.13.0-40-generic?  How can I use "Advanced Options" to load the previous kernel?

---

### Post by ray9 on 2014-12-11
Ok I figured that out.  Went into advanced and booted to "40" kernel and all is well.  So my question is obvious I guess but I'll ask anyway, from now on until a new kernel comes out I'm going to have to go into advanced to boot the old kernel or should I reinstall it???

---

### Post by ajgreeny on 2014-12-11
You could uninstall the 3.13.0-43 kernel if you really want to, then the system will boot into the 3.13.0-40 version by default, but it would be far better in my opinion, if you simply accepted the recommendation and installed the Cedar Radeon 5000/6000/7350 AMD driver for the 3.13.0-43 kernel, which will then probably work fine, just like the current kernel does.

---

### Post by ray9 on 2014-12-11
The green dot says it's using the recommened driver.  I'm confused.  Besides it won't let me accept anything.  Is the option with the brown dot the driver recommendation,  "Using X org x server AMD/ATI driver wrapper from x server x org video ati open source"?  Because it looks like it has the correct driver.  So why don't I have any X?

---

### Post by ajgreeny on 2014-12-12
> **ray9 said:**
> The green dot says it's using the recommened driver.  I'm confused.  Besides it won't let me accept anything.  Is the option with the brown dot the driver recommendation,  "Using X org x server AMD/ATI driver wrapper from x server x org video ati open source"?  Because it looks like it has the correct driver.  So why don't I have any X?
OK, sorry about that; I've never needed to use the Additional Drivers that are available to Ubuntu, so did not realise the significance of the green dot.

---

### Post by ray9 on 2014-12-12
Do you have any idea how I should proceed?  I'm thinking remove the kernel but I don't know how.

---

### Post by ray9 on 2014-12-13
Installed the old kernel.  Works good again now.

---

