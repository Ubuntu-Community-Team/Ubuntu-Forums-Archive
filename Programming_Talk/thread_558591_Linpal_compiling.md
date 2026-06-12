---
title: "Linpal compiling"
date: 2007-09-24
forum: Programming Talk
---

### Post by WilSteele on 2007-09-24
I have been trying to compile linpal for a while and keep coming back to the same issue

a whole lot of lines that say:
gtkmain.cpp:497: error: ‘SomethingOr_other’ was not declared in this scope

and ending with:
make: *** [gtkmain.o] Error 1

Can anyone help
OH, i have also tried to install both palace32 and phalanx under wine, neither wanted to work.

---

### Post by Soybean on 2007-09-24
Try to find the first error... I'm not familiar with linpal, but that kind of sounds like you're missing some required headers. It can probably be fixed by installing some -dev packaged in Synaptic, it's just a matter of figuring out which package you need. :)

---

### Post by Compyx on 2007-09-24
Looks like a dependency issue to me. Do have the development packages of libglade, libcurl and gtkmm installed?

---

### Post by Compyx on 2007-09-24
Hmm, even after doing a:
```
sudo apt-get install libglade2-dev libcurl4-openssl-dev libgtkmm-dev
```
I still get errors (although a lot less):
```

compyx@gutsy:~/downloads/sources/linpal-0.5$ make
g++ -Wall -pedantic -ansi -c gtkmain.cpp `curl-config --cflags` `pkg-config --cflags gtk+-2.0 libglade-2.0 glib-2.0 gthread-2.0`
gtkmain.cpp: In function ‘gboolean close_tab(GtkWidget*, void*)’:
gtkmain.cpp:532: warning: unused variable ‘num’
g++ -Wall -pedantic -ansi -c palbubble.cpp `pkg-config --cflags gtk+-2.0 glib-2.0 gthread-2.0 libglade-2.0`
g++ -Wall -pedantic -ansi -c palcallback.cpp 
g++ -Wall -pedantic -ansi -c gtkasset.cpp `pkg-config --cflags gtk+-2.0 glib-2.0 gthread-2.0 libglade-2.0`
g++ -Wall -pedantic -ansi -c gtkbubble.cpp `pkg-config --cflags gtk+-2.0 glib-2.0 gthread-2.0 libglade-2.0`
gtkbigpage.h:103: error: ISO C++ forbids declaration of ‘GtkBubble’ with no type
gtkbigpage.h:103: error: expected ‘;’ before ‘*’ token
make: *** [gtkbubble.o] Error 1

```

Looks like we're still missing some headers. I think this is one of those instances where using autotools might have helped :)


Anyway, looking at gtkbubble.h and gtkbigpage.h, I see a circular dependency, which does not bode well.

Looks like crappy code to me, but then again, I'm not an expert at C++ coding.

---

### Post by Soybean on 2007-09-24
> **Compyx said:**
> Anyway, looking at gtkbubble.h and gtkbigpage.h, I see a circular dependency, which does not bode well.

Looks like crappy code to me, but then again, I'm not an expert at C++ coding.

Well, there are times when having circular dependencies between interrelated classes is a reasonable and correct thing to do; that's why we have forward declarations.

If it were me, I'd either try to find an accurate list of requirements for this "linpal," (I did a bit of googling, but didn't come up with anything), or I'd search "libgtk" in Synaptic and start installing -dev packages at random. ;) Well, not *exactly* random... I usually try to make up some reason why a particular package seems likely before installing it. You can end up with a lot of pointless junk installed if you use the latter method, but I find that it works surprisingly often. :D

---

### Post by WilSteele on 2007-09-26
hmmm,
have run the command 
apt-get install libglade2-dev libcurl4-openssl-dev libgtkmm-dev
libcurl4-openssl-dev was not found, but i was able to get the other then later found libcurl3-openssl-dev through Synaptec.
Came up to the same Compyx.
A lot of installing libgtk packages later, and I still get the same result.
The software was written quite sometime ago, and I think someone is going to have to fix it, so I am going on a mission now I think.
Thanks guys

---

### Post by Zwack on 2007-10-20
> **WilSteele said:**
> hmmm,
have run the command 
apt-get install libglade2-dev libcurl4-openssl-dev libgtkmm-dev
libcurl4-openssl-dev was not found, but i was able to get the other then later found libcurl3-openssl-dev through Synaptec.
Came up to the same Compyx.
A lot of installing libgtk packages later, and I still get the same result.
The software was written quite sometime ago, and I think someone is going to have to fix it, so I am going on a mission now I think.
Thanks guys

I have compiled it Wil on 7.10...

You need to make one small change to the source, and you need to have various development libraries installed...  I lave libcurl4-gnutls-dev installed... plus libglade-*-dev and so on...

The change to the source is to modify gtkbigpage.h
to add 

class GtkBubble;

before the line that looks like 

class BigPage : PalCallback{

I hope that this helps,

Z.

---

### Post by WilSteele on 2007-10-23
thanks a lot, that really did help, got linpal to compile no problem on 7.04 now.
:)
now i can use linux more than windows
(major microsoft hater)

---

