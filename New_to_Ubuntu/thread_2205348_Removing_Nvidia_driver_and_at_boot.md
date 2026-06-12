---
title: "Removing Nvidia driver and at boot"
date: 2014-02-13
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-02-13
Hi,

I am planning to get a new computer and I want to migrate my existing Ubuntu installation by cloning it and restoring it to the new computer. But here is the problem, my old computer has the Nvidia driver and the new computer I am planning to get will have an intel card. So the clone will boot but the graphic wouldn't work, how can I remove the Nvidia driver and switch back to the open driver at boot? Thanks

Edited: since I am planning on keeping the old one as well so it would not be desirable to remove the driver before cloning.

---

### Post by howefield on 2014-02-13
If it were me I'd take the opportunity to have a nice clean and pristine install on the new hardware. Probably quicker than any other option :)

But if you want to clone, just disable the nvidia drivers via Additional Drivers so you are using nouveau and then do the clone.

---

### Post by monkeybrain20122 on 2014-02-13
I would prefer cloning because my system is quite customized and I have compiled quite a bit from source, don't want to go through the troubles of doing that unless it is necessary and I don't plan on going to 14.04 until July when 13.10 reaches eol.

Since I would like to keep the old machine for other purposes I would prefer not removing the driver for cloning.

---

### Post by oldfred on 2014-02-13
New computer will be UEFI with gpt partitioning, your older computer probably is BIOS with MBR partitioning.
You will have to totally erase new drive and remove all traces of gpt to have to work as an old BIOS with MBR.
New UEFI does have a CSM mode.
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

May actually just be easier to remove hard drive from new system and install a new blank drive.
Some have posted that with a new laptop they buy a higher end system with hard drive, but immediately remove hard drive and install SSD. Then later they can restore hard drive and sell laptop with unused Windows.

---

### Post by grahammechanical on 2014-02-13
May I suggest that on the first boot after putting the cloned OS on the new machine that you load into Recovery Mode and then select Resume. That should get you to a desktop without loading a proprietary video driver. From 13.10 onward we get what I think of as a sub set of Nouveau called llvmpipe. It is used by Ubuntu as a fallback for graphic adapters that do not have 3D acceleration.

Once at the desktop you can change the Nvidia driver to an Intel driver using Additional Drivers.

Regards

---

### Post by monkeybrain20122 on 2014-02-13
> **grahammechanical said:**
> May I suggest that on the first boot after putting the cloned OS on the new machine that you load into Recovery Mode and then select Resume. That should get you to a desktop without loading a proprietary video driver. From 13.10 onward we get what I think of as a sub set of Nouveau called llvmpipe. It is used by Ubuntu as a fallback for graphic adapters that do not have 3D acceleration.

Once at the desktop you can change the Nvidia driver to an Intel driver using Additional Drivers.

Regards

Thanks, that makes sense.

---

### Post by monkeybrain20122 on 2014-02-13
> **oldfred said:**
> New computer will be UEFI with gpt partitioning, your older computer probably is BIOS with MBR partitioning.
You will have to totally erase new drive and remove all traces of gpt to have to work as an old BIOS with MBR.
New UEFI does have a CSM mode.
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

May actually just be easier to remove hard drive from new system and install a new blank drive.
Some have posted that with a new laptop they buy a higher end system with hard drive, but immediately remove hard drive and install SSD. Then later they can restore hard drive and sell laptop with unused Windows.

Well actually I am planning to get a system 76 or Zareason computer which already has Ubuntu preinstalled. Will these considerations still apply?

---

### Post by oldfred on 2014-02-13
Then you already have a nice clean install of Linux.

I would backup and restore your /home. Perhaps some settings from /etc if you customized hardware settings.
Export list of installed apps and install those.
The only issue then is the custom complied apps, but can you not just copy them over without recompiling? Or if different version of Ubuntu then you may have dependency issues.

---

### Post by monkeybrain20122 on 2014-02-16
This turns out to be really simple. Apparently all I have to do is to remove the file /etc/X11/xorg.conf and boot normally. The Nvidia driver won't load then. I suppose you can do this in recovery mode > root session. But I am running another Ubuntu session on another drive, so I just plugged in the hard drive with the Ubuntu that has the Nvidia driver and removed xorg.conf there. Then reboot from the second drive, everything works normally 

(This is a try run with a partial clone and I happen to get my hands on an Intel machine)

---

