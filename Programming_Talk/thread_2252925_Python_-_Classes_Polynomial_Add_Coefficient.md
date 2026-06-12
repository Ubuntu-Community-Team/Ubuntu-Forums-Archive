---
title: "Python - Classes: Polynomial Add Coefficient"
date: 2014-11-15
forum: Programming Talk
---

### Post by Yozuru on 2014-11-15
Hello good people!

I am working on a practice problem in my python book and I came across an interesting question. So I am doing a class for polynomials, in my constructor (__init__), I will have tuples. So the goal of this is to make this into a dictionary with the (exponent, coefficent at the end). I managed to do just that. 

But I was wondering what would happen if you have two tuples with the same exponents? To make it look better, I would want to add the two coefficients together and make it into one key:value pair. Trouble is that I am having a bit of trouble figuring it out. This is what I have currently so far:

```
class Poly:
    def __init__(self, *termpair): 
        self.t_dict = {}
        for key, value in termpairs:
            self.t_dict[value] = (key) # Reverses key value pairs
            if key in self.termdict:
                self.t_dict[key] += key # Should add coefficent to current 1
            if key not in self.t_dict:
                # Creates a new entry for the exponent
```

Mines unfortunately does not come out right and I need some help on it if you do not mind. I am a visual learner so this is one of the reasons why programming is so hard. 

Any help is appreciated!

Edit: So I know if an exponent exist, then I must add the coefficent to the one already in the dict. And that if it is not, then it will be added onto the list. So I need an if-else or if-elif statement.

---

### Post by ofnuts on 2014-11-16
Do yourself (and us) a favour. Stop using the generic "key", "value" variable names. Call them "exponent" and "coefficient" ("exp" and "coeff", if you are lazy). Maybe the problem will become obvious, because right now it's hard to tell if you expect the dictionary keys to be the coefficients or the exponents...

---

### Post by Yozuru on 2014-11-18
Hi nuts!

Its always good to see a reply from you, you've helped me a lot in the past.

I have taken your advice and changed my variable names. It helped me to solved my problem so thank you a lot! You're awesome.

---

