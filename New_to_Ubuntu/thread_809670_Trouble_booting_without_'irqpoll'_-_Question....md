---
title: "Trouble booting without 'irqpoll' - Question..."
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Kale Kold on 2008-05-27
The only way i can get Ubuntu to run on my machine is to use the 'irqpoll' kernel option in the boot setup (f6) on the live cd. I read this somewhere that it helps this bug.

1. What does this actually do?
2. If i installed Ubuntu on my machine can this option be set permanently on boot?
3. Is there a fix?

Ubuntu 8.04 LTS (64 bit)
Intel core2 quad 3.4ghz on Abit IP35 Pro (off limits).

Thanks.

---

### Post by Paqman on 2008-05-27
It's a hardware thing. I'm certainly not a kernel hacker, but my understanding is that it changes the way the kernel communicates with the various hardware devices in your machine.

To set it permanently you need to edit the file /boot/grub/menu.lst Scroll right down to the bottom and you'll see the various Grub boot options, just add irqpoll to the end of the line that has the kernel location and ends with "quiet".

As for a fix, that will come from the kernel teams. Go to Launchpad and see if the bug is logged for your hardware. You can subscribe to bugs and get updates sent about progress on them.

---

