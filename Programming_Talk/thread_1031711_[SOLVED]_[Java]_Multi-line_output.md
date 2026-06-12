---
title: "[SOLVED] [Java] Multi-line output?"
date: 2009-01-05
forum: Programming Talk
---

### Post by fiddler616 on 2009-01-05
I'm still trying to learn Java, and have run into an un-Googlable stumbling block:
How do you do multi-line printing?
In Python I would either do
[PHP]print '''Line 1
Line 2
Line3'''[/PHP]
or
[PHP]print "Line 1 \
Still Line 1 \n\
Line 2 \n\"
[/PHP]
What's the best, most Java-esque (or whatever the heck the equivalent of "Pythonic" is) way of doing that?

Thank you.

---

### Post by mike_g on 2009-01-05
IIRC you can just do:
```
System.out.print("Line1\nLine2\nLine3");
```

---

### Post by shadylookin on 2009-01-05
System.out.print("LINE1\nLINE2\nLINE3\n");

or 
System.out.println("line1");
System.out.println("line2");
System.out.println("line3");

\n will give you a new line.

---

### Post by rlzyoner on 2009-01-05
System.out.println("Line one " + "Line two" + "Line three");

---

### Post by dwhitney67 on 2009-01-05
> **rlzyoner said:**
> System.out.println("Line one " + "Line two" + "Line three");

+1

Or:
```

System.out.println("Line one " +
                   "Line one continued\n" +
                   "Line two.");

```

---

### Post by rlzyoner on 2009-01-05
Yep,... dwhitney67 explained that better than me :)

---

### Post by fiddler616 on 2009-01-05
I was opening my mouth to bash my communication skills, but thank you dwhitney and rlzyoner for solving the problem I meant :) 
(Though I am kind of surprised there's not a more compact way of doing that. Never mind, this is Java--why use two words when [s]one[/s] six will do?

---

### Post by mike_g on 2009-01-05
> **dwhitney67 said:**
> +1

Or:
```

System.out.println("Line one " +
                   "Line one continued\n" +
                   "Line two.");

```

Personally, I never used println for multiline output. You could have a simple rule - add new lines where appropriate. Or have a complicated one where you where you have to remember all those variable conditions. Tbh I cant see the benefit. Maybe I'm missing something here?

---

### Post by fiddler616 on 2009-01-05
> **mike_g said:**
> Personally, I never used println for multiline output. You could have a simple rule - add new lines where appropriate. Or have a complicated one where you where you have to remember all those variable conditions. Tbh I cant see the benefit. Maybe I'm missing something here?
I'm not perfectly sure I'm following you on this, but isn't:
```
s.o.p("1, which is reaaaaaaaaaaaaaaaaaaaaaaaaally long\n" + 
"2, which is also reaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaly long\n" +
"3"); 
```
better than
```
s.o.p("1, etc.");
s.o.p("2, etc.");
s.o.p("3, etc.");
```
(Keeping in mind I compressed the verbosity of System.out.print(ln))? That's a bunch of extra typing that can add up...

---

### Post by mike_g on 2009-01-05
I would say yes, but you can do that System.out.print or System.out.println. The difference is that with println you have to remeber how it behaves under different conditions. Its not much, but I think its an unnecessary waste of brain space.

---

### Post by fiddler616 on 2009-01-05
> **mike_g said:**
> I would say yes, but you can do that System.out.print or System.out.println. The difference is that with println you have to remeber how it behaves under different conditions. Its not much, but I think its an unnecessary waste of brain space.
True, I guess it boils down to cluttered brain vs. cluttered code, both of which are very arguable.

---

### Post by mike_g on 2009-01-05
Not quite. print produces no more cluttered code than println. and vice versa

---

### Post by pcman312 on 2009-01-06
While one version is not necessarily "better" than the other, I did just write a simple test to see if one was significantly faster than the other. Basically, it comes down to a question of whether string concatenation is faster than outputting to the console.

Here's the code that I used:

```
public class Sandbox
{
	public static void main(String[] args)
	{
		long start = System.currentTimeMillis();
		
		for (int i = 0; i < 1000000; i++)
		{
			// System.out.println("My line!\n" + "my second line\n" + "my third line\n");
			System.out.println("My line!");
			System.out.println("my second line");
			System.out.println("my third line");
		}
		
		long end = System.currentTimeMillis();
		
		System.out.println(((double)(end - start)) / 1000);
	}
}
```

I got approximately 12 seconds for the string concatenation vs 35 seconds for the individual outputs. This doesn't surprise me since output is very slow compared to other operations. Although, it would not surprise me if these results would change if there are other variables introduced to the test, such as additional computations, complex string concatenations (with variables instead of other strings like I put for example), overloading java's string pool, etc.

Granted, these results do say that each System.out.println call takes approximately 0.000012 seconds (12 microseconds). By comparison, just the loop of i to 1,000,000 (one integer addition and an integer comparison operation per loop) takes a total of 0.006 seconds, with each loop taking about 0.000000006 seconds (6 nanoseconds). Quite a difference.

Just some food for thought (which many of you probably already know).

---

### Post by fredscripts on 2009-01-06
I would never do in Java System.out.print ("....\n").

Here is an article my programming teacher wrote and explained in class a few weeks ago:

[http://www.onlamp.com/pub/a/onlamp/2006/08/17/understanding-newlines.html](http://www.onlamp.com/pub/a/onlamp/2006/08/17/understanding-newlines.html)

---

