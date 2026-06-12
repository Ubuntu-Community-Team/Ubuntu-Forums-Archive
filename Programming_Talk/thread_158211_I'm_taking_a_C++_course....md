---
title: "I'm taking a C++ course..."
date: 2006-04-10
forum: Programming Talk
---

### Post by Narpas on 2006-04-10
And the course uses MS Visual Studio. Is there a good open equivelent to this? Note that my knowledge on the subject is terribly limited. I've tried Anjuta, but it doesn't seem to have the libraries necessarry. 

Questions are:
Are the libraries included in MS Visual Studio Microsoft-only, or could I install them? I've got the Windows install discs.
If not, are there equivelent libraries available? The closer to the included libraries, the better.
I'm willing to work outside the box, but I don't know how... I expect I could run g++ through a terminal on a file made with gedit, but I don't exactly know how. Insights?

---

### Post by gerbman on 2006-04-10
[QUOTE=Narpas]And the course uses MS Visual Studio. Is there a good open equivelent to this? Note that my knowledge on the subject is terribly limited. I've tried Anjuta, but it doesn't seem to have the libraries necessarry. 

Questions are:
Are the libraries included in MS Visual Studio Microsoft-only, or could I install them? I've got the Windows install discs.
If not, are there equivelent libraries available? The closer to the included libraries, the better.
I'm willing to work outside the box, but I don't know how... I expect I could run g++ through a terminal on a file made with gedit, but I don't exactly know how. Insights?[/QUOTE]If all you're doing is writing non-gui programs, then g++ might work for you, although there are some syntactic constructions allowed in g++ that are flagged as errors in MSVS. For a g++ tutorial, see [here]("http://www.google.com/search?hl=en&q=g%2B%2B+tutorial&btnG=Google+Search"). If you're doing a lot of compilation, you might want to take a look at ``makefiles" as well (lots of tutorials out there). If you're writing anything more than simple programs it is going to be rough moving code back-and-fourth between MSVS and g++...just my guess.

---

### Post by rfruth on 2006-04-10
Is the object to master MS Visual Studio, to learn structured programming / debugging skills, code writing, or all the above and more ?

---

### Post by thumper on 2006-04-11
Open source for windows or linux?

MS have recently made their compilers free.  You can download the "express" version of visual studio after registering on their website.  It doesn't include all the GUI wizards that the professional version does - so if your course is heavily dependent on the wizards then you are out of luck anyway.

If you are using a modern(ish) VC compiler then it should be mostly standards compliant. GNU g++ is also mostly standards compliant and if you are just writing console type applications, then g++ will be fine.

---

### Post by LordHunter317 on 2006-04-11
Well, to be somewhat pedantic, they made their IDEs free, for a single language.  The compilers for .NET were always free, for the life of the platform and they had released a free C++ compiler some time in the past.

---

