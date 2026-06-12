---
title: "TextIO.getlnInt , how does this work in an IDE Netbeans?"
date: 2010-04-03
forum: Programming Talk
---

### Post by Oscar wollex on 2010-04-03
Please i will really appreciate if there is anybody over there that could help me out with how to RUN a program in a netbean having inside the subroutine TextIO.getlnInt . program sample is this below , please highlighting me.
 
 
EXAMPLE:
Let's write a program that plays a guessing game with the user. The computer will choose a random number between 1 and 100, and the user will try to guess it. The computer tells the user whether the guess is high or low or correct. If the user gets the number after six guesses or fewer, the user wins the game. After each game, the user has the option of continuing with another game.
 
static void playGame() {
int computersNumber; // A random number picked by the computer.
 
int usersGuess; // A number entered by user as a guess.
 
int guessCount; // Number of guesses the user has made.
 
computersNumber = (int)(100 * Math.random()) + 1;
 
// The value assigned to computersNumber is a randomly
 
// chosen integer between 1 and 100, inclusive.
 
guessCount = 0;
 
TextIO.putln();
 
TextIO.put("What is your first guess? ");
 
while (true) {
 
usersGuess = TextIO.getInt(); // Get the user's guess.
 
guessCount++;
 
if (usersGuess == computersNumber) {
 
TextIO.putln("You got it in " + guessCount
+ " guesses! My number was " + computersNumber);
 
break; // The game is over; the user has won.
}
if (guessCount == 6) {
 
TextIO.putln("You didn't get the number in 6 guesses.");
 
TextIO.putln("You lose. My number was " + computersNumber);
break; // The game is over; the user has lost.
}
 
// If we get to this point, the game continues.
 
// Tell the user if the guess was too high or too low.
 
if (usersGuess < computersNumber)
 
TextIO.put("That's too low. Try again: ");
 
else if (usersGuess > computersNumber)
 
TextIO.put("That's too high. Try again: ");
}
TextIO.putln();
} // end of playGame()
 
}

---

### Post by anewguy on 2010-04-04
You'd probably have better luck posting this in the programming forum.

Dave ;)

---

