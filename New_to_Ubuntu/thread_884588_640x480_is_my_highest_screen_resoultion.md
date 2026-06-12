---
title: "640x480 is my highest screen resoultion?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by metasolaris on 2008-08-09
Hi

Just downloaded Hardy. Used Envy to get the right driver for my system. Rebooted but my highest screen resolution is 640x480. I'm not sure what to do to increase it and help would be great!

My system is Hardy on a amd64 x2 4400+. 2 GB RAM, Asus Geforce 8600gts card, Samsung Syncmaster 900 ift moniter.

---

### Post by metasolaris on 2008-08-09
In addition, only a small part of the Log On Screen displays, making it impossible to enter my username or password (I'm typing this from a Windows PC!) so its now impossible to log on to ubuntu!

Help!

---

### Post by PmDematagoda on 2008-08-09
Boot Ubuntu in Recovery Mode, then select xfix and see if that brings back a normal resolution. For the Nvidia driver, remove the Nvidia driver with Envy and try and install it through Hardware Drivers in System>Administration>Hardware Drivers.

---

### Post by metasolaris on 2008-08-09
Manage to fix the logon screen and remove the driver  - thanks!

What is the best way to get a restricted driver for the 8600gts?

I would be happy with the 'unrestricted' driver if the screen objects were not distorted (too tall, too thin) anyone know how to fix this?

---

### Post by PmDematagoda on 2008-08-09
> **metasolaris said:**
> What is the best way to get a restricted driver for the 8600gts?

Did you try taking a look at the Hardware Drivers application?

---

### Post by metasolaris on 2008-08-09
> **PmDematagoda said:**
> Did you try taking a look at the Hardware Drivers application?

Nuts - got an error message and Ubuntu rebooted

---

### Post by PmDematagoda on 2008-08-09
> **metasolaris said:**
> Nuts - got an error message and Ubuntu rebooted

What was the error message you got?

---

### Post by metasolaris on 2008-08-10
E: dpkg was interuppted, you must manually run 'dpkg --configure -a' to correct this problem
E: - cache ->open () failed, please report


Do I need to reinstall Hardy?

---

### Post by Methuselah on 2008-08-10
Try what it said.
Open a terminal and enter

```

sudo dpkg --configure -a

```

---

### Post by !ndy on 2008-08-10
i have a very different lowe-class geforce, but i was trying to set things up yesterday...
what helped me was uninstalling drivers with EnvyNG (hardy version)
and installing (in EnvyNG manual installation of 169.12 something)

some guys say that this helps:
[http://ubuntuforums.org/showthread.php?t=610272](http://ubuntuforums.org/showthread.php?t=610272)
on the bottom of that post are some famous four lines

and from here i have learned useful console commands for nvidia drivers
[http://ubuntuforums.org/showthread.php?t=534396](http://ubuntuforums.org/showthread.php?t=534396)

---

### Post by psycosmyth on 2008-08-10
Are you using the restricted kernel then?
I had this issue the other day and found a post here that helped. I'll try to fing it and get back if you don't get it resolved by then.

---

### Post by metasolaris on 2008-08-11
> **psycosmyth said:**
> Are you using the restricted kernel then?
I had this issue the other day and found a post here that helped. I'll try to fing it and get back if you don't get it resolved by then.

Well I have now tried Envy and Hardware Drivers to install the right driver for my asus 8600gts. Both approachs had the same results 1) a maximum screen resolution of 640x480 and 2) the log on screen becoming unuseable because its off centre.

As I said I would be happy just to rely on the free open driver but even this has a major problem; the text and images are distorted so that they look too tall and too thin.

I know there must be a way I can get my graphics to work!

meTa

---

### Post by metasolaris on 2008-08-11
> **metasolaris said:**
> Well I have now tried Envy and Hardware Drivers to install the right driver for my asus 8600gts. Both approachs had the same results 1) a maximum screen resolution of 640x480 and 2) the log on screen becoming unuseable because its off centre.

As I said I would be happy just to rely on the free open driver but even this has a major problem; the text and images are distorted so that they look too tall and too thin.

I know there must be a way I can get my graphics to work!

meTa

Ok well Im not sure what I did differently this time but I now have the restricted driver installed and 1280 x 1060 desktop, which is excellent!

One remaining problem is that the log on screen is seriously wrong, I can log on but its very off centre. Any ideas?

Thanks for all your advice to date!

---

### Post by peterjakey on 2008-08-11
I had a similar problem to this and it turned out it was my monitor, I had a 800x600 res and after I installed the nvidia driver I was limited to 640x480 however when i plugged a different monitor in it worked fine, try going to your display settings and selecting your monitor manually.

---

