---
title: "Bash newbie help, swapping stuff around."
date: 2011-01-16
forum: Programming Talk
---

### Post by oopsie on 2011-01-16
I apologise for not being able to put what I mean into words very well. Is there an easy way to swap two pieces of text around?

I have a monstrosity of a line I've written for bash, and inside it is this
```
cut -d ' ' -f 5,8
```
Which you probably know shows the fifth and eighth element in a line of elements separated by spaces. What I'd like to know how to do though is to swap them around. I tried 
```
cut -d ' ' -f 8,5
```
But that doesn't swap them around at all.

So, is there an easy way to do this?

---

### Post by MadCow108 on 2011-01-16
maybe cut can also do it somehow but I personally prefer awk for splitting.
displaying 5 and 8 swapped would be:
echo "1 2 3 4 5 6 7 8" | awk '{print $8" "$5}'

---

### Post by ghostdog74 on 2011-01-16
> **oopsie said:**
>  I'd like to know how to do though is to swap them around. I tried 
```
cut -d ' ' -f 8,5
```
But that doesn't swap them around at all.

So, is there an easy way to do this?

use awk, as shown, or you can just the shell without calling external commands.
```

var="1 2 3 4 5"
set -- $var
echo "$5 $3"

```

---

