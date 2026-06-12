---
title: "booleans in C"
date: 2009-09-07
forum: Programming Talk
---

### Post by MadCow108 on 2009-09-07
hi,
if have a huge array of char's to check some status. It should only save 0 or one.
currently it looks something like that:
```

#define INDEX(a,b,c) (a*size2*size3 + b*size3 + c)
...
char * ar = malloc(size1*size2*size3)
...
ar[INDEX(i,j,k)] = 1
...
if (ar[INDEX(i,j,k)])
...

```

a char are 8 bit so I could theoretically save the same information in an eighth of the memory.
I'm currently thinking of a bitfield but unfortunately you can't address members of a bitfield so I need to calculate the member from the index requiring a bit of runtime overhead.
Is there a way to do this in C with less or even no overhead?

---

### Post by OutOfReach on 2009-09-07
How about looking into stdbool.h? That'll allow you to use the **bool** type directly.

---

### Post by MadCow108 on 2009-09-07
stdbool.h only seems to typedef an integer to a bool and define true and false
so that would not really help me reduce memory usage

---

### Post by Simian Man on 2009-09-07
You can do this in C, but you have to do it manually with bit manipulation (untested code):
```

typedef bitfield unsinged char;

int is_set(bitfield field, int pos) {
    return (field & (1 << pos));
}

int set(bitfield* field, int pos) {
    *field |= (1 << pos);
}

int unset(bitfield* field, int pos) {
    *field &= ~(1 << pos);
}
```

You could change the char to an long in the typedef above to get (probably) 64 boolean values.  For anything else, you'd have to use arrays which would add a bit of logic, but it still isn't too bad.

---

### Post by MadCow108 on 2009-09-07
perfect thanks

this is my code for arrays in case someone is interested:
```

#define INDEX(a,b) (a*SIZE+b)

int is_set(bitfield *field, int pos) {
	div_t res = div(pos,8);
	return (field[res.quot] & (1 << res.rem));
}

int set(bitfield* field, int pos) {
	div_t res = div(pos,8);
	field[res.quot] |= (1 << res.rem);
}

int unset(bitfield* field, int pos) {
	div_t res = div(pos,8);
	field[res.quot] &= ~(1 << res.rem);
}
..
set(bf,INDEX(2,3));

```

---

### Post by dribeas on 2009-09-07
I don't believe in early optimization, nor in macros, but if you really want to go for it...

If you intend on using 8 bits (char) then you can use a macro/function to calculate the offset in a faster way by manipulating bits. 

```

#define DIV_8( x ) ( (x) >> 3 )
#define MOD_8( x ) ( (x) & 0x07 )

```

Then you can avoid shifting to get the bit mask by precomputing the eight bit masks you will need:

```

char masks[] = { 0x1, 0x2, 0x4, 0x8, 0x10, 0x20, 0x40, 0x80 };

```

So that the mask you want to apply is `mask[ MOD_8( POS(x, y) ) ]` in your code, for just one indirection.

```

// SET is easiest, can precompute the position and keep it, as it does not return it can be a
// block of code, it is also the safest as arguments are only used once
#define SET( data, x, y ) { register int pos=POS((x),(y)); (data)[ DIV_8(pos) ] |= mask[ MOD_8(pos) ]; } 

#define GET( data, x, y) ((data)[ DIV_8( POS((x),(y)) ) ] & mask[ MOD_8( POS((x),(y)) ) ]

```

Of course, the compiler can do anything it wants to with the register keyword, but in most cases (even if you did not actually requested it) it will be able to keep it in a register (the scope is minimal, just three instructions all of which do use the variable).

Now, I recommend that you do not go this way and instead use regular functions. At any rate, and seeing the use of macros in your OP, note that you should use parenthesis around all the arguments to avoid problems with the code after the macro expansion. Also note that if an argument is used more than once inside the macro (as in GET) you risk users having unexpected results when they call the macro: GET( i++, j++ ) will increment both i and j variables twice (as compared to the SET( i++, j++ ) that will only increment each variable once.

A last remark, how big is a HUGE array of bools? Note that you are sacrificing performance for memory, and current systems do have lots of memory (and CPU for that matter), but anyway, given current hardware, in most cases you would be better helping programmers (that is regular functions, regular data structures) than helping the computer. Just think of how much your time costs as compared to CPU/memory costs... how much work will you do to avoid buying a 4 Gb ram module for less than 75&#8364;, how much work do you want to spend to save for a 10% performance that can be payed by 50&#8364; worth of CPU upgrade (from one frequency to the next would probably be less than that, just rough numbers).

---

### Post by TheBuzzSaw on 2009-09-07
It is much better to simply use bit operators than to create a fancy new datatype.

---

### Post by socool274 on 2009-09-07
I would suggest creating a function that returns a string. it returns in the format of an 8 bit binary code. "00110101", for example. Essentially, it converts a char number into a binary string format, which you can then check, and theoretically store 8 true/false values within one byte of memory.

---

### Post by jpkotta on 2009-09-07
> **socool274 said:**
> I would suggest creating a function that returns a string. it returns in the format of an 8 bit binary code. "00110101", for example. Essentially, it converts a char number into a binary string format, which you can then check, and theoretically store 8 true/false values within one byte of memory.

Yuck.  How on earth is this better than what was described in first post?

---

### Post by Reiger on 2009-09-07
> **TheBuzzSaw said:**
> It is much better to simply use bit operators than to create a fancy new datatype.

Quite, in mock-C:
```

/**
 * Extracts a bit as boolean value from a data array
 * index = 0 based index of the bit to look up (e.g. the first bit has index 0)
 * data = the data buffer that holds your bits, accessible as array
 * returns true if the bit is a 1 (on), false if it is a 0 (off). 
 */
boolean extractBit(byte[] data, int index) {
  int charIndex = index >> 3;
  int bitIndex = index & 0x7; // the mod 8 operation
  return ( data[charIndex] & (1 << bitIndex) ) > 0;
} 

```

---

### Post by Can+~ on 2009-09-07
> **socool274 said:**
> I would suggest creating a function that returns a string. it returns in the format of an 8 bit binary code. "00110101", for example. Essentially, it converts a **char number into a binary string format**, which you can then check, and theoretically **store 8 true/false values within one byte of memory**.

You might want to check your facts.

---

### Post by MindSz on 2009-09-08
Well you could try using an int and then use a mask to get the value of the bool.

For example, in an int you have (depending on the OS) 4 bytes = 32 bits.

Now each bit could represent a boolean variable. So the number 5 means that bits 0 and 2 are true while the rest (1,3, 4, 5, etc) are false.

To determine this you can use a mask, so to SET a bool

```
bit0 = boolInt | 0x01
bit2 = boolInt | 0x04
```

And to get the value of a particular position
```

bit0 = boolInt & 0x01
bit2 = boolInt & 0x04
```

Now this is off the top of my head, but it might work. I've done similar stuff in my code before.

---

### Post by MadCow108 on 2009-09-08
thanks for all your suggestions

the runtime impact of this is actually very very small as get/setting the bit is not the only operation done in the loop of my application.

---

