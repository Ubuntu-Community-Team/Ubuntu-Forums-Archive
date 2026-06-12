---
title: "CLI - cron update/upgrade"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by adamogardner on 2008-10-01
I'd like to set up my rig to sudo apt-get update/upgrade once per day.  will this work with 'sudo?'  How do I do this?  Do I start a new shell script, or edit an existing one?

---

### Post by kpkeerthi on 2008-10-01
Just add ```
apt-get update && apt-get upgrade
``` to root's crontab.

To edit root's crontab:
```
sudo crontab -e
```

[[More Info]("https://help.ubuntu.com/community/CronHowto")]

---

### Post by adamogardner on 2008-10-01
> **kpkeerthi said:**
> Just add ```
apt-get update && apt-get upgrade
``` to root's crontab.

To edit root's crontab:
```
sudo crontab -e
```

[[More Info]("https://help.ubuntu.com/community/CronHowto")]

what does...  # m h  dom mon dow    command...mean?  and I past the above below this?  and it knows to do it daily? or how often?

---

### Post by superprash2003 on 2008-10-01
hope this helps [http://prash-babu.blogspot.com/2008/07/how-to-schedule-your-ubuntu-machine-to.html](http://prash-babu.blogspot.com/2008/07/how-to-schedule-your-ubuntu-machine-to.html)

---

### Post by hyper_ch on 2008-10-01
actually you'd use 
```

apt-get update && apt-get -y upgrade

```
But I would not auto-upgrade the packages.

---

### Post by adamogardner on 2008-10-01
> **hyper_ch said:**
> actually you'd use 
```

apt-get update && apt-get -y upgrade

```
But I would not auto-upgrade the packages.

why not?  It is all related to existing software, not like it's gonna overhaul my system, right?  Yeah I was waiting for someone to suggest 'apt-get' rather than aptitude.  wasn;t sure if it was the same thing or not.  Just one other question; What is '-y'?

---

### Post by hyper_ch on 2008-10-01
> **adamogardner said:**
> why not?  It is all related to existing software, not like it's gonna overhaul my system, right?
Sometimes it breaks stuff... especially when you get a new kernel and then wonder why vbox/vmware don't work... I rather manually say what I want to upgrade... however you can also just fetch all the upgradable .debs by using the "download" instead of "install" directive.

> **adamogardner said:**
> Just one other question; What is '-y'?
Open a terminal, type:
```

man apt-get

```
and then browse for the -y option. Apt-get has plenty of other options/directives, so if you really wanna know what apt-get can do, have a little read through the man page :)

---

### Post by kpkeerthi on 2008-10-02
> **hyper_ch said:**
> actually you'd use 
```

apt-get update && apt-get -y upgrade

```


Thanks hyper_ch for pointing out the missing -y switch.

---

### Post by gewone on 2011-01-08
It won't fly =/

I did *'sudo crontab -e'*, and filled in:
```
*00 13 * * * apt-get -y update && apt-get -y upgrade*
```Thought this would make it update/upgrade _everything_ at 1 PM every each day. Anyways, it doesn't seem to do anything.
When I manually do *'sudo apt-get upgrade'* after time has reached 1 PM, it says I still have ~hundreds of packages to upgrade.
This wouldn't be the case if it had actually performed the cron job. Right?

---

### Post by gewone on 2011-01-08
Okey, right now I'm so confuzed that I can't stand on my two feet.
My previous attempt (sudo crontab -e) did not work.
Now i tried another approach. I simply added the following line to */etc/crontab*:
```
00 13 * * * root apt-get update && apt-get -y upgrade
```
This worked! Why?
What am I missing out on with the 'sudo crontab -e' command?

--EDIT--
I now read: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
It says:

Depending on the commands being run, you may need to expand the root users PATH variable by putting the following line at the top of their crontab file:
```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
```
However. Let me add, I figured there could be PATH issues so I have actually tried filling out complete path (i.e. /usr/bin/apt-get) in root's crontab.
Still not working. The only way I got it to work was by editing /etc/crontab. Now. I'm there. I know. Anyways, I would still like to know _why_ the previous did not work.

---

