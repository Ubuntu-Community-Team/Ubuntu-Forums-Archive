---
title: "a brain teaser..."
date: 2007-08-28
forum: Programming Talk
---

### Post by abadfish on 2007-08-28
I saw this in a job posting and thought it was rather interesting:

> 
To Apply:

1.Answer the following: 66 28 31 35 29 3d 3f 3b 66 28 6e 29 20 3d 20 66 28 6e 2d 31 29 2b 66 28 6e 2d 32 29 2b 66 28 6e 2d 33 29 3b 66 28 6e 3c 3d 32 29 3d 6e

Paste your result into the subject line and attach your code in the body. 


if you want to see my solution, scroll down














































































I've translated the ascii stream to be 16-bit hex values.  Assuming that is correct, using an ASCII table we get:

f(15) = ? ;
f(n) = f(n-1)+f(n-2)+f(n-3);
f(n <=2) = n

The simplest implementation in C is:

```

int func(int num)
{
    if (num<=2) return num;
    return ( func(num-1) + func(num-2) + func(num-3) );
}

```

Of course you don't want to do it this way!  Why?  The two biggest reasons are overhead and inefficiency.  Let's address these.

Using the following test program:
```

int main(int argc, char *argv[]
{
    int i;

    i = func(atoi(argv[i]));
    printf("i = %s  func(i) = %d\n", argv[i], i);
    return 0;
}

```

If you run this with a value of 36 (the max value before you overrun a 32-bit integer:

```

% TIMEFORMAT="" time junk 36
i = 36  func(i) = 1748130326
16.24user 0.00system 0:16.27elapsed 99%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+155minor)pagefaults 0swaps

```
It takes 16+ seconds to run this and you use 99% of the CPU.  There's a lot of overhead in all those recursive calls.

Its also highly inefficient.  Think about what happens when you compute the value of func(36).  By the recursive algorithm, you have to compute func(35), func(34), and func(33).  In order to compute func(35), you'll have to compute func(34), func(33), and func(32).  So you've now done func(34) twice, func(33) three times, etc, etc.  You'll computing func() for the lower numbers quite a few times.  Why do it multiple times when you only really need to do it once.

To improve upon this, lets do an iterative solution rather than a recursive one.  To determine the correct solution, lets see what this algorithm is doing:

```

i       func(i)
0       0
1       1
2       2
3       (f(2) + f(1) + f(0)) = 3
4       (f(3) + f(2) + f(1)) = 6
5       (f(4) + f(3) + f(2)) = 11
6       (f(5) + f(4) + f(3)) = 20
7       (f(6) + f(5) + f(4)) = 37
8       (f(7) + f(6) + f(5)) = 68
9       (f(8) + f(7) + f(6)) = 125
10      (f(9) + f(8) + f(7)) = 230

```

As you can see, all we really need to keep track of are the previous three computations of func().  This gives us the following code:

```

int func(int num)
{
    int prev1, prev2, prev3, retval;

    if (num<=2) return num;
    prev1 = 2;
    prev2 = 1;
    prev3 = 0;
    while  (num >= 3)
    {
        retval = prev1 + prev2 + prev3;
        prev3 = prev2;
        prev2 = prev1;
        prev1 = retval;
        num--;
    }
    return retval;
}

```

Running this code using the same benchmark test we get:

```

 % TIMEFORMAT="" time junk 36
i = 36  func(i) = 1748130326
0.00user 0.00system 0:00.00elapsed 0%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+155minor)pagefaults 0swaps

```

The same computation using the iterative method is almost instantaneous and uses almost no CPU time.

---

### Post by triptoe on 2007-08-28
when i wrote a fibannoci algorithm i did the same thing.. i just kept track of the previous value rather than using recursion.. so i didn't have to use "hints" and it was much faster. but


Newb here... when you say you translated it to hex values.. wasn't it already in hex values?

I tried changing the hex values to decimal.. then i changed them to see if they were letters and some secret code... but it wasn't

---

### Post by nanotube on 2007-08-29
** spoiler **

translating from hex to text in python:

```
>>> a = '66 28 31 35 29 3d 3f 3b 66 28 6e 29 20 3d 20 66 28 6e 2d 31 29 2b 66 28 6e 2d 32 29 2b 66 28 6e 2d 33 29 3b 66 28 6e 3c 3d 32 29 3d 6e'
>>> import binascii
>>> binascii.unhexlify(a.replace(' ',''))
'f(15)=?;f(n) = f(n-1)+f(n-2)+f(n-3);f(n<=2)=n'

```

now, for some simple calculations:

```

>>> l = range(3)
>>> l
[0, 1, 2]
>>> range(3,16)
[3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
>>> for i in range(3,16):
...   tmp = sum(l[-3:])
...   l.append(tmp)
... 
>>> l
[0, 1, 2, 3, 6, 11, 20, 37, 68, 125, 230, 423, 778, 1431, 2632, 4841]
>>> l[15]
4841

```

computation speed ~ 0 sec.

et voila :)

isn't python great? :)

---

### Post by abadfish on 2007-08-29
> **triptoe said:**
> 
Newb here... when you say you translated it to hex values.. wasn't it already in hex values?

Perhaps that was a poor choice of words.  My intent was that its a hex stream where the stream is in 16-bit chunks where each chunk is an ascii character represented by its hex value.

> **nanotube said:**
> 
isn't python great? :)
Isn't C great?  this wasn't intended to be this language is better than this language thread (like so many of the other threads in this forum).    I prefer not to let it turn into one.

---

