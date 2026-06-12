---
title: "Trouble upgrading 7.04-8.04"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Tssabackus on 2008-06-30
I have tried ```
apt-get dist-upgrade
```, which said nothing was needed. I have also tried ```
sudo update-manager --dist-upgrade
``` which at least brought up the dist upgrade screen, but it told me my system is up to date. 

A few days ago I was going to upgrade, and I started the process, but I canceled *before* the point of no return when its not recommended you stop the process. What can I do?

On a side note, help setting up dual-monitors with a Radeon 9550 would be appreciated ;)

---

### Post by avtolle on 2008-06-30
Well, first of all, you are trying to do a direct upgrade from 7.04 to 8.04, which (although I've read where others have managed to do it) isn't supposed to be possible. I believe the recommended way to do this via the upgrade manager is to go from 7.04 to 7.10, then after fully updating 7.10, go on to 8.04. To go from 7.04 to 8.04, generally (and I recommend) a clean install from the iso burned to CD is the way to do it.

EDIT: [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) discusses upgrading from 7.04 to 7.10 via a "network upgrade", if you are interested.

---

### Post by Inxsible on 2008-06-30
Have you tried using the update manager to upgrade your distribution?

```
sudo update-manager
``` to start it. It will have a button which will ask you if you want to upgrade your OS.

---

### Post by philinux on 2008-06-30
I always used

update-manager -d

It then asks for you password at a later stage.

---

### Post by Tssabackus on 2008-06-30
Alright its updating now. Its currently updating to 7.10.

Thank you both for your help. Does apt-get dist-upgrade not work anymore? Why did those commands tell me I was up-to-date, while this works?

---

### Post by philinux on 2008-06-30
Which command did you use.

---

### Post by Inxsible on 2008-06-30
> **Tssabackus said:**
> Alright its updating now. Its currently updating to 7.10.

Thank you both for your help. Does apt-get dist-upgrade not work anymore? Why did those commands tell me I was up-to-date, while this works?
Good Luck waiting !!

Its gonna take a long time to upgrade to 7.10 and then from 7.10 to 8.04 ;-)

---

### Post by Inxsible on 2008-06-30
> **philinux said:**
> Which command did you use.They both amount to the same thing. my command requires the user to click on the button to upgrade. with the -d option i think it assumes dist upgrade using development releases

---

