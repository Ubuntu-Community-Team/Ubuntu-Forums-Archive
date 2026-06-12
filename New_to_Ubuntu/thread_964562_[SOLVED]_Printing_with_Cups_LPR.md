---
title: "[SOLVED] Printing with Cups LPR"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Devastator9 on 2008-10-31
Just installed 8.10 and only one thing left to get working. 
My printer is on the network and needs to be LPR. I cant seem to find out how to install it with the new cups system.
Everything else has been great on 8.10

Dev

---

### Post by Peter09 on 2008-10-31
Have you CUPS installed. If so going to firefox and putting in the address should give you the CUPS system

```
:http://localhost:631
```

---

### Post by LookTJ on 2008-10-31
> **Peter09 said:**
> ```
http://localhost:631
```
Basically just the above quote, add printer and follow what it tells you and you should be good to go.

---

### Post by Devastator9 on 2008-10-31
Thanks you 2. After some playing around with where you sent me I
 got it to work.
For those who have the problem with LPR printing I did this to get it to work, under APPSOCKET I set the url as LPD://ip-address of printer/the printer name as listed by my D-link.
I use a D-Link DP-300 ethernet print server for my printing here.
Hope this helps.

---

### Post by meindian523 on 2008-10-31
For good citizenship of the forums.A good title and the end post describing how the problem was solved.Very Good.

---

### Post by bailey86 on 2008-11-19
Just to possibly help with further details.

I added a LaserJet 4050 which was plugged into a D-Link DP-300+ to my Hardy Heron Ubuntu Dell laptop.

Select from the menu:

System - Administration - Printing

New Printer - AppSocket/HP JetDirect

For the host put in the IP address only.  Then select the printer from the list and it should be fine from there.

Cheers,

Kevin

---

### Post by Devastator9 on 2009-01-29
> **Taylor said:**
> Basically just the above quote, add printer and follow what it tells you and you should be good to go.

I just did from the quote and added print from there.

---

