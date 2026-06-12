---
title: "[SOLVED] HIBERNATION is no different than Shut down + Restart... why?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by the8thstar on 2008-06-07
Whenever I choose Hibernation, the computer does what it's supposed to do and eventually after more than a minute of disk writing and lagging the power goes off.

Then when I turn it back on, the grub menu greets me and launches Ubuntu. There is no difference whatsoever with a normal boot. The applications I had opened have not been saved in the hibernation process and the computer still takes a minute to load the whole shabang.

**[COLOR="Blue"]So what's the point of hibernation? Can it be fixed?[/COLOR]** Your help will be greatly appreciated.

I use the latest kernel ...19.

---

### Post by PmDematagoda on 2008-06-07
> **the8thstar said:**
> Whenever I choose Hibernation, the computer does what it's supposed to do and eventually after more than a minute of disk writing and lagging the power goes off.

Then when I turn it back on, the grub menu greets me and launches Ubuntu. There is no difference whatsoever with a normal boot. The applications I had opened have not been saved in the hibernation process and the computer still takes a minute to load the whole shabang.

**[COLOR="Blue"]So what's the point of hibernation? Can it be fixed?[/COLOR]** Your help will be greatly appreciated.

I use the latest kernel ...19.

I believe that this is something with kernel 2.6.24 which is known to be having racy suspend and hibernation. Fortunately these issues seem to be fixed on kernel 2.6.25, so you can either compile that kernel or wait until Ubuntu Intrepid.

---

### Post by jflaker on 2008-06-07
> **the8thstar said:**
> Whenever I choose Hibernation, the computer does what it's supposed to do and eventually after more than a minute of disk writing and lagging the power goes off.

Then when I turn it back on, the grub menu greets me and launches Ubuntu. There is no difference whatsoever with a normal boot. The applications I had opened have not been saved in the hibernation process and the computer still takes a minute to load the whole shabang.

**[COLOR="Blue"]So what's the point of hibernation? Can it be fixed?[/COLOR]** Your help will be greatly appreciated.

I use the latest kernel ...19.

Is there confusion on suspend vs hibernate?  

If I remember right, suspend grabs a system state image then goes to near zero (not shut down) power....your system is running, but only to power RAM
Hibernate is similar to suspend, but the system will shut down instead....

Educate me if I am wrong.

---

### Post by wdaniels on 2008-06-07
> **the8thstar said:**
> **[COLOR="Blue"]So what's the point of hibernation? Can it be fixed?[/COLOR]**

The point of hibernation is not for this to happen - it's not doing this by design, and it's not a generic error in the hibernation process waiting to be fixed. Probably there is some hardware in your system which doesn't play nice with hibernation, but these things can be very difficult to debug.

First place to look for clues I think would be the kernel log.

Also, if you're lucky there may already be a solution documented for your particular computer model, if it's not a custom build...

---

### Post by the8thstar on 2008-06-07
> **jflaker said:**
> Is there confusion on suspend vs hibernate?  

If I remember right, suspend grabs a system state image then goes to near zero (not shut down) power....your system is running, but only to power RAM
Hibernate is similar to suspend, but the system will shut down instead....

Educate me if I am wrong.

Thanks but no, I know the difference between the two.

> **wdaniels said:**
> The point of hibernation is not for this to happen - it's not doing this by design, and it's not a generic error in the hibernation process waiting to be fixed. Probably there is some hardware in your system which doesn't play nice with hibernation, but these things can be very difficult to debug.

First place to look for clues I think would be the kernel log.

Also, if you're lucky there may already be a solution documented for your particular computer model, if it's not a custom build... 

Ok, I'll check that out. If this is indeed true, it's quite a bad surprise because my HP is only 1.5 years old. Oh well... I hope it's only a kernel issue.

---

### Post by wdaniels on 2008-06-07
> **jflaker said:**
> Hibernate is similar to suspend, but the system will shut down instead....

Yes, but on booting, it should just repopulate the RAM with the image from disk and restore the hardware state, not just follow a normal clean boot process. It seems something is going wrong before the "suspend to disk" process completes, so it can't just be restored.

---

### Post by PmDematagoda on 2008-06-07
> **wdaniels said:**
> Yes, but on booting, it should just repopulate the RAM with the image from disk and restore the hardware state, not just follow a normal clean boot process. It seems something is going wrong before the "suspend to disk" process completes, so it can't just be restored.

Usually this can be true in the case of drivers that don't work properly like that, one example usually being the Nvidia drivers, but even the kernel can play a part in this problem since the OP has an Intel card, which has a hibernation and suspend friendly driver.

---

### Post by louieb on 2008-06-07
Maybe something simple. Do you have enough swap space? Does it show up as available? Is ** /etc/initramfs-tools/conf.d/resume **pointing to your swap partition?  

If you find you have to fix [B]/etc/initramfs-tools/conf.d/resume
[/B]Then you will need to run. 
```
sudo dpkg-reconfigure  initramfs-tools
```

for the changes to go into effect.

---

### Post by the8thstar on 2008-06-07
> **louieb said:**
> Maybe something simple. Do you have enough swap space? Does it show up as available? Is ** /etc/initramfs-tools/conf.d/resume **pointing to your swap partition?  

If you find you have to fix [B]/etc/initramfs-tools/conf.d/resume
[/B]Then you will need to run. 
```
sudo dpkg-reconfigure  initramfs-tools
```

for the changes to go into effect.

Thanks for the tip, louieb. I'll try it.As for as swap is concerned, I have 4Gb.

---

### Post by the8thstar on 2008-06-08
Alright, I did a reinstall of my system, I ran the previous command and Hibernation works. It's surprisingly slow though... I'm not sure there is a real advantage to it compared with a regular shutdown in the end.

---

