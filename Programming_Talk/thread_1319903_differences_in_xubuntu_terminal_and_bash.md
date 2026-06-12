---
title: "differences in xubuntu terminal and bash"
date: 2009-11-08
forum: Programming Talk
---

### Post by newsman on 2009-11-08
I want to know what is the difference in xubuntu terminal and bash.

This is because one of my scripts programmed on my work's remote terminal running fedora core by looks of things works on my works' (PUTTY) terminal interface using sh scriptname

But it didn't work in a similar way in my xubuntu terminal... instead I had to type BASH scriptname.


My initial thoughts were that whatever runs with the sh command should run on most terminals because sh is for compatiblity sake and it refers to the original Bourne shell rather than BASH (Bourne again shell).

Also i cannot use echo $_ in terminal---  I thought its meant to give variables such as kimBH where i would stand for interactive mode... instead the $_ variable has more to do with last program run i think

---

### Post by slavik on 2009-11-08
in fedora sh points to bash, in ubuntu it points to dash. sh proper doesn't have many features ksh and bash scripters are accostumed to.

---

### Post by newsman on 2009-11-09
how can you find out what sh points to (if you have a random distro for example)

---

