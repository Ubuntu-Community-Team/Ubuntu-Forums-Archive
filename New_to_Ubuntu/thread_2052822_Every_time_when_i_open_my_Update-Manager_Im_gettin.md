---
title: "Every time when i open my Update-Manager Im getting this error...please fix this"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by munvar on 2012-09-04
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/www.bashterritory.com_pytube_releases_en, E:The package lists or status file could not be parsed or opened.'

---

### Post by marlow59 on 2012-09-04
This is a well know bug, I personally attached my Launchpad account to it and follow the evolution of the bug, and a lot of people are still experiencing it.
 Anyway, open a terminal and run

```
sudo apt-get clean

sudo rm /var/lib/apt/lists/*

sudo rm /var/lib/apt/lists/partial/*

sudo apt-get clean

sudo apt-get update
```

normally this have worked for a lot of people whom have reported the bug. repost here if you have any other issue.

---

### Post by munvar on 2012-09-04
W: GPG error: [http://www.bashterritory.com](http://www.bashterritory.com)  InRelease: File /var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_InRelease doesn't start with a clearsigned message
W: Failed to fetch gzip:/var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_Packages  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by raja.genupula on 2012-09-04
open update manager -> settings -> from 1st TAB at download from choose best server/main server .

then update again . 

while coming to GPS issue use this

```
sudo rm -rf /var/lib/apt/lists/partial/www.bashterritory.com_pytube_releases_InRelease
```

Then try again .

---

