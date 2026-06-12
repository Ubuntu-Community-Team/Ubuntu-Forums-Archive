---
title: "no hdmi signal after newest updates"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by johnnyford on 2012-11-30
i got 16 ubuntu updates this morning. i installed them. i restarted my computer, like i was asked. now my asus monitor insists there is no hdmi signal. im using vga. 

however, i manually turned my zotac zbox on and off a few times. on hdmi, i get the "Zotac ZBOX" screen, then a dark purple screen, which i thought was a part of ubuntu's start up, then it goes black and says no hdmi signal. ugh. do i need a new driver or something?

---

### Post by johnnyford on 2012-11-30
just so ya know, problem solved. my friend talked me through it. basically, uhh, i had to, like, deactivate a newly installed kernal and revert, i think is the word, to the old one. we used grub customizer and some program line from daniel richter. my friend thinks that hopefully in a new update theyll send me something that fixes it from that angle.

---

### Post by squakie on 2012-12-01
It's quite possible you just needed to reinstall the video driver, or add a boot option for it to work.  A new kernel image means that if you had a non-Ubuntu video driver (things like nVidia proprietary) then you need to reinstall it after a kernel update.  Similarly, if you had special boot options such as nomodeset, acpi=off or noapic may also be lost unless you created your own entries in the new xorg configuration files.  I suspect there are default files there that get replaced with some updates, so if you updated one of those files before you may need to do so now.

---

### Post by NikTh on 2012-12-01
> **squakie said:**
> It's quite possible you just needed to reinstall the video driver, 

Yes, sometimes that can be happen. Especially if you have closed source driver (additional driver) for graphics card installed.

You have to use the --reinstall option , through apt-get to re-install the driver 

_Example for nvidia-current driver_
```
sudo apt-get install --reinstall nvidia-current
```

---

### Post by SeijiSensei on 2012-12-01
> **johnnyford said:**
> just so ya know, problem solved. my friend talked me through it. basically, uhh, i had to, like, deactivate a newly installed kernal and revert, i think is the word, to the old one. we used grub customizer and some program line from daniel richter. my friend thinks that hopefully in a new update theyll send me something that fixes it from that angle.

For future reference, if you install a kernel update, the previous kernel will be preserved and available from the grub menu during boot.  You'll see an entry for "previous versions".  If you select it, it will show you past kernels.  Just select the one at the top of the list, as that is the most recent one you used.  If the problem goes away with the new kernel, you'll know where the issue is.

---

