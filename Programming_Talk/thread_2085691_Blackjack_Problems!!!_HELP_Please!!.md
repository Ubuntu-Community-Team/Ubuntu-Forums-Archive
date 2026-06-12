---
title: "Blackjack Problems!!! HELP Please!!"
date: 2012-11-18
forum: Programming Talk
---

### Post by mhaggard on 2012-11-18
can someone please help me? I am stuck just trying to make the deck. My partner and I have been working on this for about two weeks now and I have decided to pretty much scrap the other code and make a new one. The project is due tonight (I know good timing huh) and I don't understand why it keeps telling me that 'class Deck has no member named push.'

Any help would be appreciated

```

// Blackjack
#include <iostream>
#include <stack>
#include <string>
#include <vector>
#include <cstdlib>
#include <fstream>
#include <ctime>

using namespace std;

string suit[4] = { "CLUBS", "DIAMONDS", "HEARTS", "SPADES" };
string value[13] = { "ACE", "TWO", "THREE", "FOUR", "FIVE", "SIX", "SEVEN", "EIGHT", "NINE", "TEN", "JACK", "QUEEN", "KING" };

struct Card {
	int value, suit;
	Card(int value, int suit);
	string toString();
	};

class Deck{
	public:
		stack<Card> deck;
	};
	
int main(){
	Deck deck;
	
	for(int i = 0; i < 13; i++){
		for(int j = 0; j < 4; j++){
			Card card(i, j);
			deck.push(card);
			}
		}



	return 0;
	}

```

---

### Post by Vaphell on 2012-11-18
because in main() you define *deck* as Deck object and call push() on it and in Deck class there is no push method. There is another *deck* (stack) which probably has push().

in other words you need *deck.deck.push(card)* - reusing generic names is confusing so you shouldn't do that.

---

### Post by mhaggard on 2012-11-18
Thanks a bunch. How is a better way to do it instead of using generic words? That might be a stupid question. Sorry in advance.

---

### Post by Tony Flury on 2012-11-20
> **mhaggard said:**
> Thanks a bunch. How is a better way to do it instead of using generic words? That might be a stupid question. Sorry in advance.

For instance : 

The type could be generic - DeckofCards

The instance should be specific - MyDeck, DealersDeck, MainDeck

If I were defining this I might use
```

struct SingleCard {
	int value, suit;
	SingleCard (int value, int suit);
	string toString();
	};


class DeckofCards{
	public:
		stack<SingleCard> Cards;
	};


int main(){
	DeckofCards MainDeck;
	
	for(int i = 0; i < 13; i++){
		for(int j = 0; j < 4; j++){
			SingleCard ThisCard(i, j);
			MainDeck.Cards.push(ThisCard);
			}

```

You could also use a naming convention - for instance - prefix class names with cls_ - that might help too.

---

### Post by Bucky Ball on 2012-11-20
***Thread Closed***

[QUOTE=mhaggard]How is a better way to do it instead of using generic words? That might be a stupid question. Sorry in advance.[/QUOTE]

Please be aware, from the code of conduct:

> While we are happy to serve as a resource for hints and for asking  questions when you get stuck and need a little help, the Ubuntu Forums  is not a homework service. Please do not post your homework assignments  expecting someone else to do it for you. Any such threads will be taken  offline and warnings or infractions may be issued.

What people usually say is 'but it's not homework, it is a major such and such'. No matter. It is still work that should be (or should have been) rightfully done by the user. There are/should be plenty of fellow students and staff to help with this.

This does not prevent you continuing the dialogue via PM. That is between two consenting parties ...

---

