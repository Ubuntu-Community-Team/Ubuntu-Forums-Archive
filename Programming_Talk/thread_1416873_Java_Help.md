---
title: "Java Help"
date: 2010-02-26
forum: Programming Talk
---

### Post by Michaeljs1990 on 2010-02-26
I'm pretty new to programming and am enjoying it quite a lot. The projects they give us to do for class are way to easy so i decided to make a program for fun. however when i try and compile this program to test it out i get...```

package javaapplication1;

/********************************************
*Michael Schuett
*2/25/10
*Java
*This is my first semi-big java program
***********************************************/
import java.util.Scanner;

public class Main
{
    public static void main(String[] args)
    {
    String input= h;

    Scanner stdIn = new Scanner(System.in);

    System.out.println("Hello, Welcome to MMath Beta 0.1");
    System.out.println("What would you like to do? (for help enter h): ");
    input = stdIn.next();
    if (h);
        {
        System.out.print("type in add to add or subtract numbers." + '\n');
        System.out.print("type in mult to multiply or divide."     + '\n');
        System.out.print("only 2 currently available in Beta 0.1"  + '\n');
        }
    }
}


```

and i get the error code
Exception in thread "main" java.lang.RuntimeException: Uncompilable source code - cannot find symbol
  symbol:   variable h
  location: class javaapplication1.Main
        at javaapplication1.Main.main(Main.java:15)
Java Result: 1
BUILD SUCCESSFUL (total time: 2 seconds)

can anyone explain how i can get the input 'h' from the user to bring up the if statement? Sorry if this is a stupid question.

---

### Post by JCoster on 2010-02-26
```
String input= h;
```

..should be:
```
String input= "h";
```

..assuming that you want the variable input to equal the character "h".

Similarly:
```

 if (h);
        {
        System.out.print("type in add to add or subtract numbers." + '\n');
        System.out.print("type in mult to multiply or divide."     + '\n');
        System.out.print("only 2 currently available in Beta 0.1"  + '\n');
        }
    }

```

..should be:
```

 if (input.equals("h");
        {
        System.out.print("type in add to add or subtract numbers." + '\n');
        System.out.print("type in mult to multiply or divide."     + '\n');
        System.out.print("only 2 currently available in Beta 0.1"  + '\n');
        }
    }

```

Although, this would be better:
```

package javaapplication1;

/********************************************
*Michael Schuett
*2/25/10
*Java
*This is my first semi-big java program
***********************************************/
import java.util.Scanner;

public class Main
{
    public static void main(String[] args)
    {
    Scanner stdIn = new Scanner(System.in);

    System.out.println("Hello, Welcome to MMath Beta 0.1");
    System.out.println("What would you like to do? (for help enter h): ");

    String input = stdIn.next();
    if (input.equals("h"));
        {
        System.out.print("type in add to add or subtract numbers." + '\n');
        System.out.print("type in mult to multiply or divide."     + '\n');
        System.out.print("only 2 currently available in Beta 0.1"  + '\n');
        }
    }
}

```

---

### Post by Michaeljs1990 on 2010-02-26
WOW thank you so much !! thats exactly what i needed!

It's like a 50 pound weight is lifted off you when you final don't see that error message.

---

### Post by JCoster on 2010-02-27
Haha no problem at all.
It's nice to finally help someone rather than be asking someone for help!
Please mark thread as solved
JC

---

