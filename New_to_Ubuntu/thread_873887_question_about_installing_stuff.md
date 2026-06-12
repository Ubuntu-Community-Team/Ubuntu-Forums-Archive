---
title: "question about installing stuff"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by jimi_hendrix on 2008-07-29
hi

ok so i know you can get stuff from synaptic or by using sudo apt-get but what do you do if you download something in a tar.gz

thanks

---

### Post by nick_h on 2008-07-29
[How to install ANYTHING in Ubuntu!](http://monkeyblog.org/ubuntu/installing/)

---

### Post by SunnyRabbiera on 2008-07-29
Usually its better to stick with the repositories, but if you need to install source code try to avoid it till you get more experience.

---

### Post by t0p on 2008-07-29
> **jimi_hendrix said:**
> hi

ok so i know you can get stuff from synaptic or by using sudo apt-get but what do you do if you download something in a tar.gz

thanks

Read the **README** or **INSTALL** files for instructions.

But, to give you some idea:
```
./configure
make
sudo make install
```

But that's a very general guide.

---

### Post by jimi_hendrix on 2008-07-29
ok thanks

---

### Post by oldos2er on 2008-07-29
> **jimi_hendrix said:**
> hi

ok so i know you can get stuff from synaptic or by using sudo apt-get but what do you do if you download something in a tar.gz

thanks

By default, Ubuntu doesn't come with a compiler. You first need to install the package "build-essential".

---

