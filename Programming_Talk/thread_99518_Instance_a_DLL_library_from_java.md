---
title: "Instance a DLL library from java"
date: 2005-12-05
forum: Programming Talk
---

### Post by cyaconi on 2005-12-05
Hi.. I'm finding the way to use a DLL from a java application (in ubuntu).
I'm a java programmer, and I can do this on windows... but I'm trying to migrate to ubuntu and until know this is my first problem.
Is there any solution to this?? I don't have the dll source code, so re-compiling isn't posible.

Maybe wine??

Please, any help will be very appreciated.

Regards.

---

### Post by amohanty on 2005-12-06
I am possibly miunderstanding your goal here, but whats the point of loading a dll (via java or otherwise) in Ubuntu??

---

### Post by toojays on 2005-12-06
amohanty: some companies provide DLL's for other developers to use to make their life easier. This is often done in the free software community as well (e.g. why program your own FLAC decoding routines when you can just use libFLAC?).

cyaconi: You will need to write a native wrapper (in C) around this DLL. The best way to go is probably to use libwine. The documentation for libwine is sorely lacking, but I'm sure it can do what you want. Your Java app would then use JNI to load the native library, which would be linked against libwine, which can load Windows DLLs.

---

### Post by amohanty on 2005-12-06
> amohanty: some companies provide DLL's for other developers to use to make their life easier. This is often done in the free software community as well (e.g. why program your own FLAC decoding routines when you can just use libFLAC?).

I realize that and understand the JNI technique too. I was just wondering if there wasnt a native library based approach that would solve cyaconi's wihout resorting to libwine, whose documentation, as you mentioned is sorely lacking and based on my past experience is a pain to get to work. 

I was wondering if you knew how the w32codecs are implemented?

Thanks.
AM

---

### Post by toojays on 2005-12-06
Yes, if there is a native library with the functionality cyaconi wants, he should use that.

I'm not sure about how the w32codecs are done. I imagine it is similar to what libwine does, but I don't know the low level details.

---

### Post by cyaconi on 2005-12-07
Thank you for your answers... 
Finally I take an alternative way, wich don't depends on the DLL file. Instead that, would be good to know how to do it anyway...

Regards

---

### Post by amohanty on 2005-12-07
Start here:

[http://winehq.com/site/docs/winelib-guide/index](http://winehq.com/site/docs/winelib-guide/index)
[http://wiki.winehq.org/](http://wiki.winehq.org/)

HTH

---

