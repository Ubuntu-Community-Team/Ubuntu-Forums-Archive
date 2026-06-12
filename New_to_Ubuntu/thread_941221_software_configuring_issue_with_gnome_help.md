---
title: "software configuring issue with gnome? help"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by aaron1011 on 2008-10-07
I am attempting to install a software program from source.

the program is called gnomesword-2.4.0

i successfully downloaded the tar.gz file
unpacked the file 
./configure

when i ./configure it starts, gets to  // checking for GNOME.......NO and quits

i have tried installing GNOME from synaptic to no avail.  something about the software repositories.
i did an //apt-get install GNOME    which ran for a second and then said it had broken packages
i did an  //aptitude get install gnome-core    it installed but didn't fix my problem
what do i do next and how do i get past this GNOME issue.    thanks

---

### Post by JoshuaRL on 2008-10-07
Alright, got a few commands for you to run:
```

sudo apt-get update
sudo apt-get upgrade
sudo aptitude install ubuntu-desktop
sudo apt-get install build-essential
sudo apt-get install -f
sudo dpkg -configure -a

```
Hopefully that will get you all you need.

---

### Post by aaron1011 on 2008-10-07
all these commands ran fine with no problems except the dpkg command

it returned       dkpg:  unknown option -o

i tried running the ./configure      command for gnomesword-2.4.0 again and it returned the same result.

---

### Post by JoshuaRL on 2008-10-08
Sorry.
```

sudo dpkg --configure -a

```
Typos.  They are not my friends.  Especially on the command line.

---

### Post by chaosdesigner on 2008-10-08
I would take look at the script your running, this might help you see where exacly the problem takes place.

Edit:

I also used to have a Gnome Problem and I just deleted the Folder called .Gnome in the Home directory, this generated it new. I'm not 100% sure that this will work but its worth a try (of course you will need to backup your .Gnome Folder incase something goes wrong).

---

