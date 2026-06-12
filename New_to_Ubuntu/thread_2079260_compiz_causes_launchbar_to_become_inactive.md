---
title: "compiz causes launchbar to become inactive"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by Alan Bradley on 2012-11-01
Just recently installed Linux for the first time and am making my first post.

I installed compiz and everything seems to work fine except that whenever I make a change to the effects in the compizconfig the launchbar stops working if I have it set on auto-hide. I then have to log out and log back in and then everything works fine, the launchbar and the effects. Its really just a minor thing but Im wondering if i have something set up incorrectly or am missing something. Also not all the effects are there, the burning windows is missing along with a few others. Im running Ubuntu 12.10

---

### Post by daslinkard on 2012-11-09
> **Alan Bradley said:**
> Just recently installed Linux for the first time and am making my first post.

I installed compiz and everything seems to work fine except that whenever I make a change to the effects in the compizconfig the launchbar stops working if I have it set on auto-hide. I then have to log out and log back in and then everything works fine, the launchbar and the effects. Its really just a minor thing but Im wondering if i have something set up incorrectly or am missing something. Also not all the effects are there, the burning windows is missing along with a few others. Im running Ubuntu 12.10

First off....welcome to the forums!  I would suggest trying the following sudo command```
gconftool-2 --recursive-unset /apps/compiz

```Restart your machine and see if this resolves your issue.  This will reset your compiz settings to default.

---

