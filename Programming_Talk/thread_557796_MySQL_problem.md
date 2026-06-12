---
title: "MySQL problem"
date: 2007-09-23
forum: Programming Talk
---

### Post by dodgem on 2007-09-23
I'm trying to perform a function in mysql which would look something like this if the actual fields were displayed:

blah blah where ',4,6,7,12,' like '%7%' and blah blah

the problem i have is that both ',4,6,7,12,' and '7' are in tables, so what i actually have is:

blah blah where Contract.SiteList like %Site.SiteID% and blah blah

Obviously that doesn't work, but hopefully it demonstrates what i'm trying to achieve!  Any ideas on how i can solve this?  There could well be mysql functions i don't know of that will help...

Thanks :)

---

### Post by dodgem on 2007-09-23
LOL

As usual i've called for help before looking properly for an answer myself!!

In case it's useful to anyone else....

blah blah where (find_in_set(Site.SiteID, Contract.SiteList) != 0) and blah blah

works perfectly :)

(you'll notice how little time it took me to find and test the solution then reply!!!  I should learn from this ;) )

---

