---
title: "Error in Card Shufling Program"
date: 2010-02-17
forum: Programming Talk
---

### Post by newport_j on 2010-02-17
[FONT=Times New Roman][SIZE=3]I ran a program and got the following error and warning. I am unsure as to what is the problem. It seems that my code is correct; the compiler says it is not.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]The output on compiling is as follows gcc -g -pg card_shuffle.c -o card [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]card_shuffle.c: In function &#8216;main&#8217;: [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]card_shuffle.c:102: error: expected expression before &#8216;;&#8217; token [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]card_shuffle.c:32: warning: return type of &#8216;main&#8217; is not &#8216;int&#8217; [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]james@james-laptop:~/Desktop/card$ gedit card_shuffle.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]james@james-laptop:~/Desktop/card$ [/SIZE][/FONT]
 
 
[FONT=Times New Roman][SIZE=3]Now on the area of line 32 is as follows:[/SIZE][/FONT]

 
```

 
The line in question is void main() ...
 
void main() 
{ 
int x=DECK; 
int card; 
char c,s; 
 
puts("Card shuffling demonstration program"); 
 
shuffle(); 
 
 
```
 
[FONT=Times New Roman][SIZE=3]Now for the second error is a warning line 102 is : s = SPADES; and again, I see nothing wrong with it.[/SIZE][/FONT]

 
```

 
* The final print displays the values 
*/ 
 
if(card>=0 && card<=13) 
s = HEARTS; 
else if(card>=14 && card<=26) 
s = DIAMONDS; 
else if(card>=27 && card<=40) 
s = CLUBS; 
else 
s = SPADES; 
 
printf("%c%c\t",c,s); 
 

```
 
 
Any help appreciated.
 
Newport_j

---

### Post by Some Penguin on 2010-02-17
> **newport_j said:**
> [FONT=Times New Roman][SIZE=3]I ran a program and got the following error and warning. I am unsure as to what is the problem. It seems that my code is correct; the compiler says it is not.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]The output on compiling is as follows gcc -g -pg card_shuffle.c -o card [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]card_shuffle.c: In function ‘main’: [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]card_shuffle.c:102: error: expected expression before ‘;’ token [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]card_shuffle.c:32: warning: return type of ‘main’ is not ‘int’ [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]james@james-laptop:~/Desktop/card$ gedit card_shuffle.c [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]james@james-laptop:~/Desktop/card$ [/SIZE][/FONT]
 
 
[FONT=Times New Roman][SIZE=3]Now on the area of line 32 is as follows:[/SIZE][/FONT]

 
```

 
[FONT=Times New Roman][SIZE=3]The line in question is void main() ...[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]void main()

```

Should be int, so that it can return an exit code to the shell.

> ```

[/SIZE][/FONT] [SIZE=3][FONT=Times New Roman]{ [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]int x=DECK; 

```

Where is DECK declared?

> ```

[/FONT][/SIZE] [SIZE=3][FONT=Times New Roman]int card; [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]char c,s; [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]puts("Card shuffling demonstration program"); [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]shuffle(); [/FONT][/SIZE]
 
```

Where is shuffle() declared?  And did you include stdio.h?

> 
[FONT=Times New Roman][SIZE=3]Now for the second error is a warning line 102 is : s = SPADES; and again, I see nothing wrong with it.[/SIZE][/FONT]

 
```

 
[SIZE=3][FONT=Times New Roman]* The final print displays the values [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]*/ [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]if(card>=0 && card<=13) [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]s = HEARTS; [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]else if(card>=14 && card<=26) [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]s = DIAMONDS; [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]else if(card>=27 && card<=40) [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]s = CLUBS; [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]else [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]s = SPADES; 

```
Where are H/D/C/S declared?
> ```

[/FONT][/SIZE]  
[SIZE=3][FONT=Times New Roman]printf("%c%c\t",c,s); [/FONT][/SIZE]
 

``` 
Any help appreciated.
 
Newport_j

---

### Post by wmcbrine on 2010-02-17
Please post the whole program. There's not enough to go on here, apart from the "void main" warning, which isn't the real problem.

---

