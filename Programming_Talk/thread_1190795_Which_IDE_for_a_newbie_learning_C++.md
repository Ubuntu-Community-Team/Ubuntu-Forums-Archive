---
title: "Which IDE for a newbie learning C++"
date: 2009-06-18
forum: Programming Talk
---

### Post by chipppy on 2009-06-18
Good Evening

I am a newbie to programming I have chosen to learn C++.
I have read through a book or two and now want to have a go at the writing of some programs (the exercises out of the books)

I read through the stick on IDE's and OMG there is such a huge choice.  Which one is the question.

I have installed a few of the one discussed in the sticky and so far had no luck in getting the classic "hello world" to work.

I have tried to use Vim, MonoDevelop, Codelite, bluefish, code::blocks, Eclipse, Anjunta.  different IDE have complained about different things.  
Mono complained about missing bits.  I think I need to download some stuff from Sun and install it but I dont really understand the instruction on how to do that.
code::blocks complained that there is nothing to build/run.  and so on.

So obviously I need spend some time getting one to work and get my head around what is required to get it to work.  But the question is which one.

I would love some advice as to which one to invest the time to get working and get my head around
I am looking for an IDE that is good for a newbie to use.  
I will need to do lots of debugging so a good debugging tool is really important.
I would prefer t to be user friendly or at least logical.
I would love the IDE to have good documentation so I can read through the manual to learn ho to use it fully as I develop as a programmer.

As silly as this sound please think back to your newbie days and not about your current favourite IDE.  What would you recommend to a newbie like me.

Any and all assistance is greatly appreciate.

Cheers
chipppy

---

### Post by Mirge on 2009-06-18
Until you become more experienced with C++, stick with a very simple IDE or text editor. My recommendation is Geany (it's in repo's, but to get v0.17 you'll hafta compile from source or hit up launchpad.net). Install the GDB plugin if you want to debug programs too.

Once you're more familiar, I'd switch to something better for C++ like Code::Blocks, but Geany should last you for a good while until you're through with the basics. Even something more simple like gedit or kate would prove sufficient if you didn't mind compiling from command line.

---

### Post by stevescripts on 2009-06-18
+1 for starting out with a text editor, and learn to build from the command line...

By the time your projects become bigger, a choice of IDE will be much easier for you to make.

Steve

---

### Post by xebian on 2009-06-18
> **chipppy said:**
> Good Evening

I am a newbie to programming I have chosen to learn C++.
I have read through a book or two and now want to have a go at the writing of some programs (the exercises out of the books)

I read through the stick on IDE's and OMG there is such a huge choice.  Which one is the question.

I have installed a few of the one discussed in the sticky and so far had no luck in getting the classic "hello world" to work.

I have tried to use Vim, MonoDevelop, Codelite, bluefish, code::blocks, Eclipse, Anjunta.  different IDE have complained about different things.  
Mono complained about missing bits.  I think I need to download some stuff from Sun and install it but I dont really understand the instruction on how to do that.
code::blocks complained that there is nothing to build/run.  and so on.

So obviously I need spend some time getting one to work and get my head around what is required to get it to work.  But the question is which one.

I would love some advice as to which one to invest the time to get working and get my head around
I am looking for an IDE that is good for a newbie to use.  
I will need to do lots of debugging so a good debugging tool is really important.
I would prefer t to be user friendly or at least logical.
I would love the IDE to have good documentation so I can read through the manual to learn ho to use it fully as I develop as a programmer.

As silly as this sound please think back to your newbie days and not about your current favourite IDE.  What would you recommend to a newbie like me.

Any and all assistance is greatly appreciate.

Cheers
chipppy

If you use KDE, then KDEvelop is good or QTCreator.  You are not only learning C++ but QT framework as well.

---

### Post by NielsBhor on 2009-06-18
In my early programming days, I didn't use any IDEs. I used gedit and played with trial and error debugging technique.

---

### Post by Mirge on 2009-06-18
> **xebian said:**
> If you use KDE, then KDEvelop is good or QTCreator.  You are not only learning C++ but QT framework as well.

If you don't have a firm grasp of C++ and OOP concepts, you're not learning Qt framework. It's only going to introduce more complexity by using a big fancy IDE this early on. Learn the language & concepts first, then pick a bigger IDE that suits you if you wish.

---

### Post by fr4nko on 2009-06-18
> **Mirge said:**
> Until you become more experienced with C++, stick with a very simple IDE or text editor. My recommendation is Geany (it's in repo's, but to get v0.17 you'll hafta compile from source or hit up launchpad.net). Install the GDB plugin if you want to debug programs too.
I'm 100% in agreement with that. A simple IDE like geany will be excellent, you should focus on programming fundamentals at the beginning. I strongly advice you to learn how 'make' works, even if nowadays 'make' is considered obsolete, especially for big projects, it is still very useful to know how it works because for many small or medium projects 'make' is just fine. You should also learn the fundamentals of gdb since it is THE debugger on GNU/linux.

Something good could be also to learn emacs, but this is only if you have a real hacker spirit! :-)

Francesco

---

### Post by PC-XT on 2009-06-18
I like to use text editors, but sometimes enjoy IDE functionality like autocomplete and allowing code to be collapsed. I learned C++ with text editors, Quincy (a fairly simple, uncomplicated C++ editor), and Dev-Cpp to get a feel for simple language and some better features as well, when I wanted them.

---

### Post by monraaf on 2009-06-18
> **PC-XT said:**
> I like to use text editors, but sometimes enjoy IDE functionality like autocomplete and allowing code to be collapsed.

Auto complete and code folding are standard features of Vim ;)

