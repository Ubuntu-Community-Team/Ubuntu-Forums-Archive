---
title: "Prioritizing Ubuntu Over windows in a Dual Boot Environment"
date: 2009-05-26
forum: Philippine Team
---

### Post by randytan on 2009-05-26
Hi All!

Is there a way to prioritize Ubuntu over windows during start up in a dual boot environment?

Nakakainis kasi kapag hindi mo nabantayan sa pag power up ng unit at didiretso siya sa windows at kailangan mo namang i-restart yung unit para ma-boot yung Ubuntu.

Thanks. :)

---

### Post by guitar_man on 2009-05-26
diba sa grub naman ubuntu unang option....kapag  hindi ka pumili ng ibang os ubuntu iboot ng computer

---

### Post by donato roque on 2009-05-26
Hi
Kailangan mong i-edit ang GRUB.
So type:  ~$sudo gedit /boot/grub/menu.lst
Depende kung ilan ang os mo pre.  0 and default so ito
ang unang i-buboot ng grub then 1 and so on.

Good luck!

---

### Post by leipogs23 on 2009-05-26
I think he is talking about this one..

[http://brainstorm.ubuntu.com/idea/15291/](http://brainstorm.ubuntu.com/idea/15291/)

---

### Post by jsgotangco on 2009-05-26
Wubi works differently compared to dual boot, so he needs to edit his GRUB list as stated earlier.

---

### Post by leipogs23 on 2009-05-26
> **jsgotangco said:**
> Wubi works differently compared to dual boot, so he needs to edit his GRUB list as stated earlier.

A ok... I just thought na pag dual boot e di sya didiretso sa Wimdows. Kala ko sa wibi lang yun. Hamunaxa!!!hehehe

---

### Post by dodimar on 2009-05-26
> **jsgotangco said:**
> Wubi works differently compared to dual boot, so he needs to edit his GRUB list as stated earlier.

Wubi... hehehe.. just tried that earlier... sumakit ulo ko.. 

anyway... yup.. you have to edit your grub,,, if need assistance.. post mo yung laman ng /boot/grub/menu.lst mo...

---

### Post by wersdaluv on 2009-05-26
sudo gedit /boot/grub/menu.lst 

(assuming that you have gedit)

There's a list of operating systems somewhere in the end. Just put your Ubuntu install on top of the Windows entry.

---

### Post by jsgotangco on 2009-05-27
> **leipogs23 said:**
> A ok... I just thought na pag dual boot e di sya didiretso sa Wimdows. Kala ko sa wibi lang yun. Hamunaxa!!!hehehe

When you dual boot, a list of operating systems is shown and there is a default system to boot in a certain amount of time. This is true not just with GRUB but other boot loaders as well (even multiple versions of Windows can be dual or multi-boot from a single machine).

Of course when there is only a single operating system, there is no need to show the OS list with the exception if you have multiple kernels.

---

### Post by leipogs23 on 2009-05-27
> **jsgotangco said:**
> When you dual boot, a list of operating systems is shown and there is a default system to boot in a certain amount of time. This is true not just with GRUB but other boot loaders as well (even multiple versions of Windows can be dual or multi-boot from a single machine).

Of course when there is only a single operating system, there is no need to show the OS list with the exception if you have multiple kernels.

Yaah yaah I got it na! ang pumasok na picture pala sa utak ko e ung press esc to show boot sequence na di tutuloy gat di ka pumipili. Sowi!!!!

---

