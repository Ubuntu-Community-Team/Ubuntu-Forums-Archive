---
title: "How would one perform this?"
date: 2011-05-24
forum: Programming Talk
---

### Post by KodR on 2011-05-24
> >>> x = 1
>>> print x
1
>>> 1 = x
  File "<stdin>", line 1
SyntaxError: can't assign to literal

Here I am able to make x = 1, but I cannot make 1 = x. I suspect this has to do with 1 being a number, and numbers cannot be the first character in a command, or that specific command?

How would I be able to make 1 = x?

---

### Post by simeon87 on 2011-05-24
You cannot assign a variable to a number because a number is just a number. But if you want to associate a number with a variable you can use a dictionary:

```
>>> p = {1: 2}
>>> p[1]
2
>>> 
```

You can also do:

```
>>> x = 5
>>> p = {1: x}
>>> p[1]
5
>>> 
```

---

### Post by dwhitney67 on 2011-05-24
1 is 1.  It cannot be another value.  Go back to math class if you somehow forgot this.

The assignment operator [=] takes the right-hand side value and assigns it to the left-hand side.  I'm not aware of any high-level programming language that does not respect this rule.

---

### Post by Zugzwang on 2011-05-24
Perhaps it is important to add that "=" in programming languages (except Pascal) isn't quite the same as the mathematical "=". While the latter denotes equality where indeed the order of the operands shouldn't make a difference, in many programming languages (like Python), "=" also denotes an assignment, i.e., a *redefinition* of the value of some variables, where the variable is always on the right-hand side of the "=" operator. Thus "1=x" would mean "from this time onwards, the value of '1' should be what is right now the value of 'x'". Most programming languages do not allow redefining the meanings of atomic values as this hardly ever makes sense and is typically not desired.

---

### Post by StephenF on 2011-05-24
If you want a variable that looks like a number you can precede it with an underscore.
```

>>> x = 1
>>> _1 = x
>>> print _1
1

```

---

### Post by KodR on 2011-05-24
> **simeon87 said:**
> 
>>> p = {1: 2}
>>> p[1]
2
>>>

Thanks dude!

I tried this, but it didn't work:

> p = {3011: Test}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'Test' is not defined

Is there a way to make a number equal a word?

---

### Post by dwhitney67 on 2011-05-24
> **KodR said:**
> 
Is there a way to make a number equal a word?

```

aNumber = "word"

```

---

### Post by StephenF on 2011-05-24
> **KodR said:**
> Is there a way to make a number equal a word?
Put the word in "quotes".

---

### Post by satanselbow on 2011-05-24
> **dwhitney67 said:**
> ```

aNumber = "word"

```

LOL


I really might be better to use numbers... as numbers... 

You can quite merrily use letters/words to carry the value of or represent numbers but it really does not work - for quite a few quite obvious reasons - the other way round... You are rather trying to reinvent the wheel in a really bad way... like out of butter... or dark matter... fun trying; but ultimately doomed to fail :D

---

### Post by KodR on 2011-05-24
That won't do. I need the number being a number, not a code.

---

### Post by simeon87 on 2011-05-24
> **KodR said:**
> That won't do. I need the number being a number, not a code.

```
>>> p = {1: "word"}
>>> p[1]
'word'
```

---

### Post by satanselbow on 2011-05-24
> **KodR said:**
> That won't do. I need the number being a number, not a code.

I think you need to take a step back and reimagine what you need to accomplish. It is very unlikely that in reality you need your variable to "be a number" ... the "value" of your variable yes! no problem you already have examples of how to implement that but the variable itself... no...

---

### Post by KodR on 2011-05-24
Ok, so what I need to do is make a number equal a phrase:

> 3000 = "this is an example"

As mentioned earlier, the above command is illegal and does not work, I need to find a work around to accomplish it.

Also, Its seems there will always be people on forums that lack the communication skills to answer a question straight up.
I could not care for suggestions. If you can't just give me a straight up answer to the way I want to do it, then don't waste my time with them.

The request is VERY STRAIGHT FORWARD! AGAIN, I DO NOT CARE FOR SUGGESTIONS OR YOUR OPINION WHY YOU THINK I SHOULD DO IT ANOTHER WAY!!!

---

### Post by matt_symes on 2011-05-24
> **KodR said:**
> Ok, so what I need to do is make a number equal a phrase:



As mentioned earlier, the above command is illegal and does not work, I need to find a work around to accomplish it.

Also, Its seems there will always be people on forums that lack the communication skills to answer a question straight up.
I could not care for suggestions. If you can't just give me a straight up answer to the way I want to do it, then don't waste my time with them.

The request is VERY STRAIGHT FORWARD! AGAIN, I DO NOT CARE FOR SUGGESTIONS OR YOUR OPINION WHY YOU THINK I SHOULD DO IT ANOTHER WAY!!!

wtf ?

caio

---

