---
title: "C cod for a histogram"
date: 2007-08-30
forum: Programming Talk
---

### Post by cape_town on 2007-08-30
Hello,

As I am learning C by myself- I am trying to solve a C exercise but I am having difficulities. Can anybody help me to write the c code in order to display a histogram in this form:

*
**
***
****
*****
******
*******
********
*********

The exercise requires to utilize only the commands: for and printf("*").

Thanks in advance!

---

### Post by CptPicard on 2007-08-30
I almost would like to tell you to re-read whatever C material you have on hand, this is really simple ;)

But I'll give you a hint. First you use the for loop to count through the number of rows. In your histogram, the row number also seems to be the number of stars on that row. Then, inside that first loop, you put a second loop that counts through the number of stars (which is also the number of the row you're on from the first loop)... and finally, inside the second loop, you printf("*") a star for each time you go through the second loop.

Finally, you need to printf("\n") a newline after each time the second loop finishes.

---

### Post by LaRoza on 2007-08-30
Answer here, don't look, unless you really want to see!
































[php]
int i;
for (i=0;i != 9;i++)
{
    int j;
    for (j=0;j != i;j++)
    {
        printf("*");
    }
    printf("\n");
}
[/php]

When I first learned to program, I found the for loop confusing, because so much was being done at once, hopefully, if you see the answer, read the explanation above, you will understand it better.

---

### Post by CptPicard on 2007-08-30
I almost would recommend you do not look at a completed solution until you're absolutely sure you're not going to figure it out from the general description of the logic I gave... getting things handed to you don't help learning :)

---

### Post by Lster on 2007-08-30
I found loops hard at first, but after an initial struggle they became much easier. The second loop makes it appear much harder than it is, IMO.

Good luck!

---

### Post by pmasiar on 2007-08-30
> **cape_town said:**
> As I am learning C by myself-

Although C is rather simple language, Python is more beginner-friendly, in not only in my opinion, but most programmers who know both languages (I do). Anecdotal evidence suggests that **learning Python and then** other C-like language (C/C++/Java) is **faster** than skipping over Python. It is because in Python, you can try most (except strong type check) concepts of those other languages, understand concepts, before you more into more details.

Here is your solution in Python, and you can try it in shell, without compiling source:
```

for i in range(1,8):
    print '*' * i

```

If you are intrigued (and I hope you are :-) ), check wiki in my sig.

---

### Post by LaRoza on 2007-08-30
> **pmasiar said:**
> 
Here is your solution in Python, and you can try it in shell, without compiling source:
```

for i in range(1,8):
    print '*' * i

```


To the OP, the for loop is different in C and Python, so comparing the syntax won't work.

If this is your first language, my or pmasiar's wiki would be helpful. If you want to stick with C, you might want to check out my wiki anyway, because it has useful C resources (free).

---

### Post by CptPicard on 2007-08-30
Python's idea of a loop iterating over a range is one of the reasons why I am not as much into Python as some other people are. Why exactly should it be done in such a contrived fashion, first generating a list from a function and then iterating over it?

In an imperative language, I much more prefer the "initialization - end condition - step" format of C-like languages. With Python you need to start wondering about how to turn your process into a generator (if you don't want to waste memory by creating a complete list). Python's looping is further crippled by not having a "do..while", IIRC. Functional programming languages are a different story...

---

### Post by nanotube on 2007-08-30
> **CptPicard said:**
> Python's idea of a loop iterating over a range is one of the reasons why I am not as much into Python as some other people are. Why exactly should it be done in such a contrived fashion, first generating a list from a function and then iterating over it?

In an imperative language, I much more prefer the "initialization - end condition - step" format of C-like languages. With Python you need to start wondering about how to turn your process into a generator (if you don't want to waste memory by creating a complete list). Python's looping is further crippled by not having a "do..while", IIRC. Functional programming languages are a different story...

to avoid creating a "complete list", just use "xrange" instead of "range". it was designed specifically for looping over. :)

so... do you like python better now? :)

also, python does have a while loop... which, in all honesty, is no different than a do-while, other than that you get the first loop iteration for 'free'. same thing can always be accomplished with the regular "while", either by modifying the condition appropriately, or throwing in a "firsttime" flag. so i don't see what the big deal is about that one.

---

### Post by pmasiar on 2007-08-30
Edit: nanotube beat me :-)
> **CptPicard said:**
> Python's idea of a loop iterating over a range is one of the reasons why I am not as much into Python as some other people are. Why exactly should it be done in such a contrived fashion, first generating a list from a function and then iterating over it?

Because it is simple? When you have any sequence, you can loop through it, and it covers 90% of use cases. Or you can use iterator instead of sequence. xrange returns itarator. In Py3K, range() will be iterator.

> In an imperative language, I much more prefer the "initialization - end condition - step" format of C-like languages. 

like xrange(from, to, step), which is iterator? You are being picky. :-)

> With Python you need to start wondering about how to turn your process into a generator (if you don't want to waste memory by creating a complete list). 

In most cases, you just don't care, if you have just couple hundreds items in a list.

> Python's looping is further crippled by not having a "do..while", IIRC. 

And you know it wrong, too. Python has "while" statement.

```

while <test>:
    block
else:
    block

```  

So, two wrong out of two - not bad? Maybe you should learn Python before complaining what does not work right? :-)

---

### Post by CptPicard on 2007-08-30
> **pmasiar said:**
> 
In most cases, you just don't care, if you have just couple hundreds items in a list.

You still need to model your algorithm in terms of list operations. It's not Lisp, and when it's not, I much prefer being able to just manipulate variables, in particular in cases like this. The range() style stuff is just an added conceptual complication. xrange() conceptually complicates a trivial thing even further.

