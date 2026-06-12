---
title: "problem in ubuntu during formating"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by coolguysraju on 2012-01-04
I have installed ubuntu 10.10 with dual booting in different drive by partion it but when the virus has attacked to windows 7 , i formatted the the C: drive and i reinstall the window 7 but my ubuntu 10.10 is disappeared i.e not showing the dual booting system when i open the computer.I have only format C:drive not other drive,recently i have installed the ubuntu 11.10 with dual booting i want to know that if th same problem repeat or not,plz anyone help from this problem.

---

### Post by oldos2er on 2012-01-04
When you installed Windows 7 it overwrote the MBR with its own bootloader, so you need to restore grub. See [https://help.ubuntu.com/community/WindowsDualBoot#Recovering_GRUB_after_reinstalling_Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering_GRUB_after_reinstalling_Windows)

---

### Post by audiomick on 2012-01-04
> **coolguysraju said:**
>  i want to know that if th same problem repeat or not

Yes it will repeat. When you install any version of windows, it will always overwrite the MBR (master boot record). There is nothing you can do to stop this. You always have to re-install grub, as explained in the link that oldos2er posted. I haven't had to do this, but I gather it is not that difficult and no great problem. All you need is a live CD, and I think one should always have one handy anyway, as they are useful for a lot of things.

---

### Post by coolguysraju on 2012-01-05
Ok i got the reason of that, now anyone give me the stepwise solution to me.

---

### Post by audiomick on 2012-01-17
To re-install GRUB2 ?

The link that oldOS2er posted would have led you to this

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

which explains quite well how to replace GRUB2.

---

