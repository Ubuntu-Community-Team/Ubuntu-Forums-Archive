---
title: "Trouble with make all TOPOVISTA"
date: 2014-05-16
forum: Packaging and Compiling Programs
---

### Post by gil.rito on 2014-05-16
Hi,

I'm trying to install TOPOVISTA

[http://www.cs.arizona.edu/projects/topovista/](http://www.cs.arizona.edu/projects/topovista/)

I've downloaded and extracted to tarball to my Home directory, but when I ran make all I got the following error

```
...
cc -O  -DTSLOOKUP -I../tokenlib -c  ingzip.c
cc -O  -DTSLOOKUP -I../tokenlib -c  inhttp.c
cc -O  -DTSLOOKUP -I../tokenlib -c  intvtp.c
cc -O  -DTSLOOKUP -I../tokenlib -c  inmem.c
cc -O  -DTSLOOKUP -I../tokenlib -c  utils.c
cc -O  -DTSLOOKUP -I../tokenlib -o topo control.o decode.o emit.o errcalc.o eps.o fetch.o infov.o interest.o lock.o main.o misc.o mqueue.o neighbor.o normal.o overhead.o path.o pnmops.o print.o split.o surface.o trans.o tile.o tstream.o tvrp.o tvtp.o view.o wrap.o input.o infile.o ingzip.o inhttp.o intvtp.o inmem.o utils.o -L/usr/X11R6/lib ../tokenlib/libtsvc.a -lm -lz -lpthread -lglut -lGLU -lGL -lXi -lXmu -lX11 -lXext
/usr/bin/ld: error: cannot find -lXmu
collect2: ld returned 1 exit status
make[2]: ** [topo] Erro 1
make[2]: Saindo do diretório `/home/gil/Transferencias/topovista-4.0/src/viewer'
make[1]: ** [../bin/topo] Erro 2
make[1]: Saindo do diretório `/home/gil/Transferencias/topovista-4.0/src'
make: ** [c] Erro 2

```

I've already done the following symbol link but without success:

```
sudo ln -s /usr/lib/i386-linux-gnu/libXmu.so.6.2.0 /usr/lib32/libXmu.so
```

Any help will be grateful. Thanks

---

### Post by oldos2er on 2014-05-16
Moved to Packaging & Compiling Programs.

---

