---
title: "How to get knee-deep in Java"
date: 2008-06-01
forum: Programming Talk
---

### Post by Lau_of_DK on 2008-06-01
Ladies and gentlemen,


I've always hated Java and therefore avoided it like the plague. Now the unfortunate thing has happend, that a Lisp has been implemented on top of a JVM, which means I have to learn alot of Java, really really fast. 

Can I have some of you Java-gurus fill me in on how I in the fastest possible pace, become familiar with as many of the major (most useful Java Classes) that Java has?

Is there something similar to CodeProject.com (Which is particularily good for C++, C# and ASP.Net) to see how alot of people solve various issues using Java? 

Thanks,
/Lau

---

### Post by mike_g on 2008-06-01
I dont know all that much about java yet either, but I found the stuff on Sun's website helpful and easy to understand. Also, if you have netbeans with the javadocs installed you can find out a lot about most things via the code completion; i found that very handy.

---

### Post by NormR2 on 2008-06-01
Here are the links to some forums for getting help that I've used:
[http://saloon.javaranch.com/cgi-bin/ubb/ultimatebb.cgi?ubb=forum&f=1](http://saloon.javaranch.com/cgi-bin/ubb/ultimatebb.cgi?ubb=forum&f=1)
[http://www.codeguru.com/forum/forumdisplay.php?s=&forumid=5](http://www.codeguru.com/forum/forumdisplay.php?s=&forumid=5)

---

### Post by pmasiar on 2008-06-01
"Head-first Java" and Bruce Eckel's "Thinking in Java" are extremely good books.

Syntax of Java is simple enough: problem is to learn the library. I read somewhere that instead of "spaghetti code" in Java we have "Ravioli code": hundreds of small objects with different fillings, you need to try each to learn what is inside. There is no way to learn such vast and byzantinely complex library fast - you learn subset you need, possibly with a help of a guru who wants what you need, to save you time. First time trying to grok it is like trying to drink from a firehose :-)

---

### Post by LaRoza on 2008-06-01
> **pmasiar said:**
> "Head-first Java" and Bruce Eckel's "Thinking in Java" are extremely good books.

Syntax of Java is simple enough: problem is to learn the library. I read somewhere that instead of "spaghetti code" in Java we have "Ravioli code": hundreds of small objects with different fillings, you need to try each to learn what is inside. There is no way to learn such vast and byzantinely complex library fast - you learn subset you need, possibly with a help of a guru who wants what you need, to save you time. First time trying to grok it is like trying to drink from a firehose :-)

Thinking In Java is on my wiki (thanks to Bruce Eckel for allow it to be downloaded).

Java annoyed me when I learned it because of all those libraries. I felt a need to use C.

---

### Post by Quikee on 2008-06-02
With learning programming languages is the same as with programming itself - you learn only what you need and don't try to learn upfront. I never had any problem with Java class library this way. The net is also full of java so usually when I need something I find it fast via google.

Of course things like reading from a file can be hell in Java and the language itself is verbose, but once you reach a certain level it is fun to program in it (however not more fun than programming in python, smalltalk or groovy).

---

### Post by xlinuks on 2008-06-02
Java is too large, there are too many areas, mobile, web, desktop, 3D, TV, Card, which one do you wanna learn?
Java is enterprise oriented, that's why it's verbose and has so many classes - you have lots of classes you don't have in other languages and many of them you'll never use (like Corba).
When programming GUI (and other areas) I find "The Java tutorial" by Sun really nice, it contains virtually anything, and it's up to date and fit for Java 6!!:
[http://java.sun.com/docs/books/tutorial/reallybigindex.html](http://java.sun.com/docs/books/tutorial/reallybigindex.html)

The latest version of "Thinking in Java" is way too verbose, many people think that he has gone too much into philosophy forgetting that readers might be busy programmers, he doesn't treat all the practical aspects of Java you're gonna face, he talks a lot about "why" while you only need/want to know "how".

Don't expect to do _serious_ programming after a month or so, and there will also be frustrations just because it's another language, it always happens, to people going from .Net to Python, from Java to C++.
And by the way, make sure you don't install OpenJDK since it (still) has seriuos problems with graphics rendering, better install Sun's JDK "sudo apt-get install sun-java6-jdk".
NetBeans is very intuitive and easy to use, it supports Java best off all keeping track of what you're doing and suggesting what you should do, IMO when it comes to Java - use NetBeans, when C++ - Eclipse or something alike.

---

### Post by Lau_of_DK on 2008-06-02
Big thanks to everyone who posted.

Especially the "dont learn upfront" comment was what I needed to hear :)

If anybody else out there has a gold-mine, feel free to share.


/Lau

---

### Post by CptPicard on 2008-06-02
Mind you, Java is probably the only language on Linux that has the sort of VS-kind tools you're missing from Windows... when it comes to the large libraries, the "IntelliSense" of Eclipse or Netbeans is very helpful, especially if you also hook the Javadoc-commented sources to the IDE so that you not only get the method signatures but also their descriptions in the pop-up box.

---

### Post by Balazs_noob on 2008-06-02
you can try this --> [http://www.java2s.com/](http://www.java2s.com/)
tons of little Java code pieces organized

---

### Post by Lau_of_DK on 2008-06-02
> **CptPicard said:**
> Mind you, Java is probably the only language on Linux that has the sort of VS-kind tools you're missing from Windows... when it comes to the large libraries, the "IntelliSense" of Eclipse or Netbeans is very helpful, especially if you also hook the Javadoc-commented sources to the IDE so that you not only get the method signatures but also their descriptions in the pop-up box.

Yea thanks Picard :)  I am of course not looking to stay in Java, just familarize myself with enough helper classes to add so much power to my emacs that it will glow in a light shade of blue. :)

