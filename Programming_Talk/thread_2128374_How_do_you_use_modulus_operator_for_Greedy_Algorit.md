---
title: "How do you use modulus operator for Greedy Algorithm"
date: 2013-03-23
forum: Programming Talk
---

### Post by hatsoff on 2013-03-23
suppose user has given us floating point number(like 0.37$) and we want it to covert into decimal by roundingoff (mayb such that it doesn't affect on answer) and then use modulus operator on them.
P.S
i have been working on project that says take amount of money from user and return back such that first use biggest possible coin(quarter,dime,nickel and penny ) and give output how much coin used up in returning back.

I wrote program it worked correctly but each time it gives me one coin less,when i debug with cout at every level problem appears on the last stage when it compensate with penny(0.01)[when a penny subtract with 0.02 it gives output of 0.009999 instead 0.01..that's creating problem]

So i decided how about if i convert float into decimal and use modulus operator and use its remainder to give it next possible coin.
while(coin can be used)
{
counter++ //coin counter
remainder = remainder%quarter(could be penny,nickel etc) //currently working as user_input = user_input-quarter(etc)
}
each time coin increase
input amount decreases

Thanks;),

---

### Post by Tony Flury on 2013-03-23
Don't deal with your cash as fractions of your of a dollar/pound - work in integers (i.e. pennies) - and then you wont get rounding errors.

---

### Post by lisati on 2013-03-23
> **Tony Flury said:**
> Don't deal with your cash as fractions of your of a dollar/pound - work in integers (i.e. pennies) - and then you wont get rounding errors.

True. When you're dealing with money, you want all the accuracy that you can muster, and using integers is often the easiest way of achieving this.

---

### Post by iMac71 on 2013-03-23
why do you use in your program```
remainder = remainder%quarter
```instead of```
remainder = fmod(quarter,remainder)
```:?:

---

### Post by trent.josephsen on 2013-03-23
hatsoff didn't name a language, there may not even be an fmod function...

---

### Post by iMac71 on 2013-03-23
> **trent.josephsen said:**
> hatsoff didn't name a language, there may not even be an fmod function...since hatsoff wrote> **hatsoff said:**
> I wrote program it worked correctly but each time it gives me one coin  less,[COLOR=#ff8c00]**when i debug with cout**[/COLOR] at every level problem appears on the last  stageI supposed that he was programming in C++.

---

### Post by trent.josephsen on 2013-03-23
You are probably right. :)

---

### Post by hatsoff on 2013-04-03
Got it Thank you guys!

---

