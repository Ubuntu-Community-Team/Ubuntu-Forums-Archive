---
title: "Coding on Linux"
date: 2011-06-19
forum: Programming Talk
---

### Post by Grenad on 2011-06-19
First of all, sorry if this thread is in the wrong section; I didnt see a programming section (maybe there should be one...).

So my question is, what are the best coding language options for Linux, specifically Ubuntu. Just to clarify, Linux is not my target; I just want to use it to do the programming, although being able to run my programs on Linux would be great. I already know C# pretty well but I have long since become annoyed with Microsoft and moved away (I LOVE Linux now:D). So, I figured I should learn another language since C# is mainly for Microsoft. I want to learn Python because it is portable, flexible, and object-oriented, and I also use Blender (<--great software) which is entirely written with Python, so Python would be of great use there. I have heard Java is very sloppy so I havent looked into that very much, and most other options arent as widely used.

 So, any suggestions will be greatly appreciated! Thanks in advance.

---

### Post by idoitprone on 2011-06-19
You can use c sharp. Just install mono, but it only supports up to .net 2.0 and the project that in charge of it is going nowhere

Unix is designed by programmers for programmers, which means linux tends to be a programming playground with support for so many languages. Java is not sloppy, it is one of the best cross-platform languages there is. Many scientific and mathematical programs are written for java.

---

### Post by lisati on 2011-06-19
*Thread moved to **Programming Talk**.*

---

### Post by nzjethro on 2011-06-19
Coming from a little bit of programming experience, I would not say that Java is sloppy at all. I've found Java extremely useful, for a range of applications. But if you are looking to learn a language "for Linux, specifically Ubuntu", I'd go Python. It's a bit more flexible than C# (or so I've heard), and is very easy and intuitive to pick-up. It also goes great in the Linux / FOSS world, as a lot of FOSS programmes use it.

---

### Post by Grenad on 2011-06-19
Haha thanks for moving it to programming talk, didnt see it;)

Thanks for the quick replies. I will definitely look further into Java, So I guess Java isnt that sloppy but could I use it for most anything from game development to desktop apps and the web? I like the look of Python but I dont know if I should use it. What about Boo? Is that a good language? I just want to know what some good languages are for different scenarios.

---

### Post by idoitprone on 2011-06-19
Since you heard java was sloppy, I guess those people are referring how the language was implemented. Even though the syntax may be simple to the eye, the underlying mechanism is complex with java. I guess it is due to the fact is contain features and many other things that add complexity. It is still a good language that is cross-platform. For the most part, if it compiles, it works unlike c, c++ and many other programming languages


