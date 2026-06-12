---
title: "upgrade from 11.10 to 12.04"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by barrykgerdes on 2012-09-07
I wish to upgrade from 11.10 to 12.04 
How do I initiate the upgrade option

Barry

---

### Post by NikTh on 2012-09-07
Hello , 

My recommendation is to do a fresh install of 12.04 . First backup all your personal data like, music , photos , documents etc to an external medium (eg : Usb flash or HDD). 

If you insist to upgrade then first disable or remove all external PPA's 

open a terminal and ```
gksudo software-properties-gtk
``` goto "Other Software" and disable (or delete) all external ppa's you added. 

Then press Alt+F2 combo and write **update-manager -d **to continue with upgrade. 

It will be good no other application running at this time .

Thanks

---

### Post by Epodx64 on 2012-09-07
I concur with a fresh installation. Upgrading shouldn't be such a point and click operation that Canonical has made it if you insist on doing it I highly recommend on killing X and upgrading from a console. I haven't upgraded to a new release in a while but I believe if you drop to a console its just

sudo apt-get update && sudo apt-get dist upgrade

---

### Post by NikTh on 2012-09-07
> **Epodx64 said:**
>  I haven't upgraded to a new release in a while but I believe if you drop to a console its just

sudo apt-get update && sudo apt-get dist upgrade

No , this will not upgrade the release from 11.10 to 12.04  . 

This will upgrade the packages . Apt-get is responsible for packages not for releases. 

From terminal (or console) the command that will upgrade the release - version of Ubuntu is 

```
sudo do-release-upgrade
``` 

But you mentioned something good . 
**@barrykgerdes**  except all steps above  , is good to do a system update with commands that **@Epodx64** mentioned_ before upgrade the release_.

So before the release-upgrade process begins , open a terminal and do 
```
sudo apt-get update ; sudo apt-get dist-upgrade
```

Thanks

---

### Post by barrykgerdes on 2012-09-07
I think that is the info I am after
Yes I can do a clean install if it fails but I want to see if I I can get an upgrade.
I already have 12.04 on another computer.

Barry

---

### Post by NikTh on 2012-09-07
> **barrykgerdes said:**
> I think that is the info I am after
Yes I can do a clean install if it fails but I want to see if I I can get an upgrade.
I already have 12.04 on another computer.

Barry

Ok , then do it and we expect the results. 

Thanks

---

### Post by Epodx64 on 2012-09-07
oh yeah sudo apt-get dist-upgrade ](*,) I really don't ever do Dist upgrades though I always do clean installs if you have a separate /home partition I really don't see why a fresh install seems so cumbersome. It will import all your settings files etc...

---

### Post by barrykgerdes on 2012-09-07
Reply #2 was the clue I was after.

However I ran out of /usr space and killed the program.
Then I installed 12.04 without any problem with wubi.exe into windows.

---

