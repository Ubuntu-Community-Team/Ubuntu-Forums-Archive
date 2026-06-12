---
title: "Switching to Linux for programming. Need advice and direction."
date: 2007-06-04
forum: Programming Talk
---

### Post by Intertricity on 2007-06-04
Hello all! It's been quite a few months, getting situated with Ubuntu. I'm loving every minute of it, and each hurdle has been exhilarating when overcome.

I've read through a lot of docs already, and I keep some pdf's handy, but I was hoping I could get some genuine community input from real veteran programmers. Let me give you an idea of where I'm at right now, and where I want to go, and hopefully some of you can point me in the right direction.

For some background information, I'm fresh out of our school's Intro to C class. Programming isn't my major, but I wanted to learn about it in my spare time. Our most complex project was just a simple hangman game, so we didn't really learn how to use separate files or libraries or anything- although I did learn a little bit about libraries and dynamic linking, I don't have a solid foundation on it. Getting better with structs and pointers. At one point, I think I managed with some help from ##C on freenode to get a function pointer into a struct, but I couldn't reproduce it from memory.

We did all of our programming in Visual Studio. It does have a nice environment, but as I've begun learning how to do equivalent things in Linux, I have to do a lot of googling and searching for setting up an efficient environment.

Am I under the right impression that it's possible to have a faster workflow in Linux than with Visual Studio? I don't mind the initial curve, I'm fighting with Blender as we speak ^_^;;

I've just gotten gvim and vim set up with .vimrc to do syntax highlighting, and I can make a basic makefile for a single program so that I can type :mak in vim. At one point, I think I had it where I could debug from vim, but I forgot.

Either way, I need input on what a real development cycle is like on Linux and what programs/tool chain it is composed of, and what I can do to put my Visual Studio friends to shame ;}

---

### Post by raja on 2007-06-04
The programming language to learn and use depends to a large extent on what you plan to do. For many general applications, you should have a look at Python as a language to use.

---

### Post by KaeseEs on 2007-06-04
Your development workflow in Linux[or another Unix, or W32]depends very much on your tools and what you're developing.  However, a basic cycle that is nearly universal (and which you're probably already following) consists of:[list]Plan[/list][list]Code[/list][list]Test[/list][list]Debug[/list][list]Repeat[/list]  

Now, this can be altered a good bit by some tools.  For example, **Subversion** is a 'version control' (also called 'source code management') system.  It's available easily through the repositories, and you can get a repository hosted for free by Google (see [http://code.google.com/hosting/](http://code.google.com/hosting/) ).  What Subversion does is keep track of changes made to your source code files, so you can easily track changes, manage code branches, and collaborate with others.  

In addition, for many **gdb** is a helpful tool for debugging.  It allows you to step slowly through your program and track the status of variables and trace execution.  For complex cases, it's often much simpler to use gdb than to insert a bunch of printf()s.

If you're going to keep experimenting and hacking away with C, you're going to want **manpages-dev** and **glibc-doc**, which document C library functions and system calls( recv(), exit()/_exit(), &c. ) through the regular manpages.

