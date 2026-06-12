---
title: "used wubi installer to install ubuntu 11.10, but can't hibernate because of no swap?"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by linuxlooser on 2012-04-14
i am EXTREMELY NEW TO LINUX. so bare with.:)

i have done hundreds of google swap searches, and they all say try doing this and that, but nothing refers to if you used wubi? when you install with wubi, it has installation drive and installation size? no swap size or anything.. so how do you change swap size with wubi installer? this question must have been asked hundreds of times, sorry!

thanks in advance!:D

---

### Post by Frogs Hair on 2012-04-14
The only reason you may want to increase swap in a Wubi installation is to allow hibernation which a Wubi installation won't do. I don't think increasing swap size alone will allow hibernation you may have to dig a little deeper.  

The Wubi swap amount is 256 Mb and will show as 0 unless in use. Wubi installations have a 30 Gb max selected during installation.

[http://askubuntu.com/questions/88614/increase-swap-size](http://askubuntu.com/questions/88614/increase-swap-size)

---

### Post by Ceedub2 on 2012-04-14
Yea Thats the thing Wubi won´t do a hibernate. Standby is all it can do.

---

### Post by bcbc on 2012-04-14
You need a swap partition (not a swap file) to hibernate. Increasing the swap file size won't do it. [http://ubuntu-with-wubi.blogspot.ca/2011/01/swap-and-hibernation.html](http://ubuntu-with-wubi.blogspot.ca/2011/01/swap-and-hibernation.html)

---

