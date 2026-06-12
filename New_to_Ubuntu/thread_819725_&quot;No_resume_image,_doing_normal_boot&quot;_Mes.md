---
title: "&quot;No resume image, doing normal boot&quot; Message"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by dee_kay on 2008-06-05
Hello there.

I hope someone can help me.

Out of the blue my Gutsy powered laptop stopped booting to gnome and errored to the command line logon prompt.  The error ran something like

> No resume image, doing normal boot.


I made myself a new swap partition, checked the blkid and nano'd the fstab file to get things in line again.

Thing is when I try to run sudo update-initramfs -u I get a "command not found" error.

Any idea why?  Or have I been barking up the wrong tree completely?

Rgds,
Dave

---

### Post by ZabiGG on 2008-06-05
I'm sorry to say I use Hardy, but I've found a few links that might help with your error message on Google...

[https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)
[http://www.linuxforums.org/forum/ubuntu-help/108636-kinit-no-resume-image-doing-normal-boot.html](http://www.linuxforums.org/forum/ubuntu-help/108636-kinit-no-resume-image-doing-normal-boot.html)
[http://ubuntuforums.org/showthread.php?t=422875](http://ubuntuforums.org/showthread.php?t=422875)

Good luck,

Z.

---

### Post by dee_kay on 2008-06-06
> **ZabiGG said:**
> I'm sorry to say I use Hardy, but I've found a few links that might help with your error message on Google...

[https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)
[http://www.linuxforums.org/forum/ubuntu-help/108636-kinit-no-resume-image-doing-normal-boot.html](http://www.linuxforums.org/forum/ubuntu-help/108636-kinit-no-resume-image-doing-normal-boot.html)
[http://ubuntuforums.org/showthread.php?t=422875](http://ubuntuforums.org/showthread.php?t=422875)

Good luck,

Z.

Thanks ZabiGG.  Food for thought there.  I wish I understood the whole boot process better.

Since I rebuilt the swap partition and rebooted my machine the kinit message has disappeared.  I boot via GRUB and end up at a console screen with a login prompt.  I login with my userid and password but if I type some thing like

> sudo update-initramfs -u

or

> sudo apt-get install ubuntu-desktop

I error out.  I can see why the repositories might not be available to me if my network connection's gone but I don't know why the update-initramfs command can't be found.

One thing I did notice a few days ago was that the text size on my screen had changed during the boot process, i.e. when it got to the GRUB part the text was larger indicating that it had decided something new about my screen resolution perhaps.  It continued to boot normally into my gnome desktop though.  Yesterday, however, the first time I booted up it took ages to get to the desktop and when I rebooted to see if this was going to be an ongoing issue I got the kinit message.

Sorry for banging on a bit but if anyone else is reading this it might spark a suggestion.  I suppose right now, given the lack of error messages, my immediate problem is how to get back to my desktop environment.

Rgds,
Dave

---

### Post by dee_kay on 2008-06-06
> **dee_kay said:**
> Thanks ZabiGG.  Food for thought there.  I wish I understood the whole boot process better.

Since I rebuilt the swap partition and rebooted my machine the kinit message has disappeared.  I boot via GRUB and end up at a console screen with a login prompt.  I login with my userid and password but if I type some thing like



or



I error out.  I can see why the repositories might not be available to me if my network connection's gone but I don't know why the update-initramfs command can't be found.

One thing I did notice a few days ago was that the text size on my screen had changed during the boot process, i.e. when it got to the GRUB part the text was larger indicating that it had decided something new about my screen resolution perhaps.  It continued to boot normally into my gnome desktop though.  Yesterday, however, the first time I booted up it took ages to get to the desktop and when I rebooted to see if this was going to be an ongoing issue I got the kinit message.

Sorry for banging on a bit but if anyone else is reading this it might spark a suggestion.  I suppose right now, given the lack of error messages, my immediate problem is how to get back to my desktop environment.

Rgds,
Dave

Just to update things, although the

sudo update-initramfs -u

still errors with "command not found" I'm not getting the kinit error anymore.

The boot process just dumps me out at a command line and I can't start up my gnome desktop environment.

I've got a couple of other threads open relating to my issue (thread 820355 & 820793) and, seeing as the underlying reason for this thread has disappeared, I'll consider this thread closed.

Rgds,
Dave

---

