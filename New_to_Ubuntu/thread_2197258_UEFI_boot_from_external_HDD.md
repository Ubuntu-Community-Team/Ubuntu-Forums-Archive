---
title: "UEFI boot from external HDD"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by supersilverstudios77 on 2014-01-02
hello, im kinda new to ubuntu and I am wondering if it is safe to boot ubuntu from my external hard drive using a UEFI laptop. Last time i booted linux mint on my home laptop, it wiped everything, so i am wondering if i could boot ubuntu safely from my external hard disk, thanks in advance

---

### Post by sudodus on 2014-01-03
Welcome to the Ubuntu Forums :-)

Yes this is possible.

If you accept to change the BIOS/UEFI setting every time, you can boot in BIOS mode from the external drive (that is boot with the old standard partition table and 32-bit or 64-bit systems.

If you want to have it more convenient, you can make an UEFI installation or simply boot a persistent live system in UEFI mode. See these wiki pages

[https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)
[booting with UEFI]("https://help.ubuntu.com/community/UEFI")

and the following [post at the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=2108487&page=2&p=12656460#post12656460")

As long as you don't install anything into your internal drive, everything is fine. The safest way is to disconnect the internal drive while you do the installation to the external drive.

---

### Post by supersilverstudios77 on 2014-01-05
Thank you sudodus, you really helped me.

Now I just need to figure out why linux mint wiped my hard drive

---

