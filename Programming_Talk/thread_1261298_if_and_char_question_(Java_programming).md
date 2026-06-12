---
title: "if and char question (Java programming)"
date: 2009-09-08
forum: Programming Talk
---

### Post by s3a on 2009-09-08
What is wrong with my code? I get one error when I attempt to compile it.

```
import java.util.Scanner;

public class Character

{
	public static void main (String [] args)
	
		{
		
			Scanner kb;
			kb = new Scanner(System.in);
			
			char ch;
		
		
			{
				
				if (ch == 'A')
					System.out.println("The letter is A.");
			
				if (ch != 'A')
					System.out.println("Not the letter A.");
			}
		}
		
}
```

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by Joshua Lückers on 2009-09-08
Your variable ch is not initialized. You have to assign the input from the scanner to it. For example like this:
```

char ch[] = kb.toString().toCharArray();

```Afterwards you can check the ch[] if it matches the character you want. For example:
```

if (ch[0].equals("A")) 
     System.out.println("The input equals A.");

```

---

### Post by Finalfantasykid on 2009-09-08
Also, for some better style, you do not need those curly braces around the two if statements.  While it should still compile with them there, it makes the code less beautiful, and can make things much more difficult to debug with large programs.

Also, even though this is a pretty trivial example, you should still join those two if statements into an if/else statement.  If you want maximum performance, you should do this instead.

```
if (ch == 'A')
       System.out.println("The letter is A.");
else
       System.out.println("Not the letter A.");
```Both accomplish the exact same thing, but this way saves a few lines of assembly code, and if this were in a loop which were iterated several trillion times, it might run a fraction faster.

EDIT:

> ```
if (ch[0].equals("A")) 
         System.out.println("The input equals A.");
```

Are you sure this would work?  ch[0] is a char, so you should be able to just use a ==.  chars do not have methods...

---

### Post by gotenks05 on 2009-09-08
> **s3a said:**
> What is wrong with my code? I get one error when I attempt to compile it.

```
import java.util.Scanner;

public class Character

{
	public static void main (String [] args)
	
		{
		
			Scanner kb;
			kb = new Scanner(System.in);
			
			char ch;
		
		
			{
				
				if (ch == 'A')
					System.out.println("The letter is A.");
			
				if (ch != 'A')
					System.out.println("Not the letter A.");
			}
		}
		
}
```

Any help would be greatly appreciated!
Thanks in advance!

You need to ask the user for input (e.g. System.out.print("Enter a character:  ")

Next you need to initialize the character variable ch with a method from the scanner class.  I may have revealed too much, but I know this from what your typed.  Also, this part of the code:

```
char ch;
		
		
			{
				
				if (ch == 'A')
					System.out.println("The letter is A.");
			
				if (ch != 'A')
					System.out.println("Not the letter A.");
			}
```

needs to look like this:

```
char ch;
		
		
			
				
				if (ch == 'A')
					System.out.println("The letter is A.");
			
				else System.out.println("Not the letter A.");
			
```
The second if is not needed.

---

### Post by Habbit on 2009-09-08
> **Finalfantasykid said:**
> chars do not have methods...

Which is one of the many reasons that push me off Java and towards C#... Oh yeah, I love the smell of Napalm in the morning :KS

---

### Post by Reiger on 2009-09-08
@OP: You use the name Character for your class which is OK (sort of) but has the problem that there already exists a Character class in the java.lang package. And the remaining problems (others have pointed out issues already) here are that:
[list="1"]
[*]java.lang is implicitly imported by *all* classes because it is the Java language. This includes the java.lang.Character class.
[*]You do not use fully qualified type names (which is OK; that is what import statements are for: enable to the shorthand aliases); but the shorthand for Character matches your class name.
[*]Your class is not part of its own package. This makes resolving name conflicts (we have two different types; both called Character) just a tad harder... 
[/list]

Finally, IMO the problems with the last few threads of yours are that:
[list]
[*]You do not post an actual description of your problem. In this case you have quite a weird situation yet expect others to recognize what is going on from the enigmatic note "my code does not compile".

You should post (a) what is wrong; (b) what the error message is, if applicable; (c) what you intend it to do; (d) what you get it to do (if applicable); (e) other symptoms & details; (f) what you have tried to resolve the issue on your own.

Consider posting a thread for help like this which is purely about your own code -and therefore 99.99% likely about a mistake of yourself- the same as filing a bug report against a program/library: your program/library to be precise. Just saying "it does not work" doesn't help anybody anything.
[*]Your code snippets are badly formatted (not at all, I might say); and should be posted inside ```
[code]
```[/code] blocks. That way the forum will ensure that indentation is kept and your code is more legible. (Alternatively you may want to use a syntax highlighted equivalent designed for PHP code: ```
[php][/php]
```)
[*]All of your problems can be resolved & avoided by you, yourself, simply using the online tutorials and documentation on the SUN website. Really, try it: type "Java", the name of the class (e.g. "Scanner") in Google and search for that. This is an example of such a google search: [http://www.google.com/search?client=opera&rls=en&q=%22Java+Scanner%22&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=%22Java+Scanner%22&sourceid=opera&ie=utf-8&oe=utf-8) You will notice the link from java.sun.com titled "Scanner (Java 2 Platform SE 5.0)".
[*]You post homework problems (assignments). The first person you should approach for help is not some random stranger on a forum but the professor/teacher/assistant. Come the exams you presumably will be facing slightly less trivial tasks which require genuine understanding of the language and then you will not be able to head for the forums, will you?
[/list]

---

### Post by Finalfantasykid on 2009-09-08
Ya the Java Documentation is seriously your best friend.  Its well written, and it covers pretty much every Java class known to man(well at least the default ones).

Also the error messages will usually tell you what line the compilation problem is on, and if you are using an IDE like Eclipse, if you highlight over that line, it should give you suggestions on how to fix it.

---

