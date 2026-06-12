---
title: "Won't boot from live CD"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by RBlank111 on 2008-10-19
Stuck at command prompt(initramfs) _

---

### Post by Scarath on 2008-10-19
Could you give more detail? Does the disk not register? Does it start to boot then freeze? 

1. Is the boot priority in the bios set to the CD drive?

2. Try burning another Live CD.

---

### Post by t0p on 2008-10-19
> **RBlank111 said:**
> Stuck at command prompt(initramfs) _

Try following the advice Thisislaw gave me in [this thread]("http://ubuntuforums.org/showthread.php?t=930225").  It didn't work for me on that occasion, but I know it *has* helped other people in the situation you describe.

**EDIT:** You may also find some help by keeping an eye on [this thread]("http://ubuntuforums.org/showthread.php?t=952975").

---

### Post by Drakkor on 2008-10-19
Hey,I'm online with the live disc finally, RBlank was posting for me, but I wanted to try to restore grub,but I hit Applications,and nothing happens,wanted to get to the terminal, but no go :confused:

---

### Post by Drakkor on 2008-10-20
'bumpZ"

---

### Post by Scarath on 2008-10-20
Hit Ctrl+Alt+F1 when you are on the desktop, that should drop you back to terminal mode, then you can start restoring grub from there.

---

### Post by desperado665 on 2008-10-20
To get my pc to boot when installing, I have to use the following additional parameters, otherwise I would also get the same (initramfs) prompt (sometimes referred to as busybox)

acpi=force all_generic_ide floppy=off irqpoll

Granted, I'm running Hardy on an older AthlonXP machine, but that was the only way I could bypass the busybox prompt since Fiesty

---

