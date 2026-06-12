---
title: "cross compiling environment"
date: 2011-01-07
forum: Programming Talk
---

### Post by superpisto on 2011-01-07
I have installed the mingw package for cross compiling. Of course, I need a cross compiled version of many library (which I already have in the linux form) to get my programs working.
Is there a common tool/suite to handle this for me? Is there a "standard" directory where windows library and headers should go, and the majority of makefiles expect to find into?
Are there common pitfalls, suggestions that I should know about cross compiling?
Thanks.

---

### Post by dodle on 2011-01-08
You can download many libraries for mingw from the web, some are found here: [http://ftp.gnome.org/pub/gnome/binaries/win32/](http://ftp.gnome.org/pub/gnome/binaries/win32/). You will need to extract the libraries into the mingw folder. I think that it is usually located under /usr/i586-mingw32msvc. If you need to compile your libraries from source you will have to use the "--host" and "--build" flags when running the configure script. And make sure to set "--prefix" to the mingw folder. So I think it would be something like this depending on your system, but I am not 100% sure:

```
./configure --build=i686 --host=mingw32 --prefix=/usr/i586-mingw32msvc
```

---

### Post by superpisto on 2011-01-08
thank you.
A last question: what does the w prefix in some libraries stands for? for example, in my amd64-mingw32msvc/lib directory I have both libopengl.a and linwopengl.a (whereas i586-mingw32msvc/lib has only libopengl.a). And why the -32 suffix still stands?

---

### Post by Utkarsh Ray on 2011-01-08
I think 32 is just the remniscent of the architectural antiquities.
E.g. the folder ./Windows in Windows has the folder system and system32 because the old 16-bit softwares will search the required system files in system folder only.
Similarly 64-bit windows has system, system32 and syswow64 because 32-bit code will find the files in system32
(But why keep folder 'system' when 16-bit codes don't run on 64-bit OS)

---

