---
title: "Synaptic package manager wont start"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by CeltWolf13 on 2008-07-07
I was trying to install java 6 through synaptic, but it froze up, so i rebooted.  when i tried to run synaptic, I get this message:E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I ran the dpkg --configure -a and i got this message:

dpkg: dependency problems prevent configuration of sun-java6-fonts:
 sun-java6-fonts depends on sun-java6-jre (>= 6-06-0ubuntu1); however:
  Package sun-java6-jre is not installed.
dpkg: error processing sun-java6-fonts (--configure):
 dependency problems - leaving unconfigured
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

I had to type no after several attempts
The add or remove programs wont come up either and i get :

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

When i run the update, i get the message:

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) isalready running. Please close that application first.

I dont even have any other things up in my workspaces!!!

Please help me install java 6 AND get synaptic working again! Thanks a million.:confused:

---

### Post by Darkade on 2008-07-07
There's a quick workaround, however, it may or may not work.
Just try rebooting and select to boot into recovery mode, and when asked select fix broken packages.

---

### Post by bumanie on 2008-07-07
You need to run > sudo dpkg --reconfigure -a The download should start from where it was interrupted.

---

### Post by Darkade on 2008-07-07
> You need to run
Quote:
sudo dpkg --reconfigure -a
The download should start from where it was interrupted.


> **CeltWolf13 said:**
> 
I ran the dpkg --configure -a and i got this message:




He already ran dpkg --configure -a

I think it might help running
```
sudo apt-get install sun-java6-jre
```

P.S: BTW I loved your sign bumanie LOL

---

### Post by philinux on 2008-07-07
Although it says run dpkg --configure -a, this is a very helpful message but it must be run with root privileges.

Hence

sudo dpkg --configure -a

---

### Post by cariboo on 2008-07-07
There is more than likely a lock file in /var/lib/dpkg. Remove the lock and everything should be OK.

Jim

---

