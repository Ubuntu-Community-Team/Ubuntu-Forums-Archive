---
title: "javac class issue can't run &quot;hello world&quot; JDK 8"
date: 2018-10-18
forum: New to Ubuntu
---

### Post by insert.memories.here on 2018-10-18
I'm in a tough spot trying to learn how to run java in ubuntu while knowing nothing about linux. I'm wrangling with two languages at once. :KS

So when I'm trying to compile my .java file into class, this shows up. (What does this mean?)
```
~/myProject$ javac Hello.java
Hello.java:5: error: cannot find symbol
            System.out.printIn("Hello World, from Ubuntu");
                      ^
  symbol:   method printIn(String)
  location: variable out of type PrintStream
1 error

```

...here's another try...
```
~/myProject$ javac Hello
error: Class names, 'Hello', are only accepted if annotation processing is explicitly requested
1 error

```

Here's my java file: Hello.java
```
public class Hello
{
        public static void main(String args[])
        {
            System.out.printIn("Hello World, from Ubuntu");
        }
}
```

and finally, when I try to run it...
```
~/myProject$ java Hello
Error: Could not find or load main class Hello
Caused by: java.lang.ClassNotFoundException: Hello

```

I'm fried.

---

### Post by spjackson on 2018-10-18
There is no [FONT=courier new]printIn[/FONT] method. I think you meant [FONT=courier new]println[/FONT]. The error when you try to run it is to be expected; you cannot run something that you have failed to compile.

---

### Post by insert.memories.here on 2018-10-18
What character is that specifically? Is that a #1?
```
public class Hello
{
        public static void main(String args[])
        {
            System.out.print1n("Hello World, from Ubuntu");
        }
}
```

Result:
```
~/myProject$ javac Hello.java
Hello.java:5: error: cannot find symbol
            System.out.print1n("Hello World, from Ubuntu");
                      ^
  symbol:   method print1n(String)
  location: variable out of type PrintStream
1 error

```

...or is that a lowercase l as in "larry"?
```
public class Hello
{
        public static void main(String args[])
        {
            System.out.println("Hello World, from Ubuntu");
        }
}
```

Result:
```
~/myProject$ javac Hello.java
Hello.java:1: error: error while writing Hello: /home/doughnuts/myProject/Hello.class
public class Hello
       ^
1 error

```

At least I didn't do anything in the terminal badly...
I just want to test my jdk installation to see if it installed properly, before actually learning java. I haven't really ran through the coding of hello world yet so I'm pretty sure something is badly written.

---

### Post by spjackson on 2018-10-18
> **insert.memories.here said:**
> 
...or is that a lowercase l as in "larry"?

Yes.
> 
```
public class Hello
{
        public static void main(String args[])
        {
            System.out.println("Hello World, from Ubuntu");
        }
}
```

Result:
```
~/myProject$ javac Hello.java
Hello.java:1: error: error while writing Hello: /home/doughnuts/myProject/Hello.class
public class Hello
       ^
1 error

```

I can't see anything wrong with that. It's perfectly correct java that compiles and runs for me when copied & pasted from above.

You can get a similar error if file permissions prevent you writing the output:
```

Hello.java:1: error: error while writing Hello: Hello.class (Permission denied)
public class Hello
       ^
1 error

```
but then it explicitly says "(Permission denied)". So I don't know why you are getting that output, I'm afraid.

---

