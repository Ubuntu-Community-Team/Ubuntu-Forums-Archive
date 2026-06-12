---
title: "NetBeans-6.8 and Ubuntu Issues"
date: 2010-01-27
forum: Programming Talk
---

### Post by kaspar_silas on 2010-01-27
Hi All,

Does anyone use the new netbeans 6.8?

I use it for some C++ and was initially quite impressed. However I upgraded recently from 6.7 and have run into some issues running under ubuntu.

For example:

Sometimes when I use the [right click]->Navigate->"Go to declaration". A separate copy of the code opens up in a new tab. Naturally this is the last saved version. So if you don't notice and make more changes you can have two different versions of code. One that runs and one you are editing and looking at. This as you can imagine led to vast confusion within me.

The opening of a copy thing also happens when debugging and a breakpoint is hit. Thou the copy opens without the breakpoints leading to more confusion as to why the hell it stopped.(especially if you add line-returns to the newly opened copy and continue as you can then stop on comments and white space).

I also have a more mysterious issue with the IDE occasionally totally freezing after a running program exits/(is closed) and returns control to it. It's a very strange lock-up that prints no error messages and is not easily killed. ("xkill" does however finish it). 

I also have a netbeans copy on my more powerful ubuntu cluster and exactly the same thing is happening there. However on a windows machine everything works as it should.

Has anyone else had these or similar problems. Or more importantly does anyone know likely paths to solve them. 

It's a pity as I quite like the netbeans layout. I realize I could switch to other IDEs but I would prefer to fix this one.

Thanks for any help.

---

### Post by kaspar_silas on 2010-01-28
Damn, O well of to the netbeans forum. Possibly that was the correct place to start. O well.

---

### Post by kahumba on 2010-01-28
Qualitative C/C++ experience for NetBeans is #INFINITY-1 on the NetBeans developers priority list.
Indexing libraries is extremely slow and hogs the CPU each time I open a Gtkmm project etc etc but in any release notes they praise performance boosts. Each time you go past a Hello World app it becomes a hog in dealing with.
I hate NetBeans but Eclipse is plain stupid asking lots of questions it should be able to answer itself for an IDE of the 21st century and the other ones are either too simplistic and/or plain bad.
So live with it, I doubt there's gonna be any serious approach to C/C++ on NetBeans since it's mostly all about Java and related stuff.
I'm constantly tempted to go the simple editor/terminal/gnu autoconfig way, but there's just no point-click-learn-start working resource (like the "The Java tutorial"), they're all fragmented referencing each other like broken symbolic links on a filesystem and you're left out to figure out where to start and which one of those confusing ways you should choose.
I know I'm not describing a wonderful world about open source so someone should jump in and slap me in the face for doing this and being "completely wrong".

---

### Post by Reiger on 2010-01-28
You might like KDevelop which is decidely C/C++ centered...

---

### Post by kaspar_silas on 2010-01-29
I will have a look at Kdevelop. I didn't like it last time I tried it but that was a while ago and it's probably improved. Anyway cheers for that. By any chance do you know an easy way to import Netbeans projects.  

I also take the point above that Netbeans isn't great for C++. I was, as I said initially impressed with 6.8. However as this issue is unsolved on both the Netbeans forum and it looks like it's back to vim (or kdevelop) I have changed my opinion somewhat.

Fixing this by switching IDEs doesn't really seem a solution but I guess it is a way forward. I suppose I could also switch the cluster to XP but somehow I don't see that happening.

Cheers anyway.

---

