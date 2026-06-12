---
title: "Java... how to start. what to use?"
date: 2006-02-15
forum: Programming Talk
---

### Post by yb1011 on 2006-02-15
Hey guys,
I am a complete noob and am trying to learn java. I installed the following using Automatix:

Sun java 1.5 jre
Sun java 1.5 sdk

I have never done programming before and want to start off with java. So how do I start?... I have the book "Java 2.0 Complete Reference " and would want to start..but dont know where to or how to...
Can somone help me? 
Thank you for the help.
(Sorry... I know my question must sound too stupid... but that is me when it comes to programming etc)

---

### Post by yb1011 on 2006-02-15
Ok. I have looked around and I see that Eclipse is a popular application. But when I try to apt-get I get 
Couldnt find package eclipse...

How can I get eclipse?
thanks guys

---

### Post by zakili on 2006-02-16
Eclipse is in universe
[http://packages.ubuntu.com/breezy/devel/eclipse-sdk](http://packages.ubuntu.com/breezy/devel/eclipse-sdk)
so you can get it with apt or you can download it from eclipse.org

---

### Post by pertti on 2006-02-16
[QUOTE=yb1011]I have the book "Java 2.0 Complete Reference " and would want to start..but dont know where to or how to...[/QUOTE]

The "Complete Reference" part sounds a bit scary for a beginner ;) . You could also take a look at [Thinking in Java]("http://www.mindview.net/Books/TIJ/"), which is available for free.

---

### Post by Heli0s on 2006-02-16
If you want to start programing i sugest you buy a book for beginners. A refrence guide is good if you want to look somthing up or if you already know some programing.

I'm personaly a great fan of the O'Reilly books so i would sugest something like [Learning Java]("http://www.oreilly.com/catalog/learnjava3/"). Afcourse there are a lot of diffrent books out there.

Also Sun has a nice tutorial at [there site]("http://http://java.sun.com/docs/books/tutorial/"). 

As a editor i would start with something like JEdit. Tho eclipse is a great tool, you need to learn how to work with that. Where is JEdit (or any othere text editor) lest you focus on Java.

Hope this helps, and happy coding ;)

---

### Post by yb1011 on 2006-02-16
thank you all for replying. I will use the links givinn and see if I can get the orielly book suggested. Thank you.
As suggested i have installed jedit and  now seem to have a problem running java. for instance i wrote a basic hello program:

> class HelloWorld
{ public static void main (String args[]) { System.out.println("Hello World"); } }


and when I try to run
javac HelloWorld

it says 
bash: javac: command not found

Does that mean java is not installed?

Also.. I have Anjuta too...can it be used to compile and run the program instead of using jedit and the terminal? 

Im sorry that I have so many questions guys. Im really lost here and would really need your advise. Thank you for your support so far and hope Id get through this...

---

