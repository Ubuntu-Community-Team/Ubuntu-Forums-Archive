---
title: "[SOLVED] Fail to update some repositories"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by emwaiz on 2008-10-08
Hi! I'm using  Ubuntu 8.04 - the Hardy Heron. The problem is that when I try to update my software sources, this error messages came in;

 " [I]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://repository.salutis.sk/production/./Packages.gz](http://repository.salutis.sk/production/./Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/I]"

It's very irratating. Could someone help me? TQ!

---

### Post by Sef on 2008-10-08
1) Moved to absolute beginners.

2) Try again later or change where the location of where to download from.  System > Administration > Software Sources > Download

---

### Post by Paqman on 2008-10-08
> **Sef said:**
> 
2) Try again later or change where the location of where to download from.  System > Administration > Software Sources > Download

The "Select best server" button there is very cool, too. That should sort you out.

---

### Post by uberdonkey5 on 2008-10-08
If the above don't work:

1. consider that the repository actually has a problem (though this is not usually the case with the main repositories)

2. Also, are you using a proxy server (e.g. at work)? Even if you have configured it for firefox, you need to configure proxy for synaptic package manager. 
If this is the case go into system, control centre, network proxy (if control centre isn't in your system menu, use system, preferences, main menu to select control centre as active in menu system). Type in settings for the proxy, and try again. (if other repositories are working this is NOT the case).

---

