---
title: "Freeing up RAM?"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by oneis on 2011-10-20
Hello, My name is Oneis and I am learning Ubuntu....

I have installed it on three of my computers.

One of the computers is a thinkpad with windows Vista....it has had severe RAM issues (15/16) of the RAM is currently used by the OS....now I know that Ubuntu is extremely efficient in the methods it uses RAM but I am wondering if there is a way to free up this RAM using the Ubuntu OS.....

I am considering getting rid of Windows all together, could this possubly be the answer to my problems?

Ubuntu has been running well since the install, but I am concerned about only having 100mb of free RAM.....

Does anyone else see this as a problem? Maybe someone could direct me to a link/guide?

Thank you for the support and I look forward to learning and becoming an active member of this community.

:p

---

### Post by wolfen69 on 2011-10-20
> **oneis said:**
> 

I am considering getting rid of Windows all together, could this possubly be the answer to my problems?



That has nothing to do with memory usage. How much ram do you have?

---

### Post by docbop on 2011-10-20
How are you determining Windows is using 15/16 of your RAM.  Is that with app's running or what, and what types of app's.  Windows app's especially .Net are notorious for leaking memory does a reboot free memory, how long does it take to fill again.

Ram is managed by the OS application request RAM from the OS.  Linux is more efficient in how it uses RAM, but if you don't have a lot of RAM and run lot of apps are one time then you're always going to have problems.

Also Window does some funky stuff in how it manages virtual memory.  How full is your hard drive?  Do you have the window default of a floating size swap that can create problems.   

Resolving issues like this take a lot of testing and experimenting to resolve.

---

### Post by oldos2er on 2011-10-21
> **oneis said:**
> Ubuntu has been running well since the install, but I am concerned about only having 100mb of free RAM.....

Does anyone else see this as a problem? Maybe someone could direct me to a link/guide?


[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Urbanmoth on 2011-10-21
> **oneis said:**
> 
Ubuntu has been running well since the install, but I am concerned about only having 100mb of free RAM.....

Er, you don't mean RAM as in Memory do you? You mean disk space I think.... If my guess is right and especaially since the other OS is Vista, my advice - backup your data from Vista. Format the drive and install a nice new version of Ubuntu :D

:idea: Don't do this if you still need Windows stuff however

---

### Post by llamabr on 2011-10-21
why do you think you're low on RAM?  Probably you are not, and possibly you're confusing RAM with disk space.  We can help you solve either problem, but we're not sure which one you have at this point.

---

### Post by bodhi.zazen on 2011-10-21
> **oldos2er said:**
> [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

This ^^

---

### Post by ubupirate on 2011-10-21
> **oldos2er said:**
> [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

And for reference, Windows also performs RAM caching.

---

### Post by d4m1r on 2011-10-21
> **oldos2er said:**
> [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)


lol nice...But I think there is an error on that site. It says you can't disable it but I told Ubuntu to NOT use a swap file and here I am ;)

damir@Damir-Ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          8065       2318       5747          0        686        837
-/+ buffers/cache:        794       7270
Swap:            0          0          0

---

### Post by dFlyer on 2011-10-21
Please post the results of the following command:

free -tom

This will tell us how much ram and swap your using. Linus handles memory much better than windows.

---

### Post by oldos2er on 2011-10-22
> **d4m1r said:**
> lol nice...But I think there is an error on that site. It says you can't disable it but I told Ubuntu to NOT use a swap file and here I am 

Swap isn't disk caching; they're two different things.

---

