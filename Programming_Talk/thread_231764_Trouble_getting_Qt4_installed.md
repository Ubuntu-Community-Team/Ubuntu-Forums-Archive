---
title: "Trouble getting Qt4 installed"
date: 2006-08-07
forum: Programming Talk
---

### Post by Luggy on 2006-08-07
Hi, I'm having some trouble getting Qt4 installed... that or I have it installed correctly and I'm just not using it right.

I've gotten the source,
extracted it, 
ran ./configure -prefix /usr/include/qt4
make
sudo make install

but when I try and run a simple hello world program I get some error messages:
```
#include < QApplication >
#include < QLabel >
int main( int argc, char *argv[] )
{
        QApplication app(argc, argv);
        QLabel *label = new QLabel(" Hello Qt!");
        label->show();
        return app.exec();
}

```

```
paul@dapper:~/dev/c++/qt tut$ g++ foo.cpp
foo.cpp:1:26: error:  QApplication : No such file or directory
foo.cpp:2:20: error:  QLabel : No such file or directory
foo.cpp: In function ‘int main(int, char**)’:
foo.cpp:5: error: ‘QApplication’ was not declared in this scope
foo.cpp:5: error: expected `;' before ‘app’
foo.cpp:6: error: ‘QLabel’ was not declared in this scope
foo.cpp:6: error: ‘label’ was not declared in this scope
foo.cpp:6: error: expected type-specifier before ‘QLabel’
foo.cpp:6: error: expected `;' before ‘QLabel’
foo.cpp:8: error: ‘app’ was not declared in this scope
paul@dapper:~/dev/c++/qt tut$
```


Any help you guys can give me would be much apprectiated.

---

### Post by KaeseEs on 2006-08-08
It appears that your main problem is that g++ can't find your QApplication and QLabel headers.  A workaround would be to locate copies of these headers and move them to your build directory, then include with quotes:
```
#include "QApplication"
#include "QLabel"
```

Once you get this working, you can try to figure out why your headers are undetected at their normal locations, then migrate back to normal shift-character includes.

---

### Post by Luggy on 2006-08-08
Well that would be a work around...

I tried that out but as it turns out A requires B which requires C etc etc...
If I were to keep that up I'd have the entire library in my working directory. I think I'd be better off trying to fix the problem with my program can't pick up my libraries.

Trolltech documentation talks about specifying the PATH but I'm not sure if I'm doing it right. [docs]("http://doc.trolltech.com/4.1/install-x11.html") Here is my .bash_profile

```
[# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
    PATH=/usr/include/qt4/:$PATH
    export PATH
fi

```

---

### Post by asimon on 2006-08-08
> **Luggy said:**
> 
I've gotten the source,
extracted it, 
ran ./configure -prefix /usr/include/qt4
make
sudo make install

/usr/include/qt4 is a very strange prefix. I suppose your libs end up in /usr/include/qt4/libs and the include files /usr/include/qt4/include.

> **Luggy said:**
> 
```
paul@dapper:~/dev/c++/qt tut$ g++ foo.cpp
foo.cpp:1:26: error:  QApplication : No such file or directory
foo.cpp:2:20: error:  QLabel : No such file or directory
foo.cpp: In function ‘int main(int, char**)’:
foo.cpp:5: error: ‘QApplication’ was not declared in this scope
foo.cpp:5: error: expected `;' before ‘app’
foo.cpp:6: error: ‘QLabel’ was not declared in this scope
foo.cpp:6: error: ‘label’ was not declared in this scope
foo.cpp:6: error: expected type-specifier before ‘QLabel’
foo.cpp:6: error: expected `;' before ‘QLabel’
foo.cpp:8: error: ‘app’ was not declared in this scope
paul@dapper:~/dev/c++/qt tut$
```

You need to tell g++ where to find the include files. I.e. something like
```

$ g++ -I/usr/include/qt4/include foo.cpp

```
But this is not enough. You also need to tell it what libraries to link against, i.e. something like
```

$ g++ -I/usr/include/qt4/include -L/usr/lib/include/qt4/lib -lQtGui -lQtCore -lpthread foo.cpp
```

You should better use some automation here, like for example Qt's qmake. I.e. put your foo.cpp program in a directory called 'foo' and run 'qmake -project'. That will scann the current directory for source files and create a foo.pro project file. Then call 'qmake' which generates a Makefile from the .pro file. Then a simple 'make' will build you program 'foo' and if everything works as expected it should take care of all the needed compiler options.

I hope this works, sadly my Qt skills are a little bit rusty.

EDIT: You make want to look at the [Qt Tutorial](http://doc.trolltech.com/4.1/examples.html), they use qmake there too.

---

### Post by Luggy on 2006-08-08
Awesome!
I had tried using qmake in the past, but I wasn't creating that project file correctly. Thanks for showing me how![-o<

---

### Post by tomiu on 2007-02-21
> **asimon said:**
> 
You should better use some automation here, like for example Qt's qmake. I.e. put your foo.cpp program in a directory called 'foo' and run 'qmake -project'. That will scann the current directory for source files and create a foo.pro project file. Then call 'qmake' which generates a Makefile from the .pro file. Then a simple 'make' will build you program 'foo' and if everything works as expected it should take care of all the needed compiler options.


Thx for showing how qmake works..:)

---

