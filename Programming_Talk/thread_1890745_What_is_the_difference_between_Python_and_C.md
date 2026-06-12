---
title: "What is the difference between Python and C?"
date: 2011-12-04
forum: Programming Talk
---

### Post by enjoijesus94 on 2011-12-04
i program in Python So it much easier 
id say the diffrence between them is Python its easier and faster to code a program

With C its more complex and takes longer but the results in C are worthwhile:popcorn:

---

### Post by Petrolea on 2011-12-04
I prefer C over python, since I don't really like high-level languages. I like to know what I'm doing and want to have everything in program under control. Plus it's much faster.

C is also a compiled language which means that when you compile it you get an executable file, which later you can just double-click to run (or for non-GUI programs use terminal to run).

---

### Post by crinus on 2011-12-04
I think that Python's (and the like) power comes from the knowledge that a lot of things work like a service; if one is accustomed to doing shell scripting it's kind of natural to choose Python.  

I have a lot more experience in C than any scripting language, but currently I notice that more and more gets done by applying Python. C was very fun to use in learning all the details of programming, and it does exhibit more down-to-hardware approach. 

I would also speculate that doing certain apps and prototypes on the mobile world is easier with Python, if the platform in question has a good support for it. But I've only scraped a little bit of C++ in Symbian. It was horrible :-) Might have traumatized and biased my opinion.

---

### Post by nvteighen on 2011-12-04
The main difference is the abstraction level. The rest is either a consequence of that or just secondary.

Python is a high-level language, whose concepts are designed to be closer to general computational ones and therefore, closer to general logic, and in summary, closer to the way we humans think. For example, Python gives you built-in lists... I'm sure the concept "list" is not arcane for you, as you surely have written some list on paper at some point of your life, e.g. a shopping list. That's a very trivial case where you can see how high-level languages are more abstract, less dependent on a specific platform of execution and closer to general data structures.

C, instead of lists, gives you tools to build them. And those tools are defined with respect to your platform (a computer...). For example, you can implement a double-linked list in C using a simple struct, a couple of pointers and some functions that do some basic operations on that struct. However... a pointer, as defined in C, is a computer-specific concept... you don't use random access memory addresses or dereference pointers but only in programming.

Both are meant to be used for different tasks. Sometimes, the amount of control C gives you is an obstacle. If you've used GTK+ 
by hand you'll know what I mean. On the other hand, sometimes you need that control that Python doesn't give you...

Of course, in order to know what is the right tool for each task, you have to know several programming languages, and know them very well. People who just know one language (whichever it is) are doomed to fail. There's no magical receipt for this but to work hard and learn.

> **Petrolea said:**
> 
C is also a compiled language which means that when you compile it you get an executable file, which later you can just double-click to run (or for non-GUI programs use terminal to run).

That's also true for any non-compiled programming language that supports shebangs (e.g. #!/usr/bin/perl)... if the program has the shebang line as its first line, uses a GUI toolkit and it's been chmod'ed to be executable, then it will be launched by opening it from the DE just as if it was a compiled program. In fact, lots of Ubuntu programs are written in Python and you might have never noticed it.

---

### Post by tartalo on 2011-12-04
- You wouldn't write an OS Kernel in Python
- You wouldn't make a website with C
- You need a beard to use C, but you are allowed to use Python if facial hair didn't grow yet.

---

### Post by 11jmb on 2011-12-04
> **tartalo said:**
> - You wouldn't write an OS Kernel in Python
- You wouldn't make a website with C
- You need a beard to use C, but you are allowed to use Python if facial hair didn't grow yet.

I'm actually in need of a shave right now, so I guess I can write a few lines of C? :P

The way I see it, you need to select the right tool for the job. IMHO, Python is the best general-purpose language I have ever used. It will almost always by my language of choice if:
1. target architecture has a Python interpreter
2. performance (time and memory constraints) are not an issue
3. it is not text manipulation (perl)

I place a high value on my time (as should you) and Python allows me to develop extremely rapidly. I do have a lot of tasks that are number crunching or embedded systems work, so I write a lot of C as well, but it takes a lot longer to write good code in C (I think the beard grows faster as I code, though). 

> **nvteighen said:**
> The main difference is the abstraction level. The rest is either a consequence of that or just secondary.

Yes and no. Another important difference between languages is the intended purpose (why the language exists in the first place). As far as consequences of abstraction go, the consequence that I almost always see is the tradeoff between development time and performance.

---

