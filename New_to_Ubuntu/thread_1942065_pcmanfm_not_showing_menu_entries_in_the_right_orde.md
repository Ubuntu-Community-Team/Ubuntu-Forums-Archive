---
title: "pcmanfm not showing menu entries in the right order"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by cheatos on 2012-03-16
Hi there,

I have a wierd problem when using pcmanfm on my lubuntu system.
Somehow it doesn't show the entries in alphabetic but in some random order.

I am confused each time I open pcman and I am starting to get really annoyed by this.
I already have chosen that the default sorting order should be alphabetically but it didn't work.
I even found a cinfog file somewhere on my filesystem where I was able to change the sort oder (it was just a number) and I tried 0, 1 and 2 but still nothing.

How can I make pcmanfm display my menu entries in a usable order? Because now I always have to click the title bar and then reconfig the sort oder to sort by name which is just stupid...

Thanks for your help!

---

### Post by JC Cheloven on 2012-03-16
Hi, 

The expected behaviour is: you click in the category you want to use for the shake of sorting (name, description, size,...), and pcmanfm sorts by that. First time you clik, it sorts in ascending orded, second click in descending order, and so on. It's supposed to be remembered for the next time you open pcmanfm.

If for any reason this doesn't work for you, please try the following:
With no pcmanfm window open, at a terminal, type 
```
nano ~/.config/pcmanfm/lubuntu/pcmanfm.conf
```
The file is quite self-explaining. The relevant lines are at the end (for me), which should read:
sort_type=0
sort_by=2
Edit as appropriate, save (ctrl-O), exit (ctrl-X), and open pcmanfm to see if that worked.

---

### Post by cheatos on 2012-03-17
Thank you, this worked.

I had the sortby option set to 1 and then it was a weird sorting order (btw what order is order1? Is it the last edit date or so?)

I'll mark this as solved.

---

### Post by JC Cheloven on 2012-03-19
Glad you solved it.

sort_by=2 means "sort by name". 
3 is to sort by size, 
7 is to sort by date
1 ... I don't find what it is for, I think it's undefined (?). That could have been causing your problems.

But of course you shouldn't need to know (or use) that under normal circumstances. That config file should be auto-updated every time you click in the categories of pcmanfm.

---

### Post by cheatos on 2012-03-20
Okay, thanks for that info, weird numbering ^^
I thougt it may start with 0 and 0 is sort by name so I tried 0 first and then 1, when it still didn't work I thought I'd try posting here

---

