---
title: "[Python] Coding Excercise"
date: 2011-06-29
forum: Programming Talk
---

### Post by ki4jgt on 2011-06-29
This is kind of a game, but, it is an exercise. The rules are simple. Each user will add/remove one line of code daily, in order to build the current round's program. At the beginning of each round, the user who finished the last round, will state the program for this round.

Moving a line of code is two steps. It is removing and adding. You may comment what ever you'd like in your post, but you MAY NOT force/expect another user to follow your code flow. They have their own ideas as to how the program should flow. All programs started in this thread are under public domain as per GPLv3+.

As most tutorials online are still based on Python 2, we will begin with it and see if we can progress to 3 and maybe even 4 (once it is developed)

EDIT: The program is considered complete when it does what it's intended to do, fancy graphics, extra additions, extra care put in the program are not required  for the program to be considered completed.
All in all, this would both allow experienced programmers to review things, and it would allow less experienced programmers to dissect programs line by line

Calculator
```
a = raw_input("Please \"ENTER\" your value: ")
```

---

### Post by nzjethro on 2011-06-29
```
a = raw_input("Please \"ENTER\" you[COLOR=red]r[/COLOR] value: **[COLOR=red]"[/COLOR]**)
```

You're going to run into some issues if you don't close that string. And, I think you missed an "r".

:p

---

### Post by ki4jgt on 2011-07-01
> **nzjethro said:**
> ```
a = raw_input("Please \"ENTER\" you[COLOR=red]r[/COLOR] value: **[COLOR=red]"[/COLOR]**)
```

You're going to run into some issues if you don't close that string. And, I think you missed an "r".

:p