> **Balazs_noob said:**
> you can try this --> [http://www.java2s.com/](http://www.java2s.com/)
tons of little Java code pieces organized

Good one! :)

/Lau

---

### Post by CptPicard on 2008-06-02
> **Lau_of_DK said:**
> Yea thanks Picard :)  I am of course not looking to stay in Java, just familarize myself with enough helper classes to add so much power to my emacs that it will glow in a light shade of blue. :)

Nah, Java is not THAT bad. :) With Clojure you can use it as a kind of lower-level "C" for performance critical bits, so getting familiar with the language is not a bad idea (after all it's a fairly simple language too, compared to learning Lisp it is a trivial exercise).

Besides, the Netbeans GUI builder really does rule.. :)

---

### Post by Lau_of_DK on 2008-06-02
> **CptPicard said:**
> Nah, Java is not THAT bad. :) With Clojure you can use it as a kind of lower-level "C" for performance critical bits, so getting familiar with the language is not a bad idea (after all it's a fairly simple language too, compared to learning Lisp it is a trivial exercise).

Besides, the Netbeans GUI builder really does rule.. :)

Yea Im sitting in Netbeans now actually, looking at images from the Mars Rover. Its pretty amazing how closely MS made C# to Java. I mean the code I understand intuitively without ever having seen Java before, there are no surprises whatsoever.

---

### Post by Wybiral on 2008-06-02
> **Lau_of_DK said:**
> Yea Im sitting in Netbeans now actually, looking at images from the Mars Rover. Its pretty amazing how closely MS made C# to Java. I mean the code I understand intuitively without ever having seen Java before, there are no surprises whatsoever.

As with all the C-like languages... If you've seen one, you've seen them all.

---

### Post by pmasiar on 2008-06-02
> **xlinuks said:**
> The latest version of "Thinking in Java" is way too verbose, many people think that he has gone too much into philosophy forgetting that readers might be busy programmers, he doesn't treat all the practical aspects of Java you're gonna face, he talks a lot about "why" while you only need/want to know "how".

There are plenty of "how" books - but if you read  only those, you will be just (highly skilled) code monkey. Eckel's "why" book helps you to learn why decisions were made, and what are the consequences of them, so there is less to remember of "how" - after you know why, rest makes more sense. It is not supposed to be first book for a busy programmer, it's goal is to guide programmer from a level of code monkey to master.

---