[http://quotes.cat-v.org/programming/](http://quotes.cat-v.org/programming/)
there some people who hate java in there
[http://harmful.cat-v.org/software/java](http://harmful.cat-v.org/software/java)

[http://en.wikipedia.org/wiki/Criticism_of_Java](http://en.wikipedia.org/wiki/Criticism_of_Java)

---

### Post by zobayer1 on 2011-06-19
mono is mono, it will always be mono, it can never be C#, so you should go for python ... :) The syntax of java is very similar to C#, so that may not be a trouble to you.

---

### Post by juancarlospaco on 2011-06-19
Python

---

### Post by TwoEars on 2011-06-19
> **juancarlospaco said:**
> Python

Wow, great answer, very detailed, I'm sure everyone will now consider Python :rolleyes:
Helpfulness includes proper answers, not single word answers. Just saying.



Anyway, OP -

It depends entirely on what you want to do. 

If you're planning on developing a cross-platform application for mainstream use, and your main target isn't Linux, then I don't suggest you use Python, but I suggest you use Java. Java is excellent for cross-platform applications, and though the language is pretty disgusting IMO, it's one of the most popular. Unfortunately, Python isn't great for applications on Windows due to the infrastructure. If your main target is Linux, then Python is great, in fact, ideal.

If you're just wanting something to use by yourself, Mono will be fine. Cross platform, and you know it already. However, for a Linux mainstream application, you'll run into issues with people whining about how evil Microsoft is. (Not the thread for this discussion, just accept it as a given). If you're still wanting to learn a new language, Python is pretty great. 

If you want a language for employment chances, I suggest you go with Java. Once you know Java, your employability rises drastically.

---

### Post by kagov on 2011-06-19
I'd definitely go with Java, it's syntax is very nice, the API is very nice, plus it opens up windows of opportunities, after learning Java, I found that learning C was so much easier. However if you don't want to do Java you could try Ruby.

---

### Post by simeon87 on 2011-06-19
Why are people recommending Java? The OP is asking for a language for Ubuntu so clearly Java is not a good choice: Ubuntu's programs are written in C, C++ or Python and very few in Java.

A language such as Python or C would be a better choice.

---

### Post by nzjethro on 2011-06-19
> **Grenad said:**
> 
So I guess Java isnt that sloppy but could I use it for most anything from game development to desktop apps and the web? What about Boo? Is that a good language?

No, not sloppy at all, and yes, a vast range of applications can be programmed with Java (of course Minecraft being a reasonably high-profile recent case). Java can also be used on just about anything (any OS or architecture, smartphones, electronics, servers, etc.) - one of it's main drawcards.

Never heard of Boo, but this is definitely the place to be asking these kinds of questions and getting good responses.

As for what is a "good language", a lot of it will come down to you setting out plans for where you'd like your programming to go, whether into kernel programming, game programming, web programming, application programming etc., and then deciding what tools you'll need for that, and then determining which language best provides those tools. In terms of Linux-based programming you can't go past Python, but for a broader range of architectures Python may not be so well suited.

---

### Post by nvteighen on 2011-06-19
> **zobayer1 said:**
> mono is mono, it will always be mono, it can never be C#, so you should go for python ... :) The syntax of java is very similar to C#, so that may not be a trouble to you.

You're misinformed: Mono is a FOSS implementation of MS .NET Framework, which is a VM that works using a specific bytecode called CLI. It's roughly the same as OpenJDK or the (dead?) GNU Java Compiler projects are compared to the formerly Sun's, now Oracle's "official" Java platform.

On the other hand, MS created several languages which they decided to implement for the .NET platform: C#, VB.NET and Silverlight are some of them. So, C# is compiled to CLI to be run on .NET or its FOSS-equivalent, Mono.

The problem you refer to is that Mono is always some steps behind .NET, but that's an inherent problem with projects that aim to clone/port another technology.

> **simeon87 said:**
> Why are people recommending Java? The OP is asking for a language for Ubuntu so clearly Java is not a good choice: Ubuntu's programs are written in C, C++ or Python and very few in Java.

A language such as Python or C would be a better choice.

Java is a language for Ubuntu as much as all other languages that can run on it. The amount of programs written in it is irrelevant, the actual problem being its poor popularity in the FOSS world.

But if Java is technically better for the task, use it. It's not a good language, but it's an impressive platform that supports portability and cross-platform better than everyone else.

---

### Post by kagov on 2011-06-19
> **simeon87 said:**
> Why are people recommending Java? The OP is asking for a language for Ubuntu so clearly Java is not a good choice: Ubuntu's programs are written in C, C++ or Python and very few in Java.

A language such as Python or C would be a better choice.

> **Grenad said:**
> 
So my question is, what are the best coding language options for Linux,  specifically Ubuntu. Just to clarify, Linux is not my target; I just  want to use it to do the programming.

He wants a *good* programming language that he can program on Linux but not for Linux.

---

### Post by TwoEars on 2011-06-19
> **simeon87 said:**
> Why are people recommending Java? The OP is asking for a language for Ubuntu so clearly Java is not a good choice: Ubuntu's programs are written in C, C++ or Python and very few in Java.

A language such as Python or C would be a better choice.

Because 1) He stated that Linux isn't his main target, but he would like his programs to run on them, 2) Python isn't widely used for applications on Windows, and 3) Java is one of the most popular languages out there, as well probably one of the best as far as employment goes. Read my other post for more reasons. For all of these reasons, neither Python nor C would be a good choice.

---

### Post by simeon87 on 2011-06-19
> **nvteighen said:**
> Java is a language for Ubuntu as much as all other languages that can run on it. The amount of programs written in it is irrelevant, the actual problem being its poor popularity in the FOSS world.

The lack of programs written in it is, of course, a result of its poor popularity in the FOSS world.

> **nvteighen said:**
> But if Java is technically better for the task, use it. It's not a good language, but it's an impressive platform that supports portability and cross-platform better than everyone else.

I agree.

> **kagov said:**
> He wants a *good* programming language that he can program on Linux but not for Linux.

Are you saying Java is good compared to Python / C ? Java is decent but not great. Like nvteighen said its strength comes from the platform, not the language.

> **TwoEars said:**
> Because 1) He stated that Linux isn't his main target, but he would like his programs to run on them, 2) Python isn't widely used for applications on Windows, and 3) Java is one of the most popular languages out there, as well probably one of the best as far as employment goes. Read my other post for more reasons. For all of these reasons, neither Python nor C would be a good choice.

