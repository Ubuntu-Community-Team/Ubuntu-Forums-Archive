---
title: "Recommended way to have user upgrade PPA"
date: 2010-11-23
forum: Packaging and Compiling Programs
---

### Post by MrQuincle on 2010-11-23
The method I tell my user now is the following:
```

cd /etc/apt/sources.list.d/
sudo cp robot3d-team-ppa-robot3d-lucid.list robot3d-team-ppa-robot3d-maverick.list
sudo sed -i 's/lucid/maverick/g' robot3d-team-ppa-robot3d-maverick.list
sudo sed -i 's/#//g' robot3d-team-ppa-robot3d-maverick.list
sudo aptitude update
sudo aptitude safe-upgrade

```

Is there some more user-friendly way to update a PPA from lucid to maverick? 

Something like update-apt-repository instead of add-apt-repository? 

Even better, perhaps it can be checked automatically by aptitude?

---

### Post by MrQuincle on 2010-11-29
I found this: [https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html](https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html)

However, automatic install of unintended updates is a bit too much. I just want to have an easy GUI that iterates through all the unintended PPAs and asks the user to re-enable them.

---

### Post by MrQuincle on 2012-05-13
After a few years, I am still curious if there is a method for this, that I can recommend to my users....

:popcorn:

---

