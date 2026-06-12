---
title: "basic C++ question"
date: 2008-08-29
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-08-29
hi

so in my learning of C++ ive found something that no tutorial seems to explain...

for the main() ive seen different people pass different parameters to it but ive never gotten an explanation also ive seen people pass no parameters...whats the difference?

---

### Post by Tony Flury on 2008-08-29
The parameters for main are the standard method of capturing and processing the command line arguments that might be passed to your application.

so if you declare : 
```

int main( int argc, char **argv[])
{
....
}

```

comple the code into the /home/me directory with the name program

and then invoke the program by using : 
```

/home/me/progam hello world

```

then in your program then argc and argv will be : 

```

argc = 2
argv[0] = "/home/me/program"
argv[1] = "hello"
argv[2] = "world"

```

There are libraries available to help you process the command line options : see getopt for instance.

I hope this helps

---

### Post by jimi_hendrix on 2008-08-29
so they arnt mandatory and they just help with command line processing?

---

### Post by nicolaary on 2008-08-29
The parameters are the input into the application

---

### Post by Tony Flury on 2008-08-29
in C++ they are not mandatory as far as i know - I am not 100% sure about C, but I think they are optional there too :-)

If you are happy that the question has been answered, can you amrk the thread as solved so everyone else knows - thanks.

---

### Post by jimi_hendrix on 2008-08-29
ok

ty

---

### Post by dribeas on 2008-08-29
> **Tony Flury said:**
> in C++ they are not mandatory as far as i know - I am not 100% sure about C, but I think they are optional there too :-)

The C++ standard (don't have time to quote, but if I find it I will edit this post) says that all programs must have one and only one main function defined with either of this signatures:
```

int main();
int main( int argc, char* argv[] );

```
Main will be the entry point for the application, it must not be called from the code (user cannot explicitly call main() ) and it is the only function that having a non-void return type can return nothing (either don't call return at all or return with no value) in which case the compiler must introduce an implicit return 0; statement.
```

int f() {}  // error, must return int [*]
int main() {} // valid, compiler must insert an implicit return 0
// int main() { return; } // this would also be valid

```

There can only be one main function in the application.

	David

[*] Note that g++ does not follow the standard here, and won't complain on this line, but it should. It won't complain even with -Wall. You need to pass -Wreturn-types to get help you debug this.

---

### Post by jimi_hendrix on 2008-08-29
1 more question...when you declare the main int thing...does it have to be an int? or can you just declare it void

---

### Post by kpatz on 2008-08-29
> **Tony Flury said:**
> so if you declare : 
```

int main( int argc, char **argv[])
{
....
}

```
Actually, that second argument should either be *argv[] or **argv (an array of char pointers, not an array of pointers to char pointers).

Here's an example:

```

#include <iostream>
using namespace std;

int main(int argc, char *argv[])
{
  cout << "argc is " << argc << endl;
  for (int i = 0; i < argc; i++)
    cout << "argv[" << i << "] is " << argv[i] << endl;
  return 0;
}

```

And compiling/running it:

```

kpatz@zuul:~$ g++ -o args args.cpp
kpatz@zuul:~$ ./args hi there
argc is 3
argv[0] is ./args
argv[1] is hi
argv[2] is there
kpatz@zuul:~$

```

As for main(...) being declared as int, you could declare it void, but int is the standard convention for main, and allows you to return a return value.

```

kpatz@zuul:~$ cat returnavalue.cpp
int main()
{
  return 123;
}
kpatz@zuul:~$ g++ -o returnavalue returnavalue.cpp
kpatz@zuul:~$ ./returnavalue
kpatz@zuul:~$ echo $?
123
kpatz@zuul:~$ 

```

---

### Post by Tony Flury on 2008-08-29
kpatz : you are entirely correct about the char **argv[] error - did mean to go back and check but i was too eager on the submit button :)

---

### Post by nvteighen on 2008-08-29
> **Tony Flury said:**
> in C++ they are not mandatory as far as i know - I am not 100% sure about C, but I think they are optional there too :-)

Yes, in C they're optional. 

But, I don't know if C++ allows you to change the variables' names as C does. I mean, C will admit your code as valid if you declare main() as:

[PHP]
/* This is C, not C++ */
int main(void); /* Off-topic: (void) is a C-quirk... don't know if also 
                 * C++'s */
