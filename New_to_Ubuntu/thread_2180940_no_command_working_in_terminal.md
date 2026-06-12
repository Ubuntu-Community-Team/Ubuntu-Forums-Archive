---
title: "no command working in terminal"
date: 2013-10-15
forum: New to Ubuntu
---

### Post by nitin_negi on 2013-10-15
i just installed ubuntu 13.04.i tried to install apache but nothing working.i tried following commands.
1)sudo apt-get update...but it shows -11system error and some index files failed to download.they have been ignorned,or old are used instead.
2)sudo apt-get install apache2....this shows unable to locate package apache2..
3)i tried to connect netsetter micromax but it shows permission denied.
i am new in ubuntu13.04...do i need to make some settings with my terminal??please someone help its urgent..

---

### Post by tgalati4 on 2013-10-15
I use *tasksel* to install apache.  Install *tasksel* first then run it using *sudo*.  The failed repositories could be the shutdown of the medibuntu repositories--I've seen those errors and they require deleting or commenting out those sources in your /etc/apt/sources.list.

tgalati4@Mint14-Extensa ~ $ cat /etc/apt/sources.list
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) nadia main upstream import
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) quantal partner
**#deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) quantal free non-free**

# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) quantal-getdeb apps
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) quantal-getdeb game

I'm not familiar with netsetter micromax.

---

### Post by Bashing-om on 2013-10-15
nitin_negi; Hi !

Maybe a simple as the CD source is enabled ?; In any event we need to know the status of the package management system.
Post back - between code tags (#) - the output of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```
and ->
[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

