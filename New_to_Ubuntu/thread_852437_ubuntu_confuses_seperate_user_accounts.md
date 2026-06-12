---
title: "ubuntu confuses seperate user accounts"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by mustard greens on 2008-07-07
I currently have two user accounts set on my computer, but ubuntu seems to be getting them confused.  one day the admin account has advanced graphics activated, the next theyre gone.  when I check the secondary account they have advanced graphics capabilities, but the admin cannot activate.  then the next day the whole thing switches again.  also when I attach my camera, flash drive etc. it seems to try and open them in both accounts at once while denying access to one or the other user.  I cant seem to find where to fix these issues.  thanks for your help.

---

### Post by pytheas22 on 2008-07-07
In general, desktop effects can only run on one account at the same time.  I've heard, but can't verify, that it's now possible to run them on more than one account if you have an nvidia or ATI graphics card, but I don't know how to enable that.  If you have Intel or other graphics, you're out of luck--after all, desktop effects require a lot of video power, and an Intel card can't really handle more than one session at once anyway.

Double-mounting of the camera seems strange.  It makes sense that only one user--the one who mounted the camera--should be able to access it, but the other one shouldn't see it at all.

Maybe if you could provide more information about your configuration, we could get a better idea of possible causes for your strange behavior.  When are you switching between two accounts, and why (it sounds like you have one person on two different accounts--is there a reason)?

---

### Post by mustard greens on 2008-07-07
the two people are me and my girlfriend.  the two accounts arent nescesary, just nice to have.
I dont know how to view my hardware configurations in ubuntu. any advice?

---

### Post by webofunni on 2008-07-07
> **mustard greens said:**
> the two people are me and my girlfriend.  the two accounts arent nescesary, just nice to have.
I dont know how to view my hardware configurations in ubuntu. any advice?

```
lspci
```

Will list the hardware informations used for various purposes. 

```
cat /proc/cpuinfo
cat /proc/meminfo

```

Are also Good ;-)

---

### Post by t0p on 2008-07-07
> **mustard greens said:**
> I dont know how to view my hardware configurations in ubuntu. any advice?

```
lshw
```

---

