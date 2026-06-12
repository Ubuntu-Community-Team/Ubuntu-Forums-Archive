---
title: "C++ function + vector + reference question"
date: 2009-06-17
forum: Programming Talk
---

### Post by Mirge on 2009-06-17
```

#include <iostream>
#include <sstream>
#include <string>
#include <vector>
#include "card.h"

using namespace std;

void BuildDeck(vector<Card>& deck);

int main()
{
    // Build a deck! A deck contains 52 cards (13 cards per suit, 4 suits).
    vector<Card> deck(52);
    BuildDeck(deck);

    // For testing purposes, lets spit out the entire deck!
    for(int i = 0; i < 52; i++) {
        cout << deck[i].GetValue() << " (" << deck[i].GetNumericValue() << ") of " << deck[i].GetSuit() << endl;
    }

    return 0;
}


void BuildDeck(vector<Card>& deck) {
    int counter = 0;
    
    // Set the suits.
    vector<string> SUITS;
    SUITS.push_back("Hearts");
    SUITS.push_back("Spades");
    SUITS.push_back("Diamonds");
    SUITS.push_back("Clubs");

    // BUILD OUR DECK OF CARDS!
    // Iterate through each suit, then iterate through all 13 cards for this particular suit.
    for(vector<string>::const_iterator suits_it = SUITS.begin(); suits_it != SUITS.end(); suits_it++) {
        for(unsigned int i = 2; i <= 14; i++) {
            stringstream ss;
            ss << i;
            string tmp_value = ss.str();
            
            if(tmp_value == "11")
                tmp_value = "Jack";
                
            if(tmp_value == "12")
                tmp_value = "Queen";
            
            if(tmp_value == "13")
                tmp_value = "King";
            
            if(tmp_value == "14")
                tmp_value = "Ace";
            
            deck[counter].SetSuit(*suits_it);
            deck[counter].SetValue(tmp_value);
            deck[counter].SetNumericValue(i);
            counter++;
        }
    }
}

```Ok, I'm building a "Blackjack" console game, basically menu-driven. I am sure the code isn't optimal, but I'm still learning, so please be gentle :).

My actual question is with the function I made... prototype:
**void BuildDeck(vector<Card>& deck);**

Now, it's my understanding that this, when used, passes a reference of the vector<Card> to the function, instead of creating a COPY of the vector<Card> to it.

Is that correct? I would imagine that it would be far more resource-friendly in more intensive applications, but I am still learning. It does work exactly as intended, and it spits out the deck just fine... I just want to make sure that the way I wrote it is actually working as I think it does before I go too much farther.

---

### Post by simeon87 on 2009-06-17
Yes, it's by reference; it's explained in detail here: [http://cplusplus.com/doc/tutorial/functions2/](http://cplusplus.com/doc/tutorial/functions2/) :)

---

### Post by Mirge on 2009-06-17
Ahh nice thanks, reading now..

---

### Post by Mirge on 2009-06-17
Yeah basically same thing I read in my books.. just wanted to make sure I had a firm grasp on what was really going on & didn't just "get lucky" with it lol.

---

### Post by monkeyking on 2009-06-17
A good thing to remember also,
is that if you only want to access(read) the value in the arguments you are passing.
Apply a const infront.
like

[PHP]
int test(const myObject &a);
[/PHP]

This can save  you many hours tracking down an unwanted modification of you object in some method you thought worked fine.

good luck

---

### Post by Mirge on 2009-06-17
Yeah, I've been trying to keep to that general guideline. Obviously, my BuildDeck() function needed to write to the vector.. but in my Card class, I use const for read-only accessor methods!

---

