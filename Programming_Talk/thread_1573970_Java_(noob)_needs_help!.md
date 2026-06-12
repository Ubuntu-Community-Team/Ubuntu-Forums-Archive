---
title: "Java (noob) needs help!"
date: 2010-09-13
forum: Programming Talk
---

### Post by fallenshadow on 2010-09-13
I only started Java today and Ive been trying to run this simple code.

```
//Java basic example

public class myclass
{

	public static void main (String[] args)
	{
		System.out.printIn("Hello");
	}
	
}
```

However it spits out an error message:

```

myclass.java:8: error: The method PrintIn(String) is undefined for the type PrintStream

```

I can't find the solution to this anywhere on the internet.

---

### Post by endotherm on 2010-09-13
look at the line noted in your error message, and look back at your book or online tutorial closely. the message is telling you that there is no such thing as System.out.printIn, and it is right. look a little closer and you will find the issue.

---

### Post by fallenshadow on 2010-09-13
I looked at the tutorial and said to myself (WTF the code is the exact same). However I knew something had to be different... then I saw the In looked more like ln.

I could have swore I heard my teacher say "In" today but I guess he said "ln". :D

I presume its ln as in meaning new line... right?

---

### Post by endotherm on 2010-09-13
> **fallenshadow said:**
> I looked at the tutorial and said to myself (WTF the code is the exact same). However I knew something had to be different... then I saw the In looked more like ln.

I could have swore I heard my teacher say "In" today but I guess he said "ln". :D

I presume its ln as in meaning new line... right?
indeed, it is "println" for "print line"

if it makes you feel any better, once you are started really programming, you will likely use editors and tools that will underline errors like that for you automatically, so while it is a growing pain, don't let it get you down. the exercise reading and interpreting error messages is a skill you pick up quickly when doing it by hand.

---

