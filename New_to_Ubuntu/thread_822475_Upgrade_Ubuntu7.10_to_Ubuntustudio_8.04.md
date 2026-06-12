---
title: "Upgrade Ubuntu7.10 to Ubuntustudio 8.04"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by rapattack1 on 2008-06-08
Hi how do and can I upgrade from Ubuntu 7.10 to Ubuntustudio 8.04? Also I think I made a boo boo with medibuntu and need to get rid of whatever I did because there is an update available that doesn't update. It is alerting me up the top of the desktop and I run it but it doesn't update. I have tried to solve this separately but don't know what I am doing. I really want to install ubuntustudio on the machine anyway and have the dvd. So I would like to know how to get the repositories active to do it. Is this possible? Oh and is it safe or should I back up files first?

---

### Post by atomkarinca on 2008-06-15
For your package update problem you can try this: open up Synaptic and hit "Mark All Upgrades", this should do it.

From Ubuntu 7.10 to Ubuntu Studio 8.04, the best bet would be upgrading to Ubuntu 8.04 then installing the Ubuntu Studio meta package. Do a dist-upgrade

```
sudo update-manager --dist-upgrade
```

or

```
sudo update-manager -p
```

After it's finished, you can install Ubuntu Studio:

```
sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

---

### Post by morganzoo on 2008-06-15
Thanks... looks helpful for my issue.  I am trying to install studio from edububtu 8.04.  I used the script, but it is asking for the edububtu cd...pop it in and I get stuck from there...any thoughts?

---

### Post by atomkarinca on 2008-06-15
Maybe you have the "apt on cd" (I don't remember what exactly it's called) option enabled. System > Administration > Software Sources and try disabling CD/DVD for install/update.

---

### Post by kansasnoob on 2008-06-15
Just FYI, while I've never dealt with Ubuntu Studio, I have done over 20 Ubuntu installs (mostly for seniors that were stuck on Win 98 and ME) and my experience with the upgrade path is about 50/50! Half the time it works, and the other half I just end up doing a clean install!

Just my 2 cents worth:confused:

---

### Post by RedRat on 2008-06-15
> **kansasnoob said:**
> Just FYI, while I've never dealt with Ubuntu Studio, I have done over 20 Ubuntu installs (mostly for seniors that were stuck on Win 98 and ME) and my experience with the upgrade path is about 50/50! Half the time it works, and the other half I just end up doing a clean install!

Just my 2 cents worth:confused:

I must second that. I had a Dell installed 7.10 on my 530n and when I attempted to install Ubuntu Studio, the system went into the toilet. My only recourse was to wipe the disk and install vanilla Ubuntu 7.10 This worked quite well except that I did have initial problems with the nVidia settings. My upgrade to 8.04 went very well and resolved my nVidia problems. The system appears to be stable and works. No problems so far.

I would approach putting Studio on with some care--just my 2 cents worth.

---

### Post by morganzoo on 2008-06-16
It worked!  Disabling the cd worked like a charm...  now I'm running Studio and I didn't lose a thing.

Thanks!

---

### Post by rapattack1 on 2008-06-17
Oh I managed to get rid of the medibuntu entry in the repositories so everything is good with that. I should have mentioned I don't have enough internet usage to upgrade via the net. I got ubuntu 8 from a friend that has got plenty of usage. So there is no way I can do a full upgrade of anything from the net.
So if you are all saying that it would be risky doing it from a dvd then I will have to back up everything first. I do have both Ubuntu 8 plain and ubuntustudio on different dvd's.

---

