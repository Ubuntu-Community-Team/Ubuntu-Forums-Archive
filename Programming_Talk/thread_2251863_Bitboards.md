---
title: "Bitboards"
date: 2014-11-07
forum: Programming Talk
---

### Post by spacerocket on 2014-11-07
Hello,

I decided to post here regarding to the bit operations. So, my concern is about how to use the bitwise operators effectively (eg. in board games like connect four, sudoku etc.) and thought if it would be possible to organize some lessons about that.

Ok, so converting hexadecimal representations

0x0(decimal 0)=0000
0x1=0001
0x2=0010 ....

Logical AND (&)

And takes two equal-length binary representations and performs the logical and operation on each pair of the corresponding bits, by multiplying them
The bit in the resulting binary representation is 1 (1 × 1 = 1); otherwise, the result is 0 (1 × 0 = 0). For example:

1101110 & 0110111 = 0100110

The operation may be used to determine whether a particular bit is  

set(1) or clear(0)

       0011  decimal(3)
 &    0010  decimal(2)

   = 0010 decimal(2)

because the result is non-zero, we know the second bit in the original pattern was set...?


Shifting is simple, for example: board>>8 shifts the board 8 bits to right (shifted bits become 0?)

Now, what use is & operator together with >> or << ?

---

### Post by trent.josephsen on 2014-11-07
Think about how you'd write code that's able to check whether any bit is set:
```
#define BIT_0 1
#define BIT_1 2
#define BIT_2 4
#define BIT_3 8
...

bool is_bit_set(unsigned n, unsigned b) {
    switch (b) {
    case 0: return n & BIT_0 ? true : false;
    case 1: return n & BIT_1 ? true : false;
    case 2: return n & BIT_2 ? true : false;
    case 3: return n & BIT_3 ? true : false;
    ...
    }
}
```

Compare that to a version using << to shift 1 into the appropriate mask position, then >> to normalize the result to 0 or 1:

```
bool is_bit_set(unsigned n, unsigned b) {
    return (n & (1 << b)) >> b;
}
```

Bit-shifts come in handy when doing masking operations, but don't feel like you have to use them all the time.

---

### Post by spacerocket on 2014-11-07
Ok,

Let`s say I have a board structure

bitset<9> board (string("00000000"));

which is 

000
000
000


If a player occupies a position in the game board, then the associated bit would be 1 otherwise 0.

Then I use << to shift 1 to the mask (unknown, not known) position (determined at run time) where a player lands either 'X' or 'O'.

After first move the board would look like this:

000
000
001


Then I 'hit' (shift) all those numbers with 1, so that 0&1 becomes 0 (bool occupied=false) and only the associated bit becomes 1&1=1 (bool occupied=true)

---

### Post by spacerocket on 2014-11-07
Well this seems a little difficult, maybe I overreached. I searched some information:

However, ANDing a value with 0 is guaranteed to return a 0, so it is possible to turn a bit off by ANDing it with 0: Y AND 0 = 0. To leave the other bits alone, ANDing them with a 1 can be done.

Now it is possible to turn bits off but not on, but if I get a board with one bit set, this means the board includes a win and the function returns true.


Something like this for a tic-tac-toe:

y = board & (board >> 4)

010 & 101 = 000
001 & 110 = 000
110 & 001 = 000

---

### Post by ofnuts on 2014-11-07
You can turn a bit on by ORing it: 101 | 010 = 111. You can toggle a bit by XORing it 101 ^ 010 = 111, and 111 ^ 010 = 101.

---

### Post by spjackson on 2014-11-07
I can see a point in learning about bit twiddling for the sake of it and also for the types of application where it is relevant. I remain to be convinced that games such as Connect 4, Sudoku and tic-tac-toe are genuine use cases for this style - unless you are targetting severely limited hardware.

---

### Post by spacerocket on 2014-11-08
This tic tac toe game seems a little complicated, so I studied about bits (and will cover later more) But now I made a plan how to proceed:

Basically, the board is a 3x3 =structure which is one byte +1. Bits are numbered starting with 0 from the rightmost and ending up with 8 in this case (leftmost)

Step 1: Check if a square is occupied by a player (if in use, the corresponding bit would be 1)   // This is important so that a player can`t land X or 0 to a square already occupied, in case 1 bool legal=false.

Step 2: Indicate whether a square is in use, and removing a square from use.

I would start with

char occupied= 0;

Now, how we can check if a particular square is empty before we try to use it? We need to isolate the one bit that corresponding to that square. We use bitwise operators to ensure every bit of the result is zero except, possibly, for the bit we want to extract. What we really want to do, is to shift a bit over a certain number of places. We can use a bitwise leftshift to accomplish this.

bool occupied(int square)

{

return occupied & 1 <<square;

}


// Continue to set the in-use bit for squares....


Of course, I would need to initialize int square somehow.


Step 2:

void check_occupation_state (int square_num)
{

    in_use = in_use ^ 0<<square_num;

}

// some code....

if (in_use) { bool legal=false; }

---

