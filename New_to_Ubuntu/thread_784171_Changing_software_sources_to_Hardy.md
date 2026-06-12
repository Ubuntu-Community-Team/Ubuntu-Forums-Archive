---
title: "Changing software sources to Hardy"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by sports fan Matt on 2008-05-06
If one like myself who upgraded from Gutsy went into software sources and "changed" the software sources items from Gutsy to Hardy, would he or she would have a complete up to date machine upon completion of the updates? (This would be after upgrading to Hardy of course)

---

### Post by Paqman on 2008-05-06
During the upgrade process your software sources will be switched from Gutsy to Hardy anyway. Or at least, they should be. Have you still got Gutsy ones?

---

### Post by mano cazalet on 2008-05-06
Yes, I believe you have an updated hardy. 
To make sure you can check it in System tab of your system monitor. 

It should say Ubuntu Release Hardy (8.04)

---

### Post by ukripper on 2008-05-06
it updates software sources itself during the upgrade from gutsy to hardy repos.

---

### Post by aysiu on 2008-05-06
That's the old way to do it (manually change the sources and then *dist-upgrade*).

The newer way is safer and does all that for you:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Hospadar on 2008-05-06
While changing the software sources like that will end you up with all the current hardy packages, you may miss new base packages, and some out-of-date packages may hang around.  You're better of doing a dist-upgrade from the command line or update manager.  Really the best way to do it is by keeping a seperate home partition and re-installing from CD, but depending on what kind of configurations you have (let's say something special to make your wifi or sound work) that might be more trouble then it's worth.

---

