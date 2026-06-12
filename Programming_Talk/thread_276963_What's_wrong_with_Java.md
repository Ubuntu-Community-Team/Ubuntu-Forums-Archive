---
title: "What's wrong with Java?"
date: 2006-10-13
forum: Programming Talk
---

### Post by Nonno Bassotto on 2006-10-13
First, let me make clear I'm not a programmer. I've an idea of the principles, but I've got no experience in programming, and I'd like to start.

One language I happen to like is Java. It seems easier and more elegant than C++ and it seems more complete and object-oriented than Python. Still, for some reason, is very rare to find a project made in Java. Moreover most programs (I think in order to be portable) don't use native widgets and so look not so good on whatever OS.

So, the question is: why isn't people adopting Java? Are there libraries to make Java programs for Gnome, for example? Is it good to start with Java (maybe together with Python)?

---

### Post by meng on 2006-10-13
I'm also a novice programmer, and having tried to make inroads into Java several times, I have recently come to Python and I have been very impressed. I think it's simpler to work with, but I would argue that it is just as object-oriented as Java is. It is just as cross-platform as Java, and also has good cross-platform GUI development tools.

The only drawback I can see is that the JRE is more prevalent on Windows machines than is Python. But when you take into account poor compatibility between different Java versions (1.3, 1.4, 1.5) this is not much of an advantage/disadvantage.

---

### Post by ciscosurfer on 2006-10-13
Java is made to be platform-independent, and thusly creates a bottleneck of sorts that on the one hand allows it to be run in/on various architectures but because of this fact, makes it very slow and processor intensive.  So, it allows for ubiquity but suffers speed due to this fact.  I enjoy programming Java from time to time, but I personally don't find it that useful.  I know there are those out there who disagree with me.  Now, despite my own dislike for Java, it happens [to be the most popular]("http://www.tiobe.com/tpci.htm") (according to TIOBE Software and other mainstream critics and proponents) -- I believe its popularity is due primarily to the fact that it takes its nods from [Objective-C]("http://en.wikipedia.org/wiki/Objective-C"),  [C++]("http://en.wikipedia.org/wiki/C%2B%2B"), [Smalltalk]("http://en.wikipedia.org/wiki/Smalltalk"), [Eiffel]("http://en.wikipedia.org/wiki/Eiffel_programming_language"), [C#]("http://en.wikipedia.org/wiki/C_sharp"), to name a few.  So people that are already used to these syntaxes, find Java to be a natural switch.  That, and it's easy to learn.  I believe Python is easier, but that's just my take.

---

### Post by meng on 2006-10-13
And there are many principles of programming that apply across different languages, such that the differences in syntax are not the major component of learning how to program. What I'm saying is, you can start in Python and after you become proficient, learn about Java.

I would advise against learning more than one language simultaneously though!

---

### Post by bieber on 2006-10-14
Y'all forget the most important reason you don't see many Java programs for GNU/Linux.  Sun's Java is proprietary software, and if you develop applications using it, you're effectively coercing others to give up their freedom.

---

### Post by Nonno Bassotto on 2006-10-14
> **ciscosurfer said:**
> Java is made to be platform-independent, and thusly creates a bottleneck of sorts that on the one hand allows it to be run in/on various architectures but because of this fact, makes it very slow and processor intensive.  So, it allows for ubiquity but suffers speed due to this fact.

Is it slower than Python?

---

### Post by Nonno Bassotto on 2006-10-14
> **bieber said:**
> Y'all forget the most important reason you don't see many Java programs for GNU/Linux.  Sun's Java is proprietary software, and if you develop applications using it, you're effectively coercing others to give up their freedom.

Yeah, this is actually a problem. But for simple programs one could use free implementations of Java, even if they are not very up to date.

---

### Post by Nonno Bassotto on 2006-10-14
> **meng said:**
> I have recently come to Python and I have been very impressed. I think it's simpler to work with, but I would argue that it is just as object-oriented as Java is.

Well, maybe it is. But it seems that you can write code in a functional way if you want. Actually some tutorials I have teach you this first, and only later teach you how to use classes.

---

### Post by nereid on 2006-10-14
> **Nonno Bassotto said:**
> Is it slower than Python?

This is hard to say. But Java is not very fast compared to a native language like C++. Java is very verbose and has, IMHO, very much overhead. If you want to learn how to program try a scripting language like Python or Ruby. Ruby is completly object oriented, much more than Python, and is also very easy to learn.

---

### Post by 3rdalbum on 2006-10-15
Problems I've observed with Java:

1. The JREs are always badly written, causing worse cross-platform issues than I've ever had with Python. On some platforms, running a Java program is likely to bring the machine down.

2. It's unneccessarily difficult to write in. Python is much easier, not merely because of the dynamic variables, but mostly because there are large-grained functions (i.e. opening, writing and closing a file in Python is 3 lines; in Java it's 8 or 9 lines unless you use a RandomAccessFile, in which case you wouldn't be able to cleanly overwrite an existing file without reading it first.)

---

### Post by Lster on 2006-10-15
I used to program in Java, and found it much easier than C/ C++, but Java is just too slow (mostly down to memory usage I think) and the JRE is >100MB.

---

### Post by rekahsoft on 2006-10-15
> **ciscosurfer said:**
> Java is made to be platform-independent, and thusly creates a bottleneck of sorts that on the one hand allows it to be run in/on various architectures but because of this fact, makes it very slow and processor intensive.  So, it allows for ubiquity but suffers speed due to this fact.  I enjoy programming Java from time to time, but I personally don't find it that useful.  I know there are those out there who disagree with me.  Now, despite my own dislike for Java, it happens [to be the most popular]("http://www.tiobe.com/tpci.htm") (according to TIOBE Software and other mainstream critics and proponents) -- I believe its popularity is due primarily to the fact that it takes its nods from [Objective-C]("http://en.wikipedia.org/wiki/Objective-C"),  [C++]("http://en.wikipedia.org/wiki/C%2B%2B"), [Smalltalk]("http://en.wikipedia.org/wiki/Smalltalk"), [Eiffel]("http://en.wikipedia.org/wiki/Eiffel_programming_language"), [C#]("http://en.wikipedia.org/wiki/C_sharp"), to name a few.  So people that are already used to these syntaxes, find Java to be a natural switch.  That, and it's easy to learn.  I believe Python is easier, but that's just my take.

it takes its nods from C#??? wt hell is that...Java was created way before C#...C# is MS's rip off of Java

---

### Post by ciscosurfer on 2006-10-15
What I meant to say, if I was not clear, was the C# takes its nods from C++, which it does.

---

### Post by Hendrin on 2006-10-15
There is nothing wrong per say with Java. It's a great language to teach if you have people going into C++ afterwards as it teaches good design(or at least it did when I used it a few years ago).   I would recommend Python before Java though...

The Linux JRE is 15.75 MB, and depending on the program can take anywhere from 20MB and up for its memory usage.  GCJ memory usage is alot worse, but given its nature should get better as time goes by.  It can also be very quick being JIT'ed, but likely won't come close C/C++ in most normal circumstances.

Yes, Sun's Java is proprietary, but Sun seems interested in open sourcing it.  Lets wait and see what the license they release it under is like and how long it takes.  Honestly, I would rather program in C# under Mono considering the licensing of most of that is GPL or MIT.  Unfortunately there likely to run into a number of patent violations the more WinForms they implement.

Lastly, I highly recommend Python.  Learn the concepts.  Learn the patterns and algorithms.  Make some small programs.  Once you know the concepts, its much easier to move into another language, whatever it might be.

---

### Post by misha680 on 2006-10-16
First of all, I have to say that I don't know a bit of Python, but I am pretty proficient in Java, C, C++, and a few others (x86 assembly, but I haven't done that in a _long_ time, PROLOG, etc). My take on Java:

Pros:
* I love that you already have implementations of all these data structures out of the box that you don't see in other languages, like trees and sets. I really think that for certain applications, having these classes will really simplify your coding, and I strongly believe that if you can make your code simpler and more abstract by using such classes you will have better, bug free code.
* Instant cross-platform compatibility.

