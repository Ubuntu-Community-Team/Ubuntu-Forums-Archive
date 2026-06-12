---
title: "Beginner Java Question"
date: 2008-06-09
forum: Programming Talk
---

### Post by tdrusk on 2008-06-09
I have to use the /t to format my text. Hypothetically, I wrote
```
/* File Name: HelloWorld.java
 *
 * Purpose: Greeting the World.
 *
 * Name: your name goes here
 *
 */
public class HelloWorld
{
    // display the message hello World... on the screen
    public static void main(String[] args)
    {
        System.out.println("Hello World!");
    }
}

```

How do I add /t to format the text?
}

---

### Post by NormR2 on 2008-06-09
Not sure what you mean by /t. Do you mean \t (the tab char)?
The \ is called the escape character and has special usage. It tells the compiler to handle the char following the \ in a special way. For a following t it requests a tab char, for an n a newline char, for " to treat it as an ordinary char and not String delimiter, etc

How do you want to "format" your text? The println() method writes to stdout. Add a \t to the String your writing with println() and observe the output.

---

### Post by tdrusk on 2008-06-09
> **NormR2 said:**
> Not sure what you mean by /t. Do you mean \t (the tab char)?
The \ is called the escape character and has special usage. It tells the compiler to handle the char following the \ in a special way. For a following t it requests a tab char, for an n a newline char, for " to treat it as an ordinary char and not String delimiter, etc

How do you want to "format" your text? The println() method writes to stdout. Add a \t to the String your writing with println() and observe the output.
I'm sorry. I meant \t. That was my original problem.
I didn't think it would be as simple as just adding it in the "\tHello World!"
Is that proper?

---

### Post by NormR2 on 2008-06-09
Depends what you want the output to look like. Try it and see if its what you want.

---

### Post by tdrusk on 2008-06-09
> **NormR2 said:**
> Depends what you want the output to look like. Try it and see if its what you want.
Looks fine to me. Thanks for your help guys.

---

