---
title: "[SOLVED] multiple versions of gcc"
date: 2008-11-24
forum: Programming Talk
---

### Post by monkeyking on 2008-11-24
Is it possible to have multiple version of gcc installed on the same ubuntu installation.

And if so, how do I choose which to use.


thanks in advance

---

### Post by kjohansen on 2008-11-24
[http://www.linuxquestions.org/questions/slackware-14/multiple-versions-of-gcc-599326/](http://www.linuxquestions.org/questions/slackware-14/multiple-versions-of-gcc-599326/)

---

### Post by monkeyking on 2008-11-24
This is exactly as complicated as I thought it would be.

I remember a java utility,
that made it possible to change version,
with the click of a button.

This would be nice

---

### Post by joseangelini on 2008-11-24
perhaps you can use update-alternatives command. Look at this [http://http://ubuntuforums.org/archive/index.php/t-80145.html]("http://http://ubuntuforums.org/archive/index.php/t-80145.html")

Good luck

---

### Post by joseangelini on 2008-11-24
perhaps you can use update-alternatives command. Look at this [http://ubuntuforums.org/archive/index.php/t-80145.html](http://ubuntuforums.org/archive/index.php/t-80145.html) 

Good luck

---

### Post by wmcbrine on 2008-11-25
It's not complicated, if you're using the multiple versions available from the Ubuntu repositories... all you have to do is invoke the non-default versions like so:

gcc-3.4

instead of just:

gcc

In a makefile, you should be able to achieve the same result by putting a line like "CC = gcc-3.4" at the top.

---

### Post by monkeyking on 2008-11-25
> **wmcbrine said:**
> 
gcc-3.4

Do you know,
if this approch will use the proper "old" includes?

---

### Post by dribeas on 2008-11-25
> **monkeyking said:**
> Do you know,
if this approch will use the proper "old" includes?

I currently use g++ 3.4, 4.2 and 4.3 for development. Header files are not compatible and it works just fine.

---

### Post by monkeyking on 2008-11-25
Thanks.

---