### Post by Revert on 2006-02-16
As I recall, JEdit requires a few plugins to integrate the Java compiler (I may be wrong, but that's how I remember it).  Actually, JEdit always seemed like somewhat of a pain.  I'd suggest giving SciTE a try.

This [online book's]("http://greenteapress.com/thinkapjava/") pretty decent for starting out with.

---

### Post by steve.horsley on 2006-02-16
For a beginner learning java, I would like to suggest a small IDE called BlueJ. It has all the basics you might want - editor, compile button that highlights the error in the editor, debugger, but also has a "workbench" with the ability for you to make objets and then manually call methods on them and inspect their state.

See [www.bluej.org](www.bluej.org) 
and [http://www.bluej.org/papers/1999-11-JOOP4-blue-env.pdf](http://www.bluej.org/papers/1999-11-JOOP4-blue-env.pdf)
Edit: That's not the one I meant - see this one: [http://c2.com/doc/oopsla89/paper.html](http://c2.com/doc/oopsla89/paper.html)

Also, hava a look at Sun's Java Tutorial. It's huge and thorough. Find it at java.sun.com.

---

### Post by yb1011 on 2006-02-16
Guys.. thank you for your input.
As suggested I have downloaded that jar file from the site and when I do 
java -jar bluej-212.jar

It starts the installer and says :
Directory to Install ---- select dir
Java (jdk) Directory ---  select dir

where should I install and what would be java jdk directory be?

By the way when I do
> sudo update-alternatives --config java
I get the following 
> There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
      3        /usr/local/jre1.5.0_06/bin/java
*     4        /usr/lib/j2re1.5-sun/bin/java

Looks like im in the last stage of getting this running... please suggest! thanks!

---

### Post by kvorion on 2006-02-17
I had also asked for help about an IDE for Java and I was suggested to use BlueJ and I am liking it. I would suggest you also start off using BlueJ, then after you are proficient enought maybe you can switch to Netbeans or Eclipse.

You can find Eclipse in your synaptic packet manager, the packet name is eclipse-jdt

But before you go on with any IDE......do try a couple of simple programs directly from your command line. Write the code in your favourite text editor and save it as a .java file.

```
javac classname.java
```

```
java classname
```

If that is working fine then you can move ahead. I dont know why you got a bash error saying it could not locate javac. It could mean that java is not installed, but then you do say that you have installed it from automatix.

Make sure that you type the commands properly and include the .java after the filename. It should work.

About anjuta.....you can use it for C/C++ and not Java. Start off with BlueJ for Java

---

### Post by healychan on 2006-02-17
Since Java is a pure object-oriented language, I suggest you try to get some idea about object-oriented design. Object-oriented programming is really powerful in a software engineering point of view. It improves reusability, integrity...etc

You should learn the tools such as "javadoc" as well. "javadoc" helps you to produce API document of your program easily.

To understand the syntax of Java, the Sun web site is a good place to start.

In my opinion, an IDE is not a must for a beginner. Using simple text editor such as emacs gives you less overhead. But of course when you start to write a big program or graphical user interface, an IDE can save you lots of time.

There are so many resources in the Sun web site includes tutorials and examples. You can also download the API reference(in html format) from Sun web site. It is very useful since Java provides a rich set of lib.  I always use the API reference when programming Java, especially when doing GUI programming.

---

### Post by steve.horsley on 2006-02-18
[QUOTE=yb1011]Guys.. thank you for your input.
As suggested I have downloaded that jar file from the site and when I do 
java -jar bluej-212.jar

It starts the installer and says :
Directory to Install ---- select dir
Java (jdk) Directory ---  select dir
where should I install and what would be java jdk directory be?
[/QUOTE]
Instal where you like, really. I put mine in /home/steve/data/java/bluej. I have a feeling it may save preferences to its install directory, so I don't suggest installing one shared copy outside of your home dir.

The java JDK directory will be the directory where the jdk you want bluej to use is. Mine is /opt/jdk1.5.0_05. You could have multiple JDK versions installed. You must tell Bluej which one to use (even if you only have one). The BlueJ installer normally finds it so you just have to click the OK button though. When you upgrade your JDK, you may hvae to re-run the Bluej installer to point it to the new path.
> 

By the way when I do
[QUOTE]sudo update-alternatives --config java
I get the following 
> There are 4 alternatives which provide `java'.

Selection Alternative
-----------------------------------------------
1 /usr/bin/gij-wrapper-4.0
+ 2 /usr/lib/jvm/java-gcj/bin/java
3 /usr/local/jre1.5.0_06/bin/java
* 4 /usr/lib/j2re1.5-sun/bin/java 

Looks like im in the last stage of getting this running... please suggest! thanks![/QUOTE]
This is not required for running BlueJ, because it uses the JRE from the JDK to do its stuff. This is for choosing which java runtime to use when **not** running under BlueJ. 

I'm not sure what 1 is at all.
2 is the open-source java runtime that Ubuntu shops with. You are better off using a Sun or IBM runtime, really.
Number 3 looks most recent Sun jre to me. I suggest you choose this one.
4 looks like an earlier JRE.

What ths script does is set which java you use by changing the link in /etc/alternatives. The script didn't even find the jre that I installed from Sun, so I modified the link in /etc/alternatives myself. The way the alternatives work is that there is a java in /usr/bin, but this just points to the one in /etc/alternatives. This one should be changed to point to whichever alternative you want to use. Here is mine:
> steve@StevesPC:~$ which java
/usr/bin/java
steve@StevesPC:~$ ls -l /usr/bin/java
lrwxrwxrwx  1 root root 22 2005-10-15 00:10 /usr/bin/java -> /etc/alternatives/java
steve@StevesPC:~$ ls -l /etc/alternatives/java
lrwxrwxrwx  1 root root 29 2005-10-20 17:21 /etc/alternatives/java -> /opt/jdk1.5.0_05/jre/bin/java
steve@StevesPC:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)
steve@StevesPC:~$


---

### Post by knalle on 2006-02-18
1 /usr/bin/gij-wrapper-4.0
+ 2 /usr/lib/jvm/java-gcj/bin/java
3 /usr/local/jre1.5.0_06/bin/java
* 4 /usr/lib/j2re1.5-sun/bin/java


man, you need the j2sdk (Software Developer Kit) not the j2re (Java Runtime Engine).

install the SDK not the JRE to get javac working in bash.

---

### Post by kvorion on 2006-02-18
Someone please tell me more about javadoc. About the point that an IDE is not really required for a beginner, I guess that is true in the very beginning.

One thing I liked about BlueJ is that it makes you think in an OO fashion right from the beginning. Simple to use, you can start off by designing off all the classes you want in the beginning and add your code to them later. You can instantiate objects of different classes independently; which would be really nice for unit testing. One more thing is that it automatically generates the API reference for you project. 

I dont know about other IDE's and how they implement these things, but I found BlueJ nice, and I loved the fact that its such a small jar file :)

---

### Post by LordHunter317 on 2006-02-18
[QUOTE=healychan]It improves reusability, integrity...etc[/quote]OOP is about neither.  It's simply a concept for modeling behaviors.  It doesn't improve reusability at all.

> You should learn the tools such as "javadoc" as well. "javadoc" helps you to produce API document of your program easily.No, he should, as he won't be writing libraries anytime soon, and unless you're going to do J2EE and need xdoclet, there's no point. 

Regular comments suffice just as well for the commenting he'll need to do.

[quote=kvorion]Someone please tell me more about javadoc. About the point that an IDE is not really required for a beginner, I guess that is true in the very beginning.[/quote]Don't worry about javadoc for now.  Really.

---

### Post by gabri3d on 2006-07-25
i've to do an exercice in java that i've to use a .jar file with some classes implemented, how i can set the path to use that .jar file?

thanks

---

### Post by mlind on 2006-07-25
> **gabri3d said:**
> i've to do an exercice in java that i've to use a .jar file with some classes implemented, how i can set the path to use that .jar file?

thanks

Include it on build classpath.

---

### Post by gabri3d on 2006-07-25
thanks for the answer :) but if i'm not using and IDE?

---

### Post by mlind on 2006-07-25
> **gabri3d said:**
> thanks for the answer :) but if i'm not using and IDE?

javac -classpath /path/to/jarfile.jar sourcefile.java

---

