---
title: "return statement problem (java)"
date: 2009-11-11
forum: Programming Talk
---

### Post by s3a on 2009-11-11
Here is my functional code without a return statement:

```
import java.util.Scanner;

import java.util.Random;



public class Asg_3B

{ // main method:

	public static void main (String[] args)

	{

		playGame();

	}



// playGame() method:



	public static void playGame()

	{

		Random rand = new Random();

		int random_number = rand.nextInt(100);

		System.out.println("Secret number (for programming use): " + random_number);

		System.out.print("The secret number is between 1 and 100.\nWhat's your guess? ");

		Scanner kb = new Scanner(System.in);

		int guess = kb.nextInt();

		int amount_of_tries = 1;



		while(guess != random_number)

		{

			if(amount_of_tries == 10)

			{

				System.out.println("You lose! The number was " + random_number + ".");

				System.exit(0);

			}



			if(guess < random_number)

			{

				System.out.print("Too low, guess again? ");

				guess = kb.nextInt();

			}

			else

			{	System.out.print("Too high, guess again? ");

				guess = kb.nextInt();

			}

			amount_of_tries++;

		}



		if(amount_of_tries == 10)

		{

			if(guess == random_number)

			{

				System.out.println("Bravo! It took you " + amount_of_tries + " tries.");

				System.exit(0);

			}



			else

			{

				System.out.println("You lose! The number was " + random_number + ".");

				System.exit(0);

			}

		}

		else if(amount_of_tries < 10)

			{

			if(guess == random_number)

				{

					System.out.println("Bravo! It took you " + amount_of_tries + " tries.");

					System.exit(0);

				}

			}







		}

}

```

And here is my code that gives compilation errors:

```
import java.util.Scanner;

import java.util.Random;



public class Asg_3B

{ // main method:

	public static void main (String[] args)

	{

		boolean outcome = playGame();

		/*if(outcome)

		wincount++;

		/*else

		losecount++;*/

		

	}



// playGame() method:



	public static boolean playGame()

	{

		Random rand = new Random();

		int random_number = rand.nextInt(100);

		System.out.println("Secret number (for programming use): " + random_number);

		System.out.print("The secret number is between 1 and 100.\nWhat's your guess? ");

		Scanner kb = new Scanner(System.in);

		int guess = kb.nextInt();

		int amount_of_tries = 1;



		while(guess != random_number)

		{

			if(amount_of_tries == 10)

			{

				System.out.println("You lose! The number was " + random_number + ".");

				win_or_lose = false;

				//System.exit(0);

			}



			if(guess < random_number)

			{

				System.out.print("Too low, guess again? ");

				guess = kb.nextInt();

			}

			else

			{	System.out.print("Too high, guess again? ");

				guess = kb.nextInt();

			}

			amount_of_tries++;

		}



		if(amount_of_tries == 10)

		{

			if(guess == random_number)

			{

				System.out.println("Bravo! It took you " + amount_of_tries + " tries.");

				win_or_lose = true;

				//System.exit(0);

			}



			else

			{

				System.out.println("You lose! The number was " + random_number + ".");

				win_or_lose = false;

				//System.exit(0);

			}

		}

		else if(amount_of_tries < 10)

			{

			if(guess == random_number)

				{

					System.out.println("Bravo! It took you " + amount_of_tries + " tries.");

					win_or_lose = true;

					//System.exit(0);

				}

			}

	return win_or_lose;

	}

}

```

The code with errors was my attempt to solve a previous compilation error which complained that there was no return statement but I had put return true or false depending if the loop is for a win or a loss so where there is win_or_lose = true or false, there use to be a return true or false; and I noticed that the return statement had to be the bottom before the last two brackets (return win_or_lose;). I am just confused as to how to return a true or false to the main method to let my program know whether the user won or lost so that a message could be printed to inform the user of how many games he or she won or lost.

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by dwhitney67 on 2009-11-11
Here's some insight/help, that is not related to your homework...
```

public class Return
{
   static boolean isOddValue(int value)
   {
      return (value % 2 == 1 ? true : false);
   }

   public static void main(String[] args)
   {
      int value1 = 3;
      int value2 = 6;

      System.out.println("The number " + value1 + " is an odd value: " + isOddValue(value1));
      System.out.println("The number " + value2 + " is an odd value: " + isOddValue(value2));
   }
}

```

---

### Post by issih on 2009-11-11
I suspect your main compilation problem arises from not declaring your boolean "win_or_lose" variable at the top of the playgame method consequently you never type the variable as a boolean prior to trying to use it nor do you define its scope as being outside the various loops you use.

Now...you have several other issues in your code.

You use "System.exit(0);" a lot in your original version (which is not a brilliant design choice imo, but we shall ignore that).

By just commenting them out in your newer version you break your logic. The new code will never exit until you guess the number, and will just keep informing you that you have failed again and again until you guess the correct number to make it break out of the first loop. You need to use either a break or a return statement to make that loop end as originally intended.

Your handling of success and failure cases if also rather broken...

Your original code is meant to:

