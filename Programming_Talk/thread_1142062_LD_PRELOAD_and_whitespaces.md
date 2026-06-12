---
title: "LD_PRELOAD and whitespaces"
date: 2009-04-28
forum: Programming Talk
---

### Post by WitchCraft on 2009-04-28
Hi, question:

I need LD_PRELOAD to preload some shared libraries.

Now LD_PRELOAD is a whitespace seperated list of shared libraries that the linker should preload.

My problem now is that the path of one of the shared libraries has a whitespace in it...

export LD_PRELOAD="/home/username/Desktop/drmdeprot/posix/linux 2.6/glibc.so"

I tried setting double quotes, but that doesn't work...
Anybody knows how I can handle a whitespace in LD_PRELOAD (escape sequences?) ?

---

### Post by WitchCraft on 2009-04-28
Looks like it is not possible:

> 
We use LD_PRELOAD environment variable in couple of places. For those of you not familiar with it: LD_PRELOAD is an environment variable which allows you to specify dynamic libraries which will be loaded before all other libraries. This technique allows you to intercept calls to standard libraries is used by many debugging and analysis tools. Or you could alter behaviour of tsndard libraries for different purposes (e.g. fault injection).
 As other variables like PATH or LD_LIBRARY_PATH, this variable may contain list of library names separated by colons. But... for compatibility with legacy systems it is possible to separate LD_PRELOAD elements by spaces. And older systems did not understand escaping so it turns out it is impossible to put full library paths into LD_PRELOAD if they contain spaces.
 But here is the trick. You may put library directory name(s) with spaces into LD_LIBRARY_PATH (which is kind of a PATH but for dynamically linked/loaded libraries) and put short library name(s) into LD_PRELOAD. Of course, short library file name must not contain spaces but this is less of a limitation.


---

### Post by Arndt on 2009-04-29
> **WitchCraft said:**
> Hi, question:

I need LD_PRELOAD to preload some shared libraries.

Now LD_PRELOAD is a whitespace seperated list of shared libraries that the linker should preload.

My problem now is that the path of one of the shared libraries has a whitespace in it...

export LD_PRELOAD="/home/username/Desktop/drmdeprot/posix/linux 2.6/glibc.so"

I tried setting double quotes, but that doesn't work...
Anybody knows how I can handle a whitespace in LD_PRELOAD (escape sequences?) ?

Create a symbolic link with a name not containing spaces, pointing to the name with spaces. Then use the name of the link in the LD_PRELOAD variable.

---

### Post by WitchCraft on 2009-04-30
> **Arndt said:**
> Create a symbolic link with a name not containing spaces, pointing to the name with spaces. Then use the name of the link in the LD_PRELOAD variable.

Good idea, can even be automatized.
Thanks!

---

