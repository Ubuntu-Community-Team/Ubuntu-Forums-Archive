---
title: "java prob"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by jackgu1988 on 2008-09-29
hi! i am new to this forum and i think it's very cool! i am using ubuntu 8.04.1

i have a problem trying to compile a java prog... here is the prog:

> import java.util.*;
public class test3
{
public static void main(String[] args)
{
float a,b;
Skanner sc = new Scanner(System.in);
System.out.print("\nInput a\n");
a=sc.nextFloat();
System.out.print("\nInput b\n");
b=sc.nextFloat();
System.out.print("\n\nTOTAL=" + (a+b) + "\n");
}
}

and here is what happens when i type javac test3.java :

> Found 2 semantic errors compiling "test3.java":

     7. Skanner sc = new Scanner(System.in);
        ^-----^
*** Semantic Error: Type "Skanner" was not found.


     7. Skanner sc = new Scanner(System.in);
                         ^-----^
*** Semantic Error: Type "Scanner" was not found.

what have i done wrong? is it ubuntu that can not compile it? thank you!

---

### Post by issih on 2008-09-29
You have simply put Skanner instead of Scanner...note the k where the c should be. The compilers output is then telling you that it can't find a class called Skanner in any of the files or libraries you have told it to look in...because you made a typo.

Ubuntu certainly can compile java..no problem at all.

---

### Post by jackgu1988 on 2008-09-29
sorry i noticed it! thanks about that! but it can not recognize the 2nd scanner neither... i also fixed the 1st one and the same error appears!

> Found 2 semantic errors compiling "test3.java":

     7. Scanner sc = new Scanner(System.in);
        ^-----^
*** Semantic Error: Type "Scanner" was not found.


     7. Scanner sc = new Scanner(System.in);
                         ^-----^
*** Semantic Error: Type "Scanner" was not found.
thank you

---

### Post by The Cog on 2008-09-29
Those error messages look odd to me. And your code (after correcting "Skanner") compiles OK for me.

What version of java are you using? What is the output of these two?
java -version
javac -version

I get this:
> steve@Titch:~$ javac -version
javac 1.6.0_10-beta
steve@Titch:~$ java -version
java version "1.6.0_10-beta"
Java(TM) SE Runtime Environment (build 1.6.0_10-beta-b25)
Java HotSpot(TM) Server VM (build 11.0-b12, mixed mode)


If the java version doesn't say HotSpot then I guess you haven't got Suns java. In that case I suggest you install Suns JDK. It's in the repositories.

---

### Post by jackgu1988 on 2008-09-29
the output is:

> jack@jack-laptop:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Server VM (build 1.6.0_0-b11, mixed mode)
jack@jack-laptop:~$ javac -version
Jikes Compiler - Version 1.22 - 3 October 2004
Copyright (C) IBM Corporation 1997-2003, 2004.
- Licensed Materials - Program Property of IBM - All Rights Reserved.
Originally written by Philippe Charles and David Shields of IBM Research,
Jikes is now maintained and refined by the Jikes Project at:
<http://ibm.com/developerworks/opensource/jikes>
Please consult this URL for more information and for reporting problems.
sorry but i am new to linux and i don't realy know what to do now so i can fix this... thank you

---

### Post by jackgu1988 on 2008-09-29
just fixed it! this thread helped a lot: [http://ubuntuforums.org/showthread.php?t=76702]("http://ubuntuforums.org/showthread.php?t=76702")... thank you!

---

