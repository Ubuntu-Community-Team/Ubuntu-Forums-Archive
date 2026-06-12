---
title: "what is the simplest way to make an image of OS?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by danny_galaga on 2008-11-19
ok, ive now upgraded to 8.10 and before i make too many changes, id like to make an image and burn it to cd/dvd. as it stands, if i screw something up really badly, i only have 8.04 on disk, without updates.

so what would be the easiest, most GUI based way to do this?

---

### Post by rampageoberon on 2008-11-19
You can use Remastersys or PartImage for imaging your install.

---

### Post by harvey186 on 2008-11-19
> **rampageoberon said:**
> You can use Remastersys or PartImage for imaging your install.

remastersys is simply the best :-)

---

### Post by Dedoimedo on 2008-11-19
Hello,
I'd say go with Remastersys. A great program.
You can also create custom live CDs - or even share with friends.
Dedoimedo

---

### Post by danny_galaga on 2008-11-25
ok, ive finally gotten around to using remastersys. looks like ive made an iso. i canttell! at the end of it it said it should be in home/remastersys/remastersys. i think that was it. did it yesterday. should i have had the cd in right at the start maybe?

---

### Post by kpkeerthi on 2008-11-25
You can use a CD burner application like brasero, k3b to burn the ISO you just made to a CD

---

### Post by danny_galaga on 2008-11-25
sorry, i cocked up that last post. what i meant was i cant see the iso! i mean, i went through the whole process and at the end it said the iso is in the home directory. but i dont see it there. why would that be? im loath to just do the whole process again. i dont really want to fill up my hard drive with invisible iso's!

---

### Post by danny_galaga on 2008-11-27
thoughts, anyone?

---

### Post by tarps87 on 2008-11-27
Did you look for an iso or the remastersys file. Try:
```
nautilus /home/remastersys/remastersys
```

If its not there it would appear it hasn't written to the disk for some reason

---

### Post by Dedoimedo on 2008-11-27
Maybe you do not have enough free space to write the image to the desired location?
Dedoimedo

---

### Post by hyper_ch on 2008-11-27
dd makes it very simple

---

