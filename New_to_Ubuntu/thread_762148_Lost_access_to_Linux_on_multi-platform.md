---
title: "Lost access to Linux on multi-platform"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by barrykgerdes on 2008-04-21
Hi

I have suddenly lost my access to my Linux installation. The multiboot menu no longer appears. I have boot magic installed which was never a problem before. If bootmagic was enabled all I got were the normal DOS/Windows starts. If I disabled bootmagic I always started with the Linux multiboot menu. This is no longer the case with boot magic disabled the computer boots to the windows boot.ini.

How do I get back to my original state.

Barry

---

### Post by Ryutatsu on 2008-04-21
Have you considered installing grub onto whichever disk boots first? Once it's installed it's relatively easy to customize and there are plenty of guides here and on the net on how to do that with pretty much any setup.

---

### Post by barrykgerdes on 2008-04-21
Thanks I will look for those guides.

---

### Post by blonde-wanna-be on 2008-06-07
i have the same issue except it refuses to forget the cd so demands a cd if i boot up always the unbuntu 8.04

why?
and it wont allow me to partitition
why?
so i lost accsess to xp on my munti platform just want linux

---

### Post by rraj.be on 2008-06-07
Try reinstalling GRUB.

To reinstall grub

Boot into live cd.

Open terminal and type

```
sudo grub

find /boot/grub/stage1
```

if it returned like hd(x,y)

```
type root (x,y)

setup (x)

quit

sudo reboot
```

this should work if your Grub is missing.

---

### Post by rraj.be on 2008-06-07
> **blonde-wanna-be said:**
> i have the same issue except it refuses to forget the cd so demands a cd if i boot up always the unbuntu 8.04
linux

could you be a bit clear when its asking.

and what its displaying exactly.

---

