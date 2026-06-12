---
title: "[SOLVED] suck in  command line"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by kennydidit on 2008-10-16
I lost my desktop I was playing around with installing openoffice it had conflicts so I was trying to clear them up and I uninstalled a few programs one of then has a list that is was connected to and asked if I want to remove them to so I did things went crazy after that now when I reboot I get a command line prompt that says:
Kinit: name_to_dev_t(/dev/disk/by-uuid/4ba0e284-8e2b-4ff5-a7aa-b9bcc6fc8663) =s da3(8,3)
Kinit: trying to resume from dev/disk/by-uuid/4ba0e284-8e2b-4ff5-a7aa-b9bcc6fc8663  
Kinit: no resume image, doing normal boot….

Ubuntu 8.04.01 kennydidit tty1

Kennydidit login:

Anyone have any idea on what I did or where I am at and most importantly any idea on how to get this to run normally

---

### Post by slugboat on 2008-10-16
after you login, try typing

```
startx
```

also try ctrl+alt+F7

---

### Post by rraj.be on 2008-10-16
Try this command  . .

```
sudo gdm

```


This will open you the gui mode . .

if its being uninstalled then try this.
```

sudo apt-get install gdm
```

---

### Post by kennydidit on 2008-10-16
I tried 
the startx and I got into icewm
I just tried both gdm and sudu atp-get gdm and got 
sudo: unable to resolve host kennydidit 
E: invalid operation gdm 

PS as now I cannot  copy and past these line because my Linux box is stuck in command line so i am useing my pos windows box to post this

---

### Post by RATM_Owns on 2008-10-16
sudo aptitude install gdm

Don't forget install. sudo aptitude gdm will come up as an invalid option.

---

### Post by sumguy231 on 2008-10-16
Actually, you should do this:
```
sudo aptitude install ubuntu-desktop
```
As it will install all the desktop-related packages that come with Ubuntu.

---

### Post by kennydidit on 2008-10-16
I tried sudo aptitude install gdm
it did install but i was still in command line so tried 

> **sumguy231 said:**
> Actually, you should do this:
```
sudo aptitude install ubuntu-desktop
```
As it will install all the desktop-related packages that come with Ubuntu.

it installed and is setting up now we'll see what happen when it is done

---

### Post by kennydidit on 2008-10-16
installing the desktop worked 
Thank you all for your help
now back to installing openoffice LOL
kenny

---