Thanks LOL, I was in the middle of something and was trying to rush along :-(

```

while a.isdigit() <> True:
    a = raw_input("Please \"ENTER\" your value: ")

```

---

### Post by pafoo on 2011-07-03
```
a = raw_input('Please "ENTER" your value:')
```

Instead of escaping the quotes just replace first double with single

Also lets instead make the calculator a better script by not asking questions. (Avoid the BS make it take arguments)

Like...

```

import sys
num1 = sys.argv[1]
nsign = sys.argv[2]
num2 = sys.argv[3]

```

---

### Post by ki4jgt on 2011-07-05
> **pafoo said:**
> ```
a = raw_input('Please "ENTER" your value:')
```

Instead of escaping the quotes just replace first double with single

Also lets instead make the calculator a better script by not asking questions. (Avoid the BS make it take arguments)

Like...

```

import sys
num1 = sys.argv[1]
nsign = sys.argv[2]
num2 = sys.argv[3]

```

Nice, but the idea is to force the current coder to work off the ideas of other coders so, their brains will be forced to think in different ways. That's why it goes line by line, each user adding their own line.

---

### Post by tatterdemalion on 2011-07-05
If i get it right i should add another line. Right?

```
if a.isdigit():
```

---

### Post by ki4jgt on 2011-07-05
> **tatterdemalion said:**
> If i get it right i should add another line. Right?

```
if a.isdigit():
```

pretty much.

---

### Post by Arndt on 2011-07-05
I seem to remember that there was a description of what the program is meant to do, but now I only see the word "calculator". Is that the whole specification?

---

### Post by TwoEars on 2011-07-05
> **ki4jgt said:**
> Thanks LOL, I was in the middle of something and was trying to rush along :-(

```

while a.isdigit() <> True:
    a = raw_input("Please \"ENTER\" your value: ")

```

This is not Pythonic at all.
What is the main benefit of Python? Readability. 

```
while not a.isdigit():
    a = raw_input('Please "ENTER" your value: ')

```

---

### Post by Arndt on 2011-07-05
> **TwoEars said:**
> This is not Pythonic at all.
What is the main benefit of Python? Readability. 

```
while not a.isdigit():
    a = raw_input('Please "ENTER" your value: ')

```

We had better give 'a' some value first:

```
a=""
while not a.isdigit():
    a = raw_input('Please "ENTER" your value: ')

```

---

### Post by pafoo on 2011-07-05
> **TwoEars said:**
> This is not Pythonic at all.
What is the main benefit of Python? Readability. 

```
while not a.isdigit():
    a = raw_input('Please "ENTER" your value: ')

```

Ok lets press on with the calc. I like the while loop check so since we will be asking the same question multiple times, lets define our question as a function so we dont repeat any code.

```

def question(a=[FONT=monospace]'Please "ENTER" your value[/FONT]: '):
    answer = raw_input(a)
    while not answer.isdigit():
        print "Sorry not a valid number"
        answer = raw_input(a)   
    return answer 

number = question()

```

---

### Post by ki4jgt on 2011-07-06
> **TwoEars said:**
> This is not Pythonic at all.
What is the main benefit of Python? Readability. 

```
while not a.isdigit():
    a = raw_input('Please "ENTER" your value: ')

```

You're right. It's not Pythonic. It's setup to make you think in different ways. When you were a kid, did you ever play the game where your family went through the car and each person was only allowed to add one word? It's hard to imagine how one word can change an entire story, or force someone to takes curves and turns to avoid your negative word you just put into the entire story to make it turn out for the bad, when they wanted good. So, no it's not Pythonic. It's mentally challenging.

```

def question(a='Please "ENTER" your value: '):
    answer = raw_input(a)
    while not answer.isdigit():
        print "Sorry not a valid number"
        answer = raw_input(a)   
    return answer 

number = question()
number2 = question()

```

---

### Post by TwoEars on 2011-07-06
> **ki4jgt said:**
> You're right. It's not Pythonic. It's setup to make you think in different ways. When you were a kid, did you ever play the game where your family went through the car and each person was only allowed to add one word? It's hard to imagine how one word can change an entire story, or force someone to takes curves and turns to avoid your negative word you just put into the entire story to make it turn out for the bad, when they wanted good. So, no it's not Pythonic. It's mentally challenging.

```

def question(a='Please "ENTER" your value: '):
    answer = raw_input(a)
    while not answer.isdigit():
        print "Sorry not a valid number"
        answer = raw_input(a)   
    return answer 

number = question()
number2 = question()

```

Just because it's a challenge doesn't mean it's an excuse to write _****_ poor code. While I'm at it, that's a poor name for a variable intended to hold a question. If anything in this context, I would've thought "a" might have held the answer.

As a side note, how on earth did you magically jump from
```
a=""
while not a.isdigit():
    a = raw_input('Please "ENTER" your value: ')
```
to
```

def question(a='Please "ENTER" your value: '):
    answer = raw_input(a)
    while not answer.isdigit():
        print "Sorry not a valid number"
        answer = raw_input(a)   
    return answer 

number = question()
```
?
I thought the idea was to add one line at a time? (Perhaps I just don't understand)

---

### Post by pafoo on 2011-07-06
Ya, I kinda messed up with 1 line at a time! My bad.

The naming on the variable is a because I didnt care to change the original variable

---

### Post by cgroza on 2011-07-06
What is the point of this thread again? If you want to learn something, your are bettor off alone.

---

### Post by matchett808 on 2011-07-06
Not to disagree but I have recently started learning python (I could already do bash, c, php and some other stuff too) and this was quite an interesting read for me.....

.....Probably not much use if you have just started programming full stop.

---

### Post by pafoo on 2011-07-06
> **ki4jgt said:**
> You're right. It's not Pythonic. It's setup to make you think in different ways. When you were a kid, did you ever play the game where your family went through the car and each person was only allowed to add one word? It's hard to imagine how one word can change an entire story, or force someone to takes curves and turns to avoid your negative word you just put into the entire story to make it turn out for the bad, when they wanted good. So, no it's not Pythonic. It's mentally challenging.


my add on

```

def question(a='Please "ENTER" your value: '):
    answer = raw_input(a)
    while not answer.isdigit():
        print "Sorry not a valid number"
        answer = raw_input(a)   
    return answer 

number = question()
number2 = question(a='Please "ENTER" your second value: ')

basic_operators = ['*',  '/',  '+', '-']


```

---

