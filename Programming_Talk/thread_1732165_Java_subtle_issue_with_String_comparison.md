---
title: "Java: subtle issue with String comparison"
date: 2011-04-17
forum: Programming Talk
---

### Post by alexmoca on 2011-04-17
SOURCE:

```

        String a = "a";
        String b = "a";
        String c = new String("a");
        String e = new String("a");

        System.out.println(a == b);
        System.out.println(a == c);
        System.out.println(a == e);
        System.out.println(c == e);

```OUTPUT:

```

true        <<<<< WHY?
false
false
false

```Question: Why?

So [FONT=Courier New]c[/FONT] and [FONT=Courier New]e[/FONT] are instantiated with the [FONT=Courier New]new[/FONT] operator. Therefore, they refer to different memory addresses and afaik this is true for all objects instantiated with this operator. But what is the process behind creating the Strings [FONT=Courier New]a[/FONT] and [FONT=Courier New]b[/FONT]? I was a bit surprised to find that [FONT=Courier New]a == b[/FONT] returned[FONT=Courier New] true[/FONT].

---

### Post by Some Penguin on 2011-04-17
'Interning'.

See [http://en.wikipedia.org/wiki/String_interning]("http://en.wikipedia.org/wiki/String_interning") and [http://javatechniques.com/public/java/docs/basics/string-equality.html]("http://javatechniques.com/public/java/docs/basics/string-equality.html")

---

