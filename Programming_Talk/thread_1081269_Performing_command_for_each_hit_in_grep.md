---
title: "Performing command for each hit in grep"
date: 2009-02-26
forum: Programming Talk
---

### Post by Visti on 2009-02-26
Hi guys, I'm doing a small script and I've seem to hit a wall here:

Basically, I want to write a script to check for updates on a certain website, but only displaying the headlines in the terminal.

So looking at the site, I see that every headline has a "posted by:" line under it, so I came up with this command right here:

```
lynx -dump http://www.rlslog.net | grep -B2 Posted | cut -b 1-3 --complement
```

It just greps for the word posted and displays a few lines above it as well, while cutting off lynx's link numbering. Now this returns a bunch of not very neatly formatted headlines including both the "posted by" line, the headline I want and a space in between.

Now here's what I would like to do:
Format it using something like "head -1", but for each hit. Then it would return a nice list of just the information I want. Is this possible at all?

Can it be achieved by a script using a for loop or something similar?

---

### Post by monkeyking on 2009-02-26
use xargs

---

### Post by sisco311 on 2009-02-26
```
lynx -dump http://www.rlslog.net | grep -B2 Posted | grep -v Posted | sed -e 's/\[.*\]//' -e '/^--$/d' -e '/^$/d'
```

---

### Post by Visti on 2009-02-26
> **sisco311 said:**
> ```
lynx -dump http://www.rlslog.net | grep -B2 Posted | grep -v Posted | sed -e 's/\[.*\]//' -e '/^--$/d' -e '/^$/d'
```

Thanks!

This worked, but it seems xargs might do it in a more readable way (sed and awk stuff still look like nothing to me and I have no idea where to begin). 

However if I try xargs it feeds every word into head, no matter what arguments I use.

---

### Post by geirha on 2009-02-26
You could make a while loop that reads the output line by line, but only outputs every fourth line.
```

lynx -dump http://www.rlslog.net | grep -B2 Posted | 
while read line; do
    echo "$line"
    # Read and forget the next three lines
    read
    read
    read
done

```

EDIT: I tried running it now. All those headlines seem to start with that link number, so you could also just grep for that.
```
lynx -dump http://www.rlslog.net | grep -B2 Posted | grep '^\[[0-9]\+\]'
```

---

### Post by Visti on 2009-02-26
> **geirha said:**
> You could make a while loop that reads the output line by line, but only outputs every fourth line.
```

lynx -dump http://www.rlslog.net | grep -B2 Posted | 
while read line; do
    echo "$line"
    # Read and forget the next three lines
    read
    read
    read
done

```

EDIT: I tried running it now. All those headlines seem to start with that link number, so you could also just grep for that.
```
lynx -dump http://www.rlslog.net | grep -B2 Posted | grep '^\[[0-9]\+\]'
```

Ah, that second solution looks pretty efficient, but since it's not that intensive a task, I'll just stick with sed! I even used the example given here to modify it for some other sites, learning about sed in the process.

Thanks everyone!

---

