---
title: "application icons, where?"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by degarb on 2012-07-20
I am trying to setup wbar as an alternative.  But it requires icons for the ap.  I cannot find these. Example, I found usr/bin/chromium but no icon files yet.

---

### Post by NikTh on 2012-07-20
Hi , 
hmm.. i am not very sure , but try 
```
/usr/share/icons/
```or
```
/usr/share/app-install/icons/
```Alternatively you can use locate command
```
locate <program name>.png
```
Thanks

---

### Post by degarb on 2012-07-20
> **NikTh said:**
> Hi , 
hmm.. i am not very sure , but try 
```
/usr/share/icons/
```or
```
/usr/share/app-install/icons/
```Alternatively you can use locate command
```
locate <program name>.png
```
Thanks

Yep /usr/share/app-install/icons

I am unfamiliar with the locate command.  What is the advantage of that over the nautilus search or gnome do?  What are the limitations, allowed wildcards, and strengths?

---

### Post by NikTh on 2012-07-21
> **degarb said:**
> 

  What is the advantage of that over the nautilus search or gnome do? 

Hi , 
quicker.. much quicker. 

From terminal , do 
```
 man locate 
``` 
and 
```
man find
``` 
Thanks

---

### Post by degarb on 2012-07-22
Interestlingly, the terminal has a bug, where, when you do a man find there is no way to scroll around to read any of it.

As it is, one needs to be very clever to locate the terminal scroll bars.  Still they peak a boo up/down scrollers are unlocatable with the man command in the lxterminal.

PS.  I do think I will start using the locate, because it is lightning fast at first glance/use.

---