---

### Post by regal_dunce on 2009-06-18
I go through these cycles, where once every year or so I decide that it's time to finally start using a nice IDE for c++.  Then I use it for about a week or so.  But then, for some reason or another, I always end up back with emacs and my sweet sweet keyboard shortcuts...

In short, learning c++ will be way better if you simply choose a text editor that has good syntax highlighting, and you learn to compile from the terminal.  It's probably less work to do this than to learn the ins and outs of a full-fledged IDE.

---

### Post by Can+~ on 2009-06-18
Starting your first language mixed with an IDE, makes you IDE-dependant and you'll fail to compile more than the basic configuration that the IDE defaults to.

As mentioned above, learn how to compile "by hand" so you can understand later how to build properly your own projects with an IDE.

For me: [Eclipse with the cdt plugin]("http://www.eclipse.org/downloads/").

---

### Post by ranthal on 2009-06-18
I'm going to echo what most people have said here and tell you start with a text editor and then move on to an IDE.  Starting with an IDE will only cause you to miss finer points of the language that down the road will cause complex problems deriving from simple issues.  So with that in mind I'd say:

1. vim/emacs

I personally use vim but I know a lot of people who started with emacs and are hooked.

2. slickEdit/eclipse

I love slickEdit, but eclipse is free.

---

### Post by |{urse on 2009-06-18
Okay, i agree (kind of with most everyone) It's good to know how to write code in nano and compile with gcc/g++ via commandline. Really for noobs the best way to learn (imo) is something where they can look at the code in the same window and click a button to compile "easy peasy", the process of compiling code isn't really a skill, writing it is. Geany is nice. No sense in making things more confusing than they need to be (yet). Then of course move on to code::blocks when it's functionality becomes necessary.

---

### Post by fr4nko on 2009-06-19
> **regal_dunce said:**
> I go through these cycles, where once every year or so I decide that it's time to finally start using a nice IDE for c++.  Then I use it for about a week or so.  But then, for some reason or another, I always end up back with emacs and my sweet sweet keyboard shortcuts...
That's funny but for me it's exactly the same - I always came back to use the **old good emacs** and my keyboard shortcuts that are deeply wired into my brain... I cannot get used to fancy IDEs even if in principle they seems to be a good thing.

Francesco

---

### Post by mmix on 2009-06-19
my suggestion for newbie is trying every ide you can get. for example, if you don't mind platform, i would suggest that visual studio 2010 rc version.

---

### Post by credobyte on 2009-06-19
Simple text editor with syntax highlighting would be enough, though, Geany is my favorite ( easy to use and have an option to compile/execute your projects ).

---

### Post by pokerbirch on 2009-06-20
I tried loads of text editors and IDE's and finally settled with Code::Blocks. It's very user friendly. Code completions are a GOOD thing. I disagree with people who say that code completion makes you lazy. For me, code completion has been an excellent way of learning the language without constantly flipping back and forth to the manual. We all have preferences, but i find it quite bizarre how a lot of people seem to enjoy doing things the hard way...

---

### Post by Regele IONESCU on 2009-06-28
Hi, everybody!

I just started to learn Python. Now I discovered C++. In Python is very simple: I have Python IDE, I write the code and I could check and execute it.

Now, the problem is how do I do it for C++??? I installed gcc, g++, Codelite but I am not able to run a simple ready made program like: 

// my first program in C++

#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!";
  return 0;
}


I understood that one could write all the instructions in a text editor. But how do you save the file? What extension, how do you execute it or how do you make it executable? I tried to save it as hello.c but this done nothing. In Codelite the Build menu is not active. Also, when I start Codelite I get the message: 

[I]CodeLite detected that there is no external symbols database attached, nor it can not find any. Would you like to create one?
(attaching external symbols database improves CodeCompletion significantly)[/I] Is that database already installed on Ubuntu 9.04, do I have to install it from somwhere???

