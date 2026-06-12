---
title: "Compiling multiple files in Geany"
date: 2008-01-24
forum: Programming Talk
---

### Post by Darksouled on 2008-01-24
Hi, I recently installed Geany to create some very simple programs, but I can't figure out how to compile several files at once (two .cpp files and a .h). It seems like Geany don't understand that the three files I have opened into my project are linked together.

When I add the correct path to "Make all" and try to make all (shift+F9), I get "Permission denied". Have set permission on all files to read + write, so I'm all outta ideas now. Hope someone may help.

Btw, I'm just below the n00b stage, so an easy explanation would have been great. :)

---

### Post by Darksouled on 2008-01-25
No one knows anything?

Are there any other apps I can use as a replacement for Geany then?

---

### Post by agim on 2008-01-25
There are several other apps, depending on what you are looking for. I generally use emacs.

Its too bad to hear Geany isn't working for you, I just downloaded it myself and will give it a try soon.

anjunta
kdevelop
motor
xjed

I have heard good things about the first two and nothing of the second two. There are probably more in synaptic, I found those with a quick browse after searching "C++ ide".

Good luck.

---

### Post by Darksouled on 2008-01-25
Thanks a lot for the list :) 

Gonna check them out if I can't figure out Geany soon. Too bad really, it seems like a simple and fast IDE.

---

### Post by Darksouled on 2008-01-27
I must say, I feel pretty smart right now.

With my world-class problem solving skills I finally managed to uncover the importance of consistency in correct upper-\lowercase in file names and #include references. DoH...

Guess that solves the problem tho, so I'm happy nonetheless. :)

EDIT:

Well, it doesn't seem like Geany dows anything about any other files than the one currently active, so I can't build my program... Problem with Make All still persists: 

```
/bin/sh: /home/ronny/Documents/Geany_projects/Innlevering_1/main.cpp: Permission denied
```

Any hints?

---

### Post by Dejai on 2008-03-28
Wouldn't you just use:
g++ main.cpp -o file

---

### Post by foresto on 2008-04-04
It seems you have reached the point in your programming career where learning the ways of the Makefile will prove useful.

---

### Post by Mirge on 2009-06-15
Resurrecting old thread. Anybody know about this? Maybe there's a way to build a "project" in geany? ie: few header files, few source files, main source file... without a Makefile or g++ -o main header1.h header2.h source1.cpp source2.cpp in a terminal window?

---

### Post by Mirge on 2009-06-15
Scratch that. I actually decided to give Code::Blocks another try... a fair one this time, and I actually am really enjoying it. I still prefer Geany for non-C++ programming, but Code::Blocks is definitely my C++ IDE of choice now.

Created a similar example as before, "Animal" class.

animal.h contained the class interface. animal.cpp contained the class implementation. main.cpp made use of animal.h, and Code::Blocks correctly built the project, ran without any problems. Nice.

---

### Post by Can+~ on 2009-06-15
For now, I would stay away from big IDEs, I would first learn how to write a makefile, it will help you understand better how a compiler/linker works.

Once that you learn... I suggest giving Eclipse (with the CDT plugin) a try. It's just unpack and run if you have sun-java6-jre installed. Just don't download eclipse from the repo, it's kinda outdated

[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)

---

### Post by meastp on 2009-06-16
Yeah, Code::Blocks is a nice C++ IDE... :)

---

