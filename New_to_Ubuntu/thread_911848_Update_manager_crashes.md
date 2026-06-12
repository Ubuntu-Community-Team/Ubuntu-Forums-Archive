---
title: "Update manager crashes"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by amelie on 2008-09-06
I've lacked internet for months and now there are about 300 updates and even if I try to update partly nothing happens and I also can't open Synaptic... Please, tell me what's going on :confused:

---

### Post by iaculallad on 2008-09-06
> **amelie said:**
> I've lacked internet for months and now there are about 300 updates and even if I try to update partly nothing happens and I also can't open Synaptic... Please, tell me what's going on :confused:

What happens if you issue the commands below on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by amelie on 2008-09-06
The first: Some index fails failed to download, they have been ignored, or old ones used instead
The other thing started upgrading and 5 minutes left to finish...
Hey, how much time do you guys spent while getting used to run everything through terminal ;) It's very handy :):):)

---

### Post by iaculallad on 2008-09-06
> **amelie said:**
> The first: Some index fails failed to download, they have been ignored, or old ones used instead
The other thing started upgrading and 5 minutes left to finish...
Hey, how much time do you guys spent while getting used to run everything through terminal ;) It's very handy :):):)

That would be good, at least it responds with the update and upgrade. On your terminal again,try:

```
gksudo update-manager
```

If it will launch the Update Manager.

EDIT: If the above suggestion does not still pop the Update Manager, try this:

```
cd ~/.update-manager-core
mv meta-release meta-release.backup
gedit meta-release
```

After the gedit meta-release command, select all the texts inside the file and delete it, replacing it with the text below:

> Dist: feisty
Name: Feisty Fawn
Version: 7.04
Date: Thu, 19 Apr 2007 13:00:00 +0200
Supported: 1
Description: This is the 7.04 release
Release-File: [http://archive.ubuntu.com/ubuntu/dists/feisty/Release](http://archive.ubuntu.com/ubuntu/dists/feisty/Release)
ReleaseNotes: [http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement)
UpgradeTool: [http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz)
UpgradeToolSignature: [http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz.gpg)

Dist: gutsy
Name: Gutsy Gibbon
Version: 7.10
Date: Thu, 18 Oct 2007 12:00:00 UTC
Supported: 1
Description: This is the 7.10 release
Release-File: [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release)
ReleaseNotes: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/ReleaseAnnouncement)
UpgradeTool: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz)
UpgradeToolSignature: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg)

Dist: hardy
Name: Hardy Heron
Version: 8.04 LTS
Date: Thu, 24 Apr 2008 12:00:00 UTC
Supported: 1
Description: This is the 8.04 LTS release
Release-File: [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)
ReleaseNotes: [http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/ReleaseAnnouncement)
UpgradeTool: [http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/hardy.tar.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/hardy.tar.gz)
UpgradeToolSignature: [http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/hardy.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/main/dist-upgrader-all/current/hardy.tar.gz.gpg)

Save and Close. And on your terminal again:

```
sudo apt-get update
```

and afterwards, try accessing the Update Manager again.

---

### Post by amelie on 2008-09-06
Well, the it asked me to restart and then when clicking on available updates it started itself alone :)
Thanks a lot - you're a great pro !!!!

---

