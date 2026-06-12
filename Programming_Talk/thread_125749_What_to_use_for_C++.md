---
title: "What to use for C++?"
date: 2006-02-04
forum: Programming Talk
---

### Post by wilsonisme on 2006-02-04
Okay please be nice because I am both new to linux and C++ but here is the deal: I am taking a really basic c++ class at my highschool, and need to be able to write programs (and hopefully compile them?) at home. What is something I could do this on in ubuntu? I like GUI's but as long as something works and there is ample documentation on I don't care. At school we all are using win 2k pro and microsofts proprietary software. Would things I write at home be compatable? Thanks

Oh and a random unrelated question that I don't think deserves a seperate thread. How do I get KDE's clock off of military time?

---

### Post by cwaldbieser on 2006-02-04
[QUOTE=wilsonisme]Okay please be nice because I am both new to linux and C++ but here is the deal: I am taking a really basic c++ class at my highschool, and need to be able to write programs (and hopefully compile them?) at home. What is something I could do this on in ubuntu? I like GUI's but as long as something works and there is ample documentation on I don't care. At school we all are using win 2k pro and microsofts proprietary software. Would things I write at home be compatable? Thanks

Oh and a random unrelated question that I don't think deserves a seperate thread. How do I get KDE's clock off of military time?[/QUOTE]
If you install the "build-essential" package from the repositories, you will get g++, which is a command line program capable of compiling C++ code.

Basicaly, you edit the c++ sources in a text editor (gedit, kate, vi, emacs, pico, nano, etc.).  For a simple "hello_world.cpp" program, you would compile it like:
```

$ g++ hello_world.cpp

```
This will either produce errors or create a file called "a.out" that can be run with
```

$ ./a.out

```
There are a ton of options-- I suggest checking out the man pages or asking more specific questions.

Some of the more basic programs you write in a high school class can probably be moved between operating systems with little or no changes.  If you use OS specific libraries, however, they may not be portable.  Intro classes I took tended to focus on language syntax and implementing algorithms rather than using OS specific features, though.

For the clock problem, right click on the clock, choose "Date and Time Format", adjust to your liking.

---

### Post by Adrian on 2006-02-04
[QUOTE=wilsonisme]Okay please be nice because I am both new to linux and C++ but here is the deal: I am taking a really basic c++ class at my highschool, and need to be able to write programs (and hopefully compile them?) at home. What is something I could do this on in ubuntu? I like GUI's but as long as something works and there is ample documentation on I don't care. At school we all are using win 2k pro and microsofts proprietary software. Would things I write at home be compatable? Thanks
[/QUOTE]
Since you seem to use KDE, I'd recommend KDevelop. Just install the **build-essential** and **kdevelop3** packages.

Since it's a basic C++ course, I doubt that you will create any platform-dependent programs. As long as you follow the C++ standard, things will be fine.

---

### Post by wilsonisme on 2006-02-04
ah okay im blind regarding the clock, didnt see the p thing

---

### Post by Basu on 2006-02-05
Personally i would not recommend using kdevelop if you're new. I found it too overwhelming. Just use a text editor of your choice and the command line. Don't worry about simple programs, the code should be compatible, though you'll have to recompile of course. But if you use VB 6.0 you'll find a few headers not there in the GNU C++ standard.

---

### Post by slavik on 2006-02-05
I would suggest using Anjuta in the beginning if you really want an IDE ... I'd install both and try to write and compile a simple program as fast as possible. the IDE where you do it fastest is what you should use.

And try to figure out the things you need by yourself without help.

---

### Post by amosbatto on 2006-02-05
If you are a beginner, I don't recommend a normal text editor, then compiling with g++.  An IDE like anjuta will help you a lot, because it will tell you what you are doing wrong as you type.  For instance, if you want to use a function from the standard C library, Anjuta will tell you what arguments the function takes as you type.  This is extremely helpful.  Learning how to debug can be tough.  Debug with Anjuta--it is a lot more intuitive than gdb.  That said, I find that Anjuta sometimes gets stuck in debugger mode and I have to exist the program and restart it.  I have found ddd to be a more stable debugger, but the x windows interface doesn't always work well in GNOME.  Sometimes it is difficult to enter input in dialog boxes.  

One of the biggest failings in my opinion is the lack of good integrated help with examples.  Anjuta has links to the library documentation, but getting help on standard C functions can be really maddening.  At this stage you are probably learning the ANSI standard, so you might find this site helpful: [http://www.cplusplus.com/ref/](http://www.cplusplus.com/ref/)

good luck,
Amos

---

### Post by Viro on 2006-02-06
I disagree with learning to program using IDEs, especially the open source ones. The reason is this. When something goes wrong, which it invariably does with Anjuta, what are you going to do? The IDEs like Kdevelop and Anjuta are nice for experienced programmers, but they provide too much 'clutter'. Even as an experienced programmer, I don't like clutter. What more when starting out. 

When learning to program, you want to learn to program, not learn how your particular IDE works. I say stick with the simple text editor & command line approach until you are familiar with programming.

---

### Post by thumper on 2006-02-06
I'm with Viro on this.  Go with a simple editor.  If using KDE then Kate has nice syntax hilighting.

---

### Post by slavik on 2006-02-06
Isn't Kate considered an IDE?

Yes, abandon all IDE ... go with pico (or nano). A text editor so easy to use, you learn it in 2 minutes!!! :D

---

### Post by thumper on 2006-02-06
Kate doesn't enforce projects or workspaces on me :)

Nice syntax hilighting for a (not so) simple editor.

---

### Post by Basu on 2006-02-07
I agree with thumper. One thing that puts me off most IDEs is the insistence of using projects. I don't want to start a great big project with all the associated clutter just to write a program that'll fit in one small file.

---

### Post by AZzKikR on 2006-02-07
I just use VI/VIM mainly for editing small source files. I use a real IDE for the bigger work.

---

