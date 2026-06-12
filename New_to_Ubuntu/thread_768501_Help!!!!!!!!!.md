---
title: "Help!!!!!!!!!"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by radiopirate on 2008-04-26
now Hardy is out same problem as last time the upgrade works as far as preparing to download and stops there i have tried this for several hours leaving it on to see if it moves nothing.
we downloaded the disk it wont install from that so we tried a ssh into the computer from my wifes machine running debian told it to do a dist upgrade 
this was the result 
0 to install 0 to upgrade 0 to remove 
yet the version is running is still Gutsy 7.10 and via ssh we can see the package differances. 
i dont want to do a compleat reinstall unless absolutely necessary.
i am new to linux but my wife has run Debian for several years.

---

### Post by pro003 on 2008-04-26
if you're still able to run 7.10 than try typing in your terminal:

```
sudo apt-get dist-upgrade
```

---

### Post by billgoldberg on 2008-04-26
> **radiopirate said:**
> now Hardy is out same problem as last time the upgrade works as far as preparing to download and stops there i have tried this for several hours leaving it on to see if it moves nothing.
we downloaded the disk it wont install from that so we tried a ssh into the computer from my wifes machine running debian told it to do a dist upgrade 
this was the result 
0 to install 0 to upgrade 0 to remove 
yet the version is running is still Gutsy 7.10 and via ssh we can see the package differances. 
i dont want to do a compleat reinstall unless absolutely necessary.
i am new to linux but my wife has run Debian for several years.

What do you mean it won't install from disk?

Try booting the live cd in "safe graphics settings" or something like that.

Or use the alternate cd to install hardy heron.

(back up your data !)

Updating an OS isn't really advised.

---

### Post by radiopirate on 2008-04-26
same result
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. the full log reads
reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by ghost_ryder35 on 2008-04-26
> **pro003 said:**
> if you're still able to run 7.10 than try typing in your terminal:
 
```
sudo apt-get dist-upgrade
```
 
he said he did that
 
[quote=radiopirate] 
[SIZE=1]now Hardy is out same problem as last time the upgrade works as far as preparing to download and stops there i have tried this for several hours leaving it on to see if it moves nothing.[/SIZE]
[SIZE=1]we downloaded the disk it wont install from that so we tried a **ssh into the computer from my wifes machine running debian told it to do a _[COLOR=red]dist upgrade[/COLOR]_ **[/SIZE]
**[SIZE=1]this was the result [/SIZE]**
**[SIZE=1]0 to install 0 to upgrade 0 to remove[/SIZE]**
[SIZE=1]yet the version is running is still Gutsy 7.10 and via ssh we can see the package differances. [/SIZE]
[SIZE=1]i dont want to do a compleat reinstall unless absolutely necessary.[/SIZE]
[SIZE=1]i am new to linux but my wife has run Debian for several years. [/SIZE]
[/quote]
I would suggest running
```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```
To make sure the system is 100% updated before trying to apply the distribution upgrade.
Then
```

sudo apt-get dist-upgrade

```
 
If all else failes
 
```

cd /home/YOURACCOUNT
sudo tar -cjvf /media/BACKUPDRIVE/homebackup.tar.bz2 *

```
 
then do a fresh install

---

### Post by SunnyRabbiera on 2008-04-26
also be advised the servers are cooking right now so they might be slow

---

### Post by pro003 on 2008-04-26
> **SunnyRabbiera said:**
> also be advised the servers are cooking right now so they might be slow


yea, you got that right... yesterday I could not reload repositories in synaptic, but it helped me to change a server by selecting 

...software sources => ubuntu software => download from => other => select best server

as for upgrading I also disagree.. it's better to do a fresh install.

---

### Post by radiopirate on 2008-04-26
i thank you all for your responce we think we got it the only way to do is to edit 
/etc/apt/sources.list 
and change each occurrence of gutsy to hardy

---

