---
title: "how to remove firefox 12 from ubuntu 10.04"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by translatorvasan on 2012-03-28
When trying to install the latest firefox version, I have installed firefox 12 without knowing that it is a beta version. Now as I find that it is not stable, I want to remove it completely and install the latest stable version of firefox. Need help as to how to go about it, please.

---

### Post by zombifier25 on 2012-03-28
Where did you get Firefox 12? From a ppa or somewhere else?

---

### Post by translatorvasan on 2012-03-28
I remember having  run a command related to ppa and then sudo apt get.But I don't remember where I got the commands from.

---

### Post by zombifier25 on 2012-03-28
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:mozillateam/firefox-next

```
I'm presuming ppa:mozillateam/firefox-next is where you get your Firefox beta. If not, open Software Sources and check the PPAs you have added for a Firefox beta PPA.

---

### Post by lovinglinux on 2012-03-31
> **zombifier25 said:**
> ```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:mozillateam/firefox-next

```
I'm presuming ppa:mozillateam/firefox-next is where you get your Firefox beta. If not, open Software Sources and check the PPAs you have added for a Firefox beta PPA.

Disable firefox-next ppa from Software Sources, then run this on  terminal:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get install --reinstall firefox

```

---

