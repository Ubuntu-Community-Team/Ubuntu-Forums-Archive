---
title: "Compiz Mess Up"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Covalent Bond on 2011-10-15
Recently upgraded to 11.10; fooled around with compiz, and when I closed compiz all I had was a desk top with no launcher and no tool bar to access any programs.  Using terminal, I completely removed compiz then all I had was terminal; I reloaded compiz but all I have is terminal, and I am not proficient enough to use this.  How do I get Unity back with the launcher panel and a tool bar?  

CB

---

### Post by mcduck on 2011-10-15
Closing or removing Compiz would definitely be a problem, Unity is a Compiz plugin and can't run without it.

Anyway, make sure Compiz is installed now, and then run "unity --reset" in a terminal. it should reset Compiz settings so that unity works again.

---

### Post by Fear091 on 2011-10-15
I wouldn't mess about with Compiz right now. There've been a lot of issues with Unity and CCSM lately, I'd just leave it alone until the bugs are fixed.

---

### Post by wildmanne39 on 2011-10-15
Hi, actually it is very easy to setup things in compiz in 11.10, and what happen was unity plugin came unchecked and all you need to do is recheck it.
Thank you

---

### Post by arashiko28 on 2011-10-15
Hi, I have the same problem, I tired to activate cube and rotate cube and "poof" unity trashed... I did managed to run unity --reset but then the terminal hangs with no end of the action and if I close it, it all goes back to the faulty setting. I already unchecked what I had done in CCSM but still have the same problem. How do I reset it and keep it that way?

---

### Post by wildmanne39 on 2011-10-15
Hi, are you using 11.10?

---

### Post by arashiko28 on 2011-10-15
Yes, I think I fixed it... sort off... I opened a second terminal and reset CCSM and then unity, after a couple of restarts, seems to be back to normal, now I don't dare to customize further than making the panels transparent, anything more and "poof" again :s

This is what I did:
> gconftool-2 --recursive-unset /apps/compiz-1
unity --reset

---

