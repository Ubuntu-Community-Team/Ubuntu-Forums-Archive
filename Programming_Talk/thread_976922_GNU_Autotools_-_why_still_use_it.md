---
title: "GNU Autotools - why still use it?"
date: 2008-11-09
forum: Programming Talk
---

### Post by samjh on 2008-11-09
Does anyone here agree with me that GNU Autotools build system is just too complicated?

Why is it that GNU and so many other FOSS projects continue to use this ridiculously hard-to-use system for their build management?

Wouldn't the FOSS community be better served by more modern and easier build management systems like Ant and SCons?  What is slowing the adoption of these more modern systems?  Some major FOSS projects are using them now, but GNU Autotools remain as the dominant force, and the required system for GNU projects.

---

### Post by Delever on 2008-11-09
From newbie perspective (mine):

I learned it and can use it for my needs. If I share my projects using Autotools, I know others will understand it's structure without many problems.

Since I already know the basics of the most popular build system, it makes less sense to learn something else. Furthermore, I faced some other build systems (on windows, because on ubuntu I rarely have to compile libraries), like bjam for boost and Ant for rabbitmq. Are they better? At that moment, it seemed not, because I had to read additional documentation to get started compiling things.

---

### Post by winch on 2008-11-09
I've only used scons once and it was a pain. It looked for and installed libs in /usr/libs64 on 64bit systems yet the distro I was using used the normal /usr/lib dir. This meant patching the SConstruct file and setting the search path for all the libs the program needed.

Ant is java which you don't really want to install just to build something.

Autotools may be a pain to set up but works well for people building the software. Everybody knows how to use it, it works pretty much anywhere and doesn't have any large dependabilities.

---

### Post by WW on 2008-11-09
> **samjh said:**
> Does anyone here agree with me that GNU Autotools build system is just too complicated?

Yes.
> **samjh said:**
> 
Why is it that GNU and so many other FOSS projects continue to use this ridiculously hard-to-use system for their build management?

Because, once it is setup, it works reasonably well, and it is fairly well standardized.  People are familiar with *./configure && make && make install*.  Options such as --prefix are standard, and people know what it means.  Uninstall is also usually as easy as *make uninstall*.  Familiarity and standardization are important.

For comparison, I was shocked and amazed to find that the python build package distutils did not provide an uninstall option.
> **samjh said:**
> 
Wouldn't the FOSS community be better served by more modern and easier build management systems like Ant and SCons?

There is also cmake.  It is nicer than autotools, but still ugly, IMHO--lots of cryptic, undocumented, side-effect laden macro programming.

---

### Post by ZuLuuuuuu on 2008-11-09
I didn't use autotools for a project but used them to compile some software. The only complaint of me is that you have to install MinGW & MSYS to use autotools on Windows. MinGW is not bad but MSYS is ugly/slow/impractical solution and it just doesn't feel native. And Cygwin is worse...

I wish there would be a Windows binary for autotools which installs the compilation system to your computer and you use it from your command prompt anywhere, anytime; not a less-featured MSYS terminal with Linux imitated folder structure.

---

### Post by CptPicard on 2008-11-09
Yes, autotools is one of the most awful contraptions around. Seriously, I have never learned to use it beyond some really basic incantations (and is one of those things that I'm not ashamed of not grokking), and is one of the main factors that has always been putting me off from doing larger C/C++ projects -- Java is a much nicer project environment ;)

I can understand that a lot of the pro-autotools argumentation is similar to the pro-shell or pro-C++ argumentation -- "it's available standard anywhere", "I learned to use it and am invested in it so I won't complain", "oh, but it CAN be done by *<long cryptic wizard explanation>*, so there!", "we're just adding layers and layers of stuff on top of old stuff and can't really redo everything from scratch"...

I really like SCons, but I'm sure someone will just claim that because you can't be sure that Python is always there, one can't rely on it... :)

---

### Post by samjh on 2008-11-10
> **CptPicard said:**
> Yes, autotools is one of the most awful contraptions around. Seriously, I have never learned to use it beyond some really basic incantations (and is one of those things that I'm not ashamed of not grokking), and is one of the main factors that has always been putting me off from doing larger C/C++ projects -- Java is a much nicer project environment ;)Same with me about Autotools.  I know the bare-bones basics, but haven't made any progress in learning it more deeply.

> "it's available standard anywhere"Standards serve a purpose.  When it no longer serves it well, or others serve that same purpose better, then it needs to be replaced.

> I really like SCons, but I'm sure someone will just claim that because you can't be sure that Python is always there, one can't rely on it... :)A problem seems to be that the alternative build systems don't have a dominant player.  I don't think SCons is distinctively more popular than CMake, for example.  So that is a problem if Autotools is to be replaced by an alternative.  Related to that, GNU requires Autotools to be used, and as GNU has many many projects under its portfolio, Autotools benefits from a dominant and entrenched market share.

Python is installed by default on all major Linux distros, so the argument that "you can't be sure that Python is always there" is grasping at straws. :)

---

### Post by WW on 2008-11-10
> **samjh said:**
> 
Python is installed by default on all major Linux distros, so the argument that "you can't be sure that Python is always there" is grasping at straws. :)
Unfortunately, Linux users are only small fraction of the potential users of FOSS.  Fortunately, these days it is pretty easy to get python installed on Windows, so perhaps scons has a chance to increase its "market share".

