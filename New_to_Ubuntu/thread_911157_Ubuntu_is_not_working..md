---
title: "Ubuntu is not working."
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Urvish on 2008-09-05
I have two operating system in my computer that is ubuntu 8.04 and windows XP.I have installed XP in C drive and ubuntu in E drive.But because of some problem in windows XP I have only reinstall it in C drive after completing installation Ubuntu is not working SO How can I use ubuntu without data loss in Ubuntu ???

---

### Post by sharks on 2008-09-05
do u mean that u have lost grub? did u install windows after installing ubuntu?

Recovering Ubuntu after installing Windows
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Flimm on 2008-09-05
Did you use Wubi?
Do you recognise any of [these screenshots]("http://wubi-installer.org/screenshots.php")?

---

### Post by Urvish on 2008-09-06
No Bro,
I have already Ubuntu & XP....
I have formated the C: drive where XP is located....
And Ubuntu is in drive E: Then I instaled Xp in C: drive.then I restarted my Pc when normal booting I have asked that in which OS i have to enter LIKE

Ubuntu 8.04
other os
Xp

Above list is always coming but now automatically starts only XP it is not asking for Ubuntu

Please help me

---

### Post by Zalbor on 2008-09-06
Follow the instructions in the link above.

---

### Post by Bölvaður on 2008-09-06
> **Zalbor said:**
> Follow the instructions in the link above.

[Recovering Ubuntu After Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by 0004tom on 2008-09-06
There's a tool called EasyBCD that can boot ubuntu from Windows Boot Manger. If you un happy about reinstalling grub. A quick google search, will point you in the right direction.

---

### Post by Urvish on 2008-09-07
But EasyBCD tool is only working in latest version of vista I have XP sevice pack 2

---

### Post by sharks on 2008-09-07
use [supergrubdisk]("www.supergrubdisk.org/")

---

### Post by Paqman on 2008-09-07
Your problem is a common one. Basically Windows overwrites the Grub bootloader (the list of which OS to boot) when it is installed.

If you follow the link to the instructions for reinstalling Grub given above, you should have no problem getting Grub back. It's fairly simple.

---

