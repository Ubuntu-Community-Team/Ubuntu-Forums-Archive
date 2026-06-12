---
title: "Can't compile and link LIBCONIO (conio.h)"
date: 2005-03-03
forum: Programming Talk
---

### Post by dekae on 2005-03-03
Hello, recently I installed the libconio library. I have conio.h in /usr/include/ and libconio.la and libconio.a in /usr/lib/. When I tried to compile it said that there was an undefined reference to whatever function i tried. After that I saw on some websites that maybe I should try -lconio, so i did that this is how i compiled it:
gcc -c "prueba.c" -o "prueba.o" -lconio
but this didn't work, gcc showed an error that said that it couldn't link. So, how can i link gcc to conio library?, or is everything wrong?, I hope you can help me.
thank you

---

### Post by toojays on 2005-03-04
You need to have libconio.so. See if there is a conio-dev package or something like that.

---

### Post by dekae on 2005-03-04
Where can i find them?

---

### Post by toojays on 2005-03-04
I don't know. Where did you get libconio from? I found a website at conio.sf.net, but it looks like it's only for Windows or DOS . . .

What's it for?

---

### Post by dekae on 2005-03-04
from here [http://sourceforge.net/projects/libconio/](http://sourceforge.net/projects/libconio/) it says it's an implementation for linux

---

### Post by toojays on 2005-03-04
Sorry, my bad, libconio.a is right, you only need libconio.so if you are dynamically linking.

What's the exact error from gcc?

---

### Post by dekae on 2005-03-05
ok, i made it work finally. i added the -lconio next to LDFLAGS.
thanks a lot toojays.

---

### Post by tomchuk on 2005-03-10
for future reference libwine provides conio.h and it's installable though apt:
```

apt-file search conio.h
...
libwine-dev: usr/include/wine/msvcrt/conio.h
...

```

---

### Post by toojays on 2005-03-11
Ah, but that conio is specific to Wine, or at least to the Windows API. dekae was talking about a version for GNU.

---

### Post by Mudit_BITS on 2008-03-05
ppl i want to use graphics of turbo c on linux and i hav started hating windows 

can any 1 please help me .... i want to know how to use graphics.h header file on gcc compiler net aint giving proper answer
:confused:

---

