---
title: "Lubuntu 18.10 stopped to load with kernel 4.18.0-14 ?! Ends up with black screen?"
date: 2019-02-04
forum: New to Ubuntu
---

### Post by daareek on 2019-02-04
Hi,

I'm new to Linux, installed lubuntu 18.10 64bit on lenovo SL500, worked fine, tried to install some apps, updated packages and all of the sudden ended up into booting into black screen. As I have played with grub just discovered that there are currently two versions of kernel installed. 4.18.0-14 and 4.18.0-10. Was a kernel update recently? Unfortunately 4.18.0-14 ends up with a black screen, Ctrl-Alt-T does not bring terminal, computer as I can see from the activity works, in recovery I can boot into root but not into gfx system. Is kernel updated through packages using Muon Package Updater or sudo get-apt, if yes how many previous versions are kept by default ?

PC booted into kernel 4.18.0-10 works fine, so just modified grub to boot into this config in meantime.

Is there any fix? Or new kernel upgrade? Where I can check what is the most actual for lubuntu?

---

### Post by oldrocker99 on 2019-02-05
I upgraded to kernel 4.19 and it runs like a champ, and does use les battery power, a long-term goal.

Here's where to get it:[http://ubuntuhandbook.org/index.php/2018/10/linux-kernel-4-19-released-install-ubuntu/](http://ubuntuhandbook.org/index.php/2018/10/linux-kernel-4-19-released-install-ubuntu/).

---

### Post by daareek on 2019-02-05
Hi,

thanks! 

Just upgraded to 4.19. 4.18.0-10 and 4.19 works fine, just 4.18.0-14 do not.

---

