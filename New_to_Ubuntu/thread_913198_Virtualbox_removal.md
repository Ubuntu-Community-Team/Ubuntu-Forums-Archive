---
title: "Virtualbox removal"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by msayed2004 on 2008-09-07
Hi everybody;

Yesterday I added the new VBox repository to my sources.list then in Synaptic I reloaded my package list and asked Synaptic to remove the old VBox (installed from a manually downloaded package - I guess version 1.6.2) and to install version 2.

After that I saw the old VBox under the [Not Installed (residual config)] category in Synaptic, trying to remove it completely I get this error :

[CENTER][COLOR=Red]E: virtualbox: subprocess post-removal script returned error exit status 1[/COLOR]
[/CENTER]

Any ideas ?!

---

### Post by Xiong Chiamiov on 2008-09-07
Could you please try removing the package with apt-get and telling us what it says?
```

sudo apt-get remove [package name]

```

---

### Post by msayed2004 on 2008-09-07
Thanks for your reply :D .
For [COLOR=Blue]sudo apt-get remove virtualbox[/COLOR] & [COLOR=Blue]sudo apt-get remove --purge virtualbox[/COLOR]:```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```Remember that I asked Synaptic to remove the old version.

---

### Post by benerivo on 2008-09-07
A long while back i had the same problem with another package. From memory i think it was solved by removing all instances of it, and then clearing the residual config, and then reinstalling (all in synaptic).

Maybe you could try a command line force such as```
dpkg --purge --force-all PACKAGENAME
```although i would consider this rather extreme for this situation.

---

### Post by msayed2004 on 2008-09-07
Thanks> **benerivo said:**
> A long while back i had the same problem with another package. From memory i think it was solved by removing all instances of it, and then clearing the residual config, and then reinstalling (all in synaptic).

Maybe you could try a command line force such as```
dpkg --purge --force-all PACKAGENAME
```although i would consider this rather extreme for this situation.
```
(Reading database ... 180829 files and directories currently installed.)
Removing virtualbox ...
Purging configuration files for virtualbox ...
update-rc.d: /etc/init.d/vboxdrv exists during rc.d purge (use -f to force)
dpkg: error processing virtualbox (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 virtualbox
```Regarding the> use -f to forceI think [COLOR=Blue]f[/COLOR] will not force as it is equivalent to field !

---

### Post by forger on 2008-09-07
To completely remove it, try this:
```
sudo update-rc.d -f vboxdrv remove
sudo dpkg --purge --force-all virtualbox
```

---

### Post by msayed2004 on 2008-09-07
Thanks.```
(Reading database ... 180829 files and directories currently installed.)
Removing virtualbox ...
Purging configuration files for virtualbox ...
update-rc.d: /etc/init.d/vboxdrv exists during rc.d purge (use -f to force)
dpkg: error processing virtualbox (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 virtualbox
```Again!

---

### Post by forger on 2008-09-08
hrm.. do this:
```

sudo /etc/init.d/vboxdrv stop
sudo rm -rf /etc/init.d/vboxdrv

```

and then do the the dpkg command from above

---

