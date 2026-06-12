---
title: "java in ubuntu"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by navaleshubham10 on 2011-12-21
iam using ubuntu 11.10 i want to learn java so how can i install net beans in ubuntu 11.10 and how can get pdf books to learn java programming for free:confused:

---

### Post by cortman on 2011-12-21
A beginner can usually more easily code in Java just using a text editor, and that's what I'd recommend. Gedit, which comes bundled with Ubuntu is great and simple. If you want to use text editing power tools and don't mind putting in time learning them, by all means go with Emacs.
If you really want to use an IDE, though, I prefer Eclipse. It's easily installable.

```
sudo apt-get install eclipse
```

And as far as free PDFs, there's a world of them out there. Google search "filetype:pdf learn java" and that should get you a lot of hits.
I started out with [this excellent textbook.]("http://math.hws.edu/eck/cs124/downloads/javanotes6-linked.pdf")

---

### Post by Lars Noodén on 2011-12-21
In addition to Gedit, there are also Geany and Kate which have useful plug-ins.

Later, as you are more comfortable, you can look at Apache Tomcat and write Java Server Pages.  There are lots and lots of tutorials on the net about that.

---

### Post by vangop on 2011-12-21
Just a note - do not install any java software (eclipse, maven, netbeans, tomcat etc) from ubuntu repos. 1st of all they're outdated there, 2nd, the install will pull a crazy load of useless libs. see [example]("http://ubuntu-answers.blogspot.com/2010/12/install-maven-on-ubuntu-linux.html").
Just download the binary from the official site. In most cases no installation is needed, just unpack.
I wouldn't bother with text editors, use IDE.

---

