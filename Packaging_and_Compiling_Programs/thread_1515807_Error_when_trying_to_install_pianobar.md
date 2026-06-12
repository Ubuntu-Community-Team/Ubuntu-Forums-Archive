---
title: "Error when trying to install pianobar"
date: 2010-06-22
forum: Packaging and Compiling Programs
---

### Post by graytragedy on 2010-06-22
I'm trying to install [pianobar](http://github.com/PromyLOPh/pianobar) to stream Pandora music on Ubuntu.

I've downloaded all the dependencies, but when I try to install pianobar from the source I'm getting the following:


```
root@graytragedy-laptop:/home/graytragedy/Downloads/PromyLOPh-pianobar-3631791# make clean && make
rm -f src/main.o src/player.o src/settings.o src/terminal.o src/ui_act.o src/ui.o src/ui_readline.o libpiano/src/crypt.o libpiano/src/piano.o libpiano/src/xml.o libwaitress/src/waitress.o libezxml/src/ezxml.o \
			libpiano/src/crypt.lo libpiano/src/piano.lo libpiano/src/xml.lo libwaitress/src/waitress.lo libezxml/src/ezxml.lo pianobar \
			libpiano.so.0.0.0
cc -Wall -g -std=c99 -pedantic -I libpiano/src -I libwaitress/src \
			-I libezxml/src -DENABLE_FAAD -DENABLE_MAD -c \
			-o src/main.o src/main.c
In file included from src/main.c:47:
src/player.h:30:22: error: neaacdec.h: No such file or directory
src/player.h:34:17: error: mad.h: No such file or directory
In file included from src/main.c:47:
src/player.h:72: error: expected specifier-qualifier-list before ‘NeAACDecHandle’
src/main.c: In function ‘main’:
src/main.c:274: error: ‘struct audioPlayer’ has no member named ‘waith’
src/main.c:275: error: ‘struct audioPlayer’ has no member named ‘waith’
src/main.c:281: error: ‘struct audioPlayer’ has no member named ‘waith’
src/main.c:282: error: ‘struct audioPlayer’ has no member named ‘waith’
src/main.c:283: error: ‘struct audioPlayer’ has no member named ‘waith’
src/main.c:284: error: ‘struct audioPlayer’ has no member named ‘waith’
src/main.c:288: error: ‘struct audioPlayer’ has no member named ‘gain’
make: *** [src/main.o] Error 1
```

I don't understand these errors and couldn't find anything meaningful by searching them. I did find [this post](http://ubuntuforums.org/showpost.php?p=8618524&postcount=4) which mentions some of these errors, but [the solution](http://ubuntuforums.org/showpost.php?p=8619373&postcount=5) is something I've already done.

Can anyone tell me what the problem is?

---

### Post by mc4man on 2010-06-22
> error: neaacdec.h No such file or directory
error: mad.h No such file or directory



try this 
```
sudo apt-get install libfaad-dev libmad0-dev
```


Edit:
just grabbed your source - many times you can find useful info in a readme or install txt file - in this case "INSTALL"

> Dependencies
------------

make
libao				[http://www.xiph.org/ao/](http://www.xiph.org/ao/)
libfaad2			[http://www.audiocoding.com/downloads.html](http://www.audiocoding.com/downloads.html)
AND/OR libmad		[http://www.underbit.com/products/mad/](http://www.underbit.com/products/mad/)

Generally (not always), when you see a dep listed you'll need the header(s) for compiling (<whatever.h>
In ubuntu libraries are also generally split into shared packages (needed for running apps) and -dev packages  (needed for compiling

So if you were to search libao, libfaad, and libmad in in synaptic you'd see -dev's also listed and worth installing

Also noted in the INSTALL file is you can build with faad and mad support or just one or the other

---

### Post by graytragedy on 2010-06-23
Thanks so much! I didn't realize I also needed the -devs. Install works fine now with:

```
make clean && make
```

Thanks for the additional information as well, as I'm totally new to Linux/Ubuntu. I really appreciate it.

---

