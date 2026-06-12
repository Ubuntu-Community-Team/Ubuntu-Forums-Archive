---
title: "asus 1g graphics card driver for 13.04"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by okkie on 2013-08-09
I got an ASUS rock solid heart touching graphics card with fan cooled processor for a present which I want to use but my 13.04 Ubuntu system doesnt recognise it. Do I need drivers or something else? any help please

---

### Post by Mark Phelps on 2013-08-09
We need to know the actual  make and model of the video chipset on the card.  So, open a terminal, enter "lspci" and look for the line containing "VGA".  Post that information back here.  If your system didn't "recognize" the card, you would have no video at all.

---

### Post by okkie on 2013-08-09
Thanks Mark,
once the card is installed and the screen connected I have no video at all. Should I not disable the onboard graphics first and if yes, how do I go about it? here is the outcome of lspci as is 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
Markings on new card: EN960DGT/HTWI/1G/A AND 08G1 7019470*

---

### Post by okkie on 2013-08-20
can anybody else please assist. Mark must be away or something.

---

### Post by SweetAurora on 2013-08-20
According too Asus, the card is based on the Radeon HD3870. ATI has dropped support for that card starting with Ubuntu 12.04.2. So to use the card to it's full glory, you will have to install Ubuntu 12.04.1. Now granted, it works as it does now, but it will have terrible performance and subject to serious overheating. You can solve the heating issue with Ubuntu 13.10 (The 3.11 kernel has new Radeon power management support), but will still perform badly with 3d games. 2d on the other hand it accels at.

---

### Post by Mark Phelps on 2013-08-20
> **okkie said:**
> can anybody else please assist. Mark must be away or something.

Sorry, been busy elsewhere -- but SweetAurora is right -- AMD dropped restricted driver support for that card last summer.  All that is available that will work with 13.04 is the default drivers.

I would recommend AGAINST installing 13.10 at this time.  It's a pre-release version, and as such, is buggy and subject to crashes.

---

### Post by okkie on 2013-08-22
Thanks for the information.Just to make the effort worth the while for others as well,If one now runs 13.04,which graphics card or cards are recommended when you go shopping as in the RSA nobody in any of our Microsoft orientated shops will even know what you ars talking about.
Thanks

---

### Post by QIII on 2013-08-22
Hello!

If one wants an ATI proprietary driver to support 12.04.2 and beyond, one must use an HD 5000 or later GPU.

Be aware that some models marketed as HD 5000M series GPUs are actually overclocked HD 4000 series GPUs and will not work.

---

