---
title: "accessing windows partitions"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by grahamc1965 on 2008-04-27
I cannot access my window partitions from linux .
I use win xp , and Ubuntu 8.04 .
I just upgraded from 7.10 .
I installed ntfs-3g in 7.10 , but i kept getting access errors . Said i did not have permission . 
Xp is on its own drive as is ubuntu .
I could access xp partially before ntfs-3g .
all of my music is on the windows drive , and i would prefer not to copy it .. LOL
I am able to read and write to my ubuntu partition from windows without any problems .
I have been using linux for about 6 years , and ubuntu since 5.0

Thank you for any help you can offer .
Just started using ubuntu again . My system is dual boot ,
XP Home and Ubuntu .

:popcorn:

---

### Post by TeoBigusGeekus on 2008-04-27
Go to synaptic and install ntfs-config as well.
Then go to applications->system tools->ntfs configuration, choose your win volume and check all the buttons.

---

### Post by grahamc1965 on 2008-04-27
have already done that too :(

Still tells me i have no privileges for some reason .
It always worked before , but after i installed 7.10 it didnt , and upgrade to 8.04 didnt help .
I can see the partitions , just cant access them , which seems strange to me .

:guitar:

---

### Post by TeoBigusGeekus on 2008-04-27
Another solution would be to permanently mount your ntfs partition on boot up changing your fstab file.
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by grahamc1965 on 2008-04-27
Thanks for the link . I will try that :)

:KS

---

