---
title: "Cannot Compile Java Code From Command Prompt"
date: 2010-05-26
forum: Packaging and Compiling Programs
---

### Post by esya on 2010-05-26
[SIZE=2]I cannot compile any java code from Command Prompt.

When I write java or javac I am getting this error:
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object

I tried to set environments variables. Then I check. I gave different results for root and normal user.

echo $JAVA_HOME // As normal user
/usr/lib/jvm/java-6-sun-1.6.0.20/bin/java

echo $JAVA_HOME // As a root
/usr/lib/jvm/java-6-sun-1.6.0.20/

And this is my environment file
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-6-sun-1.6.0.20/bin/"
JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.20/

I think I did something wrong while I was trying to set environments variables but I could not figure out. And I am using eclipse with same Java version, it is working good.[/SIZE]

---

### Post by GregBrannon on 2010-05-26
Eclipse works, and since Eclipse IS a Java program, you know that Java works. In fact, Eclipse is probably started from a script that starts the Eclipse bytecode from the command line, so Java programs CAN be run from the command line.  But for some reason, YOU can't.

Post the entire command line results, starting with the command you're entering.

---

### Post by esya on 2010-05-26
First of all thanks for reply.

Actually I am compiling my java codes by using Eclips. Before I could not open eclipse. It was showing the starting icon then it was closing. Then I add -vm
/usr/lib/jvm/java-6-sun-1.6.0.20/bin line to the eclipse.ini file. It doesn't have any problem now. 

But I need to use keytool to create key pair and certificate when I wrote keytool to the terminal I got error.

> 
-desktop:~$ keytool
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object
Then I tried only java command to see I have a problem with java or not. I got error.

> 
-desktop:~$ java
Error occurred during initialization of VM
java/lang/NoClassDefFoundError: java/lang/Object


---

### Post by GregBrannon on 2010-05-26
Thanks for the clarifications.

Now that you've defined the problem better, you might find someone who can help.  Yes, it appears that your Java installation is messed.  When one types 'java' at a command prompt as you did, the response should be the same as if one had typed 'java -?' or 'java -help'.

Is it a path problem?  Unfortunately, I don't know.  You shouldn't have had to mess with that, but you did . . .

If you don't get a genius to respond with quick fix soon, you might try reinstalling Java, but there should be an easier way.

Good luck.

---

