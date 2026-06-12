---
title: "Scanner class in java - scanner declaration"
date: 2010-08-28
forum: Programming Talk
---

### Post by Sidneyaks on 2010-08-28
Ok, so I'm trying to figure out something for my java homework. We were introduced to the scanner class, and I'm trying to run it in my program.

The only problem is, when I initialize the scanner variable, like so
```
Scanner keyboard = new Scanner(System.in);
```

the compiled code prompts the user for an input at that point in the system. So, the next time I call keyboard.nextline();

it returns whatever the user first put in, an every input after that is delayed until the next call. I've searched google up and down and can find no mention of it. The posted powerpoint slides and my book don't say anything either. Any suggestions or possiblities? Could it be the compiler I'm using (gcj-4.4-jdk)? 

```
/**
  Sidney Akers
  CS 411
  Assignment 1
 */
import java.util.Scanner;

public class program1
{


	public static void main(String[] args)
	{
	boolean turn = true; //true is user turn, false is computer turn
	String input = "null";
	int userScore = 0;
	int computerScore = 0;
	Scanner keyboard = new Scanner(System.in);
		while(true)
		{
		System.out.println("Pig instructions - roll a six sided die to obtain a score, the first player to one hundred wins. A player may continue rolling his turn untill they choose to stop (at which point the sum of all rolls in that turn are added to their score), or they roll a 1 (at which point all points are lost).");
		System.out.println();
		System.out.println("User Score:" + userScore + " Computer Score:" + computerScore);
		System.out.println();
		while (turn)
			{
			System.out.println("It is your turn, you can execute the following actions by inputting the corrosponding letter");
			System.out.println("Roll");
			System.out.println("Hold");
			System.out.println("Exit");
						input =	keyboard.nextLine(); 
			
			System.out.println("--" + input + " " + keyboard + "--");
			System.out.println();			
				if(input.equalsIgnoreCase("Roll"))
					{}
				else if(input.equalsIgnoreCase("Hold"))
					{}
				else if(input.equalsIgnoreCase("Exit"))
					{System.out.println("Exit has been entered");
					System.exit(0);}
			}
		}
	}
}
```

---

### Post by GregBrannon on 2010-08-28
I think your interpretation of the results are wrong - at least based on my experience with running your code.

I have the following questions for you to consider:

Why don't you break up your lines so that they print nicely - within an 80 column limit?

Why do you instruct the user to enter the "corresponding letter," but then test for the whole word?

How do you decide the value of the die if the user chooses to roll?

How do you compute the user's score?

When/how does the computer's turn happen?

Keep working on it.

---

