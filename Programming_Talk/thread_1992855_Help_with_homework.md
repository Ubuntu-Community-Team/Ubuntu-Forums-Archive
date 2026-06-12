---
title: "Help with homework"
date: 2012-05-31
forum: Programming Talk
---

### Post by looseleaf on 2012-05-31
Hey, I'm looking to see if anyone on here wouldn't mind looking over a simple code I've written for python.  I'm doing decision structures, and I am just totally bewildered as to why this isn't executing correctly.  
I run the program and this is what I get: 

```
This program will calculate the cost of shipping determined by package weight.
Please enter the weight of your package in lbs: 4
You have entered  4 lbs.
The cost of shipping will be $1.10.
```

No matter the number I enter into the input, it incorrectly displays "the cost of shipping will be $1.10.

Here is the program:
 
```
def packageInfo ():
    weight = input ("Please enter the weight of your package in lbs: ")
    print "You have entered " ,weight, "lbs."
    if weight <= "2":  
         print "The cost of shipping will be $1.10."
    elif weight > "2" and weight <= "6":
            print "The cost of shipping will be $2.20."
    elif weight > "6" and weight <= "10":
                print "The cost of shipping will be $3.70."
    elif weight > "10":
                    print "The cost of shipping will be $3.80."
    

def main ():
    print "This program will calculate the cost of shipping determined by package weight."
    packageInfo ()

main ()
```


If anyone can give me any suggestions I would really appreciate it..

---

### Post by looseleaf on 2012-05-31
Hey, I'm looking to see if anyone on here wouldn't mind looking over a simple code I've written for python.  I'm doing decision structures, and I am just totally bewildered as to why this isn't executing correctly.  
I run the program and this is what I get: 

[COLOR=Red]This program will calculate the cost of shipping determined by package weight.
Please enter the weight of your package in lbs: 4
You have entered  4 lbs.
The cost of shipping will be $1.10.[/COLOR]

No matter the number I enter into the input, it incorrectly displays "the cost of shipping will be $1.10.

Here is the program:
 
[COLOR=Red]def packageInfo ():
    weight = input ("Please enter the weight of your package in lbs: ")
    print "You have entered " ,weight, "lbs."
    if weight <= "2":  
         print "The cost of shipping will be $1.10."
    elif weight > "2" and weight <= "6":
            print "The cost of shipping will be $2.20."
    elif weight > "6" and weight <= "10":
                print "The cost of shipping will be $3.70."
    elif weight > "10":
                    print "The cost of shipping will be $3.80."
    

def main ():
    print "This program will calculate the cost of shipping determined by package weight."
    packageInfo ()

main ()[/COLOR]


If anyone can give me any suggestions I would really appreciate it..

---

### Post by anewguy on 2012-06-01
I don't know python, but I do know you are hijacking this thread - your posts have nothing to do with the topic.  Open your own thread - you may even want to try the ubuntu programming forum.

---

### Post by lisati on 2012-06-01
I've moved your post(s) to their own thread.

---

### Post by Bachstelze on 2012-06-01
Your problem is that you are trying to do arithmetic comparisons on strings. You need to convert the weight to an integer, and compare it to other integers (i.e., not to strings).

---

### Post by ofnuts on 2012-06-01
> **Bachstelze said:**
> Your problem is that you are trying to do arithmetic comparisons on strings. You need to convert the weight to an integer, and compare it to other integers (i.e., not to strings).Integers, or maybe floats...

---

### Post by trent.josephsen on 2012-06-01
Also note that when you do this:
```
    if weight <= 2:  
         print "The cost of shipping will be $1.10."
    elif weight > 2 and weight <= 6:
            print "The cost of shipping will be $2.20."
```

if the elif-branch is reached, you know that weight is greater than 2 (because if it weren't, the if-branch would have been executed instead). So the weight > 2 check is redundant and partially defeats the purpose of using elif's in the first place.

---

### Post by Vaphell on 2012-06-01
... and weight > 10 could be done with else:

besides printing all these lines is redundant, they are exactly the same except the number
it would be better to parametrize the print line and have it only once.
```
if   weight <=  2:  cost = 110  
elif weight <=  6:  cost = 220
elif weight <= 10:  cost = 370
else:               cost = 380

print "the cost will be $%.2f" % ( cost/100.0 )
```

another advantage is that you can pass the variable further to use it in some calculations, should such a need arise, while multiple prints are worthless in that aspect.

also note that i used integers (cents) because there is no risk of precision loss in case of integers, which happens in case of floats due to their internal representation. To get dollar value for presentation purposes - /100.0

---

