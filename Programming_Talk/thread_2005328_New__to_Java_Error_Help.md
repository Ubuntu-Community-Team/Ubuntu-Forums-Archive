---
title: "New  to Java Error Help"
date: 2012-06-17
forum: Programming Talk
---

### Post by NewStudentJJJ on 2012-06-17
I'm just beginning to run through some java examples in a book and code them. I have run into an error while trying to run the below program, any help would be appreciated. Thank you.

Error:
Compiling your program...
Build completed successfully!
Running your program...
The program raises a runtime error


Code:

import java.io.*;
import java.util.Scanner;

class Addition

{
* public static void main(String[] args)
{
	java.util.Scanner*input*=*new*java.util.Scanner(System.in);*


	int number1;
	int number2;
	int sum;

	System.out.print( "Enter first digit: " );
	number1 = input.nextInt();

	System.out.print( "Enter second digit:" );
	number2 = input.nextInt();

	sum = number1 + number2;

	System.out.printf( "Sum is %d\n, sum" );
* **
}
}

---

### Post by Perfect Storm on 2012-06-17
Moved to Programming and Talk.

---

### Post by r-senior on 2012-06-17
Welcome to the forum.

Where did all the asterisks come from? :confused:

I took them out, compiled and ran. The error was:

```
Sum is Exception in thread "main" java.util.MissingFormatArgumentException: Format specifier 'd'
	at java.util.Formatter.format(Formatter.java:2487)
	at java.io.PrintStream.format(PrintStream.java:970)
	at java.io.PrintStream.printf(PrintStream.java:871)
	at Addition.main(Addition.java:19)

```

That's because you've put the double quote in the wrong place on this line:

```
System.out.printf("Sum is %d\n, sum[COLOR="Red"]"[/COLOR]);
```

It should be:

```
System.out.printf([COLOR="DarkGreen"]"Sum is %d\n"[/COLOR], sum);
```

When you post code, there's a little button (#) in the toolbar that allows you to preserve the formatting. Just highlight code and press the button to wrap in code tags.

---

### Post by trent.josephsen on 2012-06-17
> **NewStudentJJJ said:**
> Error:
Compiling your program...
Build completed successfully!
Running your program...
The program raises a runtime error

What software produced this error? I don't know of any Java IDE that produces such singularly unhelpful messages.

---

### Post by NewStudentJJJ on 2012-06-18
Thank you.....the astericks some how got into the posting......thank you so much.....ugh! I'll give the quotes a shot. 
JJJ

---

### Post by NewStudentJJJ on 2012-06-18
Also, the Java app is one for my ipad that I loaded yesterday. JJJ

---

### Post by NewStudentJJJ on 2012-06-18
Ok, I fix astericks and quote and changed class addition to class main. And I get this error:


Exception in thread "main" java.util.NoSuchElementException
	at java.util.Scanner.throwFor(Scanner.java:838)
	at java.util.Scanner.next(Scanner.java:1461)
	at java.util.Scanner.nextInt(Scanner.java:2091)
	at java.util.Scanner.nextInt(Scanner.java:2050)
	at Main.main(Main.java:19)

Thoughts?
Thank you,
JJJ

---

### Post by ofnuts on 2012-06-18
> **NewStudentJJJ said:**
> Ok, I fix astericks and quote and changed class addition to class main. And I get this error:


Exception in thread "main" java.util.NoSuchElementException
    at java.util.Scanner.throwFor(Scanner.java:838)
    at java.util.Scanner.next(Scanner.java:1461)
    at java.util.Scanner.nextInt(Scanner.java:2091)
    at java.util.Scanner.nextInt(Scanner.java:2050)
    at Main.main(Main.java:19)

Thoughts?
Thank you,
JJJ
assuming your code is now correct, this error can be caused by your input, for example a Ctrl-D to indicate the end of the  input. Have the code print the numbers it has read.

By the way, with this code, you can enter both numbers at the first prompt (nextInt() will stop on the first whitespace).

---

### Post by NewStudentJJJ on 2012-06-19
So do I have to remove nextint()? Here's the code as it stands now:

import java.io.*;
import java.util.Scanner;

class Main

{
public static void main(String[] args)
{
java.util.Scanner*input*=*new*java.util.Scanner(System.in);

int number1;
int number2;
int sum;

System.out.print( "Enter first digit: " );
number1 = input.nextInt();

System.out.print( "Enter second digit: " );
number2 = input.nextInt();

sum = number1 + number2;

System.out.printf( "Sum is %d\n", sum );
}
}

---

### Post by ofnuts on 2012-06-19
> **NewStudentJJJ said:**
> So do I have to remove nextint()? Here's the code as it stands now:

import java.io.*;
import java.util.Scanner;

class Main

{
public static void main(String[] args)
{
java.util.Scanner*input*=*new*java.util.Scanner(System.in);

int number1;
int number2;
int sum;

System.out.print( "Enter first digit: " );
number1 = input.nextInt();

System.out.print( "Enter second digit: " );
number2 = input.nextInt();

sum = number1 + number2;

System.out.printf( "Sum is %d\n", sum );
}
}
No... that just means that you code will print "Enter second digit:" without pausing for input if one enters two numbers at the first prompt.

It remains that the exception you get is legitimate in some cases, so you would have to show us your input (which, ideally, you keep in a file that you pipe to your code to run your tests....).

Also, your code won't fly in front of real-life users, just see how it reacts to tpyographicla erorrs (hint: catch exceptions).

---

