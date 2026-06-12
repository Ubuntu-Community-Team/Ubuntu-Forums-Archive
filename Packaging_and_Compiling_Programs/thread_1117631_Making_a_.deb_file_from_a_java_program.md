---
title: "Making a .deb file from a java program"
date: 2009-04-06
forum: Packaging and Compiling Programs
---

### Post by HawkST on 2009-04-06
How can I create a deb file from java source code?
Is it possible to include the necessary images for the progam in the deb file as well?
Thanks very much to anyone who can help me

---

### Post by 0cton on 2009-04-10
java is a programming langauge that runs into a virtual machine
its needs the JVM to run the .class (compiled java programs)
and sicne its not native code you can't make a java .deb just as you can't make a java .exe (you can link the JVM with the the class file but its still not a compiled exe I am not sure if there arent any java compilers but it would defeat the purpose)
Anyway a simple answer is you can;t do that
just like you can't make a python .deb  as its interpretted
(correct me if i am wrong not completely sure if you cant indirectly pack it but you still need a native executable)

---

### Post by hessiess on 2009-04-10
It should be possible, maby try installing the compiled java code into /usr/bin and creating a shell script to run it woith the virtual mashean.

---

### Post by 0cton on 2009-04-12
> **hessiess said:**
> It should be possible, maby try installing the compiled java code into /usr/bin and creating a shell script to run it woith the virtual mashean.

well yes as i've said it still needs a native executable that will start the java one
Netbeans its made in java but has a starter AFAIK

---

### Post by SlCKB0Y on 2009-04-14
> **0cton said:**
> 
just like you can't make a python .deb  as its interpretted
(correct me if i am wrong )

:roll:

Yea, you're wrong. You can put anything you like in a deb file, it just wont run if they either dont have jre installed, or you dont make it a dependency

Just like you can put .py files in a deb, or bash scripts.

Soooooo wrong

---

### Post by HawkST on 2009-04-17
> **SlCKB0Y said:**
> :roll:

Yea, you're wrong. You can put anything you like in a deb file, it just wont run if they either dont have jre installed, or you dont make it a dependency

Just like you can put .py files in a deb, or bash scripts.

Soooooo wrong

Thank god for that!

Whats the best way to go about this?
Any useful links that might help me out? - I have tried searching but so far no luck!

---

### Post by HawkST on 2009-04-20
Apologies for the double post, but is there any chance someone could help with this?
I kind of need to know by Thursday... ;)

---

### Post by HawkST on 2009-04-22
Anyone? Please!?

---

