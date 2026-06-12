---
title: "Ubuntu 12.04 hangs during shutdown/suspend"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by shobhit6993 on 2013-06-24
I am using Ubuntu 12.04 on my Dell Inspiron N5110 with Nvidia Geforce GT 525M graphics card. Recently, Ubuntu has started freezing during shutdown/suspend. During shutdown, the purple screen with Ubuntu logo and animated dots appears, but it freezes there only and I am forced to manually shut down the laptop using the power button. Can someone suggest a fix for this. I did try few fixes which I found on similar threads like modifing ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` to  ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
``` in /etc/default/grub but in vain.

---

### Post by dino99 on 2013-06-24
remove the "quiet splas" to get the verbose mode, which let you see the shutdown comments, and know where/when it hangs. Dont forget to run: sudo update-grub to activate the changes.
also you might post inside the Dell subforum to get better support.

---

### Post by GrouchyGaijin on 2013-06-24
Try using the nouveau video driver and not the Nvidia driver.

---

### Post by shobhit6993 on 2013-07-04
Sorry for such a late reply. I removed the "quiet splas" to get the verbose mode. The laptop freezes after Will Now Halt, Power Down. Above this, all the prompts are [OK].

---

### Post by rbasset on 2013-07-04
Im having the exact same problem with Ubuntu 13.04, im going to try installing nouveau video driver as suggested by Grouchy and see if that works.

---

### Post by mardybear on 2013-07-05
Howdy.

One of my systems has never liked shutting down Ubuntu from within the desktop environment. I previously tried to fix without success so now i simply logout and then shutdown from the login screen, works perfect every time. Sorry more of a work around than a fix....good luck.

mardybear

---

### Post by shobhit6993 on 2013-07-05
> **rbasset said:**
> Im having the exact same problem with Ubuntu 13.04, im going to try installing nouveau video driver as suggested by Grouchy and see if that works.

I am using the Bumblebee package which uses Nvidia drivers. Do tell me if replacing the Nvidia drivers with Nouveau drivers fixes the isuue, in which case, I would also unistall Bumblebee project and switch to Nouveau drivers.

---

### Post by shobhit6993 on 2013-07-05
> **mardybear said:**
> Howdy.

One of my systems has never liked shutting down Ubuntu from within the desktop environment. I previously tried to fix without success so now i simply logout and then shutdown from the login screen, works perfect every time. Sorry more of a work around than a fix....good luck.

mardybear

This work-around doesn't work for me.
Also, my laptop successfully restarts even from the desktop environment but shut down freezes from desktop environment as well as after logging out.

---