Getting for each in list-style operations is a great plus certainly, but seeing everything terms of them makes Python seem like a weird hybrid...

> 
And you know it wrong, too. Python has "while" statement.


No, I want a do..while. I don't like replicating my logic before the initial while so I can get the "first one for free".

---

### Post by LaRoza on 2007-08-30
> **CptPicard said:**
> 
No, I want a do..while. I don't like replicating my logic before the initial while so I can get the "first one for free".

Most languages have looping constructs, all of them have different ways, try Fortran for some fun. C doesn't use Pythons method either, but that does prevent me from using C.

---

### Post by pmasiar on 2007-08-30
> **CptPicard said:**
> The range() style stuff is just an added conceptual complication. 

You are ridiculous, but OP did not expressed any interest in Python, so I will stop right here. We will fight it another time! :-)

---

### Post by CptPicard on 2007-08-30
> **LaRoza said:**
> C doesn't use Pythons method either, but that does prevent me from using C.

Care to elaborate? The for (;;) loop yields itself easily into iterating over iterable structures, but the foreach list style needs a specific generator function to achieve what for (;;) achieves without anything extra... or I didn't get what you're after here...

---

### Post by CptPicard on 2007-08-30
> **pmasiar said:**
> You are ridiculous, but OP did not expressed any interest in Python, so I will stop right here. We will fight it another time! :-)

Now, now.. I would have expected a bit more of an argument from you (and generally respect your views), and I am not seeking a fight, merely expressing my view that Python has a bit too much of an ideological approach to this, forcing you to actually generate lists through some mechanism even when it is not neccessary...

---

### Post by LaRoza on 2007-08-30
> **CptPicard said:**
> Care to elaborate? The for (;;) loop yields itself easily into iterating over iterable structures, but the foreach list style needs a specific generator function to achieve what for (;;) achieves without anything extra... or I didn't get what you're after here...

I use Fortran, C, and Python (among other languages, but these are the one for this discussion). Each one has loops differently. I like C's for loop, because I am used to it, and it is one of the most useful loops there is; however, it is "extra", a feature of the language. Its function can be replicated easily.

```

        INTEGER i
        i = 0
10     IF (i .le. 10) THEN
            write (*,*) i
            i = i + 1 
            GOTO 10
        ENDIF

```

This is the the same as:
[php]
for (i = 0; i<10;i++)
{
    printf("%d\n",i);
}
[/php]

Look at the "do" loop from Fortran, for a more confusing syntax :D.

The point is, exactly how a language loops depends on the use of the language. Python's method is very useful for what Python is used for.

---

### Post by CptPicard on 2007-08-30
> **LaRoza said:**
> ...and it is one of the most useful loops there is

Yes, my point exactly. It is a very versatile structure. Restricting the for keyword for list processing -- and thus forcing the use of additional constructs to achieve something basic such as integer counting -- seems like a form of unnecessary bondage and discipline...

> however, it is "extra", a feature of the language. Its function can be replicated easily.

I find C-style for to be a fairly fundamental construct, as it contains *the* ideas that are central to a loop (init, condition, how to go forward) within itself, on one line. Of course, someone might claim that it's strange to put, say, increment before the code that the increment is done after, but can't have everything...

You CAN replicate it certainly, but something like

```

index = 0;
while index < 10:
  blahblah...
  index = index + 1   # index++ is so much more concise...

```

is more verbose. And that you "can" replicate its structure by something as awful as using something with a GOTO is hardly an argument... you can do all sorts of things, but it doesn't mean you should :) If the C-style "for" is an extra that keeps you from using GOTO, then, let's be glad we have it and consider its virtues regarding other languages too.. ;)

> Python's method is very useful for what Python is used for.

Does this mean Python is restricted in its usage to problems that are easily modelled as processing of list members?

---

### Post by Wybiral on 2007-08-30
Pythons iterators, even if you find them "conceptually complicated" are very powerful and useful. Perhaps not in this situation... But then I again I don't see how:

```

for i in xrange(100):

```

Is more "conceptually complicated" then:

```

for(i = 0; i < 100; i++)

```

---

### Post by LaRoza on 2007-08-30
> **CptPicard said:**
> 
Does this mean Python is restricted in its usage to problems that are easily modelled as processing of list members?

Does this mean C can't do that?

Looping constucts vary across language, but all can achieve the same thing. Some languages don't have C style for loops, some don't Python, some have both types, PHP.

A simple syntax difference shouldn't cause such alarm over a language. If such things are important, stick with the language of your choice. pmasiar's solution in Python was perfect, and just as easy to understand as mine, maybe easier, if you knew both languages.

---

### Post by xtacocorex on 2007-08-30
> **LaRoza said:**
> Look at the "do" loop from Fortran, for a more confusing syntax :D.

I don't think the FORTRAN DO loop has confusing syntax, seems pretty simple to me: (F90/95/03)
```

DO <loop counter> = <start> , <end>, <step>
     ... statements
     ... statemends
END DO 

```
I'm hijacking this thread now.  LaRoza, did you know that you don't need to declare variables in FORTRAN 77?  All variables in FORTRAN 77 are assumed to be REAL, with the exception of I, J, K, L, M, N and anything defined as another type. ([http://www.fortran.com/fortran/F77_std/rjcnf0001-sh-4.html#sh-4](http://www.fortran.com/fortran/F77_std/rjcnf0001-sh-4.html#sh-4) - Section 4.1.2)

---

### Post by Wybiral on 2007-08-31
> **xtacocorex said:**
> I don't think the FORTRAN DO loop has confusing syntax, seems pretty simple to me: (F90/95/03) ...

That reminds me of BASIC:

```

FOR I = 0 TO 99 STEP 1
NEXT

```

---

