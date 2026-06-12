---
title: "Need help installing Ubuntu on a PC with Windows Vista"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Artess on 2008-05-16
Hello to everybody here.
I'm completely new to Ubuntu, as well as to Linux in general. I need some help with installing it as a second OS (Windows Vista as first) with dual-booting (on a separate HDD). The first time I tried to, Ubuntu just wouldn't appear as a possibility in OS choose screen and didn't show any other signs of its existence. The second time I managed to completely destroy the Windows boot sector, so I had to re-install it (and then Ubuntu disappeared mystically again).
Would be very thankful, if someone could give a manual on how to do this. The one in official documentation didn't help.
Thanks in advance.

---

### Post by rbc on 2008-05-16
I have tried this method so i cannot vouch for it, but have a read:
[http://www.pronetworks.org/forum/about78184.html](http://www.pronetworks.org/forum/about78184.html)

---

### Post by rbc on 2008-05-16
That should have said, "I have NOT tried this method..........

---

### Post by bodhi.zazen on 2008-05-16
You need to either :

1. Install GRUB into the MBR of the first hard drive. This will boot either Vista or Ubuntu. This is, IMO, the best and easiest method.

2. Install GRUB into the MBR of the second hard drive. You will then need to select (from your BIOS) which drive to boot (as master). If your bios does not support this, you would need to physically move the hard drives between master ans slave depending on OS. This is not bad if supported by your bios.

3. Configure Windows to Boot Linux (Ubuntu). I do not know how to do this, google search or contact Microsoft ?

---

### Post by arochester on 2008-05-16
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by Artess on 2008-05-16
> **bodhi.zazen said:**
> Install GRUB into the MBR of the first hard drive. This will boot either Vista or Ubuntu. This is, IMO, the best and easiest method.
And could you please tell me how exactly to do it, cause I'm rather unfamiliar with GRUB.

---

### Post by bodhi.zazen on 2008-05-16
Install Ubuntu and go with the defaults.

---

### Post by sailor2001 on 2008-05-16
a great help would be to download and burn a 'super grub' disk and keep it handy...supergrubdisk.org

---

