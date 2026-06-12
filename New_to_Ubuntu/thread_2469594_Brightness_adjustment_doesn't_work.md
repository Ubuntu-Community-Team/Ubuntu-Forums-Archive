---
title: "Brightness adjustment doesn't work"
date: 2021-12-03
forum: New to Ubuntu
---

### Post by jbohol on 2021-12-03
Hello Ubuntu masters,
Greetings!

I'm having trouble with my ubuntu 20.04 running on dell xps 13 9310.  The brightness adjustment seem to be not working.  I already modified the grub file with the following line but still not working.
I'd like to check with you guys if you already encountered this case.  If so, can you share some info on how to get rid with this?   Thanks in advance!

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""
```

---

### Post by T6&amp;sfpER35% on 2021-12-03
stupid question...does the brightness control key on the keyboard also not work?

i'm thinking way back some time i had a laptop that for some reason the brightness control was set to off in BIOS...
have a look at BIOS settings for something to do with brightness

---

### Post by deadflowr on 2021-12-03
It's unclear if you reloaded/updated grub?

---

### Post by grahammechanical on 2021-12-03
In my ignorance I do not understand how adding a command to change the configuration of Grub would solve this problem. Surely the place to look is with the Linux configuration. After all, Linux is the operating system. But here is the issue. There are several command line utilities that can be installed to configure screen brightness but they only work on the X-Server and not on a Wayland compositor.

In Ubuntu 20.04 the place to make adjustments is System Settings>Power. On my desktop machine I do not get a slider to make screen brightness adjustments. Things might be different for a laptop. It could also be that I need to make an adjustment in the machine's BIOS (it is an old machine and recently was put back to a default configuration and that could be the reason for no option to change screen brightness). So, I support the above given advice to look in the UEFI settings.

Regards

---

### Post by jbohol on 2021-12-04
@3Nd -- Stupid question???  Well, I thank you for that :-)

The control on the keyboard doesn't work.  Of course, I checked on the BIOS.   Thanks for your response. :-) LOL

---

### Post by jbohol on 2021-12-04
deadflowr -- I just tried this one -> [https://ubuntuforums.org/showthread.php?t=2032376&p=12126780#post12126780](https://ubuntuforums.org/showthread.php?t=2032376&p=12126780#post12126780)

---

### Post by jbohol on 2021-12-04
grahammechanical -- Thanks for the response.  I really appreciate it.  I'm new to linux and trying to learn to solve things with my own machine.  I just switched from Windows to Linux and trying to learn new things here. :-)
Thanks again.

---

### Post by him610 on 2021-12-04
Display too bright?
```
$ xgamma -gamma 0.8

```
Display too dim?
```
$ xgamma -gamma 1.2

```
Reset to original value.
```
$ xgamma -gamma 1.0

```

---

