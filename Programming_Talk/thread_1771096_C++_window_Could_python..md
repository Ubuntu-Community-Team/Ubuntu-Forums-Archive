---
title: "C++ window? Could python?."
date: 2011-05-30
forum: Programming Talk
---

### Post by ThatCoolGuy220 on 2011-05-30
Hi after researching i decided to go c++ and python (Mostly C++). IDK why it looks easier for me (Though ppl say its horribly hard :().
But im like comparing stuff.

Well the problem is that i have this 3 files.

- Untitled (No extension) but seems to be an executable an icon that looks like a "<>"

- Untitled.cpp (Source code)

- Untitled.o (o! whats that i couldnt open that file anyway)

Ok when i click The first one it doesnt matter how many times, it wouldnt open any window of any kind.

i read that if i add:

#include <window.h>

it will but there no such library.

what im doing wrong!



Could python workaround this better (How?)

Or there is a solution for C++


Thanks for the help:p

---

### Post by unknownPoster on 2011-05-30
There is "windows.h" but that's from the Windows API, not sure if that is what you mean or want.

Nothing will happen from just including a header file. You'll actually have to write code to make a window appear.

For example, in C++ with QT:
```

#include <QtGui>   
int main(int argc, char *argv[])  {      []("http://doc.qt.nokia.com/main-snapshot/qapplication.html")[U]
[/U]QApplication app(argc, argv);      
QWidget window;      
window.resize(320, 240);      
window.show();      
window.setWindowTitle(QApplication::translate("toplevel", "Top-level widget"));      
return app.exec();  
}

```

---

### Post by ThatCoolGuy220 on 2011-05-30
Hi thx for your answer im not familiar with QT and also im newbie on C++ though i like it.

I have some questions about your method:

- Is Qt Multiplatform (Could do its job on other OS as well)

- After all the Int Main stuff i could still write a code 

(How? A new Int or just keeping writing.... let me explain better)

Supposing im writting the typicall Hello World Aplication:

```

#include <iostream>

int main()
{
using namespace std;

cout << "Hi World!!";

cin.get();
return 0;
}

```


Were it shuold go....

Sorry if you get mad with such a Dumb question....

---

### Post by ThatCoolGuy220 on 2011-05-30
I tried 

#include <QtGui>

but outputs this

untitled.cpp:2:17: fatal error: QtGui: No such file or directory

Though it could be easily solved...

---

### Post by unknownPoster on 2011-05-30
From reading this and some of your other posts, I'm not sure you're ready to develop GUI applications.

By nature most GUI toolkits introduce some advanced topics such as advanced Object Oriented Programming. You can expect to see polymorphism, inheritance, etc.

I'd argue that you need to have a pretty firm grasp on basic programming before you tackle GUI toolkits.

---

### Post by ThatCoolGuy220 on 2011-05-30
Seems like so.

Anyway thx for the help

---

### Post by nvteighen on 2011-05-30
It seems to me that everybody has ignored the central point: explaining how to run things in the terminal.

By default, programs will only work in the console or terminal emulator. To execute it, you have to open a terminal, enter the directory where the program is and type:

```

./<program_name>

```

Try it with your Hello World and it will work.

You can only double-click executables that are GUI programs, only if the required libraries are installed (which is usually the case, so don't worry). 

FYI, the .o file is an intermediate stage of the compilation process, the so-called object code. This file is your program compiled, but not linked to the required libraries to male it run... Let's say it's just the binary translation of your code, but that won't run. These files can be used as static libraries, though, and interrupting compilation at that stage is a very useful step for huge multifile projects (it allows you to recompile only the modified modules and relink everything much faster... well, you'll get it later).

---

### Post by Petrolea on 2011-05-30
> **unknownPoster said:**
> From reading this and some of your other posts, I'm not sure you're ready to develop GUI applications.

By nature most GUI toolkits introduce some advanced topics such as advanced Object Oriented Programming. You can expect to see polymorphism, inheritance, etc.

I'd argue that you need to have a pretty firm grasp on basic programming before you tackle GUI toolkits.

I agree. You can't start by making GUI apps. Well, you can but if you won't understand anything in your code and you will just copy-paste you will never achieve anything. Because as soon as you'll want to do something your way you won't know how.

My recommendation is that you first learn basics of C++ and then later, when you'll understand it (to some point) you can get into GUIs. And you should also take a look into differences between programming on Windows and Linux distros.

---

### Post by ThatCoolGuy220 on 2011-05-30
I don't copy paste that worked for me to get acustom with linux i wasnt meaning a complex window just meaned a window that contain text simple as that like ppl do it on windows.

Though i will never look behind to windows is just i think im not so good searching

---

### Post by ThatCoolGuy220 on 2011-05-30
Though im now learning it without it but i would be cool to see my hello world or a sum app on a window

---

### Post by ThatCoolGuy220 on 2011-05-30
> **nvteighen said:**
> It seems to me that everybody has ignored the central point: explaining how to run things in the terminal.

By default, programs will only work in the console or terminal emulator. To execute it, you have to open a terminal, enter the directory where the program is and type:

```

./<program_name>

```

Try it with your Hello World and it will work.

You can only double-click executables that are GUI programs, only if the required libraries are installed (which is usually the case, so don't worry). 

FYI, the .o file is an intermediate stage of the compilation process, the so-called object code. This file is your program compiled, but not linked to the required libraries to male it run... Let's say it's just the binary translation of your code, but that won't run. These files can be used as static libraries, though, and interrupting compilation at that stage is a very useful step for huge multifile projects (it allows you to recompile only the modified modules and relink everything much faster... well, you'll get it later).


Thanks for clarifying it

---

### Post by TheStroj on 2011-05-30
> **ThatCoolGuy220 said:**
> Though im now learning it without it but i would be cool to see my hello world or a sum app on a window

Even that requires some knowledge of a programming language. Anything that has something to do with a GUI is complex as long is it is not just a blank window (and even that requires a few lines of code - GTK example: init GTK, set size, make it closable, bind event with closing function).

---

### Post by ThatCoolGuy220 on 2011-05-30
Would you recomend me keep on the c++ thing or going to Python

The easiest lenguage i have ever seen was php that is cool

$ for variable

echo"LOL";


Bad thing is it cannot be used for making programs or aplications 
(Non web based)

Also Ill like to make some questions that seem nobody aswered:

- Qt or GTK?

- Window Api does that works on linux?

- Could Python make it without too much halse?

- Should i give up?

- Is there a way to make the application open the terminal when double      
  click it?

- Using Geany is ok for the stuff im trying to accomplish?

- Qt or GTK will work on windows as well?

- Why i couldnt find a guide directly related to linux about programming (  (Up to date one).


Im sorry is just that the Road seems to dark for me I left windows on April but im not saying there is not benefits on linux is just is hard and im like the only one who has it on my town (Though)


And yes sorry for Broken English actually is not my natal lenguage....

---

### Post by matthew.ball on 2011-05-31
> **ThatCoolGuy220 said:**
> Also Ill like to make some questions that seem nobody aswered:

- Qt or GTK?

You could use a widget library like [wxWidgets]("http://www.wxwidgets.org/") to get the native look for either (it's also cross-platform). 

> **ThatCoolGuy220 said:**
> 
- Window Api does that works on linux?

Not entirely sure with this one. But, both Qt and KDE have support for Windows (Qt [here]("http://qt.nokia.com/products/platform/qt-for-windows/"), GTK [here]("http://www.gtk.org/download-windows.html"); they were just found from quick google searches, and I do not know what is involved in setting either up). So, maybe you could consider this route instead.

> **ThatCoolGuy220 said:**
> 
- Could Python make it without too much halse?

Sure. Though just what exactly "it" is, I don't believe you have mentioned.

> **ThatCoolGuy220 said:**
> 
- Should i give up?

Of course not. But do keep in mind, programming requires some pretty serious dedication. It's certainly rewarding, but the rewards don't necessarily come easy.

> **ThatCoolGuy220 said:**
> 
- Is there a way to make the application open the terminal when double click it?

Yep. Though, a bit vague, you might want to explain a bit more here.

> **ThatCoolGuy220 said:**
> 
- Using Geany is ok for the stuff im trying to accomplish?

Sure.

> **ThatCoolGuy220 said:**
> 
- Qt or GTK will work on windows as well?

I think I answered this.

> **ThatCoolGuy220 said:**
> 
- Why i couldnt find a guide directly related to linux about programming (up to date one).

Not sure what you mean here (or you gave up rather quickly). Did you read the [stickies]("http://ubuntuforums.org/showthread.php?t=1766253/") which Ubuntu Programming provides? Probably the best destination from here.

---

### Post by ThatCoolGuy220 on 2011-06-02
@Matthew.ball
Though is marked as solved.

i have to say yes I was  very lazy an after forgetting all the problems that involved the window creation.

I studied  also I talked with my dad which I didn't know, programmed on C, Fox, etc. years ago and actually helped me in some stuff.

I created an application capable of summing 2 numbers, I know is not such a big thing but is a big advantage and yes I should have a good Grasp on the language side first before trying new stuff.

And about The terminal to be opened when double clicked.... well if there is an easy way it would be cool, if not well its also cool.

---

