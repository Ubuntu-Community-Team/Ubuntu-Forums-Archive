---
title: "Compiling st2205tool and a gdlib error"
date: 2008-04-14
forum: Packaging and Compiling Programs
---

### Post by bobbarker on 2008-04-14
I've been trying to compile st2205tool** (to modify a pictureframe LCD). I'm very newbish to compiling anything but I've read through tons of stuff, have the normal build-essentials and the like.

**Link to source: [http://spritesmods.com/picframe/st2205tool-v1.4pre1.tgz](http://spritesmods.com/picframe/st2205tool-v1.4pre1.tgz)

Right.

When I try and compile I get this:

adamsteele@bim:/usr/local/src/st2205tool$ make
make -C setpic
make[1]: Entering directory `/usr/local/src/st2205tool/setpic'
gcc -o setpic main.o -lgd -L../libst2205 -lst2205  
main.o: In function `sendpic':
/usr/local/src/st2205tool/setpic/main.c:59: undefined reference to `gdImageTrueColor'
/usr/local/src/st2205tool/setpic/main.c:60: undefined reference to `gdTrueColorGetRed'
/usr/local/src/st2205tool/setpic/main.c:61: undefined reference to `gdTrueColorGetGreen'
/usr/local/src/st2205tool/setpic/main.c:62: undefined reference to `gdTrueColorGetBlue'
collect2: ld returned 1 exit status
make[1]: *** [setpic] Error 1
make[1]: Leaving directory `/usr/local/src/st2205tool/setpic'
make: *** [setpic/setpic] Error 2

So obviously there's a problem with libgd and from what I understand there's a few different versions (xpm vs. no xpm) and I've tried both versions with the same results....and I've got no clue what to do. I even tried libgd1 which gave problems of the library not even being found. It's not my code, but it apparently has worked for plenty of other people.

I'm using 7.10 with all this.

---

### Post by bobbarker on 2008-04-15
My only guess is that the libgd in the ubuntu repos is bad. I had this compiled and running within about 5 minutes after booting up Fedora. I suppose I'll try and compile libgd from source.

---

### Post by bobbarker on 2008-04-15
Compiled libgd from source and it worked.

---

