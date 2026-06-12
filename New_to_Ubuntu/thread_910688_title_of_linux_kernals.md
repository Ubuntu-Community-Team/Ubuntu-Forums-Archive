---
title: "title of linux kernals"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-09-04
to simplify my grub list i was wondering if i could change the name of my kernals on the list 

ex. from: Ubuntu 8.04.1, kernel 2.6.24-19-rt
      to: Ubuntu Studio 8.04.1

---

### Post by mlentink on 2008-09-04
For the first line, which is the title, you could. But somehow, there's something that tells me to advise your to simply leave thisngs as they are. You might want to change something in the future, and know what....

---

### Post by PatrickMoore on 2008-09-04
> **mlentink said:**
> For the first line, which is the title, you could. But somehow, there's something that tells me to advise your to simply leave thisngs as they are. You might want to change something in the future, and know what....

yeah my concern is running into a snafu

---

### Post by philinux on 2008-09-04
> **PatrickMoore said:**
> to simplify my grub list i was wondering if i could change the name of my kernals on the list 

ex. from: Ubuntu 8.04.1, kernel 2.6.24-19-rt
      to: Ubuntu Studio 8.04.1


No problem it's just a title. i triple boot and title them how i like.

---

### Post by mrsteveman1 on 2008-09-04
I'm guessing that the update-grub script is what sets those titles, perhaps there is a standard config for it in /etc/default or somewhere similar. Or perhaps you can just edit the script to tell it not to add kernel numbers to the title.

Anyway i suppose this is all aesthetic but I'm sure you could hack it.

EDIT: I read through the script quickly but its ~1400 lines and I'm tired :D

/usr/sbin/update-grub line 324 might be relevant, and i believe lines 693 through 701 are the function that puts kernel version in the title.

---

