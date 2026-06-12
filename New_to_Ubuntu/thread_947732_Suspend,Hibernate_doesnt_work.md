---
title: "Suspend,Hibernate doesnt work"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Nedimm on 2008-10-14
When I try to Hibernate I get black screen and blinking cursor.Then I need to reset computer on button to log in.
In case when I click on Suspend computer shuts down and when I press power button on computer he starts but monitor is off, when try to power on monitor I cant.So I must reset computer on button to boot computer again.


O.S. Ubuntu 8.04
Motherboard:MSI P35 Platinum

---

### Post by nhasian on 2008-10-14
how much ram does your pc have?  also how big is your swap partition?

---

### Post by Nedimm on 2008-10-14
RAM:2 GB
Swap:953,7 MB

---

### Post by nhasian on 2008-10-14
for the suspend & hibernate features to work properly your swap partition must be at least as large as your ram.

---

### Post by Nedimm on 2008-10-14
How to extend swap?

---

### Post by nhasian on 2008-10-14
the easiest way is to boot off the liveCD and then run the gparted parition editing software from the system/administration toolbar.

Dont edit partitions while they are mounted or you will damage your data!  thats why you need to boot off the liveCD to do it.

Then you can resize your / or /home partition to make the /swap larger.  if you have 2 gigs of ram then make sure you have at least 2048M of swap.

please dont forget to thank me and mark the thread solved if this resolves your problem.  good luck!

---

### Post by Nedimm on 2008-10-17
Easier way [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
My swap is now 2.9 GB and no effect!

Anyone have other ideas?

---

