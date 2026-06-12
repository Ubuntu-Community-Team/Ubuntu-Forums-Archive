---
title: "A few python questions"
date: 2008-08-28
forum: Programming Talk
---

### Post by Bodsda on 2008-08-28
Hi, im attempting to write a blackjack program but ive stumbled upon a few problems.

When asking the player if they want to stick or twist im using a loop

```
ans = ""
while ans == "":
    ans = raw_input("Stick or Twist: ")

```

how can i make it just use the original prompt instead of printing a new prompt everytime the input is blank?

My other problem is how can i use regex (or anything else) to replace a string with something else?
eg -- card = "queen"

replace queen with 10

??

thanks

Bodsda

---

### Post by days_of_ruin on 2008-08-28
> **Bodsda said:**
> Hi, im attempting to write a blackjack program but ive stumbled upon a few problems.

When asking the player if they want to stick or twist im using a loop

```
ans = ""
while ans == "":
    ans = raw_input("Stick or Twist: ")

```

how can i make it just use the original prompt instead of printing a new prompt everytime the input is blank?

My other problem is how can i use regex (or anything else) to replace a string with something else?
eg -- card = "queen"

replace queen with 10

??

thanks

Bodsda

You should just make a dictionary that has the numerical value of each
card.```
>>cards = {'queen':10}
>>>print cards['queen']
10
```

---

### Post by jimi_hendrix on 2008-08-28
> **Bodsda said:**
> Hi, im attempting to write a blackjack program but ive stumbled upon a few problems.

When asking the player if they want to stick or twist im using a loop

```
ans = ""
while ans == "":
    ans = raw_input("Stick or Twist: ")

```



have it print stick or twist outside of the loop

```

>>> def test():
...     print "Stick or Twist: "
...     ans = ""
...     while ans == "":
...             ans = raw_input()

```

thanks also for giving me something to do on a boring day...make a texas hold em console game

---

### Post by nvteighen on 2008-08-28
> **Bodsda said:**
> Hi, im attempting to write a blackjack program but ive stumbled upon a few problems.

When asking the player if they want to stick or twist im using a loop

```
ans = ""
while ans == "":
    ans = raw_input("Stick or Twist: ")

```

how can i make it just use the original prompt instead of printing a new prompt everytime the input is blank?

Impossible without relying on a terminal-manipulating library. ncurses is the most used one and has Python bindings; and it's relatively easy to use it for what you want. Install the "libncurses5-dev" package.

> My other problem is how can i use regex (or anything else) to replace a string with something else?
eg -- card = "queen"

replace queen with 10

Using a dictionary?

---

### Post by nvteighen on 2008-08-28
> **jimi_hendrix said:**
> have it print stick or twist outside of the loop

```

>>> def test():
...     print "Stick or Twist: "
...     ans = ""
...     while ans == "":
...             ans = raw_input()

```


That will shift the input cursor one line for each non-valid input...

---

### Post by jimi_hendrix on 2008-08-28
o...ignore my answer then...

---

### Post by Bodsda on 2008-08-31
Thanks for the replies.

Il try the dictionary method out, cheers :)

---

