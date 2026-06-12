---
title: "Eagle pcb designer only runs as root."
date: 2011-12-03
forum: New to Ubuntu
---

### Post by johnnybgoode on 2011-12-03
I try to use Eagle 5 PCB designer and it works perfect until I try to save a new library. The program says "Access denied". So I then run the program as root and it runs and save the naw library.
So I tried to chown eagle john. In the properties window under permissions is indeed the new owner john, but when I run the program again under user john, the new library want save. What do I wrong? Note; I'm just a beginner with linux

---

### Post by zero2xiii on 2011-12-03
Hay,

Owning "eagle" (assuming you are speaking of the program) wont solve the problem. You should rather own the entire eagle directory with settings that is at: ~/.eagle (well atleast on my system. Although it contains a few symbolic links. Might work chown'ing them, not sure. You might try only owning the libraries located at: /usr/share/eagle/lbr But i suggest using caution. Rather own JUST the directory, as saving a new library should then work. If you feel the need to edit current libraries, then rather run eagle as root with the gksudo prefix. But I strongly advice that you make SURE what you are doing, since doing ANYTHING as root, can harm the system or the program.

Good luck

---

### Post by zero2xiii on 2011-12-03
Hay,

I have tested this and found that:

```
sudo chown $(whoami) /usr/share/eagle/lbr
```

Fixes the error of trying to save a NEW library. This new library is then owned by you, so you may alter it as you wish.

If you need to edit the other libraries already contained here (**and you understand the risk of owning crucial program working files**) this will fix the error:

```
sudo chown $(whoami) -R /usr/share/eagle/lbr
```

Cherz and safe editing...

---

### Post by johnnybgoode on 2011-12-25
Thankx.I tried your second option and it works!

---

### Post by zero2xiii on 2011-12-25
Hay,

Glad it helped :). Please marked your thread as solved using the thread tools.

Cherz

---

