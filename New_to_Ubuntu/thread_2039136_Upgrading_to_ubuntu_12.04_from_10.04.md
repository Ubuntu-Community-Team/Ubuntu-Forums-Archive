---
title: "Upgrading to ubuntu 12.04 from 10.04"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by Lingadharini on 2012-08-08
I am using ubuntu 10.04. Is it possible to directly upgrade to 12.04 without having to install all the other versions like 10.10 etc?
If so, tell me how to do that..
Is it possible to upgrade from a iso copy of 12.04 or will I have to make a fresh installation if I use 12.04 cd?

---

### Post by mcduck on 2012-08-08
Yes, it's possible as 10.04 and 12.04 are both LTS versions, and the upgrades from one LTS version to other are supported even though you usually can't jump over any version when upgrading.

You will most likely have to do the upgrade using the Update Manager, as any CD you download wouldn't have updated packages of any extra software you have installed on your computer. Anyway, the Update Manager should show you a button that allows you to do the update to 12.04.

However I would recommend making a fresh install instead, while such update is supported in theory, there are loads and loads of changes between tose versions and you are more likely to get a smoothly working and problem-free system (probably even with less work) by backign up your files and making a fresh instal of 12.04...

---

### Post by Lingadharini on 2012-08-08
How to make a backup of all the softwares I have installed?

---

### Post by mastablasta on 2012-08-08
it is also faster to do a fresh install.

---

### Post by HeinS5 on 2012-08-08
If you want to upgrade within the system :
1) open the terminal
2) type : sudo apt-get dist-update
3) type : sudo apt-get dist-upgrade

It works for me!

If you want to know more open the terminal and type : man apt-get
Then you get a manual for the apt-get software manager with an explanation about distribution update.

---

### Post by HeinS5 on 2012-08-08
> **Lingadharini said:**
> How to make a backup of all the softwares I have installed?

In the terminal :
dpkg -- get-selections '*' > programlist.txt

Then you make a text file with all the installed programs. This text file will be put in the active folder.

To put everything back :
dpkg -- set-selections < programlist.txt

followed by :

aptitude install

or

apt-get -u dselect-upgrade
for more info :
'man dpkg' in the terminal.

P.S. Please tell me if it worked, because i've never tried this myself.

---

### Post by Lingadharini on 2012-08-08
I dont think I am going to upgrade my 10.04 to 12.04 now. May be some time later 'coz I dont have the 12.04 iso cd. And it will take years if I have to download with my slow Internet connection. I will update sometime later.

---