1) C is a good choice for both Linux and Windows; Python with some effort as well but I agree with your point (2) that it's not common to use Python for Windows applications. Point 3 is true although many Java projects in companies are boring consulting projects - you will have a job but the majority of projects will be CRUD work: moving data around.

The OP also expresses a desire to learn Python. Lastly, he knows C# pretty well which is very similar to Java and better in some respects. There's no point in learning Java because it can be picked up easily if you know C#.

---

### Post by TwoEars on 2011-06-19
> **simeon87 said:**
> 
1) C is a good choice for both Linux and Windows; Python with some effort as well but I agree with your point (2) that it's not common to use Python for Windows applications. Point 3 is true although many Java projects in companies are boring consulting projects - you will have a job but the majority of projects will be CRUD work: moving data around.

The OP also expresses a desire to learn Python. Lastly, he knows C# pretty well which is very similar to Java and better in some respects. There's no point in learning Java because it can be picked up easily if you know C#.

C is a good choice - if you are willing to maintain slightly different versions for each OS, and compiling for different OSs. Java is "plug and play" - no need to mess around with compatibility coding. 
I know, I know, I hate Java too. It's okay. But sometimes to get onwards in life, we all have to learn how to do evil things. :P

I would not put him off learning Python, Python is without a doubt my favourite language, but in order to meet the needs he's described, I feel that Java's the better choice.

---

### Post by JupiterV2 on 2011-06-19
I would suggest Java as well. I don't particularly like the language itself (overly verbose, exception handling mechanism, etc) but it literally is a "write once, run anywhere" language. That is of course, if you don't count the fact that OpenJDK only has up to the Java SE6 specification. However, that being said, I've yet to come across a Windows PC without a Java VM installed. Not to say they don't exist but just that most do. Unless you plan to use third party libraries like SWT, dependencies aren't an issue either. I just hope stable OpenJDK will have SE7 soon...

Contrast this to Python, which is ideal for Linux, you'll find most Windows users will need to install Python in order to run your program. Depending on your audience this could be an huge issue for some users.

---

### Post by kagov on 2011-06-19
> **simeon87 said:**
> Are you saying Java is good compared to Python / C ? Java is decent but not great. Like nvteighen said its strength comes from the platform, not the language.

Perhaps not over C, but over Python yes (I generally dislike Python).

---

### Post by cgroza on 2011-06-19
> **kagov said:**
> Perhaps not over C, but over Python yes (I generally dislike Python).
Python is godsent!

---

### Post by Grenad on 2011-06-19
Alright, right now I think the general vote is for Java. I am considering java since it seems to be very popular and, apparently, not sloppy. However, I am still considering Python. I don't see why Python is such a bad choice. It seems very flexible, it has a lot of different uses, and if I wanted to run it on Windows, couldn't I just bundle python in the download (like blender does)? And as for C, I have never really wanted to use it. I dont know much about it but from what I see, it is not widely used and it is outdated. But I also know that it is used in the core of many great apps that I use (such as unity3d, which is so stubborn as to not make a linux version :mad:, but that is a topic for another thread). Im not really sure about C.

