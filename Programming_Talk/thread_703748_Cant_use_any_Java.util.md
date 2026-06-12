---
title: "Cant use any Java.util"
date: 2008-02-21
forum: Programming Talk
---

### Post by travist120 on 2008-02-21
I installed sun-java5-jdk and I still can't use java.util.scanner (I don't know java's workings well, I am a student who is sick and would like to be able to catch up in my computer science class from home) I use SciTE as my editor, but when I run Compile, then Go, I get this

```

	at java.util.Scanner.throwFor(Scanner.java:838)
	at java.util.Scanner.next(Scanner.java:1461)
	at java.util.Scanner.nextInt(Scanner.java:2091)
	at java.util.Scanner.nextInt(Scanner.java:2050)
	at L3_7Rock.main(L3_7Rock.java:18)

```

---

### Post by lsmobrian on 2008-02-21
Could u post any code, that might help rule out programming errors (no offense, just helpful to check)

---

### Post by jerrek71 on 2008-02-21
> **travist120 said:**
> I installed sun-java5-jdk and I still can't use java.util.scanner (I don't know java's workings well, I am a student who is sick and would like to be able to catch up in my computer science class from home) I use SciTE as my editor, but when I run Compile, then Go, I get this

```

	at java.util.Scanner.throwFor(Scanner.java:838)
	at java.util.Scanner.next(Scanner.java:1461)
	at java.util.Scanner.nextInt(Scanner.java:2091)
	at java.util.Scanner.nextInt(Scanner.java:2050)
	at L3_7Rock.main(L3_7Rock.java:18)

```

Hi there,
   What's the exception that's being thrown? There's not much to see from just the line numbers :-)

I recommend Eclipse for writing Java apps - though to be honest I have never used SciTE so it could be even better!

