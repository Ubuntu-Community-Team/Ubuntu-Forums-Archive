---
title: "Please Help Me Fix This - Java"
date: 2009-11-24
forum: Programming Talk
---

### Post by keygiwawah on 2009-11-24
I am making a deck of cards and then trying to shuffle them.
Here is my class for a card.
```

public class Card{
 int rank,suit;
 
 public Card(int s, int n){ 
  rank = n;
  suit = s;
 }
 
 public int getRank(){
  return rank;
 }
 
 public void setRank(int n){
  rank = n;
 }
 
 public int getSuit(){
  return suit;
 }
 
 public void setSuit(int s){
  suit = s;
 }
 public String toString(){
  String asdf = "";
  String fdsa = "";
 
  if(getSuit() == 0){
   asdf += "Spades";
  }
  else if(getSuit() == 1){
   asdf += "Diamonds";
  }
  else if(getSuit() == 2){
   asdf += "Clubs";
  }
  else{
   asdf += "Hearts";
  }
 
 
  if(getRank() == 0){
   fdsa += "2";
  }
  else if(getRank() == 1){
   fdsa += "3";
  }
  else if(getRank() == 2){
   fdsa += "4";
  }
  else if(getRank() == 3){
   fdsa += "5";
  }
  else if(getRank() == 4){
   fdsa += "6";
  }
  else if(getRank() == 5){
   fdsa += "7";
  }
  else if(getRank() == 6){
   fdsa+= "8";
  }
  else if(getRank() == 7){
   fdsa += "9";
  }
  else if(getRank() == 8){
   fdsa += "10";
  }
  else if(getRank() == 9){
   fdsa += "Jack";
  }
  else if(getRank() == 10){
   fdsa += "Queen";
  }
  else if(getRank() == 11){
   fdsa += "King";
  }
  else if(getRank() == 12){
   fdsa += "Ace";
  }
 
  return fdsa + " of " + asdf;
 }
}

```
 
Here is a class for the deck.
```

public class Deck{
 
  Card[] theDeck;  //decalres an array of integers.
  Card[] deckShuffled;  //decalres an array of integers.
  Card[] pickedNums;  //decalres an array of integers.
 
 public Deck(){
  theDeck = new Card[52];  //allocates memory for 52 cards.
  //This is the deck untouched.
 
  int x = 0;
 
  for(int i=0; i<4; i++){
 
   for(int c=0; c<13; c++){
 
    theDeck[x] = new Card(i,c);
    System.out.println(theDeck[x]);
    x++;
 
   }
  }
  //This has just created all of the cards in order.
 
  deckShuffled = new Card[52];  //allcates memory for 52 cards.
  /*This is where the shuffled deck will be, cards are randomly placed
  here from the deck.*/
 
  pickedNums = new Card[52];  //allocates memory for 52 cards.
  /*This will contain the cards that were transfered from deck to 
  deckShuffled and will be used to stop cards from being used multiple times.
  */
 
  int[] PickedNums = new int[52];
  for(int i =0; i<PickedNums.length; i++){
   PickedNums[i] = -1;
  }
 
  int pickedNumsIndex = 0, shuffledNumsIndex = 0, num = 0;
  boolean hasBeenPicked = true;
  while(shuffledNumsIndex<=51){
   System.out.println("shuffled nums index: "+shuffledNumsIndex);
   while(hasBeenPicked){
    num = (int)(Math.random()*52.0);
    System.out.println(num);
    for(int c=0; c <= pickedNumsIndex; c++){
     if(num == PickedNums[c]){
      System.out.println("num has been found at: "+c);
      hasBeenPicked = false;
     }
     else{
      hasBeenPicked = true;
      break;
     }
 
    }
   }
   hasBeenPicked = true;
   PickedNums[pickedNumsIndex] = num;
   pickedNumsIndex++;
 
   deckShuffled[shuffledNumsIndex] = theDeck[num];
   shuffledNumsIndex++;
  }
 theDeck = deckShuffled;
 
 }
 
 
 
}

```
I am having trouble with my deck shuffling. It seems to be stuck in an infinate loop, and I am not sure how to fix it. I printed out num to show the infinate loop, you can just delete that if you don't need it. Please show me how to fix it using my code, not by introducing entirely new concepts. I am new to java and may not be using the most eficient methods to solve problems.
 
Here is my driver.
```

public class DeckDriver{
 public static void main(String[]args){
 
  Deck asdf = new Deck();
 }
}

```

---

### Post by Reiger on 2009-11-24
```

  int[] PickedNums = new int[52];
  for(int i =0; i<PickedNums.length; i++){
   [COLOR="#ff0000"]PickedNums[i] = -1;[/COLOR]
  }
 
  int pickedNumsIndex = 0, shuffledNumsIndex = 0, num = 0;
  boolean hasBeenPicked = true;

  while(shuffledNumsIndex<=51){
   System.out.println("shuffled nums index: "+shuffledNumsIndex);
   [COLOR="Red"]**while(hasBeenPicked)**[/COLOR]{
    [COLOR="#ff0000"]**num = (int)(Math.random()*52.0);**[/COLOR]
    System.out.println(num);
    for(int c=0; c <= pickedNumsIndex; c++){
     if([COLOR="#ff0000"]num == PickedNums[c][/COLOR]){
      System.out.println("num has been found at: "+c);
      hasBeenPicked = false;
     }
    [COLOR="#ff0000"] else{
      hasBeenPicked = true;[/COLOR]
      break;
     }
 
    }
   }
   [COLOR="#ff0000"]hasBeenPicked = true;[/COLOR]
   PickedNums[pickedNumsIndex] = num;
   pickedNumsIndex++;
 
   deckShuffled[shuffledNumsIndex] = theDeck[num];
   shuffledNumsIndex++;
  }
 theDeck = deckShuffled;
 
 }

```

I'm not fully awake at the moment (see my other comments in the last few minutes) but I thought I'd mark some of the more suspicious lines of code anyways.

As far as I can see you are initializing an array to -1 (not yet drawn) cards then try to fill them and use a comparison to check whether or not a card has been visited yet. But it seems to me that the proper check for visited or not is not an equality but a not-equality. Namely if PickedNums[num] != -1 this should correspond to an initialised card right?

Anyways: have you considered a more lazy approach? Why shuffle a complete Deck when you can simply use fixed constants to denote cards and randomly draw such a constant? -- Only when you need to actually _have_ a value?

Using your code you could do this somewhat like so:
```

Card[] drawn = new Card[52];
int sumOfDrawn = 0; // progress measurement
int sumOfAllCards = 1378; // 52 * (52 + 1) / 2 = 53 * 26 = 1378. Courtesy of Gauss.
// check whether or not the Deck is empty (i.e. all Cards have been dealt).
boolean empty() {
   return sumOfAllCards == sumOfDrawn;
}

// randomly select a Card from the remaining Deck
Card dealCard() {
  if(empty()) {
    return null;
  }
  do {
  int i= ... // obtain a random number
  }
  while(drawn[i] !=null ) // if dealt already; attempt again

  drawn[i] = new Card(/* params based on i */);
  sumOfDrawn += (i + 1);
  return drawn[i];
}
```

Furthermore you can make your life easier by learning about the switch() statement for comparing an integer to many possible cases; and you can make your code simpler by learning about Enum types. In actual fact, the very tutorial on Enum types features the Card/Deck scenario.

---

