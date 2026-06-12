---
title: "nautilus crashes while trying to empty or access root's trash"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-06-15
Hi folks, 

So I run nautilus with the following command, on occasion, when I need to do stuff as root - generally moving files from the desktop into root-accessible directories such as any of the /usr directories:

```

gksudo nautilus

```

I deleted something from the /usr/share/applications folder as root, and when trying to go into root's trash to get rid of the deletion, nautilus froze up and I had to force quit. 

Thereafter, my system became very very slow and started using up a lot of system resources - lots of RAM (I have 1 GB, which I've heard is sufficient), lots of processor (I have a dual-core P4 1.8 GHZ, which should also be sufficent), even a little bit of the swap, which never happens. There was also a ton of hard drive activity going on. 

The only way to stabilize things was to reboot. 

Mind you, these problems started happening out of the blue one day. 

How can this be resolved? 

-'Mage

---

### Post by Eisenwinter on 2008-06-15
open terminal
type su, enter root password.

cd into root's trash: cd /home/root/.Trash (usually that'll be the folder)

then type mv <filename you wish to undelete> /usr/share/applications/

Hope this will help you, I've never undeleted anything from Trash through the terminal, but I think mv should do it.

---

### Post by UnWarierMage224 on 2008-06-15
Great, it worked!
Thanks!

---

### Post by slythfox on 2008-07-29
Your solution does not work for me. I get the same crashing effect when trying to go to the trash using gksudo nautilus.

But here's the thing, a .trash (.Trash) does not exist for root or my regular user... This sucks.

Edit: ```
gksudo nautilus /root/.local/share/trash/file
```
You won't believe how long it took me to find that. Everything has been pointing to .trash/ folders.

---

