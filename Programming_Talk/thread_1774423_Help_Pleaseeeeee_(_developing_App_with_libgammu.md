---
title: "Help Pleaseeeeee :( developing App with libgammu"
date: 2011-06-03
forum: Programming Talk
---

### Post by imblack on 2011-06-03
Hello,

I was using kannel but it has some problems, now i want to write my own SMS sending receiving library.

I planned to use libgammu that is for C++.

The problem is that I installed the "libgammu-dev" package but when I try to compile a very simple code I keep getting this error.

"gammu.cpp:1:19: fatal error: gammu.h: No such file or directory"

Now why doesn't installing a dev package automatically setup the include path?

when I fix it by manually adding -L/usr/include/gammu/ while compiling with g++ It gets fixed but I then get Linker errors.

Can anyone please help me?

I would be very thankful, also if you have better options in mind for me please do share.

---

### Post by SevenMachines on 2011-06-03
Yep, the gammu headers are in a sub directory of the /usr/include compiler search path so need to be added to the command line. luckily gammu uses pkg-config so you can get include and link options automatically

```
$ dpkg -L libgammu-dev |grep pkgconfig
/usr/lib/pkgconfig
/usr/lib/pkgconfig/gammu.pc
/usr/lib/pkgconfig/gammu-smsd.pc
```so we can do,
```
$ pkg-config --cflags --libs gammu
-I/usr/include/gammu  -lGammu -lm
```with compiler lines like
```
$ gcc -o myprogram myprogram.c `pkg-config --cflags --libs gammu`
```

---

### Post by imblack on 2011-06-04
Thankyou very much, because of you I am back on track :)

PythonGammu is also very interesting and more straightforward than libgammu but it's a bit slow.

Also can you please tell me how can I handle multiple mobiles using gammu? I will write my own code on top of gammu but you can i guess only connect to one phone with gammu.

---

### Post by SevenMachines on 2011-06-04
Sorry, I've never used gammu so I don't really know what it can or can't do. good luck though :)

---

