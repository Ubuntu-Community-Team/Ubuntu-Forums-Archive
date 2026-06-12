---
title: "Bash script help: awk time out of date and use"
date: 2009-06-11
forum: Programming Talk
---

### Post by barmylad on 2009-06-11
Hello,

I'm just learning bash scripting and need some help.

What i want to do is give a message at different times of the day, say good morning when between 06:00 and 11:59, good afternoon when its between 12:00 and 18:00 and finally good evening when its between 18:00 and 23:59.

like i said I'm just a beginner so be gentle :p

here is what i have so far:

date > time1
awk '{print $4}' time1

this gives me the time but after that I'm stuck, I have tried a few 'if' statements but i cant get it to work e.g: if (this) then echo "that" sort of stuff but no luck :(

Any help would be much appreciated.

Thanks.

Barmy.

---

### Post by unutbu on 2009-06-11
Are you looking for hints, or a solution?

---

### Post by Dill on 2009-06-11
You should check out the man page for **date**:

```
man date
```

Instead of having to redirect output or use awk to look for the field you need, you should be able to simplify the output of date to *hours*, from which you can generate your message accordingly.

If you're still having trouble with conditionals, I would suggest Googling "bash conditionals" and check out the examples in the pages you find.

Cheers,
Dill

---

### Post by barmylad on 2009-06-11
o a solution would be nice and if i could be cheaky enough to ask with an explanation too:D

I was going to say gimme some tips but its dong my head in now so someone please put me out of my misery.

---

### Post by barmylad on 2009-06-11
Ok thanks for the reply Dill I'll check that out.

---

### Post by unutbu on 2009-06-11
[PHP]#!/bin/bash
hour=$(date +%H)               # This returns just the hour
echo "$hour"                   # <-- See?
if [ "$hour" -lt 12 ]; then    # test if hour is < 12
    echo "Good morning"
elif [ "$hour" -lt 19 ]; then
    echo "Good afternoon"
else
    echo "Good evening"
fi
[/PHP]

---

### Post by barmylad on 2009-06-11
Haha thank you very much unutbu that is very helpful. ;)

I was going about it all the wrong way like Dill said, and in my if statements i was using ()  were i shouldn't have been and also {} braces.

Cheers again. :D

Barmy

---

### Post by ghostdog74 on 2009-06-11
> **unutbu said:**
> [PHP]#!/bin/bash
...
elif [ "$hour" -lt 19 ]; then
    echo "Good afternoon"
...
[/PHP]
there should be another check for 12 to 19 because from 1 to 11 is morning.

---

