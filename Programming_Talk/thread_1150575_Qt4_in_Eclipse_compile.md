---
title: "Qt4 in Eclipse compile"
date: 2009-05-06
forum: Programming Talk
---

### Post by buonaparte on 2009-05-06
Hello!

First of all excuse me for my english. I'm having a big problem, I'm using Eclipse for C++ programming (Eclipse - CDT allready installed), yesterday tried to compile a simple Qt4 tutorial program, like a window called "Hello World!" (preaty standard :)).
But that was not so easy as I imagined at first look, I read some info in internet about how to make Eclipse work with Qt, so I installed Qt4 and other dependencies in Ubuntu Jaunty (Gnome) and a Qt-Eclipse package.

I don't understand, now in Eclipse I have Qt - C++ perspective (good), but wen I try to compile I get in Problems - nothing and in Console is written "make: *** No rule to make target `debug'.  Stop. in qt-eclipse". For Eclipse is mentioned to use executables for Qt form "/usr/bin" and headers from "/usr/include/qt4". What to do I do not know, but I really wanted to give Qt a try.

Please Help! :(

---

### Post by Graf+ on 2009-05-13
I don't know , will you be satisfied with it or not, but I (and numerous people) have the same problem.
Here is my quick fix (if you want to create an application and just have very little time to play with Eclipse) I already posted at 
"Went to the workspace directory, then to the project directory (/home/pavel/workspaces/Test), did qmake first, then make. Both the qmake and make processes not failed, the executable was created with the name Test, I managed to run it and saw an empty window (exactly what empty project is about). So this is problem with Eclipse, not Qt. Still have no idea how to fix it, doing qmake and make by hand is not a solution, why I need Eclipse then?
"
In general the "No rule to make target" means that no Makefile found. Makefile should be created by Qmake.

---

### Post by samjh on 2009-05-13
> **buonaparte said:**
> I don't understand, now in Eclipse I have Qt - C++ perspective (good), but wen I try to compile I get in Problems - nothing and in Console is written "make: *** No rule to make target `debug'.  Stop. in qt-eclipse". For Eclipse is mentioned to use executables for Qt form "/usr/bin" and headers from "/usr/include/qt4". What to do I do not know, but I really wanted to give Qt a try.

Ubuntu does not have a package for Eclipse's Qt plugin.  So I suspect that whatever method you used to install the Qt plugin for Eclipse was wrong.

I've personally found learning Qt using only a simple text editor and the command-line was far easier than using any IDE.  So I suggest ditching Eclipse and just using a text editor (eg. gedit) and the command-line terminal.

For example, all you need to do to make a "hello world" program in Qt using a text editor and terminal is:

1. Create a directory for your qt program (eg. ~/qtprograms/helloworld)
```
mkdir ~/qtprograms/helloworld
```

2. Type the code below into a text editor and save it as main.cpp
```
#include <QApplication>
#include <QPushButton>

int main(int argc, char* argv[])
{
	QApplication app(argc, argv);

	QPushButton hello("Hello world!");
	hello.resize(100, 30);

	hello.show();
	
	return app.exec();
}
```

3. Use the terminal to navigate into your program's directory.  Example:
```
cd ~/qtprograms/helloworld
```

4. Run qmake -project to generate the .pro Qt project file
```
qmake -project
```

5. Run qmake to create the Makefile for building
```
qmake
```

6. Run make to compile into an executable
```
make
```

At the end, you should get a ./helloworld executable.  Try it and post here if you need more help. :)

---

### Post by Graf+ on 2009-05-16
> **samjh said:**
> Ubuntu does not have a package for Eclipse's Qt plugin.  So I suspect that whatever method you used to install the Qt plugin for Eclipse was wrong.

What Ubuntu does not have package for Eclipse's Qt plugin doesn't mean that I can't install Qt plugin correctly. I followed the instructions found there - [http://www.infinitedesigns.org/archives/210](http://www.infinitedesigns.org/archives/210). Many people posted that it worked. But I and the topic starter were not so lucky... I have QT C++ perspective, I can write code, but can't compile it.
> **samjh said:**
>  Use the terminal to navigate into your program's directory.  Example:
```
cd ~/qtprograms/helloworld
```4. Run qmake -project to generate the .pro Qt project file
```
qmake -project
```5. Run qmake to create the Makefile for building
```
qmake
```6. Run make to compile into an executable
Oh, yeah, that's exactly what I do now.
I use Eclipse as a text editor and compile and run Qt application from terminal.
That's very uncomfortable - swith to terminal each time I modify code in Eclipse.
And I can't debug application - if I make mistakes all I  see is 'Segmantation fault' in terminal. That gives me no idea what I did wrong.
I am pretty sure, that there is a way to develop Qt applications in Eclipse.

---

### Post by XenonGP on 2009-11-18
Hi, I got the solution.

The problem is that eclipse uses qmake of QT3 instead of QT4... Look:
looking for qmake, i get this:
```

gaetan@altare:~$ ls -la /usr/bin/qmake
lrwxrwxrwx 1 root root 23 2009-11-10 15:05 /usr/bin/qmake -> /etc/alternatives/qmake

```and following the symlink:
```

gaetan@altare:~$ ls -la /etc/alternatives/qmake 
lrwxrwxrwx 1 root root 18 2009-11-10 15:05 /etc/alternatives/qmake -> /usr/bin/qmake-qt3

```To fix the problem, just type
```

gaetan@altare:~$ sudo rm -f /etc/alternatives/qmake && sudo ln -s /usr/bin/qmake-qt4 /etc/alternatives/qmake

```Let's get back to code.

Best,
XenonGP

---

### Post by Jean85 on 2010-03-11
I had the same problem, but the links to qmake in /usr/bin were all right. The problem was that Eclipse had wrong Include & bin path for Qt.

---

### Post by EricTheCab on 2010-09-05
A big "Thank you" to [XenonGP]("http://ubuntuforums.org/member.php?u=959250").
It was exactly what I need to execute to solve my problem.
):P

---

