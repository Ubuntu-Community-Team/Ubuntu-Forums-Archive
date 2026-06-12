---
title: "another simple java program"
date: 2009-09-20
forum: Programming Talk
---

### Post by nathang1392 on 2009-09-20
i am trying to write a program that is like a simple game. the program picks a number at random, you try to guess this number, and with each guess the program tells you if you are too low or too high. it also counts the number of guesses that it take you before you guess correctly. im not sure where i messed up on this program but if anyone knows thank you in advance for your help.

```
 import java.util.Random;
 import java.util.Scanner;
 public class GuessingGame_V3
{  
   public static void main(String [] args)
     {   
         Scanner in;  
         in = new Scanner(System.in);
         
         System.out.println("Enter a Guess ");
         int userGuess = in.nextInt();
         
         int randomNumber = 0;
         int counter = 0;
         int secretNumber = new Random().nextInt(100) + 1;
         
         randomNumber = new Random().nextInt(99) + 1;
         
         
         if (userGuess < secretNumber){
            System.out.println("Too Low ");}
            
         if (userGuess > secretNumber){
             System.out.println("Too High ");}
             
         if (userGuess == secretNumber){
             System.out.print("You guessed the Number! ");}
         
         while(userGuess > secretNumber){
            System.out.println("Enter your guess: ");}
            counter++;
         
         while(userGuess < secretNumber) {
             System.out.println("Enter your guess: ");}
             counter++;
             
             }
}


```

---

### Post by dwhitney67 on 2009-09-20
Well, I'm not sure what the problem is.  I did not feel that your code was written with efficiency in mind, so I came up with my own version.

```

import java.util.Random;
import java.util.Scanner;

public class GuessingGame
{
   public static void main(String[] args)
   {
      int counter = 0;
      int secretNumber = new Random().nextInt(100);
      int userGuess = 0;

      Scanner in = new Scanner(System.in);

      do {
         System.out.print("Guess my secret number: ");
         userGuess = in.nextInt();

         if (userGuess == secretNumber) break;

         if (userGuess < secretNumber) {
            System.out.println("Sorry, your guess is too low. Try again...\n");
         }
         else {
            System.out.println("Sorry, your guess is too high. Try again...\n");
         }

         ++counter;
      } while (userGuess != secretNumber);

      System.out.println("That's right!  It took you " + counter + " guess(es).");
   }
}

```

P.S.  One thing that is "lame" about the program I presented is that there is nothing to prevent the user from guessing indefinitely.  Perhaps you could consider augmenting the code to allow only a max number of guesses, and if the user fails to guess the secret number, then he/she loses the game.

---

### Post by nathang1392 on 2009-09-20
i dont know what the problem is. it is like there is no control of the flow. even with your revised version when i compile and run all i get is a constant loop that prints Sorry, your guess is too low. Try again...im not sure what exactly i need to do, i feel like it should work.

---

### Post by nathang1392 on 2009-09-20
```

/** 
  * Write a description of class HeadsOrTailsV1 here. 
  *  
  * @author (your name)  
  * @version (a version number or a date) 
  */  
 import java.util.Random;
 import java.util.Scanner;
 public class GuessingGame_V3
{  
   public static void main(String [] args)
     {   
         Scanner in;  
         in = new Scanner(System.in);
         
         System.out.println("Enter a Guess ");
         int userGuess = in.nextInt();
         
         int randomNumber = 0;
         int counter = 0;
         int secretNumber = 0;
         
         
         if (userGuess < secretNumber){
            System.out.println("Too Low ");}
         else if (userGuess > secretNumber){
             System.out.println("Too High ");}
         else 
             System.out.print("You guessed the Number! ");}
         
         while (userGuess > secretNumber) && (userGuess < secretNumber){
            secretNumber = new Random().nextInt(100) + 1;
            randomNumber = new Random().nextInt(99) + 1;
            System.out.println("Enter your guess: ");}
            counter++;
     
             
      }
}
```

i have updated my code to this, which i think is a little more efficient, but i get the error illegal start of type on my while statement. if anyone knows anything thank you in advance.

---

### Post by Volt9000 on 2009-09-20
> i have updated my code to this, which i think is a little more efficient, but i get the error illegal start of type on my while statement. if anyone knows anything thank you in advance.

Yes, you have some extra parentheses. The while condition must be completely enclosed.
So change this

```

while (userGuess > secretNumber) && (userGuess < secretNumber){

```

to this

```

while (userGuess > secretNumber && userGuess < secretNumber){

```

However, it would be a lot easier to have a single condition, thusly:

```

while (userGuess != secretNumber){

```

which will accomplish the same thing.

---

### Post by dwhitney67 on 2009-09-20
Here, another attempt.  Do you see how the program is structured?

1.  Initialization
2.  Determine secret number
3.  While the user has yet to win:

a.  Ask for a guess
b.  Determine if the user has won; if so, set the win flag
c.  Else determine if the user guessed low; if so, notify user
d.  Else notify user that they have guessed high.

4.  After N failed guesses or the user has won, display the result.

The code:
```

import java.util.Random;
import java.util.Scanner;

public class GuessingGame
{
   public static void main(String[] args)
   {
      int MAX_GUESSES = 10;

      int counter = 0;
      boolean win = false;
      int secretNumber = new Random().nextInt(100);

      Scanner in = new Scanner(System.in);

      while (counter < MAX_GUESSES && !win) {
         System.out.print("Guess my secret number: ");
         int userGuess = in.nextInt();

         ++counter;

         if (userGuess == secretNumber) {
            win = true;
         }
         else if (userGuess < secretNumber) {
            System.out.println("Sorry, your guess is too low. Try again...\n");
         }
         else {
            System.out.println("Sorry, your guess is too high. Try again...\n");
         }
      }

      if (win) {
         System.out.println("That's right!  It took you " + counter + " guess(es).");
      }
      else {
         System.out.println("Jeez you're dumb!  After " + MAX_GUESSES +
                            " attempts you could not guess the secret number: " + secretNumber);
      }
   }
}

```

---

### Post by nathang1392 on 2009-09-21
thank you guys for the help. it is much appreciated.

---

