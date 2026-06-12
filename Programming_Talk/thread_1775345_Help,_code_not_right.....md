---
title: "Help, code not right...."
date: 2011-06-04
forum: Programming Talk
---

### Post by thunderkyss on 2011-06-04
I'm using an old book to learn Java Programming. *Java 2 game programming*. I've copied a class out of the book, word for word, letter for letter, symbol for symbol.
> public class Card
{
	//array representing all possible face values
	public static final String[] FACES = {"2", "3", "4", "5", "6", "7", "8", "9", "10", 					      "J","Q", "K", "A"};	
	// array representing all possible suit values
	public static final String[] SUITS = {"Hearts", "Spades", "Clubs", "Diamonds"};

	// the maximum number of cards that can be indexed
	public static final int MAX_CARDS = FACES.length * SUITS.length;

	// the value assigned to this Card
	protected int value;

	// creates a default Card with a value of 0
	public Card ()
	{
	    value = 0;
	}

	// creates a Card indexed by n. invalid indexes will cause the program to 
	// terminate


	public Card (int n)
	{
	   // rather than allowing errors to appear later, just terminate the program 		  // with an error message if an invalid index is specified
	      if (n < 0 || n>= MAX_CARDS)
	        {
		System.out.println("Error: Invalid Card Index ("+n+"). Program 						terminating.");
		System.exit (0);
	        }
	       else
	       {
		value = n;
	       }
	}

	// returns the String representation of this Card's face value
	public String  getFace()
	{
	     return FACES[value%FACES.length];
	}

	// returns the String representation of this Card's suit value
	public String getSuit()
	{
	     return SUITS[value%SUITS.length];
	}

	// returns the string representation of this Card
	public String toString()
	{
	    return getFace() + "of" + getSuit();
	}
}	// Card


The Java compiler of my Mac. G4 powerpc, doesn't want to compile it. 

I get one error.
> GetCard.java:1: modifier private not allowed here
private class Card

I don't understand.

Can you help?

---

### Post by ThatCoolGuy220 on 2011-06-04
IDK if it has something to do with new standards and I'm not the indicate person to tell you,

Don't worry somebody will answer  soon people on this forum are very clever...

---

### Post by Barrucadu on 2011-06-04
Can't reproduce with Sun JDK 6u25.

Additionally, the error says you have used "private class Card", whereas the code you posted uses "public class Card". Are you sure that's the code you're trying to compile?

---

### Post by r-senior on 2011-06-04
You are declaring a class called Card in a file called GetCard.java. I'm not sure that's your problem because I thought it gave a different message, but it's not right. It should be Card.java.

EDIT ...

If I compile it like you have, I get this:

```

$ javac GetCard.java
GetCard.java:1: class Card is public, should be declared in a file named Card.java
public class Card
       ^
1 error

```

Which is clearer. The class compiles if you rename to Card.java.

---

### Post by Petrolea on 2011-06-04
> **thunderkyss said:**
> I'm using an old book to learn Java Programming. *Java 2 game programming*. I've copied a class out of the book, word for word, letter for letter, symbol for symbol.


The Java compiler of my Mac. G4 powerpc, doesn't want to compile it. 

I get one error.

I don't understand.

Can you help?

In Java, name of the class must always have the same name as name of the file.

---

### Post by thunderkyss on 2011-06-04
> **Petrolea said:**
> In Java, name of the class must always have the same name as name of the file.

Thanks, that makes sense. I'll try it when I get home.

---

### Post by cgroza on 2011-06-04
> **Petrolea said:**
> In Java, name of the class must always have the same name as name of the file.
Names of public classes if I am not mistaken.

---

### Post by Petrolea on 2011-06-05
> **cgroza said:**
> Names of public classes if I am not mistaken.

Of course, my mistake.

---

