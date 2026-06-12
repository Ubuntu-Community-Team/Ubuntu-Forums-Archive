---
title: "absolute value urgent"
date: 2008-06-06
forum: Programming Talk
---

### Post by aonks on 2008-06-06
can someone please tell me the inline assembly code to find the absolute value of a double variable ??

it is very urgent ...


i'm using GCC in Cygwin

reply soon

---

### Post by NathanB on 2008-06-06
> **aonks said:**
> can someone please tell me the inline assembly code to find the absolute value of a double variable ??

it is very urgent ...


i'm using GCC in Cygwin

reply soon

Just bit-wise AND the value with $0FFFFFFF to clear the sign bit.

Nathan.

---

### Post by aonks on 2008-06-06
#include <stdio.h>
#include <stdlib.h>

#define PRECISION 3

double absD (double n)
{

// i need the code here, plz write me the code
// i m due an assignment, and its very urgent

return n;

}

int main (int argc, char **argv)
{
double n = -12.45576;
int number = -1234;

if (argc > 1)
n = atof(argv[1]);

printf("abs(%.*f) = %.*f\n", PRECISION, n, PRECISION, absD(n));


printf("\n\nnumber: %d  absolute value: %d\n", number, abs(number));

return 0;
}

---

### Post by aonks on 2008-06-06
plz .. nathan .. i need ur help urgently

do reply .. anything would do

---

### Post by KingTermite on 2008-06-06
It's been years since I've toyed with assembly, but to change sign of a two's compliment number, IIRC, you reverse bits and add 1 (not "just" change sign bit).

so you could (algorithmically)

If ($80000000 AND Number) /* sign bit shows its negative)
Number XOR $FFFFFFFF
Number = Number +1

---

### Post by KingTermite on 2008-06-06
> **NathanB said:**
> Just bit-wise AND the value with $0FFFFFFF to clear the sign bit.

Nathan.

Numbers should be in two's compliment, so its more than "just" changing the sign bit, IIRC.

Also, you show that in Hex, so you would be clearing the top 4 bits. For your example, wouldn't you want to AND it with $7FFFFFFF?

---

### Post by rye_ on 2008-06-06
Asking for advice is one thing, or introducing a discussion, but people aren't going to do your homework for you.  It just not on.

Ryan

---

### Post by aonks on 2008-06-06
i 've no clue about the syntax either .. i know, i'm bein a pain in da *** .. but plz could u tell me the exact code .. my prof. is gonna flunk me other wise

---

### Post by mike_g on 2008-06-06
> Just bit-wise AND the value with $0FFFFFFF to clear the sign bit.

Nathan.
Wouldent a double consist of 8 bytes? Also, to mask out the sign bit on a 32 bit integer would be 0x7FFFFFFF. Never really did any bitwise stuff with floating point tho.

> 
// i need the code here, plz write me the code
// i m due an assignment, and its very urgent

What have you tried?

---

### Post by aonks on 2008-06-06
m really sorry for this .. i know, i should have studied, this is not like me .. but can u help me, just this one time

---

### Post by Phenax on 2008-06-06
[FONT=monospace]Haven't tried it:
```

cltd
xorl %edx,%eax
subl %edx,%eax

```
[/FONT]

---

### Post by KingTermite on 2008-06-06
> **mike_g said:**
> Never really did any bitwise stuff with floating point tho.
Just realized when you said this that he was asking for a double value. That's a WHOLE DIFFERENT ball game. I was thinking of a 2's compliment integer.

I think you can just change the sign bit (which is the 1st bit).

Double =
1-11-52 (bit fields for sign-exponent-mantissa) IIRC.

Just check the first bit (double is 64-bit) and change to a 0. Actually...you can just force to a 0 and not worry about checking.

Number = Number AND $7FFFFFFFFFFFFFFF

---

### Post by aonks on 2008-06-06
phenax .. can u tell me the exact syntax ?

---

### Post by aonks on 2008-06-06
i can understand your logic .. but have no clue about the syntax

---

### Post by KingTermite on 2008-06-06
I think you've had enough help....if you know your assembly at all, you should be able to this command or two easily. If you can't even do that command or two, then quite frankly, you should flunk.

---

### Post by aonks on 2008-06-06
plz ... i beg of u
dnt ditch me ... i 'll
have 2 repeat my whole semester

---

### Post by Phenax on 2008-06-06
Actually:
[http://www.scriptlance.com/projects/1212744106.shtml](http://www.scriptlance.com/projects/1212744106.shtml)

He's signed up to create it for a customer at ScriptLance for $30. Do your own work.

---

### Post by KingTermite on 2008-06-06
> **Phenax said:**
> Actually:
[http://www.scriptlance.com/projects/1212744106.shtml](http://www.scriptlance.com/projects/1212744106.shtml)

He's signed up to create it for a customer at ScriptLance for $30. Do your own work.

LOL....nice find!

---

### Post by mike_g on 2008-06-06
Rofl!

---

### Post by aonks on 2008-06-06
mr. smarty pants ...

---

### Post by NathanB on 2008-06-06
> **KingTermite said:**
> Numbers should be in two's compliment, so its more than "just" changing the sign bit, IIRC.

Also, you show that in Hex, so you would be clearing the top 4 bits. For your example, wouldn't you want to AND it with $7FFFFFFF?

Yeah, that's it.  Nice catch!

Nathan.

---

### Post by KingTermite on 2008-06-06
> **NathanB said:**
> Yeah, that's it.  Nice catch!

Nathan.

That's why we're here as a community. :) :popcorn:

---

### Post by aonks on 2008-06-06
fine .. u guyz busted me, i'm guilty as charged. but plz, help out this poor lad .. for some charity work .. god will bless u all

---

### Post by slavik on 2008-06-06
May god be with you on your journey!

---

### Post by aonks on 2008-06-06
i might sound stupid, but am not dat dumb .. dis looks lyk the code for an infinte loop

---

### Post by Lster on 2008-06-06
It is. **Do not run the command above!**

---

### Post by LaRoza on 2008-06-06
> **aonks said:**
> i might sound stupid, but am not dat dumb .. dis looks lyk the code for an infinte loop

This forum is for Ubuntu support. It has other sections that are not directly related to Ubuntu, but none of them are to be used this way.

I see all your posts are in this thread. This forum isn't here to do your work, but to help you.

Please do not abuse this forum. If you have no interest in the topics of this forum, please don't use it. (I am going to help with this ;))

---

