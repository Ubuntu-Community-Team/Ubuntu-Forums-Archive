---
title: "Good Decision?"
date: 2008-02-06
forum: Programming Talk
---

### Post by slats on 2008-02-06
i have just completed programming with VisualBasic.net and currently learning java. Since I'm just a beginner with programming was it a good decision to switch to Ubuntu or did i make a bad choice?

---

### Post by DamagePlan on 2008-02-06
You wont be able to use visual basic in ubuntu but you can use Java. If you now use ubuntu then I recomend learning python. Python is just as easy as vb.

---

### Post by slats on 2008-02-06
yeah i dont really care to use vb cuz i dont really like it
i just like raw code
no having to add the visual stuff

im learning java through school because im going to a tournament later this year
what is python good for in ubuntu?

---

### Post by lnostdal on 2008-02-06
No, go for it.

```

lars@ibmr52:~/programming/java$ sudo aptitude install sun-java6-jdk
lars@ibmr52:~/programming/java$ sudo update-java-alternatives -s java-6-sun
.....

lars@ibmr52:~/programming/java$ cat Hello.java

public class Hello {
  public static void main(String args[])
  {
    System.out.println("Hello World!");
  }
}


lars@ibmr52:~/programming/java$ javac Hello.java
lars@ibmr52:~/programming/java$ java Hello
Hello World!
lars@ibmr52:~/programming/java$ 

```

Java is easy to install and use under Ubuntu.

---

### Post by slats on 2008-02-06
is python used more often in ubuntu or is java?

---

### Post by SOULRiDER on 2008-02-06
> **slats said:**
> is python used more often in ubuntu or is java?

It is. If you are going to learn Java at school I say go learn Java. Check out a book called "First Head Java", I wish i had had it when I started to learn Java

---

### Post by Zugzwang on 2008-02-06
> **slats said:**
> is python used more often in ubuntu or is java?

You shouldn't care. If you need to learn Java anyway, sticking with Java is totally fine. It's just that a lot of the Ubuntu extensions are coded in Python. Whether Python or Java is easier to learn/use is often a matter of taste anyway.

---

### Post by slats on 2008-02-06
i have "A Guide to Programming in Java" which was provided by my school
but in the competition i am studying for, i can use python, and im not that far into java

so should i just learn python?
because i would like to use the more practical language.

---

### Post by Tuna-Fish on 2008-02-06
> **slats said:**
> is python used more often in ubuntu or is java?

Python, by far.

Python is currently the posterboy for scripting in foss world. Java is used mainly in enterprise coding.

Their design reflect this; python is a language where it is really fast (and fun!) to build quick systems, just for testing, and if they turn out good, it won't crash and burn when you expand those. Java is designed for really strict design practises, where you really should do a lot of class design before you even touch the keyboard. The common joke is that java is built by smart people for stupid people (a lot of language features that take power out of the hands of the coder to protect him from himself, or from other coders in the same department), whereas python is built by smart people for smart people (lots of power in the language).

(also, by that count, c++ is built by batshit insane people for morons...)


And ps, before you start a language war, I write mostly java these days. Yes, I guess that makes me stupid... :)

---

### Post by slats on 2008-02-06
ok i guess i'll try out Python
does anyone know any good tutorials or books on the subject?

---

### Post by Tuna-Fish on 2008-02-06
Seriously, if you want to be a good programmer, you will eventually learn both. And when you do, you wonder why you made such a fuzz about choosing the language. Learning the language doesn't matter half as much as learning to program. The big concepts such as recursion, oop and such are pretty much the same everywhere.

I'd learn python for now, just because you can be lazy and type less to get the same program in it. Also, the libraries are better organized and easier to learn.

---

### Post by pmasiar on 2008-02-06
> **slats said:**
> i have just completed programming with VisualBasic.net and currently learning java. Since I'm just a beginner with programming was it a good decision to switch to Ubuntu or did i make a bad choice?

Java is OK - and good to know get job. 
Python is rather popular as important Ubuntu development language (Canonical prefers it), and agile language for web app development.

