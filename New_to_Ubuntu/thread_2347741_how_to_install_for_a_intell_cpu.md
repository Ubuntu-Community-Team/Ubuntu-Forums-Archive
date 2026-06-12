---
title: "how to install for a intell cpu"
date: 2016-12-28
forum: New to Ubuntu
---

### Post by spankstergangster on 2016-12-28
so i am currently using an amd cpu and my next pc will have an intel one. how do i install a version of ubuntu on my computer that works with an intel architecture not an amd one

---

### Post by howefield on 2016-12-28
There is no specific iso image for the Intel processor, don't worry about the amd64 nomenclature.

amd64 images will work well on both amd and Intel architecture.

---

### Post by Keith_Helms on 2016-12-28
AMD and Intel use the same architecture although various processors from each of them may have some additional instructions.  AMD was first to develop 64-bit instructions, so the 64-bit standard used by both AMD and Intel is referred to as amd64.

---

### Post by oldfred on 2016-12-28
If a new computer whether AMD or Intel, it will probably be UEFI.

And since UEFI includes compatiblity with the 35 year old BIOS/MBR configuration, the install process is a bit more complicated. You have to choose whether you want UEFI or BIOS. And Windows implemented UEFI Secure boot, so with UEFI you have two choices.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

And more info on UEFI in link in my signature below.

---

