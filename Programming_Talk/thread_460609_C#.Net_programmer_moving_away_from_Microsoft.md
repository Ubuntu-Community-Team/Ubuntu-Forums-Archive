---
title: "C#/.Net programmer moving away from Microsoft"
date: 2007-05-31
forum: Programming Talk
---

### Post by cprofitt on 2007-05-31
I am curious if anyone has any suggestions on migrating from Windows to Linux in regard to programming. I am currently aiming to learn Python and (Java or C/C++). Do any of you have any suggestions for making it a smooth transition?

Thanks.

---

### Post by Mirrorball on 2007-05-31
- To compile C/C++ programs, install the package **build-essential** from Synaptic. It will install the compiler **gcc** and some other tools you'll need.
- You can start learning Python now. You'll see it's easier than C#.
- Java is a good language to learn from a professional perspective.

---

### Post by samjh on 2007-05-31
If you're a C#/.NET programmer, you can immediately leverage that by using Mono ([www.mono-project.org](www.mono-project.org) ).

For Python, pmasiar is the user you want to contact.  He's very good about everything to do with Python.  But to get started, Python is already installed on Ubuntu by default.  Just type
```
python
```to bring up the interpreter.  There are a variety of IDEs in the repositories.  I like IDLE and SPE.

Python's website, [www.python.org](www.python.org) , has an excellent set of tutorials.


