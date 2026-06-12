---
title: "Geany - Execute"
date: 2009-04-14
forum: Programming Talk
---

### Post by swappo1 on 2009-04-14
Hello,

I just started using Geany.  If I have a program open and I edit it, save then compile it, and click execute, the program prior to the changes runs.  Is it running a previously saved program?  The only way for me to get the new saved version to run is to go to the command line and compile and run it that way.  Then the next time I hit execute it will run.  It seems like I have to compile from the command line every time. How do I get Geany to compile and execute the current program I am working on without using the command line?

---

### Post by Vadi on 2009-04-14
Can you try using an updated version? [http://www.getdeb.net/search.php?keywords=geany](http://www.getdeb.net/search.php?keywords=geany)

---

### Post by swappo1 on 2009-04-15
I tried removing geany and then reinstalling version 0.14-1 for hardy and I still get the same problem.  I will go in and actually comment out large blocks of code and then save and compile it.  I get a ton of errors, but if I hit execute it still runs successfully.  It must save an original somewhere and run off of that because no matter what I do it always runs the same way.  I have looked over everything in preferences and can't find any way to get this to work right.  Does anybody have any ideas what could be the problem?  Is it a setting?  It looks like a cool IDE but if I have to run everything from the command line then I'll have to find something else use.

---

### Post by Vadi on 2009-04-15
No, the point is, that the latst version is 0.16 already and they might have fixed it. If no, we can ask the developers why is this behavior as such.

---

### Post by swappo1 on 2009-04-15
0.14-1 is the latest version for hardy which is what I use.  0.16 is for intrepid.  Will 0.16 work on hardy?

---

### Post by Vadi on 2009-04-15
Ah. Try installing it, if it doesnt work, I'll get it updated.

---

### Post by swappo1 on 2009-04-15
I tried installing 0.16 amd64 and I got an error message: > Error: Dependency is not satisfiable: libglib2.0-0

---

### Post by Vadi on 2009-04-15
Ah. That means it requires a newer version of glib - I'll see if a hardy package can be built. If no, we'll bug the authors about this behavior ;)

(though personally, I like building via terminal - then I can stop the build process at anytime. Not a CLI fan though)

---

### Post by swappo1 on 2009-04-15
Thanks, I appreciate your help. BTW, is there a difference between terminal and CLI?  I always use the two terms interchangeably.  Terminal is what I am really using when I say command line.  I guess the lingo is just left over from my windows days.

---

### Post by Vadi on 2009-04-15
A terminal *is* a CLI (command line interface), or a CLUI (command line user interface). GUI is a "graphical user interface".

So... you can use terminal and CLI inter-changable. Only lingo from windows would be cmd.exe ;)

---

### Post by Vadi on 2009-04-15
Alright, a 0.16 is up for hardy now.

---

### Post by swappo1 on 2009-04-16
I installed the 0.16 version of geany(thanks for putting it up).  I still am having the same problem though.  I'm begining to think geany just doesn't wan't to run on my computer.  I tried anjuta but don't like the look and feel of it.  Code::blocks is a lot of work to install it just to see if I might like it.  All I really want to do is be able to run a small program quickly without having to do alot of typing at the terminal(it also has to have a dark background since the white really bothers my eyes).  But I do like the code folding feature and the ability to quickly move around in the text window with geany.  Gedit is too limiting with its lack of features.  Thanks for the help.

---

### Post by Vadi on 2009-04-16
Ok. here's what a person at *#geany* said:

> (12:28:43 PM) FraLan: vadi2: " I get a ton of errors, but if I hit execute it still runs successfully.  It"
(12:28:56 PM) FraLan: the user should clean up tis dir
(12:29:04 PM) FraLan: and check the error messages on compiling

---