---

### Post by simeon87 on 2011-06-19
> **Grenad said:**
> Alright, right now I think the general vote is for Java. I am considering java since it seems to be very popular and, apparently, not sloppy.

It wouldn't be my advice given that you already know C#. I think you'll learn more new things from Python or C than from Java. The programming style in C# is quite similar to Java but Python and C open up new possibilities of writing your code.

> **Grenad said:**
> However, I am still considering Python. I don't see why Python is such a bad choice. It seems very flexible, it has a lot of different uses, and if I wanted to run it on Windows, couldn't I just bundle python in the download (like blender does)?

Python is not a bad choice, many people develop their applications and websites in Python. Various companies are now also using Django (written in Python) for their websites and not some PHP framework. You can bundle Python with your program's installation, that's not a problem. It's just that you need to do this, Python is not installed by default on Windows. But then, the JVM for Java isn't installed by default either, although many probably have it installed by now.

> **Grenad said:**
> And as for C, I have never really wanted to use it. I dont know much about it but from what I see, **it is not widely used and it is outdated**. But I also know that it is used in the core of many great apps that I use (such as unity3d, which is so stubborn as to not make a linux version :mad:, but that is a topic for another thread). Im not really sure about C.

That's just plain wrong, it's used far more than Java or Python. Operating systems, compilers, embedded systems and more are written in C.

---

### Post by cgroza on 2011-06-19
> **Grenad said:**
> Alright, right now I think the general vote is for Java. I am considering java since it seems to be very popular and, apparently, not sloppy. However, I am still considering Python. I don't see why Python is such a bad choice. It seems very flexible, it has a lot of different uses, and if I wanted to run it on Windows, couldn't I just bundle python in the download (like blender does)? And as for C, I have never really wanted to use it. I dont know much about it but from what I see, it is not widely used and it is outdated. But I also know that it is used in the core of many great apps that I use (such as unity3d, which is so stubborn as to not make a linux version :mad:, but that is a topic for another thread). Im not really sure about C.

C, outdated? Heck, in 50 years from now, C will still be here and all those languages will be long forgotten and replaced. We do the programming languages, drivers and OS in C.

I will be dead, my kids too, but my nephews will program in C.

---

### Post by TwoEars on 2011-06-19
I find it hard to believe that anyone can dislike Python unless they haven't tried it, and merely pass it off as "one of those crazy languages for kids".

@OP

As for Python, if you read my original post, I explain when you should use Python for cross-platform development and when you shouldn't. 

If using for yourself and yourself alone, then go crazy with Python.

If developing for Linux as a primary target, then go crazy with Python.

Else just use Java. It will save hassle.

Also, C's no-where near obsolete. You simply didn't get any support for because it's not as cross-platform as Java/Python/Mono. C is used almost everywhere.

---

### Post by Grenad on 2011-06-19
Ok I guess my friend was COMPLETELY wrong about C. Sorry bout that.

I am going to try to learn Python since I think that Java would be relatively easy to learn from C#. Then I will try to pick up Java. But is C similar to C# at all? Will it be difficult to learn from a C# standpoint?

---

### Post by TwoEars on 2011-06-19
> **Grenad said:**
> Ok I guess my friend was COMPLETELY wrong about C. Sorry bout that.

I am going to try to learn Python since I think that Java would be relatively easy to learn from C#. Then I will try to pick up Java. But is C similar to C# at all? Will it be difficult to learn from a C# standpoint?


Knowing C# will be very little help in learning C. They are completely different beasts. One of the best ways to teach someone C that I've found is to first teach them Python, then teach them how to convert their Python applications into their C equivalents. This is also what I do with all production code, as it cuts down developing time amazingly.

---

### Post by lykwydchykyn on 2011-06-19
> **TwoEars said:**
> One of the best ways to teach someone C that I've found is to first teach them Python, then teach them how to convert their Python applications into their C equivalents. This is also what I do with all production code, as it cuts down developing time amazingly.

