---
title: "confusion to install software......."
date: 2016-11-24
forum: New to Ubuntu
---

### Post by hasan5599 on 2016-11-24
hello helpful guys....................

I am new in Ubuntu and installed 16.04.1 LTS now it's running good but a problem seems appear . A notification comes to my window [COLOR=#ff0000]"Update software has been issued since Ubuntu 16.04 was released. Do you want to install it now[/COLOR]" and then I close my window and gave these 2 command to up-to-date my system

apt-get update && apt-get upgrade and my terminal return


[COLOR=#ff0000]hasan@Anaymous-Pc:~$ sudo su -[/COLOR]
[sudo] password for hasan: 
[COLOR=#ff0000]root@Anaymous-Pc:~# apt-get update[/COLOR]
Hit:1 [http://mirror.dhakacom.com/ubuntu-archive](http://mirror.dhakacom.com/ubuntu-archive) xenial InRelease
Hit:2 [http://mirror.dhakacom.com/ubuntu-archive](http://mirror.dhakacom.com/ubuntu-archive) xenial-updates InRelease      
Hit:3 [http://mirror.dhakacom.com/ubuntu-archive](http://mirror.dhakacom.com/ubuntu-archive) xenial-security InRelease     
Reading package lists... Done
[COLOR=#ff0000]root@Anaymous-Pc:~# apt-get upgrade[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic snapd
  ubuntu-core-launcher
[COLOR=#006400] 0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.[/COLOR]
root@Anaymous-Pc:~# 

I can see any update and upgrade there everything is up-to-date  , Nothing is there to install but a notification came to update .............Please see my attachment .

What is the problem ??? Where is my update or Upgrade file ??

---

### Post by ian-weisser on 2016-11-24
Read your output again.
Your system is telling you that it is NOT up to date

> **hasan5599 said:**
> 
root@Anaymous-Pc:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
**The following packages have been kept back:**
  linux-generic linux-headers-generic linux-image-generic snapd
  ubuntu-core-launcher
0 upgraded, 0 newly installed, 0 to remove and **5 not upgrade**.

---

### Post by hasan5599 on 2016-11-24
Is this really, my system is not up-to-date ??
I don't actually understand what you are talking about ...........make it clear or elaborate your answer please....Thanks

---

### Post by ian-weisser on 2016-11-24
> **hasan5599 said:**
> Is this really, my system is not up-to-date ??

Yes, your system is NOT up to date.
Read your output. That is why you have output.

'apt upgrade' does not upgrade some system-critical packages. Use 'apt full-upgrade' for those.
See 'man apt' for a full explanation of the difference between 'upgrade' and 'full-upgrade'

---

### Post by Autodave on 2016-11-24
Run these commands.....

sudo apt-get update
sudo apt-get upgrade

---

### Post by QIII on 2016-11-24
The user did run those commands.

"apt-get" is unnecessary in 16.04.  "apt" will do.

In any case, fully upgrading is the correct approach.

---

### Post by vasa1 on 2016-11-24
I can't understand the fascination with root:```
hasan@Anaymous-Pc:~$ sudo su -
[sudo] password for hasan: 
root@Anaymous-Pc:~# apt-get update

```

---

### Post by &amp;KyT$0P# on 2016-11-24
```
sudo apt-get update
sudo apt-get [COLOR="#FF0000"]**dist-**[/COLOR]upgrade
```

---

### Post by hasan5599 on 2016-11-24
Thanks all of friends .............for your kind reply I have solved my problem this morning..............

---

### Post by wildmanne39 on 2016-11-24
Please post the solution here so the whole community will benefit from your answer.
Thanks

---

### Post by hasan5599 on 2016-11-26
When the pop up window came then I hited the install botton then everything became up to date

---

