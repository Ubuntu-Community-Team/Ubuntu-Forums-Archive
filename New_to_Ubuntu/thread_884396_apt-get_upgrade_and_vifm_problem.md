---
title: "apt-get upgrade and vifm problem"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by scuba123 on 2008-08-09
Hi everyone,

I just ran command "sudo apt-get update" and then "sudo apt-get upgrade". I received the following error message:

 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up vifm (0.3-2) ...
dpkg: error processing vifm (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vifm
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help. Thank you.

---

### Post by scuba123 on 2008-08-09
I completely removed vifm from synaptic package manager. My "sudo apt-get upgrade" is now back to normal. Thank you.

---

