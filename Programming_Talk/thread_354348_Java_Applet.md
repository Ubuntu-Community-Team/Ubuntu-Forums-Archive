---
title: "Java Applet"
date: 2007-02-05
forum: Programming Talk
---

### Post by nhandler on 2007-02-05
I've been programming in Perl for a while now. Recently, I have decided to attempt and learn Java (sort of a personal goal). Unless there is some major reason keeping me from doing this, I would like to start with Java web applets. Is that possible? Or do I need to start with command line programs? Also, could someone recommend a good tutorial on applets? I need a pretty basic tutorial (that goes from compiling to finished product). Thanks

---

### Post by randomnumber on 2007-02-05
I always recommend the basic hello world program.
I use a book called big java by horstman, it is a good book for general java but may be a little less advanced than you need. 

I understand that applets are disappearing and that they are all but obsolete in web pages. I think embedded jar files are replacing them. To be honest I do not deal with web pages much. 

I think that Java is structured a little differently in that it is object oriented.

Remember, Java is a object oriented language that has strict permission limits. You can not go outside an array bounds etc. 

An interesting note is that our CS degree went from c to c++  to Java. With each transition the failure rate increased. From what I understand, the CS department is going  back to C++. I was told that in into and intermediate classes the failure rate was over 50%. I am just saying do not get too discouraged if you find it difficult, its' not after a while. 

Good Luck

---

### Post by mrpeenut24 on 2007-02-06
We started out in Java in my CS degree (a few years before, students started out in C/C++), then went to C and then to Python (I think the intro classes are now being taught Python).  We also used the Big Java book.  It's often best to start small then work up, even if you work up fast.  I like Java, but I enjoy Python much more.  OO programming isn't too hard as long as you remember that it is different.  You can't really compare it to scripting languages.  But I think that if you can get into it, you'll really enjoy it.

---

### Post by Unterseeboot_234 on 2007-02-06
I adore java. It can create an application with all the computer's resources available or an applet that has to stay within its own sandbox. And, it's not hard at all to convert your efforts back and forth between these two types of creations. Objects are really productive and even more so with inheritance -- the heirachy. Learn what an array is and you've got Objects under your belt. An array has similar items grouped together and the items are recalled with an index number. Objects are a fancy array with names to recall the items grouped within that Object.

For beginners there is maximum frustration just getting the Java Development Kit (JDK) installed and connected on their machine. Therefore, I highly recommend NetBeans 5.5, which is free for download. Another, simplier IDE also available from the NetBeans website is called BlueJ and is used for a lot of intro courses in java.

Java is "template" coding. That is, it uses a huge library to get your efforts going. Knowledge of those libraries (the API) is essential. NetBeans prompts you to import the proper pieces your software needs. Also, NetBeans lets you do textbook examples, something any other IDE won't let you do. Or, NetBeans lets you use their methods to save a whole lot of time -- but you have to know what it is NetBeans has already set up for you.

Games were always my fastest tutorial learning curve. "The Black Art of Java Game Programming" leads you through several simple game examples with advanced instruction about the inheritance, the objects, the variables. The current release of java is 1.6 and that revision is vast with a huge learning curve. "Black Art" is an older book. It pertains to 1.1 but it would be very instructive to peruse that book, along with BlueJ, or NetBeans and with those two IDEs they will warn you about "deprecicated" code. Go for it! Learn java, you can always take a look backwards at C/C++/C@.

---

### Post by phossal on 2007-02-06
I *adore* Java, too. It's a fun language that makes jumping into C or C++ a little easier. I'm a fan of the O'Reilly series rather than any other for Java, because they produce on title on virtually every API, every IDE, and all of its extra toys, like Tomcat. For that reason, I would recommend: *Learning Java* as the best book to get started with.

You'll find out over time that Java can exist in a lot of places, and using an applet is just way of deploying it. Really though, as was said in a previous post, applets have really fallen away from mainstream use as an overcomplicated method for accomplishing relatively simple goals. For the uses most people think of when considering applets, it's almost always better to use PHP, or another alternative. 

However, there are still plenty of corporations that deploy applets which run major programs, like Yahoo Chess, etc.

I've never found Java to be strong on the command line. It's simpler to use other languages, like perl or python. Java's strengths are API's like: Networking, JDBC (Database Connectivity). Java is a great language to build a mail client, a browser, music sharing program, etc. It's a great language to develop those kind of networking-heavy programs that can be run right from within its own folder, and distributed to virtually any machine with a JVM.

---

