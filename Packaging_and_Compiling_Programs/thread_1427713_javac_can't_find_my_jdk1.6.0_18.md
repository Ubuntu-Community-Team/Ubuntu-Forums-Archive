---
title: "javac can't find my jdk1.6.0_18"
date: 2010-03-11
forum: Packaging and Compiling Programs
---

### Post by honey toast on 2010-03-11
Hi

I manually installed jdk1.0.6_18 on my karmic system. I'm using eclipse for building java apps. When I tried to compile my java program using the standard javac foo.java I received a msg like this:  	Code:
 	the program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
javac: command not found 
I know the next step would be to select the 'sun-java6-jdk', but there is already a javac exe file inside of my /opt/java/32/jdk1.6.0_18/bin file. I want to use that one. How can I use that one? 
And so you all know, I have already tried javac -classpath . foo.java and I received the same msg as above. Thanks .

---

### Post by dxxvi on 2010-03-13
if you

echo $PATH

do you see /opt/java/32/jdk1.6.0_18 there?

---

