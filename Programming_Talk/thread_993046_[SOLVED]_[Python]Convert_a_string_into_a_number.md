---
title: "[SOLVED] [Python]Convert a string into a number?"
date: 2008-11-25
forum: Programming Talk
---

### Post by fiddler616 on 2008-11-25
Hello,
As part of a project I'm working on, I end up scraping a number off a website--in this case 189.2 It's returned as a string--which would be fine, except I have to do math on it.
[PHP]
spam = "189.2"
spam = int(spam)
print spam + 1 [/PHP]
doesn't work--it throws up an error.
I'm a bit stymied about what else to do--I'm sure this is a perfectly simple task, but it's hard to Google. (I also realize that 189.2 isn't an int--I guess it's a floating point number(?) but Python has spoiled me into not learning as much as I should about that)

Thanks

---

### Post by dje on 2008-11-25
try:
```
spam = float(spam)
```
instead ;)

dje

---

### Post by fiddler616 on 2008-11-25
Thanks--that helped, but I'm still having issues:
[PHP]gas = float(gas) #Price of gas
print gas + 1
mpg = raw_input("How many miles per gallon do you get?")
dist = raw_input("How far are you traveling?") 
gas_cost = dist / mpg * gas
print gas_cost
[/PHP]
This returns gas + 1, and the two inputs, but throws an error before/while computing gas_cost. I'm stumped.

---

### Post by sisco311 on 2008-11-25
> **fiddler616 said:**
> Thanks--that helped, but I'm still having issues:
This returns gas + 1, and the two inputs, but throws an error before/while computing gas_cost. I'm stumped.

try:
[php]
gas = float(gas) #Price of gas
print gas + 1
mpg = float(raw_input("How many miles per gallon do you get?"))
dist = float(raw_input("How far are you traveling?")) 
gas_cost = dist / mpg * gas
print gas_cost[/php]

raw_input reads a string. you need to convert it to a float.

---

### Post by fiddler616 on 2008-11-25
> **sisco311 said:**
> try:
[php]
gas = float(gas) #Price of gas
print gas + 1
mpg = float(raw_input("How many miles per gallon do you get?"))
dist = float(raw_input("How far are you traveling?")) 
gas_cost = dist / mpg * gas
print gas_cost[/php]raw_input reads a string. you need to convert it to a float.
Wow, this thread keeps making me feel smarter and smarter....
Thanks though--that did the trick.

---

### Post by Tony Flury on 2008-11-26
eval works as well (and i would suggest is preferable)

using float will always return a float which might introduce errors if the actual input is an int (some ints cannot be accurately reproduced as floats), wheras eval will return an int if the input is an int, and only produce a float if the input needs a float.

---

