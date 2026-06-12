---
title: "Issue compiling gtk+"
date: 2007-07-06
forum: Programming Talk
---

### Post by treak007 on 2007-07-06
Hello all,

I have been attempting to compile the newest version of gtk+.

So far I have installed the newest version of glib. Glib compiled into /usr/local/ and I set the pkg-config path such as it can see the glib installation and I get the proper output for glib when I run it. Now, the problem I am having and the question I have arises when I attempt to compile atk. Despite pkg-config returning the correct values for my glib install, atk complains that I do not have a current version of glib installed.

Does anyone have any ideas what would cause this?

---

### Post by geraldm on 2007-07-07
In linux, it is not enough to install glib; after installing you must either:
1) run command (as root) ldconfig   OR
2) reboot
The reason is that linux uses a cache for the libs; the command flushes
the obsolete cache, and loads anew.

Gerald

---

### Post by treak007 on 2007-07-07
I already tried that (sorry, I should have mentioned that in my previous post). I did check using ldconfig -p and I can see the libraries in there.  The output is:

```

 ldconfig -p |grep glib-2.0
        libglib-2.0.so.0 (libc6) => /usr/local/lib/libglib-2.0.so.0
        libglib-2.0.so.0 (libc6) => /usr/lib/libglib-2.0.so.0
        libglib-2.0.so (libc6) => /usr/local/lib/libglib-2.0.so
        libglib-2.0.so (libc6) => /usr/lib/libglib-2.0.so

```

Thanks for your quick response though. Any other ideas?

---

### Post by geraldm on 2007-07-07
Be certain that the actually library is there.  It should be a longer number, 
such as /usr/local/lib/libglib-2.0.so.1200.9
You could try setting the configure options for the root of glib with --with-glib=
On occasion I have resorted to link trickery: set links in /usr/lib 
to point to where pkg-config says it is.
If I have different versions in /usr/lib than in /usr/local/lib I might
try moving the older version to a temporary location while the package
is built.
Gerald

---

### Post by treak007 on 2007-07-07
The libraries are indeed there. They also do have the larger numbers as you mentioned. The shared object files with .0's are actually symbolic links to the actual files. 

```

 ls /usr/local/lib/ | grep glib-2.0
glib-2.0
libglib-2.0.la
libglib-2.0.so
libglib-2.0.so.0
libglib-2.0.so.0.1200.7
libglib-2.0.so.0.1200.9

```

Currently, pkg-config sees the library and gives all the correct linking and compiler flags. However the configure script still does not see it.

---

### Post by HermanAB on 2007-07-07
Hmm, I went through that just a few days ago on a RedHat system, now I'm wondering what all the gotchas were...

Question:
Did you remove the previous version of Glib?

The Ubuntu distributed version will likely be in /lib, while your own one will probably default to /usr/local/lib.  So a simple search will likely find the older one first, since /lib is likely earlier in the search path.

Try a find:
# find / -name libglib*

and see what pops out of the woodwork.

Cheers,

Herman

---

### Post by treak007 on 2007-07-07
> Question:
Did you remove the previous version of Glib?

No, I did not. I wish to keep both versions.  Do you think it would be more beneficial to remove the old?

---

