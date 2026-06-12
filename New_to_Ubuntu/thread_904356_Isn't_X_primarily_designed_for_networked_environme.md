---
title: "Isn't X primarily designed for networked environment?"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by known on 2008-08-29
Is there any light weight version of X for Laptops?

---

### Post by forger on 2008-08-29
you mean like [xfce]("http://www.xfce.org/") or [enlightment]("http://www.enlightenment.org/") ?

---

### Post by Joeb454 on 2008-08-29
X is a standard interface.

If you want a lightweight desktop environment, you should look at XFCE or a *box DE :)

---

### Post by known on 2008-08-29
> **Joeb454 said:**
> X is a standard interface.

If you want a lightweight desktop environment, you should look at XFCE or a *box DE :)

Hi, I am looking for lightweight X tself (and not environment)

---

### Post by finer recliner on 2008-08-29
the only two choices really are xorg and xfree86. ubuntu uses xorg. there is no "light" version


X *could* be used such that the X server and X client are on two different machines, however it is still very common that both are hosted on the same machine. it does not cause a major performance drain to have both on the same computer.

---

### Post by Titan8990 on 2008-08-29
XFCE is my favorite light weight desktop. Another that is not bad is Flux. Both are available in *buntus.

> the only two choices really are xorg and xfree86. ubuntu uses xorg. there is no "light" version

Isn't "Vesa" another substitute for xorg?

---

### Post by kellemes on 2008-08-29
> **known said:**
> Hi, I am looking for lightweight X tself (and not environment)

You need to do it with xorg I'm afraid..
I wonder why you need a lighter alternative for it.

---

### Post by LowSky on 2008-08-29
> **Titan8990 said:**
> Isn't "Vesa" another substitute for xorg?

Vesa is a graphics card driver

Xorg is pretty lightwieght for any modern laptop, unless your trying to run it on something from the early 1990's, then maybe it wont work, but it still might. I believe even Damn Small Linux uses Xorg.

---

### Post by Titan8990 on 2008-08-29
Yeh, I had known it to be a failsafe driver but what confused me is an option in Puppy Linux. When Puppy Linux boots from it's live CD you get the option for vesa or xorg.

---

### Post by Oldsoldier2003 on 2008-08-29
> **Titan8990 said:**
> Yeh, I had known it to be a failsafe driver but what confused me is an option in Puppy Linux. When Puppy Linux boots from it's live CD you get the option for vesa or xorg.

IIRC that just means if you choose the vesa option it loads the vesa configuration. xorg reads your normal xorg configuration. It's a little confusing for newer folks and I can see how it would lead someone to thing vesa was more than a graphics driver.

---

### Post by kagashe on 2008-08-29
[Xvesa]("http://www.xfree.org/current/Xvesa.1.html") is a tiny X server. But it is insecure because you can run it only as root. I had installed Debian Lenny recently on my old PC which has 32 MB RAM only. When I added xorg the monitor was flickering so I installed Xvesa (there is a .deb package available) and I could run it by giving the mode option in the command.

Finally I could write xorg.conf to suite the monitor and use xorg. Practically there was no difference between running Xvesa and xorg. It is a myth that Xvesa needs less memory compared to xorg.

You can read about my experience in [this thread]("http://ubuntuforums.org/showthread.php?t=870061") on Ubuntuforums.

When you chose Xvesa in Puppy Linux it is same Xvesa and not xorg. On Puppy also there is not much difference in the memory usage.

kagashe

---

### Post by Oldsoldier2003 on 2008-08-29
Thanks for the clarification:)  I haven't run puupy in quite some time, so it didnt dawn on me that the OP was talking about xvesa , not vesa.

---

### Post by kellemes on 2008-08-29
Thanks *kagashe* for clearing stuff up. I was starting to get confused here.. :confused:

---

