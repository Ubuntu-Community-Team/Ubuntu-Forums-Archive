---
title: "GTKmm and Anjuta - sigc?"
date: 2007-05-22
forum: Programming Talk
---

### Post by Mathiasdm on 2007-05-22
I'm trying to learn GTK using their tutorial. When I run the example program: [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03s07.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch03s07.html)
When I try to build the example, I get an error saying "error: ‘sigc’ has not been declared"

I'm using the exact code that's on the gtkmm.org page, so I'm guessing I have some sort of dependency problem. I checked, and I think I have the right libraries installed. (I'm on Windows right now, as I don't have reliable wireless on Ubuntu -- so I'll post the list of libraries later).

Does anybody know what I'm forgetting here?

---

### Post by WW on 2007-05-23
I am using dapper, and I have the package **libgtkmm-2.4-dev** installed.  These commands worked for me:
```

g++ -c main.cpp `pkg-config --cflags gtkmm-2.4`
g++ -c helloworld.cpp `pkg-config --cflags gtkmm-2.4`
g++ main.o  helloworld.o -o main `pkg-config --libs gtkmm-2.4`
./main

```

EDIT:  I just reread your post--I forgot that you had 'Anjuta' in the subject.  Try those commands in the command line, to be sure it works.  Then figure out how to add the pkg-config options to Anjuta's build commands.  I've never used Anjuta, so I can't help you there.

---

### Post by butterfingers on 2007-06-02
I was facing the same problem as you. I found the solution [here]("http://ubuntuforums.org/showthread.php?t=139429&highlight=anjuta+pkg-config+gtkmm"), but I will post it again:
Go to Settings >> Compiler and linker settings.. >> Options and then, in Additional Options there is Compiler Flags (CFLAGS), there you should write 
`pkg-config gtkmm-2.4 --cflags`
(don't forget the backquotes), Then at Linker flags (LDFLAGS) you should write
`pkg-config gtkmm-2.4 --libs`
(again, don't ignore the backquotes).
Still you may have problems. That is because Anjuta will be sarching for libgtkmm-2.0, and you want to use liggtkmm-2.4. One way around this is to create a new project and make it a Console Project in the initial wizard. 

Hope it helps.

---

