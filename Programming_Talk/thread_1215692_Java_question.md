---
title: "Java question"
date: 2009-07-17
forum: Programming Talk
---

### Post by old_dope on 2009-07-17
I have never attempted to learn a fully fledged Programming language but a friend of mine has persuaded me to have a go at learning Java. Told me to download JDK 6 with Netbeans. But i looked in Synaptic and found that both

sun-java6-bin + sun-java6-jre were pre-installed. Would this be adequate for me to start?

Also, i would prefer not having to learn via a terminal/command line so is there a GUI i could use?

Finally, is there a simple command i could type into a terminal to see if everything is ready for me to start learning Java?

Thanks everyone

---

### Post by Finalfantasykid on 2009-07-17
I love java its an amazing language.

To see if you are all set up you can type...

```
java -version
```

...if that comes out with anything really then you are set to go, but the newest JRE is 1.6.14 so if it says something less than that then you might want to consider upgrading.

As for a GUI, Eclipse is an excellent IDE for programming in Java(as well as many other languages like c/c++ and python, etc.).  

```
sudo apt-get install eclipse
```

Unfortunatly Ubuntu hasn't updated their repositories for eclipse for some time now, and so we are stuck with 3.2(the newest is 3.5).  However you can get the newest version straight from the eclipse.org website.

---

### Post by ddrichardson on 2009-07-17
No, you need a JDK too, which if you install eclipse you will get.  Frankly, if you're beginning, Eclipse and Netbeans are overkill - [BlueJ]("http://www.bluej.org/") is much better for getting your head around OOP which is the part most struggle with rather than syntax.

---

### Post by HotCupOfJava on 2009-07-17
If you do decide to use Netbeans, might I suggest you NOT grab the one from the repositories. It is very clunky and will probably frustrate you. Go to Netbeans' website instead and download from there. They have good instructions for installing on Ubuntu. 

I personally feel that for just starting off in Java you might should use a simple text editor and the command line. If you already have the sun-java6-jdk installed, you should be good to go. Learning how to write your programs with a simple text editor will help you learn the syntax correctly (none of the IDE auto-complete stuff), and compiling and running your code on the command line will help you get a grasp on the way the compiler and java virtual machine actually work.

Just a thought.

---

### Post by old_dope on 2009-07-17
Thanks for the help and advice everyone. Cheers OD

---

### Post by old_dope on 2009-07-17
Have just been and opened a terminal and typed:

java -version

and got the following response:

OldDope@OldDope-desktop:~$ java -version
javaversion "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)
OldDope@OldDope-desktop:~$

If i'm good to go, i don't suppose anyone would like to buddy up and help just to get me started? Can pm me if you like. Thanks

---

### Post by jespdj on 2009-07-17
Download NetBeans from [http://www.netbeans.org](http://www.netbeans.org). Installing it is easy, just run the downloaded installer in a terminal window:
```
sudo sh <name of downloaded file>
```
It will show you an installation wizard. After installation, you can find NetBeans in the Applications / Programming menu.

---

### Post by old_dope on 2009-07-18
As stated previuosly i opened a terminal and typed: 

java -version

and got the following response:

OldDope@OldDope-desktop:~$ java -version
javaversion "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)
OldDope@OldDope-desktop:~$

I thought i was ready to go!

But when i tried to compile a source file i typed the following at the prompt: javac HelloWorldApp.java

And was informed that:

The program 'javac' can be found in the following packages:
* gcj-4.2
* java-gcj-compat-dev
* jikes-sablevm
* kaffe
* sun-java6-jdk
* jikes-kaffe
* gcj-4.3
* cacao-oj6-jdk
* jikes-classpath
* openjdk-6-jdk
* ecj
* sun-java5-jdk
* jikes-sun
Try: sudo apt-get install <selected packages>
bash: javac: command not found

Could someone tell me where i go from here please. Just don't want to make any mistakes. Big thanks

---

### Post by apoth on 2009-07-18
sudo aptitude install openjdk-6-jdk

---

### Post by ddrichardson on 2009-07-18
> **apoth said:**
> sudo aptitude install openjdk-6-jdk
Java consists of more than one part, the JRE and the JDK - Java Runtime Environment runs Java bytecode, Java Development Kit contains the javac compiler which creates said bytecode. To run Java you need a JRE, to develop, you need a JDK too.

I'm probably going to get flamed for this but what the hey.

I know openjdk has been certified now but as he has sun-java6-jre installed I have found it better, especially when following guides and tutorials, to use sun-java6-jdk atleast not to mix the two JRE and JDK.

There's nothing more disheartening when learning to code than thinking you have your head round a concept than finding your code wont compile, then spending hours to find the situation is relieved by using Sun's JDK..

Here's some links that will assist you in learning Java too:
[http://www.javaomatic.com/](http://www.javaomatic.com/)
[http://www.wikijava.org/wiki/Main_Page](http://www.wikijava.org/wiki/Main_Page)
[http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)

If you join the Open University's free Open Learn project, then this course is good, although not actually Java, its a good introduction to modelling:
[http://openlearn.open.ac.uk/course/view.php?id=2674](http://openlearn.open.ac.uk/course/view.php?id=2674)

---

### Post by old_dope on 2009-07-18
Thanks both

---

### Post by old_dope on 2009-07-18
Success! I'm on my way. Thanks again everyone :D

---

