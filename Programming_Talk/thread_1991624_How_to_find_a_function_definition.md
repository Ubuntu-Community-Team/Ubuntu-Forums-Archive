---
title: "How to find a function definition?"
date: 2012-05-30
forum: Programming Talk
---

### Post by mabo5184 on 2012-05-30
Hi, 
 
I'm new to programming so I apologize if my question is a stupid one ...
 
I'm looking for a way to search/find the source for a function that is called from a program?
 
Further details for those that have time to read further ...
 
I am reading the source for rhythmbox trying to understand how it works and I came across a function (rb_ipod_db_get_type) that is used but I can't find the source for the function, so I'm looking for the function definition, not sure if that is correct terminology?
 
What I have tried so far;
 
I have downloaded the source tar balls and used grep to search -
 
Precision-M6500:~/work/rhythmbox-2.96$ grep -Hnr -e rb_ipod_db_get_type *
plugins/ipod/rb-ipod-db.h:37:#define RB_TYPE_IPOD_DB (rb_ipod_db_get_type ())
plugins/ipod/rb-ipod-db.h:55:GType rb_ipod_db_get_type (void);
Binary file plugins/ipod/.libs/libipod.so matches
Binary file plugins/ipod/.libs/libipod.soT matches
Binary file plugins/ipod/.libs/libipod_la-rb-ipod-db.o matches
Binary file plugins/ipod/.libs/libipod_la-rb-ipod-static-playlist-source.o matches
 
The search found the function prototype, a MACRO that uses the function, and some binary files from where I compiled the program.
 
The binary file names suggest that libipod may be involved in some way so I searched the libipod source ...
 
The search directories -
mabo@mabo-Precision-M6500:~/work$ ll
total 6836
drwxrwxr-x 4 mabo mabo 4096 May 30 19:33 ./
drwxr-xr-x 54 mabo mabo 4096 May 31 2012 ../
drwxrwxr-x 9 mabo mabo 4096 Oct 12 2010 libgpod-0.8.0/
-rw-rw-r-- 1 mabo mabo 997674 May 30 19:32 libgpod-0.8.0.tar.gz
drwxrwxr-x 20 mabo mabo 4096 May 28 19:31 rhythmbox-2.96/
-rw-rw-r-- 1 mabo mabo 5984192 Mar 11 20:28 rhythmbox-2.96.tar.xz
 
The search command -
mabo@mabo-Precision-M6500:~/work$ grep -Hnr -e rb_ipod_db_get_type *
rhythmbox-2.96/plugins/ipod/rb-ipod-db.h:37:#define RB_TYPE_IPOD_DB (rb_ipod_db_get_type ())
rhythmbox-2.96/plugins/ipod/rb-ipod-db.h:55:GType rb_ipod_db_get_type (void);
Binary file rhythmbox-2.96/plugins/ipod/.libs/libipod.so matches
Binary file rhythmbox-2.96/plugins/ipod/.libs/libipod.soT matches
Binary file rhythmbox-2.96/plugins/ipod/.libs/libipod_la-rb-ipod-db.o matches
Binary file rhythmbox-2.96/plugins/ipod/.libs/libipod_la-rb-ipod-static-playlist-source.o matches
 
I have also used objdump and strings to look inside the binary files but I have not found any clues.
 
I would have expected the definition to be in the rhythmbox source files somewhere, because the function name matches the style used to name the other functions, which leads me to consider that the defintion does not exists ...
 
Does anyone have a suggestion to what I can try next ...

---

### Post by roelforg on 2012-05-31
```

find . | grep "\.h" | xargs grep <function_name_here>

```

---

### Post by Simian Man on 2012-05-31
You can use find and grep, but there are *much* better tools available for this.  I'd recommend cscope.  Install it, then go to the top level of the source directory and type:
> cscope -R

Then you will have the option to find C symbols (any use of a function or variable), find global definitions (the definitions of globals including functions), and even find which functions call another function.  Navigate between the search area and the results area with the Tab key and quit with Ctrl-D.

It's an incredibly useful tool - especially when you are dealing with large and unfamiliar code bases.

Cheers.

---

### Post by Simian Man on 2012-05-31
Well my advice is still good in general, but yeah that function sure is missing from the source isn't it?  I'll hunt around a little bit.

---

### Post by ofnuts on 2012-05-31
> **mabo5184 said:**
> Hi, 
 
I'm new to programming so I apologize if my question is a stupid one ...
 
I'm looking for a way to search/find the source for a function that is called from a program?
 
Further details for those that have time to read further ...
 
I am reading the source for rhythmbox trying to understand how it works and I came across a function (rb_ipod_db_get_type) that is used but I can't find the source for the function, so I'm looking for the function definition, not sure if that is correct terminology?
 
What I have tried so far;
 
I have downloaded the source tar balls and used grep to search -
 