If you are learning Java at school, keep at it, there is no reason to jump from one language to another, you will learn many more during your career, so don't be afraid to learn one more.

But I would advise you to take a look at Python when you have a week or so free - it is very easy to learn, and for someone like you, being steeped in statically typed, class-obsessed language like Java, Python has big surprise: dynamic typing and late binding. You will be surprised how much freedom it gives you, and how it simplifies programming (some people say it just shifts errors to runtime, but we don't do errors, so it does not matter :-) )

I know shops who use C++ for raw performance (when milliseconds matter, like automated stock trading), using agile languages like Python for tasks where flexibility and ease of maintenance and change is more important than runtime: managing deployment (Google and it's close to million servers), flexible data massaging, creating test data etc.

And yes, hacking on Python is more fun, you can make 5 times as much in same amount of time and code compared to Java. Python will be far better for a competition, if you can use it. Allowing Python would be almost unfair advantage :-)

See wiki in my sig for links and training task

---

### Post by Tuna-Fish on 2008-02-06
> **slats said:**
> ok i guess i'll try out Python
does anyone know any good tutorials or books on the subject?

Pmasiars' sig. Look above ^^·

---

### Post by lnostdal on 2008-02-06
> **slats said:**
> is python used more often in ubuntu or is java?

for *distro related programming* (#1) python is the "officially preferred language" for ubuntu .. this means that much of the stuff that glues the different software pieces and projects together into the distro known as "ubuntu" is written and maintained in python .. so if you want to work on the "glue" python is more used than java

however this doesn't have any consequences for anyone wishing to use other languages and tools under ubuntu for their projects or applications .. the projects and applications are the pieces (written in any language) .. while the ubuntu project prefer to use python to make these pieces "part of" the ubuntu distro

ubuntu is linux .. and linux is linux .. and linux has excellent support for many languages and tools including java and python

linux or ubuntu doesn't force any particular language or tool upon you or your projects, and doesn't try to cripple tools or languages "it doesn't like"

in short: use whatever language you prefer .. you will find a big, enthusiastic and caring community behind most of them


#1: distro related programming is not something an application or web programmer has much interest in .. there is a clear separation here

---

### Post by hod139 on 2008-02-06
> **lnostdal said:**
> 
```

lars@ibmr52:~/programming/java$ sudo aptitude install sun-java6-jdk

``` <snip>


This will only install sun's java, not make it the default on the system.  To do that you need to do 
```

sudo update-java-alternatives -s java-6-sun

```

---

### Post by lnostdal on 2008-02-06
ty hod139,  i've now added this to my previous post

---

### Post by slats on 2008-02-06
> **pmasiar said:**
> Java is OK - and good to know get job. 
Python is rather popular as important Ubuntu development language (Canonical prefers it), and agile language for web app development.

If you are learning Java at school, keep at it, there is no reason to jump from one language to another, you will learn many more during your career, so don't be afraid to learn one more.

But I would advise you to take a look at Python when you have a week or so free - it is very easy to learn, and for someone like you, being steeped in statically typed, class-obsessed language like Java, Python has big surprise: dynamic typing and late binding. You will be surprised how much freedom it gives you, and how it simplifies programming (some people say it just shifts errors to runtime, but we don't do errors, so it does not matter :-) )

I know shops who use C++ for raw performance (when milliseconds matter, like automated stock trading), using agile languages like Python for tasks where flexibility and ease of maintenance and change is more important than runtime: managing deployment (Google and it's close to million servers), flexible data massaging, creating test data etc.

And yes, hacking on Python is more fun, you can make 5 times as much in same amount of time and code compared to Java. Python will be far better for a competition, if you can use it. Allowing Python would be almost unfair advantage :-)

See wiki in my sig for links and training task



well i borrowed a book from my school from the technology teacher
because i was at the top of my vB.net class, and it is only one semester long. And he said i could learn java, but i just started it, and i dont know too much about it so i think ill put java on hold and just learn python, because from what everyone is saying it seems more universal then java

so I'm going to start python today
thanks

---

### Post by johnnyb1726 on 2008-02-06
> **SOULRiDER said:**
> It is. If you are going to learn Java at school I say go learn Java. Check out a book called "First Head Java", I wish i had had it when I started to learn Java

i think he means to check out "Head First Java".  I do not know of a book call "First Head Java".

---

### Post by SOULRiDER on 2008-02-06
> **slats said:**
> i have "A Guide to Programming in Java" which was provided by my school
but in the competition i am studying for, i can use python, and im not that far into java

so should i just learn python?
because i would like to use the more practical language.

Ive been in a couple of ACM ICPC competitions, Python isnt allowed ther, but I wouldnt use it anyways due to it being slower than other languages.

---

### Post by SOULRiDER on 2008-02-06
> **johnnyb1726 said:**
> i think he means to check out "Head First Java".  I do not know of a book call "First Head Java".

Doh, my bad, i did indeed mean Head First and not First Head.

---

### Post by pmasiar on 2008-02-06
> **SOULRiDER said:**
> Ive been in a couple of ACM ICPC competitions, Python isnt allowed ther, but I wouldnt use it anyways due to it being slower than other languages.

If competition is about how fast your code runs, C C++ or C# might be better choice.

But if competition is about solving some problem quickly, Python is far better choice, and you are fooling yourself ignoring it.

I might be even glad you ignore it - more power to me! :-) "Speed to the market" is most important speed for me - and my boss.

---

### Post by motang on 2008-02-06
> **slats said:**
> ok i guess i'll try out Python
does anyone know any good tutorials or books on the subject?

Matter of fact I am interested in learning Python also and I know of a free book it's called [Dive Into Python]("http://www.diveintopython.org/").  You might want to give that a try.  I heard that it comes with Ubuntu installations, I think you can find in the Help and Support.

---

### Post by LaRoza on 2008-02-06
> **motang said:**
> Matter of fact I am interested in learning Python also and I know of a free book it's called [Dive Into Python]("http://www.diveintopython.org/").  You might want to give that a try.  I heard that it comes with Ubuntu installations, I think you can find in the Help and Support.

Dive Into Python is not for people that do not already know a programming language. See my wiki for tutorials for beginners.

---

### Post by DrMega on 2008-02-06
> **slats said:**
> i have just completed programming with VisualBasic.net and currently learning java. Since I'm just a beginner with programming was it a good decision to switch to Ubuntu or did i make a bad choice?

I think you've gone down the right route. By doing VB.Net you've gained experience in the .Net framework. The same framework is used in C#.net, which you can develop in on Ubuntu via Mono if you so choose.

By switching to Java you are placing yourself on a good launching pad to other languages (if you want to switch again in the future, and in any case Java is popular and well supported). The syntax of Java is much more like other languages than VB is. Once you've done Java for a while, if you look at some C#, C++ or PHP code you'll see many similarities that aren't there with VB.

---

### Post by slats on 2008-02-06
hmmm i feel stupid cuz im reading a few tutorials on pyhton but where do i actually write the code?
cuz there is no python program in my applications tab
and i know its installed cuz i checked in the terminal
but how do i access it?
do i write in notepad like java or php?

---

### Post by Tuna-Fish on 2008-02-06
yes. to run the program, in terminal, type 

```
python yourprogramname.py
```

Or, if you want to make it behave like a real app, start the file with:

```

#! /usr/bin/env python
# encoding=UTF-8

```
Then, you can just give the file executable permissions, and double-click it.

There are methods of packaging a python script in an .exe with an interpreter for shipping stuff to windows people.

---

### Post by pmasiar on 2008-02-06
See "IDLE toying" tutorial on my wiki

---

### Post by Tuna-Fish on 2008-02-06
also, you can use any number of python ide's, there are plenty in the repositories.

And, to use python interactively, just open a terminal and type python

---

### Post by slats on 2008-02-07
yeah i started reading A Byte of Python
and i realized that i needed an editor
which i didnt have
so thanks all for your input

---

