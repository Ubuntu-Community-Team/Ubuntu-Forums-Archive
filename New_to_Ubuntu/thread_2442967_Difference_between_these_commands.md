---
title: "Difference between these commands?"
date: 2020-05-09
forum: New to Ubuntu
---

### Post by ferfykins on 2020-05-09
sudo apt update vs sudo apt-get update    and  sudo apt upgrade vs sudo apt-get upgrade    Which is better? thanks guys

---

### Post by The Cog on 2020-05-09
Update just fetches the latest list of what packages/versions are available. It doesn't install them. Upgrade installs the latest versions it knows about, but doesn't update its list of versions. So you always need to do update followed by upgrade.

apt only fairly recently got the ability to update and upgrade (I think it was originally a databse query tool). I use apt because it's shorter to type than apt-get. I think there are minor differences in options that I never use, but they can both do basic update and upgrade, which is all I ever use.

---

### Post by ferfykins on 2020-05-09
so apt and apt-get are no major differences?

---

### Post by CatKiller on 2020-05-09
apt is newer than apt-get. apt does some things that apt-get doesn't do, and apt-get does some things that apt doesn't do. aptitude does a different set of things again.

There are some details [here.](https://itsfoss.com/apt-vs-apt-get-difference/)

---

### Post by TheFu on 2020-05-09
> **ferfykins said:**
> so apt and apt-get are no major differences?

For certain values of "major differences", that could be true.  

The manpage for each is where i'd look for differences.  i always thought apt was a wrapper around apt-get and use them interchangeably until i require something specific to either one.

For example, **apt search** is very handy.  But so is **apt-get purge network-manager***  apt-get has globbing support that apt does not.

An added consideration may be which has the more stable interface.  apt warns that using in any scripts is not recommended because the interface (i.e. command options) are still changing. apt-get doesn't have that warning.

---

### Post by ActionParsnip on 2020-05-10
apt update

Reads your package sources to get the packages they offer. No packages are installed or altered 

apt upgrade 

Will download any package that has a newer version in your sources and install it as well as any deps needed.

---

### Post by ActionParsnip on 2020-05-10
The man pages can tell you more

---

