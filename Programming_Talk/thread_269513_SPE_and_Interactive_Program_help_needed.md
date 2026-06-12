---
title: "SPE and Interactive Program help needed"
date: 2006-10-01
forum: Programming Talk
---

### Post by Ziggy72 on 2006-10-01
I've just installed and started using SPE 0.8.2.a but I cannot work out how to enter data for an interactive program when using SPE. For example:
```

gallon_price = 2.41

print
print "This program calculates a car mileage"
print

distance = float(raw_input("How many miles were measured ? "))
print
consumed = float(raw_input("How many gallons of gas were consumed ? "))

mpg = distance / consumed
cost = gallon_price / mpg

print
print "mileage is", mpg, "miles per gallon"
print
print "cost is US$", cost, "per mile"
print

```

When I run this within SPE the program outputs:
> 
This program calculates a car mileage
How many miles were measured ? 


and sits there awaiting input which I can't enter directly on to the screen.
How do I enter my program input? Help will be much appreciated...

---

### Post by Ziggy72 on 2006-10-01
Ok - problem solved - silly me! I now see that there are 3 "run in terminal" options...

---

### Post by DirtDawg on 2006-10-01
Good work.

FYI, if you would like to print a blank line, you can use '\n' rather than a blank 'print' line.

Like this:
```
def yayforme():
    print "I say \nyay \n\nfor me!"
```
>>> yayforme()
I say
Yay

for me!

Have Fun! :KS

---

### Post by stani on 2007-02-24
Follow the new development of SPE on:

[http://pythonide.stani.be](http://pythonide.stani.be)

Stani

---

