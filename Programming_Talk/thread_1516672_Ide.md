---
title: "Ide"
date: 2010-06-24
forum: Programming Talk
---

### Post by l3ecl on 2010-06-24
Is there an IDE that produces make files so I don't have to make my own? 
Sounds simple enough eh =D

---

### Post by BenAshton24 on 2010-06-24
I don't think that there is... You could try this though: [http://sourceforge.net/projects/make-generator/](http://sourceforge.net/projects/make-generator/)

---

### Post by trent.josephsen on 2010-06-24
Not to my knowledge.  To build a project, you need more information than is contained within the source files alone, so I'm not sure how it would be possible to automatically write a makefile (or set of makefiles) for an existing project.  How big a project are you looking at?

---

### Post by Simian Man on 2010-06-24
This doesn't exactly answer your question, but Id' recommend scons instead of make.  Unlike make, scons is smart enough to figure out dependencies between files on its own.  Writing a scons script for a project is usually pretty trivial (and usually doesn't have to be changed when you change the projects structure).  I will never write makefiles by hand again - what a pain.

---

### Post by Le-Froid on 2010-06-24
You can try netbeans, I think they do that stuff for you.

---

### Post by pbrane on 2010-06-24
Anjuta will create the configure scripts and makefiles.

---

