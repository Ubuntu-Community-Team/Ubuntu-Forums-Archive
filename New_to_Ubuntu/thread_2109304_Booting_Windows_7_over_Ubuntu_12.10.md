---
title: "Booting Windows 7 over Ubuntu 12.10"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by Brianret on 2013-01-27
I have installed Win 7 on a separate partition to Ubuntu - it would have been easier to install Win 7 first but I didn't so I am stuck with it!
I am desperately trying to install the boot loader so that I have the option to boot either but win 7 is the only one I can use at the moment. I have searched the forums to find a simple way to do this but they are all way too complicated for me.
Is there an easy (for me) way to install the boot loader so I have a choice. I have tried Virtual Box but prefer the boot method.
Thanks for any help available.

---

### Post by Double.J on 2013-01-27
Hi there!

You can try installing easyBCD and adding ubuntu to it's boot order. I actually have [easyBCD]("http://neosmart.net/EasyBCD/") on all my pc's; I install each distro's boot loader to a partition, not the MBR of the hard drive; it makes it a lot simpler if you have to reinstall windows as their boot loader's are unaffected.

Fixing ubuntu's grub is fairy straight forward, but it is best done from the live cd. The easiest guide on how to do this is [here]("https://help.ubuntu.com/community/Boot-Repair").

---

### Post by Brianret on 2013-01-27
> **gnu/mirow said:**
> Hi there!

You can try installing easyBCD and adding ubuntu to it's boot order. I actually have [easyBCD]("http://neosmart.net/EasyBCD/") on all my pc's; I install each distro's boot loader to a partition, not the MBR of the hard drive; it makes it a lot simpler if you have to reinstall windows as their boot loader's are unaffected.

Fixing ubuntu's grub is fairy straight forward, but it is best done from the live cd. The easiest guide on how to do this is [here]("https://help.ubuntu.com/community/Boot-Repair").
Hi 
Brilliant! I used the Boot-Repair method and it took less than 5 minutes (most of that was typing).
Thanks a lot for your help.
Brian

---

