---
title: "[SOLVED] Accessing files that were on my XP OS in Ubuntu"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Troy Hopkins on 2008-08-13
Yesterday I installed Ubuntu onto my hard drive. I now have one hard drive with both Ubuntu and XP on it (dual boot). 

Is there a way that I can access my files (such as music) that were on the XP operating system in Ubuntu. I would like to transfer the files from XP but since they are on the same hard drive, I do not know how to do this.

Any info helps. Thanks.

---

### Post by nicedude on 2008-08-13
You just need to mount the XP drive so that you can access it. The easiest way for me to tell you how to do this using a nice easy GUI is to install a program called pysdm. it is available from the Ubuntu repositories so to download it run theh following in a terminal ( to open a terminal Applications -> Accessories -> Terminal ) just paste the following in the terminal and hit enter

sudo apt-get install pysdm

and then to run it type

sudo pysdm


This will open the GUI and you can select to mount partitions and it will do it for you.

hope this helps

---

### Post by Troy Hopkins on 2008-08-13
When I enter "sudo apt-get install pysdm" in terminal, I get the following:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
troy@troy-laptop:~$ 

What does this mean?

---

### Post by halitech on 2008-08-13
do you have Synaptic open as well as trying to run the command in the terminal?

---

### Post by Troy Hopkins on 2008-08-13
I got it!! Thank you for your help. As you can tell, I'm new to this but I am glad to be trying Ubuntu out. So far, I like it.

---

### Post by halitech on 2008-08-13
was Synaptic open as well?

if you have it solved, remember to mark the thread solved so we know its fixed :)

---

