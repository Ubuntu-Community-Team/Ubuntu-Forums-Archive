---
title: "Modifying my kernel"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by DyBurke on 2008-10-05
Gateway MT6723
Intel Pentium dual-core T2310(1.46GHz) 533Mhz FSB 1MB L2chache
1.5 GB of RAM
Intel GMA X3100  Integrated Shared Memory (Pulls as much as it needs I believe?)

Hey, guys.  Great forum, I'm definitely learning some things.  And plan to learn more!

Especially with this project.  I'm trying to cut my boot time down to something ridiculously low.  To do that I figure I need to figure out what modules need to run in order for my computer to operate and then compile those into the kernel, leaving all other modules out of the equation.  Also, I would like to minimize the amount of scripts/apps that start up and instead have them called upon when the desired funtionality needs them.  

Also, when I began using ubuntu I installed a ton of programs and tested out a ton of different things, just to get a good feel of the different things I could do with ubuntu.  For that reason I feel like there is a good chance there are a ton of things that my computer is littered with that don't need to be there.

So, my questions are:

Is there a nice simple command to give all the basic specs of my computer?
How do I find out what modules I NEED?
How do I find out more about the boot process my computer goes through?
What files do I use to edit the boot process?
How do I find out if there are dormant (or otherwise not used) packages on my system?
Any suggestions in terms of filesystem?  (I'm up for experimentation to get speed and efficiency.)
Any random tips or suggestions to make my system run wicked fast?

---

### Post by DyBurke on 2008-10-10
Bump?

---

### Post by jemate18 on 2008-10-10
> **DyBurke said:**
> Gateway MT6723
Intel Pentium dual-core T2310(1.46GHz) 533Mhz FSB 1MB L2chache
1.5 GB of RAM
Intel GMA X3100  Integrated Shared Memory (Pulls as much as it needs I believe?)

Hey, guys.  Great forum, I'm definitely learning some things.  And plan to learn more!

Especially with this project.  I'm trying to cut my boot time down to something ridiculously low.  To do that I figure I need to figure out what modules need to run in order for my computer to operate and then compile those into the kernel, leaving all other modules out of the equation.  Also, I would like to minimize the amount of scripts/apps that start up and instead have them called upon when the desired funtionality needs them.  

Also, when I began using ubuntu I installed a ton of programs and tested out a ton of different things, just to get a good feel of the different things I could do with ubuntu.  For that reason I feel like there is a good chance there are a ton of things that my computer is littered with that don't need to be there.

So, my questions are:

Is there a nice simple command to give all the basic specs of my computer?
How do I find out what modules I NEED?
How do I find out more about the boot process my computer goes through?
What files do I use to edit the boot process?
How do I find out if there are dormant (or otherwise not used) packages on my system?
Any suggestions in terms of filesystem?  (I'm up for experimentation to get speed and efficiency.)
Any random tips or suggestions to make my system run wicked fast?

@Is there a nice simple command to give all the basic specs of my computer?
a. type cat /proc/cpuinfo
b. This will give some details about your computer
c. type sudo fdisk -l 
d. This will give your storage details
e. type df -h
f. This will give info on your mounted filesystem
g. type dmesg
h. This will give you the messages on the boot process

---

### Post by jemate18 on 2008-10-10
you can also type 
free -m
this will display your RAM and swap usage in the command line

---

### Post by jemate18 on 2008-10-10
@How do I find out what modules I NEED
Basically, modules are compiled in the kernel and others are loaded by the kernel. All modules you need is loaded by Linux at default. Therefore, when you try to mount an ntfs drive, linux loads it for you.. Or you can do the command line thing to load it, if for some reason, linux didnt load it for you....


The question would be,,, what modules I need for my .......... and so and so........

---

