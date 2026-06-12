---
title: "Platform SDK"
date: 2008-05-10
forum: Programming Talk
---

### Post by eeboy on 2008-05-10
In Windows I have the Platform SDK to reference. I assume similar documentation is available in the Linux world. What is it called and how do I get it? Thanks!

---

### Post by LaRoza on 2008-05-10
> **eeboy said:**
> In Windows I have the Platform SDK to reference. I assume similar documentation is available in the Linux world. What is it called and how do I get it? Thanks!

For those of us that don't program for Windows (hint: this is a Linux forum), could you explain what the "Platform SDK" is?

That is like me going on a Windows forum and asking how to get the man pages for the doskey command.

---

### Post by LaRoza on 2008-05-10
> **LaRoza said:**
> For those of us that don't program for Windows (hint: this is a Linux forum), could you explain what the "Platform SDK" is?

That is like me going on a Windows forum and asking how to get the man pages for the doskey command.

A quick google: [http://en.wikipedia.org/wiki/Microsoft_Windows_SDK](http://en.wikipedia.org/wiki/Microsoft_Windows_SDK)

For this, you have the repositories and man pages.

Packages in the repositories with the forum "*-dev" are the development files, and the man pages for development can be installed. They can also be viewed on line [http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

---

### Post by eeboy on 2008-05-10
It's the documentation that provides me system function calls, code examples, etc. to do anything and everything. For example, if I want to figure out how to open a file in C I would reference the file I/O section of the document.

---

### Post by eeboy on 2008-05-10
Ok, assume I don't have an internet connection. Take the example of me trying to find out more about file I/O. I understand that there is a man page for this but how do I know where it is and what it's called? Thanks!

---

### Post by LaRoza on 2008-05-10
> **eeboy said:**
> Ok, assume I don't have an internet connection. Take the example of me trying to find out more about file I/O. I understand that there is a man page for this but how do I know where it is and what it's called? Thanks!
I don't know if these are on the CD, but if it is, this command will prompt you to put the CD in:
```

sudo apt-get install manpages-dev

```
An example of use:
```

$ man 3 <function-name>

```

It is in the main repository, which I think is on the CD.

---

### Post by eeboy on 2008-05-10
Thanks! That works great for more information on functions I already know the name of (I did a quick 'man 3 printf' to show that it works). However, if I don't know the function name is there anyway to search on a descriptive term? Say for example I want to find out how to output data to the serial port I could search for RS232 or serial port or something similar.

---

### Post by samjh on 2008-05-10
Unfortunately Linux doesn't really have a definitive "platform SDK" like Windows does.

If you're looking at the bare bones, then the glibc documentation is probably best.  You can download a local copy.  Glibc is the GNU Project's C library including ISO C, with substantial portions of the POSIX standard, and BSD functions.  It's pretty much standard fare for programming on Linux platforms using C.

See the manuals here: [http://www.gnu.org/software/libc/manual/](http://www.gnu.org/software/libc/manual/)

---

### Post by DavidBell on 2008-05-11
Where do you find good docs for kernel functions? For eg there is lot's of google hits for the function

**input_report_abs**(input_dev *dev, unsigned int code, int value)

(lives in Linux-#.#.#/include/linux/input.h)

but they are all bits of kernel source code

The man pages web site you pointed to doesn't have anything. I did once find a page on it but it was along the lines of ...

Function : input_report_abs (input_dev *dev, unsigned int code, int value)

Purpose: reports input as abs

Parameters:

    input_dev *dev: the dev you are inputing
    unsigned int code: the code for the input
    int value: the value to input

I guess it would be useful if the code was already working :-(

DB

---

### Post by slavik on 2008-05-11
man is a very powerful utility. it has an option -k which would allow you to search by keywords, there is also apropos.

man and apropos are your best friends. I also recommend looking into stdlib.h and unistd.h for some basic system level stuff (of course there is more).

the definitive guide for the Linux kernel is it's source, the most fun think is to rgrep fuc on the source code ;)

---

### Post by KIAaze on 2008-05-11
I am also often offline and having offline doc is extremely useful.
Here are some of the solutions I found:

1)Install *-doc packages of libraries you plan to use.
They usually add useful documentation to /usr/share/doc.
It's mostly in html format, so you can browse it with Firefox for example.

2)Some interesting packages:
-devhelp -> The closest thing I found so far to a "Platform SDK"
-doc-central
-dwww
-dhelp
-httrack+webhttrack ->Allows downloading whole websites for viewing offline. Very useful for tutorial pages and so on.
-qt4-dev-tools ->For QT4 development
-qt3-assistant ->For QT3 development

3)KDevelop has an inbuilt documentation browser.

Just remember that every library used in a GNU/Linux system is usually an independant project. So they each have their own documentation, the quality of which can vary.
This is different from Microsoft where everything is centralized.

By the way, if you want to document your own code, I highly recommend [doxygen]("http://www.stack.nl/~dimitri/doxygen/") (GUI version: doxywizard).
It generates documentation from special comments in the source code and offers all kinds of output formats, from html to manpages. :)

---

### Post by fifth on 2008-05-11
As already mentioned, most libraries on Linux are separate projects, and the documentation your looking for will depend on the libraries your using.

I mostly code with the QT toolkit, which, (iirc) has [documentation]("http://doc.trolltech.com/4.3/index.html") which is similar to the MS SDK. The [docs]("http://doc.trolltech.com/4.3/classes.html") for most classes contain code examples, such as for the [QPushButton]("http://doc.trolltech.com/4.3/qpushbutton.html")

---

