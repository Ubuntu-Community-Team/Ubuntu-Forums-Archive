---
title: "Executable &amp; libraries in one folder, but force it's output into different folder"
date: 2014-08-09
forum: Programming Talk
---

### Post by wolfgentleman on 2014-08-09
I have a set of binaries, 2 regular and 3+ libraries. Some libraries are in sub-folders. I want to launch the main binary in such a way that it places any files it creates into a folder above it. Here is a generic layout before and after the run.

Before:
[TABLE="width: 300, align: left"]
[TR]
[TD][FONT=fixedsys]BaseDir[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]exec[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]lib1.so[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]libDir[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]library1a.so[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]library1b.so[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]textfile.txt[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]OtherDir[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][/TD]
[/TR]
[/TABLE]
[HR][/HR]
After (how it is now):
[TABLE="width: 300, align: left"]
[TR]
[TD][FONT=fixedsys]BaseDir[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]exec[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]lib1.so[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]libDir[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]library1a.so[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]library1b.so[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]textfile.txt[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]someDir[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]generatedFile.txt[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]otherGeneratedFile.txt[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]OtherDir[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][/TD]
[/TR]
[/TABLE]
[HR][/HR]
After (how I want it):
[TABLE="width: 300, align: left"]
[TR]
[TD][FONT=fixedsys]BaseDir[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]exec[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]lib1.so[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]libDir[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]library1a.so[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]library1b.so[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]textfile.txt[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]OtherDir[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]someDir[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]generatedFile.txt[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=fixedsys]
[/FONT][/TD]
[TD][FONT=fixedsys]otherGeneratedFile.txt[/FONT][/TD]
[TD][/TD]
[/TR]
[/TABLE]
[HR][/HR]
So, how can I launch it in such a way that it writes/reads generated files/folders to 'OtherDir', but still use the libraries and run the other executable (which is in a sub-directory of 'BaseDir') without linking the entire contents of 'BaseDir' into 'OtherDir'. I just so everyone knows: this is a closed source and commercial program that, with the permission of the developers, I am making a deb package for. The files it generates are databases and uploaded content, of which would get destroyed on an upgrade - I did it without backing up the folder and poof...

---

### Post by ofnuts on 2014-08-09
The setup is totally non-Unixish. Even on Windows now it's a capital sin to mix user data and executable code in the same directories.... if only because as you saw this often puts your data in jeopardy.

You don't tell us why it writes files in specific directories. Is it because it is the current directory when it starts? Or because it finds it using the location of the executable itself? If the latter there are likely ways to trick it using links in the proper directories. Typically you would set up a directory for data and put in it links to the executable files installed elsewhere. This way you can put th executable files in a public place, and keep the data separately (and each user with his own set of data). Of course you would start the application using the "user" links.

---

### Post by wolfgentleman on 2014-08-09
> **ofnuts said:**
> The setup is totally non-Unixish. Even on Windows now it's a capital sin to mix user data and executable code in the same directories.... if only because as you saw this often puts your data in jeopardy.
If only it was punishable :p

> **ofnuts said:**
> You don't tell us why it writes files in specific directories. Is it because it is the current directory when it starts? Or because it finds it using the location of the executable itself? If the latter there are likely ways to trick it using links in the proper directories.
I didn't say because I don't know... Let me cd to the external directory and maybe run it using the relative path.
UPDATE: Running it with a relative path made it balk because it did not find the libs.
UPDATE 2: Tried linking the libraries, but it still complained.
UPDATE 3: I had an idea, but it just seems so sloppy... I could run it, kill it, move the generated files, and symlink them back...

> **ofnuts said:**
> Typically you would set up a directory for data and put in it links to the executable files installed elsewhere. This way you can put the executable files in a public place, and keep the data separately (and each user with his own set of data). Of course you would start the application using the "user" links.
Unfortunately, they didn't do it that way. As stupid as it is... And BTW those files are system wide, as it is a service that provides a server.

---

### Post by ofnuts on 2014-08-10
> **wolfgentleman said:**
> If only it was punishable :p

It is punished. Misbehaving software like this gets bad press. Sooner or later is means some sale going to the competition (which could come from some developer fed up with their stuff and deciding to make his own).

> **wolfgentleman said:**
> Unfortunately, they didn't do it that way. As stupid as it is... 

If they are really interested in getting a .deb, then they could tell you how they locate the files and then you could devise some way to keep them happy. Otherwise, they aren't interested in having a .deb, in which case see my remark above.

---

### Post by dwhitney67 on 2014-08-11
Just write a script to take care of the undesirable nuances of the executable program.  For example:

```

#!/bin/bash

LD_LIBRARY_PATH=$PWD:$PWD/libDir ./exec

if [ $? -eq 0 ]; then
    mv someDir otherDir
    mv otherGeneratedFile.txt otherDir
fi

```

---

