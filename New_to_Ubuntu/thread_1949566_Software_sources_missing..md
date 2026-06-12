---
title: "Software sources missing."
date: 2012-03-30
forum: New to Ubuntu
---

### Post by bbemmerful on 2012-03-30
I wanted to install a game from the repos, but when I used the software manager it says package not found. I looked at my software sources and seems that there might be some missing. I was wondering how I can check to see what ones should be in there such as a list. Also cant remember are the multi and universe should be in there.

---

### Post by ptn107 on 2012-03-30
A default /etc/apt/sources.list file looks like the following.  Replace *'precise'* with the codename of your Ubuntu version.

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by bbemmerful on 2012-03-30
Thankyou for the quick response, one other question how do I open the sources.list via terminal tried 
"sudo /ect/apt/sources.list gedit" but got command not found,but gave it a shot lol.

---

### Post by Cheesemill on 2012-03-30
Or you can generate a new one here:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Cheesemill on 2012-03-30
> **bbemmerful said:**
> Thankyou for the quick response, one other question how do I open the sources.list via terminal tried 
"sudo /ect/apt/sources.list gedit" but got command not found,but gave it a shot lol.
```
 gksudo gedit /etc/apt/sources.list
```

---

### Post by bbemmerful on 2012-03-30
Ah the gedit comes first and and use gksudo thanks.

---

