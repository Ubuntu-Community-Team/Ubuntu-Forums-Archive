---
title: "learning java, already compiled, what next?"
date: 2008-06-26
forum: Packaging and Compiling Programs
---

### Post by rtoot3 on 2008-06-26
i just downloaded jdk, and i made a file called Hello.java the contents say this

```
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, world!");
    }
}
```

i compile it, and it turns into Hello.class. so then i tried opening it with firefox, it didnt work it just came up as a download. what do i open it with?

?_?

---

### Post by WW on 2008-06-27
You have create a Java program, but not a complete applet.  You can run it from the terminal like this:
```

$ ls
Hello.java
$ javac Hello.java 
$ ls
Hello.class  Hello.java
$ java Hello
Hello, world!
$ 

```
Check out [this thread](http://ubuntuforums.org/showthread.php?t=713622). (Since you already have java installed, you can skip to step 1.)  A good place to ask questions about programming in java is in the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forum.

EDIT: Also check out [this thread](http://ubuntuforums.org/showthread.php?t=842060), which was started within a few hours of this one.  Are you and "cheechandchong" the same person?  Or maybe you are in the same Java class? (No pun intended. :))

---

### Post by rtoot3 on 2008-06-27
thanx, and no, were not the same person

---

