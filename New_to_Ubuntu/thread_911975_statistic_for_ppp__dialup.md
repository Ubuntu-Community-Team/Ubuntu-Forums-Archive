---
title: "statistic for ppp / dialup"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by biji on 2008-09-06
hi all, 
is there any application which shows statistic for ppp / dialup connection (logs connect time and bytes transferred)
it is similiar to kppp statistic but in gnome... thanks

---

### Post by t0p on 2008-09-06
If you run **wvdial**, when you disconnect wvdial will display how long you were connected and how much data was transferred.

wvdial is a command-line utility.  It's included in ubuntu installation.

---

### Post by biji on 2008-09-06
yes thanks.. but i mean those statistic logged to summary total connection in 1 month

---

### Post by t0p on 2008-09-06
> **biji said:**
> yes thanks.. but i mean those statistic logged to summary total connection in 1 month

No,wvdial won't do that for you.  I suppose you could write a script yourself to log that info.  But I don't know where the script would collect that data from

---

### Post by biji on 2008-09-07
hi.. found this: umtsmon
this is great apps .. but can't find ubuntu package for it

---

