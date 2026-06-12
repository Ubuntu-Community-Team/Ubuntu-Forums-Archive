---
title: "Permission denied?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Maximusmaximus on 2008-11-09
evening all,
i am having serious problems with permission in the terminal, nearly any command i do/attempt i get a "permission denied" statement from the terminal, i am an administrator and have tried using sudo commands but nothing seems to work. i recently tried to change from hardy heron to compiz fusion and it would not let me, and i am currently trying to modify alsa sound driver and nothing is working. is there anyway i can get permissions changed?

---

### Post by hyper_ch on 2008-11-09
posting an example of what would help and not just make us merely guess what you do.

---

### Post by Maximusmaximus on 2008-11-09
> **hyper_ch said:**
> posting an example of what would help and not just make us merely guess what you do.

root@kev-desktop:/home/max# /proc/asound/version
bash: /proc/asound/version: Permission denied

is one example, and alot of other times i try to load/modify files i get that, i was trying to check the version of my sound drivers

---

### Post by hyper_ch on 2008-11-09
(1) you should not login as root
(2) your command issues tries to run that file hence it needs to be executable but that's not what you want

---

### Post by Maximusmaximus on 2008-11-09
> **hyper_ch said:**
> (1) you should not login as root
(2) your command issues tries to run that file hence it needs to be executable but that's not what you want

 max@kev-desktop:~$  /proc/asound/version
bash: /proc/asound/version: Permission denied

[http://alsa.opensrc.org/index.php/TroubleShooting#Check_the_ALSA_driver_version](http://alsa.opensrc.org/index.php/TroubleShooting#Check_the_ALSA_driver_version)

??? i have tryed alot of things on that help page but i still get denied

---

### Post by hyper_ch on 2008-11-09
yet you still try to execute that file

---

### Post by Maximusmaximus on 2008-11-09
if you went to the link thats what it tells me to do

---

### Post by hyper_ch on 2008-11-09
no, it says you should have a look at that file not that you shall run it.

---

### Post by Maximusmaximus on 2008-11-09
that was a stupid mistake
#-o

---

### Post by hyper_ch on 2008-11-09
so you figured it out?

---

### Post by 3rdalbum on 2008-11-09
Maximusmaximus, when you just put in the path of a file into the terminal, it's telling Linux that you want to execute the file. This file isn't executable, so it's telling you "permission denied".

To look at the file, you need this command:

```
cat /proc/asound/version
```

So, you put "cat" and then the file name.

To look at a long file, you use "less" instead of "cat", and then you can scroll up and down.

If you want to edit a file, you use "nano" instead; and if it's a system file, you must put "sudo" before "nano" in order to have the permissions to edit it:

```
sudo nano /etc/X11/xorg.conf
```

I'd recommend looking at a Linux command-line tutorial so you know what you're doing within the terminal.

---

### Post by Maximusmaximus on 2008-11-09
yeah i did and i also found how to give proper permission to normal users so i managed to easially install compiz fusion thanks for the help i just need to war away with alsa now

---

### Post by hyper_ch on 2008-11-09
good luck with the rest of it

---

