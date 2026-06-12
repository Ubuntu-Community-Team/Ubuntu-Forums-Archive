---
title: "Sometimes Date and Time doesn't show up"
date: 2013-11-02
forum: New to Ubuntu
---

### Post by jdwaugh on 2013-11-02
I upgraded to 13.10 and noticed sometime the date and times doesn't show up in the indicator bar.  Sometimes the machine boots and it is there and sometimes it is not.  Is there anyway of resolving this?  I did a google search and couldn't find any resoultion.  Everythign talks about installing the date and time indicator, which is already installed.  Is this just a bug that will be resolved with an update in the future?

---

### Post by deadflowr on 2013-11-02
Don't know if it'll be resolved, but there is a bug report on it( or at least one bug report on it)
[https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1228360](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1228360)

You can mark it as affecting you as well.

It seems a lot of users are having this problem.

---

### Post by jdwaugh on 2013-11-03
WEll at least then I know it isn't something wrong with my machine specifically.

---

### Post by craig10x on 2013-11-03
I guess a lot of us are getting it...i get that too, on occasion...when i do, i log out and then log back in and then it goes back to normal...

---

### Post by syam-nair on 2013-11-03
use dconf editor to set the values. You may find it under com > canonical > indicator > datetime.  Reboot and check again, if it still persists report bug.
to open dconf editor type "dconf-editor" in the terminal

---

### Post by mc4man on 2013-11-03
see here, if inclined try the -proposed indicator-datetime  package (and -proposed indicator-session package
[https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1239710](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1239710)

---

