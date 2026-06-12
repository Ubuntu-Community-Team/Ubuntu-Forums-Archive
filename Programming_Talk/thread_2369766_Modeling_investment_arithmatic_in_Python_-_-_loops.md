---
title: "Modeling investment arithmatic in Python - - loops"
date: 2017-08-26
forum: Programming Talk
---

### Post by Drone4four on 2017-08-26
I am having trouble getting a python script to run.

The purpose of my script is to calcualte a return on the user’s investment every year for however many years the client would like to keep their money invested. 

So in my script I ask the user how much tthey want to invest.  Then I ask the user how much they anticipate the anual return in percent.  And then finally using a loop I perform the calculation, one year at a time. 

Here is my script: [https://pastebin.com/X8AtRLpW](https://pastebin.com/X8AtRLpW)

There is no traceback, so the syntax is fine.  It’s just my arithmetic calculation

I figure the line with my mistake is line 14.  Say for example the user enters $1000 as their initial investment.  If they choose 2 % interest and keep it invested for 5 years, then at line 14 should be read by the interpreter as:

```

new_total = 1000 * 1.02 * i (each time the loop iterates - - the number of years the user wants it invested)

```

So with my physical calculator, such values should calculate to $1,126.16 for 5 years.  That’s is what I am trying to accomplish.  But the result in my interpreter a the end of the fifth year is $4,000.00! So I tried changing the anual_mult variable by removing the “+ 1”, so that the anual_mult in the loop (at line 14) is just 0.02, but the the total in the output shows $0.00 for each year. I also tried changing some of the variables from integers to floats. Didn’t help.

There is obviously something going very wrong with my Python model of the investment arithmetic.  

Can anyone lend a helping hand?

Thanks for your attention.

---

### Post by spjackson on 2017-08-26
Changes are marked '# CHANGED'
```

#!/usr/bin/env python2

amnt = int(raw_input("How much would you like to invest in dollars? >> "))

percent = int(raw_input("How much do you anticipate you will earn with this investment in percent? >> "))

percent = percent/100.0 # CHANGED We don't want integer division

anual_mult = percent + 1

years_invested = int(raw_input("How long would you like to keep your money invested (in years)? >>  "))

new_total = amnt # CHANGED
for i in range(0,years_invested):
     new_total = (new_total * anual_mult) # CHANGED
     int(new_total)
     print "Your new total is, ${:.2f}".format(new_total)
     pass


```

---

### Post by Drone4four on 2017-08-26
Thank you **@spjackson** for your help.  Those three small changes has made my script behave as intended.  We don’t want integer division, I had to finish declaring the new_total variable properly and in turn there was a better way handling the new_total variable properly in the loop.  

Now I have decided to modularize my code by using two functions. When I ran my new code with the two new functions, the interpeter helpfully pointed to some issues which I was able to correct.  Now when I attempt to run the code, it’s as if invoking python in my terminal doesn’t even register that it is interacting with my script:
```

$ python investment-loop.py
$

```

Here is what my script looks like now: [https://pastebin.com/2QUpw6Gd](https://pastebin.com/2QUpw6Gd)

Any advice?

---

### Post by spjackson on 2017-08-27
> **Drone4four said:**
> Now when I attempt to run the code, it’s as if invoking python in my terminal doesn’t even register that it is interacting with my script:
```

$ python investment-loop.py
$

```

Here is what my script looks like now: [https://pastebin.com/2QUpw6Gd](https://pastebin.com/2QUpw6Gd)

Any advice?
What your script does now is define two functions: start and invest. You need to call the start function for example by adding at the bottom of your script:
```

start()

```

---

### Post by Drone4four on 2017-08-27
Thanks again, **@spjackson **.  That worked perfectly.  My script runs really well now.  

I will be back here if I make any changes or encounter any new issues

:P

---

