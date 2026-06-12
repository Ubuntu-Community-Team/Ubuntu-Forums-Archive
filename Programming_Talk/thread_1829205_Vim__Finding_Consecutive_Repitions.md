---
title: "Vim : Finding Consecutive Repitions"
date: 2011-08-20
forum: Programming Talk
---

### Post by b1tchacked on 2011-08-20
IMP-Need a solution only in the scope of the text editor VIM!!!
----------------------------------------------------------------------------------------------------------------------------------
How to find n[fixednumber] consecutive repitions of a specified word with blankspaces or newline characters in between?

eg-
--
There are 10 strings "IDIOTS" and 100 strings "IDIOTS" in two separate regions of a text file consecutively. How to find the first occurrence of the  100 word sequence..

I tried many regular expressions but could not find an expression to search but could not search for consecutive repetitions of a fixed word for a fixed :mad:number of times........


Thanks in advance would help a lot for my project!!!!!!

---

### Post by gmargo on 2011-08-20
Regular expression for "IDIOTS" followed by whitespace including newline, 100 times:
```

\(IDIOTS\_s\+\)\{100}

```

---

### Post by b1tchacked on 2011-08-21
Thanks a lot!!! Perfect I made a tiny mistake and could learn the mistake in the regular xpression....... 

Can you give me some good source to learn regular expressions prefectly?:)

---

### Post by Brandon_R on 2011-08-21
There are many online tutorials but there is this one book in particular for  learning regular expressions and it's called mastering regular expressions. It's in the 3rd edition so make sure to get the updated one.

---

