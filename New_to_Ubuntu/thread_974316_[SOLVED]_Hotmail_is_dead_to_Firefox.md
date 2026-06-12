---
title: "[SOLVED] Hotmail is dead to Firefox"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-11-07
How dumb am I? Hotmail (Windows software) offered an upgrade to my web-based email account. It worked 1 day. Now, when I reply to or compose an email, I cannot type in the body of the message box. I thought maybe Java and JavaScript were not enabled, but they are (and were).

Have you encountered this?

Have you found a solution?

---

### Post by Tony Flury on 2008-11-07
3 options : 
1) Don't use hotmail 
2) Run IE6 under Wine 
3) Download the User Agent Switcher plugin for firefox - and use it to make Firefox pretend it is IE.

---

### Post by Titan8990 on 2008-11-07
I have not had any problems...

---

### Post by Tony Flury on 2008-11-07
There certainly was a problem reported in the most recent Hotmail "upgrade", but to be honest i thought they had fixed that problem.

---

### Post by DJ_Peng on 2008-11-07
I saw an article on [Linux-Watch.com]("http://www.linux-watch.com/news/NS6023147333.html") that may have some helpful info for you.

---

### Post by Mark_in_Hollywood on 2008-11-07
> **DJ_Peng said:**
> I saw an article on [Linux-Watch.com]("http://www.linux-watch.com/news/NS6023147333.html") that may have some helpful info for you.

I read the article, yet, my FF's useragent has no "iceweasel" at all. And the correct value Firefox/3.0.3 or something similar is where it belongs.

I'm screwed.

M$ sucks.

---

### Post by Yashiro on 2008-11-07
open about:config in the address bar.
change whatever values you have set to the following:
> 
general.useragent.extra.firefox               Firefox/3.0.3
general.useragent.vendor                    Firefox

---

### Post by LowSky on 2008-11-07
You do realize that you should write to their customer service and explain your issue. From the amount of thread I have been seeing, alot of people are effected.

---

### Post by Tomatosoup on 2008-11-07
Removed.

---

### Post by fizikz on 2008-11-09
> **Yashiro said:**
> open about:config in the address bar.
change whatever values you have set to the following:

Thanks! I had the same problem, and this solved it for me.

---

### Post by forumreader on 2008-11-10
This does the trick, just want to make sure that more people see the solution!

---

