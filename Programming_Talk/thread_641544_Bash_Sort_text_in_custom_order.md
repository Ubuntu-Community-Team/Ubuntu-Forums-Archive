---
title: "Bash: Sort text in custom order"
date: 2007-12-15
forum: Programming Talk
---

### Post by durand on 2007-12-15
Hi,
I'm writing a bash script for a project and I need to sort text in a certain order. This is my example text:

D-10
S-10
D-2
H-2
C-4
C-6

I can remove the (-) if needed.
This set is generated randomly so there may be J, Q, K, A as well in the second bit.

I tried using sort to sort it in alphabetical order but even this didnt seem to work right as the 10 came before the 2. It would be a lot more useful if I could sort this is a certain order. This is for a card game so the SDHC stand for Spades, Diamonds, Hearts and Clubs.

So, for the first letter, I need it to be sorted in this order - D,C,H,S and for the second part, it has to be in this order - numbers 3 to 10, (J)ack, (Q)ueen, (K)ing, (A)ce and finally 2 at the end.

So, the final order would look like this:


D-10
D-2
C-4
C-6
H-2

or if possible:

C-4
C-6
D-10
S-10
D-2
H-2

so it sorts the second part first.

---

### Post by geirha on 2007-12-15
Does it have to be a bash script? It's possible, but will require a lot of lines. Doing it in python would be much easier and shorter.

---

### Post by durand on 2007-12-15
Ok, if you would show me how to do it in python, that would also help. I can just run it off the bash script anyway. Thanks

---

### Post by Trumpen on 2007-12-15
Well, a little escamotage consists in using sed to translate your personal range to an alphabetical one so that you can exploit sort.

Something like this:

[CODE]sed -e 'y/SDHC/abcd/' -e 'y/3456789JQKA2/BEFLMNORTUVW/' -e 's/10/P/' cards | 
sort -t- -k1 | 
sort -t- -k2 | 
sed -e 'y/abcd/SDHC/' -e 'y/BEFLMNORTUVW/3456789JQKA2/' -e 's/P/10/'[CODE]

where cards is the file containing a card (e.g. S-2) per line . We translate S,D,H,C respectively to abcd, 3,4,5,6,7,8,9,J,Q,K,A,2 to BEFLMNORTUVW (notice that these letters must be both in alphabetical order and not used by other cards). Finally 10 is substituted with P. 

After sorting we just need to retranslate back to the original range.

A bit scheming but it seems to work :)

Update: sorry, I have seen too late you had already solved it :/

---

### Post by durand on 2007-12-15
Thanks! I was thinking of the sed method but I didn't know that you can combine them together! I was just thinking of doing:

sed 's/2/P/g' and repeating that for different letters. This would have just taken too much space..

EDIT: Your sed method works great! Thanks.

geirha, I'm still interested in the python method as I'm thinking of porting this to python later anyway.

---

### Post by geirha on 2007-12-15
Using sed like that was clever :)

Here's the python approach I would use.

If you want the script to mimic the sort command, you'll read them from stdin with ```
import sys
cards= sys.stdin.readlines()
```

Since you want to sort in a non-alphabetical and non-numerical way, it's best to make a dictionary that dictates the order
```

suits= { 'D': 1, 'C': 2, 'H': 3, 'S': 4 }
values= { '3':1, '4':2, '5':3, '6':4, '7':5, '8':6, '9':7, '10':8, 'J':9, 'Q':10, 'K':11, 'A':12, '2':13 }

```
Create a function to compare two cards that return -1, 0 or 1 if card1 is "before" card2, card1 equals card2 or card1 is "after" card2 respectively.

```

def card_compare(card1, card2):
    suit1, value1= card1.strip().split('-')
    suit2, value2= card2.strip().split('-')
    return cmp(values[value1],values[value2]) or cmp(suits[suit1],suits[suit2])

```
Then use the python list's sorting function ```
cards.sort(card_compare)
```
And print the result```
sys.stdout.writelines(cards)
```

EDIT: So I guess I was wrong. bash used fewer lines :)

---

### Post by durand on 2007-12-15
Hehe, this reminds me of the bubble sort algorithm we were learning in decision maths :D But anyway, thanks a lot geirha! That will be really useful. I just need to learn python :P

---

