---
title: "Software Center - Impossible to download?"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by Kanahau on 2013-01-10
Hi guys,
              I am trying to install apps (skype, wine applications, qgis, even suduko) through the software center but i keep getting this boxed message:

**"Requires installation of untrusted packages**
the action would require the installation  of packages from unauthenticated sources"

options in box are:
details, ok, repair

**details - **tell me i.e. libqtwebkit4 (this was for skype install) 
**repair -** just makes the box disappear for a while, two arrows spin in the top bar next to the word progress ( 1 then 2 ) and it says installing......  then it comes back again with the same message
**ok -** just stops the install and leaves the message "please install skype via your normal software channels. Only install this file if you trust its origin

must admit to finding this mildly frustrating as i have tried with all sorts of apps ? its the same for all  ??????? :confused:

---

### Post by uzumakifahim on 2013-01-10
It seems your problem is related to "Software sources". Check software sources to understand everything is alright. After opening Ubuntu Software Center click Edit > Software Sources. Software sources window will appear. Select all the check boxes in the "Downloadable from the Internet". Then click on the next tab "Other Software" also select all the check boxes here.

After these procedures, try again to install the softwares you want and post the result here.

Wishing best luck.

---

### Post by ibjsb4 on 2013-01-10
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And please post the results using code tags.

[ATTACH]229838[/ATTACH]

---

### Post by Kanahau on 2013-01-10
uzumakifahim - thanks did as you instructed and all seems fine so far, thanks

ibjsb4 - now its working should i still enter 
sudo apt - get update ?

Thanks for your help

---

### Post by mevets on 2013-01-10
> **Kanahau said:**
> 
sudo apt - get update ?

That command just updates the listings on your system pertaining to the latest software. It won't hurt if you do it, but I suspect others wanted you to do it simply because it sometimes can output information that would help solve the problem you were having.

---

