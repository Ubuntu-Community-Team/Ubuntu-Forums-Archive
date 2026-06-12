---
title: "Catching Kernel Options in Bash"
date: 2008-07-25
forum: Programming Talk
---

### Post by SuperMike on 2008-07-25
I have a need to catch a kernel option after the OS is loaded but before X is not yet started. I want to have a Bash script detect this option and use the appropriate xorg.conf file. That way, when I boot up, my Grub boot menu can display a menu that basically says, "Boot in Xinerama mode with attached monitor" and the other option says, "Boot as standalone laptop".

Is there a way I can edit my grub menu and then catch that setting on boot?

---

### Post by Yannick Le Saint kyncani on 2008-07-25
Hi SuperMike, /proc/cmdline contains the arguments passed to the kernel.

Cheers.

---

### Post by SuperMike on 2008-07-25
Thanks. That did the trick. I passed "xinerama" in my grub at the end of the kernel parameters and was able to detect it not only with dmesg and a grep, but through a grep on /proc/cmdline output. I then have an /etc/init.d boot script that does an if/then on the grep -b output of that, looking for my magic keyword, and it copies out the appropriate xorg.conf file. Mission accomplished.

---