### Post by avidday on 2010-02-17
> It seems that my code is correct; the compiler says it is not.

That seems to be a rather common theme in your questions here. I think we should defer to the compiler as the final arbiter of syntactical correctness.

There is an error somewhere _before_ this block of code.
```

if(card>=0 && card<=13) 
s = HEARTS; 
else if(card>=14 && card<=26) 
s = DIAMONDS; 
else if(card>=27 && card<=40) 
s = CLUBS; 
else 
s = SPADES; 

```

If you care to show the code rather than selected highlights, someone might be able to help you.

---

### Post by newport_j on 2010-02-17
Okay as for the first error: actually a warning the code I changed to

int main(void)

and it did not complain. I found this program in  c programming manual. I was looking for a card shuffling program and it seemed to fit the bill. I was wondering since this is clearly a DOS program how does writing it in:

void main()

that seems to satisfy Visual c or Inprise c (whichever this is), it does not satisfy gcc. Is gcc that different?


If you know of a good c card shuffling program let me know where it is.

newport_j

---

### Post by nvteighen on 2010-02-17
No; it's not gcc. The C Standard requires main to have one of these signatures:

```

int main(void);

```

or, for passing arguments from shell:

```

int main(int, char **);

```

What happens is that some compilers are more tolerant than others... which is a good idea for some specific stuff, but not for such a crucial one like how you are supposed to declare main.

So, gcc will usually accept some things if no further compiler flags are placed to explicitly make gcc stricter. But, please, try to follow what's right.

Possibly, the error is because of DECK... Is that a macro or what?

---

### Post by newport_j on 2010-02-19
Here is the card shuffling program with a bug in it. I found it on the web, but I must not have copiied it correctly since there is a bug in it which I talk about above.
 
If you knwo of any other card shufling program (ie. one that is better), please give me the website address. I am lookng for a good one.
 
NJ
 
```

 
/*
* Card-Shuffling Program
* James M. Yunker
*
*/
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#define DECK 52 //Cards in a deck
#define HEARTS 0x3 //Heart chraracter
#define DIAMONDS 0x4 //Diamond chrarcter
#define CLUBS 0x05 //Clubs character
#define SPADES //Spa;de character
int draw_card(void);
void shuffle(void);
int rnd(int range);
void seedrnd(void);
 
/*
* The cards array is stuck out here in no-man's
* land to make it available to both shuffle
* and draw-card functions
*/
 
int cards[DECK]; //Deck of cards
int main(void)
{ 
int x=DECK;
int card;
char c,s;
puts("Card shuffling demonstration program");
shuffle(); 
/*
* Sift through the entire deck, decrementing
* variable x from 52 down to 0.
*
* Start drawing the card for each loop.
*
* Theo cjur card%13 math converts to the random number from
* 1 to 52 into chucks of 0 to 12 like the cards 
* in a suit. The +1 makes the numbers 1 through 13.
* 
* The switch case structure weeds out the ace, ten,
* jack, queen, and king, setting the chrarcters 
* in a c vzriable.
*
* The (card%13)+'1' sets the remaining charactrers 
* equal to 2 through 9; adding them to the character 
* '1', which according to thw ASCII file from 
* Volume 1, works out just fine. 
*/
while(x--)
{ 
card = draw_card();
switch((card % 13) + 1)
{
case(1):
c = 'A';
break;
case(10):
c = 'T';
break;
case(11):
c = 'J';
break;
case(12):
c = 'Q';
break;
case(13):
c = 'K';
break; 
default:
c = (card%13) + '1';
}
 
/*
* A complex if-then-else structure handles the suits,
* dividing the values into four chunks. This sets
* the s character equal to the character for 
* hearts, diamonds, etc. 
* 
* The final print displays the values 
*/
if(card>=0 && card<=13)
s = HEARTS;
else if(card>=14 && card<=26)
s = DIAMONDS;
else if(card>=27 && card<=40)
s = CLUBS;
else
s = SPADES;
printf("%c%c\t",c,s);
/*
* This little gem is for formatting only. You divide 
* x (the loop counter) by four -- X MOD 4. When the 
* result is zero, a newline is printed. The ! (not)
* reverses the results of the MOD; otherwise, the 
* newline would print three times in a row.
*/
if(!(x%4))
putchar('\n');
}
}
/* The draw_card routine returns a random number
* from 1 to 52 for eqach rurns the same card in the deck. 
* It never returns the same cardal twice as long 
* as you call the shuffle rotitne - just like 
* in real life!
*/
int draw_card(void)
{
int card;
do 
{
card=rnd(DECK); //draw card
}
while(cards[card]); //is card drawn?
cards[card]=1; //mark it as drawn
return(card+1); //make it 1 to 52
}
 
/*
* The shuffle routine does two things;
* It initializes the randomizer andialies
* initializes the cards[] array.
*/
 
void shuffle(void)
{
int x;
seedrnd();
for(x=0;x<DECK;x++)
cards[x] = 0;
}
/* Generate a random value */
int rnd(int range)
{
int r;
r=rand()%range; //spit up a random number
return(r);
}
/* Seed the randomizer */
void seedrnd(void)
{
srand((unsigned)time(NULL));
}
 
 
 
 
```

