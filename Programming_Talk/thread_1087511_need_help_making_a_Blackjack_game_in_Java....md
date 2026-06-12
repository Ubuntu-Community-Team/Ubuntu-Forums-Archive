---
title: "need help making a Blackjack game in Java..."
date: 2009-03-05
forum: Programming Talk
---

### Post by Mia_tech on 2009-03-05
guys, I'm working on a project for class, and it's about making a Blackjack game (console) no gui, and I'm in need for ideas to make my code simpler, and also how I could implement the deal, hitme, stay methods, and if anyone could suggest me a better way to store all the 52 cards I'll appreciate, as you can see I input them one by one into the arraylist.... I'm not asking to do it for me just ideas, or any suggestions are welcome

```
public class cards {

    String suit = "";
    String cardType = "";

    public cards(String s, String c)
    {
        this.suit = s;
        this.cardType = c; 
    }

    public String getcardType()
    {
        return cardType;
    }
    public String getsuit()
    {
        return suit;
    }
    @Override
    public String toString()
    {
        return suit + " of " + cardType;
    }

}
```

```
public class Game {
    public String Deal()
    {
        
    }
    public String hitme()
    {

    }
    public String stay()
    {

    }
}
```

```
import java.util.*;
import java.util.Scanner;
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        Scanner in = new Scanner(System.in);
        ArrayList<cards> cardDeck = new ArrayList<cards>();

        cardDeck.add(new cards("Ace", "diamonds"));
        cardDeck.add(new cards("2", "diamonds"));
        cardDeck.add(new cards("3", "diamonds"));
        cardDeck.add(new cards("4", "diamonds"));
        cardDeck.add(new cards("5", "diamonds"));
        cardDeck.add(new cards("6", "diamonds"));
        cardDeck.add(new cards("7", "diamonds"));
        cardDeck.add(new cards("8", "diamonds"));
        cardDeck.add(new cards("9", "diamonds"));
        cardDeck.add(new cards("10", "diamonds"));
        cardDeck.add(new cards("Jack", "diamonds"));
        cardDeck.add(new cards("Queen", "diamonds"));
        cardDeck.add(new cards("King", "diamonds"));
        
        cardDeck.add(new cards("Ace", "hearts"));
        cardDeck.add(new cards("2", "hearts"));
        cardDeck.add(new cards("3", "hearts"));
        cardDeck.add(new cards("4", "hearts"));
        cardDeck.add(new cards("5", "hearts"));
        cardDeck.add(new cards("6", "hearts"));
        cardDeck.add(new cards("7", "hearts"));
        cardDeck.add(new cards("8", "hearts"));
        cardDeck.add(new cards("9", "hearts"));
        cardDeck.add(new cards("10", "hearts"));
        cardDeck.add(new cards("Jack", "hearts"));
        cardDeck.add(new cards("Queen", "hearts"));
        cardDeck.add(new cards("King", "hearts"));


        cardDeck.add(new cards("Ace", "clubs"));
        cardDeck.add(new cards("2", "clubs"));
        cardDeck.add(new cards("3", "clubs"));
        cardDeck.add(new cards("4", "clubs"));
        cardDeck.add(new cards("5", "clubs"));
        cardDeck.add(new cards("6", "clubs"));
        cardDeck.add(new cards("7", "clubs"));
        cardDeck.add(new cards("8", "clubss"));
        cardDeck.add(new cards("9", "clubs"));
        cardDeck.add(new cards("10", "clubs"));
        cardDeck.add(new cards("Jack", "clubs"));
        cardDeck.add(new cards("Queen", "clubs"));
        cardDeck.add(new cards("King", "clubs"));
        
        cardDeck.add(new cards("Ace", "spades"));
        cardDeck.add(new cards("2", "spades"));
        cardDeck.add(new cards("3", "spades"));
        cardDeck.add(new cards("4", "spades"));
        cardDeck.add(new cards("5", "spades"));
        cardDeck.add(new cards("6", "spades"));
        cardDeck.add(new cards("7", "spades"));
        cardDeck.add(new cards("8", "spades"));
        cardDeck.add(new cards("9", "spades"));
        cardDeck.add(new cards("10", "spades"));
        cardDeck.add(new cards("Jack", "spades"));
        cardDeck.add(new cards("Queen", "spades"));
        cardDeck.add(new cards("King", "spades"));

        //deal
        System.out.println(cardDeck.get((int)(Math.random()*52)));
        System.out.println(cardDeck.get((int) (Math.random()*52)));
    }
}

```

---

### Post by Mia_tech on 2009-03-05
well, I give the card notation, a second thought I realize that there's a much better (simpler) way of doing it... probably there are better ones, but here's mine


```
String suit[] = {"Spade", "Hearts", "Clubs", "Diamonds"};
        String number[] = {"Ace","2","3","4","5","6","7","8","9","10","Jack","Queen","King"};
        for(int i = 0; i < suit.length; i++)
        {
            for(int j = 0; j < number.length; j++)
            {
                cardDeck.add(new cards(suit[i], number[j]));
            }
        }
```