Precision-M6500:~/work/rhythmbox-2.96$ grep -Hnr -e rb_ipod_db_get_type *
plugins/ipod/rb-ipod-db.h:37:#define RB_TYPE_IPOD_DB (rb_ipod_db_get_type ())
plugins/ipod/rb-ipod-db.h:55:GType rb_ipod_db_get_type (void);
Binary file plugins/ipod/.libs/libipod.so matches
Binary file plugins/ipod/.libs/libipod.soT matches
Binary file plugins/ipod/.libs/libipod_la-rb-ipod-db.o matches
Binary file plugins/ipod/.libs/libipod_la-rb-ipod-static-playlist-source.o matches
 
The search found the function prototype, a MACRO that uses the function, and some binary files from where I compiled the program.
 
The binary file names suggest that libipod may be involved in some way so I searched the libipod source ...
 
The search directories -
mabo@mabo-Precision-M6500:~/work$ ll
total 6836
drwxrwxr-x 4 mabo mabo 4096 May 30 19:33 ./
drwxr-xr-x 54 mabo mabo 4096 May 31 2012 ../
drwxrwxr-x 9 mabo mabo 4096 Oct 12 2010 libgpod-0.8.0/
-rw-rw-r-- 1 mabo mabo 997674 May 30 19:32 libgpod-0.8.0.tar.gz
drwxrwxr-x 20 mabo mabo 4096 May 28 19:31 rhythmbox-2.96/
-rw-rw-r-- 1 mabo mabo 5984192 Mar 11 20:28 rhythmbox-2.96.tar.xz
 
The search command -
mabo@mabo-Precision-M6500:~/work$ grep -Hnr -e rb_ipod_db_get_type *
rhythmbox-2.96/plugins/ipod/rb-ipod-db.h:37:#define RB_TYPE_IPOD_DB (rb_ipod_db_get_type ())
rhythmbox-2.96/plugins/ipod/rb-ipod-db.h:55:GType rb_ipod_db_get_type (void);
Binary file rhythmbox-2.96/plugins/ipod/.libs/libipod.so matches
Binary file rhythmbox-2.96/plugins/ipod/.libs/libipod.soT matches
Binary file rhythmbox-2.96/plugins/ipod/.libs/libipod_la-rb-ipod-db.o matches
Binary file rhythmbox-2.96/plugins/ipod/.libs/libipod_la-rb-ipod-static-playlist-source.o matches
 
I have also used objdump and strings to look inside the binary files but I have not found any clues.
 
I would have expected the definition to be in the rhythmbox source files somewhere, because the function name matches the style used to name the other functions, which leads me to consider that the defintion does not exists ...
 
Does anyone have a suggestion to what I can try next ...
To use a library you don't need its source code, the bare minimum is the library executable (libsomething.so for share libs or libsomething.a for static libs) and the description of the library API, usually as C header files (.H). Which is what you found with rhythmbox (likely dragged is as a dependent libipod-dev package or somesuch).

If you need to see the source code for libipod, see there: [http://libipod.sourceforge.net/](http://libipod.sourceforge.net/)

---

### Post by gnusci on 2012-05-31
Use the Devs documentation

[http://developer.gnome.org/rhythmbox/unstable/](http://developer.gnome.org/rhythmbox/unstable/)

---

### Post by Simian Man on 2012-05-31
Something strange is going on here.  I searched for that function in the binaries of rhythmbox and libgpod and it isn't there.  At first I thought maybe that plugin is deprecated and ipod support was pulled into the main code base, but that doesn't seem to be true.  There's something I'm missing because that code shouldn't compile as is, but it surely does...

---

### Post by Tony Flury on 2012-05-31
I wouldn't expect to see the function name in binaries (unless the binaries have been compiled with debug options turned on).

The names might be in the libraries, but remember they could well be munged.

---

### Post by Simian Man on 2012-05-31
> **Tony Flury said:**
> I wouldn't expect to see the function name in binaries (unless the binaries have been compiled with debug options turned on).

The names might be in the libraries, but remember they could well be munged.

Actually function names are in the binary files whether or not you use debug options.  You can inspect them easily enough with objdump.  And C compilers generally do not mangle names as compilers for other languages do.

---

### Post by Tony Flury on 2012-05-31
> **Simian Man said:**
> Actually function names are in the binary files whether or not you use debug options.  You can inspect them easily enough with objdump.  And C compilers generally do not mangle names as compilers for other languages do.

I stand corrected ;-)

---

### Post by mabo5184 on 2012-05-31
> **Simian Man said:**
> Well my advice is still good in general, but yeah that function sure is missing from the source isn't it? I'll hunt around a little bit.
 
Thanks for the suggestion, I will try it tonight ...
 
My question was a general one because searching a source struck me as a useful tool for the toolbox when debugging.
 
I don't pretend I would ever be able to understand a program as large as Rhythmbox, but I though it would be an interesting place to start given I like using the program and I have been having some problems. I naively thought I might be able to fix my problem while learning some programming along way.

---

### Post by mabo5184 on 2012-06-04
A final update for anyone that may have been interested.
 
The recommended program cscope was very good for searching the source code.
 
Regarding the missing function ... 
 
The function I was looking for is automatically defined with the macro G_DEFINE_DYNAMIC_TYPE, so the function is part of the Glib/GObject system which explains why I could not find it in the source files ...

---

