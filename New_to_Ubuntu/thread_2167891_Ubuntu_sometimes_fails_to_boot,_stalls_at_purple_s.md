---
title: "Ubuntu sometimes fails to boot, stalls at purple screen or black screen"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by nustang70 on 2013-08-15
Hi, I recently installed 13.04 exclusively (no dual boot) onto a recently-purchased refurbished Lenovo Z580.  It sometimes fails to boot and stalls at the purple screen, or at a black screen, sometimes before GRUB, sometimes after.  I've tried reinstalling 13.04, I've tried installing 12.04 LTS instead, and I've tried installing in Legacy mode in BIOS rather than UEFI.  I've used boot-repair, and I've followed its instruction to create a boot partition with gParted.  Nothing has worked.  Is this a hardware issue I should take up with Lenovo, or something else?    

I don't know if this is related, but when it does boot, it will momentarily display this line on a black screen before booting: [    8.934151] kvm: disabled by bios.    
I'm pretty sure I've seen a different number at times as well.  The only other thing I've changed which might have prompted that is that I've disabled Secureboot.  

Any help would be greatly appreciated.  It's been a trying few days.

---

### Post by Crusty Old Fart on 2013-08-16
> **nustang70 said:**
> ...I don't know if this is related, but when it does boot, it will momentarily display this line on a black screen before booting: [    8.934151] kvm: disabled by bios.    ...


If you are connecting to your monitor through a KVM splitter, remove it and do a clean reinstall without it hooked up. The KVM splitter gave me fits a few years ago while helping someone install Lucid. For some reason, which we never discovered, the KVM splitter was hosing our install and even subsequent boot ups afterwards. If you get everything running without it, maybe you can sell it on eBay.

---

### Post by Doomspark on 2013-08-16
This sounds a lot like what my Dell laptop is doing, and thus far I've been unable to get it fixed.  Did you install from a CD or USB?

---

### Post by nustang70 on 2013-08-16
Doomspark, I installed from USB. 

And thanks for the tip COF, but I'm using a laptop.

---

### Post by nustang70 on 2013-08-19
No other advice for this?

---

### Post by petejbm on 2013-09-01
I am geting the same problem. Sometimes I think I can fool the bootup by going into cmd and run info or similar. If that does not work I also have Fedora on disc. that also fails at same place but when I put Ubuntu back in it boots up Ok.
I currently have it running so dare not switch off in case I cannot get it up again. I treied to update sys last time I was running this but that failed as could not get lots of files. What is causing this is a mystery but someone somewhere knows how to cure it.

---

### Post by petejbm on 2013-09-01
By the way, what is KVM and what does it do???

---

### Post by Mark Phelps on 2013-09-01
I had similar problems and added "rootdelay=45" to the Linux kernel line in the default GRUB file (etc/default/grub).  Be sure to do a "sudo update-grub" afterward.

And yeah, before I catch grief about this only being needed for mounting filesystems from USB, this is what actually worked on my desktop for Ubuntu 12.10.

I didn't need this for any earlier version of Ubuntu, but 12.10 would randomly freeze during boot until I added this.

If "45" works, you can try reducing that until it doesn't work anymore.  I found that anything less than 45 still had the lockups, and I was willing to trade dealyed booting for a guarantee of getting (eventually) to a desktop.

---