For Java, you will need to install Sun Java by typing this in the command-line:
```
sudo apt-get install sun-java6-jdk
```
And then either use a code/text editor and the command-line Java tools, or download an IDE (I recommend Netbeans - [www.netbeans.org](www.netbeans.org) - download the .bin file and run it to install, but make sure you're not using the "Desktop Effects" option on Ubuntu).

The best Java tutorial on the web is the official one: [http://java.sun.com/docs/books/tutorial/](http://java.sun.com/docs/books/tutorial/)


For C/C++, you need to install the g++ compiler.  You can install the essential build tools by typing this in the terminal:
```
sudo apt-get install build-essential
```
For good C/C++ tutorials, go here: [www.cprogramming.com](www.cprogramming.com)

Best of luck to you!

---

### Post by jro on 2007-05-31
I am a programmer and I worked for a while in C#/.NET. I felt bad when I moved back to Linux/Java development that all the C# skills I had accumulated over two years. But then I found Monodevelop and Glade. You can write some full featured desktop apps with C# and Glade. The Glade Interface Designer is slick and you can create GTK apps with C# backends. I have found it to be alot of fun and it keeps my C# skills fairly fresh.

---

### Post by cprofitt on 2007-05-31
Where would be a good point to learn Java if I want to write GUI applications with the language?

---

### Post by pmasiar on 2007-05-31
> **PrivateVoid said:**
> migrating from Windows to Linux in regard to programming. I am currently aiming to learn Python and (Java or C/C++). Do any of you have any suggestions for making it a smooth transition?.

Be prepared that Linux is different world than .NET: different object structure, different way to solve the same problems. It might be annoying. And if you decide to try Java, it is yet another world, designed to be incompatible. It might take couple years to become expert in each one.

If you are C# expert you need to think carefully if it makes sense to invest time learning Java, which is language pretty much like C#, only all libraries are different. More exactly, C# was designed to be MS version of  Java, when Sun sued MS. So unless you see clear way to use Java to advance your career, I would think that becoming better C# expert is better return of your time investment.

Linux is different - and learning Python is something I strongly recommend.  After C# (language with static typing), learning dynamically typed language like Python is quite an experience. Warning: after learning Python, programming in c# will feel clunky and less fun! :-)

To reuse your investment in learning .NET, you may want to look into IronPython: Python for .NET.

But even if you decide for IP, still invest time to slowly learn linux: it will take you substantial amount of time, but Linux is the way of future. Let me explain you why:

First, think about definition of [commodity](http://en.wikipedia.org/wiki/Commodity) like sugar or gas: when you are buying it, you look at convenience and price, not at brand.

20 years ago, small start-up Microsoft made hardware manufacturer IBM obsolete by creating MS-DOS as software platform, and transforming PC hardware into commodity. As profit margin declined, IBM could not compete and reinvented itself as software services company.

Now IBM is working hard to return the favor: converting operating system to commodity - and you cannot get it cheaper than free! :-)

It is called "commoditization" and that is why MSFT is so scared. But the precess is slow, MSFT is deeply entrenched, and it would take 10-20 years to broke the monopoly. But free software is more fun, and more rewarding personally, IMHO.

Java was Sun's attempt for similar goal, almost successful and short-time good to know. But short-time, C# is it's equivalent. Future belongs to dynamically typed languages (with time-critical code in C libraries of course) like Python on Linux.

---

### Post by barmazal on 2007-06-01
tbh i don't know why Novell went towards faking .NET for Linux. Their first aim should have been Windows developers as their reason was to screw MS.

I'm sure there are Linux native platforms that fits better Linux structure of applications. Unfortunately nothing close to C# or .NET except of Java which is C# origin.

I agree with pmasiar for a change but again future not for Python but for all high level languages when C libraries will be reused and improved by real programmers and not just those who want to write some small application fast. So C#, .VB, Ruby, Perl and anything else has has OOP and good framework will work out just fine.

C# is more strict(which make sense to some) and has much better IDE than Python has but Windows only.

Let's wait for .NET3.0 to come out with proper IDE which will turn programming into joy. Hopefully someone will fake it properly on Open Source basis so we can enjoy proper framework, easy IDE and great ability to see the code behind objects we call and not just hints with parameters.

---

### Post by cprofitt on 2007-06-01
> **pmasiar said:**
> Java was Sun's attempt for similar goal, almost successful and short-time good to know. But short-time, C# is it's equivalent. Future belongs to dynamically typed languages (with time-critical code in C libraries of course) like Python on Linux.

I fed at the Microsoft tit long enough so I am ready to make the jump. My job will still involve Microsoft, at least until I understand Linux well enough to champion it, because I manage an AD environment and program in .net for them.

I was an annual subscriber to their Action Pak -- $300 -- and you get a lot of their software for internal use. I just grow tired of having to throw money at them like that for little to no benefit -- though it was much cheaper than purchasing actual licenses for the software.

I enjoy writing small utility applications currently and do not care how much time it takes to learn as long as I have fun.

I will learn Python (just bought a book last night - though it covers 2.3 and not 2.5 as there were no books covering 2.5 available). The next question was C/C++/Java -- which one would be valuable. I may continue to toy with C# at home using Mono, but learning new things is more fun to me than becoming an expert in just one.

---

### Post by pmasiar on 2007-06-01
> **PrivateVoid said:**
> I fed at the Microsoft tit long enough so I am ready to make the jump. 

Excellent. I certanly understand your frustration. Been there done that.

> I will learn Python (just bought a book last night - though it covers 2.3 and not 2.5 as there were no books covering 2.5 available).

Changes between version are pretty minor to for better. Bigger change for you will be to let go stronghold on statid type check. :-) Check the version your ubuntu distro has. You can also "from __future__ import " many features - so you can have 2.5 features in 2.4. You can check "what's new" in each version

Check pythonchallenge website for fun tasks to solve. Good luck!

And don't forget IronPython - you can reuse your .NET library knowledge.

Seems like MSFT guys are smarter than many competitors, they realized (they hired IP author to help them realize BTW) that future programming paradigm is: "dynamic language for development speed, static compiled language libraries for execution speed". .NET 3.0 CLR has changes to run dynamic languages faster.

> The next question was C/C++/Java -- which one would be valuable.

C might be simpler to learn and more valuable (C libraries for Python speed). C++ will be very like C# when you need it in some project you decide to participate - easy switch. Java has the pain of learning completely different incompatible library - not /my/ definition of fun :-) 

Bruce Eckel (mindview.com) is expert behind "Thinking in..." series, which is available for free download, and C has nice course. His books are great what they are not focused on explaining features, but explaining *why* design decisions were made, and what are consequences. Highly recommended, also his blog and essays.

---

### Post by cprofitt on 2007-06-01
pmasiar:

Thanks for the reply -- lots of useful information....

Sounds like the best plan currently would be to learn Python -- exploit IronPython when needed -- and if the need really, really calls for it learn C for specific tasks.

---

### Post by pmasiar on 2007-06-01
Exactly.

C only for specific libraries, which you implemented in Python, and you *measured* that code is bottleneck.

---

### Post by Dyst Mingus on 2007-06-01
C/C++/Python & Java all have strengths and weaknesses. I have heard very little about Java in the replies. I disagree with the person who felt that Java would be a difficult language to learn because of the libraries. In fact, if you are used to C#, Java will be very intuitive for you.  My favorite Java IDE is eclipse, available fro eclipse.org. The Java Swing library will give you a toolbox of GUI components that are relatively easy to set up and will be portable to any system with the JRE installed. I am not knocking the other languages, i just think Java is worth having in your arsenal of tools. Java is a type safe (* weak parametric polymorphism due to a reluctance to change the JVM not withstanding), fully featured, portable language with tools to integrate with almost any emerging technology you can think of. It has tons of options for distribution and persistence and is in wide spread use. Why would you ignore it?  ;)

---

### Post by cprofitt on 2007-06-01
I will likely not ignore Java... in fact when I was still wearing the shades that Bill gave me I was debating Java vs. C#.net... obviously the wrong choice was made back then (well from the rear view mirror anyway) but at 40 I am not too old to learn new stuff, hehe.

---

### Post by jdunn on 2007-06-01
For Java development, I'm using Eclipse.  I'm very happy with it.  It was recommended for the course I'm taking.  Its available in the repositories.

---

