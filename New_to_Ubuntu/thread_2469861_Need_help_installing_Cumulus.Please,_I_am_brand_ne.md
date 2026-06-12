---
title: "Need help installing Cumulus.Please, I am brand new to Ubuntu,"
date: 2021-12-11
forum: New to Ubuntu
---

### Post by socrates117117 on 2021-12-11
84 year old newbie. Want to use. terminal to install Cumulus or Meteo. My first question is where to get them from (which repository) and then what to enter into termina. I need a step by step guide. Thanks for any help you can give me.

---

### Post by deadflowr on 2021-12-11
This is moot as far as Cumulus is concerned, but depends on what version of Ubuntu you are using.
The last available was for Ubuntu 20.04 focal fossa  from here: [https://launchpad.net/~cumulus-team/+archive/ubuntu/cumulus?field.series_filter=focal]("https://launchpad.net/~cumulus-team/+archive/ubuntu/cumulus?field.series_filter=focal")
But as the page tells us at the top it no longer works as the APIs for the service required have changed, making it as I started this thread moot.

As for meteo, looks like it's available from this PPA: [https://launchpad.net/~bitseater/+archive/ubuntu/ppa]("https://launchpad.net/~bitseater/+archive/ubuntu/ppa")
In general you'll need to run
```
sudo add-apt-repository ppa:bitseater/ppa
sudo apt-get update
sudo apt install com.gitlab.bitseater.meteo
```
It looks like it's fully supported for all current Ubuntu releases.

---

