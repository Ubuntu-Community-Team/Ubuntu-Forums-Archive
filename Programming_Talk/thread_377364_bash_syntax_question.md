---
title: "bash syntax question"
date: 2007-03-06
forum: Programming Talk
---

### Post by mynamewastaken on 2007-03-06
```
cut -d: -f1 < /etc/passwd | sort | xargs echo
```

Is there some advantage to doing it this way instead of cat/more/less /etc/passwd > cut ?

Only thing I can think of is it cuts out the cat/more/less...

---

### Post by mynamewastaken on 2007-03-06
```
cut -d: -f1 < /etc/passwd | sort | xargs echo
```

Is there some advantage to doing it this way instead of cat/more/less /etc/passwd > cut ?

Only thing I can think of is it cuts out the cat/more/less...

---

### Post by ghostdog74 on 2007-03-06
> **mynamewastaken said:**
> ```
cut -d: -f1 < /etc/passwd | sort | xargs echo
```

Is there some advantage to doing it this way instead of cat/more/less /etc/passwd > cut ?

Only thing I can think of is it cuts out the cat/more/less...

this command gets only the username in /etc/passwd. another way is 
```

awk -F":" '{print $1}' /etc/passwd 

```
without sorting. The difference is you do not need to use too many shell tools piped together.

---

### Post by Mr. C. on 2007-03-06
The cut command accepts a filename as an argument.  You do not need to redirect from STDIN (eg. cut /etc/passwd).

The line:

cat/more/less /etc/passwd > cut

will create a file name "cut".

See Week 4 Coursework here:  [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)  and Week 11 (Loose Ends) here: [http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

This will give an explanation about your question regarding "cat"...

MrC

---

### Post by kidders on 2007-03-06
[COLOR="Silver"](oops... sorry)[/COLOR]

---

### Post by mynamewastaken on 2007-03-07
> **Mr. C. said:**
> The cut command accepts a filename as an argument.  You do not need to redirect from STDIN (eg. cut /etc/passwd).

The line:

cat/more/less /etc/passwd > cut

will create a file name "cut".

See Week 4 Coursework here:  [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)  and Week 11 (Loose Ends) here: [http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

This will give an explanation about your question regarding "cat"...

MrC


Aye, just made a stupid typo a > where it should have been a pipe. I suppose my main question still stands in that is the only advantage to doing it that way saving out on the cat/less/more command?

---

### Post by Mr. C. on 2007-03-07
I gave you the answer!

 ...  Week 11 (Loose Ends) here: [http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

This will give an explanation about your question regarding "cat"...

---

