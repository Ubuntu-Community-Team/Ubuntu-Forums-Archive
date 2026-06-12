---
title: "Anjuta and wxWidgets"
date: 2005-12-27
forum: Programming Talk
---

### Post by Nikusan on 2005-12-27
The title says it all, I guess.
I'd like to get wx up and running in anjuta. I notice that anjuta has a wx template in its project wizard, which is pretty neat.
When I finish the wizard anjuta starts the autogen/automake process but borks part way through with the following messages:

configure.in: 8: required file './config.h.in' not found
src/Makefile.am:21 variable 'WX_LIBS' not defined

and then autoconf spews a number of possibly undefined macro errors.

I've been told I should make sure I have all the relevant dev packages installed, but I'm pretty sure I have all that I need...

Can anyone help?

---

### Post by m87 on 2005-12-28
[quote=Nikusan]The title says it all, I guess.
I'd like to get wx up and running in anjuta. I notice that anjuta has a wx template in its project wizard, which is pretty neat.
When I finish the wizard anjuta starts the autogen/automake process but borks part way through with the following messages:

configure.in: 8: required file './config.h.in' not found
src/Makefile.am:21 variable 'WX_LIBS' not defined

and then autoconf spews a number of possibly undefined macro errors.

I've been told I should make sure I have all the relevant dev packages installed, but I'm pretty sure I have all that I need...

Can anyone help?[/quote]

have you installed the wxgtk -dev packages?

---

### Post by Nikusan on 2005-12-28
Do you mean libwxgtk2.4-dev, libwxgtk2.6-dev etc?
If so, yes I have those.

---

### Post by Hendrin on 2005-12-29
Possibly missing these (I could be wrong though, never used wxwidgets/wxwindows myself):

wx2.6-headers
wx-common

---

### Post by Nikusan on 2005-12-30
No I have those too :(

---

### Post by cro.smiley on 2006-04-21
[QUOTE=Nikusan]The title says it all, I guess.
I'd like to get wx up and running in anjuta. I notice that anjuta has a wx template in its project wizard, which is pretty neat.
When I finish the wizard anjuta starts the autogen/automake process but borks part way through with the following messages:

configure.in: 8: required file './config.h.in' not found
src/Makefile.am:21 variable 'WX_LIBS' not defined

and then autoconf spews a number of possibly undefined macro errors.

I've been told I should make sure I have all the relevant dev packages installed, but I'm pretty sure I have all that I need...

Can anyone help?[/QUOTE]

I'm having the same problem.
Have you fixed it?

---

### Post by ruudiculus on 2006-04-23
Hi I'm using Anjuta for C/C++ programming too. I don't know ALL its capabilities, but you may want to define WX_LIBS (without a value) in "Settings -> Compiler/Linker settings/Defines". Then if you miss libraries things might still go wrong compiling, but it is worth a try.

Good luck!

---

### Post by Nikusan on 2006-05-20
[QUOTE=ruudiculus]Hi I'm using Anjuta for C/C++ programming too. I don't know ALL its capabilities, but you may want to define WX_LIBS (without a value) in "Settings -> Compiler/Linker settings/Defines". Then if you miss libraries things might still go wrong compiling, but it is worth a try.

Good luck![/QUOTE]

The KDevelop wx hello world project builds and runs perfectly, so I don't think it's an issue of me not having the required libs. I think I'll just give up on anjuta for now :(

---

### Post by Xanatos Craven on 2006-08-13
Hey there. I'm just going to cut to the chase here... I followed all the above suggestions and I'm still getting the exact same error this thread's starter got.

---

### Post by Daverz on 2006-08-13
Maybe this should be filed as an ubuntu bug? I don't see why any fussing around with this stuff should be neccessary, you should be able to just install the packages and go.

---

### Post by yesidh on 2006-08-24
Have anyone get it working?.

I have a similar problem but worse becuase it doesn't work nor anjuta neither kdevelop, I remenber once it was working out of the box. I appreciatte your help:

* Anjuta: I create the project with the wizard and everything goes perfect the first phase, then I do a compile with make (Shift + F11), everithing perfect, and then a build and it fails: No targets specified and no makefile found. Stop.

* Kdevelop: I did a probe in kdevelop and it work, great. 

Anyway I would like to have it running in anjuta, It likes me more. Thanks.

---

### Post by ruudiculus on 2006-08-24
Just maybe...

When you use Anjuta with a new project, it tries to compile a simple Hello World program. While doing this Anjuta generates warnings and messages of packages you still miss. Maybe you've missed one of those messages and you have to install a few more packages.

If the Hello World builds successfully, but other (bigger) projects don't, you might need to enable the RT and GTK libraries in the "Compiler and Linker Options" window. I had to do this to get things up and running.

Good luck!

---

### Post by ani5lin on 2006-09-05
I've managed to build Hello world program with Anjuta.
You need to install automake 1.9 and modify a configure.in file generated by Anjuta. 

See: 

[http://www.wxwidgets.org/wiki/index.php/Anjuta]("http://www.wxwidgets.org/wiki/index.php/Anjuta")
[http://www.linuxquestions.org/questions/showthread.php?t=422531]("http://www.linuxquestions.org/questions/showthread.php?t=422531")

---

