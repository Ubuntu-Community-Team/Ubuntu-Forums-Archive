---
title: "Differences between compiling and building in geany (C++)"
date: 2008-02-11
forum: Programming Talk
---

### Post by sujinge9 on 2008-02-11
Hi,

New to linux and the geany IDE and I'm just wondering what's the difference between compiling and building. In Dev C++ I would just hit compile and the compiler would work it's magic, but in geany, compile does nothing just perform as a debugger or something, instead, you have to build then execute. 

My reason for asking this is because I would like to be able to use compile to build my programs or somehow incorporate the build button into the tool bar. 

Thanks.

---

### Post by amingv on 2008-02-11
Compile creates the object files, while build links and creates an executable.

There's 3 steps in compiling C++ code (and mostly any other languaje), preprocessing, compiling and linking.

[http://geany.uvena.de/manual/0.13/index.html#build-system](http://geany.uvena.de/manual/0.13/index.html#build-system)

---

### Post by sujinge9 on 2008-02-12
Yes, I know that, but I just want to know why I can't compile then execute instead of having to build then execute while "compiling" seems to do nothing. 

And I have seen the options, but there is no option to put "build" onto the toolbar.

---

### Post by slavik on 2008-02-12
as amingv said, compiling only compiles the current file (in case you have a single source file from a project and just need to recompile that one file) while "building" in geany makes it compile other related files and call the linker to link them.

and as you said, compiling can be used as a quick syntax checker. :)

EDIT: as you also said, no "build button" is also messed up, you should file a bug for it :) (I got used to pressing F9 :))

---

### Post by amingv on 2008-02-12
> **sujinge9 said:**
> Yes, I know that, but I just want to know why I can't compile then execute instead of having to build then execute while "compiling" seems to do nothing. 

And I have seen the options, but there is no option to put "build" onto the toolbar.

No you didn't :). You said compile was some debugging function, which it isn't.

I just installed geany to check about the build button not being there, and it isn't (quite weird). Still, you can use F8 and F9 to compile and build respectively.

I'll check the source to see if I can find a hack to it...

---

### Post by amingv on 2008-02-12
Whoa! Source in C. Backing off...

But If you really want to use those buttons, there's a quick dirty hack you can use...

Go to Build>Set Includes and Arguments:

Change the compile line to
```
g++ -Wall -o "%e" "%f"
```
and click OK. Now your compile button will compile and link in one step.

Notice that in doing this you will not get an object file (if you wanted one), Just an executable.

---

### Post by sujinge9 on 2008-02-13
> **amingv said:**
> Whoa! Source in C. Backing off...

But If you really want to use those buttons, there's a quick dirty hack you can use...

Go to Build>Set Includes and Arguments:

Change the compile line to
```
g++ -Wall -o "%e" "%f"
```
and click OK. Now your compile button will compile and link in one step.

Notice that in doing this you will not get an object file (if you wanted one), Just an executable.

Sorry for the misstatement in my initial post. But since I'm just starting programming, I don't believe I will need a object file (not sure what it does, could you tell me?), and thanks for the quick fix, I'll give it a whirl in a minute.

---

### Post by slavik on 2008-02-13
object file = assembly before being linked together and translated into machine language.

very nice when you want to check the difference between i++ and ++i or somesuch :)

---

### Post by amingv on 2008-02-13
Object Code is the set of instructions from your program translated to machine language (not assembly). You can't run it because it needs to be linked to other libraries for the OS to be able to use it.

Picture's worth a thousand words:

[IMG]http://www.webopedia.com/FIG/COMPILE.gif[/IMG]

---

### Post by vishzilla on 2008-02-14
> **amingv said:**
> Object Code is the set of instructions from your program translated to machine language (not assembly). You can't run it because it needs to be linked to other libraries for the OS to be able to use it.

Picture's worth a thousand words:

[IMG]http://www.webopedia.com/FIG/COMPILE.gif[/IMG]

Nice!
Compiling creates one obj file for each cpp file.  Building, which includes compiling, also links all obj and lib files into an executable file

---

