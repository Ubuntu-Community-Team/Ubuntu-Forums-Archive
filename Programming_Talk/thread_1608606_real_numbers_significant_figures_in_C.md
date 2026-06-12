---
title: "real numbers significant figures in C"
date: 2010-10-29
forum: Programming Talk
---

### Post by fasoulas on 2010-10-29
How can i set how many significant figures i want after decimal point in a float number in C.

i want something like this 
original number 5.1568794
rounded number 5.17

and be able to show this terminal with the printf() function and %f

---

### Post by dwhitney67 on 2010-10-29
```

printf("%.2f\n", value);

```
P.S.  When rounding 5.1568794 to two decimal places, you should expect 5.16, not 5.17.

---

### Post by trent.josephsen on 2010-10-29
Hate to break it to you, but 5.1568794 will never round to 5.17. ;)

On a serious note, the only way to get a fixed number of significant figures on a number whose order of magnitude is unknown is to use scientific notation.  %f won't work for this.  %g, with a precision of 3, will always give 3 significant figures, as will %e with a precision of 2.

If you're using the term "significant figures" to mean "digits after the decimal place", my high school physics teacher would like to have a word with you and you can do that with %f.

---

### Post by fasoulas on 2010-10-29
Thanks a lot for the help.
By the way yes 5.17 was a mistake.

---

### Post by worksofcraft on 2010-10-29
> **fasoulas said:**
> Thanks a lot for the help.
By the way yes 5.17 was a mistake.

I think 5.17 is correct and it is the standard library that makes the mistake. I actually wrote my own [formatting library]("http://code.google.com/p/speaknumber/") because there are a few other things that need fixing :P Like scientific notation should have exponents that are multiples of 3 IMHO, but my real issue is with internationalization of the formats.

---

### Post by Tony Flury on 2010-10-29
> **worksofcraft said:**
> I think 5.17 is correct and it is the standard library that makes the mistake.

I do hope you are joking : 5.1568794 will round successively to : 

5.1568794
5.156879
5.15688
5.1569
5.157
5.16 - and definitely not 5.17

---

### Post by jon zendatta on 2010-10-30
> **Tony Flury said:**
> I do hope you are joking : 5.1568794 will round successively to : 

5.1568794
5.156879
5.15688
5.1569
5.157
5.16 - and definitely not 5.17

Thats truncating not rounding?

---

### Post by lisati on 2010-10-30
> **jon zendatta said:**
> Thats truncating not rounding?

If it had gone to 5.15 that would be truncating.

---

### Post by worksofcraft on 2010-10-30
> **Tony Flury said:**
> I do hope you are joking : 5.1568794 will round successively to : 

5.1568794
5.156879
5.15688
5.1569
5.157
5.16 - and definitely not 5.17

Yeah my bad... didn't read it properly.
standard library does actually round it correctly.

---

