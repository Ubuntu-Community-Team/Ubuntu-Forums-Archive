---
title: "need java help!"
date: 2008-06-27
forum: Programming Talk
---

### Post by rtoot3 on 2008-06-27
i just downloaded jdk, and i made a file called Hello.java the contents say this

```
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, world!");
    }
}
```

i compile it, and it turns into Hello.class. so then i tried opening it with firefox, it didnt work it just came up as a download. what do i launch it with?

?_?

---

### Post by LaRoza on 2008-06-27
You run it with:

```

~$cat p.java
public class p
{
    public static void main(String[] args)
    {
        System.out.println("Hello world");
    }
}
~$javac p.java
~$java p
Hello world
~$

```

Writing applets is different.

---

