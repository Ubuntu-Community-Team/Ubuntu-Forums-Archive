---
title: "Updated nvidia drivers, now gnome/x server wont start."
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Chookah on 2008-10-18
Well I had to do it didn't I.  "I'm getting pretty good at linux, i'll follow the instructions on the nvidia site and update to the latest drivers"


Now when I boot I get taken to a text prompt to log in.

I did some searching, found the xorg.conf and replaced it with a xorg.conf.backup file I found in the same directory, that didnt fix the problem.

When I type *startx* I get the following...

[I]Fatal server error:
Caught signal 11.  Server aborting


waiting for X server to begin accepting connections
giving up.
xinit: Connction reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.[/I]


I tried */etc/init.d/gdm start* and get permission denied.
I tried *sudo /etc/init.d/gdm start* and it says Starting GNOME display manager [ok]

Did I really stuff it up as bad as I think I did?

---

### Post by medic2000 on 2008-10-18
It has broken my X too. There is a bug in new drivers?

---

### Post by phidia on 2008-10-18
From the command line try > sudo dpkg-reconfigure -phigh xserver-xorg

That should create a new xorg for you, and back up your present one.

---

### Post by phidia on 2008-10-18
Are you both using Hardy? The safest way to install the nvidia driver is through apt or synaptic if you have a desktop > sudo apt-get install nvidia-glx-177

---

### Post by Chookah on 2008-10-18
Thanks for jumping in on this thread!
Yes, using Hardy (god bless its soul)

> **phidia said:**
> From the command line try 

That should create a new xorg for you, and back up your present one.
Just tried that, the output it gave me was the same as when I pressed esc during the grubloader to go to recovery mode and choose xfix.

It didnt fix :(

> **phidia said:**
> Are you both using Hardy? The safest way to install the nvidia driver is through apt or synaptic if you have a desktop
When I tried *sudo apt-get install nvidia-glx-177 *  I got a message saying couldn't find package nvidia-glx-177

---

### Post by medic2000 on 2008-10-18
Nope i am using ArchLinux. It has rolling release. They gets the new driver to repos as soon as it released. So this is the disadvantage of rolling release :D

---

### Post by Chookah on 2008-10-18
I Fixed it!!  :guitar:


After the previous reply where it said it couldnt find the nvidia-glx-177 package, I tried sudo apt-get install nvidia-glx 

rebooted, I have gui!!

---

