---
title: "Minimum space per user, or Max number of users per install"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by crjackson on 2008-08-15
I've installed 8.04 on a small HD (12GB HD).  I then created a user id and pw for 3 of my kids and my wife.

All the kids have been able to login and use there accounts, but when my wife tried to login the peach colored screen (just before the desktop) turned white.  The login music plays but it stops there and never loads the desktop.

I logged in and deleted her user/group, then tried to recreate.  I got the same thing again.  I created a test user and still the same result.

There is 6.5 GB left on this drive.  I'm wondering if there is a minimum amount of space required or a maximum number of users allowed.

If I hit the ctrl+bkspc the desktop background of HER login will flash and then drop back to a login screen.

Any ideas?

---

### Post by cariboo on 2008-08-15
Remember 5% of the drive space is reserved for the root user, this will come in to play if you don't have a separate /home partition.

Jim

---

### Post by crjackson on 2008-08-15
> **cariboo907 said:**
> Remember 5% of the drive space is reserved for the root user, this will come in to play if you don't have a separate /home partition.

Jim

The thing says it has 6.5 GB free.  Do you think that is the issue.

---

### Post by appi2012 on 2008-08-15
Do you have compiz running? Sometimes if compiz is running, and multiple users are logged in, it does the white screen thing. The white screen in just a display problem. you can blindly type your username and password in the box as you normally would, and it will login.

---

### Post by crjackson on 2008-08-15
> **appi2012 said:**
> Do you have compiz running? Sometimes if compiz is running, and multiple users are logged in, it does the white screen thing. The white screen in just a display problem. you can blindly type your username and password in the box as you normally would, and it will login.
no compiz - it just happens when trying to login as the last user added (5th user).

---

