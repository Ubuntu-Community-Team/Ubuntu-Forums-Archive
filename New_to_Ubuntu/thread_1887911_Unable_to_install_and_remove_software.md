---
title: "Unable to install and remove software"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by MUK3SH on 2011-11-28
Sorry Guys It May repeated post.
I tried search But didn't find any better solution (Or the Noob don't Know how to search.)


[B]When i am installing any software from software center I am getting following error.
[/B]>  The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software. Please some one Give me an solution. 
[B][COLOR=Lime]

[COLOR=Navy]Thank You [/COLOR]
[/COLOR][/B]

---

### Post by westie457 on 2011-11-28
Hello MUK3SH

Welcome to the Forums.

Open a terminal (Ctrl+Alt+T) and run the following commands one at a time.
```
sudo dpkg --configure -a

sudo apt-get install -f

sudo apt-get update

sudo apt-get upgrade
```


Hopefully this should fix things.

If it does not post the error messages here between ```
 and 
``` tags by clicking the # button.

Thank you.

---

### Post by lalitpratap on 2011-11-28
One possible reason for this issue can be your source /etc/apt/sources.list got corrupted.
If this the case then please verify this file  and then delete it.

This will update you software repository list to default one, possible this happens when you have added some invalid software repository.

After deleting that source list, run below command, hope it will work for you.

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by MUK3SH on 2011-11-28
**Thanks A lot. God Bless You my dear friend, It worked Fine :)**

---