int main(int, char **); 
[/PHP]

So, I could define main as "**int main(int hello, char **world)**" and it would still be correct, because what matters is the data type. But, argc and argv are a sort of tradition, even in languages not related to C, like Python (sys.argv and sys.argc)...

But, I've heard that there's a third possibility to grab environment variables from shell... I suppose it isn't standard and it smells like a GNU extension, but can someone confirm that?

---

### Post by Tony Flury on 2008-08-29
> **nvteighen said:**
> 
But, I've heard that there's a third possibility to grab environment variables from shell... I suppose it isn't standard and it smells like a GNU extension, but can someone confirm that?

Posix allows a declaration of the form : 
```

int main( int c, char *argv[], char *envp[] )
{
...
}

```
Which allows access to the environment variables using envp.
The last entry in the envp array is always a NULL string - you can enumerate the array using : 
```

for (int n=0; envp[n]; n++)

```

[http://www.informit.com/guides/content.aspx?g=cplusplus&seqNum=136](http://www.informit.com/guides/content.aspx?g=cplusplus&seqNum=136) has details which will correct any errors in my text.

---

### Post by happysmileman on 2008-08-29
> **jimi_hendrix said:**
> 1 more question...when you declare the main int thing...does it have to be an int? or can you just declare it void

It shouldn't be declared void but many compilers tolerate it. (They basically treat it like it's returning an int and return 0 by default)

---

### Post by jimi_hendrix on 2008-08-29
> **happysmileman said:**
> It shouldn't be declared void but many compilers tolerate it. (They basically treat it like it's returning an int and return 0 by default)

then why make it an int?

---

### Post by LaRoza on 2008-08-29
> **jimi_hendrix said:**
> then why make it an int?

Because that is what it is supposed to be. Don't use tolerant compilers as an excuse for sloppy or non-standard code.

---

### Post by kjohansen on 2008-08-29
> **jimi_hendrix said:**
> 1 more question...when you declare the main int thing...does it have to be an int? or can you just declare it void
the main function must be of type return type int in C and C++.

