---
title: "How to create sound files with C++"
date: 2009-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by WitchCraft on 2009-04-30
To create (=not play) sound files in Linux from your C++ program, you need to read the specification for each sound file, implement the usage of the specificatiion and then you're done.

However, this is difficult and needs much time.

Much simpler is the use of an audio library.
For example: libsndfile

You can find it here:
[http://www.mega-nerd.com/libsndfile/](http://www.mega-nerd.com/libsndfile/)

alsong with some sample programs:
[http://www.mega-nerd.com/libsndfile/tools/](http://www.mega-nerd.com/libsndfile/tools/)


Usage it simple:
install fftw (fast fourier transformation)
```

 apt-get -y install fftw-dev libfftw3-dev

```

./configure
make
make install

then the same for the tools

---

### Post by raulih on 2009-09-22
How would you then use this library, say, to create a simple recording or to read a file to create a wave graph?

---

### Post by raulih on 2009-09-23
I tried some examples included in source and got errors:

```
$ gcc sndfile-to-text.c
/tmp/ccQcE1bj.o: In function `convert_to_text':
sndfile-to-text.c:(.text+0x109): undefined reference to `sf_readf_float'
/tmp/ccQcE1bj.o: In function `main':
sndfile-to-text.c:(.text+0x26d): undefined reference to `sf_open'
sndfile-to-text.c:(.text+0x295): undefined reference to `sf_strerror'
sndfile-to-text.c:(.text+0x2cc): undefined reference to `sf_strerror'
sndfile-to-text.c:(.text+0x334): undefined reference to `sf_close'
collect2: ld returned 1 exit status
```

I'm new with C/C++ but would like to get started.

---

### Post by raulih on 2009-10-12
Had to compile differently. 

This configuration is sometimes needed:

```
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
```

Compiling:

```
gcc sndfile-to-text.c `pkg-config --cflags sndfile` `pkg-config --libs sndfile` -o sndfile-to-text
```

Then i could run:

```
./sndfile-to-text somefile.wav somefile.txt
```

---

### Post by WitchCraft on 2009-11-01
> **raulih said:**
> How would you then use this library, say, to create a simple recording or to read a file to create a wave graph?

It has a sample program that does just that...

---

