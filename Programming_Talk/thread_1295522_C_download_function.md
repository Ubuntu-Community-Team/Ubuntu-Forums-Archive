---
title: "C download function?"
date: 2009-10-19
forum: Programming Talk
---

### Post by Levo on 2009-10-19
Hi! I am making a program using C. I need a way to download files from the net. I searched but I didn't found anything. I don't want to use wget. Thanks in advance!

---

### Post by dwhitney67 on 2009-10-19
Consider libcurl.

P.S.  Go here to view some example programs.  [http://curl.haxx.se/libcurl/c/example.html](http://curl.haxx.se/libcurl/c/example.html)

---

### Post by openfly on 2009-10-19
Just want to chime in seconding curl.  libcurl knowledge is pretty transferable from all languages so you'll be learning something basic and useful all over the place.

---

### Post by Levo on 2009-10-20
> **dwhitney67 said:**
> Consider libcurl.

P.S.  Go here to view some example programs.  [http://curl.haxx.se/libcurl/c/example.html](http://curl.haxx.se/libcurl/c/example.html)

yes i tried libcurl before posting, but it didn't compile.

---

### Post by JordyD on 2009-10-20
> **Levo said:**
> yes i tried libcurl before posting, but it didn't compile.

Isn't libcurl in the repos?

---

### Post by Levo on 2009-10-20
> **JordyD said:**
> Isn't libcurl in the repos?

I weren't clear. I want to compile it under windblows using devc++.

---

### Post by Zugzwang on 2009-10-20
Should be no problem to compile libcurl in DevC++. You can also try the already compiled versions for windows from libcurl's homepage.

Probably this is your problem: [http://pidgin.im/pipermail/devel/2009-February/007571.html](http://pidgin.im/pipermail/devel/2009-February/007571.html)

---

### Post by Levo on 2009-10-20
> **Zugzwang said:**
> Should be no problem to compile libcurl in DevC++. You can also try the already compiled versions for windows from libcurl's homepage.

Probably this is your problem: [http://pidgin.im/pipermail/devel/2009-February/007571.html](http://pidgin.im/pipermail/devel/2009-February/007571.html)

Yes that's it. But where to run the command described? And the file "makefile.mingw" doesn't exist. I tried adding "-L"C:/Dev-Cpp/lib/curl"" in makefile.win, but nothing changed.

---

### Post by Levo on 2009-10-20
What I want to do is to compile the curl headers in my program (no external library).

---

### Post by dwhitney67 on 2009-10-20
> **Levo said:**
> What I want to do is to compile the curl headers in my program (no external library).

Header files are always compiled.  If the header files declare functions, these functions must be implemented somewhere if they are going to be used.

libcurl is a collection of header files and both shared-object library and static library files.

Obviously to reference the correct syntax for a libcurl function, you will need to include the header file which declares the function.

When it is time to link your application to form the executable, you have two choices: link with the shared-object libraries, or link with the static libraries.  Typically one does not build these libraries when the application is built.

If you link with the shared-object libraries, then your app will have a small-footprint on the hard-disk, because during runtime it will automatically reference the necessary shared-object library as needed.

If you are looking to create an application that can be moved from one (similar) machine to another, without having to worry if libcurl is present or not, then you would link your application with the static libraries.  Bear in mind that this will significantly increase the footprint size of the application.

Either way, if you develop under Windows, the executable will not run under Linux, unless 1) you recompile the source, or 2) you run it under a Windows Emulator (eg wine).

---

### Post by Levo on 2009-10-20
> **dwhitney67 said:**
> Header files are always compiled.  If the header files declare functions, these functions must be implemented somewhere if they are going to be used.

libcurl is a collection of header files and both shared-object library and static library files.

Obviously to reference the correct syntax for a libcurl function, you will need to include the header file which declares the function.

When it is time to link your application to form the executable, you have two choices: link with the shared-object libraries, or link with the static libraries.  Typically one does not build these libraries when the application is built.

If you link with the shared-object libraries, then your app will have a small-footprint on the hard-disk, because during runtime it will automatically reference the necessary shared-object library as needed.

If you are looking to create an application that can be moved from one (similar) machine to another, without having to worry if libcurl is present or not, then you would link your application with the static libraries.  Bear in mind that this will significantly increase the footprint size of the application.

Either way, if you develop under Windows, the executable will not run under Linux, unless 1) you recompile the source, or 2) you run it under a Windows Emulator (eg wine).

My problem is that I cannot link the static libraries. I don't know how. And I cannot find anything searching the web.

---

### Post by dwhitney67 on 2009-10-20
> **Levo said:**
> My problem is that I cannot link the static libraries. I don't know how. And I cannot find anything searching the web.

Under Linux, one would do something like:
```

gcc MySource.c -static -lcurl -o myapp

```
I do not know what the construct is under Windows.  IMO, Windows are great to look out of, but not for computing.

---

### Post by shae on 2009-10-20
If you cannot get libcurl to work in windows, you can implement your own downloader with sockets.  Here is a good introduction: [http://beej.us/guide/bgnet/](http://beej.us/guide/bgnet/).

---

### Post by interval1066 on 2009-10-20
> **Levo said:**
> What I want to do is to compile the curl headers in my program (no external library).

When you say "DevC++" are you talking Microsoft Developer's Studio? May not be as strait forward as you are attempting. I would look for a Win32 (or 64) version of libcurl (may not exist, but it may) targeting DevStudio, or just develop your app on cygwin, which is not a bad way to go. You know you can develop apps with cygwin and re-distribute the cygwin dll with your monstrous creations. At least I believe you can, I think there's a permission slip somewhere in the cygwin readmes.

---

### Post by Levo on 2009-10-20
> **shae said:**
> If you cannot get libcurl to work in windows, you can implement your own downloader with sockets.  Here is a good introduction: [http://beej.us/guide/bgnet/](http://beej.us/guide/bgnet/).

I don't make this program for me, so I'd prefer an easiest way.

Dev-C++ [http://www.bloodshed.net/](http://www.bloodshed.net/)

---

### Post by Levo on 2009-10-21
OK, I fixed the problem with the linker options. But when I download a file that is more than 1-2 megabytes it is always corrupted. Does anybody know anything about this?

---

