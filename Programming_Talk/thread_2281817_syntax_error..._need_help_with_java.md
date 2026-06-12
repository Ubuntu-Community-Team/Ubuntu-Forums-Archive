---
title: "syntax error... need help with java"
date: 2015-06-09
forum: Programming Talk
---

### Post by sypher2 on 2015-06-09
So I'm following this book, "Head First : Java", and it covers Java 5.0. I think that may be where my problem lies, because I am trying to run this program directly from the book, and I am getting a syntax error. I understand what its saying, but im trying to figure out why this book wanted me to do it this way in the first place, and then figure out what I can do to solve this.

So here's what's happening, I run this program, and its an infinite loop. The 3 players guesses are never considered true/correct, even though they guess the same number as the random number. The game should end , but it doesnt. it stays on an infinite loop. I will post three different classes all pertaining to this game.



public class GameLauncher {
    public static void main(String[] args){
        
        GuessGame game = new GuessGame();
        game.startGame();
    }
}

---------------------------------------------------------------------------------------

public class Player {
    int number = 0;
    
    public void guess() {
        number = (int) (Math.random() * 10);
        System.out.println("Im guessing " + number);
    }
}
------------------------------------------------------------------------------------------------------------
public class GuessGame {
    Player p1;
    Player p2;
    Player p3;
        public void startGame(){
            p1 = new Player();
            p2 = new Player();
            p3 = new Player();
                int guessp1 = 0;
                int guessp2 = 0;
                int guessp3 = 0;
                    boolean p1isRight = false;
                    boolean p2isRight = false;
                    boolean p3isRight = false;
                    
                int targetNumber = (int) (Math.random() * 10);
                System.out.println("I'm thinking of a number between 0 and 9. . .");
            
            while(true){
            System.out.println("Number to guess is " + targetNumber);
        p1.guess();
        p2.guess();
        p3.guess();
        
    guessp1 = p1.number;
    System.out.println("Player one guessed " + guessp1);
    guessp2 = p2.number;    
    System.out.println("Player two guessed " + guessp2);
    guessp3 = p3.number;
    System.out.println("Player three guessed " + guessp3);
    
  if (guessp1 == targetNumber){
    p1isRight = true;
} if (guessp2 == targetNumber){
    p2isRight = true;
} if (guessp3 == targetNumber){
    p3isRight = true;
}
    if (p1isRight || p2isRight || p3isRight){
        System.out.println("We have a winner!");
        System.out.println("Player one got it right? " + p1isRight);
        System.out.println("Player two got it right " + p2isRight);
        System.out.println("Player three got it right" + p3isRight);
        System.out.println("Game is over!");
    } else {
        System.out.println("Players will have to try again");
    }
}
}
}

---

### Post by trent.josephsen on 2015-06-10
First, the Head First books are great -- I have not personally used the Java one, but I think I can still say good choice.

I downloaded the code for the book from [here](http://www.headfirstlabs.com/books/hfjava/) and there is a difference between their GuessGame class and yours. I didn't find it in the [errata for the book](http://www.oreilly.com/catalog/errata.csp?isbn=9780596009205), so maybe you just copied it out wrong.

(BTW, a "syntax error" is something you might get if you misplaced a parenthesis -- your code wouldn't compile. What you have is a "logic error": the code compiles, but doesn't do what you want. Better known as a "bug" and sometimes referred to as a "feature".)

---

### Post by sypher2 on 2015-06-10
ah yes I should not have titled this "Syntax error", I see that now. thankyou for explaining that to me :) 
ok so, i downloaded what you downloaded to compare and make sure its the same as the book and yes it is. So i tried finding my error but i could not. I assume my error is in the area of where the random number is created, or where the players guesses are. could you please point out my mistake please?

---

### Post by spjackson on 2015-06-10
In the download, after
```

System.out.println("Game is over");

```
there is a break statement which exits the while  (true) loop. What you posted does not have this and therefore does not exit that loop.

---

### Post by sypher2 on 2015-06-10
ah i see.. it doesnt have a break in the book. Maybe its because my book only covers Java 5?? :/

---

### Post by trent.josephsen on 2015-06-10
No version of Java will magically break out of infinite loops ;-)

If the break is missing in the book, it's a mistake in the book. I encourage you to submit a report to the errata page I linked earlier. It's not uncommon for things to be accidentally deleted while a book is being prepared for printing. Having a report in the errata not only helps O'Reilly to fix it in future editions, but lets other people know what *should* have been there.

---

