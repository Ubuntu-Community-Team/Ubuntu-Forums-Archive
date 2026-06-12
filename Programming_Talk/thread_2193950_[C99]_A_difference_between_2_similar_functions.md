---
title: "[C99] A difference between 2 similar functions?"
date: 2013-12-15
forum: Programming Talk
---

### Post by ppplayer80 on 2013-12-15
Hi,

I would like to ask what is the difference between these 2 functions:
[Function 1]("http://pastebin.com/aauhLr6L")
[Function 2]("http://pastebin.com/7fmDMncy")

Because I am 100% sure there must be a difference. When I run my program with a first function, my program works perfectly.

These 2 functions are run by this loop:
```
for (int Number=0; Number<8; Number++)
    {
        if (Function(tab, Number, x, y, &nx, &ny) == 1) 
        {
                        *...*
        }
    }
```
And of course I count from 1 to 8 when I run first function (because there is a 'switch' which takes Number from 1 to 8).

Thanks!

---

### Post by ofnuts on 2013-12-15
1) You should index the array with (Number -1) if Number is in 1..8.

2) Even given this, I would expect mopre parallelism between the values in the array and those used in the 'case' version. Your first "case" is (x+1, y-2) while its equivalent in the 'array' version gives (x+2,y-1). You have other such errors.

General comment: unless the function and variable names have been anonymized to be posted here, you should give more meaningful names to your variables and functions (and the leading uppercase is frowned upon in most coding conventions).

The 'array' version is much better than the 'case' one, but you can also express the deltas you apply to x and y as a short arithmetic expression based on "number". This may better explain to a future code reader(*) that these values are not completely arbitrary.

(*) You, 6 months from now, after a bad night or a hangover.

---

### Post by ppplayer80 on 2013-12-15
Thank you for the answer, @ofnuts!

> You should index the array with (Number -1) if Number is in 1..8.
I'm sorry, but I don't understand this :-(
EDIT//
Ah... I think I get it. But that's what I said in the first post! I count from 0 to 7 in an 'array' version and from 1 to 8 in a 'switch' one. 

> Even given this, I would expect mopre parallelism between the values in the array and those used in the 'case' version.
Yes. That is because these two codes come from other sources (the first one is found somewhere on the Internet and the second is made by me). But anyway, this shouldn't change anything since function is run in a for loop which repeats itself 8 times so every combination will be tried before leaving a loop.

> unless the function and variable names have been anonymized to be posted  here, you should give more meaningful names to your variables and  functions (and the leading uppercase is frowned upon in most coding  conventions).
Yep, I thought it will be easier for you if I replace words from my native language into this neutral version. Also there was no uppercase before creating this topic :P
Sorry, just thought it will be easier =)

> The 'array' version is much better than the 'case' one,
Exactly! And that is why I created this topic. I also think that the 'array' version is better and I want to make this version work.

> you can also express the deltas you apply to x and y as a short arithmetic expression based on "number".
What do you exactly mean? What kind of arithmetic expression?


And again, big thanks for the answer!

---

### Post by ofnuts on 2013-12-16
1) You can't create two functions that purposefully return different results from the same input ("Number) (*)and ask why there are differences. You built the differences in.... Otherwise what differences do you see that are meaningful for you?

2) If all you need is to make sure you generate all the cases, when you look at your function: 


[LIST]
[*]The absolute value of x is 1 or 2, and the absolute value of y is 2 or 1 (their absolute values are never equal) 
[*]X can be either positive of negative 
[*]Y can be either positive of negative 
[*]This makes 8 cases, indexed by numbers 0 to 7, that are represented exactly by all combinations of bits from 000 to 111, and are the combination of three binary choices. 
[*]So you can look at your index as an array of flags: 
[/LIST]
[INDENT]```
    X X X 
    A A A
    | | |
    | | +--- 0: abs(x)=1, abs(y)=2, 1: abs(x)=2, abs(y)=1
    | +----- 0: x>0: 1: x<0
    +------- 0: y>0: 1: y<0
```
[/INDENT]

[LIST]
[*]Translated into C code using bit masks (with 1: values, 2, sign of x, 4: sign of y): 
[/LIST]
[INDENT]```

    int x = ((n & 1) + 1) * ((n & 2) ? -1: +1);
    int y = (2 - (n & 1)) * ((n & 4) ? -1: +1); 


```
[/INDENT]

(*) and actually it's not even the same input if you don't use the same range in the input parameter...

---

