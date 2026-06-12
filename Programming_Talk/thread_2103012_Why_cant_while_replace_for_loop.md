---
title: "Why cant while replace for loop ???"
date: 2013-01-08
forum: Programming Talk
---

### Post by vikkyhacks on 2013-01-08
As far as my perception goes for loop is used to run a statement some specific number of time and while loop to run until a specific condition is met.

but why cant while be like this and REPLACE the for loop

```
i=0;
while(i<10)
{
        code....
        ........
        i++;
} 
```

i know the basics of python, c, java and php .. help me with these languages and please don bring in any other languages.

---

### Post by Petro Dawg on 2013-01-08
> **vikkyhacks said:**
> As far as my perception goes for loop is used to run a statement some specific number of time and while loop to run until a specific condition is met.

but why cant while be like this and REPLACE the for loop

```
i=0;
while(i<10)
{
        code....
        ........
        i++;
} 
```i know the basics of python, c, java and php .. help me with these languages and please don bring in any other languages.

Why do you believe you can't?  

I would probably write it like this though...

```

var i = 0;

while(i<10){
code............;
i++;
}
```

---

### Post by Vaphell on 2013-01-08
while loop and for loop really are interchangeable

```
for( [COLOR="DarkGreen"]i=0;[/COLOR] [COLOR="Blue"]i<10[/COLOR]; [COLOR="Red"]i++[/COLOR] )
{
  ...
}

[COLOR="DarkGreen"]i=0[/COLOR];
while( [COLOR="Blue"]i<10[/COLOR] )
{
  ...
  [COLOR="Red"]i++[/COLOR];
}
```

---

### Post by ofnuts on 2013-01-09
> **vikkyhacks said:**
> As far as my perception goes for loop is used to run a statement some specific number of time and while loop to run until a specific condition is met.

but why cant while be like this and REPLACE the for loop

```
i=0;
while(i<10)
{
        code....
        ........
        i++;
} 
```i know the basics of python, c, java and php .. help me with these languages and please don bring in any other languages.

To add to the other fine comments: it's also a matter of style. If you use a for loop you are implicitly telling readers that you are going to exhaustively process all elements in a list or all values in a range (unless you break early). Playing with the loop index outside the for statement will raise the WTF rating of your code. The while statement; by contrast, indicates that anything can happen to invalidate the exit condition, and that the index is incidental and isn't a taboo variable.

---

### Post by greenpeace on 2013-01-09
In Python, the for loop is also very useful for processing the contents of a list in a sensible manner.  consider the following examples

```
#!/usr/bin/env python

my_list = ["a", "b", "c", "d", "e"]

# for loop to process the elements of the list
for item in my_list:
  print item


# whereas to do the same with a while loop
i = 0
while i < len(my_list):
  print my_list[i]
  i+=1
```

I think you'll agree that the for loop is "cleaner", and much better suited to this scenario.  The code is much easier to read (by you, and third parties), which is a good practice to keep.

---

### Post by rivode on 2013-01-09
The for loop has the loop initializaion and incrementing on one line, which can make things a bit more readable because these statements aren't scattered around.

---

### Post by lisati on 2013-01-09
Both the "for" and "while" loops have a place. As your experience grows, you'll probably find that in some situations, "for" is a more natural construct, and and in other places, "while" is more natural.

---

### Post by vikkyhacks on 2013-01-09
thanks for the answers, are u telling me that just for clean code we have for loop and we can also write for programs using while loops **WITHOUT USING FOR LOOPS in ALL CASES**, 

no offence, but i just am not satisfied with any of the answers, did dennis and all other great minds bring for loop just for CLEAN CODE, isn't there some kind of code which only for loop can do !!!

---

### Post by muteXe on 2013-01-09
In coding there's always more than one way to skin a cat. It's that simple.

---

### Post by spjackson on 2013-01-09
> **vikkyhacks said:**
> thanks for the answers, are u telling me that just for clean code we have for loop and we can also write for programs using while loops **WITHOUT USING FOR LOOPS in ALL CASES**, 

no offence, but i just am not satisfied with any of the answers, did dennis and all other great minds bring for loop just for CLEAN CODE, isn't there some kind of code which only for loop can do !!!
I'll talk C since that's what I know best of the 4 languages you list.

C has 3 looping contructs, for, while, and do..while. This is a common feature of many languages. However, in C at least, any loop expressed in one of the 3 forms can also be expressed in both of the other forms, perhaps with the addition of extra variables, tests and braces. In fact, all loops can be expressed with if and goto.

Some languages are more restrictive than C about how a for loop may be used, but so long as there remains a facility for an early exit from the loop (e.g. break, goto, return) then the looping
constructs are probably completely interchangeable.

The choice of construct is a matter of style; use whichever form seems most appropriate in the circumstances.

---

### Post by greenpeace on 2013-01-09
> **muteXe said:**
> In coding there's always more than one way to skin a cat. It's that simple.

+1 

Like many things in life, there are both good and bad ways of writing code.  

You should be trying to write efficient and easy to read (read, maintain, understand) code.  

To achieve this, you should be using the various tools at your disposal. "for" and "while" loops are just 2 of those tools.

---

### Post by ofnuts on 2013-01-09
> **vikkyhacks said:**
> thanks for the answers, are u telling me that just for clean code we have for loop and we can also write for programs using while loops **WITHOUT USING FOR LOOPS in ALL CASES**, 

no offence, but i just am not satisfied with any of the answers, did dennis and all other great minds bring for loop just for CLEAN CODE, isn't there some kind of code which only for loop can do !!!

Everything you do with a "while" can be done with a "for" and vice-versa ("for ( ;*condition*; )" is identical to "while (*condition*)"). And both can be replaced by "if" and "goto", if you insist...

---

### Post by trent.josephsen on 2013-01-09
> **vikkyhacks said:**
> no offence, but i just am not satisfied with any of the answers, did dennis and all other great minds bring for loop just for CLEAN CODE, isn't there some kind of code which only for loop can do !!!

No. In fact, in C, no looping construct at all is necessary; any program that can be written, can be written as one monolithic function with labels and goto. You can eliminate if and switch statements too, since C has the ternary operator ?:. But computer languages are designed for humans, not for computers. The CPU doesn't care if the code it's running has been run before, or if it's in a loop, or if it's in a different function -- it's just electronics; it does what the current instruction tells it (and a surprisingly small number of instructions is necessary to make a universal language). Loops and functions and blocks and everything else in a language, to include the language itself (including assembly languages), all exist for the sole purpose of *making it easier for humans to read and write code*.

So to answer your other question, yes, for loops only exist to make while loops a little cleaner in some cases.

---

### Post by muteXe on 2013-01-09
agreed. You can also get rid of a lot of if's and switches by using polymorphism.

---

### Post by vikkyhacks on 2013-01-09
Thanks every one for the reply, make it a lot better now !!!

> **spjackson said:**
> ... perhaps with the addition of extra variables, tests and braces. In fact, all loops can be expressed with if and goto.

That makes it very very very clear, I got it !!! :guitar::p....

---

