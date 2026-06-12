---
title: "Vi reg exp find string"
date: 2012-05-03
forum: Programming Talk
---

### Post by fokuslee on 2012-05-03
Hi All 
I have a question on building a regular expression, this is probably the best place for it
I only have Vi on an Unix machine and need to look at an error log.
I know the time of the error was 
May<white spaces>2<white spaces>06:<some minutes>:<some seconds> 

I was in Vi trying to find this string but my expression is not correct at all
what is the reg exp equivalent of my search string? 
Also how do you find next and find previous in Vi

Thanks abunch

---

### Post by SuaSwe on 2012-05-03
Hi fokuslee,

To find next and previous, use / to search then just press n for "next" and p for "previous". :)

You could use cat instead of vi to display to terminal and use "May 2 06:" for example, inserting or removing whitespace as necessary. Far as I know you can use:

```

/May 2 06:

```

(for example) in escape mode within vi as well, to search for instances of that string. Once it's found it, use n and p to toggle between the results. Does this help or have I misunderstood the question?

---

### Post by fokuslee on 2012-05-03
/May  2  06: is the first thing i tried but returned no pattern found
so i suspect it's to do with white spaces.  Maybe there is 3 instead of 2 white spaces? what is the regular expression of one or more white spaces? [].* ?

---

### Post by Lars Noodén on 2012-05-03
A regular expression with zero or more whitespaces can be done like this: [font=Courier New]/May**[[:space:]]***2[/font]

Also when working with logs you might consider using [less](http://manpages.ubuntu.com/manpages/precise/en/man1/less.1.html) or [egrep](http://manpages.ubuntu.com/manpages/precise/en/man1/egrep.1.html).  You can also pipe [font=Courier New]grep[/font] through [font=Courier New]less[/font]:
[font=Courier New]egrep "May**[[:space:]]***2" /var/log/some.log | less[/font]

---

### Post by fokuslee on 2012-05-03
Thanks all 
problem solved

---

### Post by codemaniac on 2012-05-03
> **Lars Noodén said:**
> A regular expression with zero or more whitespaces can be done like this: [font=Courier New]/May**[[:space:]]***2[/font]

Also when working with logs you might consider using [less](http://manpages.ubuntu.com/manpages/precise/en/man1/less.1.html) or [egrep](http://manpages.ubuntu.com/manpages/precise/en/man1/egrep.1.html).  You can also pipe [font=Courier New]grep[/font] through [font=Courier New]less[/font]:
[font=Courier New]egrep "May**[[:space:]]***2" /var/log/some.log | less[/font]
Lars Noodén ,
your regex will match zero or more occurences of white spaces .
The records that dont have spaces between **May **and **2** will also get matched by your regex .
Consider the below input .
```

May 2 06:
May206:
May          2                                          06:
```
The egep regex will match the 2nd row also , but the OP dont wnat that .The below would ensure one or more spaces between month and date .
```
"May[[:space:]]+2"
```

---

### Post by Lars Noodén on 2012-05-03
@codemaniac: thanks for catching that.  I have the bad habit of using * everywhere, even when it's not correct.  + is the right answer.

---

