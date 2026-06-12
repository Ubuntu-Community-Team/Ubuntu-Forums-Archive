---
title: "Bash script question"
date: 2010-11-24
forum: Programming Talk
---

### Post by Reddoug on 2010-11-24
Hi All 

I am trying to figure out why when I type ./pnum Now is the time! it counts and displays the word on a separate line and why when I type ./pnum it does not do anything. Below is the script and out put. Trying to figure this out.

#!/bin/bash
count=0
for item in $*
do
  count=`expr $count + 1`
  echo $count $item
done

red@reds-VirtualBox:~$ ./pnum Now is the time!
1 Now
2 is
3 the
4 time!

Thanks, Doug

---

### Post by mobilediesel on 2010-11-25
> **Reddoug said:**
> Hi All 

I am trying to figure out why when I type ./pnum Now is the time! it counts and displays the word on a separate line and why when I type ./pnum it does not do anything. Below is the script and out put. Trying to figure this out.

#!/bin/bash
count=0
for item in $*
do
  count=`expr $count + 1`
  echo $count $item
done

red@reds-VirtualBox:~$ ./pnum Now is the time!
1 Now
2 is
3 the
4 time!

Thanks, Doug

if you type ```
./pnum
``` with nothing after it it's not going to do anything since you didn't give it any input.

---

### Post by DaithiF on 2010-11-25
the part I'm curious about is what you expect it to do when you don't give it any input?

---

### Post by universe-traveller on 2010-11-25
do you mean
```
echo -n $count $item
```

---

### Post by Reddoug on 2010-11-25
Hi 
Trying to gt straight in my head how  count=0  works and how the for statement with the (item in $*) is used. I figured out that it is counting the amount of words that are entered after ./pnum, I am not sure how it all works. 

Thanks, Doug

---

