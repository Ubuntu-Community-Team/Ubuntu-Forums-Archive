---
title: "Xorg is it needed?"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by LeftNut on 2008-10-13
Hi,

   I ran the sys. monitor and found that a process called xorg is take 16-50% of processing power alot of the time and is starting to bog the system down. my question is what program would this be attached to. any information would be greatly appreciated. I just want to make my system run more efficient considering it is a intel duo 1.9 ghz processor/3gb ram/gaming graphocs card.


Thanks for the help,
Gary

---

### Post by WWSmith36 on 2008-10-13
xorg is absolutely required.  It runs your all your windows and your graphics.

---

### Post by OutOfReach on 2008-10-13
Xorg is the program that makes everything that you see on your screen! So yes, it is pretty important, unless you want a command line enviroment. :)

---

### Post by ethoxyethaan on 2008-10-13
there are alternatives for Xorg but i suggest you stick with Xorg unless you want to spend several hours configuring another window manager.

---

### Post by t0p on 2008-10-13
> **ethoxyethaan said:**
> there are alternatives for Xorg but i suggest you stick with Xorg unless you want to spend several hours configuring another window manager.

Which window manager doesn't need xorg?

---

### Post by ethoxyethaan on 2008-10-13
> **t0p said:**
> Which window manager doesn't need xorg?

Xversa

---

### Post by LeftNut on 2008-10-13
yes i found this out the hard way >.< (idiot ideas).
i renamed the x11 directory to x11(2) and now i can only get into the command prompt. and when i do logged in as root:
cd /etc
rename xm11(2) xm11
i get and error about the "("

so if there is any way to reverse this i would greatly appreciate it. otherwise ill be reinstalling ubuntu for the second time ;\


Thank you,
Gary


EDIT:
i can log onto my vista partion but can't see my ubuntu file because of the ext3 thing i believe. >.>

---

### Post by omns on 2008-10-13
Do you still have a Live install CD

If so try mounting the / partition using a method like in this post
[http://ubuntuforums.org/showthread.php?t=343326](http://ubuntuforums.org/showthread.php?t=343326)

and then rename the folder from within the mounted partition

---

### Post by LeftNut on 2008-10-13
> **GrantG said:**
> Do you still have a Live install CD

If so try mounting the / partition using a method like in this post
[http://ubuntuforums.org/showthread.php?t=343326](http://ubuntuforums.org/showthread.php?t=343326)

and then rename the thread from the mounted partition

alright i got it mounted successfully but i couldn't rename the folder in file browser because of lack of permissions. and when i tried it in terminal i get an error because i renamed it with a (2) at the end and it dont read the "(".

any help would be appreciated,
Gary

---

### Post by Rolcol on 2008-10-13
> **LeftNut said:**
> alright i got it mounted successfully but i couldn't rename the folder in file browser because of lack of permissions. and when i tried it in terminal i get an error because i renamed it with a (2) at the end and it dont read the "(".

any help would be appreciated,
Gary
You will need to escape the parentheses.  ```
mv x11\(2\) x11
```

---

### Post by OutOfReach on 2008-10-13
Try starting the file manager in the LiveCD as root:
goto a terminal (Applications>Accessories>Terminal) and type in ```
gksu nautilus
```

Then navigate and rename the x11(2) folder...

---

### Post by LeftNut on 2008-10-13
> **OutOfReach said:**
> Try starting the file manager in the LiveCD as root:
goto a terminal (Applications>Accessories>Terminal) and type in ```
gksu nautilus
```

Then navigate and rename the x11(2) folder...

thank you very much.

this solved this problem now all i have to do is see why xorg is taking 20% of my cpu usage now >.<

Thank you,
Gary

---