exit the program if the user fails to guess within 10
if the user guesses correctly within 10 then:
check if the number of tries taken was exactly ten:
   if it was 10 and the number guessed was correct - say well done
   and exit
   else if it was exactly 10 and the number guessed was wrong then
   say you lost and exit.(N.B. you can never reach this option)

Finally if the number of guesses was less than 10 you check if the guess is right and then say well done.

Whilst this works...it is unnecessarily complex, and inaccurate.

Checking if the number of tries is valid is pointless...as the first loop will have exited the program if the user has failed.

Similarly checking if the number was guessed correctly is pointless as the initial loop has already checked this, and this bit of code is never run if the user fails.

Finally there is no need to distinguish between the cases for exactly 10 tries and less than 10.

In fact, given that this bit of the code is only ever reached if the user succeeds in winning the game, then you can just print out a well done and the number of tries, with no further validation whatsoever...

Hope that helps

---

### Post by issih on 2009-11-11
Well, I was bored...so here are 3 versions of your code that *should* work - not tested at all.

First version uses multiple return statements and therefore has multiple exit points to the method..this is logically most similar to your version with lots of system.exit calls, but calling return simply passes control back to the calling method along with the return value - rather than exiting the program altogether. Also note that no validation is needed on the success/failure messages, as they are tied into the code flow. This is my favourite by far.

```
	public static boolean playGame(){

		Random rand = new Random();
		int random_number = rand.nextInt(100);
		System.out.println("Secret number (for programming use): " + random_number);
		System.out.print("The secret number is between 1 and 100.\nWhat's your guess? ");
		Scanner kb = new Scanner(System.in);
		

		int guess = kb.nextInt();
		int amount_of_tries = 1;

		while(guess != random_number)
		{
			if(amount_of_tries == 10)
			{
				//if count reaches 10 - inform of failure and exit method with a false return value.
				System.out.println("You lose! The number was " + random_number + ".");
				return false;
			}

			if(guess < random_number)
			{
				System.out.print("Too low, guess again? ");
				guess = kb.nextInt();
			}
			else
			{
				System.out.print("Too high, guess again? ");
				guess = kb.nextInt();
			}

			amount_of_tries++;
		}
		// this code only ever reached if you win game and exit above loop. with guess = random number
		// inform of success and return true to calling method.
		System.out.println("Bravo! It took you " + amount_of_tries + " tries.");
		return true;
	}
```

Second version uses a  break statement to exit the loop, and continue code flow at the end of the while statement. It uses a boolean win_or_lose variable which is set appropriately within the initial loop, and is later used as a switch to send the user the appropriate message, and is finally returned to the calling method.

```
	public static boolean playGame()
	{
		Random rand = new Random();
		int random_number = rand.nextInt(100);
		System.out.println("Secret number (for programming use): " + random_number);
		System.out.print("The secret number is between 1 and 100.\nWhat's your guess? ");
		Scanner kb = new Scanner(System.in);

		int guess = kb.nextInt();
		int amount_of_tries = 1;

		//declare and initialise boolean to use in return value at end
		boolean win_or_lose = true;

		while(guess != random_number)
		{
			if(amount_of_tries == 10)
			{
				// you lose so set boolean flag
				win_or_lose = false;

				// break out of loop..
				break;
			}

			if(guess < random_number)
			{
				System.out.print("Too low, guess again? ");
				guess = kb.nextInt();
			}
			else
			{
				System.out.print("Too high, guess again? ");
				guess = kb.nextInt();
			}

			amount_of_tries++;
		}

		//N.B. loop above now always exits and passes control here.

		if(win_or_lose)
		{
			System.out.println("Bravo! It took you " + amount_of_tries + " tries.");
		}
		else
		{
			System.out.println("You lose! The number was " + random_number + ".");
		}

		//return our win/lose valus to calling method
		return win_or_lose;
	}

```

Finally.. A version that uses a logical and to exit the loop after 9 guesses (NOTE all of these allow 9 guesses which is what your original code did - I have no idea if that was intentional or you meant to have 10). The system then does validation to work out if the user has won or lost based on how many tries were taken...Again note how little validation is actually required.

```
public static boolean playGame(){

		Random rand = new Random();
		int random_number = rand.nextInt(100);
		System.out.println("Secret number (for programming use): " + random_number);
		System.out.print("The secret number is between 1 and 100.\nWhat's your guess? ");
		Scanner kb = new Scanner(System.in);

		int guess = kb.nextInt();
		int amount_of_tries = 1;

		//make loop guarantee to exit after 9 goes if not guessed yet - using a logical "and"
		while(guess != random_number && amount_of_tries<10)
		{
			if(guess < random_number)
			{
				System.out.print("Too low, guess again? ");
				guess = kb.nextInt();
			}
			else
			{	System.out.print("Too high, guess again? ");
				guess = kb.nextInt();
			}
			amount_of_tries++;
		}
		
		//In this version we always reach here with no real idea if we have won or not…so you then need validation
		//similar to what you did in your version - but note how much less is actually required:

		
		//amount of tries variable will always have a value between 1 and 10, any value other than 10 is a win, as 
		//you made the above loop exit by guessing the number.
		
		boolean win_or_lose = true;
		if(amount_of_tries == 10)
		{
			System.out.println("You lose! The number was " + random_number + ".");
			win_or_lose = false;
		}
		else
		{
			System.out.println("Bravo! It took you " + amount_of_tries + " tries.");
			//N.B. win_or_lose is initialised to true…so no need to set it here.
		}
		
		return win_or_lose;
	}


```