---

### Post by Some Penguin on 2010-02-19
> **newport_j said:**
> Here is the card shuffling program with a bug in it. I found it on the web, but I must not have copiied it correctly since there is a bug in it which I talk about above.
 
If you knwo of any other card shufling program (ie. one that is better), please give me the website address. I am lookng for a good one.
 

You'll possibly learn if you make an attempt at understanding instead of relying on copypasta.

> 
```

#define DECK 52 //Cards in a deck
#define HEARTS 0x3 //Heart chraracter
#define DIAMONDS 0x4 //Diamond chrarcter
#define CLUBS 0x05 //Clubs character
#define SPADES //Spa;de character

```


1.  One of the suites is not like the others -- copypasta fail.

2.  Don't put comments in #define macros.  BAD.   Read up on what #define actually does if you want to know why.

---

### Post by talonmies on 2010-02-19
> **newport_j said:**
> 
If you knwo of any other card shufling program (ie. one that is better), please give me the website address. I am lookng for a good one.
 

That [code]("http://www.c-for-dummies.com/sourcecode/vol2/shuffle.c") is so awful it defies comment. If you want to do card shuffling, a heap sort with a weight generated using a high quality random generator is a rather elegant way to do it. Heapify the deck or decks and just pop cards off the top of the heap. Heap sort is an n log n complexity operation which is straightforward and completely analogous to a deck of cards.

---

### Post by wmcbrine on 2010-02-19
Here's how I implemented shuffling in an old program of mine -- cards are just represented by numbers 0-51, the deck by an array of int. Snipping the irrelevant bits:

```

#include <stdlib.h>

/* ... */

int deck[52];

/* ... */

void shuffle(void)
{
        int x, y, tmp;

        stacked = 52;

        for (x = 0; x < stacked; x++)
                deck[x] = x;

        for (x = 0; x < stacked; x++) {
                y = x + (rand() % (stacked - x));
                tmp = deck[x];
                deck[x] = deck[y];
                deck[y] = tmp;
        }
}

/* ... */

int main(int argc, char **argv)
{
        /* ... */

        srand(time(0));
        
        /* ... */

        shuffle();

        /* ... */
}

```

---

### Post by ve4cib on 2010-02-19
> **talonmies said:**
> That [code]("http://www.c-for-dummies.com/sourcecode/vol2/shuffle.c") is so awful it defies comment. If you want to do card shuffling, a heap sort with a weight generated using a high quality random generator is a rather elegant way to do it. Heapify the deck or decks and just pop cards off the top of the heap. Heap sort is an n log n complexity operation which is straightforward and completely analogous to a deck of cards.

For something as simple as shuffling you can do in O(n) though, so the heapified solution, while pretty, isn't really all that useful.

Someone else posted a sample of the O(n) shuffle.  For those less-literate in C here's a pseudo-code version:

```
// we'll use a 52-element int array for the deck
// in a real program you'd probably have an array of
// CARD structs or (Card objects) with a value and a suit
deck = [0,1,2,3,4,...,49,50,51];

for i in [0,deck.length) {
    rnd = random number in range [i,deck.length)
    swap deck[i] and deck[rnd]
}
```

