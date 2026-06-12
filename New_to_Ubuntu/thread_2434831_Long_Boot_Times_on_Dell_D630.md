---
title: "Long Boot Times on Dell D630"
date: 2020-01-11
forum: New to Ubuntu
---

### Post by eg-bnb on 2020-01-11
I am running 18-LTS on a Dell Latitude D630 with 16 GB ram & a (leftover) SSD.  
My boot times are exceedingly long... It takes **forever** to get to the log-in screen and, then, 4X as long from log-in screen to desktop.

Anything I can do to improve boot times, especially post login?

TIA.

---

### Post by Autodave on 2020-01-11
How long is "long"?

---

### Post by crip720 on 2020-01-11
In terminal,  system-analyze and system-analyze-blame should show what is slowing things up.

---

### Post by GhX6GZMB on 2020-01-11
Your D630 has the Intel 965GM chipset, which brings problems. (I still wonder why this hasn't been fixed over the last 10 years).
See this post #223, especially the paragraph "Getting rid of the errors":
[https://ubuntuforums.org/showthread.php?t=2130640&page=23](https://ubuntuforums.org/showthread.php?t=2130640&page=23)

This should take care of the issue. Good luck :)  And Welcome, BTW.

---

