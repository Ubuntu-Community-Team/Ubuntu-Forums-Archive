---
title: "[SOLVED] compiling from source"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by rockerphil on 2008-07-13
ok, i'm attempting to compile a program from source for the first time, and of course i'm running in to problems. the first of which was caused by not having the program "gcc" installed, which is resolved, now, to the problem upon which i'm stuck. the program's readme.txt file says to cd to the directory to which the source code is downloaded, which i've done, and then to run "make clean <system>" which in my case i'm choosing linux-x86-any, which will hopefully avoid any problems, but when i run it i get this error output

DES_fmt.c: In function ‘get_key’:
DES_fmt.c:302: warning: incompatible implicit declaration of built-in function ‘memcpy’

which to me is a bit baffling, any ideas? thanx in advance,


Phil

---

### Post by ChameleonDave on 2008-07-13
If "make clean" fails, then just clean it manually by deleting the whole directory, and starting from scratch by re-extracting the tarball you downloaded.

Make sure, of course, that you have installed the package "build-essential" via Synaptic or by typing "sudo apt-get install build-essential" on the command line.

---

### Post by rockerphil on 2008-07-13
Make sure, of course, that you have installed the package "build-essential" via Synaptic or by typing "sudo apt-get install build-essential" on the command line.[/QUOTE]

thanx man, this did it, like i said, this is my first time compiling from source, so i didn't know, much thanx bro:guitar:

----------------
Now playing: [Candlebox - Far Behind](http://www.foxytunes.com/artist/candlebox/track/far+behind)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

