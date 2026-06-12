---
title: "how can i run my c program in ubuntu?"
date: 2005-09-23
forum: Programming Talk
---

### Post by zdcode81 on 2005-09-23
the problem is i am a new user of ubuntu, i have a program that i made it in c language using windows how can i run those program?

---

### Post by thumper on 2005-09-23
[QUOTE=zdcode81]the problem is i am a new user of ubuntu, i have a program that i made it in c language using windows how can i run those program?[/QUOTE]
That very much depends on whether or not you are using any Windows specific C calls.

If you have a file called test.c, then you compile it with the command

gcc test.c

And run it with

./a.out

If you want to call your program foo instead of the default (which is not that usefull really), do this

gcc -o foo test.c

---

### Post by toojays on 2005-09-23
Additionally, if your program does use windows specific calls, you may be able to get it to compile in Ubuntu by installing the libwine-dev package, and using winegcc instead of gcc.

---

