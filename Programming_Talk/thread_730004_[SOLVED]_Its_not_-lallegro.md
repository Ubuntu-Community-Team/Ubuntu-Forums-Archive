---
title: "[SOLVED] Its not -lallegro ?"
date: 2008-03-20
forum: Programming Talk
---

### Post by Zeotronic on 2008-03-20
Just a few minutes ago, I aquired the code to a project that uses Allegro... I downloaded the development files from Synaptic, but I cant figure out the command to link to allegro... my experiance linking is rather limited, so its not suprising that I cant figure it out. How do I link to Allegro?

---

### Post by WW on 2008-03-20
The lib name appears to be **alleg**, not allegro.

By the way, a quick check of the files shown [here](http://packages.ubuntu.com/gutsy/i386/liballegro4.2-dev/filelist) shows a program called **allegro-config**.  Try this command:
> 
$ allegro-config --libs

to see if it gives the correct options for linking the library.

---

### Post by Zeotronic on 2008-03-20
> The lib name appears to be alleg, not allegro.

By the way, a quick check of the files shown here shows a program called allegro-config. Try this command:
Quote:
$ allegro-config --libs
to see if it gives the correct options for linking the library.
It returned:
> -L/usr/lib -lalleg-4.2.0 -lm -lpthread -lXxf86vm -lXcursor -lXpm -lXext -lX11 -ldl

... erm, what does that mean?

Edit:
Ok, that string it returned seems to link it properly... But I assume it to be excess?

---

### Post by WW on 2008-03-20
Those are all the options required to link the allegro library.  For example, if you have a single file, say main.c (or main.cpp if C++) that uses allegro, and you have already compiled it to main.o, then to link you would do something like this:
> 
$ gcc main.o `allegro-config --libs` -o main

By putting the command in back-quotes like that, the shell will replace the command with its output.  You could also do it this way:
> 
$ gcc main.o $(allegro-config --libs) -o main


---

