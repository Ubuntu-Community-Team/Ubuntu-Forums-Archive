---
title: "Linux Applications and Bootloaders"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by clementchiew on 2013-08-12
So I'm just new to the Linux community and as expected, I am confused already with all the distros and desktops versions. But never mind. One of my concerns is rather, are Linux applications designed for a specific OS or for Linux OS'es in general? I mean, can I install Steam in a different Linux OS from Ubuntu (like RHEL, CentOS, PuppyOS etc..) or have VLC in them? And also, I learnt that different Linux OS'es use different Bootloaders (Grub 2 for my Ubuntu currently, sth sth etc...) and I am worried that installing maybe Mint or other OS'es side-by-side will break Grub 2. Please guide me. :D

---

### Post by nerdtron on 2013-08-12
Not sure about Steam though. Maybe their website has a list of officially supported linux ditributions.
As far as other applications, if it is in the software repository of your chosen distribution, it can be installed. VLC can surely be installed in most distributions.
I haven't had problems in GRUB when installing Mint, or other debian based derivatives in the same computer. The only problem you should look for is which OS controls GRUB. If you install Ubuntu, then install Mint, (if you don't change the default) Mint will overwrite the GRUB of Ubuntu and install its GRUB. This will mean that if you want to change settings regarding GRUB, you should change the settings in Mint and not in Ubuntu.

---

