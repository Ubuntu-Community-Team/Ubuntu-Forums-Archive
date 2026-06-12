---
title: "Help with installing FLTK? [Configure could not find required X11 libraries]"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by N00bMonkey on 2012-02-24
Hey there, I'm really new to Linux and I'm actually pretty lost when it comes to installing things and getting things to work... I'm using Ubuntu 10.04 and would like to install FLTK... When I type 'make' in the terminal i get the error: 

"configure: error: Configure could not find required X11 libraries
./configure: line 11558: exit: aborting.: numeric argument required
./configure: line 11558: exit: aborting.: numeric argument required
make: *** [makeinclude] Error 255"

I really have no idea what to do to get it working... Could somebody please help me? 
Thank you in advance :)

---

### Post by MG&amp;TL on 2012-02-24
FLTK is in the ubuntu repositories, unless you have reasons not to, you can install it (I assume you mean the development libraries) with:

```
sudo apt-get install libfltk1.3-dev
```

If you do have a reason (i.e. you're a FLTK developer), you probably want one of the X libraries, I think libx11-dev:

```
sudo apt-get install libx11-dev
```

If you need more help, give us more information. :)

---

