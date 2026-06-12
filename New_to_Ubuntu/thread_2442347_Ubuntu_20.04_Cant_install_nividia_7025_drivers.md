---
title: "Ubuntu 20.04 Cant install nividia 7025 drivers"
date: 2020-05-02
forum: New to Ubuntu
---

### Post by eltiti on 2020-05-02
Hello! Im new to linux!
I install ubuntu 20.04 but the screen is full with artifacts. Im trying to install these drivers [https://www.geforce.com/drivers/results/114714](https://www.geforce.com/drivers/results/114714) but i get the error 
Unable to find the system utility "ld" - please make sure you have the package binutils installed. If you do have binutils installed then check ld is in your PATH

I dont know what to do!

Thanks!!

---

### Post by CelticWarrior on 2020-05-02
Welcome.

Unfortunately there are bad news. 304 driver is no longer supported. The last Ubuntu release where it was supported is 16.04 with the original kernel version, i.e., no higher than 16.04.1. The included kernel version is supported until the end of that release (April 2021). After that you need to find something else not in Ubuntu family (or use the default open-source nouveau drive that may or may not work properly).

---

### Post by CatKiller on 2020-05-02
Also if you were using a card that was supported by current drivers you wouldn't install them by downloading and running some random file, you'd just use the package manager.

---

### Post by eltiti on 2020-05-04
> **CelticWarrior said:**
> Welcome.

Unfortunately there are bad news. 304 driver is no longer supported. The last Ubuntu release where it was supported is 16.04 with the original kernel version, i.e., no higher than 16.04.1. The included kernel version is supported until the end of that release (April 2021). After that you need to find something else not in Ubuntu family (or use the default open-source nouveau drive that may or may not work properly).

Thanks for the reply!
I have an hd 6450 radeon video card, that would work???

---

### Post by CelticWarrior on 2020-05-04
> **eltiti said:**
> Thanks for the reply!
I have an hd 6450 radeon video card, that would work???

It's supported by the open-source driver 'radeon'. Already included, no installation required.
The aforementioned driver was developed with AMD so it's a different situation than with 'nouveau' for Nvidia cards.

Whether or not it works satisfactory in this day and age with legacy hardware your experience will tell.

---

### Post by eltiti on 2020-05-04
Of course! I live in argentina, and for the moment for my mother is more than enought for web browsing. Thanks for the reply!

---

### Post by mörgæs on 2020-05-08
If you have an HD 6450 you are good to go for many years to come using the default radeon drivers. Just install something lighter than Ubuntu which is about as heavy as one can go within the Buntu world. 

Don't try to add anything Nvidia related to the system.

---

