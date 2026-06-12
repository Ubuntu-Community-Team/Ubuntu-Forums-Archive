---
title: "java.util.Scanner usage question"
date: 2010-03-19
forum: Programming Talk
---

### Post by derekeverett on 2010-03-19
I am new to Java programming and building a number guessing game.

Everything is almost working as desired but I am having some trouble with my Scanner usage I think.

I am using the same Scanner instance to take as input from the user an int, and then later on a String.

I have learned that after the int I need to soak up the new line character.. this works and allows me to use the Scanner instance for the String input.

However, when I use the equalsIgnoreCase method to compare the String entered by the user I am not getting expected results. Is there something about my Scanner usage I am not understanding?

```

import java.util.Scanner;

public class NumberGuess
{
	static Scanner myScanner = new Scanner(System.in);

	public static void main(String args[])
	{
		String userPlayAgainQuestion;
		int userGuess = 0;

		System.out.println("Welcome to Number Guess!\n");

		do
		{
			int secretNumber = ((int)(Math.floor(Math.random() * 10))) + 1;	// Generate random number between 1-10

			while((userGuess < 1) || (userGuess > 10))	// Loop until userGuess is valid int
			{
				System.out.print("Please enter your guess: ");
				userGuess = myScanner.nextInt();
				myScanner.nextLine();

				if((userGuess < 1) || (userGuess > 10))	// Check that userGuess is valid int
				{
					System.out.println("Guess must be between 1-10. Please try again.");
					continue;
				}

				if(userGuess == secretNumber)
				{
					System.out.println("You guessed it!! The number was " + userGuess + "!!");
				}
				else
				{
					System.out.println("Sorry the secret number was " + secretNumber + ".");
				}

			}



			System.out.print("Do you want to play again? Type \'yes\' to continue: ");
			userPlayAgainQuestion = myScanner.nextLine();	// Problem here??????					

		}while(userPlayAgainQuestion.equalsIgnoreCase("yes"));

		System.out.println("\n\nThanks for playing! See you soon.");
	}
}

```

---

### Post by Some Penguin on 2010-03-19
From looking at your code, but not bothering to compile and execute it, I suspect that what you are seeing is that it is repeatedly asking you whether you wish to play again, instead of actually soliciting additional guesses.

If so, you should ask yourself under what conditions it wouldn't actually ask for a guess.  Think about what your variables look like after the first time you give a valid (as in within the range, not necessarily correct) guess.

---

### Post by derekeverett on 2010-03-19
> **Some Penguin said:**
> From looking at your code, but not bothering to compile and execute it, I suspect that what you are seeing is that it is repeatedly asking you whether you wish to play again, instead of actually soliciting additional guesses.

If so, you should ask yourself under what conditions it wouldn't actually ask for a guess.  Think about what your variables look like after the first time you give a valid (as in within the range, not necessarily correct) guess.

You are right, it is asking me whether or not I want to play again over and over until I enter something other than "yes".

I have gone over my code, and even entered a line to print to screen the results of userPlayAgaingQuestion = myScanner.nextLine(); and it displays "yes" which looks right to me.

I'm sure I'm missing something but I just don't see it. My looping worked fine before I had the user inputting anything so I don't think it's a looping problem....

---

### Post by Some Penguin on 2010-03-19
Well, more directly:

```

while((userGuess < 1) || (userGuess > 10)) {
...
}

```
[FONT=monospace]
Let's say you've already been through that loop once -- the user entered a guess that is within that range.  It then tells the user whether or not the guess was right, and asks whether he wants to play again.

Assume that the user types 'yes', and the program correctly reads it.   What happens?

It goes back to the top of the do/while, picks a new secret number -- which you can easily check whether or not it is actually reaching this point by having it output something like "I've picked a new secret number", and reaches inner while() loop again.  What will the result of that test (the 'is the guess in range' test) be?
[/FONT]

---

### Post by derekeverett on 2010-03-19
ahhh.. ok I think I fixed it. 

I had to move my int declaration and initialization inside the do while loop so that it would initialize to zero with every loop iteration.

The way the code was written the int userGuess was assigned by the user 1 time and then just bounced right out while loop at the test expression and straight to the "play again" question.

THANK YOU!

I am impressed that you could see that so quickly. Hope I get an eye that good one day!

---

