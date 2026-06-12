---
title: "linux programming nubee, what do i need? (c/c++/allegro)"
date: 2006-08-28
forum: Programming Talk
---

### Post by stairwayoflight on 2006-08-28
hi,

i have programmed before a little in windows. i don't know what i need for ubuntu, i saw a couple of basic questions "how do i make a program?" etc., i know how to write one even the cmd (eg. gcc foo.c -o foo) but what do i need?

specifically i need gcc for c/c++, but also for allegro i need "make" or something right? the allegro library page already assumes linux has these things installed.

also can you suggest an ide and perhaps mention how to set it up to compile with the allegro library?

i would really appreciate any help on this, thank you.

---

### Post by kaamos on 2006-08-28
to get make, gcc, g++ and such, use
```
sudo aptitude install build-essential
```

For general c/c++ ide, you could try for example Anjuta.

---

### Post by X.Cyclop on 2006-08-28
```
sudo apt-get install liballegro4.2
```

And download [Code::Blocks]("http://codeblocks.org"). ;)

---

### Post by stairwayoflight on 2006-08-29
hi,

thnks for the nfo's. i have the library, but couldn't find the source? i assume its ready to rock'n'roll, but i wanted the source code for the demo, example programs, etc. it seemed unclear from the "properties" dialog of the "liballegro-doc" if they are included, or just doc's re them are included.

eg. i wanted to open up ex12bit.c and compile for a test run. i would immediately grab a tarball of it myself, but if there is a package for it and a default location, i would rather stick to defaults than run into problems later.

perhaps i'll grab the source, and use it at least temporarily from my ~/ --but i don't really know where this stuff is supposed to go in *nix anyways.

---

