---
title: "GNU Java Question"
date: 2006-06-25
forum: Programming Talk
---

### Post by bieber on 2006-06-25
On July 1, I'm going to be starting AP Computer Science online (Florida Virtual School).  It should be an easy enough course, but it requires use of Java.  I was worried at first I'd be stuck having to use Sun's proprietary Java, but it seems that GCJ should be plenty mature enough for me to be able to write and run the code I'll need to for the course (it'll be only *very* simple programming stuff).  So, I decided it would be a good idea to go ahead and try out gcj, to make sure I at least know how to work it, before starting the class, and it's a good thing I did, because it's looking like I don't.

I copied the following into a file called hello.java
```
class HelloWorld {

    public static void main (String args[]) {
    
      System.out.print("Hello, World!");
  }

}


```

Then, I tried compiling with gcj using the syntax I would if I were compiling C or C++.  That is, ```
gcj -o hello hello.java
```
That, however, gets me this error message
```

/usr/lib/gcc/i486-linux-gnu/4.1.0/../../../../lib/crt1.o: In function `_start':../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status

```

Then, I tried compiling to a .class file and then executing it, as the tutorial I got the Hello World program out of said to do.  The command ```
javac hello.java
``` ran without errors, and left HelloWorld.class in the directory.  However, running ```
java hello.class
``` presented this error at runtime. ```
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld.class
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: HelloWorld.class not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)