Not to hijack the thread, but do you have a resource for learning how to do that?  I've tried to jump from python to a compiled language and not had much success.

@OP:  I think the hard part about answering this question is that it depends on what you're programming and for what purpose you're programming.  I use python to develop software for Windows all the time at work, but since it's work I have tighter control over the workstations it's going to run on.  So the whole "python isn't good for windows" thing isn't necessarily true.

---

### Post by TwoEars on 2011-06-19
> **lykwydchykyn said:**
> Not to hijack the thread, but do you have a resource for learning how to do that?  I've tried to jump from python to a compiled language and not had much success.

I'm afraid not. I just play it as it comes, teach Python, teach basics of C, translate minor programs from Python to C, learn more about C, improve on translated programs, then more on to creating more complicated programs in Python, and start over again.
It's the sort of thing you can't learn from a book, but from pure practice.

---

### Post by kagov on 2011-06-19
> **cgroza said:**
> Python is godsent!

I may look back into it (everything deserves a second chance eh?), but i disliked it ever since I tried it a while back.

---

### Post by cgroza on 2011-06-19
> **kagov said:**
> I may look back into it (everything deserves a second chance eh?), but i disliked it ever since I tried it a while back.

I learned programming with it and the way the language gets out of my way and lits me think in my human way amazes me.

What aspects of python you do not like anyway?

---

### Post by idoitprone on 2011-06-19
The c language is really simple. There are many reason why for os programming c is superior to other languages.

[http://net.pku.edu.cn/~course/cs101/2008/resource/The_C_Programming_Language.pdf](http://net.pku.edu.cn/~course/cs101/2008/resource/The_C_Programming_Language.pdf)



c++ people who design os tend to hate it. Of course, they hate many other languages such as java and etc.

[http://harmful.cat-v.org/software/c++/](http://harmful.cat-v.org/software/c++/)

As other say, c# is close to java.

---

### Post by Shippou on 2011-06-19
Hello guys/gals.

I tried reading all responses to this thread, but honestly, I got bored. :)

To the OP: just use what you know. Rephrasing that a little bit, just use what you think is appropriate for what you want to implement. You don't need to learn a new programming language, let's say C++ or APL, in order to produce an app if you can do it in a language you already know, say Java or Fortran. Not only will you need time to learn the new language, you will also need time to master the language. Using a language you already know not only eliminates this, but also allows you to concentrate more on what you want to implement than syntax and other stuff that may be irrelevant to what you want to do. 

Just a side note, I would like not only you, but also others to read about this article:

Teach Yourself Programming in Ten Years
[http://norvig.com/21-days.html](http://norvig.com/21-days.html)

[rant]
Honestly, can we just abandon the language/framework wars? Each of them has their own pros and cons, no matter how questionable they may be.
[rant]

I hope we also have BBCodes for [rant]. :lol:

---

### Post by Grenad on 2011-06-19
@Shippou

I didnt think this was a war going on here. I just asked for suggestions on a second language to learn, and everyone has given me their opinions and suggestions. I want to learn a second language to be able to use different languages for different purposes and to broaden horizons. But thanks for the suggestion and the link!

---

### Post by llanitedave on 2011-06-19
There's a lot I like about Python, but it's downfall is performance, if you want to do really intensive data manipulation, modeling, or simulations.

C is easy to learn, but it's said to be hard to master.  I don't know, my own knowledge of it is rudimentary, but I do enjoy what it is capable of.  If you want raw performance, C will give it to you.

Both Python and C are easy to learn, and they each compliment one another in their strengths and can support each other in their weaknesses.  It seems to me that having knowledge of both Python and C, and using them together in an application, would make for an extremely powerful combination.

Use Python for the interface, security and management functions of your app, and use C for high performance routines that involve lots of loops or calculations.

---

### Post by GenBattle on 2011-06-20
I agree with others pointing to C and Python. Both are very useful to know, and they both give you very different perspectives and styles of programming (but not as different as something like Go or Haskell or something).

Python is more useful for desktop apps, scripts, web sites, etc.

C is more useful for hardware programming, drivers, OS programming, High speed data processing, etc.

That said, both languages can be used for many other purposes, and even overlap each other. They can also be used in combination; a C program can execute python code and vice versa.

---

### Post by juancarlospaco on 2011-06-20
Python can use C directly...

---

### Post by cgroza on 2011-06-20
> **juancarlospaco said:**
> Python can use C directly...
The CPython implementation. Do not forget there is a Java JPython implementation.

---

### Post by TwoEars on 2011-06-20
> **cgroza said:**
> The CPython implementation. Do not forget there is a Java JPython implementation.

There are many more than just two. ;)

---

### Post by DangerOnTheRanger on 2011-06-20
Let's not forget that [IronPython]("http://ironpython.codeplex.com/") can use .NET code, as well...

---

### Post by cgroza on 2011-06-20
> **DangerOnTheRanger said:**
> Let's not forget that [IronPython]("http://ironpython.codeplex.com/") can use .NET code, as well...
You mean CLI bytecode...:)

