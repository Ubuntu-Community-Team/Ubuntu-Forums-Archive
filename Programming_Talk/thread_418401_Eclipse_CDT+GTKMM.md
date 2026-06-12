---
title: "Eclipse CDT+GTKMM"
date: 2007-04-22
forum: Programming Talk
---

### Post by Redscare on 2007-04-22
Hey guys!! I am using the Eclipse CDT and program mainly in C++. I have tried anjuta, but I much prefer Eclipse CDT, mainly because the autocomplete in anjuta is terrible. Has anyone managed to use the Eclipse CDT and GTKMM together and compiled a working project? If so, could you please tell me how to setup Eclipse for GTKMM?

---

### Post by Burkey on 2007-04-25
/BUMP

I am after the same thing.. I want to use libglade, trying to get it working right now... did you find any solution?

The reason for GTK and Eclipse.. cross-platform! I need to be able to take my software over to windows and re-build there.

---

### Post by cybrid on 2007-08-12
More of the same, but in my case is CDT GTK-2 using C not C++. It should be the same, but after looking at CDT site for a guide onto how to link libraries I still can't manage to get a simple gtk hello world program. Any ideas over here?

---

### Post by cybrid on 2007-08-12
I think I found it, but I'm not totaly sure. Once you have created a project go to:

Project-->Properties--->C/C++ Build---> Tool Settings tab ---> GCC C Compiler--->Directories

And then add /usr/include/gtk-2.0 or /usr/include/gtkmm

---

### Post by olejorgen on 2007-08-12
It seems like the easiest thing whould be to make your own makefile, and use a Standard make c/c++ project.

So you'll probably need to learn make basics (and pgk-config)

---

### Post by cybrid on 2007-08-12
Only if the project is small; on a mid-big one, writing the makefile by yourself can be a nightmare. That's one of the points of using an IDE; to avoid not-coding work. Tha's my opinion.

---

### Post by olejorgen on 2007-08-13
Yes, you might say that. Problem is that (as far as I can see) eclipse is not mature enough.

If it's a big project, it would be a good idea to use automake/conf.

If your really want to do it from eclispe (managed build) do this:
```

pkg-config --cflags gtkmm-2.4
pkg-config --libs gtkmm-2.4 

```
Everythink behind "-I" should go in extra include paths, and everything behind "-l" should go in libraries.

DISCLAIMER:
I'm *not* a very experienced eclipse user. (nor an gnu autotools expert or a gtk guru)

EDIT:
> I think I found it, but I'm not totaly sure. Once you have created a project go to:

Project-->Properties--->C/C++ Build---> Tool Settings tab ---> GCC C Compiler--->Directories

And then add /usr/include/gtk-2.0 or /usr/include/gtkmm
Yes, that's it. In addition you need to specify extra libraries under linker option. (see output from pgk-config)

---

### Post by Skretch on 2008-03-26
Here you will find a resolution of your problem:

[http://kapo-cpp.blogspot.com/2007/02/gtkmm-and-eclipse.html](http://kapo-cpp.blogspot.com/2007/02/gtkmm-and-eclipse.html)

---

### Post by vfargenta on 2010-06-03
I added this:
pkg-config --cflags --libs gtkmm-2.4
[FONT=monospace][FONT=Verdana]to 'command line pattern' of Project -> Properties -> C/C++ Build -> Settings -> Tool settings -> GCC C++ Compiler and GCC C++ Liker[/FONT][/FONT].
It works for me.

Regards,
Vinícius

---

