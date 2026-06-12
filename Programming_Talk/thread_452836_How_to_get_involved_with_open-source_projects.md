---
title: "How to get involved with open-source projects?"
date: 2007-05-23
forum: Programming Talk
---

### Post by kobewan on 2007-05-23
I'm sorry if this kind of discussion has already taken place on the board; I've searched around a bit but didn't find anything relevant. I had assumed that a topic like this would've been stickied, or at least had a prominent position  on this board.

My situation is this: I've taken a semester of C (and some very basic C++) programming in the first year of college. I've also taken somewhat of an interest in programming, so I bought and went through, cover-to-cover, a book on C (C Primer Plus, by Stephen Prata). I assume that I've now gotten the basics, and would like the move on to actual applications. At the same time, I've been using Ubuntu and other OSS exclusively for almost a year now. 

I figure the next logical step is to go through the source code of a few applications, get a feel for them, and then either start a project of my own or jump onto an existing one. The problem is that it still seems like I'm not ready; I can't make heads or tails of any of the programs that I've looked at. Now, I realize that I won't be able to understand the kernel or other low-level projects like wine. However, I'm hoping that there exists some guide or tutorial or list of help files that will ease the transition from book-learning to practical applications. Does anybody know of any resource that aims to introduce fledgling programmers to the world of GNU/Linux? Any recommendations on where to start? Is there a list of library functions that I should know, special indentation guidelines I should follow, any other programming practice to strictly follow etc.? Are there any small programs that people should look at first to get a hang of things? I don't mind working on little things at first; Firefox extensions or the like. I'm just not sure where to start. 

Also, does anybody recommend learning C++ as well, before jumping in? I use KDE, and it seems like all of their development resources are geared towards C++ programmers. I do plan on learning C++ in the future, but I'd like to really get a good hold on C first.

---

### Post by seamless on 2007-05-23
> **"kobewan"]Is there a list of library functions that I should know, special indentation guidelines I should follow[/QUOTE]
If you're going to work on an existing project find out for that project. Basically if you are working on a GTK based app then learn about GTK, if you are leaning about a Qt based app learn about Qt. Every project you encounter will do things a little differently especially when it comes to indentation.

