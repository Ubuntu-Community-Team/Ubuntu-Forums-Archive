---
title: "Ubuntu 16.04 alongside Windows 10 Pro hung on &quot;installation type&quot;"
date: 2018-06-15
forum: New to Ubuntu
---

### Post by masterdesai on 2018-06-15
Can't get past the "Installation Type" screen on the Ubuntu installer

I have verified that I have space allocated for the Ubuntu partition

[IMG]https://i.imgur.com/PBD5fdI.png[/IMG]

I have verified that Fast Boot is turned off

[IMG]https://i.imgur.com/dKGiPDw.png[/IMG]

I used Rufus with "ubuntu-16.04.4-desktop-amd64.iso" for installation via USB.

Everytime I run the installer I see

[IMG]https://i.imgur.com/L8sEJqy.jpg[/IMG]

What am I missing? What information could I provide you guys for more help?

---

### Post by yancek on 2018-06-15
You have windows 10 installed in UEFI mode so you need to boot and install Ubuntu UEFI also.  How to do all that is explained in detail at the Ubuntu documentation site below.  Your screen image shows you are not booting Ubuntu UEFI.  Also check in the BIOS for anything related to hibernation and do a full shutdown of iwndows.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

