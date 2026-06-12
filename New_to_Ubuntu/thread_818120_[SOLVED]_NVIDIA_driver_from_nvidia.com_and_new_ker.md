---
title: "[SOLVED] NVIDIA driver from nvidia.com and new kernels etc."
date: 2008-06-04
forum: New to Ubuntu
---

### Post by philinux on 2008-06-04
> When using manually installed NVIDIA binary drivers you will need to reinstall the driver every time packages related to mesa or linux-image are updated (see the Kernel and Mesa Updates section for details). Attempts to revert to the Ubuntu provided NVIDIA binary drivers may prove troublesome and upgrades to the next Ubuntu release may fail unless the manual install is correctly uninstalled first.

Read this and thought arrrgghh. I've installed driver 173.14.05 from the site.

Had to reinstall it after kernel 18 update.

As far as I can tell I'm getting no difference in performance than with the nvidia-glx-new 169.12 version in synaptic.

Regarding the above quote. Should I just stick with it now or is there no way back?

[COLOR="Red"]Edit- save you reading the whole thread.[/COLOR]
Ok here's the deal. I'm trying to go back to using the driver in the repo and remove nvidia.com's

I used envyng which offered to uninstall the driver. Off it goes doing it's stuff, done.

Right I thought I'll reset the /etc/modules and /etc/defaults/linux-restricted-modules-common back to normal.

Copied a backup xorg.conf I saved before I started any of this.

Reboot.

And still got NVIDIA Driver Version 173.14.05 which works with no blacklisted modules or modified xorg.conf.

Could someone explain

---

### Post by kpkeerthi on 2008-06-04
Stick with what repo has/provides. Thats always better Stability wise). The easiest way to uninstall 173.xx.xx is by using envy. 

Uninstall the driver using envy. Switch to "nv" in xorg.conf and then install off repo using System -> Admin -> Hardware Drivers.

---

### Post by philinux on 2008-06-04
I followed this really good guide to get it installed.

[http://ubuntuforums.org/showpost.php?p=5082510&postcount=2](http://ubuntuforums.org/showpost.php?p=5082510&postcount=2)

I might stick with it for now.

I supposed I should have realised that new kernel means it need to be recompiled.

I cant believe how many kernels have come out lately and they've been borking wireless, wired net, suspend&hibernate, etc etc. Not good.

---

### Post by SunnyRabbiera on 2008-06-04
> **philinux said:**
> I followed this really good guide to get it installed.

[http://ubuntuforums.org/showpost.php?p=5082510&postcount=2](http://ubuntuforums.org/showpost.php?p=5082510&postcount=2)

I might stick with it for now.

I supposed I should have realised that new kernel means it need to be recompiled.

I cant believe how many kernels have come out lately and they've been borking wireless, wired net, suspend&hibernate, etc etc. Not good.

well I know there is a new kernel family out, and its still new.
Most kernels are a bit buggy when they first come out.

---

### Post by bumanie on 2008-06-04
G'day Philinux,
Personally, I would stick with the ubuntu driver unless it didn't work in your particular system (which I know is not the case). Updating manually every time there is a kernel upgrade would be a pain in the ... you know where.

---

### Post by philinux on 2008-06-04
> **bumanie said:**
> G'day Philinux,
Personally, I would stick with the ubuntu driver unless it didn't work in your particular system (which I know is not the case). Updating manually every time there is a kernel upgrade would be a pain in the ... you know where.

Cheers, I'm off to the gym this arvo. So I'll leave fiddling to uninstall the driver till later.

---

### Post by sweeneytodd on 2008-06-04
don't know what nividia's problem is, but as far as i'm concerned they can rot in hell, they're up there with the vista crew, thinking they're ahead of everybody else only to crash in their self-absorbed egos

---

### Post by philinux on 2008-06-04
Ok here's the deal. I'm trying to go back to using the driver in the repo and remove nvidia.com's

I used envyng which offered to uninstall the driver. Off it goes doing it's stuff, done. 

Right I thought I'll reset the /etc/modules and /etc/defaults/linux-restricted-modules-common back to normal. 

Copied a backup xorg.conf I saved before I started any of this.

Reboot.

And still got NVIDIA Driver Version 173.14.05 which works with no blacklisted modules or modified xorg.conf.

Could someone explain. :)

---

### Post by philinux on 2008-06-05
Still got hi res but very curious.

---

### Post by philinux on 2008-06-05
Bump

---

### Post by philinux on 2008-06-05
Bump in case nvidia experts around :lolflag:

---

### Post by yipperzz on 2008-06-05
> **sweeneytodd said:**
> don't know what nividia's problem is, but as far as i'm concerned they can rot in hell, they're up there with the vista crew, thinking they're ahead of everybody else only to crash in their self-absorbed egos

so what makes ati any better as far as the drivers?  i'm having more issues with my ati card right now than my nvidia card. if you go away from the default drivers, won't you have the same issue no matter which brand you own?

---

### Post by philinux on 2008-06-05
That's no help, thanks.

---

### Post by philinux on 2008-06-05
bump

---

### Post by kpkeerthi on 2008-06-06
> **philinux said:**
> Ok here's the deal. I'm trying to go back to using the driver in the repo and remove nvidia.com's

I used envyng which offered to uninstall the driver. Off it goes doing it's stuff, done. 

Right I thought I'll reset the /etc/modules and /etc/defaults/linux-restricted-modules-common back to normal. 

Copied a backup xorg.conf I saved before I started any of this.

Reboot.

**And still got NVIDIA Driver Version 173.14.05 which works with no blacklisted modules or modified xorg.conf.**

Could someone explain. :)

How are you checking the driver version? Using **modinfo nvidia** or with the nvidia-settings tool. 

Try reinstalling nvidia-settings from the the repo, reboot and check again.

```

sudo aptitude purge nvidia-settings
sudo aptitude install nvidia-settings

```

---

### Post by Bachstelze on 2008-06-06
As the text you quoted in your firs message says, reverting to the Ubuntu-packaged driver can be quite tricky and troublesome. Not worth the hassle, if you ask me. Since you have the nvidia.com drivers installed and working, why not stick with them ?

---

### Post by philinux on 2008-06-06
This what modinfo shows and the screens shot show the the nvidia settings.

```
 modinfo nvidia
filename:       /lib/modules/2.6.24-18-generic/kernel/drivers/video/nvidia.ko
license:        NVIDIA
alias:          char-major-195-*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        i2c-core
vermagic:       2.6.24-18-generic SMP mod_unload 
parm:           NVreg_EnableVia4x:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_UseVBios:int
parm:           NVreg_RMEdgeIntrCheck:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_NvAGP:int
parm:           nv_disable_pat:int

```

---

### Post by nanog on 2008-06-06
You have to manually remove the nvidia driver by going to the directory where you installed it and runnning:

```
sudo sh name_of_the_nvidia_installer --uninstall
```

Using the driver in the ubuntu repo does not always result in a more stable system. There are significant bugs in the 169.12 driver that were fixed in the new 173.14 driver. (I have a box that was basically unuseable with 169.12 due to a known memory leak bug.)

---

### Post by philinux on 2008-06-07
> **nanog said:**
> You have to manually remove the nvidia driver by going to the directory where you installed it and runnning:

```
sudo sh name_of_the_nvidia_installer --uninstall
```

Using the driver in the ubuntu repo does not always result in a more stable system. There are significant bugs in the 169.12 driver that were fixed in the new 173.14 driver. (I have a box that was basically unuseable with 169.12 due to a known memory leak bug.)
 
I'm sticking with 173.14.05

FF stable, compiz stable, wine games stable. etc etc.

Thanks all for help.

---

