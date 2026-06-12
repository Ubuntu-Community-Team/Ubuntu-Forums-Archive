---
title: "changing swappines permanent"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Troca on 2008-06-19
Hi i read a guide on speeding up ubuntu abit 

its basicly to make ubuntu use the ram more and the swap partion less if i got it correct any way i followd the guide everything worked good and i think i notice a difrens tbh. anyway my problem is when iam trying to change it permanent so when ubuntu boots its allready set this is what the guide says 


(my problem is when i open sudo gedit /etc/sysctl.conf
i cant fint the line vm.swappiness=60 well no line with swappiness in it at all.) 




THE GUIDE 


Tip No. 1: Use that memory!
In an excellent three-part article, Tom Adelstein observes that for the longest time, Linux was used as a workstation or server rather than as a desktop operating system. Thus, the default settings that come with most distributions are not optimized for desktop PC systems.

One bottleneck, Adelstein says, is the tendency of Linux to use a swap file on the hard disk instead of RAM. Since the hard disk is 100 times slower than internal memory, this can slow things down considerably.

The tendency of Linux to go to the swap file is controlled by a variable called “swappiness” and the higher the number, the greater the tendency to go to the disk. To find out what the swappiness is on your machine, type the following in a terminal window (if you want to make sure you don’t make any typing errors, you can copy the line and paste it into the terminal window with Ctrl-Shift-V) :

sudo cat /proc/sys/vm/swappiness

Type your password and wait for the terminal program to come back with a number. If you have the default Ubuntu setting, it will say “60.” We want to lower that to 10 by typing this in the terminal window:

sudo sysctl -w vm.swappiness=10

To make sure the system always uses a swappiness of 10 on every boot, we’ll need to edit the sysctl.conf file in the etc directory. To do this, type:

sudo gedit /etc/sysctl.conf

This will call up a text editor with the configuration file. Find the line that says “vm.swappiness=60” and change the 60 to 10, taking care to change nothing else in the file. Save the file and you’re done.

---

### Post by sdennie on 2008-06-19
The default swappiness is 60 so, there probably isn't an entry in /etc/sysctl.conf because it's redundant.  You can simply add:

```

vm.swappiness = 0

```

(Or whatever you want to set the swappiness to)

---

### Post by fatality_uk on 2008-06-19
Yes you have to add
> vm.swappiness = 0
to the end of sysctl.conf

I know this from Ubuntu installs on the eeePC :D

---

### Post by Troca on 2008-06-19
thanks for your help guys

---

