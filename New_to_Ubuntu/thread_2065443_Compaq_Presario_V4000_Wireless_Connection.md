---
title: "Compaq Presario V4000 Wireless Connection"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by Wheeladrew on 2012-10-01
Hello, my Compaq Presario V4000 will not connect to the Internet on Ubuntu. I know that it is a firmware problem and not a hardware one, as it works fine on my second, smaller partition of Windows XP. I've looked through a figurative TON of other threads on the issue, and none have fixed my problem. 
When I click on the connection icon at the top-right of my interface (I am using Ubuntu 12.04 stock-standard, vanilla Unity), it says that the wireless connection has been disabled via a hardware switch. . .which simply isn't true. I'm positive that this is a driver/firmware issue, I just don't know how to fix it.
Any help would be greatly appreciated. 

Long story short:
Compaq Presario V4000
Ubuntu 12.04, Unity
Bad Wireless Driver

---

### Post by critin on 2012-10-02
Boot the machine with the live os, the cd/flash that you installed with and see if the internet connects with it that way.   Choose TRY when it boots.  Check sound and whatever else you can.  Also, take a look at Additional Drivers which is in System settings.  See if it has recommendations.   (Cog on top right corner of screen, next to user name.)

---

### Post by Wheeladrew on 2012-10-02
I've tried that. Everything works but the wireless, which, despite having the computer connected via ethernet during the Additional Driver check, comes up with nothing.

---

### Post by Hadaka on 2012-10-02
Hi, please post the output of..

```
lspci -nnk | grep 0280 
```

thanks.

---

### Post by Wheeladrew on 2012-10-04
> lspci -nnk | grep 0280
outputs
> 06:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)

---

### Post by Wheeladrew on 2012-10-05
I got it sorted. 
rfkill list all
and then unblocked the one that was softblocked
rfkill unblock 0

---