Have a little look at those.... Hopefully they will help you to grasp the way program flow should be structured.

---

### Post by s3a on 2009-11-12
Thanks your explanation helped me get through that problem but now I do not have a compilation error anymore which is good so I was just hoping you or somebody else could help explain to me in easy to understand words what is bold in the following code does and means:

```
import java.util.Scanner;

import java.util.Random;



public class Asg_3B

{ // main method:

	public static void main (String[] args)

	{

		Scanner kb = new Scanner(System.in);

		String inputLine;

		char answer;		

		//initiliazes winCount and loseCount variables.

		int winCount = 0, loseCount = 0;

		do

		{

		// calls play(game) method to return boolean value of true (=win) or false (=lose)

		boolean outcome = playGame();

		// evaluates whether the condition is true, if it is, it adds a value of 1 to win score

		if(outcome)

		winCount++;

		// executes if the condition is false, if it is, it then adds a value of 1 to win score

		else

		loseCount++;

		System.out.print("Do you want to play again?: ");

		inputLine = kb.next();

		answer = inputLine.charAt(0);

		System.out.println();

**		//kb.nextLine(); //check what this does (like why the teacher put it)**

		} while(answer == 'y' || answer == 'Y');

		

		//print how many games were won and/or lost as well as played

		System.out.println("\nGames won: " + winCount);

		System.out.println("Games lost: " + loseCount);

		System.out.print("Games played: " + (winCount + loseCount));	

	}

// playGame() method:

	public static boolean playGame()

	{

		**Scanner kb = new Scanner(System.in); // why do I have to put this here if it's in main? (confirm)**

		Random rand = new Random();

		int random_number = rand.nextInt(100);

		System.out.println("Secret number (for programming use): " + random_number);

		System.out.print("The secret number is between 1 and 100.\n\nWhat's your guess? ");

		int guess = kb.nextInt();

		int amount_of_tries = 1;

		

		while(guess != random_number)

		{

			if(amount_of_tries == 10)

			{

				System.out.println("You lose! The number was " + random_number + ".");

				return false;

			}



			if(guess < random_number)

			{

				System.out.print("Too low, guess again? ");

				guess = kb.nextInt();

			}

			else

			{	System.out.print("Too high, guess again? ");

				guess = kb.nextInt();

			}

			amount_of_tries++;

		



			if(amount_of_tries == 10)

			{

				if(guess == random_number)

				{

					System.out.println("Bravo! It took you " + amount_of_tries + " tries.");

				}

			}

			else if(amount_of_tries < 10)

				{

				if(guess == random_number)

					{

						System.out.println("Bravo! It took you " + amount_of_tries + " tries.");

					}

				}					

		}

		return true;

	}

}

```

Thanks!

Edit: I found a minor bug with this code that did not say Bravo etc if I I got the answer on the first guess but I fixed that now in a newer version but I'm still leaving this version here because it's good enough for the explanations I seek. When I'm completely satisfied, I will post my final program just in case others would benefit from it in the future.

---

### Post by dwhitney67 on 2009-11-12
The answer you seek is documented here:
[http://java.sun.com/javase/6/docs/api/java/util/Scanner.html#nextLine(](http://java.sun.com/javase/6/docs/api/java/util/Scanner.html#nextLine())

Consider bookmarking the root of the Java API site:
[http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)

Btw, when appropriate, you should indent statement(s) that apply to an 'if' or 'else', or for that matter, any other block of code.  The following, which appears in the code you presented, is badly formatted:
```

if(outcome)

winCount++;

// executes if the condition is false, if it is, it then adds a value of 1 to win score

else

loseCount++;

```

---

### Post by issih on 2009-11-13
As for your secondary bit of bold text..a method does not have access to the variables of the calling method.

Consequently the kb variable defined in main is not visible from within playgame().

The solution you appear to be using effectively creates a 2nd scanner object within the playgame method in order to access the keyboard input.

Now, I do not know enough about java Scanner objects to know whether having multiple scanners defined on the same input stream (System.in) simultaneously is a bad idea or not, but it is something you should check.

Personally I would just pass the object you create in main into the playgame method rather than making 2 of them.

You'd do this by declaring the method as:

```
public static boolean playGame(Scanner aScanner)
```

and call it from within main with:

```
playGame(kb);
```

Note that you'd need to make sure that all the references to the scanner object within playGame referenced it as "aScanner" rather than "kb" as that is the name of the variable holding the Scanner object within the playGame class.

Hope that helps

---

