---
title: "Makefile with Subdirs"
date: 2009-06-09
forum: Programming Talk
---

### Post by xnevermore on 2009-06-09
I have a directory structure as follows:
program/
|-src/
|-build/

I would like to write a simple Makefile which compiles all .c source files in the src/ subdir and places the resulting .o module files in the build/ subdir. The main program executable should also be placed in the build directory.

Can anyone show me a simple way of doing this? It should probably use wildcards, because I don't see any reason why I should have to maintain a list of all of the source/module files I want compiled and linked, it should just compile/link them all.

---

### Post by dwhitney67 on 2009-06-09
See this [reply]("http://ubuntuforums.org/showpost.php?p=7419953&postcount=3") to someone who had similar requirements as yours.

---

### Post by xnevermore on 2009-06-09
The example given in that post seems more complicated than it needs to be. Are the embedded shell scripts really necessary after all (i.e. patsubst and find)? It seems like make should have all of this functionality built-in. Plus, I don't need the make-repo/buildrepo functionality either.

I guess my question is, does anyone know a simpler way of doing this? I'd like to see a small, concise example of compiling from the src/ subdir and into the build/ subdir.

Thanks.

---

### Post by dwhitney67 on 2009-06-10
> **xnevermore said:**
> The example given in that post seems more complicated than it needs to be. Are the embedded shell scripts really necessary after all (i.e. patsubst and find)? It seems like make should have all of this functionality built-in. Plus, I don't need the make-repo/buildrepo functionality either.

I guess my question is, does anyone know a simpler way of doing this? I'd like to see a small, concise example of compiling from the src/ subdir and into the build/ subdir.

Thanks.
I'm the one that posted that reply in the other post; if there was an easier way, I would have suggested it.

I'm not an expert with respect to Makefiles, but I have been developing them for over 20 years.

The issue that is complicating your world is that you stipulated that you wanted your source files in one directory, and the produced object files in another.  If you merely would "marry" the two into the same directory, then the Makefile would be much easier.

You have not even considered the ramifications of checking for dependencies before compiling a source file, thus if you are thinking of compiling a source file in place, then moving (using either the 'mv' or 'install' command) the object file to another directory, then you will be for a big surprise when you attempt to perform dependency checks.

Use the Makefile I provided in that post, or alternatively rethink your requirements, and live with the object files in the same directory as the source files.  If you go with the latter suggestion, let me know and I will throw together a simple Makefile for you.

---

