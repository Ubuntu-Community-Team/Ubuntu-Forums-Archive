---
title: "Allegro 5 static compile"
date: 2012-07-03
forum: Programming Talk
---

### Post by vanio on 2012-07-03
Hi, I'm writing a little J&R game under allegro 5, which I compiled from source and installed. The game is nearly done and I want to do a static compile, but I get these errors:
```
/usr/bin/ld: cannot find -lallegro_acodec
/usr/bin/ld: cannot find -lallegro_audio
/usr/bin/ld: cannot find -lallegro_color
/usr/bin/ld: cannot find -lallegro_image
/usr/bin/ld: cannot find -lallegro_main
/usr/bin/ld: cannot find -lallegro_memfile
/usr/bin/ld: cannot find -lallegro_primitives
/usr/bin/ld: cannot find -lallegro_ttf
/usr/bin/ld: cannot find -lallegro_font
/usr/bin/ld: cannot find -lallegro
collect2: ld returned 1 exit status
```This is what I use to compile:
```
gcc -Wall -o game.run game.cpp `pkg-config --cflags --libs --static allegro-5.0 allegro_acodec-5.0 allegro_audio-5.0 allegro_color-5.0 allegro_font-5.0 allegro_image-5.0 allegro_main-5.0 allegro_memfile-5.0 allegro_primitives-5.0 allegro_ttf-5.0` -static
```And this is what "pkg-config --cflags --libs --static allegro-5.0 " returns:
```
-I/usr/local/include  -L/usr/local/lib -lallegro  
```Finaly here is a little screen from the game I want to be able to share ;)

[IMG]http://i47.tinypic.com/2j1x5j7.png[/IMG]

---

### Post by dwhitney67 on 2012-07-03
> **vanio said:**
> And this is what "pkg-config --cflags --libs --static allegro-5.0 " returns:
```
-I/usr/local/include  -L/usr/local/lib -lallegro  
```
That's great that pkg-config seems to be returning a result.  But what's on your system's disk?  Can you locate **/usr/local/lib/liballegro.a** (which is the static library)?

P.S.  Undoubtedly you should have other Allegro related libraries in /usr/local/lib.

P.S. #2  Use 'g++' for compiling C++ code, not 'gcc'.

---

### Post by vanio on 2012-07-03
Nope, no liballegro.a
```
liballegro_acodec.so@       liballegro_main.so.5.0@
liballegro_acodec.so.5.0@   liballegro_main.so.5.0.6
liballegro_acodec.so.5.0.6  liballegro_memfile.so@
liballegro_audio.so@        liballegro_memfile.so.5.0@
liballegro_audio.so.5.0@    liballegro_memfile.so.5.0.6
liballegro_audio.so.5.0.6   liballegro_primitives.so@
liballegro_color.so@        liballegro_primitives.so.5.0@
liballegro_color.so.5.0@    liballegro_primitives.so.5.0.6
liballegro_color.so.5.0.6   liballegro.so@
liballegro_font.so@         liballegro.so.5.0@
liballegro_font.so.5.0@     liballegro.so.5.0.6
liballegro_font.so.5.0.6    liballegro_ttf.so@
liballegro_image.so@        liballegro_ttf.so.5.0@
liballegro_image.so.5.0@    liballegro_ttf.so.5.0.6
liballegro_image.so.5.0.6   pkgconfig/
liballegro_main.so@         python2.7/

```As far as I recall, I compiled and installed allegro in the following maner:
```

mkdir build
cd build
cmake ..
make
make install
```Am I missing something during the way?
:-k

---

### Post by dwhitney67 on 2012-07-03
> **vanio said:**
> Am I missing something during the way?
:-k

I can't say; I don't know anything about Allegro.  But I can tell that you are missing the static libraries.  If your goal is to proceed with testing your application, for now I suggest that you rely on linking with the shared-object libraries.  In the meantime, perhaps someone more knowledgeable than I can assist you in building the static libraries for Allegro.

P.S.  Allegro itself relies on other libraries, hence it is possible that building a static library doesn't make sense.  But that is just a guess that I'm floating.

---

### Post by omgimdrunk on 2012-12-16
I know this post is a bit old but to solve this issue and help anyone else that comes across this, the *.a allegro files that need to be staticly linked are in the directory in which  you compiled allegro5.

For example:

I would cd into:
/home/omgimdrunk/allegro5

Then:
```
mkdir build
cd build
cmake ..
make
sudo make install
sudo ldconfig
```Then in code::blocks
Settings -> Compiler and Debugger settings -> [tab] Linker settings -> add

and select all the *.a libs in 
/home/omgimdrunk/allegro5/build/lib/

---

