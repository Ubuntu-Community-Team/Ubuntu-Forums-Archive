---
title: "[SOLVED] A working cross-platform sound library"
date: 2008-08-23
forum: Programming Talk
---

### Post by WitchCraft on 2008-08-23
Anybody knows a WORKING cross-platform sound library?

I've been trying OpenAL, but it is impossible to set it up with MinGW.

Then I tried ccaudio2-0.1.0, but it doesn't compile on my Linux machine.

Then I tried libmad, but this is again impossible to set up with MinGW.

I need something to play wav and mp3 or ogg on Linux, BSD, and Windows, and it would be nice if it worked with Apple, too.

And I don't want to use SDL for various reasons.

Any suggestion?

---

### Post by Reiger on 2008-08-23
Ehrm... Java! :D

---

### Post by WitchCraft on 2008-08-23
> **Reiger said:**
> Ehrm... Java! :D

errrm, never!!! If at all, I prefer to shoot a  bullet directly in my head.

But never  mind, i got OpenAL to work (f***ing dll-hell, i hate windows)

---

### Post by StOoZ on 2008-08-23
im not a java programmer , but why do people are so anti-java?

---

### Post by stevescripts on 2008-08-23
Another alternative is Snack:

[http://www.speech.kth.se/snack/](http://www.speech.kth.se/snack/)

For a couple of little projects I have done, it was quite useful.

Steve

---

### Post by kknd on 2008-08-23
I use gstreamer. Very powerful! Theres also audiere.

---

### Post by WitchCraft on 2008-09-13
> **StOoZ said:**
> 
im not a java programmer , but why do people are so anti-java?


Because Java doesn't work.
Instead of operating system version dependancy, it creates a JVM dependency.
Because it is closed-source.
Because a program is not compiled, but interpreted, running very slow.
Because it has problems handling Unicode.
Because Microsoft deliberately tries to make Java-Programs not working on Windows.
Because there is no decent IDE that works on all platforms.
Because Java programs are only marginally less difficult to write than C++ programs.
Because you can use C++ and wxWidgets, and your programs also run on all major platforms, and wxWidgets is OpenSource, and C++ is compiled, and runs and starts fast as hell compared to Java.
Because most Java programs I ever tried crashed at some point like opening or closing the application, or before saving a document.

Because most Java programmers are MORONS.
This has to do with the number of people in the world that describe themselves as Java programmers and work at day jobs doing Java programming. What are there, like 15 million of them? More? So it's just a numbers thing, really. There just aren't that many good programmers overall in the world -- and most them wouldn't be caught dead doing Java.


Because IIS does not support JSP.

Java is too Fragmented
Java has a gazillion open-source frameworks, and because most of them don't work either with your IDE or your version of the Java Virtual Machine, or because a moron wrote them, they all are worth nothing.

Java is Too Slow
You can't use it for any larger project, because if somebody uses an older computer, it will take forever for a simple progam to load (e.g. tax or online-banking programs). That's almost never a problem when using C++.

Java has bad debugging support
Java has "great and powerful" debugging (which is very necessary since most Java code sucks so much).

No warnings - There’s often no warning that you’re about to click on a link or enter a site which requires Java. I think this should be mandatory in the same way that browser’s often give you security warnings about certain sites.

"No Memory leaks"
Actually this is completely the opposite: With a language supporting garbage collection, such as Java, you are leaking memory all the time.
Memory is constantly being allocated dynamically (often more than would be really necessary) and then "forgotten" (the language actually forces you to forget about them). That is, the coder leaves it to the garbage collection engine to clean up his memory allocation mess. Why does this matter? It matters for the exact same reason why memory leaks are bad in general: They consume more memory than necessary. What the garbage collection scheme causes is that the process will consume more memory than it really needs (in pathological cases it can consume even hundreds of times more memory than it really is using). This memory is away from other processes running in the same system. Unless the operating system has a way to tell the garbage collection engine "hey, free up some unneeded memory", it will hog everything it can and other processes may suffer from shortage of free memory. The fact is that garbage collection is a selfish algorithm. It only takes care of the program itself not running out of memory due to a memory leak. Unless it has a really close relation to the OS, it completely disregards the memory usage of other processes. 


Sharing a resource
An argument which is sometimes presented is that garbage collection makes it easier to share data between several objects: If two or more objects share the same reference to some data, since the objects don't need to take care of freeing the data, the programmer doesn't have to decide which one of the objects is responsible for this freeing. However, if you have this kind of code in your program, you have a serious flaw in your OO design. In good OO design one object makes one task, and the responsibilities of each object is crystal-clear. If you have an ambiguity in responsibilities, then your OO design is crappy. And: Memory is not the only resource which can be allocated and freed. What if the shared resource is, for example, a file handle? Which one of the objects should be responsible for freeing it? If the problem is in crappy OO design, the right solution is not to encourage this practise by building a compiler feature which encourages this. 

GargabeCollection efficiency
Some garbage collection engines make memory deallocation faster than it would be eg. in C++ with explicit deallocations. This is because they can optimize by merging several deallocations into one using complex algorithms. A program which is constantly allocating and deallocating large amounts of small chunks of memory can sometimes see a speed benefit from such GC. Of course GC advocates use this fact to boast about GC being faster than explicit memory management. However, this is a bad generalization. Yes, there are cases where it makes the program faster. However, there are many other cases where it makes the program, and worse, the entire OS much slower. 

Memory consumption
By its very design Java is a memory hog. You simply can't make a memory-efficient program which handles enormous amounts of data while still preserving good object-oriented abstraction in your program. 

Only references
Java coders will tell you that Java has no pointers. However, in Java everything is a pointer (they are just called references). Granted, these "pointers" are safer than C++ pointers, but they are still just "handles" to the object, and you can't get the object itself. Why does this matter? Well, you can't easily, for example, give an object to a function by value, swap the values of two objects, etc. While it's rather rare to have to do these kinds of things, when you would have to, I wish you good luck (and having much time). 

# Since there's no easy way of abstracting internal types away and since there's no operator overloading (which could be used to easily change an internal type to a class), programmers are forced to either make less abstract code (causing potential maintenance nightmares) or tons of unnecessary code which is hard to read and probably inefficient.
# Due to the inconsistency between internal types and abstract types making eg. generic containers for all of them is impossible.
# Forbidding multiple inheritance sometimes forces programmers to do one of the biggest sins in programming: Code repetition. 

The vast majority of the high-profile attempts to use Java to create major desktop applications have failed. The reasons are straightforward. Java hype is built on the promulgation of two Big Lies. 
No. 1: Java is as fast, or faster, than other programming languages. And 
No. 2: Java is "portable" -- it is "write-once, run-everywhere" -- in other words, a Java program can be written once and then run on any kind of computer or operating system. But five years after Java's introduction, it is still slow and cumbersome, and not only has the "write-once, run-everywhere" promise not been delivered on, it's also turned out to not even be necessary. 

The creators of Java tried to make a better C++. But they ended up with a language that is ugly, hard to read and that requires an inordinate amount of typing because of a variety of pedagogical restrictions imposed by Java's creators. They ended up with a slow mess. 

Remember back in October 1996 when Corel announced that it was creating Corel Office for Java? Corel promised us a complete rewrite of WordPerfect and other office applications, which would have supposedly allowed these new Java-based applications to run on any Java-compliant machine. Office for Java was a failure. While the product is still in the Sun Java Solutions catalog and you can download the beta from a few archive sites on the Internet, the project was abandoned in August 1997. Download it for yourself and you'll find out why: It's buggy and sluggish. The program's speed, alas, was dreadful. 

Netscape had similar problems when it attempted to rewrite large parts of Netscape Navigator into Java. Indeed, the damning article What Netscape Learned from Cross-Platform Software Development," explains how Netscape's engineers were sold on the language and started writing large chunks of Navigator into Java. Netscape was committed to delivering Navigator on nearly a dozen different platforms, so Java seemed like the perfect solution. But Netscape's engineers couldn't make the language perform as Sun had advertised: Java was simply too slow. Netscape's engineers tried writing their own Java implementation, thinking that they could build a version that was faster than Sun's, but even that didn't work. "By mid-1998, Netscape was not only deemphasizing Java, it was even planning to replace existing implementations with C and C++." In other words, Netscape was taking the new code that had been written in Java and was rewriting it in C and C++. Look, they almost completely wasted 3 year (which company can afford that???), and finally got owned by Microsoft running it's C++ browser on only ONE os, and today, no more Netscape.


A 1999 study of programming efficiency goes a long way toward explaining the conflicting experiences with Java's performance. For the study, Lutz Prechelt, a senior research associate at the school of Informatics at the University of Karlsruhe, Germany, had 38 graduate students write 40 different versions of a simple text manipulation program. The programmers, who had an average experience of eight years, created 24 versions in Java, 11 in C++, and five in C. The results, published in Communications of the ACM, were revealing. The majority of programs written in C or C++ could complete the given task in between one and five minutes. Most of the Java programs, on the other hand, required between two and 30 minutes, with some taking more than an hour. In other words, the fastest Java programs, written by the most experienced Java programmers, could significantly outperform the poorly-written C programs. But the typical Java program was much slower than the typical C program. The upshot: It's better to train programmers to write efficient code than to depend on new programming languages to do it for them. 

The simple point is this: "If you weren't good enough to program in C or LISP or PL/1 or Pascal, then you aren't going to be good enough to program in Java." 

I read this from somebody:
“Cross Platform” Yeah right!
I recently made one of my more smarting computer moves by buying a Mac. However, the Java Applet that I need to upload files to a server didn’t work on it. It barely worked in Windows at times but on the Mac it simply didn’t even respond. If you didn’t know, Macs have different requirements for Java as you’ll find if you look for the scant information that exists about it on the Sun Java website. (The solution incidentally was to use Windows in Parallels and upload the files that way). Sometimes it simply doesn’t work - Even in Windows, the aforementioned applet was very temperamental. If it did finally open, files would require renaming to upload, it would freeze, crash, the browsing interface would kind of make folders and files disappear for a while before deciding to make them reappear again. Using Java is sometimes like a game of Russian roulette…

 Results 1 - 10 of about 351,000 for why i hate java. (0.18 seconds)

---

### Post by hod139 on 2008-09-13
I don't understand why people thanked this post:confused:  I found there to be little fact and the few real facts/data given was all outdated.  I am by no means a java fan boy, but I felt compelled to respond to all of your points.

> **WitchCraft said:**
> Because Java doesn't work.

It most certainly does work.  
> 
Instead of operating system version dependancy, it creates a JVM dependency.
C++ still has libstdc++ dependencies, and OS dependencies.  Plus the C++ "standard" is anything but; venders are left to implement the standard as they see fit, and "standard" code is not guaranteed to compile everywhere.
> 
Because it is closed-source.
Not any more.  
> 
Because a program is not compiled, but interpreted, running very slow.
This just isn't true any more with modern JVMs.  On numerically intensive apps, there is a small performance edge with compiled code.  But using modern [JIT]("http://en.wikipedia.org/wiki/Just-in-time_compilation") compilers can often times be faster than compiled code, since it can make runtime decisions that statically compiled code cannot.
> 
Because it has problems handling Unicode.
It's unicode support far surpasses C++'s, which has none.
> 
Because Microsoft deliberately tries to make Java-Programs not working on Windows.
How is this the fault of Java?
> 
Because there is no decent IDE that works on all platforms.
Eclipse and NetBeans are both excellent, and run on all platforms that support java.
> 
Because Java programs are only marginally less difficult to write than C++ programs.
You have no proof of that, and from the sound of the dll linking issues you are having you are not making a good case for C++.
> 
Because you can use C++ and wxWidgets, and your programs also run on all major platforms, and wxWidgets is OpenSource, 
Now you just added another dependence for C++, and wxWidgest does not build on as many platforms as java.  Also, wx has a learning curve to use.
> 
and C++ is compiled, and runs and starts fast as hell compared to Java.
You already said this, and I already disagreed.
> 
Because most Java programs I ever tried crashed at some point like opening or closing the application, or before saving a document.
Examples??  
> 
Because most Java programmers are MORONS.
This has to do with the number of people in the world that describe themselves as Java programmers and work at day jobs doing Java programming. What are there, like 15 million of them? More? So it's just a numbers thing, really. There just aren't that many good programmers overall in the world -- and most them wouldn't be caught dead doing Java.
Again, how does this show something negative against java.  If anything is shows how java is more newb friendly than C++.

> 
Because IIS does not support JSP.
Why do I care about a microsoft technology not working?  I also don't think this is a correct statement, but I'm not sure. The burden is on you to prove it, not me to disprove.

> 
Java is too Fragmented
Java has a gazillion open-source frameworks, and because most of them don't work either with your IDE or your version of the Java Virtual Machine, or because a moron wrote them, they all are worth nothing.
While true in the past, it is actively being resolved right now.

> 
Java is Too Slow
You can't use it for any larger project, because if somebody uses an older computer, it will take forever for a simple progam to load (e.g. tax or online-banking programs). That's almost never a problem when using C++.
This just isn't true.  Here is an old example ([http://www.kano.net/javabench/](http://www.kano.net/javabench/)) and Sun's jvm's have only been improving.  Also, even if C++ has a minor speed advantage, today's modern hardware makes it not even noticable.

> 
Java has bad debugging support
Java has "great and powerful" debugging (which is very necessary since most Java code sucks so much).
First it's bad, then it's great and powerful???

> 
No warnings - There’s often no warning that you’re about to click on a link or enter a site which requires Java. I think this should be mandatory in the same way that browser’s often give you security warnings about certain sites.
How would you you implement this?  When the plugin is not installed, you get a nice error message in brower.  Nothing crashes.  What's the problem?

> 
"No Memory leaks"
Actually this is completely the opposite: With a language supporting garbage collection, such as Java, you are leaking memory all the time.
Memory is constantly being allocated dynamically (often more than would be really necessary) and then "forgotten" (the language actually forces you to forget about them). That is, the coder leaves it to the garbage collection engine to clean up his memory allocation mess. Why does this matter? It matters for the exact same reason why memory leaks are bad in general: They consume more memory than necessary. What the garbage collection scheme causes is that the process will consume more memory than it really needs (in pathological cases it can consume even hundreds of times more memory than it really is using). This memory is away from other processes running in the same system. Unless the operating system has a way to tell the garbage collection engine "hey, free up some unneeded memory", it will hog everything it can and other processes may suffer from shortage of free memory. The fact is that garbage collection is a selfish algorithm. It only takes care of the program itself not running out of memory due to a memory leak. Unless it has a really close relation to the OS, it completely disregards the memory usage of other processes. 
If automatic garbage collection is so bad, why do almost all modern languages have it, and why is C++0X adding it? Your rant above mentions nothing technical about automatic garbage collections downsides, and only complains about memory consumption.  First, you can limit the amount of heap space a java program is allowed  to use.  Second, memory is dirt cheap,  4GB is $70.00USD.

Also, with C++'s exceptions (you are using exceptions right) it is almost impossible to guarantee that your program will not leak.

> 
Sharing a resource
An argument which is sometimes presented is that garbage collection makes it easier to share data between several objects: If two or more objects share the same reference to some data, since the objects don't need to take care of freeing the data, the programmer doesn't have to decide which one of the objects is responsible for this freeing. **However, if you have this kind of code in your program, you have a serious flaw in your OO design**. In good OO design one object makes one task, and the responsibilities of each object is crystal-clear. If you have an ambiguity in responsibilities, then your OO design is crappy. And: Memory is not the only resource which can be allocated and freed. What if the shared resource is, for example, a file handle? Which one of the objects should be responsible for freeing it? If the problem is in crappy OO design, the right solution is not to encourage this practise by building a compiler feature which encourages this. 
(emphasis added)
This just isn't true.  For one example, say you have a collision detection library.  Now, your main program doesn't know how many collisions there will be when it calls the collision detection library, so it can't pre-allocate (unless it just guesses a maximum number of collision and over allocates) the memory to store the results.  With reference counted objects, the library can make as many as it needs, and pass references to the main program.  Then when the main program is done, it deletes the references and, like magic, the memory is freed. 

> 
GargabeCollection efficiency
**Some garbage collection engines** make memory deallocation faster than it would be eg. in C++ with explicit deallocations. This is because they can optimize by merging several deallocations into one using complex algorithms. A program which is constantly allocating and deallocating large amounts of small chunks of memory can sometimes see a speed benefit from such GC. Of course GC advocates use this fact to boast about GC being faster than explicit memory management. However, this is a bad generalization. Yes, there are cases where it makes the program faster. However, there are many other cases where it makes the program, and worse, the entire OS much slower. 
(emphasis added)
We are not talking about any random automatic garbage collection schemes.  Your complaint is with Sun's java, do you know what they are doing?  I personaly do not, but again you need to provide the evidence to back up your claims, not me.

> 
Memory consumption
By its very design Java is a memory hog. You simply can't make a memory-efficient program which handles enormous amounts of data while still preserving good object-oriented abstraction in your program. 
You seem to be really concerned about memory consumption.  What is the point of memory if not to be consumed.  Again, you can limit the amount with the JVM, so I'm not sure what your complaint here is.  By pre-allocated more memory, a program can run faster, which is why lots of programs do that.

> 
Only references
Java coders will tell you that Java has no pointers. However, in Java everything is a pointer (they are just called references). Granted, these "pointers" are safer than C++ pointers, but they are still just "handles" to the object, and you can't get the object itself. Why does this matter? Well, you can't easily, for example, give an object to a function by value, swap the values of two objects, etc. While it's rather rare to have to do these kinds of things, when you would have to, I wish you good luck (and having much time).
A valid complain, but as you noted not a real big problem.  

> 
# Since there's no easy way of abstracting internal types away and since there's no operator overloading (which could be used to easily change an internal type to a class), programmers are forced to either make less abstract code (causing potential maintenance nightmares) or tons of unnecessary code which is hard to read and probably inefficient.
# Due to the inconsistency between internal types and abstract types making eg. generic containers for all of them is impossible.
# Forbidding multiple inheritance sometimes forces programmers to do one of the biggest sins in programming: Code repetition. 
No operator overloading and no multiple extending of classes (you can multiply include interfaces) were purposeful design decissions.  The problems associtated with them were deemed to outway the benefit by the language designers.  These merits have been discussed before, so i'm not going to rehash these arguements here.

> 
The vast majority of the high-profile attempts to use Java to create major desktop applications have failed. The reasons are straightforward. Java hype is built on the promulgation of two Big Lies. 
No. 1: Java is as fast, or faster, than other programming languages. And 
No. 2: Java is "portable" -- it is "write-once, run-everywhere" -- in other words, a Java program can be written once and then run on any kind of computer or operating system. But five years after Java's introduction, it is still slow and cumbersome, and not only has the "write-once, run-everywhere" promise not been delivered on, it's also turned out to not even be necessary. 
Again with your rants, not proof.  I happen to think there are a lot of neat applications out there.  Here is a page with some fun demos: [https://jogl-demos.dev.java.net/](https://jogl-demos.dev.java.net/)
Note, they look pretty portable to me, and run pretty fast, so I don't know what your complaint is.  As for a bigger applications for examples, how about OpenOffice and Eclipse?

> 
The creators of Java tried to make a better C++. But they ended up with a language that is ugly, hard to read and that requires an inordinate amount of typing because of a variety of pedagogical restrictions imposed by Java's creators. They ended up with a slow mess. 
This is your opinion, not fact.  Hard to argue no facts.

> 
Remember back in October 1996 when Corel announced that it was creating Corel Office for Java? Corel promised us a complete rewrite of WordPerfect and other office applications, which would have supposedly allowed these new Java-based applications to run on any Java-compliant machine. Office for Java was a failure. While the product is still in the Sun Java Solutions catalog and you can download the beta from a few archive sites on the Internet, the project was abandoned in August 1997. Download it for yourself and you'll find out why: It's buggy and sluggish. The program's speed, alas, was dreadful. 
This is not 1996, but 2008.  Java has come a long way.  Have you tried OpenOffice,  I hear it is pretty good office suite.

> 
Netscape had similar problems <snip>
Again, way to old of an example.

> 
A 1999 study <snip>
9 years in CS is an eternity.  Again, this is way to old for a fair comparison.

> 
I read this from somebody:
“Cross Platform” Yeah right!
I recently made one of my more smarting computer moves by buying a Mac. However, the Java Applet that I need to upload files to a server didn’t work on it. It barely worked in Windows at times but on the Mac it simply didn’t even respond. If you didn’t know, Macs have different requirements for Java as you’ll find if you look for the scant information that exists about it on the Sun Java website. (The solution incidentally was to use Windows in Parallels and upload the files that way). Sometimes it simply doesn’t work - Even in Windows, the aforementioned applet was very temperamental. If it did finally open, files would require renaming to upload, it would freeze, crash, the browsing interface would kind of make folders and files disappear for a while before deciding to make them reappear again. Using Java is sometimes like a game of Russian roulette…
You know, it is quite possible that the applet was poorly written.  Also, nobody liked applets and Sun realized this.  You don't make applets any more, now you use [java webstart,]("http://java.sun.com/javase/technologies/desktop/javawebstart/index.jsp") which is a really cool technology.

---

### Post by Sockerdrickan on 2008-09-13
**^fail** :(

OpenAL Soft rocks [http://kcat.strangesoft.net/openal.html](http://kcat.strangesoft.net/openal.html)

---

