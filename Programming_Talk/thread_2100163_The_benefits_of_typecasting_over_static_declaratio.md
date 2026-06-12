---
title: "The benefits of typecasting over static declaration"
date: 2012-12-31
forum: Programming Talk
---

### Post by eazar001 on 2012-12-31
It has frequently occurred to me that, in terms of memory efficiency, typecasting has benefits over declaration of static spaces.

For example, in this snippet of a script:

```

system(strcat(strcat(strcat((char[sizeof(LINK)+6]){},LINK),(char[3]){'0',i+48,'\0'}),".mp3"));
```

It makes perfect sense to me that garbage collection would be immediate, as opposed to:

```

system(strcat(strcat(strcat(newlink,LINK),num),".mp3"));
```

In the second snippet of code, I assume that I have created two extra strings (C-style char arrays) that have allocated memory space for the concatenation operations.

Yes, in the above snippet, it is also assumed that garbage collection occurs at the end of the script. I am also aware that upon compilation, optimizations are made to correct for redundancies in the abstract level code. I know this may be a moot point to make, but I was just wondering how such optimizations at this level make a difference on a larger scale? Or is it just a waste of time to make such reductions in the real world?

Any coding gurus have any input on this topic? I am curious to see what others have to say about this. Thanks in advance.

---

### Post by trent.josephsen on 2012-12-31
Casting (typecasting is something that happens to actors) is a compile-time operation and has no effect on the efficiency of the resulting code.

```
(char[sizeof(LINK)+6]){}
```

What do you think this does?

**Edit** -- Wait, my mistake, I think I'm misunderstanding you. What do you think the difference is between

```
strcat((char[4]) {0}, "foo");
/* and */
char l[4] = {0};
strcat(l, "foo");
```

---

### Post by eazar001 on 2012-12-31
> **trent.josephsen said:**
> Casting (typecasting is something that happens to actors) is a compile-time operation and has no effect on the efficiency of the resulting code.

```
(char[sizeof(LINK)+6]){}
```

What do you think this does?

Minor correction, typecasting is *also* what happens to actors. Typecasting is also another way of saying "casting."

Anyway, I see your point. So are you trying to tell me that garbage collection doesn't occur immediately with that line of code?

When you ask me "What do you think this does?" Well, here is what I think it does: It creates a temporary char array and concatenates it with another string. Garbage collection then removes the waste from memory. Or am I wrong here? This is my real question.

---

### Post by eazar001 on 2012-12-31
> **trent.josephsen said:**
> Casting (typecasting is something that happens to actors) is a compile-time operation and has no effect on the efficiency of the resulting code.

```
(char[sizeof(LINK)+6]){}
```

What do you think this does?

**Edit** -- Wait, my mistake, I think I'm misunderstanding you. What do you think the difference is between

```
strcat((char[4]) {0}, "foo");
/* and */
char l[4] = {0};
strcat(l, "foo");
```

Okay, so let me try to understand your point, by answering your question (feel free to correct afterwards).

I **think** that the first example concatenates two temporary strings together, and then those two temporary strings are garbage-collected immediately in the next line.

In your second example I **think** that a temporary string is concatenated with a previously declared string named "l". However, here I believe that "l" is not garbage collected until termination of the program.

---

### Post by trent.josephsen on 2012-12-31
I'll let your terminology slide, this time.

Garbage collection doesn't occur in C, not unless you write it yourself. (I'm assuming we're talking C here, not C++, although for this question I don't think it would matter.)

When you do something like (char[N]) {0}, the compiler(*) generates code to reserve space on the stack for N characters. This memory does not incur additional overhead and it vanishes without a trace when the calling function returns. This is exactly identical to the behavior of an ordinary char[N] declared with automatic storage duration. In fact, my test showed that gcc was not quite smart enough to give the cast version the same code as the sensible one, so it would actually underperform in practice (though probably imperceptibly).

(*) Tested with gcc; I'm not sure what the Standard has to say about this rather unusual construct.

