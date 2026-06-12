---
title: "[SOLVED] Minimal cd installation. Hard drive not detected."
date: 2008-07-10
forum: New to Ubuntu
---

### Post by cristo-father on 2008-07-10
Hi
While i was in the pre-install sections of the minimal cd version of hardy 64bit, i got stopped by a message saying that my hard drive was not detected and i was given a list of drivers to chose.
Can anyone help me? Which one should i choose?
By the way my hd is 500GB sata2 16MB cache.
Thanks

---

### Post by sydbat on 2008-07-10
Does the hard drive show up in BIOS? Did you have any other OS on this machine before? Using the same HDD?

---

### Post by cristo-father on 2008-07-10
> **sydbat said:**
> Does the hard drive show up in BIOS? 
How do i see if the hard drive is shown in bios?
> **sydbat said:**
> Did you have any other OS on this machine before? 
Windows xp 64 bit

> **sydbat said:**
> Using the same HDD?
Yes i am using the same harddrive.

---

### Post by sydbat on 2008-07-10
Well, the last two should answer the first one (BIOS). However, to make sure, BIOS is entered when you first boot up your machine, before any OS options are seen. Hitting the 'delete' key or 'F1', or 'Esc' usually gets you into it.

In BIOS, you do have to be careful, but everything is straight forward. The first screen should show your System Time followed by a list of attached drives, RAM, etc. Your SATA drive should be listed. 

But, as I said, if you have been able to boot into Windows on the same drive, that tells me it is recognized in BIOS and you may not need to go in there.

---

### Post by cristo-father on 2008-07-10
> **sydbat said:**
> Well, the last two should answer the first one (BIOS). However, to make sure, BIOS is entered when you first boot up your machine, before any OS options are seen. Hitting the 'delete' key or 'F1', or 'Esc' usually gets you into it.

In BIOS, you do have to be careful, but everything is straight forward. The first screen should show your System Time followed by a list of attached drives, RAM, etc. Your SATA drive should be listed. 

But, as I said, if you have been able to boot into Windows on the same drive, that tells me it is recognized in BIOS and you may not need to go in there.

Yep. I went to bios and the hd was detected.

---

### Post by sydbat on 2008-07-10
Hmmm...I'm out of suggestions. If the HDD is detected in BIOS, AND you can boot into XP-64, I really do not know why the Ubuntu install is asking where the drive is. If you can see the drive in the "Live CD" session, it should be there for install.

---

### Post by cristo-father on 2008-07-10
> **sydbat said:**
> Hmmm...I'm out of suggestions. If the HDD is detected in BIOS, AND you can boot into XP-64, I really do not know why the Ubuntu install is asking where the drive is. If you can see the drive in the "Live CD" session, it should be there for install.

I am installing the minimalcd version. It does not have a livecd option.

---

### Post by sydbat on 2008-07-10
Try downloading the full 600+Mb CD and see if that helps. Then you can do the "Live CD" bit.

---

### Post by cristo-father on 2008-07-10
> **sydbat said:**
> Try downloading the full 600+Mb CD and see if that helps. Then you can do the "Live CD" bit.

I see my disk from the live cd. Any suggestion on how to solve the problem?

---

### Post by sydbat on 2008-07-10
OK...let's review. 
1) You are attempting to do a fresh install of Ubuntu 8.04 from a minimal install CD. 
2) You are doing this in order to dual boot with XP-64, yes? 
3) But the install itself is not recognizing that the SATA drive is even there.

Does the minimal CD have wubi as an option? In windows, put the CD in and see if it asks if you want to install it. Otherwise, maybe try the full install CD and see if that clears everything up.

Sorry I can't be of more assistance with this.

---

### Post by avtolle on 2008-07-10
OK, as I recommended to you on one of your other threads (was that one about the same computer?), use the all_generic_ide boot option.

---

### Post by cristo-father on 2008-07-10
> **avtolle said:**
> OK, as I recommended to you on one of your other threads (was that one about the same computer?), use the all_generic_ide boot option.

How do i do that with the minimalcd version?
And btw i think it does not have wubi.

---

### Post by avtolle on 2008-07-10
Press F1 at the initial screen for advanced options, and follow the directions there.

No, the minimal install iso does not have Wubi.

With the specs of your hardware, why are you trying to do a minimum install anyway?

---

### Post by cristo-father on 2008-07-10
> **avtolle said:**
> Press F1 at the initial screen for advanced options, and follow the directions there.

No, the minimal install iso does not have Wubi.

With the specs of your hardware, why are you trying to do a minimum install anyway?

Because with the "normal" install i cannot boot properly...
[http://ubuntuforums.org/showthread.php?t=854774&highlight=busybox](http://ubuntuforums.org/showthread.php?t=854774&highlight=busybox)

---

### Post by cristo-father on 2008-07-10
> **avtolle said:**
> Press F1 at the initial screen for advanced options, and follow the directions there.

The directions are not that clear...maybe it is because i am dumb.
Could you go beyond the steps you just mentioned? In other words can you be more rigorous and in depth with the steps that follow F1?

---

### Post by avtolle on 2008-07-10
Well, if it won't boot from a regular installation, there's a very high probability it won't boot from the minimal installation, as the problem seems to be the SATA drive. I'm not very familiar with the options that are given when one selects F1 under the minimal installation. 

BTW, what driver options were you given (that you mention in one of the earlier posts you made)? Perhaps if you list them, someone with more knowledge than I can identify the one you need.

---

### Post by avtolle on 2008-07-10
A thought; if the all_generic_ide boot option allowed you to install, you might need to try that on boot (assuming you have your "normal" install still on that computer). See [https://help.ubuntu.com/community/BootOptions#When%20installing](https://help.ubuntu.com/community/BootOptions#When%20installing) for both how to edit the boot script on boot to include this option, as well as how to make that permanent.

---

### Post by cristo-father on 2008-07-10
> **avtolle said:**
> A thought; if the all_generic_ide boot option allowed you to install, you might need to try that on boot (assuming you have your "normal" install still on that computer). See [https://help.ubuntu.com/community/BootOptions#When%20installing](https://help.ubuntu.com/community/BootOptions#When%20installing) for both how to edit the boot script on boot to include this option, as well as how to make that permanent.

Thank you soooooooooooooooooooooooooooooooooooooooooo much!
It finally works.

---

