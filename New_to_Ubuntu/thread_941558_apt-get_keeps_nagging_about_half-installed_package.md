---
title: "apt-get keeps nagging about half-installed package"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by deaf_null on 2008-10-08
Hi Guys/Girls,

I installed OTRS on my Ubuntu 8.04 Hardy Server

The OTRS installer ends with this message:

[I]Creating config file /etc/apache2/conf.d/otrs2 with new version
This module does not exist!
dpkg: error processing otrs2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 otrs2
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

No problem, OTRS runs after I set my permissions right and kick
apache2 daemon, BUT, whenever I use 'apt-get' now, it ends with a
reconfigure of otrs, because it ended with an error code during
initial installation.

I did an "apt-get clean && apt-get autoclean" but still same issue after that. I wanted to install nmap, so:

***$ apt-get install nmap (last lines output)***

[I]Unpacking nmap (from .../archives/nmap_4.53-3_amd64.deb) ...
Setting up otrs2 (2.2.4-1) ...
dpkg: error processing otrs2 (--configure):
 subprocess post-installation script returned error exit status 10
Setting up nmap (4.53-3) ...

Errors were encountered while processing:
 otrs2
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]


How can I solve the issue, that whenever I use apt-get, it wants to (re)install otrs again and takes me into otrs setup screen? 

I was reading the dpkg man pages, but could not find the fix. The OTRS package seems half-installed, but working correctly, I fixed the errors by hand.

Thanks!

---

### Post by Bucky Ball on 2008-10-08
[LEFT]```
sudo dpkg --configure -a
```
That will configure any outstanding packages. 
[/LEFT]

---

### Post by deaf_null on 2008-10-08
Hi Bucky,

But I don't want to (re)configure OTRS, it will mess up my configs again and return with an error code, I'm stuck in some sort of loop.

Could you tell me which file holds this info about partly-installed packages, maybe I could manually remove it from there so apt-get/dpkg thinks OTRS is installed and configured correctly...

Cheers.

---

### Post by Bucky Ball on 2008-10-08
> **deaf_null said:**
> 
Could you tell me which file holds this info about partly-installed packages, maybe I could manually remove it from there so apt-get/dpkg thinks OTRS is installed and configured correctly...

Cheers.

Good question and one which I can't answer. Sorry. ;(

You could try opening Synaptics and that gives you a report of broken packages at bottom left from memory. Edit menu gives an option to fix them.

---

### Post by sanshaloo on 2010-03-24
The way I resolved it is to reconfigure it and select the mode which is for DB experts (non db-config option). No more nagging question from dpkg

> **Bucky Ball said:**
> Good question and one which I can't answer. Sorry. ;(

You could try opening Synaptics and that gives you a report of broken packages at bottom left from memory. Edit menu gives an option to fix them.

---

