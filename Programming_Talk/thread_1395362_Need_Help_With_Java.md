---
title: "Need Help With Java"
date: 2010-01-31
forum: Programming Talk
---

### Post by *Raz0r* on 2010-01-31
Hey guys, I have installed JRE and JDK on my Ubuntu 9.10 But I keep getting the following error. "Cannot Find The Symbol" Does anyone know how to get around this so I can run my program ? I heard that you might have to edit system path .bashrc in my home directory. But I would need simple step by step help for that.

---

### Post by Axos on 2010-01-31
I need more detail to help you. What are you trying to do? Which JRE and JDK did you install, Sun or OpenJDK?

---

### Post by Reiger on 2010-01-31
Being unable to find a symbol of any kind in programming means a polite &#8220;you made an error; you misspelt something&#8221;.

At least 99.5% of the time. The other 0.5% of the time it is a genuine deployment issue, but by the time you hit _those_ you would probably phrase your opening post a whole lot differently. (Much more technical, and detailed.)

---

### Post by pedrotuga on 2010-01-31
AFAIK that's a compile error. Are you trying to compile something?

In particular, that means that, in your source, you have a variable that does not exist (is not defined, the compiler can't find it) in the current scope.

---

### Post by Finalfantasykid on 2010-01-31
If I can remember correctly, I have had this error message before when I was using an older jre(like 1.4, and compiling some 1.5/1.6 compliant code).  Since those newer JREs added some extra syntax stuff and more methods, the older JRE did not recognize some of the syntax.

Maybe just check to see which version of java you are using...

```
java -version
```

---

### Post by TheTank on 2010-02-01
In addition to what Finalfantasykid wrote, you might also like to check what version you are compiling with, as java allows you to compile versions <=[current version]
So even if you use 6.0 but your compiler is set to 1.4 you could add in 6.0 stuff, yet still get that error.

It would help to know what tools you are using, else we can only guess.

---

### Post by *Raz0r* on 2010-02-01
I got the most current version JDK 6. And the program is so simple that there is no mistakes, its just a Hello World

class Hello
{
    public static void main (String[] args)
    {
        System.out.printIn("Hello World");
    }
}

---

### Post by Zugzwang on 2010-02-01
> ***Raz0r* said:**
> I got the most current version JDK 6. And the program is so simple that there is no mistakes, its just a Hello World

```

class Hello
{
    public static void main (String[] args)
    {
        System.out.printIn("Hello World");
    }
}

```


Oh, there is a mistake: It should be "println" instead of "printIn".

---

### Post by *Raz0r* on 2010-02-01
Oh thank you some much man, I was going through all the forums and Java In Easy Steps Book and still could not find anything. I though it said In and not ln, 

Once again cheers, just starting my first course with java programming. Thats why getting silly errors

---

### Post by TheTank on 2010-02-01
I'd suggest you get Eclipse or NetBeans, they can really help you find those kind of bugs.

---

