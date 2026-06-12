---
title: "error in a make file I can't figure out.."
date: 2010-03-20
forum: Programming Talk
---

### Post by Affrikka on 2010-03-20
Hey, I'm making d2x-xl (a descent 2 port) and while making it I get this error:

```
mathieu@prometheus:~/Desktop/d2x-xl$ make
make  all-recursive
make[1]: Entering directory `/home/mathieu/Desktop/d2x-xl'
Making all in 2d
make[2]: Entering directory `/home/mathieu/Desktop/d2x-xl/2d'
g++ -DHAVE_CONFIG_H -I. -I.. -I ../include -I ../input/include -I ../network/linux/include -I ../audio/linux/include -I /usr/local/include/SDL    -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -O3 -Wall -Wno-char-subscripts   -fopenmp -MT bitblt.o -MD -MP -MF .deps/bitblt.Tpo -c -o bitblt.o bitblt.cpp
In file included from ../include/piggy.h:17,
                 from ../include/loadgamedata.h:19,
                 from ../include/descent.h:76,
                 from bitblt.cpp:18:
../include/audio.h: In member function ‘int CAudioChannel::Playing()’:
../include/audio.h:185: error: ‘struct CAudioChannel::tChannelInfo’ has no member named ‘mixChunkP’
bitblt.cpp: In function ‘void gr_linear_rep_movsd_2x(ubyte*, ubyte*, uint)’:
bitblt.cpp:167: warning: dereferencing type-punned pointer will break strict-aliasing rules
make[2]: *** [bitblt.o] Error 1
make[2]: Leaving directory `/home/mathieu/Desktop/d2x-xl/2d'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mathieu/Desktop/d2x-xl'
make: *** [all] Error 2
mathieu@prometheus:~/Desktop/d2x-xl$ make
make  all-recursive
make[1]: Entering directory `/home/mathieu/Desktop/d2x-xl'
Making all in 2d
make[2]: Entering directory `/home/mathieu/Desktop/d2x-xl/2d'
g++ -DHAVE_CONFIG_H -I. -I.. -I ../include -I ../input/include -I ../network/linux/include -I ../audio/linux/include -I /usr/local/include/SDL    -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -O3 -Wall -Wno-char-subscripts   -fopenmp -MT bitblt.o -MD -MP -MF .deps/bitblt.Tpo -c -o bitblt.o bitblt.cpp
In file included from ../include/piggy.h:17,
                 from ../include/loadgamedata.h:19,
                 from ../include/descent.h:76,
                 from bitblt.cpp:18:
../include/audio.h: In member function ‘int CAudioChannel::Playing()’:
../include/audio.h:185: error: ‘struct CAudioChannel::tChannelInfo’ has no member named ‘mixChunkP’
bitblt.cpp: In function ‘void gr_linear_rep_movsd_2x(ubyte*, ubyte*, uint)’:
bitblt.cpp:167: warning: dereferencing type-punned pointer will break strict-aliasing rules
make[2]: *** [bitblt.o] Error 1
make[2]: Leaving directory `/home/mathieu/Desktop/d2x-xl/2d'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mathieu/Desktop/d2x-xl'
make: *** [all] Error 2

```


I see that it says the whole "has no member mixChunkP" but I can't figure out how/where to get it

---

### Post by Affrikka on 2010-03-20
bump

---

### Post by wirelessmonkey on 2010-03-21
First install all of your dependencies...
```

sudo aptitude install libsdl-dev libsdl-mixer1.2-dev libsdl-image1.2-dev libgl1-mesa-dri libgl1-mesa-dev libmotif3 libmotif-dev libdirectfb-dev libgtk-directfb-2.0-0 libgtk-directfb-2.0-dev libglew-dev libglew1.5 libglewmx-dev libglewmx1.5 libcurl4-dev curl


```

Then get the latest SVN release...

```

svn co https://d2x-xl.svn.sourceforge.net/svnroot/d2x-xl d2x-xl

```

Then...
```

cd d2x-xl/
./autogen.sh
./configure
make

```


Then you'll need to download all the associated data files.

Best of Luck

---

