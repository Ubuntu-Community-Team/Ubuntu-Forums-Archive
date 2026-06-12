---
title: "Nvidia driver help"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by bb12489 on 2008-04-22
back with yet another problem........i finally got ubuntu installed on my laptop and i went and got the linux drivers from nvidia for my card, but when i try and install them it tells me i need a pre compiled kernel interface and another thing about libc development package

---

### Post by Biggy on 2008-04-22
Go to System > Administration > Restricted Drivers Manager  and enable Nvidia accelerated graphics driver

---

### Post by chewearn on 2008-04-22
> **bb12489 said:**
> back with yet another problem........i finally got ubuntu installed on my laptop and i went and got the linux drivers from nvidia for my card, but when i try and install them it tells me i need a pre compiled kernel interface and another thing about libc development package

How are you try to install the driver?  Normally, simplest way to install nvidia driver is via:
Panel Menu > System > Administration > Restricted Drivers Manager

Enable the corresponding checkbox.

EDIT:
lol. Too slow this time.  I will have my revenge...   :lol:

---

### Post by Nepherte on 2008-04-22
> **bb12489 said:**
> back with yet another problem........i finally got ubuntu installed on my laptop and i went and got the linux drivers from nvidia for my card, but when i try and install them it tells me i need a pre compiled kernel interface and another thing about libc development package
The easiest way is through the restricted drivers manager. When downloading the driver from the nvidia site, you will also need to install build-essential:
```
sudo apt-get install build-essential
```

---

