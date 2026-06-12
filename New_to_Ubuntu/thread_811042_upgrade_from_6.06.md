---
title: "upgrade from 6.06"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by allenb.bigal on 2008-05-28
Being an absolute beginner, I don't know what to do about upgrade.

I am using 6.06 and I have a Celeron 2.26Ghz processor which I believe is 32 bit. What I don't know, is can I upgrade to the latest version (which I understand is 64 bit) or do I have to stay on the current version?

I've looked in the forums and cannot find any reference to this question.

Thanks

---

### Post by kwacka on 2008-05-28
I don't believe that you could upgrade from 32-bit 7.4 to 7.10, so I would make the assumption that you can't upgrade from 6.06 32-bit to 8.04 64-bit.

If you've got your /home on a separate partition just re-install without formating that partition, if you haven't you'll have to backup, of course.

---

### Post by cdtech on 2008-05-28
See if maybe this site can help you with your upgrade. If not just let us know.

[[COLOR="DarkRed"]How to Upgrade[/COLOR]]("http://www.debianadmin.com/how-to-upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn.html")

Hope this helps......

P.S.
I just tried the GUI link and instead of this [gksu “update-manager -c ”] use this:
```
sudo update-manager -c
```

---

### Post by pdwerryhouse on 2008-05-28
> **allenb.bigal said:**
> I am using 6.06 and I have a Celeron 2.26Ghz processor which I believe is 32 bit.

The lastest release has both 32 and 64 bit versions (as did 6.06), so that won't be an obstacle to your upgrade.

Jumping directly from 6.06 to 8.04 might be problematic; you could just try updating your /etc/apt/sources.list file to point at gutsy and then running:

apt-get update
apt-get -s dist-upgrade

...and it will list all the changes that it will make, without actually performing them. You'll then be able to see which packages will get added and removed.

You might be better just backing everything up and reinstalling.

---

### Post by theophiles on 2008-05-28
> **pdwerryhouse said:**
> The lastest release has both 32 and 64 bit versions (as did 6.06), so that won't be an obstacle to your upgrade.

Jumping directly from 6.06 to 8.04 might be problematic; you could just try updating your /etc/apt/sources.list file to point at gutsy and then running:

apt-get update
apt-get -s dist-upgrade

...and it will list all the changes that it will make, without actually performing them. You'll then be able to see which packages will get added and removed.

You might be better just backing everything up and reinstalling.

"Problematic" is a very diplomatic way of putting it. Instead it is better to move up through the upgrades: 6.10  to 7.04; 7.04 to 7.10; then 7.10 to 8.04.

[This site]("https://help.ubuntu.com/community/UpgradeNotes") has links for how to do each of them. 

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by louieb on 2008-05-28
Look around  6.06 Dapper was the 1st  LTS  80.4 Hardy is the 2nd LTS. I've seem to remember you can directly upgrade.  Ok just found the wiki page 
[https://help.ubuntu.com/community/HardyUpgrades#head-e7f287c730b93116f89de7ea7e05efbe95fa6dd1](https://help.ubuntu.com/community/HardyUpgrades#head-e7f287c730b93116f89de7ea7e05efbe95fa6dd1)

You can do a direct upgrade. But as alway backup your system. I use partimage available on the SystemRescue CD

---

### Post by lazyart on 2008-05-28
Yes, you can upgrade directly from Dapper (6.06) to Hardy since they are both LTS.  However you can not upgrade from 32 bit to 64 bit-- you'll have to do a fresh install.  Save your /home if you do!

---

