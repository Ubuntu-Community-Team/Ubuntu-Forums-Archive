---
title: "How to port g++ programs to MS/Mac?"
date: 2008-09-03
forum: Programming Talk
---

### Post by akbeancounter on 2008-09-03
Hey folks,

I'm currently taking a C++ programming class, my first serious attempt at learning a programming language.  I know a few things in BASIC, Javascript, & Ruby, but I've never really made anything terribly complex.  They've mostly been monkey-see-monkey-do projects.

I run Hardy Heron and gcc at home, but as you might imagine, most of the computers at the University run WinXP.  When I compile my programs in gcc, they execute fine in Ubuntu, but Windows just identifies them as "file" and doesn't know how to open them.  Is there something I need to do while or after compiling so that other OS'es will know what these files are and how to run them?

FWIW, we're not talking about terribly complicated programs yet; we're in the second week of class, so my most complex project so far is a Fahrenheit - Celsius converter.  This isn't a class requirement, either; the requirement is that the program runs on the department's Linux server, so I think I'm covered there.  I'm just interested in being able to write programs, however basic, that'll run in Windows or Mac.

-- A.

---

### Post by LaRoza on 2008-09-03
You have to recompile them for Windows or OS X.

Since you are already familiar with gcc (g++), you can use them in Windows and in OS X.

[http://www.mingw.org/](http://www.mingw.org/)

[http://developer.apple.com/tools/gcc_overview.html](http://developer.apple.com/tools/gcc_overview.html)

If you want to have a portable compiler (meaning, you can use it on any Windows box), [http://sourceforge.net/projects/devcpp-portable](http://sourceforge.net/projects/devcpp-portable) (it is an IDE, but it also uses mingw, which you can use through the command line)

---

### Post by akbeancounter on 2008-09-03
> **LaRoza said:**
> You have to recompile them for Windows or OS X.

I'd kind of suspected that.  Thanks for the quick response!

-- A.

---

### Post by cmay on 2008-09-03
> I run Hardy Heron and gcc at home, but as you might imagine, most of the computers at the University run WinXP. When I compile my programs in gcc, they execute fine in Ubuntu, but Windows just identifies them as "file" and doesn't know how to open them. Is there something I need to do while or after compiling so that other OS'es will know what these files are and how to run them?
you have to just use standard c library and compile it on each platform. and dont use too long filenames. i have still the same first cpp files on back up i did on winXP and they compile under linux just the same.a good tool on windows is devcpp which is free and uses gcc as a port from a project called mingw.i dont know about mac however. you have to ask someone else.

---

### Post by LaRoza on 2008-09-03
> **cmay said:**
> you have to just use standard c library and compile it on each platform. and dont use too long filenames. i have still the same first cpp files on back up i did on winXP and they compile under linux just the same.a good tool on windows is devcpp which is free and uses gcc as a port from a project called mingw.i dont know about mac however. you have to ask someone else.

Way too late ;)

---

### Post by cmay on 2008-09-03
> Way too late 
yes i saw that:)
i am just to lousy at spelling so it takes too long.

---

### Post by LaRoza on 2008-09-03
> **cmay said:**
> yes i saw that:)
i am just to lousy at spelling so it takes too long.

That's ok. English is a spelling nightmare. It is the hardest aspect of the language I believe.

For future reference, it is "with" not "whit". It is just something that bothers me, nothing personal :-)

---

### Post by cmay on 2008-09-03
> For future reference, it is "with" not "whit". It is just something that bothers me, nothing personal
i will try keep that advise -> with <- me from now on.
i also always spell you "yuo " the first time . its how the keys are arranged on my keyboard and after typing then i have to correct the errors i see. and so thats why i am always too late:)

---

### Post by tbunix on 2008-09-03
Visual C++ Express is a free Win IDE also
[http://www.microsoft.com/express/vc/](http://www.microsoft.com/express/vc/)

---

### Post by LaRoza on 2008-09-03
> **cmay said:**
> i will try keep that advise -> with <- me from now on.
i also always spell you "yuo " the first time . its how the keys are arranged on my keyboard and after typing then i have to correct the errors i see. and so thats why i am always too late:)

I often misspell certain words also. Typing them correctly just makes you better in the long run anyway.


