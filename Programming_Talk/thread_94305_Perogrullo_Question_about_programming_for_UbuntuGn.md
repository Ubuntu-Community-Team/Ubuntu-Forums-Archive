---
title: "Perogrullo Question about programming for UbuntuGnome"
date: 2005-11-23
forum: Programming Talk
---

### Post by xerman on 2005-11-23
Hello there,

I was wondering, as a new "programmer" for linux, what are the needs for writing my first program.
I've installed Glade+Anjuta, and made my first "sorta" glade tutorial not finished because i get this error:
> --@--:~/Proyectos/CelsiusToFarenheit$ autogen.sh
bash: autogen.sh: command not found
--@--:~/Proyectos/CelsiusToFarenheit$

but doing a "ls" the "autogen.sh" file is there.

I was doing step by step what stated in the tutorial:
[http://www.kplug.org/glade_tutorial/glade2_tutorial/glade2_introduction.html]("http://www.kplug.org/glade_tutorial/glade2_tutorial/glade2_introduction.html")

Maybe I'm missing something, I haven't installed something or whatever. At least I've got "build - essentials" installed.

Any way, if someone recommends another pair of tools to develop apps for gnome-linux-ubuntu, and most important, a good learing guide for doing so, I will be very thankful.

Best regards
xermán

by the way, I'm on BreezyAMD64, maybe this affects to

---

### Post by gord on 2005-11-23
```
sudo apt-get install autogen
```

you might also need 
```
sudo apt-get install autoconf automake1.9
```

allthough apprently automake1.9 has troubles with anjuta, iv had no problems with it.

---

### Post by xerman on 2005-11-24
Hi Gord,

I'll try those ones and hope they work.

Thanks a lot in advance.
Best regards.
xermán

---

### Post by monkey89 on 2005-11-24
You have to do ./autogen.sh, not just autogen.sh, because . is not in your PATH.

---

