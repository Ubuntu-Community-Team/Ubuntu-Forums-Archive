---
title: "Trouble compiling module"
date: 2015-05-22
forum: Packaging and Compiling Programs
---

### Post by miatawnt2b on 2015-05-22
Hoping someone can help me. I installed the latest magic stick on my Acer Switch10. Magic stick is basically an Ubuntu 15.04 32bit USB image that has patches for baytrail tablets. 
Installing the image went fine, just as every other Ubuntu install I've done. 

The keyboard doesn't work as I had expected, so I need to compile a new hid driver.
[https://github.com/SWW13/hid-acer](https://github.com/SWW13/hid-acer)


Easy enough, though when I run make I am getting errors in the make file that aren't exactly clear. 

```

make -C /lib/modules/4.0.0/build M=/home/devnull/Switch/h/hid-acer modules
make[1]: Entering directory '/usr/src/linux-headers-4.0.0'
  CC [M]  /home/devnull/Switch/h/hid-acer/hid-acer.o
./scripts/recordmcount: 1: ./scripts/recordmcount: Syntax error: ")" unexpected
scripts/Makefile.build:264: recipe for target '/home/devnull/Switch/h/hid-acer/hid-acer.o' failed
make[2]: * [/home/devnull/Switch/h/hid-acer/hid-acer.o] Error 2
Makefile:1390: recipe for target '_module_/home/devnull/Switch/h/hid-acer' failed
make[1]: * [module/home/devnull/Switch/h/hid-acer] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.0.0'
Makefile:27: recipe for target 'default' failed
make: * [default] Error 2&#65279;

```

I have installed build-essential but have the same issue. Any thoughts on this? As you can see it is running a custom 4.0.0 build of the kernel, but i've tried another kernel and have the same basic issue.

---

