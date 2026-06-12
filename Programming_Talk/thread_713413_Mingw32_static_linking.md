---
title: "Mingw32 static linking"
date: 2008-03-02
forum: Programming Talk
---

### Post by jaddle on 2008-03-02
I've written a small program that uses libsndfile and portaudio. Compiling for linux is simple, but I want to use this in windows as well!

I've managed to get it to compile and function, using mingw32, which is great - I just had to build and install the two libraries after running the configure like this:

```

./configure --host=i586-mingw32msvc --build=i686-pc-linux-gnu  --prefix=/usr/local/i586-mingw32msvc

```

Then I had to add 
```

-I/usr/local/i586-mingw32msvc/include -L/usr/local/i586-mingw32msvc/lib -L/usr/local/i586-mingw32msvc/lib/ 

```
when compiling to use those new libraries.

However, I'd really like to make a static binary - right now, I have to distribute two DLLs along with the program, and it'd be nice if it was self-contained, or at least to have the option!

Adding -static to the compile line would be the obvious approach, but when I do that, I end up with all sorts of linking errors: undefined reference to `_waveOutGetErrorTextA@12 and the like. Do I need to compile the libraries differently to let them be statically linked? Or should I be pointing at a different directory with the -L and -I flags?

---

### Post by amingv on 2008-03-02
You will find an explanation/example in the MinGW docs. (Look under "How to create a DLL").

[http://www.mingw.org/docs.shtml#compilingandbuilding](http://www.mingw.org/docs.shtml#compilingandbuilding)

Hope it's of any use...

---

### Post by WW on 2008-03-02
I have done something similar.  Be sure to build the static versions (i.e. the .a files) of the libraries when you build them with mingw.  When you link your program, use the full path names of the static libraries instead of using the -L and -l options.  I did not need to use the -static option.

---

### Post by jaddle on 2008-03-02
Hmm.. using this setup, it did build properly, even with the -static option. But the resulting executable executable still requires the dlls be present.

Here's the command that was run: (pretty much, anyway - I took out all the object file names, and replaced with *.o)

```

i586-mingw32msvc-gcc -o ttuner.exe *.o -Wall -O5 -I/usr/local/i586-mingw32msvc/include/ -I/usr/lib/gcc/i586-mingw32msvc/3.4.5/include/  -lm /usr/local/i586-mingw32msvc/lib/libportaudio.dll.a /usr/local/i586-mingw32msvc/lib/libsndfile.dll.a 

```

Is this what you meant I should use?


I get the exact same sized executable as when I use this line
```

i586-mingw32msvc-gcc -o ttuner.exe *.o -Wall -O5 -I/usr/local/i586-mingw32msvc/include/ -I/usr/lib/gcc/i586-mingw32msvc/3.4.5/include/  -lm -lsndfile -lportaudio -L/usr/local/i586-mingw32msvc/lib/

```

---

### Post by WW on 2008-03-02
I don't use the --build option in the ./configure command, and I don't get files that end with .dll.a.  I get files that end in .la and .a; e.g. libsndfile.a, not libsndfile.dll.a.  (This is on Dapper.  I don't know if mingw in newer versions of Ubuntu behaves differently.)

EDIT:  I just tried it on my computer running Ubuntu 7.10.  By building libsndfile with the commands
> $ ./configure --host=i586-mingw32msvc --prefix=/tmp
$ make
$ make install
I ended up with libsndfile.a, libsndfile.dll.a and libsndfile.la in /tmp/lib.

Try using the .a files instead of the .dll.a files.

---

### Post by jaddle on 2008-03-03
Nope, still doesn't work. I recompiled the two libraries, using the configure line you used (just changing the prefix, so that they went into /usr/local). It made these files - .dll, (in $prefix/bin) and .dll.a, .dll.a, and .la. I then tried linking with this line:

```

i586-mingw32msvc-gcc -o ttuner *.o -Wall -O5 -I/usr/local/i586-mingw32msvc/include/ -I/usr/lib/gcc/i586-mingw32msvc/3.4.5/include/  -lm /usr/local/i586-mingw32msvc/lib/libportaudio.dll.a /usr/local/i586-mingw32msvc/lib/libsndfile.dll.a

```

(I guess the -I switches are useless in the linking phase, but it's all managed by a makefile...) Interestingly, -static added to this line did work, but didn't actually change anything at all. In every case, the executable still requires the dll to run.

What is the difference between the .dll.a and the plain .a versions? Using the .a ones in the above line, I get the undefined references. I notice that the .a versions are MUCH larger - libsndfile.a is over 2 megs, while libsndfile.dll.a is only 19K!

---

### Post by WW on 2008-03-03
I'm not sure why that is not working for you.

Just to be clear, here is what has worked for me.  I just tried this on a computer running Ubuntu 7.10 (64 bit, but I don't think that should matter).

First I built the libsndfile library with the commands
> 
$ ./configure --host=i586-mingw32msvc --prefix=$HOME/WinCrossCompile
$ make
$ make install

Then I compiled the file **make_sine.c** in the libsndfile examples directory with the command
> 
$ i586-mingw32msvc-gcc make_sine.c -I$HOME/WinCrossCompile/include $HOME/WinCrossCompile/lib/libsndfile.a -o make_sine.exe

(I gave the full path to libsndfile.a as an argument; I did not use -L or -l.)  I then copied make_sine.exe to a computer running Windows 2000 (sorry, that's the only Windows machine I have handy), where the program ran successfully.

I don't know the difference between the .a and .dll.a files. (I could speculate, but why waste the bandwidth?)  Any cross-compiling gurus out there?


EDIT:  I tried cross-compiling the portaudio library, and failed.

---

### Post by jaddle on 2008-03-04
Hmm.. must be a problem with portaudio then. I checked and yes, libsndfile is working just fine, but with portautio, libportaudio.a doesn't seem to have the symbols in it that it should.

I *think* that the .dll.a is the import library used when making a dynamic executable, and .a is for making static ones. So the .dll.a just has a list of all the stuff that's in the actual dll, and the .a has the actual code. Something along those lines anyway.

Thanks for your help though! I'll inquire on the portaudio mailing list to see if anything special needs to be done to get a static library. I know it's possible, because audacity doesn't require any libraries in windows, and it uses portaudio.

---

### Post by jaddle on 2008-03-05
I see the problem with portaudio - the portaudio library itself depends on symbols in another dll that's shipped with windows (winmm.dll). Since that's not available as a static library (.a) you can't make a static binary.

You can do it by using the following syntax:

```

i586-mingw32msvc-gcc /path/to/libs/portaudio.a test.c -o test.exe -lwinmm

```

So that side of it is happy! The only problem is that using that syntax, there's no way for gcc to search the default library directories for the portaudio file. It makes it rather difficult to write a makefile for it that will be remotely portable!

It'd be nice if you could specify a set of libraries to link statically, and then another set to link dynamically, but all using the -l option so that library paths will be searched for both of them. I don't see any way to do that, unfortunately...

I'll have a look at audacity to see how it manages it, though I'm not too optimistic that its makefile will be easy to understand.

EDIT: Ah. They cheat and just include the portaudio source as a subdir in their source tree, so they know where to find it... I may end up doing the same thing. The alternative is a special flag to pass to the configure script to point to the right directory, I suppose.

---

