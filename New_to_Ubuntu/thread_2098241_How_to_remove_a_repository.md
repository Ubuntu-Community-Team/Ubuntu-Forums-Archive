---
title: "How to remove a repository?"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by BelugaWail on 2012-12-26
I'm trying to update my software on Ubuntu 12.10 and every time I try I receive the following warning:

Failed to download repository information
Check your Internet connection
W:Failed to fetch [http://ppa.launchpad.net/cooperjona/...source/Sources](http://ppa.launchpad.net/cooperjona/...source/Sources) 404 Not Found
, W:Failed to fetch [http://ppa.launchpad.net/cooperjona/...-i386/Packages](http://ppa.launchpad.net/cooperjona/...-i386/Packages) 404 Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I have internet connection and I have uninstalled Stormcloud. If I remove the repository will this fix the issue?  How do I go about removing a repository?

Thanks in advance for the help.

---

### Post by ubudog on 2012-12-26
Open up "System Settings" and click on "Software Sources".  Once it opens go to the "Other Software" tab and uncheck any repos you don't want anymore.  Then hit close and open a terminal.  Type:
```
sudo apt-get update
```

PS: An alternate way of getting to Software Sources is by opening Ubuntu Software Center and clicking on Edit>Software Sources.

Hope this helps,
ubudog

---

### Post by ibjsb4 on 2012-12-26
[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by BelugaWail on 2012-12-30
> **ubudog said:**
> Open up "System Settings" and click on "Software Sources".  Once it opens go to the "Other Software" tab and uncheck any repos you don't want anymore.  Then hit close and open a terminal.  Type:
```
sudo apt-get update
```

PS: An alternate way of getting to Software Sources is by opening Ubuntu Software Center and clicking on Edit>Software Sources.

Hope this helps,
ubudog

Thanks!  This was exactly what I was looking for.

---

