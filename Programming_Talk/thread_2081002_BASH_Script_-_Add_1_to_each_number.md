---
title: "BASH Script - Add 1 to each number"
date: 2012-11-05
forum: Programming Talk
---

### Post by UnknownFearNG on 2012-11-05
Hello all. I am trying to write a BASH script that will add 2 to each number in an argument. I know I need to use a for loop. For example, if I have a script named "add" and put:

```
add 12345
```

I want it to add the number 2 to EACH number and display it:

```
34567
```

I know it seems pretty easy, but I honestly am not sure how to do it. I could do it if it was separated by a space, but I want to do it as one "list" of numbers.

Thanks guys!

---

### Post by sisco311 on 2012-11-05
Sound like homework. So here is your hint: I would use parameter expansion and a C-style for loop.

[http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Loops_.28while.2C_until_and_for.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Loops_.28while.2C_until_and_for.29)

---

### Post by UnknownFearNG on 2012-11-05
> **sisco311 said:**
> Sound like homework. So here is your hint: I would use parameter expansion and a C-style for loop.

Not gonna lie, it is for homework, but I have posted it differently. But thank you for pointing me in the right direction! I didn't want the answer, just a starting point.

Don't mind me for asking, but with parameter expansion, does it not use arguments with spaces? I am trying it with numbers all in one line, no spaces.

---

### Post by sisco311 on 2012-11-05
You can use substring expansion to print the n'th character of a parameter/variable. 

Then you need a for loop to iterate over the characters (1st, 2nd... last)...

---

