---
title: "Ubuntu booted up fine.. Until it didn't"
date: 2023-01-13
forum: New to Ubuntu
---

### Post by neilthommo on 2023-01-13
Hi, really hoping I can find a solution here!

I installed Ubuntu on my HP laptop (dual boot) in order to get started on the Odin Project and it was working fine for a while, then one day it failed to boot.

It would get to the HP logo screen with "Ubuntu" across the bottom-the spinning logo would appear, disappear, then that was it. 99% of the solutions seem to surround the graphics driver (nomodeset etc) but that didn't help, neither did a few other similar commands.

I then tried the "repair broken packages" fix and that moves me past the HP screen to a blank screen with a cursor but doesn't allow me to type.

Reinstalling Ubuntu wouldn't be the end of the world but I'd much rather just fix it if possible. Any ideas?

---

### Post by #&amp;thj^% on 2023-01-13
Please have a look here: [https://ubuntuforums.org/showthread.php?t=1743535](https://ubuntuforums.org/showthread.php?t=1743535)
That's a good place to start.
Good luck

---

### Post by yancek on 2023-01-13
Is this a single boot machine with only Ubuntu installed?
If not does, your other OS boot?
Is this an EFI install?  If so, can you select Ubuntu from the BIOS boot options menu?  Does that boot?
Were any software changes made just prior to this problem?  If so, what were they?

Did you get a warning message about broken packages?  If so, what was it and what command did you run to try to repair it?

---

### Post by neilthommo on 2023-01-14
> **yancek said:**
> Is this a single boot machine with only Ubuntu installed?
If not does, your other OS boot?
Is this an EFI install?  If so, can you select Ubuntu from the BIOS boot options menu?  Does that boot?
Were any software changes made just prior to this problem?  If so, what were they?

Did you get a warning message about broken packages?  If so, what was it and what command did you run to try to repair it?

It's dual boot with Windows 10. I can access the grub menu and choose Ubuntu, Windows, and other options including Ubuntu edit. Windows boots with no issues. 

I don't believe any software changes were made

---

### Post by yancek on 2023-01-14
Does Ubuntu still boot to the blinking cursor?  Does it do the same when you select it in the BIOS rather than from the Grub menu?
What graphics card do you have?  Did you do any update on Ubuntu?

You might try getting boot repair from the site below and running it with the Create BootInfo Summary option selected.  Do not try any repairs but post the link you get when boot repair finishes here and that will provide more details and someone may be able to help.  Use the 2nd option on the boot repair page with the ppa from the live Ubuntu USB you used to install it.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Impavidus on 2023-01-14
Can you boot an older kernel from the grub menu (using "advanced options for Ubuntu", or something like that)?
Can you boot an Ubuntu live disk? A live disk will give you access to your documents and log files. In /var/log/dpkg.log of your installed system you can find the packages that were recently upgraded, installed or removed. In an emergency, a live disk can be used for work, but it won't be convenient.

I use an HP laptop, but it's quite old and didn't come with all the quirks of more recent HPs.

---

