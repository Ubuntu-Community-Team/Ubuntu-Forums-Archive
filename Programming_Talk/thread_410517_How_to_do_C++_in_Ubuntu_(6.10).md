---
title: "How to do C++ in Ubuntu (6.10) ?"
date: 2007-04-15
forum: Programming Talk
---

### Post by akash.yakovsky on 2007-04-15
Somebody please tell me how to compile and run C++ or C programs in Ubuntu 6.10 (Edgy Eft). It's urgent - I want it badly...

That's all my question is. Give me either a brief or detailed explanation. [email]akash.yakovsky@gmail.com[/email].

Thank you so much.

Akash.

---

### Post by noerrorsfound on 2007-04-15
```
sudo apt-get build-essential
```

I believe this will install gcc for you. Then type:
```
gcc ./yoursource.c
```

---

### Post by beathan on 2007-04-15
> **noerrorsfound said:**
> ```
sudo apt-get build-essential
```

I believe this will install gcc for you. Then type:
```
gcc ./yoursource.c
```

For C++, I believe you're going to want to use g++, not gcc. So...

```
g++ ./yoursource.cpp
```

---

### Post by ampanab on 2007-04-15
Hey there,
I'm in a c++ class and I had the same problem programming under linux.
Luckily I stayed up for the last 20 hours trying to find the answer.
It's rather simple, here we go:
1st open up a terminal under applications and accessories
2nd open up your text editor or you can do this on the terminal by:
              sudo gedit myprogram.cpp
the text editor will automatically open up. but notice that there is no existing file unless you save it after putting your codes in.
3rd add your code within the text editor and when satisfied save and exit
4th on the terminal make sure you're in the same directory as the cpp file or else the compiler won't recognize it, type:
              g++ myprogram.cpp -o myprog
the output myprog is the executable but not the same in windows.
when the compiler is finished, on the terminal type:
             ./myprog
notice there's a period before the slash like this (.) and then a slash
then the program should work according to what you wrote in the code
hope this helps
hakunah matata <-i've always wanted to say that in a thread...lol

---

### Post by rbprogrammer on 2007-04-16
or if you might have more than one file in a "project", you could use and IDE.  i use kdevelop since i use kubuntu.  to install that just do the two commands:
```
sudo apt-get build-essential
sudo apt-get kdevelop
```

or if you use ubuntu, there are IDE specifically designed for that desktop environment. like anjuta... i'm sure there are plenty of others for both desktop environments.

---

### Post by zoogTHOMzoog on 2007-04-16
I generally use Eclipse  with the eclipse-cdt package because I also program in Java. I use g++ to compile from the command line. You can use gcc but it's got a bunch of funky compiler specific stuff so, sometimes you can get weirdo compiler errors (especially if you are used to other platforms) that make no sense (to me at least). 

But, gcc should work in a pinch, it supports C, Objectic C, C++, Java, Ada, etc. Just make sure you have all the libraries installed (which I think you should by default). Eclipse's code completion is nice (again, it's what I am used to)... but Anjuta and Kdevelop are also good.

---

### Post by ampanab on 2007-04-16
that's what i'm hearing also...but at times at compile time i get errors...there's other forums out there (not sure what it is, sorry i'm no help there) that has specific packages that you'd need installed in order for your programs to work. for example i use irrlicht and there's at least one i can think of that i had to manually install in order for the example programs to work

---

### Post by RedSquirrel on 2007-04-16
> **ampanab said:**
> Hey there,
I'm in a c++ class and I had the same problem programming under linux.
Luckily I stayed up for the last 20 hours trying to find the answer.
It's rather simple, here we go:
1st open up a terminal under applications and accessories
2nd open up your text editor or you can do this on the terminal by:
[COLOR=Red]               sudo gedit myprogram.cpp[/COLOR]
the text editor will automatically open up. but notice that there is no existing file unless you save it after putting your codes in.


Correction:

You don't need to use sudo to edit files under your home directory. You only need to use sudo to edit files that require you to have root privileges (for example, a system file such as /etc/X11/xorg.conf).

And if you're going to use a graphical editor for editing system files, it's safer to use **gksudo**:

```
gksudo gedit <filename>
```See [Running sudo graphically]("http://www.psychocats.net/ubuntu/graphicalsudo").

---

### Post by dave_567 on 2007-04-16
I would not recomend using root privledges for any early programming at all.  Simple use gedit in the normal mode.  Fron the comand line enter this.

```


gedit <filename>


```

The rest of the directions are fine.  You do not need root privledges for simple codeing.  It can and most likely will get you into trouble.  Any of the files you generate in your own area can be modified any time you want to.

Also get used to using a make file.  It is a simple text file that will execute several commands  in the compiler for you.  It will help out as it can realy get tiresome typing in the full command like each time.  Use a google search to find some good make file tutors.

---

### Post by zoogTHOMzoog on 2007-04-18
> **dave_567 said:**
> I would not recomend using root privledges for any early programming at all.  Simple use gedit in the normal mode.
Yeah, if you use sudo, you can run into trouble with ownership (i.e. root owns the file) that are added hassles for someone trying to learn Linux and C++ (if you want more info on this man or google chmod and chown).

 > **dave_567 said:**
> Use a google search to find some good make file tutors.
Make files are the only way to go in any language (C, C++, C#, Java, etc)!

Happy coding!
:guitar:

---

### Post by fatma ben said on 2009-04-21
Hello, please I want to know how can I view a message on the terminal

---

### Post by m0sh on 2009-09-12
not to bring up a really... really old thread.  But does this work in Jaunty as well?  I'm having some trouble getting it to work.

---

### Post by phrostbyte on 2009-09-12
> **m0sh said:**
> not to bring up a really... really old thread.  But does this work in Jaunty as well?  I'm having some trouble getting it to work.

For the toolchain (compiler, linker, etc):
sudo apt-get build-essential

A simple IDE:
sudo apt-get install geany

Type in your C++ code and hit "Execute".

---

