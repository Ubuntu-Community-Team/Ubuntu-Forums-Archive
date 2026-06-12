---
title: "[SOLVED] How does 'for' work in Python???"
date: 2008-08-09
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-08-09
So, how does for work in python? I don't get it when I read manuals that don't have examples.
Could you please make me at least one simple example about for, and explain it line by line, letter by letter. :confused:

---

### Post by LaRoza on 2008-08-09
> **crazyfuturamanoob said:**
> So, how does for work in python? I don't get it when I read manuals that don't have examples.
Could you please make me at least one simple example about for, and explain it line by line, letter by letter. :confused:

```

listOfNumbers = ['1','2','3']

for number in listOfNumbers:
    print number

```

It iterates over a list (or an iteratble object). The "number" is a local variable that takes the value of each member in the list as it loops.

---

### Post by NovaAesa on 2008-08-09
And in case you hadn't worked it out yet, you can generate a list of numbers with the range function. e.g.

```

>>> range(10)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> range(5, 15)
[5, 6, 7, 8, 9, 10, 11, 12, 13, 14]

```

---

### Post by LaRoza on 2008-08-09
> **NovaAesa said:**
> And in case you hadn't worked it out yet, you can generate a list of numbers with the range function. e.g.

```

>>> range(10)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> range(5, 15)
[5, 6, 7, 8, 9, 10, 11, 12, 13, 14]

```

And because it returns a list, you can iterate over it:
```

>>> for i in range(10):
...     print i
... 
0
1
2
3
4
5
6
7
8
9
>>> 

```

---

### Post by ghostdog74 on 2008-08-09
> **crazyfuturamanoob said:**
> So, how does for work in python? 

Have you read the tutorial ?
> 
I don't get it when I read manuals that don't have examples.

which manuals?

---

### Post by crazyfuturamanoob on 2008-08-09
> **ghostdog74 said:**
> Have you read the tutorial ?

which manuals?

Umm.. Python Library Reference, Python Reference Manual, and a book I have.

Their examples are too difficult to get. Especially when *my mother tongue isn't english.

*miss spelled

---

### Post by NovaAesa on 2008-08-09
Okay, I will try to explain it in as simple English as I can.

with the code:
```

for i in [1, 2, 3, 4, 5]:
    print i

```
there are a few confusing things all happening at once. The first thing is to understand with a for loop, the indented line (or lines) under the "for" part are repeated. Each time they are repeated, the variable after "for" changes value. The number of times that the contents of the loop are repeated depends on the number of items in the "list" in the for statement. In this case the loop will be repeated 5 times. Each time the loop repeats, the variable i will take a different value. The values taken will be according to what is in the list. In this example, the i value will be 1 during the first time through, 2 during the second time through, all the way up to 5 the fifth time through. You can then do something useful with the i value each time the loop loops.

Hope this helps, if there's anything here that you don't understand don't hesitate to reply back telling me which part was confusing.

---

### Post by crazyfuturamanoob on 2008-08-09
> **NovaAesa said:**
> Okay, I will try to explain it in as simple English as I can.

with the code:
```

for i in [1, 2, 3, 4, 5]:
    print i

```
there are a few confusing things all happening at once. The first thing is to understand with a for loop, the indented line (or lines) under the "for" part are repeated. Each time they are repeated, the variable after "for" changes value. The number of times that the contents of the loop are repeated depends on the number of items in the "list" in the for statement. In this case the loop will be repeated 5 times. Each time the loop repeats, the variable i will take a different value. The values taken will be according to what is in the list. In this example, the i value will be 1 during the first time through, 2 during the second time through, all the way up to 5 the fifth time through. You can then do something useful with the i value each time the loop loops.

Hope this helps, if there's anything here that you don't understand don't hesitate to reply back telling me which part was confusing.

Ok, I think I got it. Thanks :)

---

### Post by ghostdog74 on 2008-08-09
> **crazyfuturamanoob said:**
> Umm.. Python Library Reference, Python Reference Manual, and a book I have.

Their examples are too difficult to get. Especially when I mother tongue isn't english.

