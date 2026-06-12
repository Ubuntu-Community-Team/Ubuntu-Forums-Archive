---
title: "W: Duplicate sources.list entry http://archive.canonical.com hardy/partner"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by allblacks on 2008-10-15
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages)
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

this is the problem that i have and i have tried everything that i found on forums and it did not fix it

---

### Post by SunnyRabbiera on 2008-10-15
even sudo apt-get update?

---

### Post by drs305 on 2008-10-15
At least part of the problem is with a typo, probably from Ultamatix.

Open sources.list and replace any instance of '***harty*** with 'harty'.
```
/repoubuntusoftware.info_dists_***harty***_all_binary-i386_Packages
```

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksudo gedit /etc/apt/sources.list

```

You may have a line repeated. Remove or comment out one of them if that is the case.

Save the file and reload the repositories.

---

### Post by Kevbert on 2008-10-15
Please post your sources.list
There has been a problem with harty hotrod as the servers have recently been changed (this may have something to do with your problem).

---

### Post by hndaklr8480 on 2008-10-31
hey folks, I am trying to enable the Medibuntu repository on my computer and get a similar error:

W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_spring_ubuntu_dists_hardy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

then I try to do as it tells me and then it tells

W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_spring_ubuntu_dists_hardy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
hmmmmmm?

---

### Post by kostkon on 2008-11-01
> **hndaklr8480 said:**
> hey folks, I am trying to enable the Medibuntu repository on my computer and get a similar error:

W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_spring_ubuntu_dists_hardy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

then I try to do as it tells me and then it tells

W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_spring_ubuntu_dists_hardy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
hmmmmmm?
If you run *Software Sources* (*System -> Administration -> Software Sources*) do you see any duplicate entries of one of your repos in the *Third-Party Software* tab. If you do, then remove the one of the duplicate entries, press *Close* and then *Reload*.

If not, the could you post here the contents of your *sources.list* file? You can access its contents, by opening a terminal (*Applications -> Accessories -> Terminal*) and giving:
```
gedit /etc/apt/sources.list
```

---

