---
title: "Bash scripting, repeating information on same line?"
date: 2007-10-27
forum: Programming Talk
---

### Post by darksizzle on 2007-10-27
Hi All

I am making a shell script that I would like to have the time displayed.  I have a function that checks the time every second and what I would like to do is have the time keep updating but instead of having it create a new line each time I would like it to keep updating on the same line.  It would be a huge help if someone can show me how to do this or point me in the right direction!

---

### Post by ghostdog74 on 2007-10-27
just an  idea
```

while [ 1=1 ];
do
  clear
 echo `date +%S`
 sleep 1
done

```

---

### Post by weresheep on 2007-10-27
Hi,

Here is something that should do the job.

```

#!/bin/sh -

while [ 1 -eq 1 ] ; do
  printf "$(date +%T)"
  sleep 1
  printf "\b\b\b\b\b\b\b\b"
done

```

This code uses printf to display the current time, sleeps for a second then uses printf to print a series of backspaces. Its crude but works.

However, this only works if nothing else prints to the screen whilst it is running. If you want to be able to update one part of the screen independently of another you'll need to look into using ncurses etc.

Hope that helps.

-weresheep

---

### Post by cwaldbieser on 2007-10-27
> **weresheep said:**
> Hi,

Here is something that should do the job.

```

#!/bin/sh -

while [ 1 -eq 1 ] ; do
  printf "$(date +%T)"
  sleep 1
  printf "\b\b\b\b\b\b\b\b"
done

```

This code uses printf to display the current time, sleeps for a second then uses printf to print a series of backspaces. Its crude but works.


You could print a "\r" instead of the backspaces.

---

### Post by Nuup on 2010-04-14
Hi,

while I was looking for something like this hint with printf, I happend to find this thread. The last hint was quite useful for me, So I registered, to drop a line, too. 
Despite the fact, that this thread is almost 3 years old. 

I hope this alias is a good solution, too: 

```
alias rtc='while [ 1 ]; do printf "\r$(date +%T)"; sleep 1s; done'
```

Kind regards,

Nuup

---

### Post by kvforum on 2013-03-03
Your response was 3 years old and I registered 3 years later just to say this was EXACTLY what I was looking for!!! So 6 years after the original post, this is still helpful. We should all reconsider whenever we hesitate to comment on a forum that we think is "too old" to resurrect.

---

### Post by codemaniac on 2013-03-14
Closed old thread.

---

