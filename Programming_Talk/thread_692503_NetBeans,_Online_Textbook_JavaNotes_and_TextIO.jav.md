---
title: "NetBeans, Online Textbook JavaNotes and TextIO.java"
date: 2008-02-09
forum: Programming Talk
---

### Post by Ultros88 on 2008-02-09
Hi all. I have been trying to learn some Java using the online textbook JavaNotes with NetBeans for my IDE. I haven't gotten very far in the book and the author introduces the TextIO.java / .class file for use when having to deal with user input from the terminal. I have been unable to figure out how to include this .java file (or perhaps the .class file?) in the project so that my main class can compile and run. If anyone could tell me how to do this or point to somewhere I can learn about managing projects in NetBeans I would much appreciate it.

Thanks,
Ultros

---

### Post by shaggy999 on 2008-02-09
It's been a couple of years since I've done any java, but taking a look at the latest API I don't see a TextIO class, so I'm under the assumption  this file is provided by the tutorial as part of the project. If that's the case you should be able to add a -PATH option to the compiler and point it to where ever this class is and in your main document you put an include statement at the top.

---

### Post by Ultros88 on 2008-02-10
Rereading my post now, I realize I didn't make it obvious that TextIO.java is non-standard and a file that the author of the book cooked up in order to make some things easier.

Your suggestion works, but I was wondering if it was possible to somehow add the file into the NetBeans project in order to have the TextIO.class available for the main program so that when compiling with the IDE build function it is automatically recognized as necessary.

I tried setting up a Java Project with Existing Sources in the new project dialogue box and was able to have code completion for the subroutines in TextIO.java. It would be nice if I could figure out a way to add this necessary file to the project so that everything NetBeans offers would work and at the same time be able to compile and run successfully.

Any more help from anybody would be great, thanks
Ultros

---

### Post by midnightray on 2008-02-10
If you want to include this authors file, heres a few suggestions.

Imports. Java works by importing classes that other people have written. IE swing. So maybe importing the file you want.

Try in the project making 2 packages. 1 for your code and 1 for the java file.
In your package the file you wish to include the TextIO file would have the following at the top:

import packagename.TextIO;

where packagename is the other packages name.


Dunno how clear this is :P

---

### Post by Zugzwang on 2008-02-10
Probably the easiest way is to simply copy the TextIO.java file into the "src" directory of your project. :-) Make sure that you match its package name, so if TextIO.java starts with "package foo.bar;" then create a directory named "foo" in the "src" directory of you project in which you create another directory named "bar" in which you place the file.

That's fine as long as you don't distribute the package because then you might violate the author's IP. But as long as you are just learning and playing around, that's fine.

---

### Post by Ultros88 on 2008-02-10
That's great, guys. Thanks.

One last thing: Is there any way within NetBeans to add a file to a project? Or do I have to go running around in Nautilus to move it to the appropriate directory?

---

### Post by naugiedoggie on 2008-02-13
> **Ultros88 said:**
> That's great, guys. Thanks.

One last thing: Is there any way within NetBeans to add a file to a project? Or do I have to go running around in Nautilus to move it to the appropriate directory?

Hello,

The NB method for adding a file to a project is not really preferable.  You can use the option New->Class->existing sources, and it will add the source file.  But, it doesn't move it into your structure, it leaves it where you pointed to.  That can be annoying if you want to put the source under version control, and you have to keep track of it when you're moving stuff around.  

So, I find that the best methods are either physically move the file into place or create a new class file in your existing source directory and copy/paste into it.

The advice about using packages, given earlier, is sound.  I usually like to take source files like textio.java and put them in a separate package and then import as needed into my own stuff.  Seems cleaner.

Note, also, that NB has a File Explorer built into it -- you don't have to go out of the IDE to move the file.

Finally, NB has many excellent beginner tutorials at the [Netbeans]("http://www.netbeans.org") web site.

Thanks.

mp

---

