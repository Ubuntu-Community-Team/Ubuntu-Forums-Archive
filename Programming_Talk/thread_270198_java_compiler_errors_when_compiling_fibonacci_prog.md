---
title: "java compiler errors when compiling fibonacci program"
date: 2006-10-02
forum: Programming Talk
---

### Post by baldy1324 on 2006-10-02
i am writing a program in java to do the fibonacci sequence.
here is the code:```
class main
{
        public static void main(String[] args)
        {
                int n = 350;
                double first = 0;
                double second = 1;
                System.out.print(first);
                System.out.print("    ");
                System.out.print(second);
                System.out.print("    ");

                while (n>0)
                        {
                                double third = first + second;
                                first = second;
                                second = third;
                                System.out.print(third);
                                System.out.print("    ");
                                n--;
                        }
        }
}

```
when i compile it with javac there are no errors
when i run java to run/interpert it it gives the following error:
```
Exception in thread "main" java.lang.NoClassDefFoundError: main/class

```
any ideas?

---

### Post by meng on 2006-10-02
Perhaps try naming your class something other than main? Weird name for a class.

---

### Post by neilp85 on 2006-10-02
Not sure what's wrong, I just copy and pasted your code exactly and it worked perfect for me. Did you make sure to name your file main.java?

---

### Post by Seine on 2006-10-02
class name must match filename. E.g. public class DogStar { ... } must be in a file called DogStar.java

---

### Post by yaaarrrgg on 2006-10-02
when you run it, type:

```

java main

```

you don't need a .class extension.

---

### Post by Seine on 2006-10-02
:KS That'll be it

> java.lang.NoClassDefFoundError: main/class

Means you have typed **java main.class** and java interprets this as package *main*, class *class*.

---