Here is a wikipedia link talking about main functions across different languages.
[http://en.wikipedia.org/wiki/Main_function_(programming](http://en.wikipedia.org/wiki/Main_function_(programming))

---

### Post by jimi_hendrix on 2008-08-29
> **LaRoza said:**
> Because that is what it is supposed to be. Don't use tolerant compilers as an excuse for sloppy or non-standard code.

i ment why make it an int as standard if it returns 0?

---

### Post by stevescripts on 2008-08-29
0 == zero ...

---

### Post by nvteighen on 2008-08-29
> **jimi_hendrix said:**
> i ment why make it an int as standard if it returns 0?

The standard says main() has to return an integer. Usually, the convention is to return 0 when no errors were produced and something else when there were errors.

Why? Welcome to structured programming! The idea is that functions have to communicate eachother using return values. That should be familiar to you... but main() is also a function, the difference just relies in that main() is called from another program instead from one of the program's functions...

So, the main's return value is used to communicate your whole program with the outside. There are ways to get that value and make the caller do something.

---

### Post by LaRoza on 2008-08-29
> **jimi_hendrix said:**
> i ment why make it an int as standard if it returns 0?

The return value has a meaning you know. Returning 0 is a success code for most apps. 

(I just ran aptitude as non root and with a weird option, and the program exits with "255" (use 'echo $?' to get the return value))

It is used in shell scripts and other tasks to determine if there were no errors.

---

### Post by jimi_hendrix on 2008-08-29
> **LaRoza said:**
> The return value has a meaning you know. Returning 0 is a success code for most apps. 

(I just ran aptitude as non root and with a weird option, and the program exits with "255" (use 'echo $?' to get the return value))

It is used in shell scripts and other tasks to determine if there were no errors.

ty

i just tried that...who came up with the thing that says "this aptitude does not have super cow powers"?

---

### Post by jimi_hendrix on 2008-08-29
last question...this is a compiling error...so im making a poker game in the terminal and i just want to see if i made the cards right

heres my main loop
```
int main()
{
	Deck myDeck(1);
	int t = 0;
	while (t < 52 )
	{
		cout << myDeck.cards[t] << endl;
	}
	return 0;
}
```

i get these errors

```
test.cpp:80: error: new types may not be defined in a return type
test.cpp:80: error: two or more data types in declaration of &#8216;main&#8217;
```

---

### Post by cmay on 2008-08-29
> test.cpp:80: error: new types may not be defined in a return type
test.cpp:80: error: two or more data types in declaration of &#8216;main&#8217;
its been so long ago i has anything to do whit c++ but it looks
like the error is in a function ? .there is warning cpp:80 which means line number 80.how many lines is your program.
>  Deck myDeck(1); 
what ever this is and what is happening there it looks as if it must be the course. 
i cant help you that much as i dont renember very much of c++ but i guess the error is somewhere in these lines that has to do whit deck(1);
maybe post the whole code and someone could check it if you get stuck.

edit:
this link is to a c++ on windows only forum but a lot of answers can be found there just by reading the posts.
not all of the questions you may have but many of the beginning c++ questions is likely to be answered in a place like this.
[http://sourceforge.net/forum/forum.php?forum_id=48211](http://sourceforge.net/forum/forum.php?forum_id=48211)
a good exercise is to read all the post and guess the solutions from reading the compiler logs first before checking the answers giving. i used to do this often but it  has been a long time ago.
hope it helps :)

---

### Post by Lux Perpetua on 2008-08-29
> **jimi_hendrix said:**
> last question...this is a compiling error...so im making a poker game in the terminal and i just want to see if i made the cards right

heres my main loop
```
int main()
{
	Deck myDeck(1);
	int t = 0;
	while (t < 52 )
	{
		cout << myDeck.cards[t] << endl;
	}
	return 0;
}
```

i get these errors

```
test.cpp:80: error: new types may not be defined in a return type
test.cpp:80: error: two or more data types in declaration of ‘main’
```I don't think the error is in the code you posted. I'm guessing you forgot a semicolon somewhere before your main function. If you post the rest of your program, someone will spot it.

---

### Post by jimi_hendrix on 2008-08-29
ok ill post all the code

[PHP]#include <iostream>

#include <iostream>

using namespace std;

struct Deck
{
   int decks;
   Deck(int Decks)
   {
	decks = Decks*52;
	int cards[decks*52];
	int cardnumber;
	for (int i = 0; i < decks; i++)
	{
		for (int card = 0; card < 52; card++)
		{
			cards[card] = cardnumber;
			cardnumber++;
			if (cardnumber == 9)
			{
				cards[(card + 1)] = 10;
				cards[(card + 2)] = 10;
				cards[(card + 3)] = 10;
				cards[(card + 4)] = 10;
				cardnumber = 2;
			}
		}
	}
   }
}


int main()
{
	Deck myDeck(1);
	int t = 0;
	while (t < 52 )
	{
		cout << myDeck.cards[t] << endl;
	}
	return;
}
[/PHP]

if you can think of a simpler way to assign values to the cards it would be cool but i just want to compiler error fixed

---

### Post by samjh on 2008-08-29
You need a ";" after your struct declaration:
```
struct MyStruct
{
    ....
};
```

---

### Post by monkeyking on 2008-08-29
Futhermore,
the datatype called cards, isn't visible from outside. the Deck() function.
You should declare cards just belowe decks;

---

### Post by jimi_hendrix on 2008-08-29
> **monkeyking said:**
> Futhermore,
the datatype called cards, isn't visible from outside. the Deck() function.
You should declare cards just belowe decks;

isnt it public in a struct thought?

---

### Post by monkeyking on 2008-08-29
afaik all vars declared in a function only exist in that scope.
btw i recommend compiling with

```
g++ -g
```
This will catch many minor mistakes and unused variabels.

Didn't your compilation attempt catch this?

---

### Post by jimi_hendrix on 2008-08-29
nope

edit: it did after i put the semi colon

---

### Post by samjh on 2008-08-29
I just noticed another problem:

C++ does not support variable array declarations.  The size of an array MUST be a constant, it cannot be a variable.

WRONG:
int cards[variable];

RIGHT:
int cards[100]; //substitute 100 with another integer constant.

For variable arrays, try using [vector](http://www.cplusplus.com/reference/stl/vector/) instead.

---

### Post by monkeyking on 2008-08-29
I don't really have an idea on what your trying to do. :)

but a different approach, you should know when you want a variable sized array, is to make it dynamic.
btw I think you should put a return value of 0 into your main

[PHP]
int *array;
array = new int[length];
[/PHP]

---

### Post by dwhitney67 on 2008-08-29
> **jimi_hendrix said:**
> last question...this is a compiling error...so im making a poker game in the terminal and i just want to see if i made the cards right
...

Poker in C++ is not as "basic" as one would hope.  It would have been nice if you had started a new thread to present your game questions.

Anyhow, I look at your posts (including the one on page 4?), and I think you are almost on the right track concerning the design of the game, however I think the design would be a lot easier if you consider defining a Card object.  Your Deck object needs to create these Card objects, shuffle them, and then place them in a "Shoe", where the Shoe container behaves as a FIFO queue.

I took the liberty to write a little code this evening based on the Poker game, although it is far from complete.  See if you can use any of the ideas in your game.

Here it is...
[php]
#include <queue>
#include <vector>
#include <iostream>


struct Card
{
  enum Suit { HEART, DIAMOND, CLUB, SPADE, MARKER, END };

  // Member data
  //
  Suit         suit;
  unsigned int face;
  unsigned int value;

  // Functions
  //
  bool isEnd() const
  {
    return suit == END;
  }

  friend std::ostream& operator<<( std::ostream &os, const Card &card )
  {
    switch( card.face )
    {
      case  0: break;

      case  1: os << "Ace";   break;
      case 11: os << "Jack";  break;
      case 12: os << "Queen"; break;
      case 13: os << "King";  break;

      default: os << card.face; break;
    }

    switch ( card.suit )
    {
      case HEART:   os << " of Hearts";    break;
      case DIAMOND: os << " of Diamonds";  break;
      case CLUB:    os << " of Clubs";     break;
      case SPADE:   os << " of Spades";    break;
      case MARKER:  os << "Marker";        break;
      case END:     os << "End of Cards!"; break;
    }

    return os;
  }
};


class Deck
{
  private:
    typedef std::queue< Card >  Shoe;
    typedef std::vector< Card > Cards;

  public:
    // Constructor
    //
    Deck( size_t numDecks = 1 ) : m_numDecks(numDecks)
    {
      setupCards();
    }


    // Shuffle the Cards, then insert into the Shoe
    //
    void shuffle()
    {
      // Shuffling algorithm goes here...
      //
      // TODO	TODO	TODO	TODO	TODO	TODO	TODO
      //
      Cards shuffledCards( m_cards.begin(), m_cards.end() );   // for now; replace later
      //
      // TODO	TODO	TODO	TODO	TODO	TODO	TODO


      // Insert shuffled cards into the Shoe...
      //
      bool markerInserted = false;

      for ( Cards::iterator it = shuffledCards.begin(); it != shuffledCards.end(); ++it )
      {
        m_shoe.push( *it );

        // insert the marker card at approximately the 75% mark
        //
        if ( markerInserted == false &&
             (shuffledCards.size() - m_shoe.size()) / (float)(shuffledCards.size()) <= 0.25 )
        {
          Card marker = { Card::MARKER, 0, 0 };
          m_shoe.push( marker );
          markerInserted = true;
        }
      }
    }


    // Obtains the Card at the front of the Shoe; note this may be
    // the marker card.
    //
    Card dealCard()
    {
      Card card = { Card::END, 0 };    // CYA declaration

      if ( m_shoe.size() > 0 )
      {
        card = m_shoe.front();
        m_shoe.pop();
      }

      return card;
    }

  private:
    // Create the cards, in sorted fashion, for each deck required.
    //
    void setupCards()
    {
      for ( size_t d = 0; d < m_numDecks; ++d )
      {
        for ( unsigned int suit = Card::HEART; suit <= Card::SPADE; ++suit )
        {
          // Setup card values and add the weight of the card suit.
          //
          for ( size_t c = 1; c <= 13; ++c )
          {
            Card card = { (Card::Suit)suit, c, (c < 10 ? c : 10) };

            m_cards.push_back( card );
          }
        }
      }
    }

    size_t m_numDecks;   // number of decks
    Cards  m_cards;      // all cards, in sorted fashion
    Shoe   m_shoe;       // shoe for storing sorted cards
};


int main( int argc, char **argv )
{
  Deck deck(2);    // create two complete decks of cards

  deck.shuffle();  // shuffle the deck(s) and insert Marker card

  Card card;

  do
  {
    card = deck.dealCard();

    std::cout << card << std::endl;
  }
  while ( !card.isEnd() ); 

  return 0;
}
[/php]

---

### Post by nvteighen on 2008-08-30
Just a note:

I'm also implementing a card game and noticed that you don't need to generate the whole deck and shuffle it, but just have to randomly generate the total amount of "card objects" that will be played (and check there's no repeated one, of course).

---

### Post by dribeas on 2008-08-30
There are some problems here: cards should be a member attribute, your destructor should take care of the memory allocated.

```

struct Deck
{
   int decks;
   int *cards;

   Deck(int Decks)
      : decks(Decks), cards( new int[ Decks*52 ] )
   {
      // fill in the cards, with your own logic
   }
   ~Deck()
   {
      delete [] cards;
   }
};

```

Note that you should never expose your internals, more often than not you will want to use class/struct with public methods and private data.

---

### Post by jimi_hendrix on 2008-08-30
> **nvteighen said:**
> Just a note:

I'm also implementing a card game and noticed that you don't need to generate the whole deck and shuffle it, but just have to randomly generate the total amount of "card objects" that will be played (and check there's no repeated one, of course).

right...but if the user wants to play again with the same amount of decks why not just shuffle the existing?  plus this is more for learning then fun...i wouldnt play this much after i made it

well thanks all for your help

---

### Post by mike_g on 2008-08-30
The way I did this in the past was to have a number represent a card. then suit = card / 13 and rank = card % 13. 
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

typedef unsigned char Uint8;
typedef unsigned short Uint16; 
typedef struct
{
    int num_decks; 
    Uint16 size;
    int stack_pos;
    Uint8 *cards;
}Deck;

Deck* CreateDeck(Uint8 decks)
{
    if(! decks) return NULL;
    Deck *new_deck = (Deck*)malloc(sizeof(Deck));    
    if(! new_deck) return NULL;
    new_deck->cards = (Uint8*)malloc(52*decks);
    if(! new_deck->cards)
    {
        free(new_deck);
        return NULL;
    }
    Uint8 x, y;
    Uint8* ptr = new_deck->cards;
    for(x=0; x<decks; x++)
    for(y=0; y<52; y++, ptr++) 
        *ptr=y;
    new_deck->stack_pos = 0;
    new_deck->num_decks = decks;
    new_deck->size = 52 * decks;
    return new_deck;
}

void FreeDeck(Deck *deck)
{
    if(! deck) return;
    free(deck->cards);
    free(deck);
    deck = NULL;
}

const char* GetSuit(Uint8 card)
{
    static const char *suit[] = {"Clubs", "Diamonds", "Hearts", "Spades"};
    return suit[card/13];    
}

const char* GetRank(Uint8 card)
{
    static const char *rank[] = {"Ace", "Two", "Three", "Four", "Five", 
        "Six", "Seven", "Eight", "Nine", "Ten", "Jack", "Queen", "King"};
    return rank[card%13];  
}

void PrintCard(Uint8 card)
{
    printf("the %s of %s", GetRank(card), GetSuit(card));
}

void ShuffleDeck(Deck *deck)
{
    Uint8 i, temp, pos;
    for(i=0; i<deck->size; i++)
    {
        pos = rand() % deck->size;
        temp = deck->cards[pos];
        deck->cards[pos] = deck->cards[i];
        deck->cards[i] = temp;
    }
}

Uint8 DrawCard(Deck *deck)
{
    Uint8 card = deck->cards[deck->stack_pos]; 
    deck->stack_pos++;
    if(deck->stack_pos >= deck->size)
        deck->stack_pos = 0; 
    return card;   
}

int main()
{
    srand(time(NULL));
    Deck *deck = CreateDeck(1);
    ShuffleDeck(deck);
    printf("Deal 12 cards: \n");
    int i;
    for(i=1; i<13; i++)
    {
        printf("\t%2d: ", i);
        PrintCard(DrawCard(deck));
        putchar('\n');
    } 
    getchar();
    FreeDeck(deck);
    return 0;
}
```

---

### Post by nvteighen on 2008-08-30
> **jimi_hendrix said:**
> right...but if the user wants to play again with the same amount of decks why not just shuffle the existing?

What I mean is that you don't really have to have a deck to have one :p Shuffling is not trivial at all (because of the buffering... remember C++ has not automatic memory management nor a mutable list native data type) and you may possibly need an external library to do that in an efficient way.

Having the abstraction at "card at playing"-level generated by random is like having a "virtual deck" ("having a deck without having one"), so you don't care ever for shuffling... you just have to make sure you don't get the same card duplicated and the "deck illusion" will be perfect!

---

### Post by jimi_hendrix on 2008-08-30
now i get what you mean...thanks

---

### Post by mike_g on 2008-08-30
Shuffling is easy. If you're using a set of card objects just shuffle an array of pointers to the cards, but I still thing the card objects are unnecessary even if it all sounds very OO. TBH the entire deck system should be possible w/o any dynamic memory allocation at all.

---

### Post by dwhitney67 on 2008-08-30
nvteighten, jimi_hendrix -

Here are some questions for you to consider in your Poker game development effort:

1.  How many times will you shuffle the cards until you believe that the cards are sufficiently shuffled?

2.  Will you shuffle the cards after each round of play, or will you continue to use the deck until a "marker" card is found?  (In casinos, multiple decks are typically used and hence not shuffled after each round; with a single deck, it probably would be prudent to shuffle after each round).

3.  If you elect not to use a "marker" card, and shuffle only after each card has been played at least once, what will you do if you are in the middle of a round and there are no more cards to draw from the deck?  Shuffle again during mid-play?  What happens if 5 aces show up when playing with a single-deck?

---

### Post by dwhitney67 on 2008-08-30
> **nvteighen said:**
> Just a note:

I'm also implementing a card game and noticed that you don't need to generate the whole deck and shuffle it, but just have to randomly generate the total amount of "card objects" that will be played (and check there's no repeated one, of course).
This would work, but does not seem very efficient.

---

### Post by nvteighen on 2008-08-30
> **dwhitney67 said:**
> nvteighten, jimi_hendrix -

Here are some questions for you to consider in your Poker game development effort:

I'm not implementing a Poker game... I said a "card game" ([Truco]("http://www.pagat.com/put/truco.html")) :p

> **dwhitney67 said:**
> This would work, but does not seem very efficient.

Well, I'm trying to write this in Scheme... using a closure and taking advantage of tail-recursion and some abstraction techniques this can turn out to be very powerful (if I happen to write this properly, of course).

In C or C++, the free()/delete overhead may be important as you'll have to deallocate memory more times than if you used a whole deck that you just deallocate once at the end of the game.

---

### Post by dwhitney67 on 2008-08-30
Why does the deck (of cards) need to be allocated?  You create it once, then that's it.  The cards can be created on the stack.

I understand you are using a different language, but in C++ it would probably best (for jimi_hendrix) to use an STL vector than an array.

Anyhow, as I mentioned in an earlier post, this discussion does not befit the title of the thread... it is far from being a basic concept.  :)

---

### Post by nvteighen on 2008-08-30
> **dwhitney67 said:**
> Why does the deck (of cards) need to be allocated?  You create it once, then that's it.  The cards can be created on the stack.

I understand you are using a different language, but in C++ it would probably best (for jimi_hendrix) to use an STL vector than an array.

Anyhow, as I mentioned in an earlier post, this discussion does not befit the title of the thread... it is far from being a basic concept.  :)

Well, I don't know C++, so I'm not quite aware of what STL can do or not. Anyway, I agree: an array is the worst choice for this.

Before going on Scheme, I prototyped this in Python... OOP seems the best way to do this, at least at deck-level (whatever you consider to be a deck: your "real" or my "virtual" one). But I do agree with mike_g that maybe the card object is overkill; maybe his modulo implementation is a bit abstract (I can smell where it comes from... [the Solitaire cipher]("http://en.wikipedia.org/wiki/Solitaire_(cipher)")), but maybe a data structure can be enough. (If you're interested, my cards in Scheme are functions... :p but that are the "weird things" you do in functional programming)

And yes, this is not a basic C++ question... it isn't even a C++ question, but a design one... So, the title is even more inappropriate than you suspected!! :)

---

### Post by mike_g on 2008-08-30
> Well, I don't know C++, so I'm not quite aware of what STL can do or not. Anyway, I agree: an array is the worst choice for this.
Why exactly would an array be the worst choice for this? An STL vector might have some advantages over an array such as bounds checking and resizability; however, I don't see the deck as something that should need to be resized. If it does then I would call that a bigger design flaw as it would be creating unnecessary complexity.

---

### Post by nvteighen on 2008-08-30
> **mike_g said:**
> Why exactly would an array be the worst choice for this? An STL vector might have some advantages over an array such as bounds checking and resizability; however, I don't see the deck as something that should need to be resized. If it does then I would call that a bigger design flaw as it would be creating unnecessary complexity.

Maybe I'm confusing something...? 

Let's see: you have a deck with a fixed amount of cards. But you have to shuffle it, so, if you use an array, how many buffers do you need in order to shuffle the deck? Wouldn't using a vector allow you to shuffle without buffering, just swapping places in its members?

Or do you create a second deck and copy things randomly from the source array to the target and then destroy the original?

Or am I overcomplicating things??

---

### Post by mike_g on 2008-08-30
> Let's see: you have a deck with a fixed amount of cards. But you have to shuffle it, so, if you use an array, how many buffers do you need in order to shuffle the deck? Wouldn't using a vector allow you to shuffle without buffering, just swapping places in its members?
You should only need 2 temp variables to perform a shuffle. A very simple and effective way to do this is called a Knuth shuffle: 
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
    srand(time(NULL));

    int i, temp, swap_pos, array[52];
    for(i=0; i<52; i++)array[i] = i; //Init
    //Shuffle
    for(i=51; i>1; i--)
    {
        swap_pos = rand() % i;     //Pick random location to swap with
        temp = array[swap_pos];     //Swap elements
        array[swap_pos] = array[i];
        array[i] = temp;
    }

    for(i=0; i<52; i++) printf("%02d\n", array[i]);
    return 0;
}
```
If you're using card objects, then you could create an array of references pointing to each card, then shuffle that array. So, yeah I think you could simplify things a little here :)

Edit: made some corrections to the code.

---

### Post by CptPicard on 2008-08-30
Hate to contradict a fellow Schemer here but I would have to agree that an in-place shuffle of a fixed-size array is IMO a very simple, obvious, efficient solution. :)

Of course in Scheme you get to do interesting kinds of modelling sure... and in pure-functional style in particular, where you do not have a mutable array in use, you may have to consider nvteighen's solution. However, we need to remember that it is quite inefficient (even in the high-level abstract sense) to essentially remember the cards you've already pulled from the deck so that you can avoid duplicates... towards the end, you have essentially generated the entire deck into your duplicates-elimination set, which you have to check each time for each attempted card. This gets really expensive towards the end, and even terminates just based on an argument from probability.

It ends up producing a very bad algorithm if I've understood correctly.

---

### Post by hod139 on 2008-08-30
> **mike_g said:**
> You should only need 2 temp variables to perform a shuffle. A very simple and effective way to do this is called a Knuth shuffle: <Snip>
There is a bug in your implementation of Knuth's shuffle.  See [http://en.wikipedia.org/wiki/Fisher-Yates_shuffle](http://en.wikipedia.org/wiki/Fisher-Yates_shuffle) for a correct implementation of the algorithm.

The big offending line of your code is
```

swap_pos = rand() % 52;     //Pick random location to swap with

```From the wikipedia article
> 
Similarly, always selecting *k* from the entire range of valid array indexes on *every* iteration (*i.e.* using k = rng.nextInt(array.length) in the Java example above) also produces a result which is biased, albeit less obviously so. This can be seen from the fact that doing so yields *N**N* distinct possible sequences of swaps, whereas there are only [*N*!]("http://en.wikipedia.org/wiki/Factorial") possible permutations of an *N*-element array. Since *N**N* can never be evenly divisible by *N*! (as the latter is divisible by *N*&#8722;1, which shares no [prime factors]("http://en.wikipedia.org/wiki/Prime_factor") with *N*), some permutations must be produced by more of the *N**N* sequences of swaps than others.


---

### Post by mike_g on 2008-08-30
Oh, I invented that algo myself then someone told me it was a called a knuth shuffle. Either way it seems to work. But yeah, I guess those changes would give a better result.

---

### Post by hod139 on 2008-08-30
> **mike_g said:**
> Either way it seems to work. But yeah, I guess those changes would give a better result.

If by works you means runs quickly and gives biased permutations of the deck, then yeah it works#-o

The correctly implemented Fisher-Yates algorithm does not give "better" results, it gives "correct" results.

---

### Post by mike_g on 2008-08-30
Well the code I posted was just meant to be a very rough example. Tbh an unbiased distribution was not something I cared about all that much and if that was the case then theres also issues with rand() that should be dealt with too.

---

### Post by hod139 on 2008-08-30
> **mike_g said:**
> Well the code I posted was just meant to be a very rough example. Tbh an unbiased distribution was not something I cared about all that much and if that was the case then theres also issues with rand() that should be dealt with too.
The problem I had is that you incorrectly called your algorithm Knuth's shuffle, where these details do matter.  If you had said, here is my shuffling algorithm then I wouldn't have answered so harshly; but you named it a well tested and mathematically proved shuffling algorithm.  And yes, there are issues with C++'s rand function that have to be dealt with, details for those interested can be found [here]("http://members.cox.net/srice1/random/crandom.html").

The ubuntuforums seem to rank high on google, so imagine if someone saw your implementation of Knuth's algorithm and though it correct.  This is why I felt the need to answer.

---

### Post by CptPicard on 2008-08-30
Actually mike_g's version is the classic way to get the shuffle wrong. Had this as a homework assignment in randomized algorithms class and it went maybe 50-50, and most of those who got it right knew already :)

Of course, nothing fundamentally wrong in making mistakes, it's a learning opportunity...

---

### Post by mike_g on 2008-08-30
Ok, I made a couple of alterations to the code I originally posted. So it should produce a better distribution now.

---

### Post by emobrad on 2008-08-30
All the things inside of the parentheses in a function allow the variables to be passed along them.

So if a function has a variable inside the parentheses you can pass it to the other functions

```
 void function(int x);
int main (int x)
```

Allows function to use x which you would declare in main, so you don't have to globally declare it (outside of a function). Which really just makes it easier to debug your program.

---

### Post by CptPicard on 2008-08-30
Something confused there in your understanding emobrad... whether a function declares something as a parameter has nothing to do with your ability to pass it along to other functions as their parameter.

In 

```

void function(int x)

```

it just says that function takes one int parameter, named x here. Which means that you call function with something like function(5), and then inside the body of function you have x = 5.

---

### Post by nvteighen on 2008-08-30
> **CptPicard said:**
> Hate to contradict a fellow Schemer here but I would have to agree that an in-place shuffle of a fixed-size array is IMO a very simple, obvious, efficient solution. :)

Oh, but I'm learning and I still have to do some more mistakes to be a real Schemer :) I'm still a padawan. (But, as you'll see, CptPicard, I got rid of iteration counters... I learned something!).

As the best way to explain what I want to do is to show the code, here it is:
```

(define (random-pick lst)
  (list-ref lst (random (length lst))))

(define make-card cons)
(define card-suit car)
(define card-value cdr)

(define (make-play suits values num)
  (lambda (x)
    (list-ref
     (let loop ((queue '()))
       (if (= num (length queue))
           queue
           (let ((buffer (make-card (random-pick suits)
                                    (random-pick values))))
             (if (member buffer queue)
                 (loop queue)
                 (loop (cons buffer queue))))))
       x)))

```

At least in the game I want to write, the cards are returned to the "deck" after each play, so I only have to generate "num" cards (num / number-of-players = cards for each player). In the case of Truco, each player receives 3 cards (so, "num" will be 6 for 2-players Truco); I just have to ensure there's no duplicate among the cards *dealt*.

Player 1 will then receive one half of the generated cards; player 2 the rest. After the round is ended, the cards are forgotten and a new set is generated.

But, anyway, I see the other method is far easier than I thought, so I won't mind to switch to that if it ends up being better. Notice that I could use the very same code to generate the whole deck (using num = 52... well, for Truco, num = 48 ), the difference would be to keep it instead of forgetting it (and after the first round, shuffling instead of regenerating).

P.S.: I post this here because discussion happens to be here, but maybe a new thread should be splited from this one?

---

### Post by emobrad on 2008-08-30
> **CptPicard said:**
> Something confused there in your understanding emobrad... whether a function declares something as a parameter has nothing to do with your ability to pass it along to other functions as their parameter.

In 

```

void function(int x)

```

it just says that function takes one int parameter, named x here. Which means that you call function with something like function(5), and then inside the body of function you have x = 5.


ahh, sorry about that. Haven't written a program in C++ in a while that I had to pass anything. Mainly just working out of a book to learn it. Thanks for correcting that

---

