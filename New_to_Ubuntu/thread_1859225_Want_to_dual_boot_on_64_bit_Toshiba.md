---
title: "Want to dual boot on 64 bit Toshiba"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by texastrey1836 on 2011-10-13
Hello all:
I have been enjoying the reviews of 11.10 and want to get back into the Ubuntu ballgame after some time away. I now have a Toshiba Satellite C655 with Intel Core i3 64 bit processor. I've combed through the forums and have seen people have a problem with this computer and Ubuntu before, but it *seems* that people have been able to get around these problems...
I have two questions:
1) Do people know a way I can test if my computer will work with Ubuntu or an online resource I'm missing that might explain things better?
2) I'm not sure whether to install 32-bit or 64-bit. I looked on the Ubuntu page and it says this:
[I]"64-bit PC (AMD64) desktop CD
    Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead."[/I]
Mine isn't listed as I have a Core i3 installed. Will 64 bit work on any Core chip?
Thanks, in advance, for these forums and all your help.

---

### Post by Paqman on 2011-10-13
> **texastrey1836 said:**
> 
1) Do people know a way I can test if my computer will work with Ubuntu

Yes, download Ubuntu and burn it to a CD or USB stick. You can then boot up from that disk or stick and check to see if the system runs ok before installing it. If you decide not to install, just shut down. It won't touch anything on your hard drive if you don't tell it to.

> 
2) I'm not sure whether to install 32-bit or 64-bit.

Your chip is 64-bit, so go ahead and install that.

---

### Post by texastrey1836 on 2011-10-13
Thank you. I'm trying it out now.

---

### Post by Musmanno on 2011-10-13
I have a Toshiba Satellite i3 64-bit laptop. 11.10 works great with it. All hardware detection was flawless, and it detected Windows and installed alongside just fine.

---

### Post by bwallum on 2011-10-13
If you decide to dual boot after trying 11.10 then I suggest you install onto it's own hard drive. This is why:-

Ubuntu issues are nearly always easily fixed but Windows can be a real pain due to licence requirements getting in the way. Dual booting involves a menu offering either OS (the boot loader menu is part of GRUB boot loader). If you put GRUB onto the hard drive that you install Ubuntu on, then the Windows drive and it's boot loader is unaffected. In your cmos (start up BIOS menu) point the first bootable hard drive to the one you loaded Ubuntu on.

Now if Ubuntu plays up, you want to remove it or sell it etc, you simply point the first bootable drive to Windows and reformat the drive you had Ubuntu on.

I have dual booted for years and now just run Ubuntu all the time. I did find Windows to be an issue from time to to time however and finally settled on the dual hard drives solution.

You can always install Ubuntu on the same hard drive as Windows in a separate partition. I am simply saying that the dual hard drive solution will probably give you less future grief.

Have fun, you wouldn't get me back to Windows if you paid me now!

---

### Post by texastrey1836 on 2011-10-13
Thanks. Just got done downloading the Ubuntu 11.10. Am testing it now. Thanks for all your help. Am going to have to dual boot the computer as I only have one hard drive on the laptop.

---

