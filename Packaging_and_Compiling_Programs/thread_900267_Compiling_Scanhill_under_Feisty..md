---
title: "Compiling Scanhill under Feisty."
date: 2008-08-25
forum: Packaging and Compiling Programs
---

### Post by Eax.exe on 2008-08-25
Hi.

I'm trying to compile Scanhill:
[http://www.enderunix.org/scanhill/](http://www.enderunix.org/scanhill/)
Because I want to test my encrypted networks security.
But when I type "make" (after having ./configured) it says:

```

eax@shodan:~/Desktop/scanhill$ make
gcc -o scanhill hash.o main.o nstrstr.o msn.o sniff.o  -lpcap -liconv -L/usr/lib -L/usr/local/lib
/usr/bin/ld: cannot find -liconv
collect2: ld returned 1 exit status
make: *** [all] Error 1

```

What am I missing?

I'm running Feisty on my Acer TravelMate 4310.
I WOULD be running Hardy but my wired network card won't work due to a kernel error.

Thanks in advance :)

---

### Post by ssam on 2008-08-25
the "-liconv" bit means that it is looking for the iconv library. this will usually be in a package called libiconv or libiconvsomething. also to compile something you need the -dev version of the package as well.

do a search for libiconv in synaptic and you should find what you need

---

### Post by Eax.exe on 2008-08-25
Great, thanks a lot :)
Did a search but it came up with nothing.
I'm going to compile it from source now :) (libiconv I mean)

---

### Post by ssam on 2008-08-25
[http://packages.ubuntu.com/search?keywords=libiconv&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libiconv&searchon=names&suite=all&section=all)

if libiconv-hook1 is it then you should find it. do you universe enabled?

---

### Post by Eax.exe on 2008-08-25
Thanks a lot :) I tried downloading it using synaptic but I still couldn't compile. Therefore I compiled it from source (libiconv).
But I get this error when I try to run Scanhill:

```
scanhill: error while loading shared libraries: libiconv.so.2: cannot open shared object file: No such file or directory

```

Any ideas on what I did wrong?

---

### Post by Eax.exe on 2008-09-10
Anyone? Is it just an error in the program or?
Seems like it doesn't work under Hardy either?

---