> **tbunix said:**
> Visual C++ Express is a free Win IDE also
[http://www.microsoft.com/express/vc/](http://www.microsoft.com/express/vc/)
Free in that it doesn't cost anything, but it is hardly free otherwise.

It is also rather large and no something you can just download. It is Windows only, and it is lacking many features in the non-free Visual Studio.

---

### Post by Sinkingships7 on 2008-09-03
An alternative (for Windows, at least) is to install [Dev-C++]("http://sourceforge.net/project/downloading.php?groupname=dev-cpp&filename=devcpp-4.9.9.2_setup.exe&use_mirror=voxel") through WINE. It works perfectly, uses the MinGW compiler (so contains most Windows-only libraries), and most importantly, compiles Windows native .exe files. That link will bring you directly to the download. The download page is [here]("http://www.bloodshed.net/dev/devcpp.html"), if you want it.

EDIT: Just re-read LaRoza's post. She seems to have the same idea as me. *fails*

---

### Post by LaRoza on 2008-09-03
> **Sinkingships7 said:**
> An alternative (for Windows, at least) is to install [Dev-C++]("http://sourceforge.net/project/downloading.php?groupname=dev-cpp&filename=devcpp-4.9.9.2_setup.exe&use_mirror=voxel") through WINE. It works perfectly, uses the MinGW compiler (so contains most Windows-only libraries), and most importantly, compiles Windows native .exe files. That link will bring you directly to the download. The download page is [here]("http://www.bloodshed.net/dev/devcpp.html"), if you want it.

That is in the first response (although it is the portable version)

---

### Post by tbunix on 2008-09-03
> **LaRoza said:**
>  
...
Free in that it doesn't cost anything, but it is hardly free otherwise.

It is also rather large and no something you can just download. It is Windows only, and it is lacking many features in the non-free Visual Studio.

free as in no dinero is the most important definition for me:)

I work for a non-profit, no budget, and used the express editions to develop many apps for them.

Never could talk them into going Linux only though - sigh

---

### Post by WW on 2008-09-03
> **akbeancounter said:**
> 
I run Hardy Heron and gcc at home, but as you might imagine, most of the computers at the University run WinXP.  When I compile my programs in gcc, they execute fine in Ubuntu, but Windows just identifies them as "file" and doesn't know how to open them.  Is there something I need to do while or after compiling so that other OS'es will know what these files are and how to run them?

If you want to  compile on Linux and run the compiled program in Windows, you can use a cross-compiler.  Check out my posts (including an example of cross-compiling a "Hello, world!" program) in [this thread](http://ubuntuforums.org/showthread.php?t=724495).  The example in that thread is C, but there is a corresponding C++ cross-compiler, too.

---

### Post by akbeancounter on 2008-09-03
> **tbunix said:**
> Visual C++ Express is a free Win IDE also

That's what we're using in the classroom, so I have a copy on my Win machine.*  We have full-version Visual Studio licenses for the whole class, but just one disk, so I'll have to wait my turn.  Still, I prefer to do most of my day-to-day stuff in Linux.  I care more about free (speech) than free (beer), although I can't say I absolutely insist on either.

-- A.
* My wife and I recently moved, so we've dug up our old computers, and we also decided it was time to upgrade.  Between the two of us, we have seven computers, ranging from a quad-core gaming rig to a 350MHz Pentium II with no hard drive.

---

### Post by LaRoza on 2008-09-03
> **tbunix said:**
> free as in no dinero is the most important definition for me:)

I work for a non-profit, no budget, and used the express editions to develop many apps for them.

Never could talk them into going Linux only though - sigh

You are restricted to what you can make with it (read the license). Not worth using. It is just a lure to get students (who can't afford VS) to get hooked.

---

### Post by tbunix on 2008-09-03
The license does not allow one to make a web service and then charge to use the service.
(not sure why?)

It does allow the creation and sale of commercial applications.

Of course it promotes and pushes the MS universe but most people develop sales resistance early in life in this modern age.


I am not pro VS,Win,MS in general
just offering a cheap and easy option to a student - unless they don't already have a Win license.

If the prof and the rest of class are using VS then...

edit
no add-ons or extensions are allowed - not an issue in a first semester class I wouldn't think.
no class diagrammer or class debugger either - which is a real nice-to-have though

---

