---
title: "Problem with up dates &quot;Could not download all repository indexes&quot;"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by math303 on 2012-12-04
Hello , first of all I am new to Ubuntu and last  week I got a message from synaptic package manager to said they was up date available , so I updated my Ubuntu and now I have this message and I don t really know how to fix this , so if anyone can help that will be great , keep in mind I am new to Linux so if you can explain step by step that will be appreciate .
this is the problem from:
synaptic package manager :**Could not download all repository indexes**

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

[B]Failed to fetch [http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/dists/precise/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead[/B].

well that the message I get and to be honest it s does not really help me but to tried to fix it , I hope one of you can make something of this .
thank you for your help

---

### Post by Krytarik on 2012-12-04
> **math303 said:**
> [B]Failed to fetch [http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/dists/precise/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead[/B].
There are no packages for Precise 12.04 available in that PPA, you can check that here also:[INDENT][https://launchpad.net/~tldm217/+archive/tahutek.net](https://launchpad.net/~tldm217/+archive/tahutek.net)[/INDENT]So just remove it from your Software Sources, sticking with Synaptic, via "Settings -> Repositories".

Regards.

---

### Post by math303 on 2012-12-04
thanks  for your help really appreciate.

---

