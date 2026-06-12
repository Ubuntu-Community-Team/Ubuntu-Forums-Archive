---
title: "Lenovo is making it hard for me to do a dual boot HELP!!!!"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by covaloch on 2008-05-26
Hi i've stated before somehwere that i wanted to do a dual boot. so i finally figured out what size my partitions should be etc etc. I was usuing ubuntu solely at that time. I left about 30gigs for winxp, and another 45gigs for a partition that would be used to store data such as pictures, movies, music, etc.

However, Lenovo, and i'm sure many other laptop manufacturers, only gives this **inane restore and rescue cd and dvd**. What it basically does is reformat my entire fraking drive, installs a hidden partition,installs an even more bloated windows xp, with a million other apps, takes 2 hours to install (i kid you not) and doesnt give me any options as to partitioning. It uses the entire hardisk and partitions it in ntfs. 

So how do i go about dual booting if the **draconian measures** taken by the rescue and recovery disk doesnt let me choose what partition i want to install winxp to? (Oh btw the kicker - for some reason, after 2 days of using winxp, i suddenly couldnt connect to the internet. wireless says its connected to my wireless router, internet explorer and wow refuses to connect). i got so irritated i just formatted everything again with a fresh Hardy Heron, where i can connect online straight away wtihout any fuss, and everything works. This however is a temporary solution as i still need to install winxp.

Any way i can do this? What about other laptop/lenovo users, how did u go about dual booting?

---

### Post by bumanie on 2008-05-26
You should ideally install xp before ubuntu as doing it the other way around causes extra work re xp overwriting ubuntu bootlader etc. I suggest install xp via the 'draconian method'. Then download and burn a copy of gparted live cd. It is a hard drive specific partitioning program which will allow you to shrink your xp partition to the size you want and then make an ext3 partition on the remainder of the disc. When installing ubuntu.

---

### Post by ingrid_ozikem on 2008-05-26
I'm sorry but is installing XP first and then installing Ubuntu not an option?

Even if XP uses up all the space, you can resize and make existing partitions smaller without losing the data on it. (It worked safe for me but you do want to back up any important data before trying to resize..)

Finally, a common problem I've read about here is that installing Windows after linux might remove the boot menu (the grub menu) which allows you to choose between Win/Lin. The solution seems to be to use supergrub -- do a search for grub in these forums if you do end up with this problem.

---

### Post by covaloch on 2008-05-26
ALrighty. Nah i was just wondering if it was possible to do it from linux->windows dualboot painlessly.

The problem is that with repartitioning winxp,i probably might lose some data. probably should do a defrag first. Thanks folks.

---

