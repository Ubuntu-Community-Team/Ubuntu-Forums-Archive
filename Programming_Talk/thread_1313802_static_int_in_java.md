---
title: "static int in java"
date: 2009-11-04
forum: Programming Talk
---

### Post by swappo1 on 2009-11-04
Hello,
I am trying to make a variable static in Java.  In C++ I would do: static int j = 0;  How would I do this in Java?  Here is the code I am using.
```
public class Practice
{
		
	public static void main(String[] args)
	{
		int i = 10;
		
		sum(i);
		
		sum(i);


	}
	
	public static void sum(int i)
	{
		static int j = 0;
		
		j += i;
		
		System.out.printf("j = %d%n", j);
	}
}
```
I keep getting an illegal start of expression error.

---

### Post by AlexZaim on 2009-11-04
Haven't been programming in java since this summer, but i think that a solution will be making j a class field (namely *practice*'s). static keywords are for classes if i'm not mistaken.

---

### Post by pbrockway2 on 2009-11-04
You can't use "static" that way in Java.  So, as Alex says, make *j* a field.  

It would be a field of whatever class sum() was a method of: which may or may not be where your main() method is located.  And the field would be a class (or static) field or an instance (nonstatic) field depending on whether sum() was static or not.

---

### Post by Tomato-kun on 2009-11-04
check out this [http://en.wikipedia.org/wiki/Final_%28Java%29](http://en.wikipedia.org/wiki/Final_%28Java%29) .

---

### Post by jespdj on 2009-11-04
Tomato-kun, what does this have to do with 'final'?

```
public class Practice
{
	private static int j = 0;

	public static void main(String[] args)
	{
		int i = 10;
		sum(i);
		sum(i);
	}

	public static void sum(int i)
	{
		j += i;
		System.out.printf("j = %d%n", j);
	}
}

```

---

