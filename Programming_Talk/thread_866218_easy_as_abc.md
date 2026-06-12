---
title: "easy as abc"
date: 2008-07-21
forum: Programming Talk
---

### Post by shifty2 on 2008-07-21
I notice that python was born out of the ABC project - creating a language as similar to english as possible.

From wikipedia here is a piece of example code:
```
HOW TO RETURN words document:
   PUT {} IN collection
   FOR line IN document:
      FOR word IN split line:
         IF word not.in collection:
            INSERT word IN collection
   RETURN collection

```

How long do you think it will be before we get a perfect ABC language. Will I ever be able to write, for example, this code:
```

For all real numbers, if that number is divisble 
by two add it to p, the set of even numbers. Add 
all numbers in the set of even numbers together.

```
Obviously you could argue that a language like this would be flawed - but think how awesome it would be to express your thoughts in code that simply.

---

### Post by WW on 2008-07-21
That could be interesting, but I don't know about "awesome". You still have to think like a programmer, and state your programs carefully.  For example, your "program" has several bugs:
[list]
[*] "For all real numbers...":  I think you mean "For all integers...", or maybe "For all positive integers...".
[*] You haven't initialized p to the empty set.
[*] You have an infinite loop, and even it it ever did finish, the answer is infinite.
[/list]
:)

---

### Post by Steveway on 2008-07-21
There is a propietary language called Plain English.
You can write your code in plain english and it will parse it and produce real code. 
EDIT: You can get it here: [https://www.osmosian.com/](https://www.osmosian.com/)

---

### Post by shifty2 on 2008-07-21
> **WW said:**
> That could be interesting, but I don't know about "awesome". You still have to think like a programmer, and state your programs carefully.  For example, your "program" has several bugs:
[list]
[*] "For all real numbers...":  I think you mean "For all integers...", or maybe "For all positive integers...".
[*] You haven't initialized p to the empty set.
[*] You have an infinite loop, and even it it ever did finish, the answer is infinite.
[/list]
:)
Well it doesn't matter if its real numbers/integers or whatever since I will still end with the even numbers. It was largely an example of what could take place - Even languages in the future won't be able to manage infinite loops ;)

I'm just wondering if its something that will be possible in the future, for example having gone from machine code to python - is the next step possible?

---

### Post by WW on 2008-07-21
> **shifty2 said:**
> Well it doesn't matter if its real numbers/integers or whatever since I will still end with the even numbers. It was largely an example of what could take place - Even languages in the future won't be able to manage infinite loops ;)

Yes, but the "real numbers" version is uncountably infinite. :)

---

### Post by shifty2 on 2008-07-21
As is positive integers etc...All irrelevant to my point though :) This new english obviously is very easy to confuse then.

---

### Post by beren.olvar on 2008-07-21
yet another irrelevant point is that
as far as i know, the cardinality of positive integers is countably infinite, not as those presumptuous real numers.

maybe such a lenguage would be easier to undertand, but i think it would be far more difficult to write. Remember, a computer does what you tell it to do, not what you want it to do (this post is a good example)

cheers

---

### Post by dribeas on 2008-07-21
> **shifty2 said:**
> I notice that python was born out of the ABC project - creating a language as similar to english as possible.


Depends on your definition of 'as similar as possible'. Natural languages have a tendency of being unprecise and context sensitive.

Bob saw the boy in the mountain with a telescope.

Who has the telescope, bob? the boy? Artificial intelligence has had quite an investment in natural language processing and I am not sure it is worth it. You can find quite 'natural' languages, SQL for example. Reading an (not-too-complex) SQL sentence is quite natural

select name, surname, phone from personel where name='robert';

---

### Post by shifty2 on 2008-07-21
> **beren.olvar said:**
> yet another irrelevant point is that
as far as i know, the cardinality of positive integers is countably infinite, not as those presumptuous real numers.

maybe such a lenguage would be easier to undertand, but i think it would be far more difficult to write. Remember, a computer does what you tell it to do, not what you want it to do (this post is a good example)

cheers

Yikes. That post lead to some googling and a massive brush up on my maths. Definitely something I should not be doing at this time of night. From what I can gather, countably infinite is defined as a set that can be mapped to the natural numbers - the positive integers therefore positive integers must be countably infinite? Then with the real numbers we get onto the continium hypothesis? How they are different sizes?

---

### Post by dribeas on 2008-07-21
> **shifty2 said:**
> Yikes. That post lead to some googling and a massive brush up on my maths. Definitely something I should not be doing at this time of night. From what I can gather, countably infinite is defined as a set that can be mapped to the natural numbers - the positive integers therefore positive integers must be countably infinite? Then with the real numbers we get onto the continium hypothesis? How they are different sizes?

Simple answer: there are more real numbers than natural ones. Even if there are just as many natural numbers as integers (positive and negative included) or even fractions. As there are just as many integers as natural numbers you can 'count' them. Not quite related to the post though.

Counting integers:
First integer is 0, then you count positive followed by negative:
Second is 1
Third is -1
Fourth is 2
Fifth is -2... 

As there are infinite natural numbers for each posible integer you can find a natural number that represents its position. That is not possible with real numbers.

   David

---

### Post by beren.olvar on 2008-07-21
The proof of it, I can remember was given by a dude called Cantor. It involved the existence of a uncontable object called number X or something similar.

look at this page [http://www.mathpages.com/home/kmath371.htm](http://www.mathpages.com/home/kmath371.htm) 
I havent read it, but seems to have it explained.

cheers

---

### Post by Torajima on 2008-07-21
Coding in plain english can be a pain in the butt.

I've done some coding in Applescript in the past, a language fairly close to plain english (and a great tool for automating a Macintosh).

The problem is, plain english is 'wordy'... you end up typing twice as much code to get things done.

The other problem is, there are a lot of different ways to say something in English, but generally the interpreter only understands ONE way.

---

### Post by shifty2 on 2008-07-21
> **Torajima said:**
> Coding in plain english can be a pain in the butt.

I've done some coding in Applescript in the past, a language fairly close to plain english (and a great tool for automating a Macintosh).

The problem is, plain english is 'wordy'... you end up typing twice as much code to get things done.

The other problem is, there are a lot of different ways to say something in English, but generally the interpreter only understands ONE way.

My answers to these posts are almost always coming back to: if the computer could think...I imagine at the point in time when there is genuine AI there will be a computer language that is english.

---

### Post by pmasiar on 2008-07-21
> **shifty2 said:**
> Obviously you could argue that a language like this would be flawed - but think how awesome it would be to express your thoughts in code that simply.

Funny, where are all those experts from another thread  accusing me that I ignore hard math focusing on pragmatical skills? Here I can show that I **do** know some theory:

[http://en.wikipedia.org/wiki/Chomsky_hierarchy](http://en.wikipedia.org/wiki/Chomsky_hierarchy)

Programming languages are context-free languages. Natural languages are very different - type 3. So obviously conversion you want is impossible.

---

