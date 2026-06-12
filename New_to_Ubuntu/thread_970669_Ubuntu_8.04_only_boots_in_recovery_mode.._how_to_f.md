---
title: "Ubuntu 8.04 only boots in recovery mode.. how to fix?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by wildscribe on 2008-11-04
Hi! I have installed Ubuntu 8.04 a Dell Dimension 2350 desktop and for some reason, whenever it boots up, I get a blank screen. The only way that I can get it to work is by hitting the escape key during the boot process and then selecting Recovery Mode from the menu.

My questions are:

How can I find out why Ubuntu is booting to a blank screen? There must be something in the start up script that is stopping it. I would like to remove this item so it will start properly?

Is there a way that I can configure a boot script so that it always boots in recovery mode? Or is this advisable? I just want to get Ubuntu to work with this desktop, which is a 2.4 ghz Intel Celeron with 512 RAM.

All the best,

WiLd

---

### Post by mindwarp on 2008-11-04
First step would be, when it is at the 'blank screen', can you hit CTRL-ALT-F1 and if so do you see a prompt?

If so, Ubuntu didn't detect your graphics right and you will need to boot in graphics safe mode or find a xorg.conf file to use.

---

### Post by roger_1960 on 2008-11-04
Hi

When you boot into recovery mode, have you tried the option 'xfix'  This solved a similar problem for me.  ie then worked after normal reboot (1st option)

---

