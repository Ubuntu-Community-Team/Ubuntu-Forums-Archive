---
title: "Proprietary drivers vs OS"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by kikapu on 2008-05-05
Hi,

i have an nVidia Quandro 140M card on a Thinkpad T61.
So, i have the problems that all seems to have with hibernate and suspend.
What it will be the difference if i disable the usage of these drivers and tell Ubuntu (i am using 8.04) to use it's default drivers ?

Will i loose desktop effects, 2D/3D performance or whatever ?


Thanks for any help (this hibernate/suspend problem is indeed driving me nuts...)

---

### Post by Paqman on 2008-05-05
Hibernate and suspend are controlled by the kernel, they don't really have "drivers" as such.

---

### Post by kikapu on 2008-05-05
> **Paqman said:**
> Hibernate and suspend are controlled by the kernel, they don't really have "drivers" as such.

Ok, but most people that have problems with this, are using nVidia drivers and i think, somehow, has something to do with it.

---

### Post by kpkeerthi on 2008-05-05
> **kikapu said:**
> Hi,

i have an nVidia Quandro 140M card on a Thinkpad T61.
So, i have the problems that all seems to have with hibernate and suspend.
What it will be the difference if i disable the usage of these drivers and tell Ubuntu (i am using 8.04) to use it's default drivers ?

Will i loose desktop effects, 2D/3D performance or whatever ?


Thanks for any help (this hibernate/suspend problem is indeed driving me nuts...)
Yes. The nvidia binary drivers have been causing hibernate/resume problems for me too in ubuntu. You can switch back to open source "nv" or "vesa" drivers. But as you said, you will be loosing 3D capabilities. Applications like compiz(desktop effects), AWN dock, 3D games and in general, any program that requires OpenGL support will cease to function.

---

### Post by Paqman on 2008-05-05
> **kikapu said:**
> Ok, but most people that have problems with this, are using nVidia drivers and i think, somehow, has something to do with it.

Ah, I see. Bummer.

I guess you have to decide which you want more: suspend or 3D graphics?

---

### Post by kikapu on 2008-05-05
> **kpkeerthi said:**
> Yes. The nvidia binary drivers have been causing hibernate/resume problems for me too in ubuntu. You can switch back to open source "nv" or "vesa" drivers. But as you said, you will be loosing 3D capabilities. Applications like compiz(desktop effects), AWN dock, 3D games and in general, any program that requires OpenGL support will cease to function.

I see...So, it's a no go for us. I will just keep using them (nVidia drivers) and forget about hibernate/suspend...:(

---

