---
title: "Listing the gcc library search path"
date: 2012-05-19
forum: Programming Talk
---

### Post by PeterP24 on 2012-05-19
Hello,

I am trying to figure a way to make gcc list all the directories in which it searches for libraries (by default with no -Ldir option supplied) - the so called link path or library search path. 

What I want is something similar to the way gcc searches for include directories:

`gcc -print-prog-name=cc1` -v

or 

cpp -v 

since include is more of a preprocessor stuff.

The best I could do was to use gcc with the -print-search-dirs option but although I obtain a listing of what it appears to lib directories, I am confused:
1) it lists, among other things stuff like:
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../../../x86_64-linux-gnu/lib/
which I don't know how to interpret it or say what it means. Here is the full output:
```
install: /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/
programs: =/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../../../x86_64-linux-gnu/bin/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../../../x86_64-linux-gnu/bin/
libraries: =/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../../../x86_64-linux-gnu/lib/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../../../x86_64-linux-gnu/lib/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../:/lib/x86_64-linux-gnu/4.5.2/:/lib/:/usr/lib/x86_64-linux-gnu/4.5.2/:/usr/lib/:/usr/lib/x86_64-linux-gnu/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/
pts@hal9000:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2$ gcc -print-search-dirs

```
2) shouldn't /usr/local/lib be present in the output given by -print-search-dirs option?

I've searched through the ld options also but couldn't find anything useful.

---

### Post by MadCow108 on 2012-05-19
> **PeterP24 said:**
> Hello,

The best I could do was to use gcc with the -print-search-dirs option but although I obtain a listing of what it appears to lib directories, I am confused:
1) it lists, among other things stuff like:
/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../../../x86_64-linux-gnu/lib/
which I don't know how to interpret it or say what it means. Here is the full output:
```
install: /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/
programs: =/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../../../x86_64-linux-gnu/bin/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../../../x86_64-linux-gnu/bin/
libraries: =/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../../../x86_64-linux-gnu/lib/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../../../x86_64-linux-gnu/lib/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../:/lib/x86_64-linux-gnu/4.5.2/:/lib/:/usr/lib/x86_64-linux-gnu/4.5.2/:/usr/lib/:/usr/lib/x86_64-linux-gnu/x86_64-linux-gnu/4.5.2/:/usr/lib/x86_64-linux-gnu/
pts@hal9000:/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2$ gcc -print-search-dirs

```


they are just displayed a bit weird, use readlink -m to canonicalize them.
in there are the usual paths /lib/, /usr/lib and /usr/lib/<arch-triplet>
the rest are gcc internal paths for its own stuff

> 
2) shouldn't /usr/local/lib be present in the output given by -print-search-dirs option?


this will never be the case in default settings
/usr/local is a place to install stuff the system does not know about by default. E.g. non package managed stuff.

---

### Post by PeterP24 on 2012-05-19
> **MadCow108 said:**
> 
> 2) shouldn't /usr/local/lib be present in the output given by -print-search-dirs option?

this will never be the case in default settings
/usr/local is a place to install stuff the system does not know about by default. E.g. non package managed stuff.

I got the first part - but now, I was looking for something else and found something here ([http://www.linuxfromscratch.org/lfs/view/6.5/chapter05/toolchaintechnotes.html):](http://www.linuxfromscratch.org/lfs/view/6.5/chapter05/toolchaintechnotes.html):)

ld --verbose | grep SEARCH

which outputs

```
SEARCH_DIR("/usr/x86_64-linux-gnu/lib64"); SEARCH_DIR("=/usr/local/lib/x86_64-linux-gnu"); SEARCH_DIR("=/usr/local/lib64"); SEARCH_DIR("=/lib/x86_64-linux-gnu"); SEARCH_DIR("=/lib64"); SEARCH_DIR("=/usr/lib/x86_64-linux-gnu"); SEARCH_DIR("=/usr/lib64"); SEARCH_DIR("=/usr/local/lib"); SEARCH_DIR("=/lib"); SEARCH_DIR("=/usr/lib");
```

It might be strange but I was expecting the output of ld --verbose | grep SEARCH to be equivalent with the output of gcc -print-search-dirs. And, as you can see, the last command outputs /usr/local/lib also.

---

### Post by MadCow108 on 2012-05-20
ok I was wrong there, usr/local/lib is added by /etc/ld.so.conf.d/libc.conf

to make it worse gcc does look in usr/local/lib by default too but its not listed by --print-search-dirs
I'm confused

---

