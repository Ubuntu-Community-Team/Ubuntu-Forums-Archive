---
title: "[SOLVED] Stop kernel module build?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Locke_99GS on 2008-09-30
Old PC, esoteric sound.

With no audio, and the point of that box to serve audio to a HTS, I found the correct alsa drivers online to build. Well, I discovered the issue in another terminal while that was adding the kernel module, so I aborted it. Everything worked fine.

Now, after I reboot, I get the message "Building modules for the 2.6.24-21-generic kernel, please wait..." and it just sits there, apparently doing nothing - there is no drive activity, and I've let it sit for hours. This happens on every boot, I cannot abort it, and it won't continue the boot. I am able to open tty1 and log-in.

How can I prevent this from trying to build this module on boot?

---

### Post by bwallum on 2008-09-30
Can you use an earlier kernel from the GRUB menu? If so use System>Administration>Synaptic Package Manager to remove 2.6.24-21 (it will then take it out of the GRUB menu as well),then reboot and upgrade through System>Administration>Update Manager

---

### Post by Locke_99GS on 2008-09-30
:) Oddly enough, thats exactly what I ended up doing - though I'm sure there had to have been something somewhere telling it to do that on boot, something that I could have edited out. Regardless, that worked. 

Thanks.

---