---

### Post by thk on 2008-11-10
Yes, it needs to go. Creating new autoconf rules is hugely time consuming and error prone. A python-based replacement is the obvious choice. I want it not only to manage configuration and build, but also to emit ready-to-install packages (deb, rpm, etc.)

---

### Post by Desty on 2008-11-10
> **WW said:**
> Unfortunately, Linux users are only small fraction of the potential users of FOSS.  Fortunately, these days it is pretty easy to get python installed on Windows, so perhaps scons has a chance to increase its "market share".
I would expect that many more users have Python on Windows than MinGW/gcc/automake/etc; since Python is required for lots of non-programmer-specific apps like Mnemosyne, Blender, err... etc. I'm not sure of much general purpose software that demands that MinGW and a C/C++ compiler and automake tools be installed in Windows :D

---

### Post by ZuLuuuuuu on 2008-11-10
> **Desty said:**
> I would expect that many more users have Python on Windows than MinGW/gcc/automake/etc; since Python is required for lots of non-programmer-specific apps like Mnemosyne, Blender, err... etc. I'm not sure of much general purpose software that demands that MinGW and a C/C++ compiler and automake tools be installed in Windows :D

Also installing Python and SCons on Windows is far more easier than installing autotools environment.

I am surprised that a lot of replies are supporting the switch to a moderner solution than autotools. I expected %50 %50 arguments "for" and "against" :D

Then, let's make the switch! :D

---

### Post by Desty on 2008-11-10
> **ZuLuuuuuu said:**
> Also installing Python and SCons on Windows is far more easier than installing autotools environment.

I am surprised that a lot of replies are supporting the switch to a moderner solution than autotools. I expected %50 %50 arguments "for" and "against" :D

Then, let's make the switch! :D
Yeah, and in (a good) Linux, installing Python looks something like "apt-get install python", and it's not a huge install.
Having used SCons and thought "hey, not too bad", I'd certainly suggest trying it over the ugliness of automake/aclocal/configure/m4/pain/etc. Writing build scripts in a proper programming language rather than some arbitrary, unexpressive thing makes sense.

---

### Post by snova on 2008-11-10
I hate Autotools. It's a conglomeration of ugly mess upon ugly mess, with macro programming and support for deprecated shells added in. I hope never to bother with it.

I like SCons. I've never tried building a large project with it, but I have every belief that it could handle it beautifully. It's dependency mechanism is a great improvement over Make. It has vast support for every tool I've never heard of. Admittedly, I've never used many of its features, but I have high expectations nonetheless.

CMake reminds me uncomfortably of Autoconf. Why another custom language? And especially one that generates Makefiles, essentially doing the same thing as Automake? Ugh. Sadly for me, CMake seems to be gaining more ground than SCons.

As for "Python isn't always there", so are most of the dependencies a modestly complex program is likely to have. That and Python is used in so many places already it's almost guaranteed to be installed, except for on Windows.

Now, "Autotools is standard and everybody knows how to use it". This is true. As much as I find alternative build systems superior, it very slightly annoys me to find something unfamiliar, or worse, something badly written that doesn't support --prefix well enough.

On the other hand, I hate no end the mass of support files Autotools requires in your project. I like a clean directory tree and all the infrastructure you have to copy around drives me batty. And then it generates even more when you use it!

---

