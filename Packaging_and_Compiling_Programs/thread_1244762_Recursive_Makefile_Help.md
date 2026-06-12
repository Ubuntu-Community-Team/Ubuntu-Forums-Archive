---
title: "Recursive Makefile Help"
date: 2009-08-19
forum: Packaging and Compiling Programs
---

### Post by KeilanS on 2009-08-19
Hey all,
 
I have a question about how to get certain behavior out of a Makefile.
 
I am working on a project that basically has 2 main sections, various classes, and then a program that makes use of those. I am trying to split it into a few directories, as follows:
 
MainDir
MainDir/Classes (contains my test files for the classes)
MainDir/Classes/src (contains various .cpp and .h files)
MainDir/Project (contains the main program I'm working on)
MainDir/Project/src (contains various .cpp and .h files)
 
Basically I want to know how to get a Makefile that can do the following:
-When called from MainDir, it compiles both the class test files and the main program
-When called from MainDir/Classes, it compiles the class test files
-When called from MainDir/Project, it compiles the main program
 
So how would I go about doing this? I'm guessing it will be some sort of recursive Makefile implementation, but I really don't know much about Makefiles and could use some guidance on how to do this. Also, I'd prefer to do it using standard GNUMake, no plug-ins or improved versions (if any exist).
 
Edit: I forgot to mention, the classes in MainDir/Project/src and dependant on files in MainDir/Classes/src

Thanks,
-Keilan

---

### Post by KeilanS on 2009-08-23
Hmmm, so am I to assume this is not doable (or not easily doable)? Or did I post in the wrong forum?

---

