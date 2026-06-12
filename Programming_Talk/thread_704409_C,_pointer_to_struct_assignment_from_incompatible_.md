---
title: "C, pointer to struct: assignment from incompatible pointer type / strcpy segfaults"
date: 2008-02-22
forum: Programming Talk
---

### Post by tehet on 2008-02-22
Hi,
I'm trying to generate a list of cards (for learning structs and pointers) by looking at example [program 5.2](http://home.netcom.com/~tjensen/ptr/ch5x.htm). First I make a struct card{} and than a deck of 52 cards. Here deck is an array of a new data type card right?
Then I want a pointer of the type card to point to the first card in the deck (lines 23, 24) and finally some loops to generate the cards. Here's the code:
```
/* Cards */

#include <stdio.h>
#include <string.h>

/* char spade = 'S';	"\u2660";    unicode not working
char club = 'C';	"\u2663";
char heart = 'H';	"\u2665";
char diamond = 'D';	"\u2666"; */

char colours[] = {'S', 'C', 'H', 'D'};
char values[] = {2, 3, 4, 5, 6, 7, 8, 9, 0, 'J', 'Q', 'K', 'A'};

struct card{
	char colour[1];
	char value[1];
};

struct card deck[52];

int main()
{
	struct card *card_ptr;
	card_ptr = &deck; /* ------- line 24 -------- */
	int i, n, card_num;
	for (i = 0; i < 13; i++)
	{
		for (n = 0; n < 4; n++)
		{
			strcpy(deck[card_num].colour, colours[n]); /* Segmentation fault :( */
			strcpy(deck[card_num++].value, values[i]);
		}
	}
	/* show_deck(card_ptr); */
	return 0;
}
```
It gives the following compiler warnings:
```
~/test$ gcc -g cards.c -o cards
cards.c: In function &#8216;main&#8217;:
cards.c:24: warning: assignment from incompatible pointer type
cards.c:30: warning: passing argument 2 of &#8216;strcpy&#8217; makes pointer from integer without a cast
cards.c:31: warning: passing argument 2 of &#8216;strcpy&#8217; makes pointer from integer without a cast
```
In short, I don't understand either the assignment warning nor the strcpy warning or how to get rid of them. Any hints on what I'm doing wrong?

And an unimportant question, is it possible to get unicode working in C? (for the spades, clubs, hearts and diamond symbols)

Thanks.

---

### Post by dwhitney67 on 2008-02-22
It was easier for me to fix your code and compile it using my system than it was to compile it in my head.

Here's the corrected code:

[PHP]/* Cards */

#include <stdio.h>
#include <string.h>

/* char spade = 'S';	"\u2660";    unicode not working
char club = 'C';	"\u2663";
char heart = 'H';	"\u2665";
char diamond = 'D';	"\u2666"; */

char colours[] = {'S', 'C', 'H', 'D'};
char values[]  = {'2', '3', '4', '5', '6', '7', '8', '9', '0', 'J', 'Q', 'K', 'A'};   // I changed this

struct card{
	char colour[1];
	char value[1];
};

struct card deck[52];

int main()
{
  struct card *card_ptr = &deck[0];   // I changed this

  int card_num = 0;   // I changed this

  for (int i = 0; i < 13; i++)   // I changed this
  {
    for (int n = 0; n < 4; n++)   // I changed this
    {
      strncpy( deck[card_num].colour,  &colours[n], 1 );   // I changed this
      strncpy( deck[card_num++].value, &values[i], 1 );   // I changed this
    }
  }

  return 0;
}[/PHP]

Compiled successfully using gcc -std=c99.  The execution was also successful.

P.S.  I believe you were getting seg faults because you hadn't initialized card_num.

---

### Post by hod139 on 2008-02-22
If I may make some general comments.  In your card struct, why are you storing an array of 1 chars, instead of just a char?  Why are you using strcpy to copy one char?

```

[COLOR=#000000][COLOR=#0000bb]struct card[/COLOR][COLOR=#007700]{
    [/COLOR][COLOR=#0000bb]char colour[/COLOR][COLOR=#007700];
    [/COLOR][COLOR=#0000bb]char value[/COLOR][COLOR=#007700];
};

...

[/COLOR][/COLOR][COLOR=#000000][COLOR=#007700]for ([/COLOR][COLOR=#0000bb]int i [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]; [/COLOR][COLOR=#0000bb]i [/COLOR][COLOR=#007700]< [/COLOR][COLOR=#0000bb]13[/COLOR][COLOR=#007700]; [/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]++)  {[/COLOR][COLOR=#007700]
    for ([/COLOR][COLOR=#0000bb]int n [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]; [/COLOR][COLOR=#0000bb]n [/COLOR][COLOR=#007700]< [/COLOR][COLOR=#0000bb]4[/COLOR][COLOR=#007700]; [/COLOR][COLOR=#0000bb]n[/COLOR][COLOR=#007700]++)   [/COLOR][COLOR=#007700]{
      [/COLOR][COLOR=#0000bb]deck[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]card_num[/COLOR][COLOR=#007700]].[/COLOR][COLOR=#0000bb]colour = [/COLOR][COLOR=#0000bb]colours[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]n[/COLOR][COLOR=#007700]][/COLOR][COLOR=#007700];  [/COLOR][COLOR=#0000bb]  
      deck[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]card_num[/COLOR][COLOR=#007700]++].[/COLOR][COLOR=#0000bb]value[/COLOR][COLOR=#007700] = [/COLOR][COLOR=#0000bb]values[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000bb]i[/COLOR][COLOR=#007700]][/COLOR][COLOR=#007700];  
[/COLOR][COLOR=#007700]    }
}
[/COLOR][/COLOR] 
```Another important change that        dwhitney67 made that he didn't mention in his post, is that he added single quotes around the numbers in your values array.  This is important, because you want to store the char 2, not an auto-casted char of the int 2.

**Edit: **About your unicode question: [http://www.cl.cam.ac.uk/~mgk25/unicode.html#c](http://www.cl.cam.ac.uk/~mgk25/unicode.html#c)

---

### Post by dwhitney67 on 2008-02-22
> **hod139 said:**
> If I may make some general comments.  In your card struct, why are you storing an array of 1 chars, instead of just a char?  Why are you using strcpy to copy one char?

Good point!

---

### Post by tehet on 2008-02-22
> **hod139 said:**
> In your card struct, why are you storing an array of 1 chars, instead of just a char?
Because in my broken version char colour[1] produced less compiler warnings than char colour[]. But yah, it's silly :)
> Why are you using strcpy to copy one char?
Because I don't know what I'm doing :lolflag:

Thanks for the help guys! It's slowly starting to sink in, those wierd pointers and all.

---

### Post by sinisterstuf on 2010-06-03
> **tehet said:**
> 
Because I don't know what I'm doing :lolflag:


**Awesome!**

This post offers no real contribution other than to assure that you are not alone ;)

---

### Post by Can+~ on 2010-06-03
> **sinisterstuf said:**
> **Awesome!**

This post offers no real contribution other than to assure that you are not alone ;)

But it assures that there's people who can't read the date of the thread before replying.

---

