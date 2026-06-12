---
title: "Permission denied in creating .jar file in java"
date: 2008-04-04
forum: Programming Talk
---

### Post by kingkong22 on 2008-04-04
I want to create a jar file that serves as a library. below is what I did:

After compile rb.java with javac succefully, try to create rb.jar
under root directory.

%>jar cvf  /rb.jar  /home/jiane/rb/*.class

it generated the following error msgs:

java.io.FileNotFoundException: /rb.jar (Permission denied)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:70)
        at sun.tools.jar.Main.run(Main.java:150)
        at sun.tools.jar.Main.main(Main.java:1022)

I have no idea about Permission denied, why ? even I used

%>sudo jar cvf  /rb.jar  /home/jiane/rb/*.class
this time, it said
sudo: jar: command not found

I totally get lost. can anyone help. please. thanks a lot.

---

### Post by themusicwave on 2008-04-04
:-(

Sorry when I first replied i missed where you tried to use sudo...so this reply was worthless.

---

### Post by nanotube on 2008-04-04
> **kingkong22 said:**
> I want to create a jar file that serves as a library. below is what I did:

After compile rb.java with javac succefully, try to create rb.jar
under root directory.

%>jar cvf  /rb.jar  /home/jiane/rb/*.class

it generated the following error msgs:

java.io.FileNotFoundException: /rb.jar (Permission denied)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:70)
        at sun.tools.jar.Main.run(Main.java:150)
        at sun.tools.jar.Main.main(Main.java:1022)

I have no idea about Permission denied, why ? even I used

%>sudo jar cvf  /rb.jar  /home/jiane/rb/*.class
this time, it said
sudo: jar: command not found

I totally get lost. can anyone help. please. thanks a lot.

try the following?:
```
jar cvf /tmp/rb.jar /home/jiane/rb/*.class
```

your rb.jar will be in /tmp, you can then move it to anywhere you want. does that work?

---

### Post by themusicwave on 2008-04-04
This post is useful...perhaps.

Do you have another program running that is holding a lock on that file? 

It's a long shot, but it can happen.

---

### Post by kingkong22 on 2008-04-04
%>jar cvf /tmp/rb.jar /home/jiane/rb/*.class

above works !

Now I copy it to /mylib/rbcore/

then, I created a test driver

import mylib.rbcore.*;
class test {
  rb t=new rb();
  ...
}

%> export CLASSPATH="/mylib/rbcore/rb.jar;."
%> javac test.java

it generated
test.java:1 package mylib.rbcore does not exist

I don't know why ? how to fix it ? thanks.

---

### Post by Zugzwang on 2008-04-05
> **kingkong22 said:**
> %>jar cvf /tmp/rb.jar /home/jiane/rb/*.class

above works !

Now I copy it to /mylib/rbcore/

then, I created a test driver

import mylib.rbcore.*;
class test {
  rb t=new rb();
  ...
}

%> export CLASSPATH="/mylib/rbcore/rb.jar;."
%> javac test.java

it generated
test.java:1 package mylib.rbcore does not exist

I don't know why ? how to fix it ? thanks.

This can't work. If you import "mylib.rbcore.*" then the package is only found if there's a jar (or zip) file in the classpath that contains the package. Open rb.jar with your favourite archive manager (ark or so). Is there a directory called "mylib" in it which in turn contains a directory called "rbcore" which contains classes such that their source files originally all started with "package mylib.rbcore;"? This has to be the case, otherwise the whole procedure fails.

Note that if you have source files starting with "package mylib.rbcore" then these have to be in the subdirectory "mylib/rbcore" of your project's source folder. See [the Java Turorial]("http://java.sun.com/docs/books/tutorial/java/package/index.html") for details.

Although most people here would disagree, using an IDE (like Netbeans) makes making JARs a whole lot easier.

---

### Post by kingkong22 on 2008-04-05
let me put it simple: rb.java is put under /home/jiane/rb/rb.java;
the tar file rb.tar being located under /mylib/rbcore/, the test client is put under /home/jiane/test.java. now rb.java looks like
//// rb.java
import java.until.*;
public class rb {
...
};
////

test.java as below
//// test.java
import mylib.rbcore.*;
import java.until.*;
class test {
...
}
 
so, how to make adjustment to rb.java & test.java so that I can make use of jar file rb.jar. please shows the steps to do. thanks.

---

### Post by Zugzwang on 2008-04-06
Ok, so step-by step.

[LIST]
[*]Move rb.java to /home/jiane/rb/mylib/rbcore/rb.java
[*]Alter rb.java to begin with "package mylib.rbcore;"
[*]Compile rb.java by running "javac mylib/rbcore/rb.java" from the directory "/home/jiane/rb/"
[*] Then make the JAR file. Never did this by hand, so read the tutorial.
[*] Check that in the JAR file there's a directory called mylib which has a subdirectory called rbcore which had a file named "rb.class" in it.
[*] Then add the JAR file to your classpath by calling ```

export CLASSPATH=$CLASSPATH:/home/jiane/rb/rb.jar
``` Note that your EXPORT command was incorrect since you didn't append your JAR to your classpath but simple rewrote it (so Java won't find that JRE libs anymore)
[/LIST]

Then you can use your classes during runtime and the compilation process.

If you have any questions, please read [the tutorial]("http://java.sun.com/docs/books/tutorial/java/package/index.html") first and then ask what you didn't understand.

---

### Post by kingkong22 on 2008-04-06
Well, Crystal clear !!! I got it working ! Thank you very much !!!

---

