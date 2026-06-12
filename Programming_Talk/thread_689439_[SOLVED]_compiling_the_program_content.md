---
title: "[SOLVED] compiling the program content"
date: 2008-02-06
forum: Programming Talk
---

### Post by Ampi on 2008-02-06
I am trying to compile a program called content. I need it for a course.
After installing almost all things with apt-get that just looked remotely as something I could need, I got my amount of errors down from uncountable ones to countable ones. So I am relatively happy.
Still I get the next errors, and sincerely I have no clue what to do about them. 
Any ideas?

```

make[1]: Entering directory `/home/amparo/content/content'
cd victor; make -f ../makefile.del victor; cd ..
make[2]: Entering directory `/home/amparo/content/content/victor'
cc -o setup setup.o utility.o -L ../../vibrant/lib -lvibrant -L ../../vibrant/lib -lncbi -L /usr/X11R6/lib -lXext -ldl -lm -lXm -lXt -lX11 
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
make[2]: *** [setup] Error 1
make[2]: Leaving directory `/home/amparo/content/content/victor'
cp victor/setup .
cp: cannot stat `victor/setup': No such file or directory
make[1]: *** [com] Error 1
make[1]: Leaving directory `/home/amparo/content/content'
make: *** [unix] Error 2

```

---

### Post by hod139 on 2008-02-08
Try installing the package: libxext-dev
That should help the linking error.  I'm not sure about the 
victor/setup error you are getting, looks like you are missing a file/dir

---

### Post by Ampi on 2008-02-12
I installed the libraries and now my erros are these. So I'm still missing a file, but now that's another one... 
I that logical??

```
helpcomp
make[2]: helpcomp: Command not found
make[2]: *** [content.hlp] Error 127
make[2]: Leaving directory `/home/amparo/content/content/victor'
cp victor/setup .
cp victor/content .
cp victor/*.so .
cp victor/*.hlp .
cp: cannot stat `victor/*.hlp': No such file or directory
make[1]: *** [com] Error 1
make[1]: Leaving directory `/home/amparo/content/content'
make: *** [unix] Error 2
```

---

### Post by amo-ej1 on 2008-02-12
I never heard about helpcomp and neither has my apt cache, so I suggest you simply type 

```

touch /home/amparo/content/content/victor/k.hlp

```

to create a dummy file so your make will continue

---

### Post by Ampi on 2008-02-12
Hmm, it helped, but now I'm missing apparently more files :(

But it's good to know I can make dummy files. Tomorrow I'll check with the software maker and if that doesn't help I'll just "dummy" the whole program! ;)

Thanks anyway! 

```
helpcomp
make[2]: helpcomp: Command not found
make[2]: *** [contds.hlp] Error 127
make[2]: Leaving directory `/home/amparo/content/content/yuri'
cp yuri/*.so .
cp yuri/*.h .
cp yuri/*.con .
cp yuri/*.hlp .
cp: cannot stat `yuri/*.hlp': No such file or directory
make[1]: *** [com] Error 1
make[1]: Leaving directory `/home/amparo/content/content'
make: *** [unix] Error 2
```

---

### Post by Ampi on 2008-02-13
Thank you guys, it has been solved!

Apparently it's a known bug and they know how to fix it, so that's all folks!

---

