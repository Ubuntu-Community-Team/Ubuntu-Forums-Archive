---
title: "Linking question [C++]"
date: 2008-07-31
forum: Programming Talk
---

### Post by StOoZ on 2008-07-31
I've installed from synaptic (8.04) this :
[http://id3lib.sourceforge.net/]("http://id3lib.sourceforge.net/")

now , except from he include I had to add to the program code, I had also need to look for this file :
/usr/lib/libid3.so

and in the linking process  supply -lbid3

my question is : why do we need to remove suffix 'lib'?
and also , how does the compiler knows that the file is in /usr/lib/    when im only writing  -lbid3   ??

thanks,

---

### Post by ceclauson on 2008-07-31
> **StOoZ said:**
> 
my question is : why do we need to remove suffix 'lib'?


I'm not sure I can give you a better answer to this than "that's just the way it is."  The compiler always looks for libraries with the prefix "lib", and so you don't specify it in the library name.

> **StOoZ said:**
> and also , how does the compiler knows that the file is in /usr/lib/    when im only writing  -lbid3   ??


This is the default location that the compiler looks in, so if a library is located here, you don't have to specify the path.  If the library, say libmylib.so, is in some other location, say /foo/bar, you'd write -l/foo/bar/mylib.

---

### Post by dribeas on 2008-07-31
> **StOoZ said:**
> 
/usr/lib/libid3.so

and in the linking process  supply -lbid3

my question is : why do we need to remove suffix 'lib'?
and also , how does the compiler knows that the file is in /usr/lib/    when im only writing  -lbid3   ??


First of all, I understand that it is a typo, but it would be -lid3. 

Why remove the lib? That is how the linker was designed, standard issue. That way all libs are named by a pattern (lib*) but you don't really need to type it. Don't quote me on this, I am just guessing here.

Now, on why you don't need the full path. Linker knows of some common standard places in which to look for libraries. It will search in directories given as -L arguments (-L/usr/local/myproject/lib), in directories given in LD_LIBRARY_PATH environment library, in directories given in its own configuration file (don't remember the name, and this is MacOSX :) ) and then in standard directories (/lib,/usr/lib,maybe /usr/local/lib)

   David

---

### Post by Npl on 2008-07-31
> **StOoZ said:**
> my question is : why do we need to remove suffix 'lib'?Moronic behavour of the gcc linker, which might have been considered "smart" one time (you know like naming a library "libiberty" so that users will link it with "-liberty"). Has nothing to do with C/C++ in general.
> **StOoZ said:**
> and also , how does the compiler knows that the file is in /usr/lib/    when im only writing  -lbid3   ??The linker has a couple default paths in which its searching.

---

### Post by dwhitney67 on 2008-07-31
These default paths are generally /usr/lib and /lib.  Other paths can be added to the /etc/ld.so.conf file or into files in /etc/ld.so.conf.d directory.  Any tweaking of the file or adding to the directory (which by the way requires root permissions) needs to be followed by running /sbin/ldconfig.

For more info on ldconfig, read the man-page for such.

P.S.  One can examine the pre-set paths that gcc uses to search for libraries using the following command:
```
gcc --print-search-dirs |grep libraries
```

---

