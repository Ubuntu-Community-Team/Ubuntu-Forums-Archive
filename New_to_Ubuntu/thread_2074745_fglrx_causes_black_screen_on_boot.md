---
title: "fglrx causes black screen on boot"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by blazemore on 2012-10-22
I'm using Kubuntu 12.10 at the moment but this problem is not specific to KDE.

After installing the AMD driver from any source (upstream or the Ubuntu tool), rebooting causes just a black screen.

I know the system is booting up fine because I hear the startup sound so I know KDE is working.

Adding "nomodeset" to the kernel line in Grub dumps me to a login console, and I can't run startx because "no screens detected".

Can someone explain a) How can I get this to work? and b) How can Canonical justify shipping a release in this state?

---

### Post by NikTh on 2012-10-22
> **blazemore said:**
> I'm using Kubuntu 12.10 at the moment but this problem is not specific to KDE.

After installing the AMD driver from any source (upstream or the Ubuntu tool), rebooting causes just a black screen.

I know the system is booting up fine because I hear the startup sound so I know KDE is working.

Adding "nomodeset" to the kernel line in Grub dumps me to a login console, and I can't run startx because "no screens detected".

> **blazemore said:**
> Can someone explain a) How can I get this to work?

Hi ,


[LIST]
[*] If your graphics card is HD2000 to 4000 series then , here is an open bug: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040)
[*] Another bug (not specific to graphics card series) is here: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/993427](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/993427)
[*] Another bug , related to Desktop Environment (not KDE) is here: [https://bugs.launchpad.net/fglrx/+bug/1068661](https://bugs.launchpad.net/fglrx/+bug/1068661)
[/LIST]
   
Search for Bugs before you install anything in a new (very new) release like Ubuntu 12.10. 

I suggest to click the "Yes affects me too" button in Launchpad , in any bug report you think affects you. 

Try to remove the fglrx driver from your system and  use the radeon (open source - pre-installed) instead.
> **blazemore said:**
>  and b) How can Canonical justify shipping a release in this state?
This question probably is for another Thread. [Ubuntu Testimonials & Experiences]("http://ubuntuforums.org/forumdisplay.php?f=103") ? Maybe.

Thanks

---

