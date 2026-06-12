---
title: "Do you program in Java?"
date: 2011-04-28
forum: Programming Talk
---

### Post by Drenriza on 2011-04-28
Do you program in Java? if so what do you create?

I'm looking a bit into this language, but kind of having a hard time to figure out what you can create with it. If i ask people i know i just get the answer "everything" but that isn't really a answer. What is it mainly used for? and is it usable in linux??

Kind regards.

---

### Post by scott-ian on 2011-04-28
Java is universal.  A Java program will work on any compatible computer with a Java Virtual Machine.  Java is used for desktop programs, but also works for web programs.  Java applets online allow advanced programs to be run in the browser.

---

### Post by llanitedave on 2011-04-28
Maybe you'd get a better discussion if you asked what *can't* you use Java for.

---

### Post by cstudent on 2011-04-28
I believe that OpenOffice is written largely in Java. Java is used in development of Android apps. We use a program where I work for coin operated vendors that tracks income and handles the handheld devices our drivers use that is largely written in Java. Java can be used just about anywhere.

---

### Post by unknownPoster on 2011-04-28
I've used Java quite a bit, to do a bit of everything. Projects I've completed:

1. Designed my own interpreted programming language that was interpreted to Java code.
2. Simple Email client using Swing (send and receive emails, contacts book, etc.)
3. A Java application that did most of the work in a virtual world bicycle simulator. You got on a exercise bike in real life and then rode around in a virtual world. Java handled all of the translation and number crunching between the bicycle hardware and the virtual world.
4. Web crawler/Spider that just crawled specific domains looking for images that met a specified requirement.

---

### Post by Simian Man on 2011-04-28
I have used Java off and on, most recently for doing some Android development.  It is a practical language in that there are lots of APIs available.  It is also cross-platform in that it can run on any platform, but it rarely feels at home on any platform, but this is mostly the fault of the horrible Swing GUI.

My main problem with Java, and the reason I avoid it were possible, is that the language has very little expressiveness.  It forces you to solve problems in a certain (often less efficient) way by removing the means to solve them any other way.  Sometimes when working with Java I feel like I'm trying to eat spaghetti with just a spoon :).

---

### Post by unknownPoster on 2011-04-28
> **Simian Man said:**
> I have used Java off and on, most recently for doing some Android development.  It is a practical language in that there are lots of APIs available.  It is also cross-platform in that it can run on any platform, but it rarely feels at home on any platform, but this is mostly the fault of the horrible Swing GUI.

My main problem with Java, and the reason I avoid it were possible, is that the language has very little expressiveness.  It forces you to solve problems in a certain (often less efficient) way by removing the means to solve them any other way.  Sometimes when working with Java I feel like I'm trying to eat spaghetti with just a spoon :).

I can attest to that. :)

---

### Post by PaulM1985 on 2011-04-28
I quite like Java.  I have been using it for creating basic games (pong, breakout, then moving onto simple platformers) which can be played on a mobile phone (Nokia), or as an online multiplayer (in the case of Pong).  I have also done various bits of web stuff for uni.  For my final uni project I am thinking of making an online multiplayer flight sim.

It has been mentioned that the Swing UI does not look great, but I have found that setting the look and feel using this:

```

    public static void initLookAndFeel()
    {
        try
        {
            UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());
        }
        catch (ClassNotFoundException e)
        {
        }
        catch (InstantiationException e)
        {
        }
        catch (IllegalAccessException e)
        {
        }
        catch (UnsupportedLookAndFeelException e)
        {
        }
    }

```

The applications can look more suited to the OS and less like the normal (and almost ugly) Java standard UI look.

I think the Java standard UI is done so that the application will look the same on all platforms, but I think people's preference is to actually have a program that suits the platform they are running it on.

The database capabilities seem to be relatively good, but that being said, it is just little bits that I have done at uni rather than full large-scale projects.

Paul

---

### Post by cgroza on 2011-04-28
> **cstudent said:**
> I believe that OpenOffice is written largely in Java. Java is used in development of Android apps. We use a program where I work for coin operated vendors that tracks income and handles the handheld devices our drivers use that is largely written in Java. Java can be used just about anywhere.

I did a slocccount once on it and C++ code is dominant in that program.

---

### Post by ratcheer on 2011-04-28
I have programmed in Java before, but I always try to avoid it.

Tim

---

### Post by stchman on 2011-04-28
Yes.

Many scripting languages use Java.

Java is one of the easiest ways to make GUIs for any OS.

Java is an excellent language for learning as it teaches good programming habits.

---

### Post by Jinren on 2011-04-28
> **Simian Man said:**
> I have used Java off and on, most recently for doing some Android development.  It is a practical language in that there are lots of APIs available.  It is also cross-platform in that it can run on any platform, but it rarely feels at home on any platform, but this is mostly the fault of the horrible Swing GUI.

