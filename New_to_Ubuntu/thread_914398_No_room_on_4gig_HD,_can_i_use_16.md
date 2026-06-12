---
title: "No room on 4gig HD, can i use 16?"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Bridge51 on 2008-09-08
I just got an eee 901. linux (running eeebuntu), 4gig and 16gig ssd's in it.

Can i mount other (16) as 'home or something?

I've been installing a lot of programs, and I have run out of room on the 4 gig. I want to know what i can do to put programs onto the other hard drive? 

or is this just for files/documents, not programs?

---

### Post by kpatz on 2008-09-08
There are a few things you could do.

1.  You could put / on the 4 and partition the 16 and put /var and /home there.  That should give you some more room on the 4 for programs.

2.  Install everything on the 16 (grub will let you boot from secondary drives) and use the 4 for /home or /var.

3.  Find out what directory most of your programs are being installed to, and put that on the 16.  For example, /usr/local.  If you don't want to repartition, create a /usr/local on the 16 and then symlink to it on the 4.

In either case, put your swap on the 16.

---

### Post by Bölvaður on 2008-09-08
I only know that you are able to do it, but **I have no idea how** :)

---

### Post by knix on 2008-09-08
when you install, choose manual partitioning. then, in gparted, switch device to your other ssd, and do whatever modification you need, then set it as /

---

### Post by Bridge51 on 2008-09-08
> **kpatz said:**
> There are a few things you could do.

1.  You could put / on the 4 and partition the 16 and put /var and /home there.  That should give you some more room on the 4 for programs.

2.  Install everything on the 16 (grub will let you boot from secondary drives) and use the 4 for /home or /var.

3.  Find out what directory most of your programs are being installed to, and put that on the 16.  For example, /usr/local.  If you don't want to repartition, create a /usr/local on the 16 and then symlink to it on the 4.

In either case, put your swap on the 16.

will doing any of this make my computer run slower?

---

