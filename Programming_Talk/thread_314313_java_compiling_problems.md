---
title: "java compiling problems"
date: 2006-12-07
forum: Programming Talk
---

### Post by Arppa on 2006-12-07
i've tried to compile hello world in java but i haven't succeeded yet.
when i try to compile for example. gcj Hello.java, compiler says:

/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status

i just started java and i really don't know what is wrong with that.
i'd be very grateful if someone could help me :confused:

code:
public class Hello
{
        public static void main(String[] args)
        {
                System.out.println("Hello World!!\n");
        }
}

---

### Post by Tomosaur on 2006-12-07
Can you post your code up here? Please use the CODE tags so it's easy to read.

---

### Post by Ramses de Norre on 2006-12-07
You should post the code you are trying to compile, only that error message doesn't give much info..

---

### Post by Desi-Tek.com on 2006-12-07
@Arppa there is nothing wrong in ur code just save it as Hello.java
and compile it using this command
```
 javac Hello.java
 
```
and run it using
```
 java Hello 
```
btw why u r using gcj? use the sun's jdk it is free it is fast it is good :)

---

### Post by Ramses de Norre on 2006-12-07
You'll have to install sun's java first then:
```
sudo aptitude install sun-java5-bin sun-java5-jdk
```
Make sure to enable multiverse to be able to install these packages.

---

### Post by Arppa on 2006-12-07
thank you for helping me :)
i've used suns jdk on windows and it's terribly slow :(
takes about 20 secs to compile that code

---

### Post by Tomosaur on 2006-12-07
> **Arppa said:**
> thank you for helping me :)
i've used suns jdk on windows and it's terribly slow :(
takes about 20 secs to compile that code

That's probably more to do with windows than it is to do with the software :P

Sun's JDK is probably the best option - gcj is incompatible and incomplete. It causes more problems than it solves in my experience.

---

### Post by ruhar on 2006-12-07
If you are having performance problems with the jdk to compile a simple HelloWorld class, it has probably got more to do with the operating system/utilities than the jdk.  I have to write my java code on Windows at work, and I can't do any work unless the virus scan is completely turned off because it is configured to deep scan all java processes.  This causes all java processes to run extremely slow (1 minute to launch eclipse) That may be why your windows compilations are so slow.

---

### Post by Ramses de Norre on 2006-12-07
> **Arppa said:**
> thank you for helping me :)
i've used suns jdk on windows and it's terribly slow :(
takes about 20 secs to compile that code

Another reason to use linux ;)

---

### Post by Arppa on 2006-12-07
intresting becouse everything else runs smoothly, but when i try to compile everything freeze for 30 secs :S

---

### Post by kaamos on 2006-12-07
> **Arppa said:**
> i've tried to compile hello world in java but i haven't succeeded yet.
when i try to compile for example. gcj Hello.java, compiler says:

/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status

i just started java and i really don't know what is wrong with that.
i'd be very grateful if someone could help me :confused:

You are trying to compile your program into a linux binary. :) Use ```
gcj -C Hello.java
```
to create java bytecode (.class-files).

---

### Post by Arppa on 2006-12-07
problem solved. thank you all :)

---

### Post by vze4p6c2 on 2006-12-07
I suggest you use Windows for that.  They have less problems like that.  And since you won't be doing kernel programming in java, you probably will encounter more problems in linux.  They have perfect [NetBeans]("http://www.netbeans.org/") and [BlueJ]("http://www.bluej.org/") compiler for Java which are very stable, and have lots of documentation on functions as well as support (especially NetBeans).

From my point of view, linux supports very little of java, comparing to c.

Vlad

---

### Post by shining on 2006-12-08
If you have the java-gcj-compat package, you can compile java programs with gcj exactly the same than with sun java.
Just do:
```

javac Hello.java
java Hello

```

For choosing between gnu java and sun java (in case you have both java-gcj-compat and sun-java5-jdk installed), use update-java-alternatives.
But it shouldn't make any difference for simple programs.

---

### Post by Circus-Killer on 2006-12-08
i agree with the other posts stating to rather use sun's java rather than gcj. as they said, sun's version offers greater compatibility. personally, i would never develop anything in java without using sun's version. just my opinion, but it also looks im not alone on this opinion.

---

### Post by Ramses de Norre on 2006-12-08
> **vze4p6c2 said:**
> I suggest you use Windows for that.  They have less problems like that.  And since you won't be doing kernel programming in java, you probably will encounter more problems in linux.  They have perfect [NetBeans]("http://www.netbeans.org/") and [BlueJ]("http://www.bluej.org/") compiler for Java which are very stable, and have lots of documentation on functions as well as support (especially NetBeans).

From my point of view, linux supports very little of java, comparing to c.

Vlad

Kernel programming in java? How would you do that?

And I program quiet a lot in java on Linux and know people who develop java programs on Linux for living and it certainly works at least as well as windows.
I'd never even think about going to windows for developing..
And the java API is available online and IDE's as eclipse give you at least as much information about available classes/methods/... as any other windows IDE.

---

