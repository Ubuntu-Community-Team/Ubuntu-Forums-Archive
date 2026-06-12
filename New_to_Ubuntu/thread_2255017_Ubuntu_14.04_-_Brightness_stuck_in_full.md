---
title: "Ubuntu 14.04 - Brightness stuck in full"
date: 2014-12-01
forum: New to Ubuntu
---

### Post by mvishnu on 2014-12-01
Hi Guys,

I am not really that familiar with linux, and installed Ubuntu 14.04 to get some project work done for college. I had a ton of issues with dual booting with win8, so i got rid of it and have only Ubuntu 14.04 on my laptop now.

I have an HP Pavilion ex-026ax ([http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c03965151](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c03965151)) that has an A-10 processor with a dual Radeon 7660G-8670M setup.

After installing linux, i first saw that the brighntess settings dont work. Googling the issue said that it was common, but most of the solutions involved adding "acpi_0" or something in a grub configuration file, which did not work. I experimented with a few things and finally found out that installing the default drivers for the AMD (which I think was wrongly detected) card fixed the issue, while the proprietary ones still break the brighness control.

All was good until today an update broke the brightness setting again. Working with a latpop on full brightness is an ACME Instant-headache for migraine-prone me, and I'd be willing to junk my files and switch to windows to avoid this.

Any pointers would be greatly appreciated. So far I have tried every combination of AMD drivers (standard and proprietary ones from fglrx, fglrx updates as avbl under Settings - > software & updates -> additional drivers). I also manually installed the drivers for my card from the AMD Support website.

I also saw many threads that fix the problem by doing something for the 'intel' backlight control or whatever ([http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/))

I havent tried this because I dont use an intel machine.

Please help.
Thanks a lot!
V

PS: When i use the function keys that control brightness, i get the notification overlay that tells me that the brightness is changing, but the actual brightness level is stuck in full.

PPS: a temp solution / hack that gets the brightness stuck in 0 is perfectly acceptable, its the full that kills me.

---

### Post by nazo-night on 2014-12-02
[http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)
You may want to try this, It fixed my problem on an nvidia laptop as well
Although im on an intel driverset, so there may have to be tweaks to the code.

---

### Post by mvishnu on 2014-12-02
> **nazo-night said:**
> [http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)
You may want to try this, It fixed my problem on an nvidia laptop as well
Although im on an intel driverset, so there may have to be tweaks to the code.

Hey, thanks. But I had previously stumbled across that thread when googling. Problem is I dont see a "graphics cards" under "system settings-> Details". All I have is Overview, Default Application, Removable Media and Legal Notice.

Also, if you can advise on how to change the instructions there to apply for Radeon cards, that'd be great. I dont quite know where to start - also, I am afraid about whether i can screw up majorly.

Thanks,
V

---

### Post by mvishnu on 2014-12-02
> **nazo-night said:**
> [http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)
You may want to try this, It fixed my problem on an nvidia laptop as well
Although im on an intel driverset, so there may have to be tweaks to the code.

Hey, thanks. But I had previously stumbled across that thread when googling. Problem is I dont see a "graphics cards" under "system settings-> Details". All I have is Overview, Default Application, Removable Media and Legal Notice.

Also, if you can advise on how to change the instructions there to apply for Radeon cards, that'd be great. I dont quite know where to start - also, I am afraid about whether i can screw up majorly.

Thanks,
V

EDIT: I also get this error - "[drm:radeon_acpi_init] * ERROR * Cannot find backlight controller" when i start my computer.

---

