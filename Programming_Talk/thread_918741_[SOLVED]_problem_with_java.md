---
title: "[SOLVED] problem with java"
date: 2008-09-13
forum: Programming Talk
---

### Post by mosty friedman on 2008-09-13
hey everyone,

i was just learning about the Scanner class in java and when i tried to use it, it gave me an error saying "Scanner cannot be resolved to a type" although i have imported the Scanner class before using it...can anyone help me with this??

---

### Post by bfhicks on 2008-09-13
If you post an example of your code you are having problems with, it is much easier to get help with a specific problem.

---

### Post by mosty friedman on 2008-09-13
[php]
import java.util.Scanner;

     public class Guess {
	 public static void main(String[]args)
	{
	  Scanner sc = new Scanner(System.in);
	  int y = (int)(Math.random()*100)+1;       //function to generate a random number from 1-100
	  int x = sc.nextInt();//takes integer input from the user
	  int guesses =1;                        //number of guesses
	  while(x!=y)
	{
	  if(x>y)
	  System.out.println("go lower");
	  if(x<y)
	  System.out.println("go higher");
	  x=sc.nextInt();
	  guesses++;
	}
	  System.out.println("true");
	  System.out.println("you have taken "+guesses+" guesses");
    }
	}
[/php]
ERROR: 
Exception in thread "main" java.lang.Error: Unresolved compilation problems:
	Scanner cannot be resolved to a type
	Scanner cannot be resolved to a type

   at Guess.main(Guess.java:4)

---

### Post by Zugzwang on 2008-09-13
First of all, as a rule of thumb, always look at the *first* error - In this case IOException could not not be resolved. Any you actually forgot in import this class.

Secondly, *when* and *where* does the error occur? This does not seem to be an error message of the Sun "javac" tool.

---

### Post by mosty friedman on 2008-09-13
well i am currently using eclipse but i also tried to compile it from the terminal and still gives me errors

---

### Post by Zugzwang on 2008-09-13
> **mosty friedman said:**
> well i am currently using eclipse but i also tried to compile it from the terminal and still gives me errors

So post them here as well. And did you try importing "IOException" correctly?

BTW: Your Java version needs to be at least 1.5 in order to use the Scanner class.

---

### Post by mosty friedman on 2008-09-13
well i have jdk6 installed.

---

### Post by screech on 2008-09-13
What is the output of 'javac -version' and 'java -version' ?
The code works for me (jdk 1.6).

---

### Post by mosty friedman on 2008-09-13
```

mosty@mosty:~$ javac -version
Eclipse Java Compiler v_774_R33x, 3.3.1, Copyright IBM Corp 2000, 2007. All rights reserved.
mosty@mosty:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)
mosty@mosty:~$ 

```

---

### Post by descendency on 2008-09-13
> **mosty friedman said:**
> well i have jdk6 installed.

is that the only jdk you have installed? You might be attempting to compile with a different JDK.

(it might have installed with another program)

---

### Post by mosty friedman on 2008-09-13
nah, i've checked and i only have jdk6 installed..i dont really know what's the problem :S

---

### Post by mosty friedman on 2008-09-13
ok guys, i've tried to run it from the terminal again and it worked but it still doesnt work with eclipse, anyone have a solution for that??

---

### Post by drubin on 2008-09-13
This would mean that ecslipse is using a the "wrong" java version.

Open eclipse.
window->preferences-> Java->installed JRE's

Make sure that you have at least 1.5 or 1.6 listed there.

---

### Post by mosty friedman on 2008-09-13
ok, it worked..thanks a lot guys for your help :)

---

### Post by luisfm on 2008-10-27
I'm getting the same problem. When I run javac locally on my Vista machine, everything works fine. I uploaded the same code to the school's system and tried to run javac there, I get:
"Calendar1.java:23: error: Scanner cannot be resolved to a type
        Scanner keyboard = new Scanner(System.in);
        ^^^^^^^
Calendar1.java:23: error: Scanner cannot be resolved to a type
        Scanner keyboard = new Scanner(System.in);
                               ^^^^^^^
2 problems (2 errors)"

I assume they have the latest version of the JDK installed. When I run java -version on both machines I get the same values (v1.6)

What is going on? I didn't have this problem before.

---

### Post by drubin on 2008-10-28
> **luisfm said:**
> I'm getting the same problem. When I run javac locally on my Vista machine, everything works fine. I uploaded the same code to the school's system and tried to run javac there, I get:
"Calendar1.java:23: error: Scanner cannot be resolved to a type
        Scanner keyboard = new Scanner(System.in);
        ^^^^^^^
Calendar1.java:23: error: Scanner cannot be resolved to a type
        Scanner keyboard = new Scanner(System.in);
                               ^^^^^^^
2 problems (2 errors)"

I assume they have the latest version of the JDK installed. When I run java -version on both machines I get the same values (v1.6)

What is going on? I didn't have this problem before.

Java is not the compiler. I would recommend trying  javac -version to get the version of the compiler. It might a pathing issue.

---

