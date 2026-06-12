---
title: "64 bit-edness"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by JiminSD on 2008-07-04
Hi,

I have an AMD 64 bit processor. Does gnu/linux automatically run in 64 bit mode, or is there a separate install for this?

How can I tell?

Thanks

---

### Post by sayakb on 2008-07-04
You need to get a LiveCD of amd64 (64-bit) architecture: [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)
Check if you have a 64-bit Ubuntu installed: At a terminal, type:
```
uname -m
```**i386, i586, i686 **and** x86** mean 32-bit
**x86_64** means 64-bit

---

### Post by Hobo Joe on 2008-07-04
There are separate versions of Ubuntu for 32 and 64 bit. They are completely separate installs, you have to download the appropriate version.

---

### Post by sisco311 on 2008-07-04
Open a terminal (Applications -> Accessories -> Terminal) and type:
```
uname -m
```
x86_64 => 64bit
i386 or i686 => 32bit

You can download the 64bit version from:[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by JiminSD on 2008-07-04
Thanks, I ran uname, but did not know how to interpret the answer (686).

---

### Post by JiminSD on 2008-07-04
Is there an automated way to install the 64 bit version via something like update manager?

I've been experiment with 8.1 for about a week now and would like to delve into some 64 bit programming for some maths problems.

Thanks again

---

### Post by JiminSD on 2008-07-04
i think that I may how found the answer to my question here:

[http://ubuntuforums.org/archive/index.php/t-265410.html](http://ubuntuforums.org/archive/index.php/t-265410.html)

I can never find anything until I ask, sorry and thanks

---