### Post by rbaleksandar on 2011-12-04
If you want more control over the internal workings of your program, C/C++ is the way. If not, use Python. With internal workings I mean memory allocation, memory alignment, process management and IPC...Low-level stuff in simple terms. Let's not forget the fact that Python's main implementation is CPython -> created in C. The more high-level the language, usually the more over-bloated it gets because it tries to 'hide' the things that many programmers don't need. A Java-programmer doesn't need to know when his object is deleted if he is not using it because the Garbage Collector takes care of this. A Java-programmer doesn't need to access the registers of the CPU on his/her machine. Same goes for Python more or less. Many things in Python and other highe-level languages are already present. In C you usually have to creates your own stuff. This might be tiresome for some, but it sure takes you to the next level, learning more and more. Python is for rapid development and prototyping.

Hope this helps.

PS: It's definitely worth learning more than one language. C + Python would be nice.

---

### Post by 3Miro on 2011-12-04
> **tartalo said:**
> - You wouldn't write an OS Kernel in Python
- You wouldn't make a website with C

I agree, although it is worth noting that while you could make a web-page in C, you cannot make an OS kernel in Python.

Python is great for general programming so long as you don't aim specifically for performance and you don't have too much of python running on your system at once.

> 
- You need a beard to use C, but you are allowed to use Python if facial hair didn't grow yet.
Apart from the obvious sexism, this is true.

---

### Post by 11jmb on 2011-12-04
> **3Miro said:**
> I agree, although it is worth noting that while you could make a web-page in C, you cannot make an OS kernel in Python.

You can also build a house without any power tools

---

### Post by 3Miro on 2011-12-05
> **11jmb said:**
> You can also build a house without any power tools

I don't fully agree.

I have not done this in C, but I made a web-page in Delphi once. You just need to get the proper libraries and then things get only marginally harder than say Perl. So the better analogy is not about building ahouse without power tools, but rather making your own power tools first.

I agree that making a web-page in C is 100% impractical, however, it is worth pointing out that the Python modules that let you do a web-page are in fact written in C.

---

### Post by 11jmb on 2011-12-05
> **3Miro said:**
> I don't fully agree.

I have not done this in C, but I made a web-page in Delphi once. You just need to get the proper libraries and then things get only marginally harder than say Perl. So the better analogy is not about building ahouse without power tools, but rather making your own power tools first.

I agree that making a web-page in C is 100% impractical, however, it is worth pointing out that the Python modules that let you do a web-page are in fact written in C.

My point was simply that you should have a good reason for choosing a language for your task and that we have a good spectrum of low and high level languages for a reason. 

Don't read too far into the metaphor :)

---

### Post by 3Miro on 2011-12-05
> **11jmb said:**
> My point was simply that you should have a good reason for choosing a language for your task and that we have a good spectrum of low and high level languages for a reason. 


That much, I agree with.

---

### Post by Petrolea on 2011-12-05
> **nvteighen said:**
> 
That's also true for any non-compiled programming language that supports shebangs (e.g. #!/usr/bin/perl)... if the program has the shebang line as its first line, uses a GUI toolkit and it's been chmod'ed to be executable, then it will be launched by opening it from the DE just as if it was a compiled program. In fact, lots of Ubuntu programs are written in Python and you might have never noticed it.

I'm aware of that. But the difference between an executable script file and compiled binary file is still huge.

---

### Post by cgroza on 2011-12-05
> **Petrolea said:**
> I'm aware of that. But the difference between an executable script file and compiled binary file is still huge.
Not from the user's perspective.

---

### Post by 3Miro on 2011-12-05
> **cgroza said:**
> Not from the user's perspective.

This is generally true, but certainly not always. The way you start a program is the same, but I could definitely see the difference in memory usage between Transmission and Deluge, and if the user runs too many Python apps then they will notice.

Also, this is the developers sub-forum and C vs Python makes a huge difference for a developer.

---

### Post by Bodsda on 2011-12-06
> **11jmb said:**
> 
3. it is not text manipulation (perl)


What text manipulation can you do with perl that you can't do with python? Especially as the re module tries to be as perl like as possible.

---

### Post by 3Miro on 2011-12-06
Hey Bodsda, did you mean:

```
while(!(succeed == Try()));
```

I guess 
```
while(!(succeed = Try()));
```
could be a good joke to see who would catch it.

---

### Post by matt_symes on 2011-12-06
> **nvteighen said:**
> The main difference is the abstraction level. The rest is either a consequence of that or just secondary.

Python is a high-level language, whose concepts are designed to be closer to general computational ones and therefore, closer to general logic, and in summary, closer to the way we humans think. For example, Python gives you built-in lists... I'm sure the concept "list" is not arcane for you, as you surely have written some list on paper at some point of your life, e.g. a shopping list. That's a very trivial case where you can see how high-level languages are more abstract, less dependent on a specific platform of execution and closer to general data structures.

