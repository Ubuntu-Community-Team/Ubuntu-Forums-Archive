---
title: "Trouble using threads"
date: 2010-09-26
forum: Programming Talk
---

### Post by -A- on 2010-09-26
So my program is supposed to take two sorted arrays and put them into one big sorted array using threads. 

Problem is that for any input I give, some of the elements in the resultant array remain 0, and I cant figure out why.

When I try to debug, after putting a breakpoint in the thread functions, after a few hits GDB tells me that "Error accessing memory address <something> : Input/output error."

Edit: *embarrassed* Ok, so I found the error, which was just a small index out of place. 

But does anyone know the reason for GDB saying that?

---

