---
title: "Convert dos files to unix format in a jar file"
date: 2007-04-14
forum: Programming Talk
---

### Post by joselin on 2007-04-14
Hi,

I have several java files that didn't work and seems that there is a problem with dos end on lines ^M. Is there any way to convert all the files inside a jar file to unix/linux end on line format?

Thanks

---

### Post by pbrockway2 on 2007-04-14
If there aren't many .java files involved you could unarchive them and use your favourite texteditor to replace the end of lines to something suitable, then rearchive.

If you want to process whole .jar files this way you could write a small Java application to do it.  Be aware that you can't alter the contents of a .jar files - what you have to do is create another one.  

So what you would do is recursively traverse through the .jar file and

(1) If there is a non .java file entry copy it to the destination .jar

(2) If there is a .java file entry use a BufferedReader to read it line by line (the BufferedReader will cope with any EOL terminations), then use a BufferedWriter to write the line to the destination .jar.  BufferedWriter's writeLine() method will write the correct sort of EOL for your system.

Of course the Readers/Writers will have to wrap JARInput/OutputStreams.

> I have several java files that didn't work and seems that there is a problem with dos end on lines

I've just read more closely and noticed this.  In general EOL problems shouldn't make the .jar file not "work".  Any .class file entries within the .jar will be unaffected.  But there could be a problem with resource files contained within the jar.

My remarks above should be taken to include any plain text (ie non binary) file within the jar.

Complain to whoever wrote the thing in the first place.  They must be reading lines from these resource files in a strange way.  As noted above a BufferedReader's readLine() method is EOL-agnostic.

---

### Post by phossal on 2007-04-14
> **joselin said:**
> Hi,

I have several java files that didn't work and seems that there is a problem with dos end on lines ^M. Is there any way to convert all the files inside a jar file to unix/linux end on line format?

Thanks

Why not post the errors you're getting when trying to use them?

---

### Post by ghostdog74 on 2007-04-14
the better way is to unjar them and pass each java file into dos2unix . then jar them up again.

---

### Post by joselin on 2007-04-14
> **phossal said:**
> Why not post the errors you're getting when trying to use them?


The first error where in the script that launch the app. The script have only one line:
```
java -jar whatever.jar^M
```

The output were that could not locate the jar file. 

I manually removed the ^M and runs fine, launch the program, but this program create an empty window (without controls, menus, etc). So i though that could be this issue, because all files inside jar end it's lines with ^M.

The program that i tried to launch can be located [_here_]("http://ie.archive.ubuntu.com/sourceforge/c/cr/cridmanager/"), the file is [this]("http://ie.archive.ubuntu.com/sourceforge/c/cr/cridmanager/cridmanager-1.4.3.zip"). Additionally exist a [source  file]("http://ie.archive.ubuntu.com/sourceforge/c/cr/cridmanager/cridmanager-1.4.3-src.zip") but i don't know how to compile or package into a jar file.

Could someone of you try to launch it and let me know if it works?

Thanks for the help

---

### Post by joselin on 2007-04-14
> **ghostdog74 said:**
> the better way is to unjar them and pass each java file into dos2unix . then jar them up again.

Could you point me on how to jar the files after doing the changes?

Thanks

---

### Post by pbrockway2 on 2007-04-14
I don't think you need to change the jar file.  

I couldn't download the file you linked to (tried twice).  But I went to SourceForge and downloaded cridmanager-1.4.3.zip.  I unzipped it then
> pbrockway@linuxdeskd6off:~/Desktop/crid$ java -jar cridmanager-1.4.3.jar
log4j:WARN No appenders could be found for logger (net.sourceforge.cridmanager.Settings).
log4j:WARN Please initialize the log4j system properly.
It started up OK, with icons (but all but the last two were dimmed presumably because I had no data).

Where did you get the command ending in^M?  I looked at the documentation but it was all in German (which sadly might as well be Greek to me!)  I'm using Java version 1.6.0 by the way, this may make a difference.

---

### Post by pbrockway2 on 2007-04-14
There is something strange with the zip file I downloaded.

The launch script start.sh did not have "#! /bin/bash" at the start, so I edited it.  Then when I ran it I got
> bash: ./start.sh: /bin/bash^M: bad interpreter: No such file or directoryNote the ^M!

It looks very much like it is this script that was written using DOS end of line markers.  All you have to do is correct the start.sh file (using the utility that was posted before) not the whole jar file.

Alternatively you can just run it from the command line.

---

### Post by ghostdog74 on 2007-04-14
> **joselin said:**
> Could you point me on how to jar the files after doing the changes?

Thanks

ok...until here, your problem if i understand correctly,  is the ^M in your launch script.  just do a dos2unix <scriptname> <scriptname> will do.

---

### Post by joselin on 2007-04-14
> **pbrockway2 said:**
> I don't think you need to change the jar file.  

I couldn't download the file you linked to (tried twice).  But I went to SourceForge and downloaded cridmanager-1.4.3.zip.  I unzipped it then
It started up OK, with icons (but all but the last two were dimmed presumably because I had no data).

Where did you get the command ending in^M?  I looked at the documentation but it was all in German (which sadly might as well be Greek to me!)  I'm using Java version 1.6.0 by the way, this may make a difference.


I attach an screenshot with how can the application looks like in my computer. Note that I using java version 1.6.0 too and I launch the file from the command line.

---

### Post by joselin on 2007-04-14
> **ghostdog74 said:**
> ok...until here, your problem if i understand correctly,  is the ^M in your launch script.  just do a dos2unix <scriptname> <scriptname> will do.

Nop, I manually correct the startup script and didn't work. And as I told in my last post, running the command in a terminal didn't work properly too.

---

### Post by pbrockway2 on 2007-04-15
It looks from your screenshot that the application is running - just not correctly :(

One difference between your setup and mine is that you're using Beryl.  A bit of a look around found this web page [http://wiki.beryl-project.org/wiki/Java](http://wiki.beryl-project.org/wiki/Java)  They say that "Java SE 6 gui applications such as Netbeans and possibly other AWT and Swing applications do not display correctly when using Beryl".  The fix looks like quite a lot of work, especially for 1.6.0.  Perhaps you could try without Beryl.

For what it's worth I've attached a screenshot of what I get.  I haven't posted here much so I hope I get the image attachment business right...

---

### Post by joselin on 2007-04-15
> **pbrockway2 said:**
> One difference between your setup and mine is that you're using Beryl.  A bit of a look around found this web page [http://wiki.beryl-project.org/wiki/Java](http://wiki.beryl-project.org/wiki/Java)  They say that "Java SE 6 gui applications such as Netbeans and possibly other AWT and Swing applications do not display correctly when using Beryl".  The fix looks like quite a lot of work, especially for 1.6.0.  Perhaps you could try without Beryl.

That were the issue. Changing to metacity the program run fine.

Thanks a lot for you help.

---

### Post by pbrockway2 on 2007-04-15
You're welcome.

---

