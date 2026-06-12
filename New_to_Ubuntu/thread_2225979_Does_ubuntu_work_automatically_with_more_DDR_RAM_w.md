---
title: "Does ubuntu work automatically with more DDR RAM when RAM added?"
date: 2014-05-24
forum: New to Ubuntu
---

### Post by gam01hr on 2014-05-24
I have 10 years old PC. It used an old 1GB DDR RAM. I added another 1GB DDR same type which is detected well (bios, ubuntu lshw -html) :p. Please, just acknowledge that the o.s. ubuntu works automatically with more DDR RAM and I don't need reinstall whole ubuntu o.s. Thank you.

---

### Post by deadflowr on 2014-05-24
You can add or subtract RAM without any need to reinstall.

---

### Post by 3rdalbum on 2014-05-24
Ubuntu doesn't remember how much RAM you had at install. It only knows how much RAM you have right now, which is 2GiB, and it will use as much of that as it needs.

---

### Post by Impavidus on 2014-05-25
If the bios recognises the new memory, Ubuntu will use it.

There is one caveat, not applicable to you, but it may be to others reading this thread. When you increase the memory over 3GiB you may need to switch to a 64 bit system, which does require a new install. 32 bit systems can use more than 3GiB using PAE, but with limitations. Xubuntu 12.04 32 bit is the last supported version of an Ubuntu flavour that has a non-pae kernel and doesn't support more than 3GiB at all, unless you install the pae kernel from the repositories.

---

