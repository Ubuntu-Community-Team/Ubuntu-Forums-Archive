---
title: "Good virtual machine for games"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Sydius on 2008-06-26
Me and my girlfriend both dual-boot with Windows XP and Ubuntu 8.04, because we play many games that don't run well in Wine.  Many of these games, though, are really not resource-intensive, and should work fine in a virtual machine, so that's what we do most of the time.  However, the virtual machine doesn't have sound (we used the virt-manager and qemu).

I was wondering if there was A) some easy way to get sound working in the above, or B) some other (easy to setup/use) virtual machine system we might try that does have sound.

---

### Post by Elfy on 2008-06-26
I use vbox and it does have sound but only 2d graphics, I don't know too much about qemu tbh

But I found this in a thread regarding similar

> Or soundhw sb16 (for a sound blaster 16 emulation), soundhw es1370
It is the same options and flags as Qemu.

[This]("http://ubuntuforums.org/showthread.php?t=732062") is the thread, so it would seem it can be done - is there a man page for qemu, maybe the options are there.

Edit - there is more information regarding sound in qemu at the documentation page for it in 3.3
[http://bellard.org/qemu/qemu-doc.html](http://bellard.org/qemu/qemu-doc.html)

---

### Post by pytheas22 on 2008-06-26
Virtual Box works fine for me, sound and everything.

Keep in mind that no virtual machines are going to support games requiring video acceleration (vmware does in principle, but I've never heard of it actually coming close to working).  But everything else will be fine.

EDIT: also if you're talking about really old DOS games, (this comes to mind because post number 2 mentions sound blaster), use dosbox.  It will be a lot better than a virtual machine for running DOS programs.

---