(*Automatic storage duration* is an important point here -- if l in my example is not automatic (if it had been declared with **static**, or outside of any function) then the memory for it would not be released until the end of the program. That's not something you could do by accident, and it could not result in a memory leak or faster stack growth because there is only one copy of each object with static storage duration in a program. This paragraph can be safely ignored.)

Your use of the word "allocate" makes me wonder if you're thinking of reserving memory with malloc() and free()ing it afterwards, which is another question entirely, but neither solution need involve casts.

---

### Post by eazar001 on 2012-12-31
Aha I see, so no additional overhead incurred from the original sensible code.

My question was derived from this simple script to automate wget:

```
#define LINK "wget http://www.toonamiarsenal.com/features/blackholemegamix/ToonamiBHM-\0"       //link base

int main()
{
  int i;
  
  for(i = 1; i <= 21; i++)
  {
      if(i < 10)
        system(strcat(strcat(strcat((char[sizeof(LINK)+6]){},LINK),(char[3]){'0',i+48,'\0'}),".mp3"));
      else
        system(strcat(strcat(strcat((char[sizeof(LINK)+6]){},LINK),(char[3]){i/10+48,i%10+48,'\0'}),".mp3"));	
  }
```

I was under the impression that this non-sensible variant would provide benefits (imperceptible benefits), but your distinction between automatic and static variables brings me back down to earth. Thanks for your prompt response.

---

### Post by eazar001 on 2012-12-31
On a rather amusing side-note, part of the description of typecasting(acting) in Wikipedia says: "Alternatively, a director may choose to cast an actor "against type," i.e., in a role that would be unusual for that actor, to create a dramatic or comedic effect." It's kind of funny how it all relates in the end.

---

### Post by Bachstelze on 2013-01-01
> **trent.josephsen said:**
> I'll let your terminology slide, this time.

I won't. :D

> **eazar001 said:**
> Typecasting is also another way of saying "casting."

No, it is not. The verb "typecast" occurrs nowhere in the C standard, so it is nonsensical in C.

---

### Post by eazar001 on 2013-01-01
> **Bachstelze said:**
> I won't. :D



No, it is not. The verb "typecast" occurrs nowhere in the C standard, so it is nonsensical in C.

You don't have to let it slide, but it doesn't mean you're right. [http://www.cprogramming.com/tutorial/lesson11.html](http://www.cprogramming.com/tutorial/lesson11.html)

Those guys apparently use it.... I don't know what you mean by "The C Standard", but I suppose you're probably referring to some kind of programmer's bible?

---

### Post by Bachstelze on 2013-01-01
> **eazar001 said:**
> I don't know what you mean by "The C Standard"

okay.jpg

I'm referring more specifically to [http://en.wikipedia.org/wiki/C99](http://en.wikipedia.org/wiki/C99)

---

### Post by eazar001 on 2013-01-01
And solely just for the sake of extinguishing a potentially unproductive flame-war over semantics, I found documentation of a visual studio 2008 warning message that says:

warning C4312: 'type cast' : conversion from 'SDWORD' to 'SQLLEN *' of greater size

Yes, I can see that there is a space between the words 'type' and 'cast.'

---

### Post by eazar001 on 2013-01-01
And come on, just because something isn't explicitly stated in your most "trusted source", doesn't mean that you always have to use the word "pre-processor directive." for example.

If Microsoft is capable of getting over it, so can you. But I'll remember the next time I ask a question, to say "type conversion", or "casting", if this makes the community happy.

---

### Post by Bachstelze on 2013-01-01
> **eazar001 said:**
> 
If Microsoft is capable of getting over it, so can you. But I'll remember the next time I ask a question, to say "type conversion", or "casting", if this makes the community happy.

No, it won't. Conversion and casting are different things (casting is a way to in a sense "force" a conversion, but conversions also very frequently happen implicitly).

(Also, there is a number of good reasons to ignore standards, but "Microsoft does it" is not one of them.)

---

### Post by eazar001 on 2013-01-01
> **Bachstelze said:**
> No, it won't. Conversion and casting are different things (casting is a way to in a sense "force" a conversion, but conversions also very frequently happen implicitly).

Good, I'm glad Bachstelze speaks for the community. Nonetheless, I never asked for an explanation as to how conversions come about. Conversions can come about via assignment statements. Or they can come about through casting. Great.

---

### Post by eazar001 on 2013-01-01
[http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf)

Apparently a draft of the C99 standard has exactly one occurrence of 'type cast.' Enough said.

---

### Post by eazar001 on 2013-01-01
> **Bachstelze said:**
> No, it won't. Conversion and casting are different things (casting is a way to in a sense "force" a conversion, but conversions also very frequently happen implicitly).

(Also, there is a number of good reasons to ignore standards, but "Microsoft does it" is not one of them.)

Also, you will notice that it is under a section labelled "Type Conversions." Just use the search function in your viewer.

---

### Post by trent.josephsen on 2013-01-01
never mind, this conversation has nowhere productive left to go

---

### Post by eazar001 on 2013-01-01
Exactly. This is why I hate vocab arguments; if you can understand the guy without difficulty, let it go. Otherwise it will degenerate into a battle of two or more people correcting each others' spelling mistakes.

---

### Post by trent.josephsen on 2013-01-01
*other's

sorry... :-P

---

### Post by eazar001 on 2013-01-01
lol, it's okay, because:

Others' = plural possessive referring to something belonging to more than one person

But I'll resist the urge to comb through the previous parts of the thread.

---

### Post by eazar001 on 2013-01-01
Haha, and then some "self-proclaimed English expert" comes out, quotes it and says "But I won't [;"

etc., etc.

---

### Post by trent.josephsen on 2013-01-01
Nope, the phrase "each other" is necessarily singular.

//

---

### Post by eazar001 on 2013-01-01
Actually your grammar is fine. And other's is correct. I will admit this; you are right. Goodbye troll.

---

