---
title: "[SOLVED] Bash Sorting by Numbers"
date: 2008-11-20
forum: Programming Talk
---

### Post by melrom on 2008-11-20
Hi everyone.

I have a file containing a list of names with a numbers attached, in the following format: 

jsmith: 25
tomf: 39
melrom: 6

And I want to offer the option of sorting the entire list based on the number on the right. For instance, say they want to do this (I'm using getopts for the args) and they type ./samplescript -n to sort by number, I'd like the output to be:

melrom: 6
jsmith: 25
tomf: 39

I'm just not sure how to implement this.

---

### Post by Cracauer on 2008-11-20
sort -n -k 2

---

