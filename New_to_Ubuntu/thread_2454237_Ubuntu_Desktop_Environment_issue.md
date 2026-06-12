---
title: "Ubuntu Desktop Environment issue"
date: 2020-11-25
forum: New to Ubuntu
---

### Post by imon57 on 2020-11-25
I had installed xfce DE in ubuntu 20.04.1 lts. While installing, I had selected lightdm as my default DE. After a week I have uninstalled xfce DE, Then I have not faced any problem. But after power off laptop, when I tried to open it again, it is not loading gnome DE which is available in system. The laptop is showing black screen and loads nothing.
Please help me to solve this issue&#128531;.
Thank you.

---

### Post by ActionParsnip on 2020-11-25
Do you have autologin enabled?

---

### Post by imon57 on 2020-11-26
@ActionParsnip
No, I have not enabled it.

---

### Post by grahammechanical on 2020-11-26
When you removed xfce DE did it remove LightDM? If it did then you need either to re-install LightDM or configure GDM3. This web site shows you how.

[https://itsfoss.com/switch-gdm-and-lightdm-in-ubuntu-14-04/](https://itsfoss.com/switch-gdm-and-lightdm-in-ubuntu-14-04/)

It is exactly the same in 20.04 as in 14.04. You need to get to a command line. At the Grub boot menu select Advance options for Ubuntu and then select a Linux kernel with recovery mode. At the recovery menu select Network to establish an internet connection. Then select Root shell prompt at the recovery menu.

When you finish configuring GDM3 type exit to get back to the recovery menu and select Resume. It should load to a login screen. From there Ubuntu should load with a low video resolution which will be fixed by a reboot.

Regards.

---

### Post by imon57 on 2020-11-27
> **grahammechanical said:**
> When you removed xfce DE did it remove LightDM? If it did then you need either to re-install LightDM or configure GDM3. This web site shows you how.

[https://itsfoss.com/switch-gdm-and-lightdm-in-ubuntu-14-04/](https://itsfoss.com/switch-gdm-and-lightdm-in-ubuntu-14-04/)

It is exactly the same in 20.04 as in 14.04. You need to get to a command line. At the Grub boot menu select Advance options for Ubuntu and then select a Linux kernel with recovery mode. At the recovery menu select Network to establish an internet connection. Then select Root shell prompt at the recovery menu.

When you finish configuring GDM3 type exit to get back to the recovery menu and select Resume. It should load to a login screen. From there Ubuntu should load with a low video resolution which will be fixed by a reboot.

Regards.

Can I use android's internet via usb tethering for establishing internet connection?

---

### Post by CelticWarrior on 2020-11-27
> **imon57 said:**
> Can I use android's internet via usb tethering for establishing internet connection?

Yes, you can.

---

### Post by imon57 on 2020-11-28
I have tried a lot of time to use live cd of Ubuntu. But I can not boot from usb, I am not getting any option to boot from usb. I have used the same usb for installing ubuntu. Why it is happening?

---