Did you have any other java packages installed? Check which version of java is being used by getting a shell prompt and typing 'java -version' (without the ' of course).

Paste the full exception though and I might be able to shed some better light.

Steve.

---

### Post by travist120 on 2008-02-21
```

// L3_7Rock by Travis Moore
// Period 1
// This program asks the users choice for rock paper or scissors and the computer makes a random choice and the two choices compete

import java.util.*; 
public class L3_7Rock {
public static final int ROCK = 1;
public static final int PAPER = 2;
public static final int SCISSORS = 3;        
    public static void main(String[] args) {           
        Scanner keyboard = new Scanner(System.in);
        int computer, user;
        String status;
        status = "null";
        computer = (int)(Math.random() * 3) + 1;
        System.out.println("Welcome to my Rock Paper Scissors game!");  
        System.out.println("Please enter 1 for Rock, 2 for Paper, or 3 for Scissors:"); 
        user = keyboard.nextInt(); 
	if (user == computer) { 
            status = "It's a tie!";         
        } else if (user == ROCK && computer == PAPER) { 
            status = "Paper covers Rock! I win!";
        } else if (user == ROCK && computer == SCISSORS){  
            status = "Rock beats Scissors! You win!";          
        } else if (user == PAPER && computer == ROCK){  
            status = "Paper covers Rock! You win!";          
        } else if (user == PAPER && computer == SCISSORS){  
            status = "Scissors cuts Paper! I win!";          
        } else if (user == SCISSORS && computer == ROCK){  
            status = "Rock beats Scissors! I win!";          
        } else if (user == SCISSORS && computer == PAPER){  
            status = "Scissors beats Paper! You win!";          
        } else {
	status = "YOU didn't chose something right FOO'!";
        }
        System.out.println("I chose " + computer +", and you chose " + user +"!");
        System.out.println(status);
    }   
} 

```

---

### Post by jerrek71 on 2008-02-21
I'm going to hazard a guess at it being this line;

> **travist120 said:**
> ```

        user = keyboard.nextInt(); 

```

Which looks like line 18 by my count.... It'll be throwing an exception because there's no input to read and Scanner won't block until input is available.

You'll need to do a bit more work up front to read the input from the keyboard before passing it to the Scanner object. You also might want to catch that specific exception and use it for error handling if the user just presses Return for example.

Hope that helps,
Steve.

---

### Post by travist120 on 2008-02-21
I'm sorry, but I don't think I was very specific. The programs I am making are for a class, a sophmore high school class, and I don't have to worry about stuff like handling Returns, the only problem that I am having is that SciTE isn't recognizing when I call the scanner. I remember reading somewhere that SciTE doesn't use SUN's java. Or if eclipse *does* use the right java, then is there any way that I can learn how to simply compile and run my code? Thank-you

---

### Post by lsmobrian on 2008-02-21
have you covered exceptions yet.   Looks like you need to handle any exceptions that might occur from Scanner.nextInt()

From the java API:
InputMismatchException - if the next token does not match the Integer  regular expression, or is out of range
NoSuchElementException - if input is exhausted
IllegalStateException - if this scanner is closed


If i run your program and enter a number everything is fine, but enter a letter and its broke

so you need something like this


try{

user=keyboard.nextInt();

}
catch(InputMismatchException e)
{ e.printStackTrace();
}

Instead of printing the stack you could output something to the user and exit so they know what they did wrong

---

### Post by Imaginationac on 2008-02-22
Actually, he's not required to handle the exception since it's unchecked. Still, it is recommended to do so.

---

### Post by themusicwave on 2008-02-22
You need to check that the scanner has a value and also the type of the value before calling nextInt.

This is because if there is no value to be read or the value to be read isn't an int an exception is thrown.  Read the spec here for details:

[http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html]("http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html")

You need to use the hasNextInt function to chec that there is an int to read.  You could use a for loop to check.

like so:

System.out.println("Please enter 1 for Rock, 2 for Paper, or 3 for Scissors:"); 

//Wait until an int is available
 while( !keyboard.hasNextInt);

//Now read the int
user = keyboard.nextInt(); 

All the details should be in that spec.  You may need to do more, such as use Try and catch to deal with any exceptions(nextInt can throw 3 of them).

Also, just so you know the current version of Java is 6, so unless you were asked to use 5 specifically you may want to install 6.

Hope that helps,

Jon

---

### Post by ZylGadis on 2008-02-22
The above post is incorrect. A Scanner object initialized on System.in will block and wait for user input, and if the user input is of the wrong type, it will throw an exception. What the OP posted as code seems correct to me (at least the parts related to the Scanner object, I did not look at the rest).

OP, what is the exact exception you are getting? Can you post the entire stack, including the root cause?

Also, I would recommend leaving for a time Eclipse, SciTE, and everything else that compiles/runs your code with the press of a button. You need to learn how to handle programs from the command line, if you are ever going to be a programmer, and the best time for that is now. An IDE is helpful to **experienced** coders because it automates tasks they already know how to do well, and avoids mindless repetition of commands. An IDE is the greatest bane ever created for **students** of programming, because it teaches them how to use the IDE, not how to program.

---

### Post by themusicwave on 2008-02-23
ZylGadis,

You are correct, I am wrong.

I misread the Spec trying to answer in a hurry.  Don't use the code I posted as it could result in an infinite loop.

I also agree with ZylGadis, we need the stack trace and error messages from the exception you are getting.

I ran the program with Java 6 and got no errors.  I used eclipse to do it as well.

Try running it from the command line:

Compile it:

javac L3_7Rock.java

run it:

java L3_7Rock

That will tell you if eclipse is the cause of the problem.

Sorry for the mistake,

Jon

---

### Post by CodeRage on 2010-05-20
sorry to dig up an old thread, but I too have experienced this issue.

I like to code in scite. Any program I use I can run in the terminal after compiling it in scite. The issue I run into is when I use a scanner object to collect keyboard input. In the terminal a program will run fine, the user can enter the input, all goes well. Running the program in scite however causes this error: 

```

>java -cp . GuessingGame
Welcome to the Number Guessing Game.
Are you smarter than a computer? If yes, then prove it!
The computer will secretly guess a number, and ask you to guess it.
The object of the game is to guess the number in as few tries as you can.

I am thinking of a special number between 1 and 100...

Please enter a number between 1 and 100: Sorry. Please enter a valid integer: Exception in thread "main" java.util.NoSuchElementException: No line found
	at java.util.Scanner.nextLine(Scanner.java:1533)
	at GuessingGame.get_valid_int(GuessingGame.java:93)
	at GuessingGame.get_guess(GuessingGame.java:107)
	at GuessingGame.play_game(GuessingGame.java:62)
	at GuessingGame.main(GuessingGame.java:27)
>Exit code: 1

```

The above is the actual error produced when attempting to run (F5) my program in scite. I can run this program perfectly fine in a terminal though (using java GuessingGame) after it has been compiled (via scite, or via javac in terminal). 

Any thoughts on this? I have tried to use the parameters tool option in scite, but that doesn't do it. The offending line is one using a scanner object to get user input. :(

Thanks
CodeRage

---

### Post by soltanis on 2010-05-20
Way to rez an old thread.

Can you please post the relevant source code, by which I mean the code where you initialize the Scanner object and then scan for input?

Also, have you tried running the program outside of the IDE? It's possible that some kind of behavior caused by the IDE is causing the exception to be thrown.

What exactly is the behavior of the program, by the way? It's hard to tell from your output alone; does the program not even wait for input, or does it wait for input but then throw an exception as soon as you press a key?

---

