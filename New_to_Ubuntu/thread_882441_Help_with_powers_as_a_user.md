---
title: "Help with powers as a user"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by manners2345 on 2008-08-07
Almost anything I want to do requires that i am able to be the root. Such as rename partitions, drag and drop a file from one partition to another because simple backup put in the wrong partition. I am in the admin group, and the root group. I am also trying to setup Tor as both a client and as relay server. Trying to use Tork. To change the config file I also need to be the root. How do I get powers of root without being root. Using 8.04 Hardy Heron

:confused:

Thanks for any help

---

### Post by Oldsoldier2003 on 2008-08-07
> **manners2345 said:**
> Almost anything I want to do requires that i am able to be the root. Such as rename partitions, drag and drop a file from one partition to another because simple backup put in the wrong partition. I am in the admin group, and the root group. I am also trying to setup Tor as both a client and as relay server. Trying to use Tork. To change the config file I also need to be the root. How do I get powers of root without being root. Using 8.04 Hardy Heron

:confused:

Thanks for any help

```
sudo <somecommand> 
``` will execute <somecommand> as root.

edit: also, don't worry that you don't see your password or asterisks shown as you enter it. just type your password and hit enter.

---

### Post by RequinB4 on 2008-08-07
See my signature for sudo and root, how they interact, and why being root is not fun.

---

### Post by manners2345 on 2008-08-07
> **RequinB4 said:**
> See my signature for sudo and root, how they interact, and why being root is not fun.
When I setup Ubuntu it did not asked me if I wanted to make my 350Gig external hard pretty much useless to me, making the owner "root",the group "root" and  limited access with no right to change.I cannot save anything to any of the partitions. I have been reading the links sent and still have no idea how to change my hdd permissions. I have tried sudo,but I have no clue as to what to put in.I have tried varations of the following  /media/ properities/permissions, nothing happens!! I have tried to use gksudo it comes wanting to know what program I want to run, me no clue!!!!

---

### Post by hyper_ch on 2008-08-07
> **manners2345 said:**
> When I setup Ubuntu it did not asked me if I wanted to make my 350Gig external hard pretty much useless to me, making the owner "root",the group "root" and  limited access with no right to change.

That's how it's supposed to work.

You can alter its user and group. You can alter it's mount settings...

---

### Post by laffinet on 2008-08-07
You can change the permissions on the external hard drive by running nautilus with gksudo

```
gksudo nautilus
```

Then right click on any of the folders of that hard drive and change the permissions.

---

### Post by Bucky Ball on 2008-08-07
Why don't you just right click the drive on the desktop, goto properties and change the permissions? If you are owner, you shouldn't need to use terminal to do this.

---

### Post by JoshuaRL on 2008-08-07
> **Bucky Ball said:**
> Why don't you just right click the drive on the desktop, goto properties and change the permissions? If you are owner, you shouldn't need to use terminal to do this.

Agreed.  This is pretty easy OP, I'm sure you just overthought it.  It's one of the tabs in the Properties menu.  "Permissions" is what you're looking for.  So from there you can change it to yourself, anyone, or whatever you want.

---

### Post by hyper_ch on 2008-08-07
> **Bucky Ball said:**
> Why don't you just right click the drive on the desktop, goto properties and change the permissions? If you are owner, you shouldn't need to use terminal to do this.

he's not the owner ;)

---

### Post by JoshuaRL on 2008-08-07
> **hyper_ch said:**
> he's not the owner ;)

I'm dumb sometimes.  But yeah, gksu nautilus should allow you to do the same thing.  Just make sure that after you do that, you close it out.  It's REALLY easy to mess up some stuff by browsing around in root nautilus.

Thanks hyper_ch.

---

### Post by Bucky Ball on 2008-08-07
> he's not the owner

ah ha. Apologies.

---

### Post by manners2345 on 2008-08-07
A 350Gig worth of thank yous, it works

Thank You
Thank You
Thank You

---

### Post by Bucky Ball on 2008-08-07
Fantastic news, manners2345!!

Can you possibly outline how you did this for future users with the same probs? :)

---

