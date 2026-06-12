---
title: "Demand for gmake?"
date: 2008-06-30
forum: Packaging and Compiling Programs
---

### Post by rivera151 on 2008-06-30
I think I'm not searching right, because I can't find a program that can handle a task I do frequently and although trivial, I think it should be automated.

This is what I figure should be a basic framework.  Say, a gui selection (icon, menu, etc.) prompts the user to select an archive (.tar.gz) that contains a standard make package.  The program 
[LIST=1]
[*]unzips the archive to /tm
[*]runs the configure script
[*]runs make
[*]runs make install (sudo of course)
[*]copies the archive to some directory (say /usr/local/src/(program_name))
[*]Can later scan through the source copied to the directory in the last step so we can run "make uninstall" if we want to
[/LIST]

So basically, its like a package manager, but for source code (tarballs).

I would imagine such a project with a plugin type architecture (say svn or cvs plugin, with automake support also pluggable, and other things).  Down the road, maybe a plugin that can scan through Makefiles and allow one to read available variables and set them.  Ok thats like waaay out there, but it would be nice.

One important feature would be some tips in a wizard style interface that tells you how to do the step in the command line.  This would be good for newbies, since they are sometimes intimidated with the task of compiling a source tarball and don't know where to start.  This program might help them get the task done and learn how to do it themselves in the future too.

Another (advanced development stage) feature would be to scan the "configure" output when it exits abnormally and try to guess the missing package name, search for it via apt-cache, and display search results in a checkbox style inteface, so that the user can select the packages from the gui and the program can then "configure" again, ..., n times. 

I like to program in my spare time and started working on something like this.  However, if you really think I'm wasting my time because there's something else like this, or, if you think you could give me some pointers on making the code publicly available (I've never coded in a group, so there you go) to ubuntu developers, then drop a line.

Ah, almost forgot.  I'm coding in Java-SWT, because I like it just as much as C#, and its so portable.  But I'm convinced the code can be easily ported to something like C#.

---

