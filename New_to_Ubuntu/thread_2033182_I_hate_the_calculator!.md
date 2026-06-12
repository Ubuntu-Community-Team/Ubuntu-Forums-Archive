---
title: "I hate the calculator!"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by yeehi on 2012-07-25
I would like to be able to calculate compound interest using a calculator as follows:

enter lump sum
enter x
enter interest rate
enter =====

For example, if the lump sum is $100 and the interest rate is (a whopping!) 8%, I would do the following:

```
100 x 1.08 = = = = =
```

And then I will get the compounded sum after 5 years of compounding.

I can do this with the calculator in windows, but not with one I have found in GNU/Linux.

Can you recommend a calculator that can do this?

Thank you!

---

### Post by ub07 on 2012-07-25
I have installed many calculators so I've forgotten what the default calculator is in Ubuntu. Have you tried gcalc? There is also xcalc. If you don't mind installing some additional components, there is also kcalc.

All of these are available in the software center. I'm not sure about xcalc ... you might have to do sudo apt-get install xcalc.

---

### Post by peter d on 2012-07-25
Try this. It does the same as you're doing but using maths not tricks.

C * (1 + r/100)^n

where C is the cash you start with, r the interest rate as a percentage, n the number of years to compound.

---

### Post by robtygart on 2012-07-25
I don't know if this helps but you can use python

use

```
python
```

then type what your looking for
```
2+2
2*2
2/2
```

```
rob@rob-mobile:~$ python
Python 2.7.3 (default, Apr 20 2012, 22:44:07) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 2*2
4
>>> 2+2
4
>>> 2/2
1
>>> 

```

---

### Post by Jay MC on 2012-07-25
He's right...  the default calculator in Ubuntu doesn't support pressing "=" multiple times to repeat a function.  I've never noticed this before, because I use the calculator for, er, mostly adding two numbers together  :oops:

Pressing "=" more than once toggles between the answer you got, and the sum you entered (presumably so you can edit it and recalculate?).

Looking at what I have installed in Software Centre, the default calculator app ("Calculator") seems to be something called "gcalctool".  It sounds like it's definitely got loads of features ("financial, logical and scientific modes") but the lack of support for re-pressing "=" seems like a funny omission.

Googling around, gcalctool is a default bit of Gnome, so I would even suggest that the OP raises it with the devs.  Click [here]("https://live.gnome.org/Gcalctool").  It may be that there's a very good reason why they've gone with the "toggle" idea, but it's worth investigating.

---

### Post by Bufeu on 2012-07-25
> **ub07 said:**
> I have installed many calculators so I've forgotten what the default calculator is in Ubuntu. Have you tried gcalc? There is also xcalc. If you don't mind installing some additional components, there is also kcalc.

All of these are available in the software center. I'm not sure about xcalc ... you might have to do sudo apt-get install xcalc.The default calculator in Ubuntu is *gcalctool*.

---

### Post by Paqman on 2012-07-25
Compound interest is easy. You're half way there by expressing the interest rate as 1.08. If you want to find out the effect of that over say 10 years you'd simply multiply by 1.08^10. If it was over 20 years it would be 1.08^20.

So yes, any calculator that does powers can do compound interest.

You can also use Libre Office Calc to do interest rates, it has pretty much the same functions available as MS Office.

---

### Post by Jay MC on 2012-07-25
> **peter d said:**
> Try this. It does the same as you're doing but using maths not tricks.

C * (1 + r/100)^n

where C is the cash you start with, r the interest rate as a percentage, n the number of years to compound.

Peter D, you just blew my mind.

I'm terrible at maths.  Brief off-topic - I used to work in a bar with an old guy who'd once known a minor mathematical celeb (I forgot the details, but he was a professor of maths who'd had a slot on some light TV game show, probably before I was born).  In the pub, the prof was also a keen darts player.

For some reason, he could do all kinds of complex equations, but had a real blind spot for doing mental subtractions.  Darts scores are all about subtractions.  Apparently he kept getting it wrong and had to be corrected all the time.

Off-topic finished  :)

---

### Post by Jay MC on 2012-07-25
On a more serious note, there are a lot of good suggestions here for rephrasing the requirement as a single equation...  but a lot of calculator users won't be that good at maths.  Isn't hitting "=" to repeat the operation a standard (useful) feature?  It's a while since I've held a pocket calculator, but they all did it when I was young.  There's a "lowest common denominator" aspect here.

