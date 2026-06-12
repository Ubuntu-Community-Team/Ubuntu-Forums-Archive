---
title: "Asus UX32VD Unbuntu"
date: 2015-03-08
forum: New to Ubuntu
---

### Post by francisco17 on 2015-03-08
Hi all,

I am new to the unbuntu environment and really like how it has been working so far but def continue to have problems. I am running unbuntu 14.04 dual boot on my asus ux32vd. I know that it has a discrete graphics card aside from the onboard one and it switches between them. How do i know if this is working the same in unbuntu? Is there anything else i need to install?

---

### Post by stalkingwolf on 2015-03-08
unbuntu?

---

### Post by newb85 on 2015-03-08
Yeah... it's Ubuntu.

If you open a terminal and run
```
sudo lshw -C display
```
what's the output?

*It'll ask for your password, and as you type it you won't get any visual feedback.  That's normal.*

---

### Post by francisco17 on 2015-03-08
Very true

---

### Post by francisco17 on 2015-03-08
*-display               
       description: 3D controller
       product: GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M]
       vendor: NVIDIA Corporation

 *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation

---