My main problem with Java, and the reason I avoid it were possible, is that the language has very little expressiveness.  It forces you to solve problems in a certain (often less efficient) way by removing the means to solve them any other way.  Sometimes when working with Java I feel like I'm trying to eat spaghetti with just a spoon :).

I would second this. It's a great language if you like to do things the "Java way", and a terrible one if you don't. As it happens, I don't.

The libraries are a huge leap beyond almost everything else though. It's worth learning Java to learn the libraries at the very least, and if you end up not liking the language itself, there are several other options that compile to the same code that you can try later. That way you can still take advantage of the libraries and the cross-platform output.

---

### Post by Reiger on 2011-04-28
I like the practicality of the language. It doesn't feel the need to use a bazillion keywords or other syntactical constructs (less stuff to bite me where it hurts) and interpreting Java code inside my head is quite easy. 

I also prefer Java's static typing and method overloading to dynamic typing and the python/PHP abomination of approximating method overloading with keyword parameter or (worse) default values. The reason for the former is that I find myself wasting far more time with trivial errors that static type checking will catch during e.g. refactoring, and miss the proper tooling support to remove the need for me to make mistakes in the first place which you can't get without static typing. The reason for the latter is that I find documentation and method invocations get an order of magnitude more difficult to deal with [what if I want to specify param 3 but not param 2] than it would be with N versions of the same method each with its proper documentation.

I kinda miss functions as first class citizens but anonymous classes are actually much more versatile in more complex scenarios so it is more of a &#8220;wish&#8221; than a pressing heartfelt need. It is the higher order functions/methods and related support in the type system that I really miss here.

What I'm not too happy about with the language is the object/primitive dichotomy. I can see why it is done that way (a lot more efficient at run time) but it remains painful to work with.

Related why would you use Java. Consider that you want to create a tool of some kind which performs functions that the user must be able to automate (through some kind of script). The JVM and JRE libs make that trivially easy. C#, Qt, Kross, etc. etc. don't come even within a parsec of how easy that is on the JVM.

---

### Post by myrtle1908 on 2011-04-28
> **Drenriza said:**
> What is it mainly used for?

Backend/middleware in enterprise environments.  Very strong as the web middle tier.  Huge amount of support in corprate world ... in this arena it's usually either .NET or JEE.  You will typically find .NET in smaller enterprises and JEE in the larger.

---

### Post by BkkBonanza on 2011-04-28
I hate Java and have always avoided it. I've programmed in it and even taught a course in it many years ago. It has always been a pig to me and while I'm sure it's very practical for many who just want to get a job done I've always found anything written in it to be very unsatisfying. Whenever having a choice I'd always take a non-java version of something.

---

### Post by Some Penguin on 2011-04-29
> **Drenriza said:**
> Do you program in Java? if so what do you create?

Text- and occasionally number-crunching code, often related to analyzing incomplete and extremely error-prone sets of records from multiple sources to identify likely correspondences between them and reconstruct actually usable data.  This gets fairly interesting when you have millions of error-prone, highly incomplete records and the sets are not guaranteed to overlap all that well.  I've also worked on building systems for classifying documents and attempting to identify when they're discussing various entities of interest, versus merely mentioning them in passing.

> I'm looking a bit into this language, but kind of having a hard time to figure out what you can create with it. If i ask people i know i just get the answer "everything" but that isn't really a answer. What is it mainly used for? and is it usable in linux??

Kind regards.

'Everything' is, however, a largely accurate answer, given that it is a capable general-purpose programming language.  Resource requirements limit the 'everything' in a practical sense; it would not make any sense to embed a JVM in a tiny low-memory, power-constrained sensor unit just to implement a basic counter.  It's also not particularly obvious that one would, say, want to implement a Crysis-like game in Java, given that there's significantly more development work writing e.g. analytical engines and data warehousing code than there is in highly-optimized-for-performance graphics drivers. There's plenty of stand-alone tiny stuff that I'd rather write in Perl, for where there's minimal build overhead and there isn't actually a need to tightly couple it to an existing system.

If you'd much research at all, you might have heard of tiny projects like Apache Tomcat, Hadoop, Lucene, and Cassandra.  Or, say, Ning's Galaxy. It can be quite useful for building systems which scale *very* well, especially with all the built-ins relating to concurrency and networking.  JAX-RS / Jersey make it pretty simple to write new web endpoints; JDBC provides a common spec for database connectivity; Spring and Guice make initialization and configuration of well-abstracted systems simpler; JUnit makes a respectable test harness; Maven is generally good at dependencies and build management; and so forth.

---

### Post by jespdj on 2011-04-29
Java is the most used programming language in the world. It's used by many, many companies. It's main success is in server-side enterprise software.

I'm a professional Java programmer, I've done lots of projects in Java, from simple web applications to just manage some data in a database to mission-critical, high-performance middleware applications.

---