Read the [Python tutorial](http://docs.python.org/tut/node6.html#SECTION006200000000000000000). The library references comes later one you grasp the concepts.

---

### Post by crazyfuturamanoob on 2008-08-09
> **ghostdog74 said:**
> Read the [Python tutorial](http://docs.python.org/tut/node6.html#SECTION006200000000000000000). The library references comes later one you grasp the concepts.

You just posted another manual that contains more bad examples.

---

### Post by ghostdog74 on 2008-08-09
> **crazyfuturamanoob said:**
> You just posted another manual that contains more bad examples.

like what?

---

### Post by pmasiar on 2008-08-09
Unless you are not expert in couple programming languages (I do not remember your background), is extremely hard to learn a language from reading reference book (I know because I did it :-) ). Read tutorial or "Dive into Python" is you are experienced programmer, or start with beginner's texts (see sticky or go directly to wiki in my sig). Plenty of examples there.

---

### Post by spadewarrior on 2008-08-09
I personally found this book very easy to understand.

[http://www.swaroopch.com/byteofpython/](http://www.swaroopch.com/byteofpython/)

It's free and online.

Best of luck!

---

### Post by crazyfuturamanoob on 2008-08-10
Thanks. And I mean those 'reference book examples' with bad examples.
As a beginner, trying to learn my first programming language, on my own,
I don't understand nearly anything about reference manual's examples.

---

### Post by LaRoza on 2008-08-10
> **crazyfuturamanoob said:**
> Thanks. And I mean those 'reference book examples' with bad examples.
As a beginner, trying to learn my first programming language, on my own,
I don't understand nearly anything about reference manual's examples.

Don't worry about it. I had trouble with for loops also (although I never admitted it on the forum) in Python.

---

### Post by ghostdog74 on 2008-08-10
> **crazyfuturamanoob said:**
> Thanks. And I mean those 'reference book examples' with bad examples.
As a beginner, trying to learn my first programming language, on my own,
I don't understand nearly anything about reference manual's examples.

you keep saying that they are bad examples but you don't say which ones. You mentioned bad examples from the Python tutorial, so which ones are?

---

### Post by nvteighen on 2008-08-10
Yes, the for loop in Python is somewhat unusual, but interestingly useful.

My philosophical question is: is it wise to advice a total programmer newbie to learn a language that uses a "non-standard" way to loop things? What will he/she do when faced to C or C++'s for-loop?

Also, the Python for loop only makes sense if you are aware that it's simultaneously iterating the source and unpacking it into the target, whatever this is. C and C-like languages instead set the for-loop as shorthand for a "variable initializing + while-loop + incrementing" sequence.

---

### Post by LaRoza on 2008-08-10
> **nvteighen said:**
> Yes, the for loop in Python is somewhat unusual, but interestingly useful.
Lots of languages have it like that though. 

> 
My philosophical question is: is it wise to advice a total programmer newbie to learn a language that uses a "non-standard" way to loop things? What will he/she do when faced to C or C++'s for-loop?


The same thing they do when the are used to C's for loop and go to Python. Unless you wish to say one language is superior to the other, it doesn't matter.

> 
Also, the Python for loop only makes sense if you are aware that it's simultaneously iterating the source and unpacking it into the target, whatever this is. C and C-like languages instead set the for-loop as shorthand for a "variable initializing + while-loop + incrementing" sequence.

The C for loop only makes sense if you realise it is initialising, comparing and incrementing/decrementing (usually).

They are different, what difference does it make? The Python way makes it easier to do what the C for loop is mostly used to do.

---

### Post by nvteighen on 2008-08-10
> **LaRoza said:**
> 
The same thing they do when the are used to C's for loop and go to Python. Unless you wish to say one language is superior to the other, it doesn't matter.

The C for loop only makes sense if you realise it is initialising, comparing and incrementing/decrementing (usually).

They are different, what difference does it make? The Python way makes it easier to do what the C for loop is mostly used to do.

Nice way to break my arguments :) You're right; never thought it that way...

---

### Post by pmasiar on 2008-08-10
> **crazyfuturamanoob said:**
> Thanks. And I mean those 'reference book examples' with bad examples.
As a beginner, trying to learn my first programming language, on my own,
I don't understand nearly anything about reference manual's examples.

Examples are OK. Your approach is wrong :-)

As beginner, you don't know how to learn languages yet, but as I said before, reading reference manuals is the hard way. Sticky FAQ has links to good learning materials (wiki in my sig), where I collected free books targeted for beginners. So if you have problems, they are caused in part by you reading wrong books.

---

### Post by pmasiar on 2008-08-10
> **nvteighen said:**
> My philosophical question is: is it wise to advice a total programmer newbie to learn a language that uses a "non-standard" way to loop things? What will he/she do when faced to C or C++'s for-loop?

Also, the Python for loop only makes sense if you are aware that it's simultaneously iterating the source and unpacking it into the target, whatever this is. C and C-like languages instead set the for-loop as shorthand for a "variable initializing + while-loop + incrementing" sequence.

C does it in a way which is intuitive only to an expert who knows how CPU does it. Python abstracts away all that machinery, if you loop through a sequence of objects, you will get your objects one by one, very intuitive for a beginner. Later, if and when beginner need deeper understanding, she can dig deeper in C, but why confuse young impressionable minds without the need?

---

### Post by nvteighen on 2008-08-10
> **pmasiar said:**
> C does it in a way which is intuitive only to an expert who knows how CPU does it.

It's funny, why couldn't I ever climb into higher-level languages?? Javascript was a pain for me; Python is (for me, again) a bit hard to understand (though I like it; very powerful)... But I'm starting to understand some Assembly... Am I a CPU?

> Python abstracts away all that machinery, if you loop through a sequence of objects, you will get your objects one by one, very intuitive for a beginner. Later, if and when beginner need deeper understanding, she can dig deeper in C, but why confuse young impressionable minds without the need?

Possibly, I have to remember what is to be a beginner, don't you think?

---

### Post by pmasiar on 2008-08-10
> **nvteighen said:**
> Am I a CPU?

If you understand CPU better than humans, possibly you **are** CPU? :-)

> Possibly, I have to remember what is to be a beginner, don't you think?

Remembering how beginner thinks (or asking them, and listening to answers!) may help you to give better advice to beginners. It might be relevant or not - depends if your goal is to take into account how human mind works, or balance CPU's load :-)

---

