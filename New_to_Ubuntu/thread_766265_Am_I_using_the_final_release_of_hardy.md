---
title: "Am I using the final release of hardy?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by ymx on 2008-04-25
This question might have been asked for hundreds of times, but I'm wondering if I'm using the final release of hardy instead of beta. I thought there might be an update last day for the final release of hardy but there wasn't, and the boot loader of grub still says that i'm using a "development branch". Should I wait for an update or just change the bootloader?

---

### Post by Saya on 2008-04-25
You are using the final version. The "development branch" thing might be because that kernel version was released during the development period.

---

### Post by keithcleaver on 2008-04-25
If you've been updating on time through the alpha-beta-rc process, you're now running the final version of 8.04

---

### Post by philinux on 2008-04-25
If you use

sudo update-grub

it will pick up the latest kernel description.

---

### Post by ymx on 2008-04-25
Yep, that worked. Thanks guys!

---

