---
title: "Vim - delete the text between pattern1 and pattern2"
date: 2012-07-06
forum: Programming Talk
---

### Post by boukli on 2012-07-06
Hi all,

I'm trying to a edit a big file, in which there are, on each line, more than one occurrence of "pattern1" and "pattern2", as follows :
> bababa pattern1 bibibi pattern2 bobobo pattern1 bebebe pattern2 bububu  etc.

I used Vim with the following command : 
> :%s/pattern1.*pattern2//

The effect of it is that it takes the first occurrence of pattern1, and delete all that follows until the last occurrence of pattern2 is reached. But what I want is to delete the text between each "pattern1-pattern2", so that the example above becomes :
> bababa bobobo bububu

How can I do this ?

---

### Post by MadCow108 on 2012-07-06
by default regex are usually try to match as much as possible, you need a non-greedy or eager match
in vim this works like this
%s/pattern1.\{-}pattern2//g

see :help non-greedy

---

### Post by boukli on 2012-07-06
Thank you, it works like a charm !

I will study the documentation to understand how it works.

---

