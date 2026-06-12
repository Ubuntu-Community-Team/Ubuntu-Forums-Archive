---
title: "'Class names are only accepted if annotation processing is explicitly requested'"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by irime on 2012-02-10
Hi-
I'm running xubuntu 11.10 and have been working on a simple java program for a school assignment. Had the program working just fine on the computers at school, then tried to do the same at home and got this error:

amanda@Marvin:~$ cd /home/amanda/Desktop
amanda@Marvin:~/Desktop$ javac NameInStars.jav
error: Class names, 'NameInStars.jav', are only accepted if annotation processing is explicitly requested
1 error
amanda@Marvin:~/Desktop$ 

The class name matches the name the file is saved under, all the capitalization is accurate, and the file extension is accurate.  Also tested with a sample program that came with Crimson Editor and got the same error, so I know it's not an issue with the program I was writing. When checking what java I had on my system, I fourd Java 6 openJDK, java 6 sun, and Java 7 openJDK.  Also have java 6 sun JDK but unsure where (terminal says it is installed).  The following is what's apparently running:

amanda@Marvin:~$ javac -version
javac 1.6.0_26
amanda@Marvin:~$ java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)

Is it just a matter of clearing out some of the assorted extra versions of java, or is something else the cause?

---

### Post by Toz on 2012-02-10
Hello and welcome to the forums.

Try renaming NameInStars.jav to NameInStars.java. See: [http://docs.oracle.com/javase/tutorial/getStarted/problems/index.html]("http://docs.oracle.com/javase/tutorial/getStarted/problems/index.html").

---

### Post by irime on 2012-02-10
Looks to have done it! Guess I'll have to watch for that with crimson editor now that I know, had noticed it had saved it that way but I didn't think it would gum things up that badly. Thanks for the help :D

---

