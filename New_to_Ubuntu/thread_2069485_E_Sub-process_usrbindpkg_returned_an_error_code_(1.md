---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by chacank on 2012-10-10
hi all ....
I have a problem every run update & upgrade in terminal ..
always appears an error message and i dont know the meaning of this result ::

```
chacank@biters:~$ sudo apt-fast install ubuntu-restricted-extras
[sudo] password for chacank: 
 
 Working... this may take a while.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up capiutils (1:3.12.20071127-0ubuntu11) ...
Note: running MAKEDEV to create CAPI devices in /dev...
mount: unknown filesystem type 'capifs'
invoke-rc.d: initscript capiutils, action "start" failed.
dpkg: error processing capiutils (--configure):
 subprocess installed post-installation script returned error exit status 32
dpkg: dependency problems prevent configuration of capi4hylafax:
 capi4hylafax depends on capiutils; however:
  Package capiutils is not configured yet.
dpkg: error processing capi4hylafax (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of isdnactivecards:
 isdnactivecards depends on capiutils (>= 1:3.12.20071127-0ubuntu11); however:
  Package capiutils is not configured yet.
dpkg: error processing isdnactivecards (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                           No apport report written because the error  message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 capiutils
 capi4hylafax
 isdnactivecards
E: Sub-process /usr/bin/dpkg returned an error code (1)
chacank@biters:~$
```

please help me to fix it .. [-o<
thanks ..

---

### Post by drpjkurian on 2012-10-11
Hi
open a terminal and do the following commands one by one

```
sudo apt-get purge isdnactivecards capiutils
sudo apt-get autoremove
``` above commands remove the conflicting packages

then try the following commands in terminal
```
sudo apt-get --fix-broken install
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by chacank on 2012-10-11
thanks for your help .... my problem solved now .. ^__^

---

### Post by drpjkurian on 2012-10-11
you are most welcome.

---