### Post by gim- on 2011-12-22
Just download it from the official site here:
[http://netbeans.org/downloads/index.html](http://netbeans.org/downloads/index.html)

---

### Post by MartijnNL on 2011-12-22
Semething useful to be aware of: the sun-java packages in the repositories are empty as of the day before yesterday, due to license issues. [See this thread]("http://ubuntuforums.org/showthread.php?t=1897885").

---

### Post by QIII on 2011-12-22
With all due respect to some of the previous posters, as a software developer who cut his teeth in the 1970's, I must state that it is my opinion that some of the advice heretofore given should be disregarded.  My opinion.

1.  Install the build-essential package.

2.  If you have installed the JRE by any other means that what I will give you in 3., uninstall it by the method you installed it.

3.  I'm on my cell, so I can't attach a url.  But google

```
easy linux tips java
```and you will find a tremendous tutorial for installing the JRE in Ubuntu.

Edit:  Here's the url:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

4.  Using the instructions on Sun's site, install the JDK in the same directory as you just installed the JRE.

5.  **USE AN IDE, EVEN AS A BEGINNER.  PERIOD.**  Unless you intend to earn a degree in Computer Science, allow the IDE to do the work of compiling and making your project.  IDEs also have some very useful built-in tools that will help you explore and understand the language.  Many of them can, for instance, let you see how many threads are being spawned and check for memory leaks.  (That's a term you should look up and be familiar with.)  Furthermore, IDEs are what guys like me use to make obscene amounts of money doing this stuff 5 days a week.  Understanding how to use an IDE is integral to developing.  If, after learning the language, you want to learn the mechanics of manually compiling and making projects then do that by all means.  It is good stuff to know.  Netbeans is really the "native" Java IDE (if there is such a thing), but I like Eclipse too.  Netbeans is quite easy to install, as has been suggested by a couple of posts above.

6.  Use google to find every online tutorial you can get your hands on and use them all.  Here's a good place to start:

[http://docs.oracle.com/javase/tutorial/](http://docs.oracle.com/javase/tutorial/)


Just the opinion of a guy who has been around since the days of punch cards and acoustic coupling devices.

Now then.  Don't limit yourself to Java.  Java has some "intriguing" limitations and a few things about the language seem bass-ackwards from my point of view.  And you'll have to decide, at some point, if you want to be big-endian or little-endian.

---

### Post by cortman on 2011-12-22
> **QIII said:**
> 
5.  **USE AN IDE, EVEN AS A BEGINNER.  PERIOD.**  Unless you intend to earn a degree in Computer Science, allow the IDE to do the work of compiling and making your project.  IDEs also have some very useful built-in tools that will help you explore and understand the language.  Many of them can, for instance, let you see how many threads are being spawned and check for memory leaks.  (That's a term you should look up and be familiar with.)  Furthermore, IDEs are what guys like me use to make obscene amounts of money doing this stuff 5 days a week.  Understanding how to use an IDE is integral to developing.  If, after learning the language, you want to learn the mechanics of manually compiling and making projects then do that by all means.  It is good stuff to know.  Netbeans is really the "native" Java IDE (if there is such a thing), but I like Eclipse too.  Netbeans is quite easy to install, as has been suggested by a couple of posts above.


Nods to the old programmer- your advice is definitely worthwhile.

Some programmers recommend starting out with just a text editor instead of an IDE so that the beginner doesn't have the added challenge of learning an IDE besides just learning the language. There is probably some merit to this but I found for myself the biggest advantage to starting out with a text editor is learning to be accurate. The IDE provides all the class and method declarations for you and automatically highlights syntactical errors, which for production programming is invaluable but for me as a rather absent minded beginner started to make me sloppy with my syntax.
I guess it's really a non-issue, but I would say that using a text editor helps sharpen your ability to program anywhere, with any editor, on any machine, and increases accuracy. Once you have that down, use an IDE by all means. I would hate to be deprived of my Eclipse.

---

### Post by QIII on 2011-12-22
What is more conducive to learning not to be sloppy:

1.  Hours or days beating one's head against the wall trying to interpret a cryptic message

-- OR --

2.  Three or four gentle reminders that you have done something wrong.

You can write sloppy code in an IDE or a text editor and the code will still compile and run.

This is just my opinion, of course.  

I used to teach people to blow things up with explosives.  Even how to make the explosives if they didn't have any but had raw materials.  I did not care that they understood very much of the physics of what they were doing, only that they could choose the appropriate explosive, place and configuration of the charges for what they were attempting to do.  If they wanted to learn more theory after I was convinced that they could take down a bridge under enemy fire, I would happily oblige.  It was neither in their best interest nor mine to have them blow themselves up first and beat their heads against a wall trying to interpret the cryptic "You are now dead" message.  Much better that they should be told what it is they are doing wrong during training and corrected immediately.  (In that context, the "gentle reminders" might still have been somewhat uncomfortable!)

I learned to do this computer thing in a green/yellow on black terminal years ago.  Not even a modern text editor included.  It is my considered opinion that the idea that one is best served by learning in a text editor is an outmoded, horse and buggy hanger-on from a bygone era that some "old timers" still think is the "real way" to do it.  

"Back in my day..." is a great way to guarantee nothing improves.

My dad is a computer geek from the 40s and even he has embraced the new.  Change is good.  

As I said.  One can always go back to the old way in Computer Science coursework (I had to do it decades ago.)  One probably should eventually scrape the paint and look at the metal.  But I don't think it is necessary for learning a language.

Again.  Just my opinion.  And, of course, no flame thrower.  I hope you can appreciate this is simply a discussion of an old fart's philosophy.

---

### Post by cortman on 2011-12-22
There's advantages and disadvantages to both ways, I guess. I hold to my position from my own personal experience. If I got an error message on compiling, it was often detailed enough to point me to the specific line of code. But it could be the OP isn't as absentminded or ADD as myself, which is quite possible...

Thanks for your contribution! I'm always interested in a computer old-timer's advice and philosophy, being pretty young myself ('89er).

---

### Post by medokr on 2012-01-06
> **navaleshubham10 said:**
> iam using ubuntu 11.10 i want to learn java so how can i install net beans in ubuntu 11.10 and how can get pdf books to learn java programming for free:confused:

Please see: [http://pdf.coreservlets.com/](http://pdf.coreservlets.com/)
Contains 19 pdf chapters (JSP and Servlets really).


[http://courses.coreservlets.com/Course-Materials/java.html](http://courses.coreservlets.com/Course-Materials/java.html)
Java syntax, and related... These are nice to have as addtional resource in addition to java trails.

Java trails:
[http://download.oracle.com/](http://download.oracle.com/)**java**se/tutorial/

---

