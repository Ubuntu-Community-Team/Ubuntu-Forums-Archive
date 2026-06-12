---
title: "Subtracting two rows from a text"
date: 2015-03-23
forum: Programming Talk
---

### Post by mcparty2 on 2015-03-23
Good Afternoon,

I have a file with a list of numbers... we will call numbers.txt here, every hour, there will be a new line added with a new amount (the value will only increment upwards)

10
2345
4356
5468
35683

From this file, take the last row (35683) and subtract the second to last row (5468) to equal a new variable. Having read through the rather confusing man pages and the forum, I cannot find the answer I am looking for.
So far this is what I have, however it gives minus figures:

```

tail -n2 numbers.txt | paste -sd- - | bc 
-30215

```

Can anyone assist or point me in the right direction please?

Kind regards

---

### Post by SeijiSensei on 2015-03-23
> **mcparty2 said:**
> From this file, I am trying to take the last row and subtract it from the second to last row to equal a new variable. Having read through the rather confusing man pages and the forum, I cannot find the answer I am looking for.
So far this is what I have, however it gives minus figures:

Perhaps because that is the correct answer?

5468 - 35683 = -30215

If you expected a positive value, you should be subtracting the second-to-last row from the last row, not the other way around.

---

### Post by mcparty2 on 2015-03-23
Thank you for your response. My wording is not very clear, even I'm confused re-reading it, apologies. (I shall edit it to avoid further confusion)

What I was trying to say is:

Take the last row 35683
Subtract the second to last row 5468

Which should give a positive number. I am not sure how to achieve this, the man pages for paste are a little sparse.

---

### Post by Lars Noodén on 2015-03-23
You could do it with [awk](http://manpages.ubuntu.com/manpages/trusty/en/man1/awk.1posix.html).

```

awk 'BEGIN { row = 0 } { prev=row; row=$0} END { print row  - prev } ' numbers.txt

```

The BEGIN clause gets executed once, before things start.  The END clause also gets executed once, but after things are done.  In the middle it reads in one line at a time from *numbers.txt* which goes into $0 which is then saved in the variable 'row'

---

### Post by matt_symes on 2015-03-23
Hi

If you want to keep your existing pipeline, you can use sort.

```
tail -n2 numbers.txt | sort -nr | paste -sd- - | bc
```

Example...

```

matthew-laptop:/home/matthew:3 % cat tmp                                               
10
2345
4356
5468
35683
matthew-laptop:/home/matthew:3 % tail -n2 tmp | sort -nr | paste -sd- - | bc
30215
matthew-laptop:/home/matthew:3 % echo 35683 - 5468 | bc
30215
matthew-laptop:/home/matthew:3
```

I suspect there may be a better way of doing this though.

EDIT: Nicely done Lars.


Kind regards

---

### Post by mcparty2 on 2015-03-23
*VirtualHighFives all around.
I forgot about sort, and as for AWK, I looked at the man pages and my head exploded.

Thanks you all for your help

---

