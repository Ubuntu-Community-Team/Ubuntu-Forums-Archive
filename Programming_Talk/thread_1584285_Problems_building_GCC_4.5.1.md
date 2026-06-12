---
title: "Problems building GCC 4.5.1"
date: 2010-09-28
forum: Programming Talk
---

### Post by quutar on 2010-09-28
I am trying to build GCC 4.5.1 on Ubuntu

I have a VirtualBox install of Ubuntu 10.04.1 64 bit (I use VirtualBox when developing, since I can take snapshots and easily roll back if i screw up the build env... now I am trying linux development)

So I start with a clean Ubuntu 10.04.1 install, do a package update to bring things up to date.... I then do the following
[http://pastebin.com/dbYyKAA4](http://pastebin.com/dbYyKAA4)
(I keep good notes to be repeatable)

After that I download and run the following script
[http://pastebin.com/yw0Ve6ZE](http://pastebin.com/yw0Ve6ZE)

The build process works until it gets to GCC itself and fails on the make process with the following errors
[http://pastebin.com/t1JJpktu](http://pastebin.com/t1JJpktu)

it seams to be failing on the multilib section... so I tried doing a 
"sudo apt-get build-dep gcc-4.4-multilib" to see if I missed anything, and it defaulted to the normal gcc-4.4 build dependencies

If needed I can upload the .vdi (VirtualBox drive image) if someone wants to load the machine and see what I am doing

---

### Post by ssam on 2010-09-29
googling "configure: error: cannot compute suffix of object files: cannot compile" gave many threads.

one suggested looking in the config.log (as suggested in the error message), so its possible a better error message is in there.

---

### Post by Bachstelze on 2010-09-29
Since you are doing this in a VBox, can't you just use Maverick? It has gcc 4.5 in the repositories.

---

### Post by quutar on 2010-09-29
> **Bachstelze said:**
> Since you are doing this in a VBox, can't you just use Maverick? It has gcc 4.5 in the repositories.

when I use vbox and maverick, other things break... the bi directional clipboard breaks, and the video drivers break (800x600 is a pain to work in)

---

### Post by quutar on 2010-09-29
> **ssam said:**
> googling "configure: error: cannot compute suffix of object files: cannot compile" gave many threads.

one suggested looking in the config.log (as suggested in the error message), so its possible a better error message is in there.

my config.log
[http://pastebin.com/zheZQfpu](http://pastebin.com/zheZQfpu)

I am looking through the threads... tried some things, not found a solution yet

---

### Post by quutar on 2010-09-29
ok... i even added "--*disable*-[I]multilib" to the ./configure command... and the make still fails in the checking multilib configuration for libgcc

what am I doing wrong?

I have all of the commands I am running, all of the libraries I am using listed there

the .vdi object is 13+ gig, so i don't think anybody wants to download it
[/I]

---

### Post by quutar on 2010-09-30
I added "export LD_LIBRARY_PATH=$DEV_LIBDIR/lib" to the build script... and that problem went away...

to be replaced by a new one

"/usr/bin/ld: cannot find -lstdc++"

[http://pastebin.com/cVDRRVj7](http://pastebin.com/cVDRRVj7)

I tried adding libstdc++6-4.4-dev but that did not fix it...

---

### Post by quutar on 2010-09-30
ok... i am still stuck on the -lstdc++ issue

I made sure libstdc++6-4.4-dev was installed via apt-get, no change

I have tried moving to a 32 bit linux install (new VirtualBox machine, clean install), no change

I also adjusted my build script [http://pastebin.com/GDkXw5E1](http://pastebin.com/GDkXw5E1) to put the gcc and all the libraries in the same directory "~/dev/usr" (vs gcc being in one, and the 6 support libraries in a second), no change

I even looked up the stdc++ library, and considered compiling it externally, but it is now part of the gcc svn download... so I have it, it should be compiled in

I don't know what I am doing wrong... I am starting with a fresh install of Ubuntu 10.04.1, doing the package update, installing the guestOS drivers from virtual box... then doing the exact commands i have listed above...

I am able to build gcc-4.4 from the package repository (as a test)... but i can't build gcc 4.5.1 from svn

---

### Post by quutar on 2010-10-01
ok, based on some help from the #gcc channel on effnet, i removed the static linking from the ./configure
(new build script is much simpler [http://pastebin.com/7yd8ZpZ7](http://pastebin.com/7yd8ZpZ7) )

and make worked... 

but my next step in the script is a "make check" for GCC and it blew up
[http://otakuvideo.com/~quu/check.txt](http://otakuvideo.com/~quu/check.txt)

so, i seam to be able to make gcc, but it fails its test, and the make install fails also

-_-;;;

---

### Post by quutar on 2010-10-03
I have simplified this as much as possible, I am no longer downloading from SCM or anything... these are all snapshots


I have a VirtualBox machine with Ubuntu 10.04.1 64-bit Desktop and a 32 gig hard drive image
I let the update manager update the system, and then I install the GuestOS additions from VirtualBox

My Linux install is then base lined (I take a snapshot)

i log in, create a sub directory in my home directory, go into that sub directory (I named it conplay-dev but it can be anything)

I then create an env.sh in this directory - [http://pastebin.com/EjSPLmNt](http://pastebin.com/EjSPLmNt)
I then create an init.sh in this directory - [http://pastebin.com/hLwLLTW3](http://pastebin.com/hLwLLTW3)
I then create a build.sh in this directory - [http://pastebin.com/8i8ugG53](http://pastebin.com/8i8ugG53)
Finally I make all three executable "chmod +x *.sh"

I run "./init.sh" and then "./build.sh"

the init runs fine (I need to put in my password for the two sudo steps)... and the build seams to run fine... until it gets to the "make check" for GCC and fails

what am I doing wrong, why is the check for GCC failing?

---

### Post by quutar on 2010-10-05
I decided to try it with GMP 4.3.2 instead of 5.0.1 and i get the same thing

```
make[3]: Leaving directory `/home/amv/dev/build/gcc/gcc'
make[2]: *** No rule to make target `check-lto', needed by `check'.  Stop.
make[2]: Leaving directory `/home/amv/dev/build/gcc/gcc'
make[1]: *** [check-gcc] Error 2
make[1]: Leaving directory `/home/amv/dev/build/gcc'
make: *** [do-check] Error 2
```

It seams that gcc itself is failing

```
        === gcc Summary ===

# of expected passes        72572
# of unexpected failures    22
# of unexpected successes    26
# of expected failures        184
# of unsupported tests        972
/home/amv/dev/build/gcc/gcc/xgcc  version 4.5.1 (GCC) 
```

If i investigate up, I see these, which add up to the amount of unexpected results

```
Running /home/amv/dev/src/gcc/gcc/testsuite/gcc.dg/guality/guality.exp ...
XPASS: gcc.dg/guality/example.c  -O0  execution test
XPASS: gcc.dg/guality/example.c  -O1  execution test
XPASS: gcc.dg/guality/example.c  -O2  execution test
XPASS: gcc.dg/guality/example.c  -O2 -flto  execution test
XPASS: gcc.dg/guality/example.c  -O2 -fwhopr  execution test
XPASS: gcc.dg/guality/guality.c  -O0  execution test
XPASS: gcc.dg/guality/guality.c  -O1  execution test
XPASS: gcc.dg/guality/guality.c  -O2  execution test
XPASS: gcc.dg/guality/guality.c  -O3 -fomit-frame-pointer  execution test
XPASS: gcc.dg/guality/guality.c  -O3 -g  execution test
XPASS: gcc.dg/guality/guality.c  -Os  execution test
XPASS: gcc.dg/guality/guality.c  -O2 -flto  execution test
XPASS: gcc.dg/guality/guality.c  -O2 -fwhopr  execution test
XPASS: gcc.dg/guality/pr41353-1.c  -O0  line 28 j == 28 + 37
XPASS: gcc.dg/guality/pr41353-1.c  -O1  line 28 j == 28 + 37
XPASS: gcc.dg/guality/pr41353-1.c  -O2  line 28 j == 28 + 37
XPASS: gcc.dg/guality/pr41353-1.c  -O3 -fomit-frame-pointer  line 28 j == 28 + 37
XPASS: gcc.dg/guality/pr41353-1.c  -O3 -g  line 28 j == 28 + 37
XPASS: gcc.dg/guality/pr41353-1.c  -Os  line 28 j == 28 + 37
FAIL: gcc.dg/guality/pr41353-1.c  -O2 -flto  line 28 i == 37
FAIL: gcc.dg/guality/pr41353-1.c  -O2 -flto  line 28 i1 == 2 * 37
FAIL: gcc.dg/guality/pr41353-1.c  -O2 -flto  line 28 i2 == 3 * 37
FAIL: gcc.dg/guality/pr41353-1.c  -O2 -fwhopr  line 28 i == 37
FAIL: gcc.dg/guality/pr41353-1.c  -O2 -fwhopr  line 28 i1 == 2 * 37
FAIL: gcc.dg/guality/pr41353-1.c  -O2 -fwhopr  line 28 i2 == 3 * 37
XPASS: gcc.dg/guality/pr41447-1.c  -O0  execution test
XPASS: gcc.dg/guality/pr41616-1.c  -O0  execution test
XPASS: gcc.dg/guality/pr41616-1.c  -O1  execution test
XPASS: gcc.dg/guality/pr41616-1.c  -O2  execution test
XPASS: gcc.dg/guality/pr41616-1.c  -Os  execution test
XPASS: gcc.dg/guality/pr41616-1.c  -O2 -flto  execution test
XPASS: gcc.dg/guality/pr41616-1.c  -O2 -fwhopr  execution test
FAIL: gcc.dg/guality/vla-1.c  -O0  line 17 sizeof (a) == 6
FAIL: gcc.dg/guality/vla-1.c  -O0  line 24 sizeof (a) == 17 * sizeof (short)
FAIL: gcc.dg/guality/vla-1.c  -O1  line 17 sizeof (a) == 6
FAIL: gcc.dg/guality/vla-1.c  -O1  line 24 sizeof (a) == 17 * sizeof (short)
FAIL: gcc.dg/guality/vla-1.c  -O2  line 17 sizeof (a) == 6
FAIL: gcc.dg/guality/vla-1.c  -O2  line 24 sizeof (a) == 17 * sizeof (short)
FAIL: gcc.dg/guality/vla-1.c  -O3 -fomit-frame-pointer  line 17 sizeof (a) == 6
FAIL: gcc.dg/guality/vla-1.c  -O3 -fomit-frame-pointer  line 24 sizeof (a) == 17 * sizeof (short)
FAIL: gcc.dg/guality/vla-1.c  -O3 -g  line 17 sizeof (a) == 6
FAIL: gcc.dg/guality/vla-1.c  -O3 -g  line 24 sizeof (a) == 17 * sizeof (short)
FAIL: gcc.dg/guality/vla-1.c  -Os  line 17 sizeof (a) == 6
FAIL: gcc.dg/guality/vla-1.c  -Os  line 24 sizeof (a) == 17 * sizeof (short)
FAIL: gcc.dg/guality/vla-1.c  -O2 -flto  line 17 sizeof (a) == 6
FAIL: gcc.dg/guality/vla-1.c  -O2 -flto  line 24 sizeof (a) == 17 * sizeof (short)
FAIL: gcc.dg/guality/vla-1.c  -O2 -fwhopr  line 17 sizeof (a) == 6
FAIL: gcc.dg/guality/vla-1.c  -O2 -fwhopr  line 24 sizeof (a) == 17 * sizeof (short)
Running /home/amv/dev/src/gcc/gcc/testsuite/gcc.dg/ipa/ipa.exp ...

```

=== g++ Summary === looks fine
=== gfortran Summary === looks fine

I don't know if the "make check" is failing due to the check-lto or all the gcc unexpected results

---

### Post by quutar on 2010-10-08
I did a "make -k check" and piped it to this file
[http://otakuvideo.com/~quu/make_-k_check.txt](http://otakuvideo.com/~quu/make_-k_check.txt)

a while bunch of un expected failures... but I am not using "cutting edge" builds of anything... i am just using snapshots

---

