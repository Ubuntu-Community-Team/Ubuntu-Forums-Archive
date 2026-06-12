---
title: "Battery problem"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by cornish12 on 2008-11-18
I am having problems with my battery indicator on my laptop. I have put a battery icon on the panel but it says that "battery charge time is currently unknown". Anyway to fix this? I am using 8.10.

---

### Post by jpoRS on 2008-11-18
I had the same problem.  Is it a fresh install/upgrade?  I ask because I noticed the problem when I upgraded, and I think I have it sorted.

The battery notification program needs to monitor your battery for a little bit to learn what it can and cannot do.  For that reason it will say that until you let the battery charge down once and charge back up again.

Hope this helps,
jim

---

### Post by phidia on 2008-11-18
What are your laptop's maker, specs and are you using any boot options to get Ubuntu to load up?
If acpi is off by using that boot option or you have it turned off in bios you won't have battery or power management functions.

See the wiki [here]("https://help.ubuntu.com/8.04/installation-guide/i386/pre-install-bios-setup.html") on power management too (that guide is for 8.04 but most of it should apply to 8.10)

---

### Post by cornish12 on 2008-11-24
Hi

My laptop is an unbranded, Intel(R) Pentium(R) M processor 1.60GHz, it was a fresh install of Ubuntu 8.10 as the sole op.

Could not find acpi option in bios. Otherwise not sure where to look.

---

### Post by jpoRS on 2008-11-24
Have you just let the battery go for a while?  I don't know if this is true, but I suspect that the charge time estimate is based off of previous performance, and thus you need to give the panel app some time to get familiar with the battery.

jim

---