[QUOTE=&#8221 said:**
> I figure the next logical step is to go through the source code of a few applications, get a feel for them, and then either start a project of my own or jump onto an existing one. The problem is that it still seems like I'm not ready; I can't make heads or tails of any of the programs that I've looked at.
There is not getting around this. All it means is you need more practice. Spend some time making some simple programs and look at existing ones some more. Instead of looking at an entire project try tracing through main. Get an idea of what it does. Then move on to the functions it calls. Work slowly and understand the parts. If you know when something should be used you are halfway there.

> **&#8221 said:**
> Are there any small programs that people should look at first to get a hang of things? I don't mind working on little things at first; Firefox extensions or the like. I'm just not sure where to start.
Pick something that interests you and is related to the tools you want to use. If you have no desire making Firefox extensions or working with Java Script then don't look at them. If you want to work with a desktop application that is written in C then your best best is to look at a GTK app.

> **&#8221 said:**
> Also, does anybody recommend learning C++ as well, before jumping in? I use KDE, and it seems like all of their development resources are geared towards C++ programmers. I do plan on learning C++ in the future, but I'd like to really get a good hold on C first.
If you are going to work on a KDE app then you will have to learn C++. KDE and to a greater extent the toolkit it uses (Qt) are C++ specific. Almost all development is going to happen in C++.

---

### Post by treak007 on 2007-05-24
Make an account on sourceforge.net and look for some projects that interest you. When you find some, message their admin to see if they could use your help.

---

### Post by kobewan on 2007-05-24
> **seamless said:**
> 
There is not getting around this. All it means is you need more practice. Spend some time making some simple programs and look at existing ones some more. Instead of looking at an entire project try tracing through main. Get an idea of what it does. Then move on to the functions it calls. Work slowly and understand the parts. If you know when something should be used you are halfway there.

Pick something that interests you and is related to the tools you want to use. If you have no desire making Firefox extensions or working with Java Script then don't look at them. If you want to work with a desktop application that is written in C then your best best is to look at a GTK app.

This is one of the problems; I've looked at the source of a few projects, and I can't even seem to locate main. There are a lot of library and header files linked together, and I'm not sure where to start. Could you maybe recommend a simple program that would be easy to start off with? Thanks.

---

### Post by ankursethi on 2007-05-24
[http://directory.fsf.org](http://directory.fsf.org) lists the common UNIX programs. Many of these are only a few hundered lines long. I suggest you take a look at them.

---

### Post by pmasiar on 2007-05-24
> **kobewan said:**
> I'm hoping that there exists some guide or tutorial or list of help files that will ease the transition from book-learning to practical applications.

Such a book was printed in 79, Wetherell "Etudes for programmers" and not reprinted since. :-(

>  Is there a list of library functions that I should know, special indentation guidelines I should follow, any other programming practice to strictly follow etc.?...  I'm just not sure where to start.  

Every project has own rules. Start with picking a project. Pick a feature you would like to add. Any project will be interested with new developer. My personal favorite for C to join would be Midnight Commander.

Consider also learning Python (see my sig). It allows you to solve many problems faster than in C (more fun hacking), and for speed you can link to fast C libraries.

EDIT: see [this blog post](http://www.nedbatchelder.com/blog/200705.html#e20070523T210157)

---

### Post by seamless on 2007-05-24
> **kobewan said:**
> This is one of the problems; I've looked at the source of a few projects, and I can't even seem to locate main. There are a lot of library and header files linked together, and I'm not sure where to start. Could you maybe recommend a simple program that would be easy to start off with? Thanks.
Since you use KDE you really should learn C++. KDE apps also are really easy to get started learning their source. I'll give you a quick example.

Let's take Dolphin (the new file manager that will be default in 4). For this I'm going to use the svn view. The project is located at [http://websvn.kde.org/trunk/KDE/kdebase/apps/dolphin/]("http://websvn.kde.org/trunk/KDE/kdebase/apps/dolphin/"). That is svn trunk for KDE. It's in KDE (the project), kdebase (the package), apps and finally dolphin. Everything in KDE follows this directory structure so if you need to look up a something referenced by the app it's not that hard to find.

Now in the source directory there are a lot of files. No worries though, this is a KDE app written in Qt. They all (should) follow the same layout of main being in [main.cpp]("http://://websvn.kde.org/trunk/KDE/kdebase/apps/dolphin/src/main.cpp?revision=651981&view=markup"). Let's look at main a bit now.
```
static KCmdLineOptions options[] =
```
This does exactly what it says, it puts the command line arguments into the options array. This way you can give it a location and it will open to that location.

```
int main(int argc, char **argv)
{
	KAboutData about(
```
Your standard main function. It starts by settings all the KDE specific about data (name, version, and so on). This will be used later on in places like the about dialog.

```
KCmdLineArgs::init(argc, argv, &about);
KcmdLineArgs::addCmdLineOptions(options);
```
Here is some KDE magic. It initializes the application based on the arguments and sets the about data.

```
DolphinApplication app;
```
This creates a new DolphinApplication object. You can see what this does by looking at [ dolphinapplication.h]("http://http://websvn.kde.org/trunk/KDE/kdebase/apps/dolphin/src/dolphinapplication.h?revision=665393&view=markup") and [dolphinapplication.cpp]("http://http://websvn.kde.org/trunk/KDE/kdebase/apps/dolphin/src/dolphinapplication.cpp?revision=665393&view=markup").

```
#ifdef __GNUC__ #
warning TODO, SessionManagement 
#endif
```
Session management isn't implemented yet so everything after this and in the #if 0 is ignored

```
return app.exec();
```
Starts the app.

That's it. Just walk through main and in the case of C++ look at what the objects do. A well written application will make it very easy to understand what is going on. For instance in src/dolphinapplication.h
```
void refreshMainWindows();
int openWindow(const KUrl& url);
void removeMainWindow(DolphinMainWindow* mainWindow);
```
Just by looking at the function names you can understand what they do.

Like I said. There are no tricks. Just find an app you would like to work on and that interests you and start walking through the source. If you are having a lot of problems finds things like main then your best bet is to download all the source and open every file in a text editor that can search through multiple files. Just search for main and everything it references and walk though it.

---

### Post by kobewan on 2007-05-24
Alright, excellent. I'm going to start off on learning C++, and in the meantime look at simple, common UNIX programs. If I end up liking C more than C++, I'll switch to GTK+. Thanks for pointing me in the right direction!

---

