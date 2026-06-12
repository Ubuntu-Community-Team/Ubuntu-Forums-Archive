---
title: "Simple java help"
date: 2006-08-06
forum: Programming Talk
---

### Post by Drakx on 2006-08-06
Hi,

I'm teaching myself java and while reading about a section I create a little program using what I've learned however this is a stupid one and not sure if I'm right.

```

/*
 * Simple password program to show if else in java
 *
 */

// Import an extra java toolkit for user input
import java.util.*;
public class IfElseJava
{
	public static void main(String[] args)
	{
		System.out.println("This program is a password program" +
				" to show if else in java");

		// Create our string variable and initialize it
		String pass = "java";
		String userEntered;
		// Declare our Scanner object
		Scanner userInput = new Scanner(System.in);

		// Now ask our question

		System.out.printf("Hello Guest, please enter a password: ");
		// Make sure we get all of what the user entered at the prompt
		userEntered = userInput.nextLine();

		// Now close our Scanner object (userInput)
		userInput.close();

		// Now the if else statment
		if (userEntered != pass)
		{
			System.out.println("\nSorry your wrong please try again\n");
		}
		else
		{
			if (userEntered == pass)
			{
				System.out.println("Wow you guessed the password\n");
			}
		}

		System.out.print("That shows our if else program\n");
	}
}
```

Can any one spot the error as its always showing "your wrong please try again" and as stupid as it seems im not too sure why :)

Thanks

---

### Post by jeff_ on 2006-08-06
When comparing strings use the .equals method and not the '==' operator.

```
if(String1.equals(String2)) {System.out.println("String1 is the same as String2!");}
```

---

### Post by Drakx on 2006-08-06
> **jeff_ said:**
> When comparing strings use the .equals method and not the '==' operator.

```
if(String1.equals(String2)) {System.out.println("String1 is the same as String2!");}
```

Thanks very much :), can you tell me why you use **.equals()** and not **==** for strings? :-k also for some reason it's still showing the wrong password as been entered :confused:

---

### Post by Drakx on 2006-08-06
Hmm I seem to of got it working after a little playing around :)
here is the new program can a java guru tell me if this correct or a dirty fix :)
```

/*
 * Simple password program to show if else in java
 *
 */

// Import an extra java toolkit for user input
import java.util.*;
public class IfElseJava
{
	public static void main(String[] args)
	{
		System.out.println("This program is a password program" +
				" to show if else in java");

		// Create our string variable and initialize it
		String pass = "java";
		String userEntered;
		// Declare our Scanner object
		Scanner userInput = new Scanner(System.in);

		// Now ask our question

		System.out.printf("Hello Guest, please enter a password: ");
		// Make sure we get all of what the user entered at the prompt
		userEntered = userInput.nextLine();

		// Now close our Scanner object (userInput)
		userInput.close();

		// Now the if else statment

		//if (userEntered != pass)
		if (!userEntered.equals(pass))
		{
			System.out.println("\nSorry your wrong please try again\n");
		}
		else
		{
			if (userEntered.equals(pass))
			{
				System.out.println("Wow you guessed the password\n");
			}
		}

		System.out.print("That shows our if else program\n");
	}
}
```

Thanks for the help also if you can answer the above question also that would help me out loads!

---

### Post by neilp85 on 2006-08-06
> **Drakx said:**
> Thanks very much :), can you tell me why you use **.equals()** and not **==** for strings? :-k 

This is because all java variables are object references not objects themselves. The .equals() method tests whether the two string objects contain the same string. Using == tests if the two string objects have the same address.

---

### Post by jeff_ on 2006-08-06
Your code is correct, not a 'dirty fix';) . To expand on what neil said, == tests to see if the two things are the same variable. For example,

```

String s1 = "hello";
String s2 = s1;

```

while .equals tests to see if the two variables have the same value. For example,

```

String s1 = "hello";
String s2 = "hel" + "l" + "o";

```

---

### Post by Drakx on 2006-08-06
Hi

Oh now I understand :) thanks very much guys! also jeff_ thanks for checking my code at least I know know how its done correctly ;)

---

