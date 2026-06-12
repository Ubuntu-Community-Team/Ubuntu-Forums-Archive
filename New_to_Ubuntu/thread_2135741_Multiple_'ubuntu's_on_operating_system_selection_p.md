---
title: "Multiple 'ubuntu's on operating system selection page"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by scimas on 2013-04-15
I use windows8. I used windows installer to install ubuntu 12.10. Then for some reasons I had to reset my computer (using the 'complete reset' feature in windows8). I forgot to uninstall ubuntu before resetting. After resetting, the computer still shows me ubuntu in the operating system selection panel. But it wont boot because the boot file is missing (since the hard drive was completely formatted during the reset). Now I have again installed ubuntu and now it shows windows8 and two ubuntus on the os selection page.
How do I get rid of the disfunct ubuntu selection?

Thanks for any help.

---

### Post by grahammechanical on 2013-04-15
I do not know the answer, but have you tried using the Windows utility called Add/Remove programs? I assume that there is such a program. The last Windows I used was Windows 98. You may remove the wrong Ubuntu listed. So, it might be better to remove both and then reinstall. I think that Windows still has information in it program registry and that is what is causing it to list a non existent program. Remember, As far as Windows is concerned Ubuntu is just another program.

By the way, did you see this?

> **Have a new PC with the Windows 8 logo or using UEFI firmware?**

[COLOR=#333333][FONT=Ubuntu]Please use a [/FONT][/COLOR][64-bit flavour]("http://www.ubuntu.com/download/desktop")[COLOR=#333333][FONT=Ubuntu] of Ubuntu, installed directly to its own partition _rather than using_ the Windows installer.[/FONT][/COLOR]

> [h=4][SIZE=2]Windows installer is not compatible with Windows 8 or UEFI firmware.[/SIZE][/h]
It is not recommended to use the 'Windows installer' with Windows 8.

[http://www.ubuntu.com/download/desktop/windows-installer?distro=wubi&release=&bits=](http://www.ubuntu.com/download/desktop/windows-installer?distro=wubi&release=&bits=)

[http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

Regards.

---

### Post by sp-1070 on 2013-04-15
You should remove both the ubuntu&#347; from your system and use a ubuntu disc/usb and install alongside to windows 8 and youll be done with it

---

### Post by oldfred on 2013-04-15
Was this a Windows 8 you installed yourself and had wubi or EasyBCD controling boot? Then you have to use bcdEdit to remove extra entries.

But if a UEFI system with Windows 8 pre-installed, UEFI remembers old settings and you have to boot directly into UEFI and delete entires from UEFI menu.

---

### Post by bcbc on 2013-04-15
[http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu](http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu)

---

### Post by scimas on 2013-04-16
> **bcbc said:**
> [http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu](http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu)
Thanks!! It worked.

---

