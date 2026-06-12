---
title: "Python"
date: 2011-09-10
forum: Programming Talk
---

### Post by Merisi on 2011-09-10
I've never done any programming before but I'd really like to learn Python but I'm not sure where to start.  I believe you get Python in Ubuntu but I can't seem to access it and I'm also worried that if I tamper with it I could mess things up.  I was also told about this website, [http://diveintopython.org/](http://diveintopython.org/) but it seems a bit overwhelming.

---

### Post by ubudog on 2011-09-10
Hi, I've moved your thread to the Programming Talk section of the forums.


Correct: Python does come with Ubuntu.
I'd recommend doing a "Hello World" tutorial in Python.  My first "Hello World" was as simple as this:

(file: helloworld.py)
```
#!/usr/bin/python
print "Hello World!"
```

You can then run that like so:
```
python helloworld.py
```

And you should see "Hello World!"

You can also do something a bit more complex, with windows and stuff, using Tk.  

You will need to have the python-tk package installed, you can do that like so:
```
sudo apt-get install python-tk
```

Check this out:
[http://www.pythonware.com/library/tkinter/introduction/hello-tkinter.htm](http://www.pythonware.com/library/tkinter/introduction/hello-tkinter.htm)

It's old, but works.  Hope this information gets you going!

---

### Post by Neoncamouflage on 2011-09-10
I've just recently started into Python myself and I must say, after trying Java a while back, it's so easy. You can learn the basics and syntax in no time, and it's really not that hard to advance along.

I highly recommend you look up A Byte of Python. That's the first tutorial book I read, and it's awesome. Don't just read one though, there's dozens of them out there for general basics and specific ideas, and it helps to read them all. Also, whenever you learn something new, make up a random program that uses it. Or a couple different programs. Find new ways that whatever you learned can be used, or can be manipulated to suit other needs. That's how you learn the fastest.

And lastly, if you have an IRC client, join up to the freenode server. #python, #pygame, and #pythonlearners are all channels I stay in, and have all helped greatly.

---

### Post by Smart Viking on 2011-09-10
Hi. If you lanch a Terminal, and write "python", and then press enter, you'll get into the python interpreter, it will be able to launch python commands. It will look similar to this:
```
Python 2.6.6 (r266:84292, Dec 26 2010, 22:31:48) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

To write real programs though, you should save it in a text file because it is much more practical, and launch it from the terminal the way ubudog explained.

Programming is not easy, it will take time to learn, but take my word for it; if you're interrested and give it a try, you'll eventually learn and understand it.

I recommend this tutorial, because that was what I started with: [http://greenteapress.com/thinkpython/html/index.html](http://greenteapress.com/thinkpython/html/index.html)

---

### Post by Merisi on 2011-09-10
Thanks for everyones replies.  After a bit of a struggle and getting some things wrong I was able to activate Python and then complete the "Hello World" tutorial.  I find computers fascinating and really want to learn and programming seemed like the next step but could anyone tell me the sort of cool things you can accomplish once you've learned some programming?

---

### Post by Smart Viking on 2011-09-10
> **Merisi said:**
> Thanks for everyones replies.  After a bit of a struggle and getting some things wrong I was able to activate Python and then complete the "Hello World" tutorial.  I find computers fascinating and really want to learn and programming seemed like the next step but could anyone tell me the sort of cool things you can accomplish once you've learned some programming?

You can create a set of primitive operations, and make the computer perform them. If you combine those primitive instructions, you can make meaningful programs that makes sense of information and solves problems.

It's much cooler than it sounds.

You can make a program that asks the users for their name and age, then tells the users wether or not they are older than your mom.

You should also know from the very beginning that computers are extremely primitive compared to our brains, you must give the computer exact instructions, it will not "guess" for you, and it doesn't care or know wether what you told it to do was correct or not. Luckily, you can use libraries (or "modules", in Python jargon), which is software that people have written before you, so you don't have to write all those primitive instructions, instead you can write a set of less primitive instructions, more natural to us.

When you tell python to print "hello, world!", you are using software written before you, the "print" statement understand how the terminal works, those who wrote it told the computer exactly how to write dots on the screen then looks like a character that we can read (well not really, but that is a healthy way to think about it.)

When you learn more about computers, you'll start to be able to "think" from a computer perspective, and you will more understand the limits and possibilities that apply to computers, and you will get an always increasingly better idea of what is easy, and what is hard to implement as a computer program. 
You will never completely understand how everything in the computer world works. That you made a computer program doesn't mean you will understand every computer problem, but you will be able to "guess" more accurately. Fortunately, you don't need to, you just need to know enough to get you going. When you start writing a program, you wont necesarily know all the practical details of how you are going to do this and that, but when you learn more you will know that it's possible, and you'll learn it as you write. 

What is not important is to know practical details about everything, what is important is to have a general idea that guide you in the right direction, so that you can learn those practical solutions increasingly faster.

I hope this helps you somewhat, I'm not really that good explaining stuff to people, but take my word for it; if you are interrested, and you actually try to understand (which is a bi-effect of being interrested really), you **will** learn, and understand computers, and you will eventually be able to write complex programs like a GUI program with buttons and such, or a command line backup utility. :)

---

### Post by ofnuts on 2011-09-10
> **Merisi said:**
> Thanks for everyones replies.  After a bit of a struggle and getting some things wrong I was able to activate Python and then complete the "Hello World" tutorial.  I find computers fascinating and really want to learn and programming seemed like the next step but could anyone tell me the sort of cool things you can accomplish once you've learned some programming?basically, have the computer do things for you :) A die-hard programmer may spend 5 days finding a way to have the computer do for him/her a task that would have taken one hour done by hand. This may lead to the ["miserable programmer's paradox"]("http://blog.garlicsim.org/post/2840398276/the-miserable-programmer-paradox")...

Now, what the computer does for you depends on what you use computers for...

---

### Post by DangerOnTheRanger on 2011-09-10
> **Merisi said:**
> Thanks for everyones replies.  After a bit of a struggle and getting some things wrong I was able to activate Python and then complete the "Hello World" tutorial.  I find computers fascinating and really want to learn and programming seemed like the next step but could anyone tell me the sort of cool things you can accomplish once you've learned some programming?

Well, [this is what I did]("http://sourceforge.net/project/screenshots.php?group_id=286783"), and am still doing, after around a year or two of Python (albeit with several years of experience programming with other languages). But there's no real example of what you can do after you've learned a language, because what is often given in textbooks have been done and re-done to death; and that brings me to what I like most about programming: The possibilities are limited only by your own imagination (and, of course, your hardware :P). Just come up with some idea that sounds cool to you, and then program it. Who knows, other people might find it interesting, and help you program it :)

---

### Post by Merisi on 2011-09-10
Smart Viking I really appreciate your explanation and the time you have taken to help me.


Ofnuts, it's ironic that programming in many ways can make a task longer.  It never occurred to me.



I have a general problem with Hello World when I use

python helloworld.py  
it doesn't work.  I'm doing this in terminal.

---

### Post by Smart Viking on 2011-09-10
> **Merisi said:**
> Smart Viking I really appreciate your explanation and the time you have taken to help me.


Ofnuts, it's ironic that programming in many ways can make a task longer.  It never occurred to me.



I have a general problem with Hello World when I use

python helloworld.py  
it doesn't work.  I'm doing this in terminal.

First off just so you know, both the Terminal and Python are case sensitive, basically a and A are two completely different characters.

Do you understand the Terminal (the bash shelll)? You should learn the basics, it will help you a bunch, especially as a programmer writing for GNU/Linux. Think of the Terminal as a file browser, it can only be in one directory(folder) at one time. When you launch the Terminal, it is usually located in /home/username. The command "python helloworld.py" will only launch the program if the program is located in the directory you are in, the working directory. If you launch the "pwd" command, it will print out to you where in the file hirarchy you are located. Since I'm no good explaining, take the time to read this guide that will teach you the basics, it's really worth it: [http://linuxcommand.org/](http://linuxcommand.org/)

P.S: When something doesn't work, you should include the error message you get (if any). That way it will be easier for us to understand the problem you're having. I assume the error you just got was something like this:
```
$ python helloworld.py 
python: can't open file 'helloworld.py': [Errno 2] No such file or directory
```

---

### Post by donkyhotay on 2011-09-10
I learned a lot by reading the source code of others and experimenting around with it. That is one of the big advantages of using linux is that almost everything is open source.

---

### Post by Merisi on 2011-09-10
It comes up with this message:

```
>>> python helloworld.py
  File "<stdin>", line 1
    python helloworld.py
                    ^
SyntaxError: invalid syntax
>>> 

```

---

### Post by DangerOnTheRanger on 2011-09-10
> **Merisi said:**
> It comes up with this message:

```
>>> python helloworld.py
  File "<stdin>", line 1
    python helloworld.py
                    ^
SyntaxError: invalid syntax
>>> 

```

You're not supposed to run that inside Python's interactive session - instead, either type the contents of the snippet ubudog gave you directly into Python's interactive session, or create a file containing the code snippet ubudog posted into a file called "helloworld.py" inside your home directory, and then type "python helloworld.py" from a terminal.

---

### Post by fractalman on 2011-09-10
Ive quite recently started playing about with python,  i've no prior programming experience or knowledge but after just a few short pages of a tutorial i managed to expand on the examples given and add a few of my own bits to the code successfully. 

[http://wiki.python.org/moin/BeginnersGuide/NonProgrammers](http://wiki.python.org/moin/BeginnersGuide/NonProgrammers)

there's a tutorial here about  making games for the beginner but building up to a full on game with gui and shiny bits!

[http://inventwithpython.com/](http://inventwithpython.com/)

just read online and save the file:)

if you are running IDLE, open a new window, type the code in, ctrl+s to save then f5 to run, it should appear in the main window.  Idle is in the repos if you need it.

---

### Post by Merisi on 2011-09-11
I've received a lot of information and I'm very grateful but now what has happened is that I'm completely overwhelmed and almost feel unsure where to start.  I'm using terminal, I've got IDLE 2.7 AND 3.1. Maybe if I take the time to read through everything I'll work it out in the end.

---

### Post by fractalman on 2011-09-11
Yeah, that was kinda how i felt,  I started with this tutorial,

[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_2.6]("http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_2.6")

or for python 3.

[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_3.0](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_3.0)

---

### Post by Neoncamouflage on 2011-09-11
> **Merisi said:**
> I've received a lot of information and I'm very grateful but now what has happened is that I'm completely overwhelmed and almost feel unsure where to start.  I'm using terminal, I've got IDLE 2.7 AND 3.1. Maybe if I take the time to read through everything I'll work it out in the end.

I think everyone starts at that point. What you need to do is fine one general beginners python tutorial and read through it. Learn the basics of how variables work, if statements and while loops. Simple things. After you go through the general tutorial, find another one and read through it, covering almost the same exact things, just to get it into your head better.

It still comes up that I feel overwhelmed when I try and get into some new part of Python, have to just stop trying to learn everything and focus on the small, basic bits, and slowly move forward.

---

### Post by Merisi on 2011-09-11
> **Neoncamouflage said:**
> I think everyone starts at that point. What you need to do is fine one general beginners python tutorial and read through it. Learn the basics of how variables work, if statements and while loops. Simple things. After you go through the general tutorial, find another one and read through it, covering almost the same exact things, just to get it into your head better.

It still comes up that I feel overwhelmed when I try and get into some new part of Python, have to just stop trying to learn everything and focus on the small, basic bits, and slowly move forward.
  
That sounds like good approach. Thanks for some good advice once again.

---

### Post by nvteighen on 2011-09-12
> **Neoncamouflage said:**
> I think everyone starts at that point. What you need to do is fine one general beginners python tutorial and read through it. Learn the basics of how variables work, if statements and while loops. Simple things. After you go through the general tutorial, find another one and read through it, covering almost the same exact things, just to get it into your head better.

It still comes up that I feel overwhelmed when I try and get into some new part of Python, have to just stop trying to learn everything and focus on the small, basic bits, and slowly move forward.

It's a good approach, but never stop practicing! Doing things will make you understand it faster and better ;)

---

### Post by drmrgd on 2011-09-12
I'm also currently teaching myself Python for fun.  I do have a little background from many years ago of C programming.  But, I think the resources I've been using the most would benefit you still.  Check out these two sites for tutorials:

[http://learnpythonthehardway.org/book/]("http://learnpythonthehardway.org/book/")
[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python]("http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python")

The other thing to do constantly is practice what you've learned by writing simple programs and trying simple exercises. I had a difficult time finding beginner exercises with solutions that I liked.  Here are two sites that I've been using lately though for fun:

[http://www.cs.washington.edu/homes/stepp/bridge/2007/exercises.html]("http://www.cs.washington.edu/homes/stepp/bridge/2007/exercises.html")
[http://cse.ucdavis.edu/~chaos/courses/nlp/Homework/Homework.html]("http://cse.ucdavis.edu/~chaos/courses/nlp/Homework/Homework.html")

The UC Davis site isn't loading at the moment, so I hope it's not down!

What I do is try to come up with a solution to the problems on my own.  When I get stuck, I Google the part I'm stuck with to see what I could find to help me out.  Then once I get a working program, I try to keep tweaking it to do more things.  For example, you could add more interactive interfaces to prompt the user for input.  Or, you could add error handling for user input programs to make sure they only input what you want them to input. 

Take your time and have fun exploring with Python!

---

