---
title: "Bridge building game: Missing Lib"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by m994301009 on 2008-04-27
I'm trying to get this game to run, and it has a linux version, but I get:
```
/home/matthew/Programs/bridgebuilding/bridgebuilding: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory
```
I have the lib, and I even tried copying it into the games folder, but I still get the error. Anyone know what to do?

---

### Post by Hospadar on 2008-04-27
What is bridgebuilding? is it something out of the ubuntu repositories? are you trying to run it or build (compile) it?

Probably what is happening is either:
- You don't have the library you think you do (look for other similarly-named libraries in the repos, it won't hurt to install a couple extra)

- The program is looking in the wrong place for the library.  The solution to this is to make a link to the library where the program expects the library to be.  
So first check: 
Is the library file named *exactly *"libSDL_image-1.2.so.0" if not, you can make a link with that name to the actual library file. ```
ln -s libSDL_image-1.2.so.0 <actual name of lib>
```"ln" is the program used to make links, "-s" option tells it to make a soft link, this is a little safer for our use (As opposed to a hard link, which follows the file if it is moved)

Also, the program may be looking in the wrong folder for the library, it might not be easy to find which folder it is looking in, and it is probably looking in multiple folders.  You could try creating links in all the different lib folders and see if that helps.  If you try this, keep track of where you put the links and exactly what you named them so you can get rid of them if it doesn't work.  Try putting links in /lib /usr/lib /usr/share/lib and see if any of those help.  (you'll have to prepend the link command with "sudo" since these are not user areas)

Another option may be to try building the program yourself.  Often this will resolve issues with binary compatability (if you downloaded a binary).  If you link to the page you got the software, we can help with that.

---

