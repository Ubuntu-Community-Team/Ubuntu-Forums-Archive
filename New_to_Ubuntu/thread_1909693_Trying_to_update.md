---
title: "Trying to update"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by eduardo saxel on 2012-01-15
I have a red warning sign on top, beside the calendar, and says:
"The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by clicking on this icon and then selecting 'Check for updates' and check if some of the listed repositories fail."

And this is what I get when checking for updates : 

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/amsn-developers/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/amsn-developers/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/evolution-developers/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/evolution-developers/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by lechien73 on 2012-01-15
It appears as if both of those repositories have been removed from Launchpad.

So, you can remove the repositories from your sources by opening a terminal window and typing:

```
sudo add-apt-repository remove ppa:evolution-developers
sudo add-apt-repository remove ppa:amsn-developers
sudo apt-get update

```

Then try your updates again :)

---

### Post by eduardo saxel on 2012-01-15
And I got this:

bastien@bastien:~$ sudo add-apt-repository remove ppa:evolution-developers
[sudo] password for bastien: 
Error: need a repository as argument
bastien@bastien:~$ sudo add-apt-repository remove ppa:amsn-developers
Error: need a repository as argument
bastien@bastien:~$ ^C
bastien@bastien:~$

---

### Post by lechien73 on 2012-01-15
Sorry...typo, should have been:

```
sudo add-apt-repository --remove ppa:evolution-developers
sudo add-apt-repository --remove ppa:amsn-developers
sudo apt-get update
```

Hope that works :)

If not, then open the **Software Center**, click the **Edit** menu and choose **Software Sources**

Then click the **Other Software** tab and uncheck the two problem repositories.

---

