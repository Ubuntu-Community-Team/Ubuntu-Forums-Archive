---
title: "counting bits set to '1' in a byte (and magic)"
date: 2008-04-27
forum: Programming Talk
---

### Post by davidmaxwaterman on 2008-04-27
Hi,

I've been looking at the online solutions to the problem of how to count the number of bits set to '1' in a byte (or whatever).

Here's some I've found - some also include explanations: [one]("http://infolab.stanford.edu/~manku/bitcount/bitcount.html"), [two]("http://graphics.stanford.edu/~seander/bithacks.html#CountBitsSetNaive"), [three]("http://groups.google.com/group/comp.graphics.algorithms/msg/43dfb1f4a0f08441"), and [four]("http://aggregate.org/MAGIC/#Population%20Count%20(Ones%20Count)").

Most of them I can understand fairly easily. For example, the naïve one is obvious, and the optimisations to it are straight forward too. The lookup table solution is also easy (though debatably it's not really working anything out).

However, the one involving magic binary numbers I still cannot 'get my head around'. There are a few 'explanations' of how it works in the links above, but nothing really explains it well enough for me to grasp the basic concepts. The post on [comp.graphics.algorithms]("http://groups.google.com/group/comp.graphics.algorithms/msg/43dfb1f4a0f08441") comes closest, but still no cigar :|

Can anyone help me understand what is going on - from the most basic level - or refer me to something that will help?

Thanks!

Max.

---

### Post by keeler1 on 2008-04-28
I did not look at the examples you have but I do have quite a simple solution.

byte defined as b in my example

```
int count = 0;
int x = 128;                     //can be changed to any power of two to check more or less bits
for(x; x > 0; x /= 2)  
{
    if(i & b)                    //bitwise and results in true if at any bit the two numbers both have a 1
    {
       count++;
    }
}
```

x is initialized to 128 because 128 is binary 1000 0000.  x /=2 will simply shift the 1 in the 128 binary number one place to the right and fill the old space with a 0.  The bitwise and will compare all bits of the byte (this is very fast on any modern computer).  Where the two numbers share a one, the resulting number will have a one for that bit.  Because we are using only numbers that are 2^X (2,4,8,16 ... 128) there will only be one 1 in x.  Therefore the only place that the byte and i can share the one is in the xth bit .  Therefore if the bitwise and returns a number that is true, you know that at bit x in the byte there is a one.

If you need more than just a byte change 128 to 2^N where N is the number of bits.

---

### Post by davidmaxwaterman on 2008-04-28
Thanks keeler1 but I'm not looking for a solution to the problem. I already have them.

If you read my post, you'll see that I have the solutions, and I understand most of them. It's just the solution involving magic numbers I don't understand and my post is asking for an explanation of that method.

For example, [this]("http://graphics.stanford.edu/~seander/bithacks.html#CountBitsSetParallel") solution, is one I don't really understand. That page refers to [this]("http://groups.google.com/group/comp.graphics.algorithms/msg/43dfb1f4a0f08441") news group post which has a longer description, but I still don't really understand.

It is a better explanation of that method that I'm after.

Thanks.

Max.

---

### Post by keeler1 on 2008-04-28
I dont quite understand that solution either.  It seems like a lot of unreadable code for barely any optimization.  If you are required to know that code for a class I can not help you as I dont understand it either.  However, if you are just looking to optimize something then my solution seems just as good.

I have both the code of you example and mine in c programs.  They both work.  After testing to make sure they worked I compiled them with gcc -s -O3 for level 3 optimization and to make gcc spout out the assembly.  I have also attached the .s files which show that both methods take pretty much the same number of instructions.  The number of instructions in the assembly for my solution is less than the other one.  I also expanded the inner for loop of my code.  It sets the number once, like the for loop, checks the condition every time, and divides every time.  I added in the last division and check even after I knew it would fail because that is what the for loop would do.

Turns out, with level 3 optimization and the for loop expanded so you can actually see how many instructions are being called, the both have around 44 instructions and use about the same memory.  I have attached all of the .c files and the .s with assembly.  The .s for the expaned for loop is commented out in bitTest3.c.txt because I could only upload 5 files.

---

### Post by davidmaxwaterman on 2008-04-28
> **keeler1 said:**
> I dont quite understand that solution either.

Thanks, but I'm not really that interested in which solution is better - at least at this point - since that depends on way too many things (compiler, CPU architecture, resources, target application, and so on).

What I'm really after is an explanation for why it works.

This is not 'home work' - I'm not at school/university - or anything like that. I just want to know for my own interest. It's a solution that interests me, and if I can understand it, perhaps I can use that same knowledge for the solution of other problem I come across.

The general question, and similar, is one I've been asked many times over the years (I'm 43) in interviews. I usually give a few answers, in this order :

[LIST=1]
[*]first, I give the obvious solution - similar to you gave but using bit shifts instead of division. I specify the reasons I prefer this method - it's way more comprehensible, and therefore is easier to maintain.
[*]I then give obvious optimisations to the above - ie finishing the loop when there are no 1 bits left. The use of 'n &= (n - 1)' in "Sparse ones" on [_this_]("http://infolab.stanford.edu/~manku/bitcount/bitcount.html") page is a new one for me, so I'll have to remember that.
[*]I then give the lookup table solution when CPU is slow and caches are big enough. However, reading up on it (see previous references), I see that the lookup table might not be faster since it increases the dependency on memory caching - if the use of memory exceeds the amount of cache it would require accessing main memory and so it might actually be slower than the other solutions. You at least need to pay attention to the caching and factor it in.
[/LIST]

