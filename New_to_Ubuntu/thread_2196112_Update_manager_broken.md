---
title: "Update manager broken"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by writersandscriptwr on 2013-12-27
Hi.... I have been an Ubuntu user for about 5 years now, and love the  flavour of distro. The community are excellent also. I have a problem. I  recently had to reinstall my firefox, as it became broken for some  reason. I looked to add sopcast to the apps that work through firefox,  and linked a source to my repository list, that has consequently caused a  fatal error. I cannot seem to access the repository list to remove the  source, either through update manager, synaptic, or the software  centre... all of which crash before being able to enter the repository  list to fix the problem. This is the message I receive:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ferramroberto-sopcast-precise.list'

Could someone help with fixing this please.... as I would like to access  the repository list to remove the offending source, and then update my  distro. I'm using the LTS 12.04 at present on a toshiba laptop... and i  have to say it works perfectly for my needs. just need to iron out this  problem and am a little stuck for ideas. many Thanks.

---

### Post by ptn107 on 2013-12-27
From the terminal you can remove the offending source before attempting to update:
```
sudo rm /etc/apt/sources.list.d/ferramroberto-sopcast-precise.list
```
then
```
sudo apt-get update
```

---

### Post by writersandscriptwr on 2013-12-28
that was perfect PTN!... thank you very much! :KS

---

### Post by claracc on 2013-12-28
In order to mark the thread as solved (to help others), please follow the steps provided in this link:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Thanks

---

