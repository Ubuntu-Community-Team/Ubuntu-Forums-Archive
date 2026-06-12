---
title: "Eclipse CDT &amp; software distribution?"
date: 2007-09-06
forum: Programming Talk
---

### Post by DannyW on 2007-09-06
I'm a new programmer, about to start a 4 year computer science course in London. I've been programming in KDevelop for a little while with C++ & SDL, but I found KDevelop over complicated, under documented and with poor support. I recently switched to Eclipse CDT which seems user friendly and well documented (it's a little slower than KDevelop, but my machine runs it smoothly).

I have made a simple game which has a few data files (.ttf and .png's), adding the files using the Eclipse project explorer.

How would you suggest I distribute this software? Should I look into creating a makefile to install it, or can Eclipse do this for me? If Eclipse can't do anything for me I would probably be happy to distribute just the executables and data files necessary to run the software (I'm not talking about selling the software, just sending to a friend or whatever). But this latter method isn't possible with the problem described below.

Also, when I browse to the project directory in Konqueror and try to run the executable by double clicking it it closes immediately (I'm guessing because it can't open fonts/FreeSans.ttf or something).

The directory structure is something like:
project/
project/fonts/FreeSans.ttf
project/images/image.png
project/Release/project.out

This is where Eclipse put the datafiles, and this is fine when I run from Eclipse.

Anywho, I would guess I can't run it by double clicking it in Konqueror because  Eclipse hasn't put the data in the Release or Debug subdirectories so I copy it there manually, and now this allows me to cd to the Release dir and run the program, but it still closes immediately after double clicking.

Where is it looking the font when I double click in Konqueror? I'm going to have another guess that I could fix this by making my program open the font using an absolute path rather than LoadFont( "fonts/FreeSans.ttf" ) which it does now. If this is the best way, how would I go about doing this in C++?

Thanks in advance,
Danny

---

### Post by DannyW on 2007-09-07
Anyone? How can I make this executable from the file manager?

---

### Post by ilkapo on 2008-08-21
May be it's too late but I find your post searching on Google for how to distribute the CDT Makefile.
Your problem is that when you run the application from Eclipse IDE it use the project root directory as working directory (i.e. /home/user/workspace/project) instead when you double-click from the file manager the working directory is the directory containing the executable (i.e. /home/user/workspace/project/**Debug**). You need to copy on the Debug directory (or the directory where the executable is created) all your shared files.
How you solve your distribution problem?

---

