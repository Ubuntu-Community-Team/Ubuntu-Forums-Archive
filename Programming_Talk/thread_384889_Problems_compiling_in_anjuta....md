---
title: "Problems compiling in anjuta..."
date: 2007-03-15
forum: Programming Talk
---

### Post by some_random_noob on 2007-03-15
I followed this ([http://www.wxwidgets.org/wiki/index.php/Anjuta](http://www.wxwidgets.org/wiki/index.php/Anjuta)) tutorial and edited configure.in but it still won't compile. I press shift+F11 and it just says...

Building the whole project
make
make: ** no targets specified and no makefile found. stop.
completed... unsuccessful

... what does it mean by no targets specified and what the hell is a makefile and why wasn't one automatically created in the first place? This is a wxwindows application thingymcbob, and I haven't even tried writing my own code - what's already there won't even compile.

Suggestions?

---

### Post by anansi on 2007-03-20
Ah yes, this problem is fimiliar

Anjuta naturally makes a file called main.cc, which is the file that has the main method.

You must be aware that the makefile must compile and create the object file for this file. Check if your makefile has it in. If you still have problems, plz post your makefile to this thread, so we can take a look

hth

---

### Post by Greykrrr on 2007-03-20
I don't know if this goes for wxwidgets but for other projects you need to configure the project for the makefile to be created. It's in the build menu.

Also if you add files to your Anjuta project make sure you run autogen (also from build) to update you makefile. Otherwise Anjuta won't link you newly included file even though its part of the project.

---

### Post by some_random_noob on 2007-03-21
Thanks, I'll take that advice... my stepdad has been telling me about makefiles and all that crazy **** which happens in C... 

I feel stupid asking :( ... but then again, what kind of IDE comes without clear instructions? Time for another FAQ thread?

**edit:** Well, I keep getting the same error and if I play around a bit more it just keeps saying I need to download more files. Funny that, I downloaded anjuta and tried to compile. That didn't work, I spent an hour and a half downloading more files and now it still doesn't work. I don't know where in the makefile I need to add main.cc and I've checked out project configuration etc etc... still, nothing... should I give up or what? Any good tutorials? In project configuration it has "makefile.am" in one of the windows. main.cc is already in that. The actual makefile.am has a bunch of crap in it, I did an include command for main.cc and still nothing. If I try something new then I just get new errors...

---

### Post by Greykrrr on 2007-03-21
> **some_random_noob said:**
> Thanks, I'll take that advice... my stepdad has been telling me about makefiles and all that crazy **** which happens in C... 

I feel stupid asking :( ... but then again, what kind of IDE comes without clear instructions? Time for another FAQ thread?

Not at all. Are you using Anjuta from a clean install? Because another thing which I think is poorly documented in Anjuta is that it does not install all the stuff you need to compile projects automatically. The way I managed to do was to create an empty project with a main file and try to do configure and build. Then when it complains that a certain package is missing (like autoconf and automake and all that) go use synaptic to install it. After six or seven runs like this all dependencies where finally satisfied and I could compile my project.

My best guess now that you have something you are already working on is to create a new project with just "hello world" program in main and see if that will compile. If it will, create new project and import you source and header files into it and try again.

If it won't try and copy the errors here to see if anyone can figure out what they mean.

---