Whatever kind of programming you're doing, I would *strongly* recommend **exuberant-ctags**.  After installing, you run ```
ctags *
``` in your project directory.  Then, when you fire up vim, you can skip to functions, #define'd stuff, constants and other stuff easily via ```
:ta *name_of_thing*
```  Note as well that tab completion works for *name_of_thing*.  This was the single most productivity-enhancing thing I learnt with vim, save...

**multiple buffers**.  You can have several files open in one window at once in vim.  With gvim, you can do this, or use tabs.  You can do it at the command line:```
vim -o file1.ext file2.ext ...
``` or with vim already open and viewing a file```
:new file.ext
```  Once you have multiple buffers open, you can copy/paste/etc between them, and switch between buffers either via emacs-style keychanins starting with C-w, or via a normal vim interface:```
:winc *window_command*
```

Now, with the exception of Subversion, everything I've said here goes toward speeding up various steps of the workflow rather than altering it generally.  You're on the right track with what you've already done.  Keep going as long as you enjoy it.

---

### Post by phishtree on 2007-06-04
you might want to check this link out:
[10 Programming Languages to learn]("http://www.eweek.com/article2/0,1759,2016415,00.asp")

---

### Post by RedGhost on 2007-06-04
If you're used to an IDE like VS you might like Anjuta (apt-get install anjuta).

A newer version may be available: [http://anjuta.sourceforge.net/](http://anjuta.sourceforge.net/)

---

### Post by pmasiar on 2007-06-04
> **Intertricity said:**
> I'm fresh out of our school's Intro to C class. Programming isn't my major, but I wanted to learn about it in my spare time. 

You know already that programming is a lot of hard work. C is rather low-level language, programmer has lot of control and lot of responsibility - and programs, if done correctly, are fast, and many programmers gets a lot of fun from knowing they squeezed all power PC has.

There are many other languages, suited for different niches, and competing for new programming converts. So you need to figure out in which niche are you interested first. 

After learning basics, excellent way to improve your programming skills is to participate in open-source project: you can learn by reading real working code written by good programmers - and learn tricks from them. Many projects are eager to get "new blood" developers, and have mentoring programs to get beginners willing to learn up to speed.

For more fun factor you can try higher-level, dynamically typed languages, like Python. Computer works much harder for you, and programming in Python is simpler than in C. Especially if programming is not your major - lots of scientists prefer simplicity of Python over faster, but harder to debug C/C++/C#/Java code.

Python has good library to write games, pygame. Games will not be as resource-effective as games written in C, but you will have something to show your friends *much* faster if you write it in Python. But decent GUI is a lot of hard work, that's why most people started with text-based adventure game...

Wiki in my sig has many projects and sites for learning programming.

Python is used by OLPC (laptop.org), is main development language for Ubuntu, and widely used and supported by Google (and many other companies). In my more that 20 years in IT I used many many languages, and Python is my favorite by far.

---

### Post by Intertricity on 2007-06-05
Your replies are all very helpful! Thank you so much!

I see I should have made clearer my purposes for programming, I apologize ^_^;

I did have a niche picked out. I would like to work with personality and AI. Also, inspired a bit by the guy at [Hanson Robotics]("http://www.hansonrobotics.com/robotics.php"), I would like to dabble a bit in device interfaces to my own animatronic type dolls, perhaps nothing more than a few servos and an Arduino board. I'm more interested in the aesthetic side of that.

My main focus is really personality and AI. I've picked C and Lisp to be my languages of choice. I've been reading the beginning of "Practical Common Lisp" by Paul Graham, but it'll have to go on the backburner for now because of summer classes =\ I really like it though (however much of a pain it was to get SLIME and syntax highlighting set up).

Right now, however, I've got a personal project going where I'm learning about Blender, (so yeah.. python is important here),  and I want to rig a simple mesh puppet up and control it with an external program via sockets programming (for now, another python program). I was assuming I could import a python sockets library within Blender to do this. As my personality and AI programming improves, I was hoping to attach an AI to it in the form of that external program. I chose Blender because I like how it includes a game engine so that I need not get bogged down in the details of 3D programming when I just want a 3D character on the screen.

I do expect my neural network in the future to saturate a lot of memory, perhaps dedicating my entire desktop to it and running the 3D client/character from my laptop (thus the socket programming would come in handy).

I'm trying not to sound too pie-high-in-the-sky here, because I understand that a lot of people tend to come by and say "Oh I want to do this this this and this!". I've been working out the details over the past few months, and I've tried to set a reasonably simple goal (model and rig a character in Blender, control it with an external program via sockets) for my first version.

--------------------------------------------
Individual responses:

KaeseEs: Ooh, this is what I've been looking for! Thanks!
RedGhost: Yes, I've tried Anjuta, it looks very nice =) I was about to go for Eclipse but I didn't really want to download over 100mb of files, lol.
Raja: See the big chunk of text above :P
phishtree: Actually, php was my first experience with c-type programming. I've done a little bit of JavaScript, won't touch perl XD;;, used a python cheat sheet, and played once or twice with bash scripting (woohoo crontab!). Since I don't plan to be a programmer by trade, I was hoping that Lisp would encompass many if not all the concepts the other programming languages bring to the table, using it for my specific purposes.
pmasiar: See big chunk of text, =)

---