### Post by dwhitney67 on 2011-05-24
> **kodr said:**
> 
the request is very straight forward! Again, i do not care for suggestions or your opinion why you think i should do it another way!!!

Read this carefully... IT CAN"T BE DONE!!!

---

### Post by satanselbow on 2011-05-24
KodR... really...

Go read a book you are not fit to be online.

Ciao

---

### Post by Barrucadu on 2011-05-24
> **KodR said:**
> Ok, so what I need to do is make a number equal a phrase:

No you do not. That is a stupid and completely unrequired thing to do. You have already been told how to do something like this, but you don't seem capable of reading the thread, so I'll tell you the answer.

```
codes = {3000 : "foo"}
```

Tada! Then you access it with codes[3000].

I think you need to learn a bit of Python before you try to write a program, as you seemingly don't even have basic knowledge of the language.

---

### Post by nvteighen on 2011-05-24
Let's see.

Numbers are defined by the quantity they represent, so redefining them is quite useless. Imagine this: if I were able to redefine 1 to be the letter 'A', that would mean that from there on I wouldn't be able to express the quantity of suns existing in our solar system, e.g. Number 1 would be lost and you'd be counting 0, 2, 3, 4... as 1 now means 'A', which does not refer to a quantity.

This is valid not only for numbers but for all values predefined by laws external to programming: numbers, characters, arithmetical and logical operators, among others.

What you seem to want is to create an association between some arbitrary number and some arbitrary data. For example, we could be designing some simple encryption code in which 1000 means "hello" and 1 means "the fox is in the kitchen". I understand that from a semiotic point of view, that could be considered a case of redefinition; but in programming, it's impossible to redefine numbers.

The solution is to use a hash. A hash is a kind of associative data structure that allows accessing some data by using a key. Think of it as something that can associate some data A with some data B. For the example above:

```

hash = {1000 : "hello", 1 : "the fox is in the kitchen"}

```

If I accessed the key 1000 in the hash, I should get "hello". If I accessed 1, I'd expect "the fox is in the kitchen". The problem is that this data structure isn't bidirectional. You cannot ask for the key k such that hash[k] is "hello", because in principle "hello" could be the value for several different keys.

In Python, hashes are oddly called "dictionaries". It's odd in the sense that only Python calls them that way. The syntax I've used above is the Python's one, like all other posters in this thread.

Now, a true "bidirectional" hash that effectively modelled the 1000 <-> "hello" relation would need some work around the default hash/dictionary data structure. I'm not sure if you want that and chances are very high that you'll be doing fine with the default "unidirectional" one (key -> value).

---

### Post by Petrolea on 2011-05-24
> **KodR said:**
> Ok, so what I need to do is make a number equal a phrase:



As mentioned earlier, the above command is illegal and does not work, I need to find a work around to accomplish it.

Also, Its seems there will always be people on forums that lack the communication skills to answer a question straight up.
I could not care for suggestions. If you can't just give me a straight up answer to the way I want to do it, then don't waste my time with them.

The request is VERY STRAIGHT FORWARD! AGAIN, I DO NOT CARE FOR SUGGESTIONS OR YOUR OPINION WHY YOU THINK I SHOULD DO IT ANOTHER WAY!!!

[U]Could someone make this guy quiet or restrict his access for some time because he's getting really annoying.
[/U]
And what you want to do is assign a value to a number. It already has a value, it is a NUMBER! 
What you want to do is probably array or comparing input to 3000 and printing a string.

---

### Post by DangerOnTheRanger on 2011-05-24
> **dwhitney67 said:**
> Read this carefully... IT CAN"T BE DONE!!!

```

+float('inf')

```

Thank you sir.
To the OP: This breaks all the rules of programming. It never has been done, and never *will *be done.

---

### Post by slavik on 2011-05-24
> **KodR said:**
> Ok, so what I need to do is make a number equal a phrase:



As mentioned earlier, the above command is illegal and does not work, I need to find a work around to accomplish it.

Also, Its seems there will always be people on forums that lack the communication skills to answer a question straight up.
I could not care for suggestions. If you can't just give me a straight up answer to the way I want to do it, then don't waste my time with them.

The request is VERY STRAIGHT FORWARD! AGAIN, I DO NOT CARE FOR SUGGESTIONS OR YOUR OPINION WHY YOU THINK I SHOULD DO IT ANOTHER WAY!!!
You ask for a work around (which multiple people have shown examples for) but yet do not want another way to do it. Pick one and don't contradict yourself.

```

> 10 = "blah"
> print 10
blah

```

Is that what you want to accomplish? If this is related to your other thread, you need to use a dictionary as people have already pointed out in this thread. What you want (the above piece of code) goes against all programming languages.

= is a binary assignment operator. It requires two items: 1. an l-value (something fit to be a symbol as defined in the programming language being used) and 2. an expression. l-value has to be on the left side.

A bit more on the subject: [http://en.wikipedia.org/wiki/Value_%28computer_science%29](http://en.wikipedia.org/wiki/Value_%28computer_science%29)

---

