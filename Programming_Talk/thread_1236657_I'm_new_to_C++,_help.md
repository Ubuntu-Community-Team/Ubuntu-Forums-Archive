---
title: "I'm new to C++, help?"
date: 2009-08-10
forum: Programming Talk
---

### Post by KinaU on 2009-08-10
[FONT=Arial]I'll be learning C++ this year and I decided to look into it before the course, so...

[http://www.cplusplus.com/doc/tutorial/program_structure](http://www.cplusplus.com/doc/tutorial/program_structure)[/FONT][FONT=monospace][FONT=Arial]/

Where do I input the code? Is there some program I should use or should I use the text editor?

Please help. I'm beginning to feel stupid. :(


Edit: I tried KDevelop, saved the file to Desktop and opened it, and I'm getting text editor. Therefore I can use text editor as well?
[/FONT][/FONT]

---

### Post by .Maleficus. on 2009-08-10
You can use either.  To actually build the program, you need the "build-essential" package though (KDevelop might have it as a dependency, I don't know).
```
sudo apt-get install build-essential
```
And then compile from within KDevelop or the terminal.

---

### Post by KinaU on 2009-08-10
> **.Maleficus. said:**
> You can use either.  To actually build the program, you need the "build-essential" package though (KDevelop might have it as a dependency, I don't know).
```
sudo apt-get install build-essential
```And then compile from within KDevelop or the terminal.

I got build-essential, but how do I use it? Where is it? :confused:

---

### Post by unknownPoster on 2009-08-10
All of your questions are answered in the stickies:

[http://ubuntuforums.org/showthread.php?t=1006666](http://ubuntuforums.org/showthread.php?t=1006666)

---

### Post by gtr32 on 2009-08-10
I would recommend to install Code::Blocks:

sudo apt-get install codeblocks

Then create a new project:

File -> New -> Project -> Console application

Build it:

Build -> Build

Run:

Build -> Run

You should now see a console pop up with "Hello World!" output.

---

### Post by KinaU on 2009-08-10
> **gtr32 said:**
> I would recommend to install Code::Blocks:

sudo apt-get install codeblocks

Then create a new project:

File -> New -> Project -> Console application

Build it:

Build -> Build

Run:

Build -> Run

You should now see a console pop up with "Hello World!" output.


This is great, thank you so much! :D

---

### Post by jamescox84 on 2009-08-10
The way I do it, but then it's not for everyone...

Write code using a text editor.  I use gedit

Compile code from terminal.
```

g++ my_first_source.cc my_second_source.cc -o my_executable

```
This is an exmaple of compiling a very simple program.  I'd make a makefile for anything over three files.

Run from terminal.
```

./my_executable

```

Make sure:
```

cd /path/to/my/source/files

```

---

### Post by nvteighen on 2009-08-10
Hm... I would recommend you first learn by using a text editor and manually compile your code first using the command line and then, using Makefiles. Sadly, C and C++ need you to know how the compiling process is divided in order to get them right. An IDE will hide that, but for example it's a crucial part on C and C++ programming when stuff is linked.

After that, IDEs will be very useful for you. They'll automate the awful compilation details, but, if the automation doesn't suit you, you'll have the knowledge to adapt it to your needs.

---

### Post by stevescripts on 2009-08-11
One more voice for first learning to code with a text editor and build from the command line ...

Steve

---

### Post by gtr32 on 2009-08-11
> **stevescripts said:**
> One more voice for first learning to code with a text editor and build from the command line ...

Eventually, yes, but for the reasons he described in his original post I'd say he is fine with an IDE right now.

---

