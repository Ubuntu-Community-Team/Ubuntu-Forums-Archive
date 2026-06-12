---
title: "Programming Challenge: February 9, 2007"
date: 2007-02-09
forum: Programming Talk
---

### Post by kpatz on 2007-02-09
Well, Meng designated me as the next programming challenger, so here goes.

Your challenge, if you choose to accept it, is to write a program that draws and tallies poker hands.

It will accept one parameter, the number of hands to draw.  Each hand is 5 cards.

For each hand drawn, determine the ranking of the hand and keep a running total of each rank.  Print the totals at the end of the draws.

Poker hands are ranked as follows (from highest to lowest):

1.  Royal Flush: Ace, King, Queen, Jack, Ten, all the same suit.
2.  Straight Flush: 5 cards of the same suit in sequence; e.g. Jack, 10, 9, 8, 7.  Ace counts as 1.
3.  Four of a Kind: 4 cards of the same value.
4.  Full House: Three cards of the same value plus two cards of the same value, such as 3 tens and 2 fives.
5.  Flush: Five cards of the same suit, any values.
6.  Straight:  Five cards in sequence (any suits).  Ace can be the highest or lowest, but not both at once.
7.  Three of a Kind: 3 cards of the same value.
8.  Two pairs: A pair is 2 cards of the same value.  So a hand of 5-5-3-7-7 has two pairs.
9.  One pair: Two cards of the same value.

To make the draws realistic, the program should simulate a deck of 52 shuffled cards, and draw from the top of the deck, reshuffling each time.  How you decide to do this is up to you.

Here's a sample output (I added explanations in italics)

Drawing 5 hands

1.  QH, QD, AD, 7S, 9H:  One Pair  *(the QH and QD)*
2.  AC, 10D, AD, AH, 10C: Full House *(the three aces and two tens)*
3.  7D, 9C, JH, JC, 7C: One Pair *(the two jacks)*
4.  6C, 8H, JH, 9C, 7D: Straight *(the 6, 7, 8, 9, and jack)*
5.  9S, 4D, 10C, KC, 3S  *(not a good poker hand)*

Totals:
Hands Drawn: 5
Royal Flush: 0
Straight Flush: 0
Four of a Kind: 0
Full House: 1
Flush: 0
Straight: 1
Three of a Kind: 0
Two Pairs: 0
One Pair: 2

For those who want more of a challenge: 

Extra Credit Assignment 1: Add an option to draw more than 5 cards per hand.  Note that the poker hands are still based on 5 cards (so a full house is still 3+2 for example, with any additional cards not counting).  More than 5 cards per hand increases the odds of getting a good hand.

Extra Credit Assignment 2: Allow draws from more than one deck (which makes it possible for more than one card of the same suit/value to be drawn).

Extra Credit Assignment 3: Add an option to make a specified card value (such as twos) wild.

Extra Credit assignment 4: Modify the program to draw repeatedly and count how many draws it takes to get a specified hand (e.g. how many draws before you get a full house).  See how many 5-card draws it takes to get a royal flush!  Or if you're a math whiz, use fancy mathematical formulas to figure out the odds.

---

### Post by 56phil on 2007-02-12
```

#!/usr/bin/env python


""" programming challenge 9 feb """


import random


S = {3:'hearts', 2:'diamonds', 1:'spades', 0:'clubs'}
F = {12:'ace', 11:'king', 10:'queen', 9:'jack', 8:'ten', 7:'nine', 6:'eight',
    5:'seven', 4:'six', 3:'five', 2:'four', 1:'three', 0:'two'}
G = {0:'Just a Bunch of Cards', 1:'One Pair', 2:'Two Pair', 
    4:'Three of a Kind', 8:'Straight', 16:'Flush', 96:'Straight Flush',
    32:'Full House', 64:'Four of a Kind', 128:'Royal Flush'}
deck = []


def print_hand(n, hand, g):
    print n,
    for card in hand:
        print F[card[0]], 'of', S[card[1]], ', ',
    print G[g]


def grade_hand(hand):
    grade = 0
    if hand[0][0] == hand[1][0] or hand[1][0] == hand[2][0] or \
    hand[2][0] == hand[3][0] or hand[3][0] == hand[4][0]:
        grade = 1
        if hand[0][0] ==  hand[3][0] or hand[4][0] == hand[1][0]:
            grade = 64
        elif (hand[0][0] == hand[2][0] and hand[3][0] == hand [4][0]) or \
        (hand[0][0] == hand[1][0] and hand[2][0] == hand [4][0]):
            grade = 32
        elif (hand[0][0] == hand[2][0]) or (hand[1][0] == hand[3][0]) or \
        (hand[2][0] == hand[4][0]):
            grade = 4
        elif (hand[0][0] == hand[1][0] and (hand[2][0] == hand[3][0] or \
        hand[3][0] == hand[4][0])) or (hand[2][0] == hand[3][0] and \
        hand[3][0] == hand[4][0]):
            grade = 2
    else:
        if hand[0][1] == hand[1][1] and hand[0][1] == hand[2][1] and \
        hand[0][1] == hand[3][1] and hand[0][1] == hand[4][1]:
            grade = 16
        if hand[0][0]+1 == hand[1][0] and hand[1][0]+1 == hand[2][0] and \
        hand[2][0]+1 == hand[3][0] and hand[3][0]+1 == hand[4][0]:
            grade += 8
        if grade == 24:
            if hand[4][0] == 12:
                grade = 128
            else:
                grade = 96
    return grade


def shuffle_deck():
    global deck
    deck = []
    for suit in range(4):
        for face in range(13):
            deck.append((face, suit))
    random.shuffle(deck)
    

def draw_5():
    hand = []
    for i in range(5):
        hand.append(deck.pop())
    return(sorted(hand))


def play(n):
    s = {0:0, 1:0, 2:0, 4:0, 8:0, 16:0, 96:0, 32:0, 64:0, 128:0}
    hands = []
    print 'Drawing %d hands' % (n)
    for i in range(n):
        shuffle_deck()
        hands.append(draw_5())
    for i, hand in enumerate(hands):
        g = grade_hand(hand)
        s[g] += 1
        print_hand(i+1, hand, g)
    print 'Totals:'
    print 'Hands Drawn: %d' % (n)
    for key in sorted(s):
        print '%s: %d' % (G[key], s[key])


if __name__ == '__main__':
    while True:
        hands_in = raw_input("How many hands? ")
        hands = int(hands_in)
        if hands < 1:
            break
        play(hands)

```

---

### Post by meng on 2007-02-15
Good challenge this week. Unfortunately I did not get time to frame a complete solution, but it made me think while I was in the shower!! Sorry you did not get more reponses from other users.

---

