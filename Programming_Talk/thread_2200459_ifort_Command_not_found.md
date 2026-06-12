---
title: "ifort: Command not found"
date: 2014-01-19
forum: Programming Talk
---

### Post by andrewrolphspam on 2014-01-19
I am new to Ubuntu. I am having the same problems as in

[http://ubuntuforums.org/showthread.php?t=2037056](http://ubuntuforums.org/showthread.php?t=2037056)
[http://software.intel.com/en-us/forums/topic/269216](http://software.intel.com/en-us/forums/topic/269216)

except I can't use their solution to source compilervars.sh as I can't find compilervars.sh or the /opt/ directory.

Error message:

root@ubuntu:~/Documents/PartIIIProject/dynnlo-v1.4# make
ifort -O3 -I/home/quezolcoatl/Documents/PartIIIProject/dynnlo-v1.4/src/Inc   -c -o /home/quezolcoatl/Documents/PartIIIProject/dynnlo-v1.4/obj/boost.o /home/quezolcoatl/Documents/PartIIIProject/dynnlo-v1.4/src/Need/boost.f
make: ifort: Command not found
make: *** [boost.o] Error 127

---

### Post by Bachstelze on 2014-01-20
If you know the directory where [font=monospace]ifort[/font] is located, just doing

```
export PATH="$PATH:/that/directory"
```

should do the trick. To make it permanent, just add that line at the bottom of your [font=monospace].bashrc[/font].

---

### Post by ssam on 2014-01-22
just to check, do you have the intel fortran compiler (ifort) installed?

---

