---
title: "java string comparison"
date: 2009-10-31
forum: Programming Talk
---

### Post by swappo1 on 2009-10-31
I am comparing a JOptionPane string with a String and I can't get figure out why the two are not equal.

```
import javax.swing.*;

public class Practice
{
	public static void main(String[] args)
	{
		String input;
		String quit = "quit";
		
		input = JOptionPane.showInputDialog("input = ");
		
		if(input == quit)
			System.out.println("input = quit");
		else
			System.out.println("input != quit");
	}
}
```
When I enter quit into the dialog box I am getting the output: input != quit.  Yet, quit == quit.  Why does this happen?  Does JOptionPane format the string differently?

---

### Post by swappo1 on 2009-10-31
I figured it out.  Java doesn't compare strings directly.  I used input.equals("quit") to return true or false.

---

### Post by mattyB on 2009-10-31
> **swappo1 said:**
> I figured it out.  Java doesn't compare strings directly.  I used input.equals("quit") to return true or false.

Don't forget to cover your bases in the event that you receive 'Quit' as input. ;-)

---

### Post by kavon89 on 2009-10-31
> **mattyB said:**
> Don't forget to cover your bases in the event that you receive 'Quit' as input. ;-)

Yea, consider equalsIgnoreCase() because equals() checks case.

---

### Post by pbrockway2 on 2009-10-31
> **swappo1 said:**
> I figured it out.  Java doesn't compare strings directly.  I used input.equals("quit") to return true or false.

Not only does == not compare strings directly: it doesn't compare strings **at all**.  == compares reference values (and primitive values and it compares them the same way).  If the values are equal you get "true" otherwise you get "false".

There can be lots of different strings that are made up of the same sequence of characters.  (like the 5th and the 12th words in the previous sentence).  It might well be the case that there are different reference values each pointing to a different string made up of the same sequence of characters.  In such a case == will evaluate to false.

The broader notion of "made up of the same sequence of characters" is what is captured by the String equals() method. Classes are free to override the equals() method so that it means something that makes sense to that class. Typically you will want the class's equals() method and not ==, not just for String but for other classes as well.

We don't think of "All men are equal" as meaning anything like "All men are identical" and so it is with Java's reference values and the things they point to.  (Of course a Java class which overrode equals() to always return true would be valid, but pointless.)

---

### Post by mattyB on 2009-10-31
> **pbrockway2 said:**
> Not only does == not compare strings directly: it doesn't compare strings **at all**.  == compares reference values (and primitive values and it compares them the same way).  If the values are equal you get "true" otherwise you get "false".


pbrockway2 touches on a important distinction in understanding how & what is being compared. This is mistake that many new (and even experienced) developers make.

---

