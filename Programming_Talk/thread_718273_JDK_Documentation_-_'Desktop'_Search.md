---
title: "JDK Documentation - 'Desktop' Search"
date: 2008-03-07
forum: Programming Talk
---

### Post by deadimp on 2008-03-07
I'm looking for a simple [open source] application on Ubuntu/Linux in general that will be able to index and search a _local_ [offline] installation of the Java SDK documentation.

Mostly something kind of like JCreator's (the IDE we use on Windows) integrated documentation feature - ie. user opens Search window, selects 'Java Documentation' in search options, types 'Array', and various pages in the documentation are brought up.
Of course, it won't be integrated into the IDE we're using because, well, what we're using doesn't exactly have that. [Read on to see]

_Extra Extra_:
I know that Eclipse has this sort of functionality as a plugin, but we're not using Eclipse.
Why? This is for our Computer Science UIL Team Hands-On Programming Competition. We're allowed a computer (surprising, I know), in most cases a laptop, with necessary software (Java environment, IDE, ...), but no internet connection.
For those who don't know the way the competition is set up, you're given a list of ten programming tasks with descriptions, You code the program, save the file to a floppy disk (archaic, yes), and turn it in to the judges, moving on to the next task while waiting.
The main points in explaining all of this are:
. No internet - Searching via Google or something like DocJar is not an option
. The programs are contained in and compiled as a single file - Using Project-only IDEs, such as Eclipse, BlueJ, MonoDevelop, etc, just won't work for us (unless these applications have some sort of simplified single-file building solution that I don't know about).

The best IDE I've found on Linux that handles the single file setup beautifully is Geany. Alternatively, we could set up some sort of command-line 'build system' that might make it easier - especially if we learn how to debug! The other people on my team are realitvely experienced with computers.

The closest thing that I've found to this is getting the J2SE6 Documents from [this site](http://www.allimant.org/javadoc/) in Windows CHM format, getting xchm, and viewing it like that. There isn't anything necessarily bad with this method, except the documentation content is fixed to the CHM, and the information is pretty outdated.
I also Googled 'round a bit and found DocFather, but that seems like an extremely old, abandoned project of Sun's...

_Extra Extra Extra_:
For the past three years that I've done the CSUIL competition, we've been using Windows. This year I'm trying to see if we can shift towards Ubuntu, if not just for the hell of it, then to see if it can be used as a better development environment.
The first year I did it we used TextPad, which sucked, and then for the next/last two years we used JCreator, which was actually pretty good.

EDIT: Crap! Can't change the actual post title!

---

### Post by deadimp on 2008-03-10
I think I've found something that I might be able to use: [swish-e](http://swish-e.org/index.html)
I woke up my computer from hibernation, saw that I had synaptic running (after installing the java demos to try and use the jpda), and randomly decided to browse it. It was frickin' awesome.
At least if this doesn't work, I know what I can search for.

---

