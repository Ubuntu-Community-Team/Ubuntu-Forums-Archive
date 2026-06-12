---
title: "SDL on ubuntu"
date: 2008-12-05
forum: Packaging and Compiling Programs
---

### Post by CrystalMoth on 2008-12-05
I went to this site: [http://lazyfoo.net/SDL_tutorials/lesson01/linux/cli/index.php](http://lazyfoo.net/SDL_tutorials/lesson01/linux/cli/index.php)
and I followed the instructions to get sdl on ubuntu. I then tried to compile the program: "g++ -o myprogram mysource.cpp -lsdl"
and it said: "cannot find -lsdl" then it said "ld returned 1 exit status"
can someone help me please

---

### Post by jpkotta on 2008-12-06
Worked for me.  Here are all the sdl packages I have:
```
$ dpkg -l "*sdl*" | grep ^i
ii  libsdl-image1.2                            1.2.6-3                                     image loading library for Simple DirectMedia
ii  libsdl-mixer1.2                            1.2.8-4                                     mixer library for Simple DirectMedia Layer 1
ii  libsdl-mixer1.2-dev                        1.2.8-4                                     development files for SDL1.2 mixer library
ii  libsdl-net1.2                              1.2.7-2                                     network library for Simple DirectMedia Layer
ii  libsdl-net1.2-dev                          1.2.7-2                                     Development files for SDL network library
ii  libsdl-ttf2.0-0                            2.0.9-1                                     ttf library for Simple DirectMedia Layer wit
ii  libsdl1.2-dev                              1.2.13-2ubuntu1                             Simple DirectMedia Layer development files
ii  libsdl1.2debian                            1.2.13-2ubuntu1                             Simple DirectMedia Layer
ii  libsdl1.2debian-alsa                       1.2.13-2ubuntu1                             Simple DirectMedia Layer (with X11 and ALSA 

```

You probably don't need all of them; my packages tend to get somewhat crufty because I usually update instead of reinstall.

---

