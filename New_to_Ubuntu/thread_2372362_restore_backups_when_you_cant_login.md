---
title: "restore backups when you cant login?"
date: 2017-09-24
forum: New to Ubuntu
---

### Post by mordax on 2017-09-24
(I am completely new to Ubuntu) 


PC1: Radeon r9 270x - Ubuntu 14.04 + 16.04 (+Win7) - **16.04 works** and **14.04 does not reach the login** after installing "fglrx with updates" from "additional drivers"
PC2: Radeon HD 5770 Ubuntu 14.04 working

[B]In short I need two things: 
A way to test video drivers and restore my systems when they don't work and I can't login to restore deja dup backups. Till now I just reinstalled Ubuntu....
Making Open CL usable on both systems in Ubuntu[/B]


---------------------------------------

I tried to install video drivers first directly from the manufacter which I then realized was wrong then I reinstalled Ubuntu and then tried to install the driver with the additional drivers menu.
They always crashed the system and I am either stuck at the "login loop" or can't even reach the "login loop" and the Systems stuck before.

Way to fix?:
I have a live cd but starting from the cd and then specifying a backup in deja dup gives me an "access denied" error.
I have access to the Ubuntu additional things like "start in safe mode" via grub.
    when I want to start in "fail safe x mode"  it tells me that it cant find "/usr/bin/x"
On PC 1 I have access to another running Ubuntu version (16.04) can I fix (14.04) from there?



**1x) how do I restore my backups made with deja dup when I am unable to log in to my system? (login loop or stuck even before login loop)**

when I google this issue it states to
1a) open terminal with I think strg+shift+F1
->problem1a: terminal asks me TWICE for some weird login information. When I use my username and my password it says login incorrect. ->????? I only ever specified one password and I don't remember all the names I used in Installation. Using the name that stands at the login screen and the password does not work.

1b) use a command and specify the backup 
->problem1b: the backups made with deja dup contain several files - which one shall I specify (I never reached that point because of the problem above so I can't test and ask beforehand)




I want to run Open CL. As I said I have either 14.04 or 16.04 as choices. I have two different video cards on two different systems: **Radeon r9 270x and Radeon HD 5770**
As I red I need FIRST a working driver and 16.04 is not supporting the r9 270x naturally, since AMD does not support it and flgrx driver does not work for 16.04.
Questions:
2a)**In general**: the r9 270x should be working on Ubuntu 14.04 using the fglrx driver from additional drivers and then support OpenCl right? (I have to install open CL runtimes afterwards of course to make it work)
2b)Does the HD 5770 support Open CL on any Ubuntu version?



out of ideas.....

:confused:

---

### Post by kevdog on 2017-09-24
You know you can always mount the directory or disk from another installation right?

---

### Post by mordax on 2017-10-02
> **kevdog said:**
> You know you can always mount the directory or disk from another installation right?

Of course not, I am completely new to Ubuntu, googled a bit and try to adapt windows knowledge...
I know that Ubuntu mounts drives and it's partitions. What do you want me to mount and how does it help me to fix the login looop problem?

---

