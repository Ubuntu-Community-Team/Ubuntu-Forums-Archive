---
title: "Creating a home samba/nas server"
date: 2014-10-25
forum: New to Ubuntu
---

### Post by lawrence9 on 2014-10-25
Hi there , newbie here. Apologies if this has even been covered before.

My situation : Dell Poweredge 850 running Ubuntu Server 14.04 with Samba, Apache, LAMP, SSH and Webmin installed.

Have set up a three user folders in root directory 'USER 1' 'USER 2' & 'USER 3', each set with their own username/passwords.

Connecting to the server via local IP works fine and am able to access each folder respectively.

When trying to access the server remotely via WAN IP this also seems ok. HTTP pages served ok.

Here is the problem : When accessing via WAN IP, I only get access to a folder named 'public', which doesn't exist on my machine, have checked using the FIND command.

Can someone help please ??

---

### Post by TheFu on 2014-10-25
Start here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - free PDF book, no hassle download.

You'll find that having spaces in directory names is a hassle. Also, creating multiple directories in the / (root) file system is normally not done.  If you just want client machines to have access to storage, then doing that on a per-user basis inside each users HOME is normally the best way.

Can't begin to help with the information provided.
* do the userids exist?
* what is the HOME for each?
* has samba been configured for each userid?  smbpasswd set? Samba access is odd compared to all other ways.
* access via ssh is different from access via CIFS shares.  
* web access is highly specialized. No user accounts are used.

Sorry, if you know these things already. Take a look at that book - skim the fist 100 pgs to get some background. I think it will save you hours, days, weeks of frustration.

---

