---
title: "DrJava problems with java.util.scanner"
date: 2010-01-31
forum: Programming Talk
---

### Post by sunnybeach on 2010-01-31
I recently installed DrJava on Ubuntu 9.10. I have java jdk version "1.6.0_15". 
I've gotten the DrJava compiler to work after manually placing the tools.jar file in the edit/preferences tab.

However, when I compile a simple program that requires importing java.util.scanner I get this error: 
"cannot find symbol 
symbol : class scanner 
location : package java.util"

I've already read this thread:[http://ubuntuforums.org/showthread.php?t=874500page=2](http://ubuntuforums.org/showthread.php?t=874500page=2)
but the answers seem to be for eclipse, not for DrJava. 

I am required to use DrJava for a course I am taking, and can't switch to eclipse.

after reading this thread: [http://ubuntuforums.org/showthread.php?t=307464](http://ubuntuforums.org/showthread.php?t=307464)

I tried to do what post #3 said but when i did the gedit command to /etc/jvm the file that popped up was blank. I typed in usr/lib/jvm/java-1.6.0-sun to the file and saved it, but nothing happened when I went back into DrJava. I've now reverted the /etc/jvm to it's original blank state.

I would really appreciate some help here as I have searched extensively for answers to my problem but seem to only be finding answers for importing into eclipse and not DrJava.

---

### Post by Some Penguin on 2010-01-31
You do mean Scanner, not scanner, yes?

---

### Post by sunnybeach on 2010-01-31
> **Some Penguin said:**
> You do mean Scanner, not scanner, yes?

Yes I do, sorry about the typo.

---

### Post by Some Penguin on 2010-01-31
Can you show the exact import line in question?

AFAICT, DrJava claims to be able to support Java 5 and 6, and the Scanner class has been part of the language definition since Java 5 (inclusive), so there shouldn't be any problems here.

---

### Post by sunnybeach on 2010-01-31
I seem to have solved the problem; I wasn't typing the commands in properly. Honest newbie mistake. :)
Thanks for your help.

---

### Post by *Raz0r* on 2010-01-31
Oh **** I get the same error Cannot Find The Symbol, its so annoying and I also dont know what to do

---

### Post by sunnybeach on 2010-01-31
Well what happened to me was that I wasn't using proper syntax. I was entering java.util.scanner (undercase) instead of java.util.Scanner (uppercase S for scanner).

---