---

### Post by Shippou on 2011-06-21
> **Grenad said:**
> @Shippou

I didnt think this was a war going on here. I just asked for suggestions on a second language to learn, and everyone has given me their opinions and suggestions. I want to learn a second language to be able to use different languages for different purposes and to broaden horizons. But thanks for the suggestion and the link!

Sorry if I misinterpreted the flow of the thread. Thanks for pointing it out. :)

If you want suggestions for another programming language to learn, I would give a list. Please note that I am only giving what I think is appropriate. So please tread with caution.

Cross-platform:
1. Java
2. ActionScript
3. .Net or Mono

Linux mostly-used languages:
1. C
2. C++
3. Python

Pure OOP languages:
1. Java
2. Ruby

Web apps:
1. PHP
2. Python
3. Groovy

Functional programming:
1. LISP
2. Scheme

Logical programming:
1. Prolog

Standard three-stool development for web apps:
1. HTML
2. JavaScript
3. CSS

I would also like to suggest that you learn an application framework, for it can simplify your application code and workflow considerably.

Some frameworks:
1. CodeIgniter - for PHP
2. Ruby on Rails - for Ruby
3. Groovy on Grails - Groovy

I would also like to mention some useful libraries:
1. JQuery - JavaScript
2. wxWidgets

Please note that I am more of a webapp programmer.

Happy coding! :)

---

### Post by cgroza on 2011-06-21
> **Shippou said:**
> 

Functional programming:
1. LISP
2. Scheme
:)
Haskell !?!?!?!?! I thought it is pretty popular.

---

### Post by Grenad on 2011-06-22
Ok sorry I couldnt get back to this thread for a few days; the giant storm in the midwest this week blew out the electricity.

Alright, I have one more question. What if I want to sell my code? I learned the basics of Python over the past few days, and from that I know that python is not good at protecting source code. What languages can be safely distributed for profit? I know that there is always a way to get at the source code but I want to know some ones that are good at protecting it. Also, if anyone knows a good way to protect python source code, I would very much like to know.

---

### Post by GenBattle on 2011-06-23
> **Grenad said:**
> Ok sorry I couldnt get back to this thread for a few days; the giant storm in the midwest this week blew out the electricity.

Alright, I have one more question. What if I want to sell my code? I learned the basics of Python over the past few days, and from that I know that python is not good at protecting source code. What languages can be safely distributed for profit? I know that there is always a way to get at the source code but I want to know some ones that are good at protecting it. Also, if anyone knows a good way to protect python source code, I would very much like to know.

You can compile python source code to pyc bytecode, so it's about as safe as java, c#, etc. In the end the only way most code is "protected" is by being compiled to binary. this process removed most of the information that allows people to make sense of the program, but it is still possible to reverse-engineer code. I would say python is no less safe for commercial apps than any other language. I have seen it used in commercial apps before; Cyberlink seem to use it in their apps, i've seen them shipping pyc files. CCP Also use a form of Python (stackless) in EVE online. Just go to the python.org website, they have a list of endorsements from companies using Python in commercial software every day.

---

