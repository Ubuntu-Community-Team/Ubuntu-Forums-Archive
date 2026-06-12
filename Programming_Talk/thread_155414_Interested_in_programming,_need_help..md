---
title: "Interested in programming, need help."
date: 2006-04-05
forum: Programming Talk
---

### Post by Knowledge2012 on 2006-04-05
Hello, i am interested in programming, and have been for quite some time, i just never seemed to be able to get up and actualy do it. I had the chance to learn java in school, but i didnt do well, mostly becuase of my own faults and not caring enough to do well. 

Basicaly i would like a way to learn c++ or any other language for that matter. c++ would be at the top of the list. What i need is a program, that offers a tutorial as well. I tried using KDevelop c/c++ but when i got into the tutorial section, it turns out i was missing hello.cpp hello.h and main.cpp, which is what i needed to get started in creating my first program. That bumbed me out because i was realy looking forward to getting started.

I would realy appreciate help. I just want to be able to get started. if there is maybe a program that provides tools for begginers like me, that would be great.

---

### Post by x5452 on 2006-04-05
to be up front I am just learning c++ myself and really dont know much. But I will relay what I found out from another programming forum, the most talked about and suggested learning book is  called accelerated c++ by Angrew Koenig,
[http://www.acceleratedcpp.com/](http://www.acceleratedcpp.com/)

 I bought it and it is great, starts off learning right away and not hard to follow.  As for compiling programs, im still using visual c++, [http://msdn.microsoft.com/vstudio/express/visualc/](http://msdn.microsoft.com/vstudio/express/visualc/)

because im new to linux and that was a good suggested starter.  Also it has lots of help info built into it.

---

### Post by Buffalo Soldier on 2006-04-05
The tutorials [**[color=red]here[/color]**](http://www.cprogramming.com/tutorial.html) are quite good I think. But I haven't tried the C++ tutorial, just C.

As for programming tools, all I need for C so far is Gedit (the default text editor) and installing the build-essential package which installs mostly all the tools for programming.
```
sudo apt-get install build-essential
```

---

### Post by x5452 on 2006-04-05
cool i did not know that, does ubuntu have an ide/compiler that can be installed?  Wheres the programming tutorials at?

---

### Post by Knowledge2012 on 2006-04-05
Hey thnx for that website, that looks realy promising.. i would like to get programming soon, so maybe ill start with that. 

Are there any native other linux programs that come with a tutorial or guide kind of like KDevelop. I think im going to upgrade and reinstall KDevelop and anythign involved or has the phrase "KDevelop" in it, because i think if i could just get that tutorial i could get on my marry way to programming, The KDevelop program looks like it should costs a few hundred bucks (if it were developed for window$). 

BTW 

Thank you ubuntu team for producing an awesome distro.

---

### Post by Buffalo Soldier on 2006-04-05
[QUOTE=x5452]cool i did not know that, does ubuntu have an ide/compiler that can be installed?  Wheres the programming tutorials at?[/QUOTE]

For simple C programming, I just install the build-essential package and use gedit. (see screenshot).

To compile the program:```
gcc -Wall hello.c -o hello
```
**gcc** = GNU C compiler
**-Wall** = Warning all / asking the compiler to be very strict
**hello.c** = name of the source code file
**-o** = compile into object file
**hello** = name of the object file

To run the program:```
./hello
```

Basically any ANSI C programming tutorials that you can find online works in Ubuntu.

If you would like something more complex, there are many IDE to choose from. For C I would suggest Anjuta.

---

### Post by daller on 2006-05-21
How do you build a GUI application using Kdevelop?

1. Design the GUI using "Kdevelop designer"?
2. Load the GUI into "Kdevelop"?
3. Write some code for the GUI.?

Or how is the progress?

Any tutorials?

---

### Post by thumper on 2006-05-21
[QUOTE=x5452]to be up front I am just learning c++ myself and really dont know much. But I will relay what I found out from another programming forum, the most talked about and suggested learning book is  called accelerated c++ by Angrew Koenig,
[http://www.acceleratedcpp.com/](http://www.acceleratedcpp.com/)[/QUOTE]
Don't forget Barbra Moo...

I also recommend this book.  I have not read it, but I have flicked through it and it seems to teach C++ the correct (IMHO) way.  

I have been programming C++ for around 12 years and I don't mind helping here.  There are other experienced C++ programmers who also frequent this forum and are also happy to help.

We won't, however, do homework or assignments.  The point is to help you learn and understand, not do stuff for you.  Ideally we like to lead you to the answers rather than just giving them to you.

[quote=Buffalo Soldier]
gcc = GNU C compiler
-Wall = Warning all / asking the compiler to be very strict
hello.c = name of the source code file
-o = compile into object file
hello = name of the object file
[/quote]
the -o flag actually stands for output - so instead of creating a.out, which is the default, it creates hello (which is the next parameter).

---

### Post by adamkane on 2006-05-21
These discussions are always endless.

The O'Reilly series has what you need to get started in whatever language suits you.

---

