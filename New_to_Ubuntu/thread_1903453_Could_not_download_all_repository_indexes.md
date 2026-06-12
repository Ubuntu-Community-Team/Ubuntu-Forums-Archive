---
title: "Could not download all repository indexes"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by sharmaneha on 2012-01-02
I am using Ubuntu 10.04 I get the following error when I try to update. 

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/nathan-renniewaldock/xmbc-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/nathan-renniewaldock/xmbc-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/tean-xbmc/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/tean-xbmc/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I read some posts with similar problems but it didn't help much and I am stuck. Any help would be appreciated.

---

### Post by audiomick on 2012-01-02
Has this been going on for a while? It is not a temporary server problem for just those ppa's , is it?

---

### Post by spacecheck on 2012-01-02
> **sharmaneha said:**
> I am using Ubuntu 10.04 I get the following error when I try to update. 

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/nathan-renniewaldock/xmbc-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/nathan-renniewaldock/xmbc-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/tean-xbmc/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/tean-xbmc/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I read some posts with similar problems but it didn't help much and I am stuck. Any help would be appreciated.

Why not close any package managers and use the terminal to run gksudo edit then  open /etc/apt/sources.list and put a hash mark # in front of  the offending source, for example:

# deb http://ppa.launchpad.net/nathan-renniewaldock/xmbc-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz
and

# deb http://ppa.launchpad.net/tean-xbmc/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz

then save the file & try a sudo apt-get update

Good luck!

---

### Post by sharmaneha on 2012-01-02
> **audiomick said:**
> Has this been going on for a while? It is not a temporary server problem for just those ppa's , is it?

Actually this has been going on for a while.

---

### Post by sharmaneha on 2012-01-02
The problem got solved when I edited sources.list file. Thank you spacecheck and audiomick too.
Have a nice day

---

### Post by spacecheck on 2012-01-02
You're quite welcome. You may also wish to review the following thread:

[http://ubuntuforums.org/showthread.php?t=1737599&highlight=xbmc](http://ubuntuforums.org/showthread.php?t=1737599&highlight=xbmc) 

Best wishes!

---

