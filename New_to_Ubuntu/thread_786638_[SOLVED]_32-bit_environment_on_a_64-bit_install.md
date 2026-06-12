---
title: "[SOLVED] 32-bit environment on a 64-bit install?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by hufferd on 2008-05-08
I have one game I play that has a linux client BUT it needs to run on a 32-bit system???  is there a compatibility environment I can install

---

### Post by warbread on 2008-05-08
Modern 64 bit processors are backwards compatible.  I think you'll be able to run it just fine.

---

### Post by Golem XIV on 2008-05-08
There are two ways of doing this:

- Recompile the program so that it runs natively in 64 bits.  This is the best solution but sometimes it can be difficult, especially for a newbie.

- Install the 32 bit support libraries:
```
sudo apt-get install ia32-libs
```
install all dependencies and then force install the program
```
sudo dpkg -i --force-all *packagename*
```

Good luck!

---

### Post by hufferd on 2008-05-08
:popcorn:

Wow you guys are so nice :) Thanks for the info --- 

have some popcorn :)

---

