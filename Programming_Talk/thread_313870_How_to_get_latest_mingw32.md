---
title: "How to get latest mingw32"
date: 2006-12-06
forum: Programming Talk
---

### Post by Crypto-138 on 2006-12-06
I'm trying to compile a dll from source on Linux, but apparently, the mingw32's g++ is outdated.

```
$ i586-mingw32msvc-g++ --version
i586-mingw32msvc-g++ (GCC) 3.4.5 (mingw special) 
```

Is there a newer version available? And could someone tell me how to get it? The main site just gave me a bunch of links to each individual files.
(I'm new to C++, let alone compiling for a whole other OS)
BTW I'm running the AMD_64 edition of Ubuntu Edgy. (If this helps)

---

### Post by cybrid on 2006-12-06
Sorry, my fear I have no idea :( try to download and compile an entire mingw. That's just an Idea.

To compile sources in a GNU/Linux box:

-Unpack the tar.gz or tar.bzip or whatever format the sources are compressed into.
-Create a new directory under /usr/local. This is in order to not screw up your current mingw install.
-Go to the folder where you unpacked the sources
-Write:
./configure --prefix=/usr/local/<the_directory_you_created_before> &&
make && make install

Hope this may help you.

---

### Post by Crypto-138 on 2006-12-07
Hrm. I don't think my version is what's stoppping me from compiling my dll... I think this version's pretty recent, because someone else tried it with 3.4.2 and it worked for him... =l

I think I'll start another topic, since I think I realize what the real problem is now.

Thanks anyways.

---

