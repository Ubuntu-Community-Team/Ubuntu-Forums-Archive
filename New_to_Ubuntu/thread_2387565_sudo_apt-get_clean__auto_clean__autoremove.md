---
title: "sudo apt-get clean / auto clean / autoremove"
date: 2018-03-20
forum: New to Ubuntu
---

### Post by deanr2 on 2018-03-20
A couple of simple questions: should I or shouldn't I use the following commands in terminal let's say, once a month? How often do you do it?

sudo apt-get clean
sudo apt-get auto clean
sudo apt-get autoremove

---

### Post by monkeybrain20122 on 2018-03-20
I do it whenever I am bored. Actually I use bleachbit Too lazy to type.

---

### Post by deadflowr on 2018-03-20
clean makes autoclean moot.
Since clean clears everything out.
(autoclean only clears the older package version archives out.)
Both clear out the downloaded installer packages that the system archives for you.

autoremove is something different.
it actually removes installed software, that the system has deemed old and obsolete.

So run one of the clean commands and the autoremove command.
Your choice as to which.

How often will depend on how liberal or stingy you were when you setup Ubuntu, in regards to the amount of hard drive space.
If you allocated a large amount of space, then you could go years without running those commands.
But if you allocated a very small amount, then you might need to run them weekly or biweekly, depending on things like what new updates come.
(or if you need the space for your own personal files)

---

### Post by monkeybrain20122 on 2018-03-20
> **deadflowr said:**
> clean makes autoclean moot.

autoremove is something different.
it actually removes installed software, that the system has deemed old and obsolete.




No, it doesn't. It removes software which are installed as dependencies of others, which you have uninstalled. Say sudo apt install A brings in B as a dependency, now you have uninstalled A (not through autoremove!) then B becomes autoremovable. The only exception I know of is old kernels. Ubuntu keeps two kernels by default, so when it upgrades to a third one, the oldest one becomes autoremovable. Since Ubuntu apparently by default puts all kernels in a tiny /boot partition ( if you install automatically, since I always do manual I can't be sure, just from reading forum threads) and many people have problems when /boot is full, I think one should do autoremove more often.

---

### Post by cruzer001 on 2018-03-20
You may find this handy

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

