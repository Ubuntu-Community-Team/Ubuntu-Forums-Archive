---
title: "Unable to Compile Gmote Source on Ubuntu 12"
date: 2013-09-15
forum: Packaging and Compiling Programs
---

### Post by TragicRemedy on 2013-09-15
I am running Ubuntu 12.04 64 bit.

I am having problems compiling the source code for Gmote which appears to be a "SVN" source.

The reason I need to, is to fix a bug I have with dual monitors documented here:

[http://code.google.com/p/gmote/issues/detail?id=15](http://code.google.com/p/gmote/issues/detail?id=15)

Someone posted a patch in that thread which appears to inject some code into a jar file. I downloaded and extracted the source and performed the patch successfully downloading the source from here:

[https://github.com/Gmote/Gmote](https://github.com/Gmote/Gmote)

The official source is here but I see no way to download it:

[http://code.google.com/p/gmote/source/checkout](http://code.google.com/p/gmote/source/checkout)

The problem I have is there is no. /configure or autoconfig.sh etc which is documented everywhere on the internet to compile the code. I have also tried various make commands without success.

The only readme or install instructions in the source I can find state "Add a VLC directory here to allow proper builds." Which is the 3rd party directory in the source.

My understanding is that I need a ./configure before I can use the make command, so what am I missing?

---

### Post by TragicRemedy on 2013-09-15
Did more work on this today. I attempted to create the config script manually.

From the root directory of the source code I ran autoscan > renamed configure.status to configure.in > ran autoconf > this created the configure script with quite a bit of code. I then ran the configure script and all it said was "configure: creating ./config.status".

No make files were created. :(

---

### Post by steeldriver on 2013-09-15
Hello and welcome to the forums

I don't program in java, but afaik it is not 'compiled' in the same sense as traditional source code. The svn repository you have checked out appears to contain 4 separate java projects in a form that you can import directly into the Eclipse IDE (File --> Import ... --> Existing projects into workspace) by pointing it at the unpacked gmote-read-only root directory. After that you probably want to select the particular project(s) that you are trying to 'compile' and choose Export ... to Java jar file.

[http://code.google.com/p/gmote/wiki/GmoteProjectInfo](http://code.google.com/p/gmote/wiki/GmoteProjectInfo)

[http://agile.csc.ncsu.edu/SEMaterials/tutorials/import_export/](http://agile.csc.ncsu.edu/SEMaterials/tutorials/import_export/)

[http://stackoverflow.com/questions/9323288/how-do-i-build-a-java-project-in-eclipse-to-create-an-external-jar](http://stackoverflow.com/questions/9323288/how-do-i-build-a-java-project-in-eclipse-to-create-an-external-jar)

[http://www.eclipse.org/](http://www.eclipse.org/)

---

### Post by TragicRemedy on 2013-09-15
Thanks for the nudge in the right direction.

I was able to import into eclipse and export the jar but I am not sure that is what I want to do.

The gmote server files that I am able to execute are a large collection of jar and class files. The jar file I created does not have a similar folder structure and does nothing when I run it. It does not contain any class files.

The patch changes code in the trackpadhandler.java file which appears to have a .class equivelent in the "compiled" server files I can run.

Maybe all I need is that class file eclipse generates with the modified code.... except even with build automatically turned on, and looking up the default output folder for java build..... there are no class files in my workspace in the bin directory.

---

### Post by TragicRemedy on 2013-09-21
Bump...  help :D

---