---

### Post by simeon87 on 2009-03-05
Well, the for-loop is certainly an improvement over the previous way of writing it ;)

> and also how I could implement the deal, hitme, stay methods

First I'd add some variables to keep track of the state of the game: whose turn is it and what cards does each player have (and the remaining cards would still be in the deck). After that, the deal, hitme and stay methods involve updating that state (i.e., taking a card from the deck and giving it to the current player, changing the turn, etc).

---

### Post by DocForbin on 2009-03-05
A few comments:

- Use String[] suit, etc. instead of String suit[]. While the latter works, the preferred convention is to use the former

- Consider a for each loop instead, e.g. for(String thisSuit : suit)

- Class names should be upper case

- consider changing number to rank and give each rank a weight number (aces will be a bit tricky since their weight varies).

hth

---

### Post by Drone022 on 2009-03-05
Hey, I tried something similar a while ago, here are a few things I did, you might/might not want to take these on board.

Card Ranks:

```

package cardgame;

public enum Rank { 
   TWO, THREE, FOUR, FIVE, SIX, SEVEN,
   EIGHT, NINE, TEN, JACK, QUEEN, KING, ACE 
}

```

Suits :
```

package cardgame;

public enum Suit { 
   CLUBS,
   DIAMONDS,
   HEARTS, 
   SPADES 
}

```

A Card:
```

public class Card {
    private final Rank rank;
    private final Suit suit;

    public Card(Rank rank, Suit suit) {
        this.rank = rank;
        this.suit = suit;
    }

    public Suit getSuit() {
        return suit;
    }

    public Rank getRank() {
        return rank;
    }

    public String toString() {
        return rank + " of " + suit;
    }
    
    public boolean equals(Card card) {
        if (this.suit == card.suit && this.rank == card.rank)
            return true;
        return false;
    }
}

```

Creates the deck of cards in a vector then you just write functions for things you want to do to the deck:
```

public class Deck {
    
    private static Vector<Card> cards = new Vector<Card>();
    
    /* Create a new deck of 52 cards */
    public Deck() {
        for (Suit suit : Suit.values()) {
            for (Rank rank : Rank.values()) {
                cards.add(new Card(rank, suit));
                cards.trimToSize();
            }
        }
    }

    public Card getFirstCard()
    public Deck removeCard(Card card) 
    public void shuffle()



```

Obviously for blackjack you'll want to attach values as previously suggested. Hope some of this helps.

---

### Post by Mia_tech on 2009-03-05
guys, how could I implement the deal, and hitme method that returns a random number from 1 to 52 which is the size of the array, but insead of having it on the main method I want to implement it on a class by itself... I'm trying to do something like 

```
cardDeck.get((int)(Math.random()*52))
```

---

### Post by kavon89 on 2009-03-05
> **Mia_tech said:**
> guys, how could I implement the deal, and hitme method that returns a random number from 1 to 52 which is the size of the array, but insead of having it on the main method I want to implement it on a class by itself... I'm trying to do something like 

```
cardDeck.get((int)(Math.random()*52))
```

Use the Random class:

```

Random rand = new Random();
cardDeck.get(rand.nextInt(cardDeck.size()));

```

That should generate a value from 0-51 if size() returns 52. (includes 0 but not the value you specify)

---

### Post by Mia_tech on 2009-03-06
yes, I'm still trying to get this working, but now I face two major constraint, and one is that instead of having the big portion of my program decision making code in the main, I would've like to have it in a different class like "Game" or "Blackjack" and implement methods like "hitme", "deal", "stay", but I didn't find a way to do it.... could anyone make a suggestion?... also I can't put the result of the ```
cardDeck.get((int)(Math.random()*52))
``` inside a int variable so I can keep the score... also need help here!
here's what I've got

Card Class
```
public class Cards {
    String suit = "";
    String cardType = "";

    public Cards(String suit, String cardType)
    {
        this.suit = suit;
        this.cardType = cardType;
    }
    public String getSuit()
    {
        return suit;
    }
    public String getcardType()
    {
        return cardType;
    }
    @Override
    public String toString()
    {
        return cardType+" of "+suit;
    }

}
```