Cons:
* Speed. Java is slow if you are trying to do something fast. But if speed is not so critical, I think it is a great language.

Anyhow, just my two cents.

Misha

---

### Post by slavik on 2006-10-16
> **misha680 said:**
> First of all, I have to say that I don't know a bit of Python, but I am pretty proficient in Java, C, C++, and a few others (x86 assembly, but I haven't done that in a _long_ time, PROLOG, etc). My take on Java:

Pros:
* I love that you already have implementations of all these data structures out of the box that you don't see in other languages, like trees and sets. I really think that for certain applications, having these classes will really simplify your coding, and I strongly believe that if you can make your code simpler and more abstract by using such classes you will have better, bug free code.
* Instant cross-platform compatibility.

Cons:
* Speed. Java is slow if you are trying to do something fast. But if speed is not so critical, I think it is a great language.

Anyhow, just my two cents.

Misha
For me a pro is that Java is the only language allowed at the ACM competitios (which I have my own gripe about not being able to use perl) which regular expressions as part of the standard library (C, C++, Ada don't).

A con is that OpenGL in Java is not the same as OpenGL in C/C++ (which I also need for speed).

The JVM is actually written in C++ ... as for speed, any language can be as fast as any other language (you can translate any interpreted language into C/C++ because the interpreters are written in usually those 2 languages) ... you can't get much faster than C/C++ :P

---

### Post by FyreBrand on 2006-10-16
I won't go into the slow thing, everyone has covered it.  Here are a couple other pro/cons from my point of view.

pros:
-at it's simplest it's a fairly easy language to get moving on.  You can write little programs within a short period of time
- you don't have to worry about de-referencing, pointers or memory management
- it's kind of cross platform (at least in theory it is)
- like any other language it's good for what it's for (kind of, although I think there is better alternatives in each case)
- generally it's a little harder to shoot yourself in the foot with this one, although it's very possible and can be very difficult to find out why.

cons:
- it has horrible file management. It's just a bear to do file i/o compared to some other languages.
- it's biggest strengths have become some of it's biggest pains.  Class libraries, inheritance, and the like.  In some cases just to perform a little gui magic or image manipulation you have a string of objects and their methods a mile long chained to each other.
- it's not an elegant language at all.
- Sun controls the main API.  I think it's a fricken mess and well, I will  just leave it at that.

Python might not be as mature, but it's development direction seems much more positive.  If you look at the way it's been changing there have been some real positive changes.  I think it would be hard for Sun to say the same thing about Java.

Elegance is in the eye of the coder, but I would say Java is clunky, bulky and sluggish. I think C++ is elegant, but that's just my opinion.  And I think "elegant" is more in how someone writes their code rather than an inherent language property.

A good example of what is good and bad about Java can be demonstrated with the Eclipse IDE.  It's a fantastic tool that is written in Java.  It's has a lot of incredible features and it's powerful and extensible.  You can custom taylor eclipse to code whatever you really want it to.  It sports a fairly nice user interface.  It's also a slug to run.  Even with minimal features there are times when it just has to let the JVM sit and think through what it's doing.  Compared to other IDE's like DevC++, Anjuta, KDevelop, and Bluefish it's way too slow.

Well that's my take on it.

---

### Post by nereid on 2006-10-16
As a novice without any experience I wouldn't recommend Java. Javas syntax is ugly as hell and it bears so much overhead that you need to write so many things before you get a working program.

Start learning programming with a scripting language. After you've got the basics in one language you can switch to any other language without a problem (functional languages are another thing).

---

### Post by Nonno Bassotto on 2006-10-16
> **nereid said:**
> As a novice without any experience I wouldn't recommend Java. Javas syntax is ugly as hell and it bears so much overhead that you need to write so many things before you get a working program.


Well, as I said I'm a novice, but I know a bit how things work. Maybe I was not clear in my first post, but the reason I posted here is the fact that I like Java sintax, but I didn't want to start some project in Java before understanding why almost nobody uses it.

---

### Post by Nonno Bassotto on 2006-10-16
> **3rdalbum said:**
> 1. The JREs are always badly written, causing worse cross-platform issues than I've ever had with Python. On some platforms, running a Java program is likely to bring the machine down.


Is this true???!??

---

### Post by Nonno Bassotto on 2006-10-16
> **FyreBrand said:**
> I won't go into the slow thing, everyone has covered it.

Yes, but almost everyone keeps suggesting to learn Python, which is interpreted as well. So, doens't Python have speed issues?

---

### Post by Nonno Bassotto on 2006-10-16
In these days I had a look at Python. There are some things I don't like very much, like the fact that you can avoid classes. But one thing I don't really understand (maybe I just understood it bad). With Python I can declare a class, say
```

class Point:
   pass

```
and then instance an object and start adding variables to this object, even if I didn't declare that the class members possess these variables
```

MyPoint = Point()
MyPoint.x = 5
MyPoint.y = 7

```
So if I create a second instance of the class, it can happen that this has a completely different set of variables
```

NewPoint = Point()
NewPoint.name = "Goofy"
NewPoint.dict = {"apple": "banana", "pear": "umbrella"}

```
So it seems to me that this construction will lead to bugs in a few lines, since I will try to apply functions and methods with object variables as argument, but I'm not sure that the object will posses the right set of variables. ](*,) 

I think I'm a bit confused... :-?

---

### Post by Ragazzo on 2006-10-16
> **Nonno Bassotto said:**
> Is this true???!??

I had written many Java applications on Windows and when I tried using them on Ubuntu, the only reason why some of them didn't work was the lack of GCJ's support for Swing (GUI library). That issue was solved by installing Sun's Java. What comes to speed, Java (version 5) is usually definitely faster than Python (just-in-time compilation for example) but Java applications have a long start-up time which gives a poor impression to some users.

---

### Post by nereid on 2006-10-16
> **Nonno Bassotto said:**
> Is this true???!??

Nope, not in my experience. If you know the basics and like the language than, why asking questions? Hop on the boat and start whacking away ;)

---

### Post by Lster on 2006-10-16
@Hendrin... Sorry, its the JDK thats >100MB](*,).

---

### Post by _asc_ on 2006-10-16
Hello!

