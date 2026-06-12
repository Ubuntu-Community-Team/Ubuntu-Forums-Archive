---
title: "Administrator (not)"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by izar21093 on 2008-11-23
Ubuntu 8.04. Yesterday all was well with regard to e-mail, internet and administrator privileges.
Today, I can get and send e-mail but can not connect to the internet wired or wireless. 
Error message: SIOCGIFFLAGSerror:no such device.
PCMCIA cards are not recognized, USB devices are not found.
Second message:You are not allowed access to the System Configuration.

I am locked out. Is there a fix for these issues?

Bill G

---

### Post by jimmy the saint on 2008-11-23
How do you sendand receive email with no internet connection?

---

### Post by diablo75 on 2008-11-23
You might check this thread out for your wireless network issues, though it is based upon an older version of Ubuntu so might not work for you.

[http://ubuntuforums.org/showthread.php?t=11891](http://ubuntuforums.org/showthread.php?t=11891)

---

### Post by rhcm123 on 2008-11-23
> **izar21093 said:**
> Ubuntu 8.04. Yesterday all was well with regard to e-mail, internet and administrator privileges.
Today, I can get and send e-mail but can not connect to the internet wired or wireless. 
Error message: SIOCGIFFLAGSerror:no such device.
PCMCIA cards are not recognized, USB devices are not found.
Second message:You are not allowed access to the System Configuration.

I am locked out. Is there a fix for these issues?

Bill G

try the following command:
```
sudo /etc/init.d/networking force-reload
```
if that works, then it's a priviliges problem. if not, then it's a configuration problem

---

### Post by izar21093 on 2008-11-23
> **jimmy the saint said:**
> How do you sendand receive email with no internet connection?

I do not know. I have sent and received e-mail both wireless and wired with Evolution but can not log on to Firefox and the wireless adapter lights show no connection.

---

### Post by izar21093 on 2008-11-23
> **rhcm123 said:**
> try the following command:
```
sudo /etc/init.d/networking force-reload
```
if that works, then it's a priviliges problem. if not, then it's a configuration problem

Where and how do I try thr sudo line? I;m new to Ubuntu.

---

### Post by jimmy the saint on 2008-11-23
Ignore the connection light as many drivers do not interact well with the machines leds... I have a thinkpad and for two years it does soemthing new with each version of Ububtu.  If you can send and recieve email, you are connected.  It sounds like maybe a firefox issue.  try this:

open a terminal appications>accessories>Terminal  and type in 
```
ping www.google.com
```
and see what it says.  Just close the terminal after a few responses.  lets us know what it says

Oh yeah, are you using a proxy by chance?

---

### Post by izar21093 on 2008-11-24
Not using a proxy.

bg

> **jimmy the saint said:**
> Ignore the connection light as many drivers do not interact well with the machines leds... I have a thinkpad and for two years it does soemthing new with each version of Ububtu.  If you can send and recieve email, you are connected.  It sounds like maybe a firefox issue.  try this:

open a terminal appications>accessories>Terminal  and type in 
```
ping www.google.com
```
and see what it says.  Just close the terminal after a few responses.  lets us know what it says

Oh yeah, are you using a proxy by chance?

---

### Post by CandyKiller on 2008-11-25
> **izar21093 said:**
> 
Bill G


This is totally off topic but could this be...Bill Gates? o.0!

---

