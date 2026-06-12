---
title: "Show Error in terminal is Some index files failed to download.they have been ignored"
date: 2014-12-24
forum: New to Ubuntu
---

### Post by chirag_moradiya on 2014-12-24
[CENTER]when i run this command sudo apt-get update,that time after some time updating....and after it wll show  "Some index files failed to download.they have been ignored"
and display error lo below.
Failed to fetch [http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/compiz/ppa/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/kazade/tickit/ubuntu/distoks/trusty/main/source/Sources](http://ppa.launchpad.net/kazade/tickit/ubuntu/distoks/trusty/main/source/Sources)  404  Not Found
o
W: Failed to fetch [http://ppa.launchpad.net/kazade/tickit/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/kazade/tickit/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/kazade/tickit/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/kazade/tickit/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/CENTER]

---

### Post by Impavidus on 2014-12-24
Those PPAs are not available for trusty. Disable these PPAs from your software sources.

---

### Post by vasa1 on 2014-12-24
> **Impavidus said:**
> Those PPAs are not available for trusty. Disable these PPAs from your software sources.
And while you're at it, disable (untick) all the source code entries as well. Most "average" end users don't need to see the source code.

---