I guess I would like to be able to understand this 'other method' using magic binary numbers, so that I can give that answer in an interview too, or at least comment on it.

So, I need to understand how it works....

---

### Post by howlingmadhowie on 2008-04-28
for a 1 bit number, the solution is just the number itself.

for a 2 bit number v, the solution is:

c = v - (v>>1 & 01)

see how this works. 
if v==00, v>>1 = 00 and 00 & 01 = 00, so c = 00.
if v==01, v>>1 = 00 and 00 & 01 = 00, so c = 01.
if v==10, v>>1 = 01 and 01 & 01 = 01, so c = 01.
if v==11, v>>1 = 01 and 01 & 01 = 01, so c = 10.

what we are trying to do is reduce the effect of a higher position in the number.

for a 4 bit number v, the solution is:

C = v - ((v >> 1) & 0101)
C = ((C >> 10) & 0011) + (C & 0011)

lets see how this works for a 4 bit number dcba (whereby d, c, b, a = 1,0)

from the first line:
C = dcba - ( 0dcb & 0101) = d(c-d)b(a-b)
and the second line:
C = (( 00d(c-d) & 0011) + (d(c-d)b(a-b) & 0011) = d(c-d) + b(a-b)
= (d+b)(c-d+a-b)
the first number (d+b) is twice as large as the second (c-d+a-b), so we have to add it twice to get one number:
= (2d + 2b +c -d +a - b)
= (a + b + c + d)

so it works for 4 bit numbers.

do you see the pattern yet? basically, your first guess at the total is the number itself. if this number is at the xth place, you now need to subtract it at each of the x-1 other places. what this algorithm does is break down x-1 using bitshifts to give O(ln(x)) speed.

so you start by subtracting it at the x-1th place (assuming the original place number even--that's what the 0x5555 is for), then at the x-2th and x-3th place at the same time (assuming the original place number is one of (2,3,6,7,10,11...) etc, etc.

i hope this clears things up a bit. the inductive proof of correctness is left as an exercise to the student :)

---

### Post by howlingmadhowie on 2008-04-28
> **keeler1 said:**
> I dont quite understand that solution either.  It seems like a lot of unreadable code for barely any optimization.  If you are required to know that code for a class I can not help you as I dont understand it either.  However, if you are just looking to optimize something then my solution seems just as good.

I have both the code of you example and mine in c programs.  They both work.  After testing to make sure they worked I compiled them with gcc -s -O3 for level 3 optimization and to make gcc spout out the assembly.  I have also attached the .s files which show that both methods take pretty much the same number of instructions.  The number of instructions in the assembly for my solution is less than the other one.  I also expanded the inner for loop of my code.  It sets the number once, like the for loop, checks the condition every time, and divides every time.  I added in the last division and check even after I knew it would fail because that is what the for loop would do.

Turns out, with level 3 optimization and the for loop expanded so you can actually see how many instructions are being called, the both have around 44 instructions and use about the same memory.  I have attached all of the .c files and the .s with assembly.  The .s for the expaned for loop is commented out in bitTest3.c.txt because I could only upload 5 files.

they may have about the same number of instructions, but the version with the magic numbers takes far less time :)

actually it's a bit of a hack, because it takes advantage of the AND and SHIFT RIGHT commands in most computer chips. that's the only reason why it's faster.

but faster it is. the other methods scale with O(x), the magic number method scales with O(ln(x)) (where x is the number of bits).

---

### Post by davidmaxwaterman on 2008-04-28
> **howlingmadhowie said:**
> i hope this clears things up a bit. the inductive proof of correctness is left as an exercise to the student :)

Yes, it does. Thanks!

I think your more wordy explanation in combination with [this]("http://groups.google.com/group/comp.graphics.algorithms/msg/43dfb1f4a0f08441") and [this]("http://graphics.stanford.edu/~seander/bithacks.html#CountBitsSetParallel"), will help me get it all clear. I still need to read it a few more times, but I have a sense of it all becoming clear - no 'aha!' moment yet, but it's close :D

To those interested in the performance of these various routines, I notice a table of timings at the bottom of [this]("http://infolab.stanford.edu/~manku/bitcount/bitcount.html") page. Specifically :
```
     No Optimization         Some Optimization       Heavy Optimization

  Precomp_16 52.94 Mcps    Precomp_16 76.22 Mcps    Precomp_16 80.58 Mcps  
   Precomp_8 29.74 Mcps     Precomp_8 49.83 Mcps     Precomp_8 51.65 Mcps
    Parallel 19.30 Mcps      Parallel 36.00 Mcps      Parallel 38.55 Mcps
         MIT 16.93 Mcps           MIT 17.10 Mcps         Nifty 31.82 Mcps
       Nifty 12.78 Mcps         Nifty 16.07 Mcps           MIT 29.71 Mcps
      Sparse  5.70 Mcps        Sparse 15.01 Mcps        Sparse 14.62 Mcps
       Dense  5.30 Mcps        Dense  14.11 Mcps         Dense 14.56 Mcps
    Iterated  3.60 Mcps      Iterated  3.84 Mcps      Iterated  9.24 Mcps

  Mcps = Million counts per second
```

...but, no, I'm not really interested in that (much) ;)

Thanks.

Max.

---

### Post by howlingmadhowie on 2008-04-28
you can thank me by clicking on the little medal bottom right in my post, if you want :)

---

