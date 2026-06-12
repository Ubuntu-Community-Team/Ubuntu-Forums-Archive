---
title: "Java doesn't work"
date: 2006-02-06
forum: Programming Talk
---

### Post by feathers on 2006-02-06
Whatever I do, I always get this message in my simple "hello world" programme:
Exception in thread "main" java.lang.NoClassDefFoundError: Main/class

My sourcecode:

```


class Main 
{ 
    public static void main (String[] args) 
   { 
      System.out.println( "Hello, world!" );
   } 
}

```
This is the command to start it: java Main.class
I installed various jre's and sdk's and set them with update-alternatives. The funny thing is, it works in Eclipse, I mean I can start the class in Eclipse but I cannot do this on the console. This is the case with several kubuntu computers I have checked.
Who can help? Thanks!

---

### Post by Viro on 2006-02-06
You start it by typing java Main (without the .class).

---

### Post by feathers on 2006-02-07
Thanks, that was exactly the problem.

---

