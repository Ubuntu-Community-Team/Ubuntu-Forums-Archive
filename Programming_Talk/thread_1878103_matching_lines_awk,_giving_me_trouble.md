---
title: "matching lines awk, giving me trouble"
date: 2011-11-09
forum: Programming Talk
---

### Post by Drenriza on 2011-11-09
Hi all.

I have a file which is as below

 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 4            0.1.9-0.5.1
 5            2.1.4-1.0.0
 5	       2.1.5-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0

What i want to do is get awk tell me on a few lines, the lines who is different from the others.
So i get output with unique and non-duplicated lines.

Example.
The above gets to be
4            0.1.9-0.5.1
5            2.1.4-1.0.0
5	      2.1.5-1.0.0

And all the other lines get discarded.
Hope it makes sense. 

Kind regards.

---

### Post by Arndt on 2011-11-09
> **Drenriza said:**
> Hi all.

I have a file which is as below

 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0
 4            0.1.9-0.5.1
 5            2.1.4-1.0.0
 5	       2.1.5-1.0.0
 5            2.1.4-1.0.0
 5            2.1.4-1.0.0

What i want to do is get awk tell me on a few lines, the lines who is different from the others.
So i get output with unique and non-duplicated lines.

Example.
The above gets to be
4            0.1.9-0.5.1
5            2.1.4-1.0.0
5	      2.1.5-1.0.0

And all the other lines get discarded.
Hope it makes sense. 

Kind regards.

sort -u

---

### Post by Drenriza on 2011-11-09
Now when i see your solution i see that the solution was staring me in the face the entire time :p
Earlier in my script i have an sort -n |uniq to do the same thing just to some other information :D

Thanks for triggering my mind.

Kind regards

---

