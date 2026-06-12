---
title: "Straight Insertion Sort and Double-Linked List?"
date: 2009-10-10
forum: Programming Talk
---

### Post by xwhisper on 2009-10-10
Hello!
I have to sort Double-Linked List via Straight Insertion Sort. The Problem is I seem to do it somehow wrong. I got Segmentation Fault after the third time cycle starts, using numbers: 3 5 4 2 7 6 8 9 1
Anyone could help. I'm more looking for hint of what I'm doing wrong than ready-to-use code. Source attached below...

---

### Post by MadCow108 on 2009-10-10
use a debugger like gdb to step though the code.

I just ran it through with list 2<->1, this was the output:
Program received signal SIGSEGV, Segmentation fault.
0x080494a6 in StraightInsertionSort () at kpp.cpp:203
warning: Source file is more recent than executable.
203	        if(p->next->prev||p->prev) p->next->prev=p->prev;
(gdb) p p->next
$4 = (linked_list *) 0x0

p->next is a null pointer so p->next->prev is undefined

on the first sight the algorithm seems strange too, does insertion sort really need the add_before? If I remember correctly you only have to swap the links

---

### Post by xwhisper on 2009-10-10
Shell sort uses swapping, SIS takes a value, compares it with the previous values and moves it at appropriate place. I use add_before() to add it to that spot (or at least I intend), but obviously I'm doing this totally wrong...

---

