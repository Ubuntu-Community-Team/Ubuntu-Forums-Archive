---
title: "Java: printf Question"
date: 2010-06-03
forum: Programming Talk
---

### Post by derekeverett on 2010-06-03
I started playing around with printf today. I have a question.

The following code does not compile:

```

import java.util.Date;

public class FormatFun
{
	public static void main(String args[])
	{
		System.out.printf(new Date());
	}
}

```

Yet when I change the statement in main to println it works no problem. Why is this?

Thanks

---

### Post by Some Penguin on 2010-06-03
Because you're using it incorrectly.  Go read the Javadoc.  

[http://java.sun.com/j2se/1.5.0/docs/api/java/io/PrintStream.html](http://java.sun.com/j2se/1.5.0/docs/api/java/io/PrintStream.html)

---

### Post by derekeverett on 2010-06-03
I figured it out. For anybody reading this that might actually want some sort of useful answer, the problem was my usage of printf. It is very similar to C.

This does compile and work
```

import java.util.Date;

public class FormatFun 
{
	public static void main(String args[])
	{
		System.out.printf("%tH%<tM", new Date());
	}
}

```

---

