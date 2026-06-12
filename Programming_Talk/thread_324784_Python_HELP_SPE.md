---
title: "Python HELP SPE"
date: 2006-12-24
forum: Programming Talk
---

### Post by nick.inspiron6400 on 2006-12-24
Hello,

I am really really new to programming, and linux so bear with me!

I installed SPE (stanis python editor) and have tried to make a "Hello World" application, i do

print "Hello World" then i go to run the application, and it asks for a "argument" what does it mean?

Thanks,

Nick,

P.S

The only program i have ever done is a "Hello World" application in Visual Basic 2005!

---

### Post by SoloSalsa on 2006-12-24
I know nothing about Python, but I know what an argument is.  It's like cases, terms, details.  Like, to find the square root of something (in Java) looks like
Math.sqrt (**42**);
42 is an **argument**.  It sounds silly, but that's what it is.  It could be one variable, it could be five strings, anything.  Like, raising a number to the second power
int x = 2;
Math.pow (**x, 2**);
Where x is a number, 2 is the power, both **arguments** for the power method.  This is a print command in Java
System.out.print (**"Hello World"**);
Where "Hello World" is the argument.  So, I do not know Python syntax, but presume that the argument "Hello World" is set up wrong...   I hope this helps somehow.

---

### Post by Wybiral on 2006-12-24
Arguments aren't important in a simple hello world program. They mean command line arguments... They are the stuff you put after a program's name in the command line that get submitted to a program. For instance, a program could be called "add" and would take in two command line arguments, add them and display the results. It would be called from the command line with "./add 10 5" and would display "15" afterwards...

But, for hello world they dont matter. I don't know how SPE operates, but you could just save it as "program.py" and execute it with "python program.py" from the command line. BTW, program.py was just and example, anything .py would work.

---

### Post by DirtDawg on 2006-12-24
For now, just ignore the request for an argument. 

I would also highly recommend you use IDLE. It is in Synaptic and is ideal for someone just starting, with far fewer potentially confusing options than SPE. SPE is extremely well designed, but has excessive features for a beginner.

There is a great Idle tutorial [here]("http://hkn.eecs.berkeley.edu/~dyoo/python/idle_intro/") if you need it. It's based on Windows Python, but that should make no difference (That's what cross-platform is all about). 

Have fun!

P.S. You can get Idle by entering this command into the terminal:
```
 sudo apt-get install idle 
```

---

### Post by DirtDawg on 2006-12-24
> **SoloSalsa said:**
> 
System.out.print (**"Hello World"**);
Where "Hello World" is the argument.  So, I do not know Python syntax, but presume that the argument "Hello World" is set up wrong...   I hope this helps somehow.

Nope, the correct syntax for a hello world program in Python is:
```
print "hello world" 
```
As they say, Python is psuedo-code that runs!

---

### Post by nick.inspiron6400 on 2006-12-25
Thanks for all your help! Merry Christmas everyone!

I will give IDLE a go, SPE is a bit hard :(  I also want to ask I installed Ruby but i cant seem to find it! Where is it? And how do i run it?

Thanks, i am a real newbie right now so i dont know these things!

---

### Post by DirtDawg on 2006-12-25
> **nick.inspiron6400 said:**
> Thanks for all your help! Merry Christmas everyone!

I will give IDLE a go, SPE is a bit hard :(  I also want to ask I installed Ruby but i cant seem to find it! Where is it? And how do i run it?

Thanks, i am a real newbie right now so i dont know these things!

I'm not sure about starting Ruby as I have not used it. If you Google for Ruby tutorials, however, you are likely to find plenty of good ones. Give Ruby a go, give Python a go, then choose one language and *stick to it*. Once you learn one language, others will come easier. Merry Christmas!

---

### Post by nick.inspiron6400 on 2006-12-25
Thanks, but i think i will stick to Python. Ruby is a difficult program to launch, considering it is not even in  Applications!!!!

Merry Christmas & Happy New Year!

Nick,

---

### Post by DirtDawg on 2006-12-26
> **nick.inspiron6400 said:**
> Thanks, but i think i will stick to Python. Ruby is a difficult program to launch, considering it is not even in  Applications!!!!

Merry Christmas & Happy New Year!

Nick,

Good choice, IMO. :cool:

---

### Post by Wybiral on 2006-12-26
BTW, you can run python and ruby programs from the command line, you don't need an IDE.

---

### Post by stani on 2007-02-24
A lot of newbies use SPE. Actually even some schools and universities use it to teach programming. I don't think Idle is more easy. For example what is very handy for a newbie is that SPE underlines syntax errors in red as you type (just like spelling checkers do). One of the advantages of SPE for Ubuntu is that I am an Ubuntu user myself. 

As a start look to this video tutorials:
[http://www.showmedo.com/videoListPage?listKey=PythonDevelopmentWithSPE](http://www.showmedo.com/videoListPage?listKey=PythonDevelopmentWithSPE)

Here is another tutorial:
[http://www.serpia.org/spe](http://www.serpia.org/spe)

If you donate a little, you get a nice pdf manual of SPE.

I just created a new blog, which I started with some publicity for Ubuntu:
[http://pythonide.stani.be](http://pythonide.stani.be)

Stani

---

