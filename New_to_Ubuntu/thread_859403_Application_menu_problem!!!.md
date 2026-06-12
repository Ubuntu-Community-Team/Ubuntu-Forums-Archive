---
title: "Application menu problem!!!"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by jrp1349 on 2008-07-14
Hi Im a new user here and well here goes for my first problem/question/help.

Well i managed to get ubuntu installed, with the help of a friend last week, and have done a partition on my hard drive, thereby i can spend some time getting used to using ubuntu and its features.
I started checking it out properly midweek and when installing ubuntu studio using sympatic manager, halfway through the downloading, it stopped. And that when the problems began. First of all we manged to figure out the problem with the ubuntu studio not downloading, turns out i needed some space as i was only using 6-7gb of hard drive space. 
Though im still stuck with the problem of my applicaitons menu not opening. Every time i try and open it and when i go and double click on it, it doesnt do anything, rather it just highlights the applications toolbar bit in blue and does nothing else. Is there a way to get rid of this or a soloution to this problem? Any help or advice would be greatly appreciated. Trust me i'm an absoloute beginner on this?

---

### Post by phoenix_abhi on 2008-07-14
Welcome to the Ubuntu forums
till the time ur not getting a proper answer use alt+F2 and select list of applications from the pop down menu or type the name of apps. Will come back with a solution after a research. do not worry, 1000 of people are here to help u

---

### Post by Het Irv on 2008-07-14
If you can, the best thing to do right now would be to reformat your drive so that the partition you are using for Ubuntu has more space, and then do a reinstall.  10 to 15 ought to be good for just a trial run.

If that is not possible, try using the LiveCD to enlarge the Partition (System-Administration-Partition Editor).  Then boot back into Ubuntu and try to redo the upgrade that failed.

---

### Post by decoherence on 2008-07-14
> **jrp1349 said:**
> 
Though im still stuck with the problem of my applicaitons menu not opening. Every time i try and open it and when i go and double click on it, it doesnt do anything, rather it just highlights the applications toolbar bit in blue and does nothing else.

When I double-click on the Applications menu, it opens and closes quickly. Try just clicking once. Could be your computer isn't fast enough for you to see it open and close again. Menus, as a general rule, are single-click things.

---

### Post by kansasnoob on 2008-07-14
Have you increased the size of your partition already?

---

### Post by jrp1349 on 2008-07-14
> **kansasnoob said:**
> Have you increased the size of your partition already?


No but my friend who helped me install it, has suggested that that might be a good method to solve, it plus would free more space up to install applications. Hes provided me with a guide on how to do it. Thanks for the response guys, been veyr helpful.

---

### Post by kansasnoob on 2008-07-14
> **jrp1349 said:**
> No but my friend who helped me install it, has suggested that that might be a good method to solve, it plus would free more space up to install applications. Hes provided me with a guide on how to do it. Thanks for the response guys, been veyr helpful.

OK, was this helpful?

> When I double-click on the Applications menu, it opens and closes quickly. Try just clicking once. Could be your computer isn't fast enough for you to see it open and close again. Menus, as a general rule, are single-click things.

Can you now open Applications, etc?

What I was going to suggest first was a simple:

```
sudo apt-get autoclean
```

or (more extreme, will even remove old .deb files):

```
sudo apt-get clean
```

but if you can't get to terminal you can't.

---

### Post by bumanie on 2008-07-14
Try doing what your friend said ie increase the partition size. Once done if the menu's are still playing up > sudo apt-get install ubuntu-desktopBy the way it is usual for full filesystems to do odd things to programs.

---

### Post by phoenix_abhi on 2008-07-14
Dop not forget make the thread solved

---