C, instead of lists, gives you tools to build them. And those tools are defined with respect to your platform (a computer...). For example, you can implement a double-linked list in C using a simple struct, a couple of pointers and some functions that do some basic operations on that struct. However... a pointer, as defined in C, is a computer-specific concept... you don't use random access memory addresses or dereference pointers but only in programming.

Both are meant to be used for different tasks. Sometimes, the amount of control C gives you is an obstacle. If you've used GTK+ 
by hand you'll know what I mean. On the other hand, sometimes you need that control that Python doesn't give you...

Of course, in order to know what is the right tool for each task, you have to know several programming languages, and know them very well. People who just know one language (whichever it is) are doomed to fail. There's no magical receipt for this but to work hard and learn.



That's also true for any non-compiled programming language that supports shebangs (e.g. #!/usr/bin/perl)... if the program has the shebang line as its first line, uses a GUI toolkit and it's been chmod'ed to be executable, then it will be launched by opening it from the DE just as if it was a compiled program. In fact, lots of Ubuntu programs are written in Python and you might have never noticed it.

Very nicely put !

This is one of the most succinct answers i have seen for ages so i am going to re-quote it.

The only main extension i can add to it is that certain abstractions are designed for certain problem domains; think Fortran, lisp and so on.

---

### Post by Simian Man on 2011-12-06
> **Petrolea said:**
> I like to know what I'm doing and want to have everything in program under control.
If you are running your programs on a modern operating system, then you do not have control over everything in your program.  The OS schedules your program, it moves around your memory, it talks to devices for you.  Do you really think your pointers refer to actual memory locations?  The addition of the Python virtual machine is hardly any different.

> **Petrolea said:**
> C is also a compiled language which means that when you compile it you get an executable file, which later you can just double-click to run (or for non-GUI programs use terminal to run).
Other people have corrected you already, but this is not true. Even if it were, it would be a laughable reason to pick one language over another.

---

### Post by Bodsda on 2011-12-06
> **3Miro said:**
> Hey Bodsda, did you mean:

```
while(!(succeed == Try()));
```I guess 
```
while(!(succeed = Try()));
```could be a good joke to see who would catch it.

Works either way, with the equal to operator the expression is evaluated as True if succeed is equal to the return value of Try(), the result of the expression is evaluated for the loop with this one.

With the assignment operator the expression assigns the return value from True() to succeed, the value of succeed is evaluated for the loop with this one.

Bodsda

---

### Post by Petrolea on 2011-12-06
> **Simian Man said:**
> If you are running your programs on a modern operating system, then you do not have control over everything in your program.  The OS schedules your program, it moves around your memory, it talks to devices for you.  Do you really think your pointers refer to actual memory locations?  The addition of the Python virtual machine is hardly any different.


Other people have corrected you already, but this is not true. Even if it were, it would be a laughable reason to pick one language over another.

By having everything under control I didn't mean all those low level things that OS does. I meant for example declaring variable size (int, long, short), managing the allocation and resizing of dynamic arrays by myself (not just doing ArrayList.Add) and so on. 

---

I didn't really say it clear but what I meant was that you actually get a file comparable to Windows's .exe files, which you just run and can't edit like a text file.
The other option that others described looks pretty much the same from users perspective, but from programmers perspective is completely different, since the resulting program is just a text file and not a binary file. 

And for me, this is an important reason to choose a programming language, but that changes from person to person.

---

### Post by Simian Man on 2011-12-06
> **Petrolea said:**
> By having everything under control I didn't mean all those low level things that OS does. I meant for example declaring variable size (int, long, short), managing the allocation and resizing of dynamic arrays by myself (not just doing ArrayList.Add) and so on.
Well that isn't having "everything" under your control is it?  Declaring the types of variables and manually resizing arrays is not control, it's minutia.

> **Petrolea said:**
> I didn't really say it clear but what I meant was that you actually get a file comparable to Windows's .exe files, which you just run and can't edit like a text file.
The other option that others described looks pretty much the same from users perspective, but from programmers perspective is completely different, since the resulting program is just a text file and not a binary file.
It is different, but how does that affect you as a programmer (except for speed of course)?  How is having a binary file any better than having a text one?  Even if you wanted a binary file, you can easily compile Python to bytecode .pyc files.

> **Petrolea said:**
> And for me, this is an important reason to choose a programming language, but that changes from person to person.
Choices like this are definitely personal, but when the reasons don't make sense and are given to beginners, I'm compelled to challenge them.

---

### Post by Petrolea on 2011-12-06
@Simian man

I understand that you replied to clears things up, that's the point of a discussion.

Yes, the speed was my main thought when talking about binary files.

---