Heeeeeeeeeeeeeeeeeeeelp!


God help us all!
Christian I. Ionescu

---

### Post by halfpower on 2009-06-28
This may depend somewhat on how you want to learn, but I would say go with a text editor.  If you are using Gnome with Ubuntu, use gedit.

---

### Post by Can+~ on 2009-06-28
> **Regele IONESCU said:**
> I understood that one could write all the instructions in a text editor. But how do you save the file? What extension, how do you execute it or how do you make it executable? I tried to save it as hello.c but this done nothing. In Codelite the Build menu is not active. Also, when I start Codelite I get the message: 

God help us all!
Christian I. Ionescu

Ok, you have the IDE syndrome. You should understand that:

An IDE hands the code to a compiler+linker+assembler to build a binary file which is a set of instructions in assembly your processor can read.

The IDE does nothing special than offer you features like syntax highlighting, code completion, etc. You could write your code on anything, even windows' notepad could do. The compiler accepts a file in C/C++ syntax and builds an executable from it (it's deeper than that, but let's keep it simple)

So, to compile your code do the following:

[LIST]
[*]Save your hello.cpp file anywhere, let's say your Desktop
[*]Open a terminal, go to your Desktop.
[*]Write [FONT="Courier New"]g++ hello.cpp -o hello[/FONT]
[*]This will generate an executable code named [FONT="Courier New"]hello[/FONT], make it executable with [FONT="Courier New"]chmod u+x hello[/FONT]
[*]Now, finally do [FONT="Courier New"]./hello[/FONT]
[/LIST]

Now, if you want an IDE that does this automatically, install **Geany**, great for starters.

```
sudo apt-get install geany
```

---

### Post by Catalyst2Death on 2009-06-28
Hi,

I know the OP asked for a simple IDE, but I find it odd that no one suggested emacs.  I started using geany, couldn't get anything to work, and emacs and vi were the only two text editors available on my remote machine.  I just went through the tutorial and in an hour was able to use emacs well enough to right code and compile it using the terminal.  

Since then emacs has grown with me and now functions as a complete IDE allowing me to spawn running processes of the code, compile and debug all in one window with the power of emacs shortcuts.  Check this article out for using emacs as an IDE:
[http://www.linuxjournal.com/article/5765](http://www.linuxjournal.com/article/5765)

---

### Post by Jonas thomas on 2009-06-28
I'm sort of a hard core vb6 programmer, but still a bit of a newb as far as C++.   I found code::blocks to be quite appealing to me.
It's cross plattform so what you learn in Linux can also be applied to Mac as well as that other operating system....
Hear's a pretty good how to.
[http://www.sci.brooklyn.cuny.edu/~goetz/codeblocks/]("http://www.sci.brooklyn.cuny.edu/~goetz/codeblocks/")

---

### Post by Regele IONESCU on 2009-06-28
> **Can+~ said:**
> Ok, you have the IDE syndrome. You should understand that:

An IDE hands the code to a compiler+linker+assembler to build a binary file which is a set of instructions in assembly your processor can read.

The IDE does nothing special than offer you features like syntax highlighting, code completion, etc. You could write your code on anything, even windows' notepad could do. The compiler accepts a file in C/C++ syntax and builds an executable from it (it's deeper than that, but let's keep it simple)

So, to compile your code do the following:

[LIST]
[*]Save your hello.cpp file anywhere, let's say your Desktop
[*]Open a terminal, go to your Desktop.
[*]Write [FONT="Courier New"]g++ hello.cpp -o hello[/FONT]
[*]This will generate an executable code named [FONT="Courier New"]hello[/FONT], make it executable with [FONT="Courier New"]chmod u+x hello[/FONT]
[*]Now, finally do [FONT="Courier New"]./hello[/FONT]
[/LIST]

Now, if you want an IDE that does this automatically, install **Geany**, great for starters.

```
sudo apt-get install geany
```

Thaaaaaaaaaaaaank youuuuuuuuuu!

---

### Post by master_kernel on 2009-06-28
Personally, I prefer Netbeans (what with auto-code completion and all). But it's just whatever fits your style!

---

### Post by Mirge on 2009-06-28
I still use Geany for everything but C++. For C++ (including using Qt4) I use Eclipse CDT with Qt4 integrated. I went from Geany to Code::Blocks & Qt Creator... to Eclipse CDT. I like Eclipse the best.

---

### Post by colau on 2009-08-17
> **Mirge said:**
> I still use Geany for everything but C++. For C++ (including using Qt4) I use Eclipse CDT with Qt4 integrated. I went from Geany to Code::Blocks & Qt Creator... to Eclipse CDT. I like Eclipse the best.
Is code completion option available in Geany and Code::Blocks?

---

