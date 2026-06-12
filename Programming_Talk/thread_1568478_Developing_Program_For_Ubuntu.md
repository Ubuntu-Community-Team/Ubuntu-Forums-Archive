---
title: "Developing Program For Ubuntu"
date: 2010-09-05
forum: Programming Talk
---

### Post by extraordinary_boy08 on 2010-09-05
Hi everyone!

I am a hobbyist on high-level programming languages such as C++ and Java and I'm just new to Ubuntu.  I'm currently working on a different project involving some interaction with the operating system (which is Ubuntu). It is about a program that could monitor and control USB Flash Drive Access on a Network. Currently, I'm on the initial step of planning the program. My initial plan is that I'm going to use Java as the language and GTK + for my GUI.

My question is how am I going to use the OS-side 'USB-detecting' feature of ubuntu to be used for my program.

Can you also give me some links to some tutorials about using or invoking Ubuntu features (commands such as turning off, locking, refreshing a computer) to be used into another working program.

Thanks and more power!

---

### Post by dv3500ea on 2010-09-05
Have a look here: [http://www.advancedlinuxprogramming.com/]("http://www.advancedlinuxprogramming.com/")

This seems to have the documentation specific to the low level interactions with Linux that are necessary for USB programming. I would learn this stuff (which will have a steep learning curve) before you even think of making a GUI.

---

### Post by extraordinary_boy08 on 2010-09-05
> **dv3500ea said:**
> Have a look here: [http://www.advancedlinuxprogramming.com/](http://www.advancedlinuxprogramming.com/)

This seems to have the documentation specific to the low level interactions with Linux that are necessary for USB programming. I would learn this stuff (which will have a steep learning curve) before you even think of making a GUI.

Thanks for the help. I just would like to ask an opinion if I'm my plans are possible to use Java for the purpose of the program. I just wanna make sure if I will be on the right track since this is my first time to work on a project outside the comfort zones of my knowledge. Thanks!

---

### Post by dv3500ea on 2010-09-05
You are probably better off using c/c++ for this sort of programming because these languages can access low level operating system functionality.

---

### Post by SaintDanBert on 2010-09-05
From your description, I'm not clear about what you are trying to do.
When you connect an external USB device, **udev rules** manage the machinations required to detect the device, load and configure drivers (typically kernel modules), and make things ready for end-user access. For example, when I connect a flash drive, udev rules dance for a while, uses the [i]dosfslabel[/b] and mounts the drive at /media/{labelString}. Configuration determines whether this mount point is available system-wide or only for the running user. Once mounted, any application can read-write the files like any other disk. Udev rules will let you detect one specific device from a dazzle* of devices and do special things for that one only.

Take a look at [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221).  There you will find details about running your own scripts or programs as part of udev processing. You might adapt some existing rule, or create your own, such that your USB goes through standard things and then your script or program runs to process whatever is specific to your application.  

Bonne chance,
~~~ 0;-Dan

* "dazzle" -- a collective noun traditionally used to describe a large group of zebra. [http://en.wikipedia.org/wiki/Lists_of_collective_nouns](http://en.wikipedia.org/wiki/Lists_of_collective_nouns)

---

### Post by extraordinary_boy08 on 2010-09-05
> **dv3500ea said:**
> You are probably better off using c/c++ for this sort of programming because these languages can access low level operating system functionality.

Okay thanks! Then, is Java not capable of accessing low level operating system functionality?

---

### Post by extraordinary_boy08 on 2010-09-05
> **SaintDanBert said:**
> From your description, I'm not clear about what you are trying to do.
When you connect an external USB device, **udev rules** manage the machinations required to detect the device, load and configure drivers (typically kernel modules), and make things ready for end-user access. For example, when I connect a flash drive, udev rules dance for a while, uses the [i]dosfslabel[/b] and mounts the drive at /media/{labelString}. Configuration determines whether this mount point is available system-wide or only for the running user. Once mounted, any application can read-write the files like any other disk. Udev rules will let you detect one specific device from a dazzle* of devices and do special things for that one only.

Take a look at [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221).  There you will find details about running your own scripts or programs as part of udev processing. You might adapt some existing rule, or create your own, such that your USB goes through standard things and then your script or program runs to process whatever is specific to your application.  

Bonne chance,
~~~ 0;-Dan

* "dazzle" -- a collective noun traditionally used to describe a large group of zebra. [http://en.wikipedia.org/wiki/Lists_of_collective_nouns](http://en.wikipedia.org/wiki/Lists_of_collective_nouns)

What I'm trying to do is to create a program that can monitor and grant access to the usage of USB flash drive in a computer. 

The creator can block USB flash drive devices everytime it is inserted to the port (except for other USB devices such as printers and scanners). Once a flash drive  is detected, the computer will be locked and prompting a message to remove the flash drive  to unlock the computer. The administrator can turn this mechanism on or off. Plus all usb related activities will be recorded in a file. And, the program is installed on 3-5 computers and 1 computer acts as a administrator. 

Thanks for the response! Can you give some other advice?

---

### Post by SaintDanBert on 2010-09-06
> **extraordinary_boy08 said:**
> What I'm trying to do is to create a program that can monitor and grant access to the usage of USB flash drive in a computer. 
...


This is a perfect job for **udev rule**(s)!!

[list]
[*]connect drive
[*]rule runs --> script runs
[*]script mounts the drive with a "magic" group ownership
[*}script sets drive permissions, too
[*]there are access control lists (ACLs) if you need fine control
[/list]


Now, only users who are members of the group have access.
Once you have this working as a script, you could make C or C++
or whatever.

~~~ 0;-Dan

---