### Post by Oscar wollex on 2010-04-03
> **Ultros88 said:**
> Hi all. I have been trying to learn some Java using the online textbook JavaNotes with NetBeans for my IDE. I haven't gotten very far in the book and the author introduces the TextIO.java / .class file for use when having to deal with user input from the terminal. I have been unable to figure out how to include this .java file (or perhaps the .class file?) in the project so that my main class can compile and run. If anyone could tell me how to do this or point to somewhere I can learn about managing projects in NetBeans I would much appreciate it.
 
Thanks,
Ultros
 
Please tell me in details i am going through the same  problem you had before with the compiling and running of TextIO.getlnInt, i will really appreciate your reply to me. For Example in considering these codes:
 
Let's write a program that plays a guessing game with the user. The computer will choose a random number between 1 and 100, and the user will try to guess it. The computer tells the user whether the guess is high or low or correct. If the user gets the number after six guesses or fewer, the user wins the game. After each game, the user has the option of continuing with another game.
 
 static void playGame() {
    int computersNumber; // A random number picked by the computer.
    int usersGuess;      // A number entered by user as a guess.
    int guessCount;      // Number of guesses the user has made.
    computersNumber = (int)(100 * Math.random()) + 1;
             // The value assigned to computersNumber is a randomly
             //    chosen integer between 1 and 100, inclusive.
    guessCount = 0;
    TextIO.putln();
    TextIO.put("What is your first guess? ");
    while (true) {
       usersGuess = TextIO.getInt();  // Get the user's guess.
       guessCount++;
       if (usersGuess == computersNumber) {
          TextIO.putln("You got it in " + guessCount
                  + " guesses!  My number was " + computersNumber);
          break;  // The game is over; the user has won.
       }
       if (guessCount == 6) {
          TextIO.putln("You didn't get the number in 6 guesses.");
          TextIO.putln("You lose.  My number was " + computersNumber);
          break;  // The game is over; the user has lost.
       }
       // If we get to this point, the game continues.
       // Tell the user if the guess was too high or too low.
       if (usersGuess < computersNumber)
          TextIO.put("That's too low.  Try again: ");
       else if (usersGuess > computersNumber)
          TextIO.put("That's too high.  Try again: ");
    }
    TextIO.putln();
} // end of playGame()

}

 
How can i make this work using an IDE netbeans?

---

### Post by Oscar wollex on 2010-04-03
> **shaggy999 said:**
> It's been a couple of years since I've done any java, but taking a look at the latest API I don't see a TextIO class, so I'm under the assumption this file is provided by the tutorial as part of the project. If that's the case you should be able to add a -PATH option to the compiler and point it to where ever this class is and in your main document you put an include statement at the top.
 please i will really appreciate if you can simply in details highlight me how to make a program contains of  TextIO.getlnInt run in an IDE netbeans. or if possible with a notepad as well.
 program code:
 
 
 
 static void playGame() {
    int computersNumber; // A random number picked by the computer.
    int usersGuess;      // A number entered by user as a guess.
    int guessCount;      // Number of guesses the user has made.
    computersNumber = (int)(100 * Math.random()) + 1;
             // The value assigned to computersNumber is a randomly
             //    chosen integer between 1 and 100, inclusive.
    guessCount = 0;
    TextIO.putln();
    TextIO.put("What is your first guess? ");
    while (true) {
       usersGuess = TextIO.getInt();  // Get the user's guess.
       guessCount++;
       if (usersGuess == computersNumber) {
          TextIO.putln("You got it in " + guessCount
                  + " guesses!  My number was " + computersNumber);
          break;  // The game is over; the user has won.
       }
       if (guessCount == 6) {
          TextIO.putln("You didn't get the number in 6 guesses.");
          TextIO.putln("You lose.  My number was " + computersNumber);
          break;  // The game is over; the user has lost.
       }
       // If we get to this point, the game continues.
       // Tell the user if the guess was too high or too low.
       if (usersGuess < computersNumber)
          TextIO.put("That's too low.  Try again: ");
       else if (usersGuess > computersNumber)
          TextIO.put("That's too high.  Try again: ");
    }
    TextIO.putln();
} // end of playGame()

}

---

