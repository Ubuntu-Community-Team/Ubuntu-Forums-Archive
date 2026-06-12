---
title: "Errors Encouter while Update"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by skhozema on 2013-04-06
Hi

I am new to Ubuntu and giving try for new OS besides upgrading to Windows8. Using Ubuntu for last one month, everyday i am learning something new and different in operating the same. My question, as the system is schedule for daily update which its doing so, but after every installation i get this message as below: I am confuse whether this  update is happening or aborted:- 


Errors were encountered while processing: 
 qmail 
Setting up qmail (1.06-4) ... 
 
The hostname -f command returned: $1 
 
Your system needs to have a fully qualified domain name (fqdn) in 
order to install the var-qmail packages. 
 
Installation aborted

---

### Post by ibjsb4 on 2013-04-06
Why are you trying to install qmail?

How are you trying to update?

```
sudo apt-get update
```

---

### Post by skhozema on 2013-04-06
Hi, 
I have not installed qmail. The systems itself by default checks for updates during end of this process i get the error message. As it hapen always i just read errror which always highlight about this qmail.

---

### Post by ibjsb4 on 2013-04-06
Qmail is not part of the default install so lets see if it can be removed.

```
sudo apt-get remove --purge qmail && sudo apt-get update
```

---

### Post by skhozema on 2013-04-07
I did  as instructed but

khozema@ubuntu:~$ sudo apt-get remove --purge qmail
[sudo] password for khozema: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  qmail*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,097 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 234271 files and directories currently installed.)
Removing qmail ...
rmdir: failed to remove `/var/lib/qmail/queue': Directory not empty
rmdir: failed to remove `/var/lib/qmail': Directory not empty
Purging configuration files for qmail ...
rmdir: failed to remove `/var/lib/qmail/queue': Directory not empty
rmdir: failed to remove `/var/lib/qmail': Directory not empty
rm: cannot remove `/etc/qmail/qmail-send': Is a directory
rm: cannot remove `/etc/qmail/qmail-smtpd': Is a directory
rm: cannot remove `/etc/qmail/qmail-verify': Is a directory
dpkg: error processing qmail (--purge):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for man-db ...
Errors were encountered while processing:
 qmail
E: Sub-process /usr/bin/dpkg returned an error code (1)


Also for updatting i got this :

W: GPG error: [http://apt.insynchq.com](http://apt.insynchq.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 06BBDC2602DFE7E7

---

### Post by ibjsb4 on 2013-04-07
To fix that GPG error; in terminal enter:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 06BBDC2602DFE7E7
```

Now for qmail.  If this was my system, I would remove those directories.  It looks like a low risk move.  But I am fully backed up so if things go south, I can restore.  Having never installed qmail I cannot be 100% certain of what will happen.  So if you can afford to take a chance, open a terminal and ..

```
gksudo nautilus
```

Then do a search on qmail and remove everything you find.

If your not feeling lucky :) give this thread a while and see if someone else will comes along that can verify these things about qmail.

---

### Post by skhozema on 2013-04-07
Thxs buddy :)
i did as instructed: got this

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.LNiyJLdSy7 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 06BBDC2602DFE7E7
gpg: requesting key 02DFE7E7 from hkp server keyserver.ubuntu.com
gpg: key ACCAF35C: public key "Insynchq Inc <services@insynchq.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

---

### Post by gnugen on 2013-04-10
If you have synaptic package manager, you should be able to remove the qmail package that has been downloaded.

---

### Post by skhozema on 2013-04-12
yes i have, but i am not getting along its usage hence worried other important files/packages if got removed besides qmail.

---