I think the reason why Java isn't used in a lot in open source projects is that Java is not free, which is about to change because Sun is going to opensource Java:
[http://www.zdnetasia.com/news/software/0,39044164,39390355,00.htm](http://www.zdnetasia.com/news/software/0,39044164,39390355,00.htm)

Another reason might be that Sun did not put a lot of effort in pushing Java desktop development. Swing applications are slow and generally do not look very good. This seems to change too. With the new JDK 6, which will be released by the end of this year, Swing performance will be increase significantly and Swing is using the native widget rasterizer to make Swing apps look native:
[http://weblogs.java.net/blog/chet/archive/2006/02/these_are_some.html](http://weblogs.java.net/blog/chet/archive/2006/02/these_are_some.html)

Regarding Java performance: In the early days Java was really slow and as I mentioned above, the Swing drawing routines were slow. But with the Hot Spot technology there has been a lot of improvement. Depending on the application Java can outperform C/C++:

[http://blogs.sun.com/jag/entry/java_urban_performance_legends](http://blogs.sun.com/jag/entry/java_urban_performance_legends)
[http://www-128.ibm.com/developerworks/java/library/j-jtp09275.html](http://www-128.ibm.com/developerworks/java/library/j-jtp09275.html)
[http://www.idiom.com/~zilla/Computer/javaCbenchmark.html](http://www.idiom.com/~zilla/Computer/javaCbenchmark.html)

Some Java resources you might be interested in:
Java podcast: [http://javaposse.com/](http://javaposse.com/)
Java blogs: [http://java.sun.com/developer/blogs/](http://java.sun.com/developer/blogs/)
Nice looking Swing app: [https://aerith.dev.java.net/](https://aerith.dev.java.net/) 

If you are looking for a good Java book, I'd suggest you take a look at "Head First Java".

---

### Post by Nonno Bassotto on 2006-10-16
Thank you all for your replies. I think I'm going to learn a bit of Python, since there are a lot of small projects where I could learn something and maybe help a bit. When I feel a bit more comfortable with programming I will consider learning Java more seriously, since I like the language.

---

### Post by FyreBrand on 2006-10-16
> **_asc_ said:**
> Hello!

I think the reason why Java isn't used in a lot in open source projects is that Java is not free, which is about to change because Sun is going to opensource Java:
[http://www.zdnetasia.com/news/software/0,39044164,39390355,00.htm](http://www.zdnetasia.com/news/software/0,39044164,39390355,00.htm)

Another reason might be that Sun did not put a lot of effort in pushing Java desktop development. Swing applications are slow and generally do not look very good. This seems to change too. With the new JDK 6, which will be released by the end of this year, Swing performance will be increase significantly and Swing is using the native widget rasterizer to make Swing apps look native:
[http://weblogs.java.net/blog/chet/archive/2006/02/these_are_some.html](http://weblogs.java.net/blog/chet/archive/2006/02/these_are_some.html)

Regarding Java performance: In the early days Java was really slow and as I mentioned above, the Swing drawing routines were slow. But with the Hot Spot technology there has been a lot of improvement. Depending on the application Java can outperform C/C++:

[http://blogs.sun.com/jag/entry/java_urban_performance_legends](http://blogs.sun.com/jag/entry/java_urban_performance_legends)
[http://www-128.ibm.com/developerworks/java/library/j-jtp09275.html](http://www-128.ibm.com/developerworks/java/library/j-jtp09275.html)
[http://www.idiom.com/~zilla/Computer/javaCbenchmark.html](http://www.idiom.com/~zilla/Computer/javaCbenchmark.html)

Some Java resources you might be interested in:
Java podcast: [http://javaposse.com/](http://javaposse.com/)
Java blogs: [http://java.sun.com/developer/blogs/](http://java.sun.com/developer/blogs/)
Nice looking Swing app: [https://aerith.dev.java.net/](https://aerith.dev.java.net/) 

If you are looking for a good Java book, I'd suggest you take a look at "Head First Java".

I think Sun might be a little late on this step.  Python already has a momentum in the right direction. The major thing Java has going for it with Sun open sourcing it is that it has name recognition and many people are familiar with it.  With the exception of a few die-hard Java fans I know most people would choose another platform if they have that option.

And as far as Java outperforming a C or C++ application I would find that very hard to believe unless it was compiled into an executable. But then it wouldn't really be the standard Java program running on the JRE then would it.  If you have a couple examples of couple similar applications where one is written in C and the other is written in Java and the Java app outperforms the C/C++ app please post it.  I would be really interested in reading about that.

Nonno ~ Just because a language is interpreted doesn't necessarily mean it's really slow.  PHP is also an interpreted language, but I don't consider it really slow.  I don't think it's always the fasted alternative, but I don't think it's slow.  Java is often slow for many reasons some of which include the fact that the JRE is a resource hog and JRE's perform differently on different platforms.  I think there is a lot of inconsistancy with Java.

Nereid's advice on starting with a scripting language is pretty good.  Overall though it doesn't matter.  Just start programming and eventually you will find the languages you like to spend time in.

---

### Post by _asc_ on 2006-10-17
> 
I think Sun might be a little late on this step. Python already has a momentum in the right direction. The major thing Java has going for it with Sun open sourcing it is that it has name recognition and many people are familiar with it. With the exception of a few die-hard Java fans I know most people would choose another platform if they have that option.

Yes, Sun is a little late on this step. But better late than never ;).
I have just started to learn Ruby, so I do not have enough experience to compare Java to any of the scripting languages. Nevertheless, I think that Java is a good programming language. And, in the end the choice of a particular programming language depends on the problem you want to solve.

> 
And as far as Java outperforming a C or C++ application I would find that very hard to believe unless it was compiled into an executable. But then it wouldn't really be the standard Java program running on the JRE then would it. If you have a couple examples of couple similar applications where one is written in C and the other is written in Java and the Java app outperforms the C/C++ app please post it. I would be really interested in reading about that.

See the links, I posted above.
Here are some additional benchmarks:
 [http://blogs.sun.com/dagastine/entry/sun_java_is_faster_than](http://blogs.sun.com/dagastine/entry/sun_java_is_faster_than),  (the source code: [http://math.nist.gov/scimark2/]("here"))
  [http://blog.planetxml.de/archives/27-Primzahlen-berechnen-in-C,-C-und-JAVA.html]() (in German)
I know that you have to take benchmarks with a grain of salt. Nevertheless, I think they show that the statement "Java is slow" is an unjustified generalization. There has been a lot of improvement in Java performance and JVM performance will continue to improve (see for example "escape analysis"). And even if Java performance isn't as good as C/C++ performance in real life applications, I think with todays hardware it is still good enough for most applications.

---

### Post by siman on 2006-10-17
> **Nonno Bassotto said:**
> In these days I had a look at Python. There are some things I don't like very much, like the fact that you can avoid classes. But one thing I don't really understand (maybe I just understood it bad). With Python I can declare a class, say
```

class Point:
   pass

```
and then instance an object and start adding variables to this object, even if I didn't declare that the class members possess these variables


...yes, you can do that. But usally you would declare the class members when declaring the class, like this:

```

class Point:
 def __init__(self,x=0,y=0):
   self.x = x
   self.y = y

```

Python doesn't force you to do this, and you can still add other member vars later on - but as you noticed, it's usually not good for the readability and maintainability of the ocde :-)

---

### Post by Tomosaur on 2006-10-17
In my experience:
Java is great for getting programs coded and running in a pretty short amount of time, but don't expect speed.

C/C++ are great for getting things running at high speeds, but don't expect development time to be as short as it would be in Java.

Python is just great all round imo. It's very clean, and I like the 'everything is an object' methodology. It just makes things so much nicer.

I don't care much for speed - modern computers can handle most applications quick enough that the user doesn't notice much, if any difference. It's only when it's very complex situations where speed starts to be an issue. If you're not writing a physics suite or a game or something, just pick whatever language you feel comfortable with, since speed is unlikely to be an issue.

However, Java apps ARE fugly at the moment.

---

### Post by james.gornall on 2006-10-17
I'm being taught Java as my first programming language at university.

So far I found it nice and easy to get in to, and like a few have mentioned its meant to be good to lead into C++ which is what I'll be doing.

---

### Post by gmallard on 2006-10-18
Nothing wrong with Java, it is my bread and butter.

I personally do not like Python, so - recommend you take a look at another (interpreted) pure OO language: Ruby.

Guy

---

### Post by jinx4848 on 2006-10-27
I don't mean to start a Python vs. Ruby war in a Java related thread, but 

> 
I personally do not like Python, so - recommend you take a look at another (interpreted) pure OO language: Ruby.


I agree. I find Ruby to be much more of a "complete" language from a design point of view. There are a lot of design "flaws"/contradictions in python, like the need to define "self" (the method's owner object reference, equivalent to 'this' in Java) in classes despite the highly strict paradigm of "clean code", the superfluous use of the '_' character, etc..

But this isn't the right place for such a discussion.. I do actually have some things to say about Java:

Java is a great language, and despite the misconception, it's an extremely popular one too. Limewire, Eclipse, OpenOffice, are just a few of the big name examples.. and when it comes to web development, there are plenty more... and can you say EMBEDDED SYSTEMS? about every consumer level cell phone (non PDA) is Java enabled.. that's A LOT of Java, considering how important cell phones are these days.

The real deal is that Java is a pretty strict language when it comes to syntax, which some people just don't dig. For extremely large projects (enterprise level) though, this is a must, or your project will likely become a mess and half. The strictness of Java is why large development teams like it so much.

Speed is an issue though. For small linux applications that prioritize on efficiency, speed and reliability, Java isn't very ideal. 

Programming is all about using languages as a tool, not a solution. If a language doesn't suit a task, don't use it. Java has it's place.

Just for clarification on the Python vs. Java speed thing... well, these numbers aren't exactly 100% accurate, but [Java kills Python in speed]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=java&lang2=python").

PS. I'm sure someone out there disagrees with something I said.. that's how these things work, so don't take it too hard 8)

---

### Post by jsmtech on 2006-10-29
I am having trouble installing java. I do not use it on this system that often but, my bother uses pogo.com and runescape.com . Is there any simple way to install it without programming?

---

### Post by nereid on 2006-10-30
Indeed there is

```

sudo apt-get install sun-java5-bin
sudo update-java-alternatives -s java-1.5.0-sun

```

should do the trick.

---

### Post by jsmtech on 2006-10-31
I am sorry I do not know what that code is for I am a newbie.

Can you please explain what it is and how to use it ?

---

### Post by nereid on 2006-10-31
Open a terminal (click on the Desktop(?) menu entry [the one on the top left side] -> System or something like it and then start the terminal application).

Then you'll get a black terminal with white fonts. Enter the first line and proceed by pressing enter. Sudo will ask for your password. You won't see any stars or something like that but your password will be there. After suppling your password proceed again with pressing enter. You will see something like "apt-get getting sun-java5-bin...blah blah". This will take a little bit but when it is finished you've got the newest Java JRE on your system.

Now you need to tell Ubuntu to use the new JRE. Copy the second line and proceed with enter (maybe sudo will ask again for your password). Thats it. If everything went all right enter this line

```
java -version
```

into the terminal and proceed again with enter. This should print something like this

```

java version "1.5.0"
Java(TM) 2 blah blah

```

If this is the case you're finished.

---

### Post by jsmtech on 2006-10-31
I recieved .....

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-bin
abc@Family:~$


What next?

---

### Post by IYY on 2006-10-31
> 
One language I happen to like is Java. It seems easier and more elegant than C++ and it seems more complete and object-oriented than Python. Still, for some reason, is very rare to find a project made in Java. Moreover most programs (I think in order to be portable) don't use native widgets and so look not so good on whatever OS.

So, the question is: why isn't people adopting Java? Are there libraries to make Java programs for Gnome, for example? Is it good to start with Java (maybe together with Python)?

The main reason is that it's very slow, and adds a large dependency to your programs (not everyone has Java installed). Mainly the slow thing.

However, Java *is* a good language to learn, especially as your first language, because it is elegant and will introduce you to object oriented design nicely.

---

### Post by brentoboy on 2006-10-31
In my experience, the projects that I have been involved in that could have been done in Java but werent, the pivital decision was made as a way of protecting the source code.  Java is a semi interpteted language, and as such is fairly easy to de-compile.

Also, in my experience, the projects that I have been involved in (or inherited) that did use Java were almost always in house software for large companies.

C# is the new java.  It seems to me to be more like Java than it is is like C++.  C# is microsoft's slant on java, and as such, it is relacing java for a lot of those big businesses that bank thier money on MS technology -- becuase C# is easier to write a "corporate wide" application than C++, but for some reason it is more desireable than java -- in my opinion this is due to the Visual Studio design IDE, it is really productive (once you know what you are doing).

Its a shame, but I think java is dieing.  The "make it open source" is an attempt to breath new life into it like star office -> Open office.

"Open Java" has a better chance of competing with MS because it will no longer get shunned by Linux die-hards.

--all my opinon, who am I to make a claim here?--

---

### Post by nereid on 2006-11-01
> **jsmtech said:**
> I recieved .....

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-bin
abc@Family:~$


What next?

Do you have the universe or multiverse repositories enabled? I'm sorry I don't know at the moment in which repo the sun package resides. Search the forum on how to add other repositories to your Ubuntu installation and then try my little guide again.

---

### Post by jsmtech on 2006-11-01
I went through the steps to add repositories and then followed your steps again and recieved the same thing. I am also not sure which repo the java file is located. Let me know if you find out.

---

### Post by jsmtech on 2006-11-01
found the repo on this site ! 

[http://www.javalobby.org/java/forums/t72809.html](http://www.javalobby.org/java/forums/t72809.html)

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse 

here is what i did and recieved from terminal ....

abc@Family:~$ sudo apt-get update
Password:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Fetched 6B in 1s (6B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
abc@Family:~$ sudo apt-get install sun-java5-jdk
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
abc@Family:~$

//////  When going through synaptic i was able to find blackdown java 1.4

---

### Post by slavik on 2006-11-02
I think Java is terrible as a first language, because it does not stress being efficient.

Memory is NOT cheap. It is cheapER (than the programmer) than it used to be 30 years ago, but it is not free.

One of my professors actually told me that she spoke with someone who does programming for a big company (which uses C++ mostly) and he told her that many Java programmers are terrible at writing optimised code.

---

### Post by McLoud on 2006-11-02
> **slavik said:**
> 
Memory is NOT cheap. It is cheapER (than the programmer) than it used to be 30 years ago, but it is not free.

If a java program is using too much memory, there is something wrong. Is not that because you can create a ton of classes doesn't mean you need to keep them all in memory at once.

> **slavik said:**
> 
One of my professors actually told me that she spoke with someone who does programming for a big company (which uses C++ mostly) and he told her that many Java programmers are terrible at writing optimised code.

That has nothing to do with the language. You can write bad code in both, the difference is that in java it will be very slow, and in C/C++ it will be slow, mess with your SO, blow your comp, wipe your harddrive... . ](*,)

---

### Post by Circus-Killer on 2006-11-02
sorry if this has already been suggested, but here it is if it hasnt.

follow [this]("https://help.ubuntu.com/community/Java") guide to install sun's java version. take note that the JRE and JDK are seperate.

i've installed java a few times using the method described in the page i just mentioned. hope it helps you as it helped me.

---

### Post by firebadger on 2006-11-03
A couple of quick points...

Speed:  When using a JRE that uses a JIT (dynamic) compiler then optimisations can be carried out at run time.  This can in practice lead to code that runs faster than a native equivalent.  I believe someone has already posted some benchmarks.  This works best on server or non-GUI apps and I think it's Swing that is giving Java as a whole its bad rep in terms of speed.

Dynamic Typing:  Not always a good thing, in fact I don't like it much, it just seems to hide problems that could be identified at compile time with a more strongly typed language.

---

### Post by McLoud on 2006-11-04
> **firebadger said:**
> A couple of quick points...
Speed:  When using a JRE that uses a JIT (dynamic) compiler then optimisations can be carried out at run time.  This can in practice lead to code that runs faster than a native equivalent.  I believe someone has already posted some benchmarks.  This works best on server or non-GUI apps and I think it's Swing that is giving Java as a whole its bad rep in terms of speed.

That possible, but I'm yet to see an application with that bad speed with source available so one can point the real problem with proper benchmarks. Netbeans 5 with JDK 1.5 is very snappy here (comparable to a gtk application and even to a qt application). Even if swing isn't the fastest toolkit around, is not like one is going to create a thousand widgets/sec and start playing with them all at once. ](*,) 

My bet is applications not using the main thread properly (eg: vb programmers wannabe doing processing on button clicks and complaining that the interface stop redrawing or redraw slow). My only real complaing about swing is that it only updates widgets while resizing when you release the mouse button. Yet GTK applications do the same to an extent.:-?  Anyone have a good example of a slow java application that is opensource so we can look at it?

---

### Post by McLoud on 2006-11-04
> **brentoboy said:**
> In my experience, the projects that I have been involved in that could have been done in Java but werent, the pivital decision was made as a way of protecting the source code.  Java is a semi interpteted language, and as such is fairly easy to de-compile.

That used to be a problem. Then crackers got better and manage to beat any application they can put their hands into so people stopped caring.

> **brentoboy said:**
> Also, in my experience, the projects that I have been involved in (or inherited) that did use Java were almost always in house software for large companies.

Large and medium companies which need to keep an application running 24/7 cares a lot about stability and backwards compatibility. Java applications since 1.1 runs all way up to java 1.6 without changes. I for one create applications on windows, test on linux and the first deployment on a AIX running IBM J9. Not a single line of code has changed for that.

> **brentoboy said:**
> C# is the new java.  It seems to me to be more like Java than it is is like C++.  C# is microsoft's slant on java, and as such, it is relacing java for a lot of those big businesses that bank thier money on MS technology -- becuase C# is easier to write a "corporate wide" application than C++, but for some reason it is more desireable than java -- in my opinion this is due to the Visual Studio design IDE, it is really productive (once you know what you are doing).

Yet if your IDE has any showstopper, where are you going to hide into? JDeveloper is one IDE that matches Visual Studio, yet you have Netbeans (slowly getting into the same line), Eclipse, JBuilder...

> **brentoboy said:**
> Its a shame, but I think java is dieing.  The "make it open source" is an attempt to breath new life into it like star office -> Open office.

Java strong side has always being embedded development. Palm and now cellphones means a lot of deployments all over the place. It has a lot of applications for web servers too. I think they want to make opensource so linux fanboys stop complaining. Most of them think they will be able to change the jvm at will and make their own java. That's just wrong, the jvm opensource doesn't mean the spec is free to change, if you want to be java, you must follow a spec. That's what make java runs across all JVM's the same way (there is issues with some, nothing is perfect, but they got close enough).

> **brentoboy said:**
> "Open Java" has a better chance of competing with MS because it will no longer get shunned by Linux die-hards.

I agree, and the weakest side of java is desktop environment. Yet, have anyone seen the matisse demos? Thats very impressive and expect a lot more in incoming netbeans versions. What the IDE allows to do speaks lots of what kind of applications one developer can make and how easy/fast. At least for the starters.

> **brentoboy said:**
> --all my opinon, who am I to make a claim here?--

Welcome aboard to the speculative side 8)

---

### Post by slavik on 2006-11-04
> **McLoud said:**
> If a java program is using too much memory, there is something wrong. Is not that because you can create a ton of classes doesn't mean you need to keep them all in memory at once.



That has nothing to do with the language. You can write bad code in both, the difference is that in java it will be very slow, and in C/C++ it will be slow, mess with your SO, blow your comp, wipe your harddrive... . ](*,)
Point being that habits stick, and if it is a bad habit of not understanding (or being ignorant about) memory management then it doesn't help anyone.

---

### Post by McLoud on 2006-11-05
Btw, if some of you could use of some swing performance, found this: [http://weblogs.java.net/blog/alexfromsun/archive/2006/04/swing_team_reve_1.html](http://weblogs.java.net/blog/alexfromsun/archive/2006/04/swing_team_reve_1.html)

Note the swing.runtwiceasfast=true which I tested and actually works :confused:

---

### Post by Darling on 2006-12-03
Some have mentioned it already, the main reason that java is not so much used in the linux community is that it was non free. 
Sun has made some big efforts, but we'll have to see if that'll change the acceptance. But this doesn't say anything about the java language.
From reading this thread, I have the impression that most of the opinions are based on second/third/fourth hand impressions from ignorant fanatics (whoohooo ;-) or from people who just looked briefly at java when version 1.0 was out. I see a lot of gratuitous thoughts, but hardly any real evidence. 

Since then a lot has changed, and I can assure you, speed is not an issue at all. Modern java setups perform near C++ speed for most common tasks. In some tasks, java has shown to be faster than C. I know this is very difficult to believe for some of you, but it becomes clear if you start to understand that a runtime optimizer (hotspot) is obviously able to make better choices than a static optimizer (C, C++). 
[http://www.idiom.com/~zilla/Computer/javaCbenchmark.html](http://www.idiom.com/~zilla/Computer/javaCbenchmark.html)
For a good collection of all articles related to this, check out [http://www.javaperformancetuning.com](http://www.javaperformancetuning.com)

I really don't understand people mentioning (java is slow) and at the same time suggesting to use Python. Java wins in execution speed with its hands in its pockets. Same for Ruby.
But then we're talking about runtime performance, for at least a moderate amount of loops. When you just need a very short-running utility for a simple, obvious task, java isn't appropriate at all. I think that's the main thing where you shouldn't use java. 

Python, and certainly ruby might (not always, it depends on a lot of parameters) beat java on development speed. 
Python and Ruby use runtime, dynamic typing, which was in the late 90's simply not done. In those years static typing was promoted as something good, mainly due to the fact that all examples where typing wasn't so strict produced horrible maintenance nightmares. From that perspective java was designed with strict static typing and strict OO enforcement. The use of 'simple types' vs. objects is about the exception (mainly for performance reasons) to this theoretical correctness.

Another problem that's often cited is the enormous memory usage. But again, 
this is mainly because it needs to start the JVM, and run the programs inside it. If you compare memory use of a simple one-task program to the same in C++ or python/ruby, java uses an extravagant amount of memory. But OTOH, if you compare the memory use for larger, application-scale tasks. The memory overhead isn't that much of a problem. So the same as I said before, don't use java for small or short-running tasks. 
Maybe that's another reason java isn't adopted well in the *nix world. It doesn't fit the classical approach of using a dedicated process for every subtask. You shouldn't write things like tail, logrotate, sed, ... in java.

When you look at the language itself, it's very very clean. Much cleaner than C/C++, and even (IMNSHO) cleaner than python/ruby. 
So, for a beginner, I think it's an excellent language (ruby at #2).

I'm not saying that java is perfect, but for the moment there's nothing better (again, ruby is coming close). (check out Bruce Tate: beyond java)

Some problems I see with java:
* Overly verbose code (that I have to write ;-(
   Who decided that closing a JDBC Connection can throw an SQLException??? and why do I have to catch that, and what the *** am I gonna do when it fails??? 
* You need a librarian to manage all the extra libraries needed when you make some real life large scale apps. 
* Choose the right editor. Eclipse is perfect, if you know the ins and outs. To start with (and especially if you don't know java yet) it might be terrible. The perfect editor is IntelliJ, but not everyone can spend a few $100 to just try out java. Maybe you can try the 30 day trial version, and after that try to switch to eclipse.

---

### Post by Darling on 2006-12-21
a reply to my own post ;-)
I just tried out netbeans again, and although it might not be as good as intellij in every aspect. It certainly looks good. For someone who just wants to try out java, I think it's easier to use than eclipse.

---

### Post by pmasiar on 2006-12-21
I kinda skipped this thread so far. I was promoting python :-)  in other threads, links from [here]("http://ubuntuforums.org/showpost.php?p=1900222&postcount=6") Some of them talk about C++, but most of the discussion is about comparing dynamically typed and statically typed languages. I was also forsed to start learning java lately (after working with perl for 3 years, and mixing in python for 2 more years). So I feel strongly about java, and can tell what is wrong with it IMHO with more informed opinios as someone who just learned java as first language and knows no better :-)

> **meng said:**
> I'm also a novice programmer, and having tried to make inroads into Java several times, I have recently come to Python and I have been very impressed. I think it's simpler to work with, but I would argue that it is just as object-oriented as Java is. It is just as cross-platform as Java, and also has good cross-platform GUI development tools.

Python is MORE object oriented than java: java lacks (1) operator overloading (for some very  important OO productivity booster), and (2) multiple inheritance. And pyhon is more flexible: it does not force everything into objects. In python , you can use procedural approach and split code into modules, until you are ready for objects. 

> **Nonno Bassotto said:**
> Is it slower than Python?

 Speed is red herring. MOST important speed is speed-to-market of your product. If your competition beats you to market, raw speed does not help you much. As I said elsewhere, implement whole thing in python, run profile, find 5% of code what uses 90% of runtime, and rewrite it in C. You have C-speed code, written and maintainable at python-speed.

Speed is not a problem until it is a problem. Usable and correct program is first.

> **nereid said:**
> This is hard to say. But Java is not very fast compared to a native language like C++. Java is very verbose and has, IMHO, very much overhead. If you want to learn how to program try a scripting language like Python or Ruby. Ruby is completly object oriented, much more than Python, and is also very easy to learn.

Ruby is also fine, but IMHO way too close to perl and its quirky syntax. Python was designed to be readable, and not verbose.

> **rekahsoft said:**
> it takes its nods from C#??? wt hell is that...Java was created way before C#...C# is MS's rip off of Java

C# is "C++ done right" by author of C++ Strousop (sp?) hired by MS. he learned from C++ and java mistakes - no wonder it is slightly better. But MS now realized they need scripting language, and they hired famous python hacker to port python to .NET: IronPython, open sourced, and very fast. Worth to watch for people interested in .NET 

> **misha680 said:**
> First of all, I have to say that I don't know a bit of Python, but I am pretty proficient in Java, C, C++, and a few others

Pros:
* I love that you already have implementations of all these data structures out of the box that you don't see in other languages, like trees and sets. ...
* Instant cross-platform compatibility.


It shows you don't know python. :-) I know java a little so I can compare

(1) Pyhon has MORE flexible structures (because of duck typing, you don't have to cast your objects when placed to collections and removed). List of dictionaries, where some values are mixed as scalars,  lists,  dictionaties, and lists of dicts - no problem in python (problem for your brain to handle that).

(2) Python runs on everything, from phones to mainframes to .NET, where C runs. java for .NET is *not* going to be inflicted upon us, I hope :-)

> **Nonno Bassotto said:**
> Yes, but almost everyone keeps suggesting to learn Python, which is interpreted as well. So, doens't Python have speed issues?

Speed is not a problem until it is a problem. Don;t guess: find bottleneck, and optimize it in C. *IF* it is a problem.

> **IYY said:**
> However, Java *is* a good language to learn, especially as your first language, because it is elegant and will introduce you to object oriented design nicely.

As I mentioned before, python is MORE OO, and is EASIER to learn, and code is less verbose ==> more elegant. Duck typing gives your development time incredible afterburner!

> **Darling said:**
> I really don't understand people mentioning (java is slow) and at the same time suggesting to use Python. 

**speed-to-market** is THE MOST important spedd in software project. In python, i write half the number of lines of code, 2 times as fast, and sped less time debugging, because python is WAY more intuitive. Duck typing and dynamic exception handling helps a lot, too,

> **Darling said:**
> I'm not saying that java is perfect, but for the moment there's nothing better (again, ruby is coming close). (check out Bruce Tate: beyond java)

Tate seems to me one of those who switched from hyping java to hyping ruby. I guess they cannot accept that python was there all the time and they missed it. I wonder what Tate will be hyping in 5 years from now. :-)

> **Darling said:**
> Some problems I see with java:
* Overly verbose code (that I have to write ;-(
   Who decided that closing a JDBC Connection can throw an SQLException??? and why do I have to catch that, and what the *** am I gonna do when it fails??? 
* You need a librarian to manage all the extra libraries needed when you make some real life large scale apps. 

With java, instead of spaghetti-code (with GOTO all over) we have **ravioli-code**: hundreds and hundreds of small, bite-size classes you need to learn, or you might bite into something indigestible. Python gives you duck typing, dynamic exceptions, and sane, spartan IDE for libraries.

---

### Post by samjh on 2006-12-21
> **pmasiar said:**
> Python is MORE object oriented than java: java lacks (1) operator overloading (for some very  important OO productivity booster), and (2) multiple inheritance. And pyhon is more flexible: it does not force everything into objects. In python , you can use procedural approach and split code into modules, until you are ready for objects. That actually makes Python less OO than Java.  To me, Python seems to be a procedural language with Objects tacked-on.  Java feels like a OO language with one deviation (ie. the "main" method, and primitive data types).  Preference for either is very subjective - I prefer the latter (ie. Java's approach).

As for operator overloading and multiple inheritance, they are not necessary in OO.  Java allows the use of interfaces instead of multiple inheritance.  Not the same thing, of course, but it's easier on the brain and reduces the chances of errors when inheriting from multiple classes.  I've never had to use operator overloading in C++, so cannot comment on that.


> C# is "C++ done right" by author of C++ Strousop (sp?) hired by MS. he learned from C++ and java mistakes - no wonder it is slightly better. But MS now realized they need scripting language, and they hired famous python hacker to port python to .NET: IronPython, open sourced, and very fast. Worth to watch for people interested in .NET You're getting people mixed up.  Bjarne Stroustrup was not the one hired by MS.  C#'s lead archtech was/is Anders Hejlsberg, who is known for developing Turbo Pascal and later, Delphi.

Stroupstrup's actual opinion of C# can be found here, at his homepage (it's not a friendly opinion):
[http://www.research.att.com/~bs/bs_faq.html#Csharp](http://www.research.att.com/~bs/bs_faq.html#Csharp)


> (2) Python runs on everything, from phones to mainframes to .NET, where C runs. java for .NET is *not* going to be inflicted upon us, I hope :-)It already has: in the absurdity that is J#.  MS tried to flush Java down the toilet with Visual J++, and now they try again with J#, with no better success than before.  Truly, they should just stick to C#.


> With java, instead of spaghetti-code (with GOTO all over) we have **ravioli-code**: hundreds and hundreds of small, bite-size classes you need to learn, or you might bite into something indigestible. Python gives you duck typing, dynamic exceptions, and sane, spartan IDE for libraries.I've never had this problem before.  In fact, I personally find it very digestible.  Of all the languages I have worked with (Pascal, C/C++, various assembly languages, Visual Basic, and Java), I find that even poorly-written Java is relatively easy to understand.  It can be a bit frustrating if you're an experienced programmer, but the one-class-per-file rule at least enforces relatively good modularity and source-file organisation.

As for ravioli-code classes, Java is heavily OO, what else can you expect?  C++ is much worse, IMHO.


A previous poster commented about incompatibilities between JVM implementations, citing examples from AIX, etc.  Please keep in mind that the only platforms Sun develops JVMs for are Windows, Linux, and Solaris.  Other JVMs for HP, IBM, etc., are developed by the vendors.

---

### Post by lloyd mcclendon on 2006-12-21
> **pmasiar said:**
> Python is MORE object oriented than java: java lacks (1) operator overloading (for some very  important OO productivity booster), and (2) multiple inheritance.

LMAO you can't be serious right

operator overloading has nothing to do with object oriented ness, it's just syntatic sugar that is often misused and while it is cool, at the end of the day it makes code harder to read and maintain.

multiple inheritance is bad design and shouldn't be used.  program to interfaces instead ... does python have those?

and what about private methods?? protected methods?  generics?  more object oriented my ***

> (1) Pyhon has MORE flexible structures (because of duck typing, you don't have to cast your objects when placed to collections and removed). List of dictionaries, where some values are mixed as scalars,  lists,  dictionaties, and lists of dicts - no problem in python (problem for your brain to handle that).

can your brain handle 

**private** List<List<Map<DomainObject, List<Map<DomainObject, DomainObject2<DO3, Do4, List<Do5>>>>>>> privateStructureThatYouCantSeeInJavaButPythonJustPutsUnderscoresAroundItBecauseItsMoreObjectOrientedIfItCanEvenSupportAnObjectThisCool;

> (2) Python runs on everything, from phones to mainframes to .NET, where C runs. java for .NET is *not* going to be inflicted upon us, I hope :-)

yeah it runs everywhere that python is installed.  java runs everywhere that java is installed which is A LOT more places.  and .NET is beat anyway who cares


> With java, instead of spaghetti-code (with GOTO all over) we have **ravioli-code**: hundreds and hundreds of small, bite-size classes you need to learn, or you might bite into something indigestible. Python gives you duck typing, dynamic exceptions, and sane, spartan IDE for libraries.

this is a pretty weak argument, how do you not have the ravioli code in "more object oriented" python?  i would argue that ravioli code is actually a good thing (to a point).  an IDE for libraries??? wtf are you smoking do you mean API?

i've run across a lot of inexperienced python zealots but you might be the biggest.

don't get me wrong i like python for quick little hacks like text processing etc, but i would never use it on a serious project.  i've got a very good stack of java frameworks and tools (python being one of them) that i can develop a web app very quickly, pythons terse syntax with no tooling support is not going to help me develop the type of stuff i do faster i'd put money on it.

---

### Post by Jeff Johnston on 2006-12-21
There is really nothing more that I can add, other than I hope that Java is given a fair shake now that it is being released under the GPL. As mentioned before most of people's opinions on Java has a basis, but on old facts that no longer apply. However, until we create more apps that really show off what Java (on the desktop) can do there is no reason to think Java's reputation will be very good.

I have been developing Java for web applications for years and it is amazing. People who are not in the Java loop have no idea just how much open source code there is in the wild. There are excellent frameworks galore, and every imaginable api to use for everything you need. The quality of the open source api's that I use are truely amazing.

For developing applications (server or client) you have industrial strength tools with Eclipse and Netbeans. A few years ago I really wanted to learn GTK+, but I could not get over the lack of good development tools. I probably shouldn't say that because for so many people tools like emacs are good enough, but they are not modern enough for people coming from windows and are comparing our tools to theirs. 

I haven't used it myself, but a very interesting project is Matisse. This a GUI tool that allows you to build Swing apps with drag and drop. I have had my doubts, but the reviews have been so good that I have to believe the project is a success! I also hear that there is work of a similar toolkit for SWT.

One interesting thing to me is I like the fact that for Python you do not compile your code, but I would say the same thing about Java. See, when you use tools like Eclipse your code compiles each time you save, but so transparently you cannot tell it is compiling at all. Then you build your projects with tools like ant, and never really get exposed to compiling anything.

Maybe the best thing to do at this point is just put your biases aside for now and start over with your opinions of Java once the GPL is fully applied to the language.

---

### Post by andyhuk on 2006-12-23
While everyone is making good and relevent points about this I also think a key point is being missed.  Its about suitability at the end of the day.  For example, if you were about to write the next great operating system you wouldn't be about to use Python (or Java for that matter) but would probably rely on plain c to do the job.  If you wanted a solid, reliable stable desktop application for MS Windows then you would probably consider visual c++ first.With c/c++ on Unix being favoured.

Other languages like Python and c# are still too new to be considered "safe" for professional development work; Java on the otherhand is a strong alternative to using c/c++.

There is nothing wrong as such with Java after all it is now open source, SDK 6.0 offers significant performance improvements (according to Sun) and it is being used for large scale projects in industry.  When a large stable, secure application is required Java is one of the "big three" c, c++ or Java are the first instinct choices for a professional programmer.

---

### Post by Wybiral on 2006-12-23
I think java and python a little less so for professional programmers... Using either of them requires the interpreter to be installed on the user end and I think a lot of companies will opt to use a language that isn't dependent on an interpreter or VM.

I've always liked python, and I'm beginning to change my mind about java (especially since they went gpl)... But, I wouldn't expect too many big companies to favor java over a compiled language, they would rather take the extra time to compile it for other platforms than risk losing users because of dependencies like an interpreter.

From the recent research I've done, the JIT is a really impression piece of code... But I highly doubt professional programmers will need to use java for much more than web development. Now, for web dev... Yes, I think java has, and will continue to, catch on and allow for extremely dynamic websites and even network/server access.

Now, don't misinterpret me here, I know that a handful of companies DO use java, I just don't see it becoming equal to C or C++ any time soon. The GPL thing might be a huge advancement for us (as in, the open source community), but I'm not sure how much that would matter to a large corporate company employing professional programmers who they expect to be able to write efficient and portable software even without java.

I'm just voicing my opinion, not challenging anyone, I've discovered java to have improved a lot since I initially learned it, and it seems like it's actually a very efficient language. I'm curious to see where java goes now and I am probably going to have to start learning it again.

Off topic:
I'm curious about one thing...
How secure is java when it comes to being used in web applets?
Does it disable or warn of the use of any malicious commands, or could I write an applet to destroy someones hard-drive in a java game? I know it may be a dumb question, I'm just curious/concerned about what kind of control embedded java apps really have.

---

### Post by SuperMike on 2006-12-23
I tried Java with all my heart for 1 year, and then JSP for the second year. I then bailed on it when I got more interested in PHP, which is my favorite language. Here's what I dislike about Java:

1. The Academic and/or RTFM community of it.

2. Who died and made the MVC model king? It's not always the most efficient way to handle a task.

3. After hours of searching and going down dead-ends, you find a function you like, but then you find it's picky about the parameters it wants. You then have to find 5-6 other functions to run your data through in order to get it in the right data type that you can pass to the function you want. It was quite aggravating and a huge time-killer.

4. Spending 2 months in OOP meetings before a block of code is ever written. I got sick of meetings like that. This took OOP to a ridiculous extreme, making every silly thing into an object even when it doesn't make efficient sense.

5. I got sick of coding, compiling, coding, compiling. I loved how in PHP I could just write the code and run it. I also got sick of having trouble compiling the Java stuff because of dependencies and command line switches, or sometimes just the way you specify the path of stuff.

6. The Java crowd seems too enamorate with the various Design Pattern books, making me have to use a fancy, stupid phrase for some OOP model I had been using for quite awhile. It gets to be a bit conceited and pretentious. I recall some "Senior" programmer arguing with me over his choice of OOP design pattern versus mine and he used all these fancy, pancy phrases that proved very little worth to anyone and only created a schism on the project team between those who were academic and those who wanted to just get the project done.

7. Java on Linux was an afterthought for quite some time. That was like majorly stupid. Sun had to take over the Java on Linux project, I think I recall. I think it was called BlackComb or something and Sun absorbed that. But Java on Windows and Java on Solaris was working for quite some time before that.

8. The fact that IBM and Microsoft were making competitive versions of Java didn't help Sun's cause very much. I can't tell you how many times I would write something in Java and pass it to a friend and they said that they couldn't run it because they were using a different brand of Java.

9. Java has a super-fast deprecation schedule. If it took you 6 months to write something, ten of the main APIs you relied on had already deprecated.

---

### Post by Tomosaur on 2006-12-23
> **Wybiral said:**
> I think java and python a little less so for professional programmers... Using either of them requires the interpreter to be installed on the user end and I think a lot of companies will opt to use a language that isn't dependent on an interpreter or VM.

I've always liked python, and I'm beginning to change my mind about java (especially since they went gpl)... But, I wouldn't expect too many big companies to favor java over a compiled language, they would rather take the extra time to compile it for other platforms than risk losing users because of dependencies like an interpreter.

From the recent research I've done, the JIT is a really impression piece of code... But I highly doubt professional programmers will need to use java for much more than web development. Now, for web dev... Yes, I think java has, and will continue to, catch on and allow for extremely dynamic websites and even network/server access.

Now, don't misinterpret me here, I know that a handful of companies DO use java, I just don't see it becoming equal to C or C++ any time soon. The GPL thing might be a huge advancement for us (as in, the open source community), but I'm not sure how much that would matter to a large corporate company employing professional programmers who they expect to be able to write efficient and portable software even without java.

I'm just voicing my opinion, not challenging anyone, I've discovered java to have improved a lot since I initially learned it, and it seems like it's actually a very efficient language. I'm curious to see where java goes now and I am probably going to have to start learning it again.

Off topic:
I'm curious about one thing...
How secure is java when it comes to being used in web applets?
Does it disable or warn of the use of any malicious commands, or could I write an applet to destroy someones hard-drive in a java game? I know it may be a dumb question, I'm just curious/concerned about what kind of control embedded java apps really have.

Java is a very professional language, and is used on many, many different platforms specifically because it is inherently cross-platform. It's one of the most 'professional' languages available. Yes, you don't often find commercial applications written in Java - but then again, most software is in-house stuff which is never released anyway. Java is very often found on portable devices and electric appliances. I think the story goes that it was invented to work on appliances to bring some kind of 'standardisation' to the market, and as such is found in Microwaves and refrigerators and stuff like that. Not to mention cell phone apps, thousands of which are written in Java. Don't underestimate it - Java makes lots and lots of money.

---

### Post by Wybiral on 2006-12-23
Oh, I know it is useful and has many practical uses... I'm just saying, it's probably not as likely to end up being more important for a lot of software developers to know than C or C++. But, it really depends what you're doing...

Different languages for different problems. Java works great for small applications and especially networking utilities such as FrostWire... But as I said, software developers don't want to limit themselves to depending on another program.

The perk: almost platform independence
The downside: dependency on the java VM

Not everyone wants to install the VM on their computer, especially not just for a single program they plan to use. They will find an alternative. Something well written in C++ can be cross compiled for the major platforms and then distributed as separate platform dependent versions. A lot of companies opt for this. And when they don't care about platform independence, unfortunately they just write it up for windows and call it a day.

I am not trying to downplay java... It probably does just fine for a lot of stuff, especially network utilities and games... I just don't think it's as big in the industry as I've seen people tout it as. You may have to learn it in college at one point or another (not sure why), but you probably wont *have* to use it much in the real world (depending on your job).

Never-the-less, it's probably worth learning anyway, it's not a terrible language... But remember that not everyone has the hard drive space, CPU power, or the patience to download and install the java JRE.

---

### Post by Tomosaur on 2006-12-23
I would have thought that VM dependance was far less demanding than architecture dependance...

When you compile C code, you compile it for one machine. If your customers do not have the same platform, and in some cases the same environment, then those customers are not available to you. The JVM is already available for a number of different platforms, eliminating this architecture dependance without any extra work. It's more convenient to say 'you need the JVM' than it is to say 'you need X architecture'.

And don't get me started on binary/library dependence. In my own view, this 'oh you need the JVM' argument is truly a non-issue. If a developer of 'real' compiled code wants to make his/her application available on multiple platforms, then he/she either needs to make their code available, requiring the customer to compile it for themself, OR compile the code a number of times, which can often involve re-writing portions of the code, which in large projects can consume a LOT of time, and increase costs. With Java, you really do just 'write once, run anywhere'. I'm not attacking you, or compiled code, I just don't see the logic behind the JVM dependancy argument. It doesn't make sense to use it to attack Java, when in reality it's actually an advantage. Sure, it can slow your program down, but in most cases, the effect is barely noticeable, and it can be overcome anyway. I would much rather have my app depend solely on the JVM rather than have it depend on a ton of third-party libraries AND a specific arch.

EDIT: In my own opinion, C, or C++ are great languages, but only because they are more powerful. They allow you to do a hell of a lot more than Java, particularly when it comes to low-level stuff, but if your app is focused on high-level stuff, then to me, Java just seems the better choice. I don't want to seem like some Java zealot - I too get irritated with it's many problems, I just want to provide my two cents :P

---

### Post by Wybiral on 2006-12-23
WHAO...

I'm not attacking java. But the fact remains that a LOT of corporate programming is done in either C or C++... I'm not trying to put java down and I don't think either of us need to "attack" each other. I'm just coming up with potential reasons why java isn't as commonly used for *most* software design.

Personally, I didn't install the JVM on my machine for a LONG time, I just recently did... And frostwire is the only program I am running on it. Chances are, I'll find a substitute for frostwire and uninstall java... Fortunately for my computers java enabledness, I haven't found a replacement for frostwire.

All I'm saying is that for most people, installing extra stuff... Just to install something else... Will probably turn them off.

Now, I realize that a lot of people have java installed to begin with, but not everyone. And I don't see why you would want to risk it if you could just write some careful C / C++ code. You don't even have to be THAT careful, just learn some good standard cross platform techniques... And cross compilers are easy to find and use... C and C++ aren't as "platform dependent" as people think.


Anyway... I don't mean to bash java. I'm just explaining why I believe it isn't being AS commonly used (not that it isn't being used). Plus, it wasn't really an attack, the topic is "What's wrong with Java?" and I was just stating my opinion.

---

### Post by lloyd mcclendon on 2006-12-24
well your opinion is based on nothing and you're starting to look silly over here.  fyi java is and has been the most popular & widely used language for a while now

[http://www.tiobe.com/tpci.htm](http://www.tiobe.com/tpci.htm)

and it is not without good reason.  jvm / arch / platform stuff aside (really nobody cares about this stuff much anymore anyway, retail pcs all have the jvm installed now) ... it's really a great language with a lot of clean useful features and a very nice standard library that makes a ton of sense once you work with it for a while.

and also there is this thing called eclipse, one of the best pieces of software ever developed.  some argue that c# is a better language, and even if they're right i'll still stick with java for eclipse.  right now it's got over 1600 developers around the world working on it, how many do you think MS has working on visual studio right now?  eclipse actually has more LOC than vista and it works amazingly well.  even if you don't do java programming, eclipse can make your life 10x easier.

---

### Post by samjh on 2006-12-24
> **Wybiral said:**
> I think java and python a little less so for professional programmers... Using either of them requires the interpreter to be installed on the user end and I think a lot of companies will opt to use a language that isn't dependent on an interpreter or VM.It's a wonder that Java and .NET are by far the two most widely used platforms in enterprise software development.  Both require the use of a virtual machine and interpreter/JIT-compiler.

I think you are incorrect in your assertion about companies not wanting to use a language dependent on an interpreter/VM.  The dominance of Java and .NET instantly proves it a fallacy.

> But I highly doubt professional programmers will need to use java for much more than web development. Now, for web dev... Yes, I think java has, and will continue to, catch on and allow for extremely dynamic websites and even network/server access.Java is one of the (if not "the") most widely used development platform for mobile devices.  Java niche in enterprises is indeed server-side, but it also has very strong presence in mobile applications too.

> Now, don't misinterpret me here, I know that a handful of companies DO use java, I just don't see it becoming equal to C or C++ any time soon.Hardly any companies use C/C++ for in-house development.  I can only think of telcos and security development houses.  One quick search at respected job search sites produces enough numbers to see that Java (along with .NET) prevail over C/C++.

> Off topic:
I'm curious about one thing...
How secure is java when it comes to being used in web applets?
Does it disable or warn of the use of any malicious commands, or could I write an applet to destroy someones hard-drive in a java game? I know it may be a dumb question, I'm just curious/concerned about what kind of control embedded java apps really have.Applets are prevented from executing system commands, so you will not be able to wipe out a person's hard-drive using a web applet.

Java *applications*, on the other hand, are much more powerful.  Java has a very strong security model, which makes it relatively easy to develop secure applications in Java, compared to "unsafe" languages like C/C++.  Apache Tomcat is a good example of how secure a well-designed Java application can be: it has no known vulnerabilities (last I checked), despite its wide usage.

But it is possible to write malicious Java applications, if it is programmed that way.  Java tries to limit the possibility of creating unintentional vulnerabilities by using very strict typing and automatic memory management (as you probably know, weak type enforcement and memory management is the main source of C/C++ vulnerabilities), and containing code execution within its VM.  However, there is still nothing to prevent a malicious coder from writing malicious software (same goes for .NET), and vulnerabilities can still be created unintentionally when using external calls or using C/C++ modules.

---

### Post by Wybiral on 2006-12-24
Ok... But I said SOFTWARE design, those statistics factored in WEB DESIGN too and obviously C and C++ cannot compete with those statistics. Find some statistics for actual vendor software and I will comply.

Btw, I hate visual studios, I don't really see what that has to do with any thing. I've used eclipse and I don't really see anything special for it. Nothing against IDE's, I just can't stand the overhead and am annoyed by autocomplete.

Anyway... You sound defensive, all I am saying is that it isn't *quite* as commonly used for software design and that I know a ton of people who have never had to learn it (and they've had a number of jobs). I never said java was bad of anything... I was just explaining why I believe C and C++ are more common.

Now, you guys need to settle down and stop biting people for not being java users.

---

### Post by samjh on 2006-12-24
If that was directed at me, I didn't intend to be defensive about Java.  But if I was defensive, well one could mistake your posts as "aggressive". ;)

Java isn't a one-stop solution to all the problems in the universe, but its influence and importance shouldn't be downplayed either.  If you mean software design as in programs that companies make to sell to others, then I agree that C/C++ are the most popular (although on the Windows platform, a lot of vendors are moving to C# and VB.NET).

---