For instance, it's easy to square a number (even I can do that) but the default calculator still has a button to do it for you.

Having said which - I *am* squirrelling these equations away for future reference  :)

---

### Post by HiImTye on 2012-07-25
you can use gcalc's Fv function to calculate compounding interest, however, it uses a recurring payment method, assuming you are adding equal payments in at each period

for instance if I enter the following into the Fv function:
Periodic Payment: 100
Periodic Interest Rate: .08
Number of Periods: 5
I end up with 586.660096 as my answer


I'm not sure of an easy way to figure out a one-time payment compounding rate

---

### Post by yeehi on 2012-07-25
I have had a look on the calculator but I can't find this button:

^

How can I do ^ in the calculator?

Thank you!

---

### Post by HiImTye on 2012-07-25
go to mode>advanced and then enter a number, click 'Xy' (the y is superscript, like a power), enter the power

edit: I find that it is almost always easier to just use the keyboard when entering equations. you just hit the caret (^) key and move on. it's also easier for isolating sections in your equations such as:
100+(100*.08*5)
would be a single payment investment ($100) with 5 periods of compounding interest at 5% (not exactly, as it doesn't compound and then recalculate, but it's a simple way of doing it)

---

### Post by yeehi on 2012-07-25
Thank you very much for your help and suggestions, everybody.

I managed to enter the following in the calculator:

```
100×1.08^5
```

and got the answer:

146.93280768

I hope this is the right result for 100$ compounded 5 times at an interest rate of 8%.

I think I will write to the developers and see if they can add this functionality with the = button!

---

### Post by HiImTye on 2012-07-25
actually, that is the correct answer, if you enter it with multiple '=' signs. I suppose I could have just thought about it a little and ended up there. just remember that you need to change how you apply the caret for more complex equations (sometimes encasing your entire formula in brackets)

and also, BOOM 1000 beans!

---

### Post by mcduck on 2012-07-25
As mentioned, the default calculator has a financial mode, which includes a function for calculating periodic interest rates.

...but if you feel like trying a better calculator, I'd recommend Qalculate. Absolutely amazing and extremely powerful calculator, with a nice simple interface that hides behind itself way more functionality and features than one person could ever need.


(and while qalculate doesn't directly repeat the calculation by pressing equal sign, it does have the "Ans" option which allows you to use the result from previous calculation in the next one. So you could do "100 * 1.08" first, and then "Ans * 1.08", after which each press of the "="-button will add the 8% to the previous result. And of course there' are variety of ready functions for economics (and everything else) as well. :))

---

### Post by HiImTye on 2012-07-25
the periodic interest rate function in gcalc assumes multiple equal payments, so instead of simply adding the interest to the initial amount, it adds the interest, adds a new payment + interest, adds a new payment + interest, etc.

---

### Post by Enter t'Ibex on 2012-07-25
I like gcalctool

a practical solution is to simply highlight '+8%' and CNTRL-C and then CNTRL-V it to the end of the result and hit '=' (or enter is what I use) right afterward.
so that
100+8%
108.000000000
108.000000000+8%
116.640000000
116.640000000+8%

and so on...

This solution is generic to the actual math.  I have used this quite often for other repetitive calcs (where a spreadsheet program is just a bit overkill)

---

### Post by mike555 on 2012-07-26
I like "SpeedCrunch" ; [http://speedcrunch.org/en_US/index.html](http://speedcrunch.org/en_US/index.html)     ... it should be in package manager.

---

### Post by mapes12 on 2012-07-26
I'd be interested to hear if anyone knows of a Calculator with a "**%**" key?

BTW - they band me from darts at work cos I'm rubbish at subtracting. How mean........:-({|=

---

### Post by mcduck on 2012-07-26
> **mapes12 said:**
> I'd be interested to hear if anyone knows of a Calculator with a "**%**" key?

BTW - they band me from darts at work cos I'm rubbish at subtracting. How mean........:-({|=

Qalculate. ;)

Doesn't have a button for that, but allows you to use it if you type in the calculation using your keyboard.

---

### Post by asmoore82 on 2012-07-26
Isn't real interest compounded monthly?

---

### Post by Paqman on 2012-07-30
> **asmoore82 said:**
> Isn't real interest compounded monthly?

Same calculation to figure it out though.

---

