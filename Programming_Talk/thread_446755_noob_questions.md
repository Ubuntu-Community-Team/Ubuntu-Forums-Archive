---
title: "noob questions"
date: 2007-05-17
forum: Programming Talk
---

### Post by silent1643 on 2007-05-17
what program should a beginner start out with?

my goal is to maybe develop small linux programs that are not to complicated at first.
i know mostly html, and a little php & actionscript so i haven't really looked into anything else until i installed ubuntu.

 Is there a program with a built in guide of sorts? Examples, Tutorials, and maybe some kind of formula menu or list of common statements that i could use? Sorta like when using "script assist", or using the clickable code to create simple and sometimes complicated statments in flash action scripting...

---

### Post by clash on 2007-05-17
My advice, find a good C++ tutorial online. They shouldn't be hard to find. 

Start coding small programs with a text editor like gedit and learn about GCC, make and makefiles eventually. 

Don't start with an IDE

Or perhaps if u must start with a simplistic IDE like BlueJ and start on Java. 

Stay away from languages like basic like they are the plaque.

---

### Post by LaRoza on 2007-05-17
This is one of the best online tutorials I've seen (it's for C++)

[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by silent1643 on 2007-05-17
great, thanks! =D>

that c++ tut looks like something i could start with.. how can i see my results or test my code?

---

### Post by samjh on 2007-05-17
First, open up terminal and type:
```
sudo apt-get install build-essentials
```
That will install the basic packages that will allow you to compile C and C++ source code, and create Debian packages.

Next, use editors (Ubuntu comes with gedit, which should be enough) to type the source code.  For C++, I recommend using .cpp or .cc as the file extension.  Save the code, for example: helloworld.cpp

Then open up terminal, and change the directory to the same place your source code file is placed.

Then to compile helloworld.cpp:
```
g++ -o helloworld helloworld.cpp
```
g++ is the compiler for C++.
-o helloworld means to output the compiled binary to a file called helloworld.
helloworld.cpp is the source code file.

Then to run helloworld:
```
./helloworld
```

Have fun! :)

---

### Post by silent1643 on 2007-05-17
awesome thanks

---

### Post by WW on 2007-05-17
*WW whispers:* **build-essential** (no "s" at the end)

---

### Post by silent1643 on 2007-05-17
> **WW said:**
> *WW whispers:* **build-essential** (no "s" at the end)

word :guitar:

---

### Post by pmasiar on 2007-05-17
> **silent1643 said:**
> what program should a beginner start out with?


Beginner? Self-learner without a teacher and tutor on your side? Definite *do not* start with C++, it is direct way to frustration. Start with something much simpler, like Python, which does not force objects on you from day one, has simple syntax, typing, and is much more intuitive. When ready, go for "hard" languages like C++, Java, C# or whatever.

Check other posts of people whose advice you want to follow, to get an idea what is their background and assumptions. What is good for experienced programmer, mich not be good for beginner.

Or go for C++, but don't say I did not warned you. :twisted:

---

### Post by darkworld on 2007-05-17
> **pmasiar said:**
> Beginner? Self-learner without a teacher and tutor on your side? Definite *do not* start with C++, it is direct way to frustration. Start with something much simpler, like Python, which does not force objects on you from day one, has simple syntax, typing, and is much more intuitive. When ready, go for "hard" languages like C++, Java, C# or whatever.

Check other posts of people whose advice you want to follow, to get an idea what is their background and assumptions. What is good for experienced programmer, mich not be good for beginner.

Or go for C++, but don't say I did not warned you. :twisted:

Hey I just read virtually the exact piece of advice in a magazine - Python good to start with.

---

### Post by Judo on 2007-05-17
I would also recommend Python for a beginner.   It's one of the easiest to learn and it seems to be the only language I use nowadays.  However, it definitely has limits.  You should keep C++ in mind for later.

---

### Post by silent1643 on 2007-05-17
> **darkworld said:**
> Hey I just read virtually the exact piece of advice in a magazine - Python good to start with.

hmm... well hat are the basic steps to using python? i have visited python.org and it says that most linux distros have python installed, does ubuntu? (i assume so since the command python takes me into some kind of termnial)are the compilers already installed? what are the steps from code to program?

---

### Post by kknd on 2007-05-17
> **silent1643 said:**
> hmm... well hat are the basic steps to using python? i have visited python.org and it says that most linux distros have python installed, does ubuntu? (i assume so since the command python takes me into some kind of termnial)are the compilers already installed? what are the steps from code to program?

Python is automaticaly bitecode compiled, and run in a "vritual machine", like Java.

All python code are run with the "pythonc ommand".

Ex.: python myscript.py

---

### Post by Judo on 2007-05-17
Python is installed, but IDLE, it's default editor is not.  I mention IDLE because that's what I use, but there are other editors (or IDE, if you prefer) available.

Python is interpreted, at least, I would say so.  If I understand this correctly, it's compiled into machine code when you execute it or as needed.  In some cases, I don't get error messages until I try to run a certain part of a program, which makes me think that not all parts are read as you execute the program.

To run a Python program (with a .py extension or others) you type something like "python program.py" and it will be exectued.  If you have the program open in IDLE, you can press F5 and it will be executed.

I don't have any tutorials to recommend.  Sorry.  I learnt it by reading examples.  It's not the fastest way, but it pays off in the end.

---

### Post by silent1643 on 2007-05-18
> **Judo said:**
> Python is installed, but IDLE, it's default editor is not.  I mention IDLE because that's what I use, but there are other editors (or IDE, if you prefer) available.

Python is interpreted, at least, I would say so.  If I understand this correctly, it's compiled into machine code when you execute it or as needed.  In some cases, I don't get error messages until I try to run a certain part of a program, which makes me think that not all parts are read as you execute the program.

To run a Python program (with a .py extension or others) you type something like "python program.py" and it will be exectued.  If you have the program open in IDLE, you can press F5 and it will be executed.

I don't have any tutorials to recommend.  Sorry.  I learnt it by reading examples.  It's not the fastest way, but it pays off in the end.

hmm.. i thought java was complied the same way c++ was, text to compiler? 

I guess there are no editors that will highlight errors in the code before it is compiled?

---

### Post by silent1643 on 2007-05-18
nevermind i found a great tut on python [here]("http://swaroopch.info/text/Byte_of_Python:Basics")

---

### Post by DarthWHO on 2007-05-18
Another good Pythod site for beginners: [http://diveintopython.org/]("http://diveintopython.org/")

Just started with this (seems to me I saw this recommended somewhere else on the board). Going good so far...

---

### Post by FuriousLettuce on 2007-05-18
As an aside, diveintopython is included in the default ubuntu installation - point firefox to file:///usr/share/doc/diveintopython/html/index.html , and the examples can be found in the terminal by doing
```
cd /usr/share/doc/diveintopython/examples
```

---