### Post by nanotube on 2007-08-29
> **abadfish said:**
> 
Isn't C great?  this wasn't intended to be this language is better than this language thread (like so many of the other threads in this forum).    I prefer not to let it turn into one.

ehrm... that was just an off-the-cuff comment to celebrate my completion of the task- certainly not intended to spark off a language war. :)

---

### Post by pmasiar on 2007-08-29
> **abadfish said:**
> Isn't C great? 

I think that nanotube was excited how simple and straightforward the decoding was in Python: just 1 quite simple line (after setting data and importing needed module). Solving it was also quite simple - he did not even needed to define the function itself, or even compile any source code - he solved it directly in the Python shell :-)

And it could be dome 1 line shorter, obviously: 
```

for i in range(3,16):
...   l.append(sum(l[-3:]))

```

I have nothing against C per se, but IMHO in these "explorative programming" tasks Python shines.

---

### Post by abadfish on 2007-08-29
I'm not disputing the usefulness/slickness/<insert whatever superlative here> of Python or any other language.  They all have their strengths and weaknesses.  They all also have   limits in their usage.  For example, (as some of you have already pointed out) Python can do this operation in a few lines of code in a script on a workstation.  Now put that code in an embedded system.  In embedded applications, C really shines.  Again, this doesn't make C better than Python.  Programming languages are tools and not all tools are applicable to all jobs.

Oh and FWIW, pmasiar did nanotubes code with one line less.  Does that necessarily make it better/faster/more efficient????  Not really.  Regardless of whether its a compiled language or an interpreted language.  It all comes down to how many instructions the code creates in assembly for the given processor.  While doing one less line made the stack smaller, it likely created the same amount of assembly instructions.

Now can we please stop bastardizing this thread into a *Python vs the world*  thread?  There are so many other threads in that forum that do already do that!

---

### Post by pmasiar on 2007-08-29
Thanks for interesting post, abadfish. I wonder what kind of company posted the job? looks like interesting company to work for, hackers were not totally over-run by marketoids yet. :-)

> **abadfish said:**
> Regardless of whether its a compiled language or an interpreted language.  It all comes down to how many instructions the code creates in assembly for the given processor.  While doing one less line made the stack smaller, it likely created the same amount of assembly instructions.

My version skipped defining tmp variable, so my gut feeling it should have shorter bytecode (unless compiler is really smart and optimizing), but it is not substantial improvement.

BTW for really compact embedded applications, [Forth](http://en.wikipedia.org/wiki/Forth_%28programming_language%29) is even **more** compact than C... I am not sure, is this hijacking by your definition? Sorry if is...

> Now can we please stop bastardizing this thread into a *Python vs the world*  thread?  There are so many other threads in that forum that do already do that![/QUOTE]

Sorry for setting your thread off... 
...but threads **always** meander into something else... and people will go tangent, commenting on BTW comments, and will not trim posts, and top-post (or bottom-post): what else is new? :-) Wanna join my crusade for trimming posts? :-)

---

### Post by LaRoza on 2007-08-29
> **pmasiar said:**
> 
Sorry for setting your thread off... 
...but threads **always** meander into something else... and people will go tangent, commenting on BTW comments, and will not trim posts, and top-post (or bottom-post): what else is new? :-) Wanna join my crusade for trimming posts? :-)

No, threads are always on-topic :D. By the way, how do I join your crusade? Is it a group, society, or just individual actions?

---

### Post by pmasiar on 2007-08-29
> how do I join your crusade?

Just add it to your sig, and then sometimes mention it to gross offenders.

It's individual actions so far, I am not sure about society... But it's a good idea! Knights of Trim, perhaps? :-) We should start a wiki where people can link and join...

uff, again off-topic! but at least not "Python vs world", I do hope OP is less offended ;-)

---

### Post by Wybiral on 2007-08-29
> **abadfish said:**
> Now can we please stop bastardizing this thread into a *Python vs the world*  thread?  There are so many other threads in that forum that do already do that!

It seemed as though _you_ were the one who "bastardized" the thread by taking a simple comment as something that it wasn't.

Just because someone says "Ah... Pepsi's great" doesn't mean they're saying "Pepsi is superior to any other cola and should be drank exclusively". It was just a random appreciation of their language.

Don't be so defensive.

---

### Post by LaRoza on 2007-08-29
> **pmasiar said:**
> 
uff, again off-topic! but at least not "Python vs world", I do hope OP is less offended ;-)

Sometimes there are lapses in communication, as we know ;-).

Adding to my sig, now.

---

### Post by abadfish on 2007-08-29
Since we're all on topic, here's me at Sears Pt last month:

[img]http://cbrworld.net/photos/riding_and_racing/images/275498/500x333.aspx[/img]

---

### Post by Vox754 on 2007-08-29
> **Wybiral said:**
> It seemed as though _you_ were the one who "bastardized" the thread by taking a simple comment as something that it wasn't.

Just because someone says "Ah... Pepsi's great" doesn't mean they're saying "Pepsi is superior to any other cola and should be drank exclusively". **It was just a random appreciation of their language.**

Exactly.

> **abadfish said:**
> Since we're all on topic, here's me at Sears Pt last month:
[picture of guy on a motorcycle]


Ha ha ha. Seriously guys, I love reading this forum.

> **abadfish said:**
> 

```

int main(int argc, char *argv[]
{
    int i;

    i = func(atoi(argv[i]));
    printf("i = %s  func(i) = %d\n", argv[i], i);
    return 0;
}

```

Watch out for a bug in this code. Can you spot it?

---

