---
title: "Errors were encountered while processing:  getdeb-repository"
date: 2015-02-23
forum: New to Ubuntu
---

### Post by Meet_Joshi on 2015-02-23
I am a beginner

I run this command:
meet@meet-Ideapad-Z570:~$ sudo dpkg -i getdeb-repository_0.1-1~getdeb1_all.deb

and I got result as:
[sudo] password for meet: 
(Reading database ... 176603 files and directories currently installed.)
Preparing to unpack getdeb-repository_0.1-1~getdeb1_all.deb ...
Unpacking getdeb-repository (0.1-1~getdeb1) over (0.1-1~getdeb1) ...
postrm called with unknown argument `upgrade'
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: ... it looks like that went OK
Setting up getdeb-repository (0.1-1~getdeb1) ...
--2015-02-24 03:21:22--  [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key)
Resolving archive.getdeb.net (archive.getdeb.net)... 144.76.200.19
Connecting to archive.getdeb.net (archive.getdeb.net)|144.76.200.19|:80... failed: Connection refused.
gpg: no valid OpenPGP data found.
dpkg: error processing package getdeb-repository (--install):
 subprocess installed post-installation script returned error exit status 2
[B]Errors were encountered while processing:
 getdeb-repository[/B]

How to resolve the issue?

---

### Post by ian-weisser on 2015-02-23
> **Meet_Joshi said:**
> 
Resolving archive.getdeb.net (archive.getdeb.net)... **144.76.200.19**
Connecting to archive.getdeb.net (archive.getdeb.net)|144.76.200.19|:80... **failed: Connection refused**.
gpg: no valid OpenPGP data found.
dpkg: error processing package getdeb-repository (--install):
 

Test that IP address to ensure it's up.
Then try installing again.

---

