---
title: "Java, Eclipse, and the Devil (Need help :S)"
date: 2009-04-14
forum: Programming Talk
---

### Post by Geistanon on 2009-04-14
Now, just a preface: I am not a programmer per se. My knowledge (although expanding rapidly since I installed Ubuntu) is still limited. That said, let me get on to my issue...

I'm on Ubuntu 8.10.

I have been running Java scripts for some time now. In order to do these scripts, I had to run the 'make' command to compile them, then run the program through the shell 'sh ./{name}'. 

I have Java JRE and JDK updated to the most recent build.

What I could not do, however, was compile new scripts. I was told that I was to save the code, via a text editor, as a .java, then use 'make' to compile. I found numerous issues with this -- the first being that new scripts were not compiling. Then I found that the environment variables for Java were not set -- JAVA_HOME and CLASSPATH. Setting these changed nothing.

All through this, my program continued to run.

I found reference to the program Eclipse being able to help with compiling new programs. I installed it and IMMEDIATELY AFTER DOING SO, all of the aforementioned commands produce mass errors (around 290), most of which are along the lines of:

```
Syntax error, type parameters are only available if source level is 5.0
```

Uninstalling Eclipse changed nothing. Changing the compliance level in Eclipse to 6.0 (the current version of Java) did nothing. Using 'sudo aptitude reinstall make' did nothing.


How can I fix this?

---

### Post by tinny on 2009-04-14
Eclipse is an IDE [http://en.wikipedia.org/wiki/Integrated_development_environment](http://en.wikipedia.org/wiki/Integrated_development_environment)

Therefore all (well most) tasks that you undertake as a programmer can be executed from within this environment.

Have you tried compiling and running your code from within Eclipse?
 

Also you should have your code within an eclipse project 

E.g.

File > New > Java Project

Then select "Create project from existing source"

---

### Post by tinny on 2009-04-14
This may be of interest to you

[http://eclipsetutorial.sourceforge.net/totalbeginner.html](http://eclipsetutorial.sourceforge.net/totalbeginner.html)

---

### Post by soltanis on 2009-04-14
Post the output of

```

javac -version

```

?

---

### Post by Geistanon on 2009-04-14
> Have you tried compiling and running your code from within Eclipse?

No I haven't. I'm trying that now, but I'm in pretty far over my head. I'll sit through the 3 hours of tutorial eventually but for now I think I'll stick to help documentation.

I've still been unable to figure out either how to compile or run from Eclipse. The Run As.. Java Application function doesn't do anything regardless what file I try, nor if I just run the project.

Like I said, I'm pretty new to this, haha.


> **soltanis said:**
> Post the output...
```
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.
```

---

### Post by jespdj on 2009-04-14
I recommend that you forget about Eclipse for now, and follow [Sun's Java tutorials](http://java.sun.com/docs/books/tutorial/). Especially have a look at the [Hello World](http://java.sun.com/docs/books/tutorial/getStarted/cupojava/unix.html) tutorial, which explains step by step how to write, compile and run your first Java program.

Eclipse is an IDE (Integrated Development Environment) which contains a lot of functionality for Java developers, but if you're a beginner who doesn't really know a lot about programming and compiling source code, then using Eclipse only makes it more complicated for you. Start with writing small programs using a simple text editor (gedit for example, which is the default text editor on Ubuntu) and compile and run your programs from a terminal window.

Note: Java source code files are **not** called Java 'scripts'. Don't call it a 'script', because this is confusing. Note that the programming language **JavaScript** is something totally different from Java.

---

### Post by johnl on 2009-04-14
> **Geistanon said:**
> No I haven't. I'm trying that now, but I'm in pretty far over my head. I'll sit through the 3 hours of tutorial eventually but for now I think I'll stick to help documentation.

I've still been unable to figure out either how to compile or run from Eclipse. The Run As.. Java Application function doesn't do anything regardless what file I try, nor if I just run the project.

Like I said, I'm pretty new to this, haha.



```
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.
```

It looks like eclipse has installed a different version of Java which has been set as the default.

You can change this by running:

```

sudo update-alternatives --config javac

```

Which will give you a menu indicating what is installed, what is currently the default, and prompt you to change it.

You may need to do this as well for the 'java' command and other java tools.  I think there was a way to configure all of this at once, but I can't seem to find it right now.  Hopefully someone else has the info on that.

---

### Post by HotCupOfJava on 2009-04-14
I may be totally off-base and if so, I apologize in advance. You have referred to your code as "scripts". These wouldn't be JavaScript, would they? Because JavaScript and Java are NOT the same thing.....

---

### Post by tamas305 on 2009-04-14
This is an alternate way, a way I believe is easier (this also works for installing the java plugin for firefox 3).

1) Boot up Ubuntu and open up a terminal (Applications --> Accessories -- > Terminal)

2) Type 

```
sudo su
```

3) Enter your password, you will not see what you enter (a security feature)

4) Type

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

5) Agree to the license agreement and let it install, restart firefox, eclipse or any other program that needs JAVA and it should work

-tamas

---

### Post by Geistanon on 2009-04-15
> Which will give you a menu indicating what is installed, what is currently the default, and prompt you to change it.

You may need to do this as well for the 'java' command and other java tools. I think there was a way to configure all of this at once, but I can't seem to find it right now. Hopefully someone else has the info on that.

This worked perfectly!

```
There are 4 alternatives which provide `javac'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/bin/javac
          2    /usr/bin/ecj
          3    /usr/bin/gcj-wrapper-4.3
*+        4    /usr/lib/jvm/java-gcj/bin/javac

Press enter to keep the default[*], or type selection number: 1
Using '/usr/lib/jvm/java-6-sun/bin/javac' to provide 'javac'.
```

I switched from 4 to 1.


I'll definitely look into the tutorials on the Sun-Java site. Eclipse was making sense on a fundamental level but technically was very far over my head.


Thanks for the help everyone!

---

