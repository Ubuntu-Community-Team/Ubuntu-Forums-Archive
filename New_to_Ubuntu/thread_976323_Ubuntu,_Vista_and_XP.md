---
title: "Ubuntu, Vista and XP"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by frank75riz on 2008-11-09
On a Toshiba laptop> I have factory installed Vista, I shrunk it and installed Ubuntu, all was well.  However, I re-shrunk , and installed XP.  Now i only get Ubuntu and XP.  How do I get the loader to find Vista.

Failing that, and since I have no data on this laptop, should I re-install all three OS', and in what order.  

Thanks for a solution..

This oldman

---

### Post by dracayr on 2008-11-09
if you want to reinstall, always install the windows Operating systems before ubuntu. to fix without reinstalling, use ubuntu to reinstall grub

dracayr

---

### Post by bumanie on 2008-11-09
You should not have to reinstall anything, however just reinstalling grub will not work. You need to add xp's bootloader files to vista's bootloader files. Vista and xp recognize each other, but they won't boot each other unless their boot files are 'joined'. The best tool to do this with is easybcd bootloader available [here]("http://neosmart.net/dl.php?id=1"). But before using easybcd, you need to repair vista's bootloader with a repair cd - if you don't have one, you can get one from the neosmart site (where easybcd was downloaded). Once you have vista dual booting with xp, you can then reinstall grub from a live cd.

---

### Post by frank75riz on 2008-11-09
well, it is a bit convoluted, but I can now get into XP, Vista and Ubuntu.

Thank you so much. If it matters, I am 77 yrs old and just love this stuff. I have a 2 desktops, one on a desk and the other on my workbench in the garage (my wife made me do it), and this new Toshiba Laptop, and in truth I am having a ball screwing things u[ and finding solutions.  I have Debian on this computer, you know what I have on the laptop, and XP in the garage, which I will now, maybe, put on Mepis or some other OS....Thanks again.


Frank Rizzo

---

### Post by frank75riz on 2008-11-09
Laughing, now XP can't find the internet...life goes on

---

### Post by bumanie on 2008-11-09
> **frank75riz said:**
> Laughing, now XP can't find the internet...life goes on

Problem these days, assuming it is a new laptop, is that now xp is no longer officially supported, sometimes only drivers for vista are included - you may be able to go to toshiba site and see if you can find the correct drivers for xp, alternatively microsoft may have them if you know the motherboard name and number etc.

---