*(note that [x,y) indicates that x is included in the range, but y is not.  So [0,5) = [0,1,2,3,4].)*

In a physical sense we'd be taking a random card from the deck and putting it on the table.  Then we take another random card and put that on top of the first.  Then another random card gets put on the pile, and so on until every card has been put on the pile.

---

### Post by nvteighen on 2010-02-20
I have another solution from my FreeTruco project; it's not suited for a general case, but just for games where you shuffle and deal a fixed number of cards cards to a fixed number of players (IMO, the best piece of code I've ever written). It's written in pure-functional Scheme (PLT-Scheme + the rest of my library... but it's quite understandable).

It doesn't deal things, but creates a "dealer" object that "contains" a set of random cards and knows whom he has to assign which card. Then, the dealer-deal procedure returns the cards belonging to the player passed as argument. The main advantage of this is that it doesn't touch the deck... all dealing is virtual and actually no shuffling is done :p

```

(define (make-dealer deck cards-num list)
  ;; Creates a dealer object and returns it.
  ;;
  ;; ARGS: 
  ;; deck: The deck we will be dealing from.
  ;; cards-num: The amount of cards each player has to get.
  ;; list: The list of players that will receive cards.
  ;;
  ;; RET: A dealer object (a compound procedure...).

  (define (list-get-index lst query pred?)
    ;; List auxiliary searcher. Gets the index of some object in a list
    ;; (actually, a set) using a query and a suitable predicate.
    ;;
    ;; ARGS: 
    ;; lst: The list.
    ;; query: What we're looking for.
    ;; pred?: The predicate procedure that will match the query with the result.
    ;;
    ;; RET: The index of query in list.

    (let loop ((i 0)
               (lookup lst))
      (cond ((null? lookup) 
             #f)
            ((pred? (car lookup) 
                    query) 
             i)
            (else
             (loop (+ i 1)
                   (cdr lookup))))))

  (define (make-deals-stream deck n)
    ;; Creates a lazy dealing generator.
    ;;
    ;; ARGS: deck: The deck object.
    ;; n: The amount of cards we need to take.
    ;;
    ;; RET: A stream of all cards that will be dealt.

    (let ((card (list-ref deck 
                          (random (length deck)))))
      (cond ((= n 0) 
             the-null-card)
            ((null? deck) 
             the-null-card)
            (else
             (stream-cons card
                          (make-deals-stream (remove card deck)
                                             (- n 1)))))))

  ;; make-dealer body. We use a lazy stream to 'pull' cards for dealing.
  (let ((deals-stream (make-deals-stream deck 
                                         (* cards-num 
                                            (length list)))))
    (lambda (player)
      ;; This works because we consider that the deals-stream is ordered in an
      ;; offset fashion: card 1 is for player 1, card 2 for player 2, card n is
      ;; for player n, card n + 1 is for player 1 and so on.

      (let ((switch (list-get-index list player eq?)))
        (let loop ((i 0)
                   (hand '()))
          (if (= (length hand) 
                 cards-num)
              hand
              (loop (+ i 1)
                    (cons (stream-ref deals-stream
                                      (+ (* switch
                                            cards-num)
                                         i))
                          hand))))))))

(define (dealer-deal dealer player)
  ;; Deals all cards for some player from a dealer object.
  ;;
  ;; ARGS: 
  ;; dealer: The dealer.  
  ;; player: The player. This has to be someone included in the player list 
  ;; that was passed to the dealer when it was created.
  ;;
  ;; RET: A list of cards.

  (dealer player))

```

---

### Post by wmcbrine on 2010-02-20
Well if we're going to depart from C... here's the Python version:

```
import random
deck = range(52)
random.shuffle(deck)
```

:D

---

### Post by ve4cib on 2010-02-21
> **wmcbrine said:**
> ```
import random
deck = range(52)
random.shuffle(deck)
```

That's all fine and dandy provided the purpose of the exercise is not to implement the shuffling algorithm oneself.  But assuming the use of existing libraries is allowed you can find an array shuffler routine for almost any language out there.

---

