---
title: "Programming, python, new to ubuntu"
date: 2010-05-04
forum: Programming Talk
---

### Post by makuab on 2010-05-04
I went to the website and got [Python  3.1.2 compressed source tarball]("http://www.python.org/ftp/python/3.1.2/Python-3.1.2.tgz")
[http://www.python.org/download/](http://www.python.org/download/)

i think i installed it

what do i do now? how do i begin coding?
this **** is so frustrating.

i think i have ubuntu 10.04

---

### Post by Seal Daemon on 2010-05-04
[How to start programming - guides and links for many languages]("http://ubuntuforums.org/showthread.php?t=333867") ( including Python ).

---

### Post by puzzler995 on 2010-05-04
Your best bet would be to get an IDE and dive in. If you become part of a project in sourceforge, you can get Wing IDE for free. Other than that you can open the terminal and type in ```
python
```. find a tutorial on Google

---

### Post by makuab on 2010-05-04
> **puzzler995 said:**
> Your best bet would be to get an IDE and dive in. If you become part of a project in sourceforge, you can get Wing IDE for free. Other than that you can open the terminal and type in ```
python
```. find a tutorial on Google
whats an IDE?

---

### Post by da burger on 2010-05-04
It stands for integrated development environment. Basically it's a program that includes a text editor and everything else you might want to help you program (a terminal, somewhere to put notes, a way to open multiple files at once and a fast way to run your program).

---

### Post by The Cog on 2010-05-04
For programming in python, I really like Geany. It's not a full IDE, but it's a text editor with syntax highlighting and function / variable recognition. I don't know how will the syntax highlighting would work with python 3 though - I only use 2.x.

---

### Post by dustinmarlowe56 on 2010-05-04
hey man, i am a university student who just completed a semester of learning python. My university (The University of Alabama) has a great website set up that you should be able to use to learn python. it has all of the tasks and things that we had to complete to pass intro to computer programming. there are tutorials and helpful links too. give it a look sometime
 
 
beastie.cs.ua.edu/cs150

---

### Post by Nebelhom on 2010-05-04
I used this free web book

[http://www.greenteapress.com/thinkpython/thinkpython.pdf](http://www.greenteapress.com/thinkpython/thinkpython.pdf)

---

### Post by Portmanteaufu on 2010-05-04
> **makuab said:**
> I went to the website and got [Python  3.1.2 compressed source tarball]("http://www.python.org/ftp/python/3.1.2/Python-3.1.2.tgz")
[http://www.python.org/download/](http://www.python.org/download/)

i think i installed it


If you want to install it using the repositories (the official Ubuntu way), use:

```
sudo apt-get install python3
```

That will do all the work for you and give you a definitive error message in the unlikely event that something should go awry.

---

### Post by CptPicard on 2010-05-04
Python is already installed, there is no need to do anything, and specifically, the "go to a website and download..." approach is essentially always wrong on Ubuntu -- use the package manager.

After that it's just usage of both the python interpreter and the text editor of choice. Whether a beginner actually needs an IDE with Python is very debatable, IMO.

---

### Post by lisati on 2010-05-04
> **CptPicard said:**
> Python is already installed, there is no need to do anything, and specifically, the "go to a website and download..." approach is essentially always wrong on Ubuntu -- use the package manager.

After that it's just usage of both the python interpreter and the text editor of choice. Whether a beginner actually needs an IDE with Python is very debatable, IMO.

+1. The Software Center and Synaptic Package Manager are good places to look at first for installing stuff that might be useful.

---

### Post by Portmanteaufu on 2010-05-04
> **CptPicard said:**
> Python is already installed, there is no need to do anything....


This is half-true. Ubuntu does come with Python 2.6 pre-installed, but it does not come with Python 3 (which is not compatible with 2.6). The original poster specifically mentioned trying to get Python 3 to go.

---

### Post by CptPicard on 2010-05-04
> **Portmanteaufu said:**
> The original poster specifically mentioned trying to get Python 3 to go.

The OP probably doesn't know of or care about the difference; he just out of habit went over to the website and grabbed what looked like the newest version.

The 2.6 that comes with Ubuntu will serve him just fine.

---

### Post by Portmanteaufu on 2010-05-04
> **CptPicard said:**
> The OP probably doesn't know of or care about the difference; he just out of habit went over to the website and grabbed what looked like the newest version.

The 2.6 that comes with Ubuntu will serve him just fine.

Yeah, more than likely. Agreed.

---

### Post by lavinog on 2010-05-04
> **CptPicard said:**
> The OP probably doesn't know of or care about the difference; he just out of habit went over to the website and grabbed what looked like the newest version.

The 2.6 that comes with Ubuntu will serve him just fine.

I think many code examples on the web use 2.X syntax...another reason to learn with 2.6

If the OP really needs to create 3.X code they can use 2.6 then use the 2to3 utility to convert it (I have read this is the preferred way to deal with the version differences)
Also to the OP: You might find that not all modules have 3.X versions still.

---

### Post by puzzler995 on 2010-05-04
> **CptPicard said:**
> Whether a beginner actually needs an IDE with Python is very debatable, IMO.
They have IDEs out just for learning python, for example [Wing IDE 101]("http://www.wingware.com/wingide-101/index")

[QUOTE=lavinog]You might find that not all modules have 3.X versions still. 	[/QUOTE]
Just like HTML5. Great to know, just not fully supported yet.__[]("http://www.wingware.com/wingide-101/index")

---

