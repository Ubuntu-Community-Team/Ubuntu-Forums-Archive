---
title: "Linker problem... ¿?"
date: 2006-03-28
forum: Programming Talk
---

### Post by daniminas on 2006-03-28
Hi everyone.

I been maded a program that uses glib... so, to get the librarys and headers i use:

pkg-config --cflags --libs gmodule-2.0 
pkg-config --cflags --libs gthread-2.0
pkg-config --cflags --libs gobject-2.0
pkg-config --cflags --libs glib-2.0

so, to compile my app i do with every source:

GLIB_FLAGGS=`pkg-config --cflags glib-2.0`
GLIB_THREADD=`pkg-config --cflags glib-2.0`

LINKER_FLAGS=`pkg-config --libs glib-2.0`
LINKER_FLAGSS=`pkg-config --libs gthread-2.0`

gcc ${GLIB_THREADD} -c src/protocol.cpp -o obj/protocol.o
gcc ${GLIB_FLAGGS} ${GLIB_THREADD} -c src/main.cpp -o obj/main.o

etc.. etc

but when i link the objects files i get a lot of errors

gcc ${LINKER_FLAGSS} ${LINKER_FLAGSS} obj/main.o obj/protocol.o -o release/myprogram


AND IF I TRY OF ONE STEP IS THE SAME ERROR AT THE LINKER TIME.. NOT CODE ERRORS I THINK.. BECAUSE WHEN I COMPILE EACH FILE NO ERROR


SOME IDEA OF ME ERROR?.. AND SORRY MY DIRRTY ENGLIS.. H

---

### Post by M4av0 on 2006-03-29
I don't know much, but aren't you supposed to use ld for linking? What errors are
you getting? Try using ld or try to put glib_flags and linker_flags into one gcc line.

---

### Post by rplantz on 2006-03-29
[QUOTE=M4av0]I don't know much, but aren't you supposed to use ld for linking? What errors are
you getting? Try using ld or try to put glib_flags and linker_flags into one gcc line.[/QUOTE]

ld is the loader, but if you use that, you need to explicitly name all the libraries. Using gcc or g++ (see below) automatically searches the standard libraries.

daniminas, do you have a typo here? (LINKER_FLAGSS is used twice.)

> ```
gcc ${LINKER_FLAGSS} ${LINKER_FLAGSS} obj/main.o obj/protocol.o -o release/myprogram
```

Anyway, the answer is that you need to use g++ for your linking. (Since your source files end in .cpp, I'm assuming that you're writing in C++.)

When I tried this with a simple "hello world" program, it compiled just fine with gcc. But I got a lot of link errors. When I did the linking with g++, it worked just fine.

When I write in C++, I use g++ both for compiling and linking.

By the way, separating compiling and linking helps determine that there was a linking error.

---

### Post by daniminas on 2006-03-30
thanks... linking and comiling with the g++ and not error.. i cant beleive!!!  oh.. salve rplantz! =)

---