main class
```

import java.util.*;
import java.util.Scanner;
public class Main {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        Scanner myscan = new Scanner(System.in);
        //making the deck of cards
        ArrayList<Cards> cardDeck = new ArrayList<Cards>();
        String[] suit = {"Spade", "Hearts", "Clubs", "Diamonds"};
        String[] number = {"Ace","2","3","4","5","6","7","8","9","10","Jack","Queen","King"};
        for(int i = 0; i < suit.length; i++)
        {
            for(int j = 0; j < number.length; j++)
            {
                cardDeck.add(new Cards(suit[i], number[j]));
            }
        }
        //Starting the Game!
        System.out.println("*****************************");
        System.out.println("****     WELCOME         ****");
        System.out.println("****       TO            ****");
        System.out.println("****    BLACKJACK        ****");
        System.out.println("*****************************");

        //User Playing
        int userTotal = 0;
        int total = 0;
        System.out.println("\n");
        System.out.println("*****User Playing******");
        System.out.println("Press enter to start!"+"\n");
        myscan.nextLine();
        for(int i = 0; i < 2; i++)
        {
            //deal two cards
            System.out.println(cardDeck.get((int)(Math.random()*52)));
        }

        while(userTotal < 21)
        {
            System.out.println("\n"+"Press 1(hit) or 2(stay)");
            int key = myscan.nextInt();
        if( (key == 1) && (userTotal < 21))
        {
            //hit me
            System.out.println(cardDeck.get((int)(Math.random()*52)));
            userTotal += total;
            if(userTotal > 21)//if user goes over 21, tell him "busted"
            {
                System.out.println("you are busted!");
                break;
            }
        }
        else
        {
            //user stay--> give user total
            System.out.println("you stay, and have a total of: "+userTotal);
            break;
        }
        }


        //computer playing!
        int computerTotal = 0;
        System.out.println("****** Computer Playing *********");
        for(int i = 0; i < 2; i++)
        {
            System.out.println(cardDeck.get((int)(Math.random()*52)));//deal two card for computer
        }

        while(computerTotal < 21)
        {
            System.out.println("press enter to deal another card!");
            myscan.next();
            System.out.println(cardDeck.get((int)(Math.random()*52)));//hit computer until makes 21 or busted
            if(computerTotal > 21)
            {
                System.out.println("Computer busted!"+computerTotal);//comptuer busted
                break;
            }
            else if(computerTotal == 21)
            {
                System.out.println("Comptuer Wins!");//comptuer wins 21
            }
        }


        if((userTotal < 21) && (userTotal > computerTotal))
        {
            System.out.println("User Wins!");
        }
        else System.out.println("Comptuer Wins!");
        
    }

}

```

---

### Post by HotCupOfJava on 2009-03-06
> **Drone022 said:**
> 

Creates the deck of cards in a vector then you just write functions for things you want to do to the deck:


Yes, well, unless you are using an older version of Java the Arraylist is a much better option than the Vector class.....

---

### Post by DocForbin on 2009-03-06
> **HotCupOfJava said:**
> Yes, well, unless you are using an older version of Java the Arraylist is a much better option than the Vector class.....

A Hashset (or Hashmap, depending on implementation) seems a better fit here.

---

### Post by Mia_tech on 2009-03-06
is there any way to make the result of

```
cardDeck.get((int)(Math.random()*52))
```

into an integer?

---

### Post by kavon89 on 2009-03-07
> **Mia_tech said:**
> is there any way to make the result of

```
cardDeck.get((int)(Math.random()*52))
```

into an integer?

Well, if your cardDeck is an ArrayList<Card> (an arraylist of Card objects), just get a random index within the list and then call some sort of "getNumericalValue()" on the Card which returns an integer. I recommend the use of an enum for all of this like someone else posted as example code.

---

### Post by simeon87 on 2009-03-07
Also, you're now taking a random card from the deck but you also need to keep track of those cards (because then you also know which cards are still *in* the deck). The reason is: the next time you draw a random card, you can't draw a card that has already been given to a player.

---

### Post by HotCupOfJava on 2009-03-07
> **Mia_tech said:**
> is there any way to make the result of

```
cardDeck.get((int)(Math.random()*52))
```

into an integer?

Well, it looks like the result is being cast into an integer, which is how you get integer results from the Math.random() method. Math.random() returns a double greater than 0.0 and less than 1.0. So, you have to multiply the result by whatever range you're looking for (like the example shows, "52") and then cast the result to an integer ( "(int)" ) to get whole-numbers.

---

### Post by tneva82 on 2009-03-07
> **simeon87 said:**
> Also, you're now taking a random card from the deck but you also need to keep track of those cards (because then you also know which cards are still *in* the deck). The reason is: the next time you draw a random card, you can't draw a card that has already been given to a player.

Howabout solving this so that when you begin you shuffle the deck into random order into list and then when you need a card you pop first card out(thus removing it from the list). No need to keep track of which you have taken since list takes care of that automaticly.

That's how I would do it.

---

### Post by simeon87 on 2009-03-07
> **tneva82 said:**
> Howabout solving this so that when you begin you shuffle the deck into random order into list and then when you need a card you pop first card out(thus removing it from the list). No need to keep track of which you have taken since list takes care of that automaticly.

That's how I would do it.

Keeping track of things can be done explicitly and implicitly :) Though, to check whether a card is still in the deck, you'd need to walk over the whole (remaining) deck. In this case, n = 52 so it wouldn't matter performance wise but a boolean array with length 52 would improve it to O(1).

---

