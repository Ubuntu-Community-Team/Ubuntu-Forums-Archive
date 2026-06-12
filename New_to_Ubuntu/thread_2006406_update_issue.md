---
title: "update issue"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by krishnan t s k on 2012-06-19
i've been unable to update ubuntu using the update manager since morning
kept getting the error in the image i've attached with post
please help and thanks in advance :)

---

### Post by NikTh on 2012-06-19
This is probably a problem with PPA , but i am not sure. Did you add PPA (repository) lately ?

Give the output of
```
find /etc/apt/ -iname "*.list" -exec echo "FILE: {}" \; -exec cat "{}" \;
```

**Copy the entire out put and paste between [CODE] brackets by clicking on # at the top of the message pane.**

---

### Post by plucky on 2012-06-19
> **krishnan t s k said:**
> i've been unable to update ubuntu using the update manager since morning
kept getting the error in the image i've attached with post
please help and thanks in advance :)

Open a terminal (Ctrl+Alt+t) and run ```
sudo apt-get update && sudo apt-get upgrade
``` and post back any errors.

Good Luck

---

### Post by krishnan t s k on 2012-06-19
> **NikTh said:**
> This is probably a problem with PPA , but i am not sure. Did you add PPA (repository) lately ?

Give the output of
```
find /etc/apt/ -iname "*.list" -exec echo "FILE: {}" \; -exec cat "{}" \;
```**Copy the entire out put and paste between ```
 brackets by clicking on # at the top of the message pane.**


[CODE]FILE: /etc/apt/sources.list
# /etc/apt/sources.list

deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse #Added by software-properties
FILE: /etc/apt/sources.list.d/scopes-packagers-ppa-precise.list
deb http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu precise main
FILE: /etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list
deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
FILE: /etc/apt/sources.list.d/precise-partner.list
deb http://archive.canonical.com/ubuntu precise partner #Added by software-center
FILE: /etc/apt/sources.list.d/opera.list
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)

# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.

# deb http://deb.opera.com/opera-beta/ stable non-free #Opera Browser (beta releases)
FILE: /etc/apt/sources.list.d/playdeb.list
# deb http://archive.getdeb.net/ubuntu precise-getdeb games

```

---

### Post by krishnan t s k on 2012-06-19
> **plucky said:**
> Open a terminal (Ctrl+Alt+t) and run ```
sudo apt-get update && sudo apt-get upgrade
``` and post back any errors.

Good Luck

```
sudo apt-get update && sudo apt-get upgrade
[sudo] password for private: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by krishnan t s k on 2012-06-19
I restarted my system and ran the update manager again... this time it told me that the software index was broken and suggested that i run sudo apt-get install -f from the terminal
I ran it and it seems to have solved the problem now... updates got installed :D:D

---

### Post by plucky on 2012-06-19
> **krishnan t s k said:**
> I restarted my system and ran the update manager again... this time it told me that the software index was broken and suggested that i run sudo apt-get install -f from the terminal
I ran it and it seems to have solved the problem now... updates got installed :D:D

If you are happy that it is **[Solved]**,you can use **[Thread Tools]** at the top of the page to mark it as **[Solved]**

Good luck

---