```

So, does anyone know exactly what I need to do to get this to work?  I'm sure I'm probably just missing something simple, I just don't know what it is, and I can't seem to find it (it seems all the beginner Java tutorials out there use Sun's java...)  Thanks in advance for any assistance.

---

### Post by LordRaiden on 2006-06-26
Try 
```
java hello
```

---

### Post by bieber on 2006-06-26
Gives the same errors.

---

### Post by tageiru on 2006-06-26
You need to add a --main=Class (where Class is the class with the main method) argument to gcj when compiling native binaries.

---

### Post by LordHunter317 on 2006-06-26
[QUOTE=bieber]Gives the same errors.[/QUOTE]You may have to specify a classpath of '.' but you shouldn't have to do this.

This is exactly why I don't ever bother with gcj.

---

### Post by bieber on 2006-06-26
Okay, now it works, thanks.  Now, will I be able to count on this to compile fairly large programs written for Sun's Java? (Apparently a part of each week's lessons is analyzing a fairly sizable program.  Although, what with it being a beginning course and all, it's probably none too big...)

Also, is there any way to get Applets working as well?

---

### Post by ynef on 2006-06-26
For your information, you should always name your source files the exact name as the class they will contain. So, in your case the file shouldn't be hello.java, it should've been HelloWorld.java. This is enforced in the Sun world, and you will most likely run into trouble if you submit files for your class if they do not follow that naming standard.

As for applets, I wouldn't hold my breath -- neither AWT or Swing (the two main components of all graphical applications and applets) are not working[1]. Also, the gcj project claims that they will have a Java 1.5 compatible system working in the relatively near future[2].

[1] [http://www.gnu.org/software/gcc/java/status.html](http://www.gnu.org/software/gcc/java/status.html)
[2] [http://www.gnu.org/software/gcc/java/](http://www.gnu.org/software/gcc/java/)

---

### Post by yaaarrrgg on 2006-06-26
[QUOTE=bieber]I was worried at first I'd be stuck having to use Sun's proprietary Java, but it seems that GCJ should be plenty mature enough for me to be able to write and run the code I'll need to for the course (it'll be only *very* simple programming stuff).[/QUOTE]

If that's your only worry, I'd recommend sticking with the Sun tools.  Sun is gradually moving Java to open source...

---

### Post by bieber on 2006-06-26
If Sun makes Java free software, I'll use it.  But at the moment, it's still proprietary, and I'm not sure if it's ever going to be truly free, since Sun seems hellbent on maintaining just a little more control over it than would be possible to make it free.

Anywho, you said they're hoping to get a system compatible with Java 1.5 soon.  Isn't Sun on like 5.0 already?  Is this likely to be a problem for me?

And finally, someone said files should be named exactly as the class they contain--does this mean each file can only contain one class?  That sounds as if it would make large object oriented projects have ungodly numbers of iiles in them...

---

### Post by yaaarrrgg on 2006-06-26
[QUOTE=bieber]If Sun makes Java free software, I'll use it.  But at the moment, it's still proprietary, and I'm not sure if it's ever going to be truly free, since Sun seems hellbent on maintaining just a little more control over it than would be possible to make it free.[/QUOTE]

I tend to prefer open source tools too... although there are pros and cons to having one entity control a standard.  I think Sun is mostly afraid that the Java will fragment into many different flavors (like linux).

[QUOTE=bieber]Anywho, you said they're hoping to get a system compatible with Java 1.5 soon.  Isn't Sun on like 5.0 already?  Is this likely to be a problem for me?[/QUOTE]

I'm not sure why, but Sun decided to start calling version 1.5 "version 5.0".  I don't think Sun's naming choices make much sense at times, and are confusing.

[QUOTE=bieber]And finally, someone said files should be named exactly as the class they contain--does this mean each file can only contain one class?  That sounds as if it would make large object oriented projects have ungodly numbers of iiles in them...[/QUOTE]

That's not entirely true... you can put multiple classes in the same file.  Just don't declare them "public."

---

### Post by LordHunter317 on 2006-06-26
[QUOTE=bieber]If Sun makes Java free software, I'll use it.  But at the moment, it's still proprietary,[/quote]Then you might as well not take the class.

No, seriously.  GCJ is not up to task for some things you may have to do in the class.  At any rate, no one in the Java community cares about GCJ in the least bit, so if you run into problems with it, everyone but the GCJ community is going to say, "Why aren't you running Sun's JDK (or BEA's or IBM's)?"

> since Sun seems hellbent on maintaining just a little more control over it than would be possible to make it free.They have their reasons.

> Anywho, you said they're hoping to get a system compatible with Java 1.5 soon.  Isn't Sun on like 5.0 already?  Is this likely to be a problem for me?Java 5 is the marketing name for Java 1.5.  GCJ is totally inadequate for any Java 5 stuff.  

> And finally, someone said files should be named exactly as the class they contain--does this mean each file can only contain one class?One public class, yes.  You can include multiple package-scoped classes in a single file, but it's not recommended practice.

> That sounds as if it would make large object oriented projects have ungodly numbers of iiles in them...Yes, they do.  File layout follows a strict convention based on namespace (package) too.

---

### Post by bieber on 2006-06-26
[QUOTE=LordHunter317]Then you might as well not take the class.

No, seriously.  GCJ is not up to task for some things you may have to do in the class.  At any rate, no one in the Java community cares about GCJ in the least bit, so if you run into problems with it, everyone but the GCJ community is going to say, "Why aren't you running Sun's JDK (or BEA's or IBM's)?"
[/QUOTE]

I largely doubt I'll be needing any features that GCJ can't provide.  I'm talking about an, IIRC, 14 week course, with each week having a title like "Setting up your environment," "Variables," "Loops," "Control Structures," and so on.  I believe the most sophisticated was "Singly Linked Lists."  If it turns out that I *really* need Sun's Java, I'll install it on a machine, but I'm avoiding it if at all possible.

On a sidenote, this post editor inserted italics bbcode tags when I instinctively hit Ctrl+i.  That's awesome.

---

### Post by LordHunter317 on 2006-06-26
[QUOTE=bieber]I largely doubt I'll be needing any features that GCJ can't provide.[/quote]Yes, but the toolchain issues alone could be enough headache to simply not bother.

---

### Post by bieber on 2006-06-26
Toolchain issues?  I run gcj just like I would with g++ or gcc, with the addition of --main=class.  Hell, once I get into actual coding, I'll probably find out that there's an Emacs command that will work just as well.  If not, I'll write a makefile...

---

### Post by ynef on 2006-06-27
Ok, sure, your computer will be "tainted" and all the software won't be released under the GPL -- however, if the course is anywhere near good, it'll make use of the latest additions to the Java language like Generics and other things that were introduced in Java 1.5 (or 5). Also, the new "foreach" loop should be mentioned and the Scanner class for input. The language has matured quite a bit, and if you have even one assignment on GUIs, the GNU implementation won't cut it.

Seriously -- it's one package[1] and its dependancies and you can remove them after the course is done.

[1] [http://packages.ubuntu.com/dapper/devel/sun-java5-jdk](http://packages.ubuntu.com/dapper/devel/sun-java5-jdk)

---

### Post by Stromham on 2006-06-27
hello fellow flvs.net user :P are you a true floridian or one of the hurricane victims. any i have ap history, math, and eng. i gotta tell you those welcome calls are a pain, but last time i checked there is no computer class avilable to students and courses last 24 weeks. :?

---

### Post by bieber on 2006-06-27
You're probably right on course time (not that I intend to spend anywhere near as much time as they want me to on the damn thing), but they definitely have computer courses.  Programming, AP CS, and a couple other simple computer courses, IIRC.

ynef, there shouldn't be any GUI programmng involved, and nothing other than the most basic of language features.  I'm not too worried about compatibility.

---

