---
title: "cacti run on ubutu 12"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by Noel.One on 2014-04-22
Greeting to all,

newbie here, would like to ask a question regarding cacti run on ubuntu. 

01. Does ubuntu 12.04.4 version come with cacti packages? Or need to separate download php, mysql, cacti, rrdtool, apache component manually?

thanks

Noel.1

---

### Post by tgalati4 on 2014-04-22
I like to use *tasksel* to install a standard LAMP stack.  I'm sure cacti exists in the 12.04 repos.  Here's what it looks like in 12.10:

tgalati4@Mint14-Extensa ~ $ apt-cache search cacti
cacti - web interface for graphing of monitoring systems
cacti-spine - Multi-Threading poller for cacti
libpam-blue - PAM module for local authenticaction with bluetooth devices
serverstats - a simple tool for creating graphs using rrdtool

I've run *cacti* and *nagios* on an older 8.04 system, so I'm sure they are available on 12.04.

These are very old instructions; there are probably better tutorials for 12.04:  [https://help.ubuntu.com/community/Cacti](https://help.ubuntu.com/community/Cacti)

---

### Post by Danger_Monkey on 2014-04-22
They are available, but they are an older version in the repositories.  In my case, I used apt to get the base, then installed the newer version so I could have all the latest bells and whistles.  

```

apt-get install cacti cacti-spine 

```

After that, I just:

```

mv /usr/share/cacti /usr/share/cacti.old

```

Then copied the latest version into that place.  Because I'm monitoring about a hundred linux machines, I scripted the config of all the servers.

---

