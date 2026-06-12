---
title: "extras.ubuntu.com/ubuntu raring Release' does not have a Release file"
date: 2017-10-13
forum: New to Ubuntu
---

### Post by langendoerfer on 2017-10-13
Hello all, i'm new to linux and am having an issue with apt-get update, it doesn't appear to be updating due to the error listed below:


W: The repository 'http://extras.ubuntu.com/ubuntu raring Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources)  404  Not Found [IP: 91.189.92.152 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

I've seen people with similar issues with ppa's but the solutions don't quite seem to apply to my problem. I'd appreciate any pointers on resolving this issue.
Thanks!

Samsung 700z5a
Intel® Core™ i7-2675QM CPU @ 2.20GHz × 8 
Ubuntu 16.04.3 LTS 64-bit

---

### Post by Frogs Hair on 2017-10-13
Hello and Welcome

Raring Ringtail is long out of support you can remove this source from software & updates . It may be under the other software tab.

---

### Post by langendoerfer on 2017-10-13
Thanks for the quick response! On Ubuntu gnome i'm not finding anything listed pertaining to 'raring' in software & updates or the software manager. If it's ignoring updates from a previous distro then I suppose it's just more of an annoyance than a problem.

---

### Post by deadflowr on 2017-10-13
I believe it's marked as Independent in Other Software in software and updates.

But for peace of mind, it would be best to post the output for the sources list file
either open gedit and go to Computer > etc > apt > sources.list
from a terminal run either
```
cat /etc/apt/sources.list
or
gedit /etc/apt/sources.list
```
then copy the output and paste it into a new post in this thread.

*Use code tags
(To use code tags click on the Reply to Thread Button, then in the new window click on the # symbol and paste the output in between the two code brackets
[noparse]```
 output-from-/etc/apt/sources.list-goes-here
```[/noparse]

---

### Post by langendoerfer on 2017-10-13
Here's the output:

[COLOR=#000000]```
 [/COLOR]

cat /etc/apt/sources.list


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main

```

---

### Post by ajgreeny on 2017-10-13
There it is! The final two lines at the bottom of the file.

Delete those two bottom lines with ```
sudo -H gedit /etc/apt/sources.list
``` or whatever text editor you use and then refresh the sources again with ```
sudo apt update
```

---

### Post by langendoerfer on 2017-10-13
Success! Thanks for the help everyone.

---

### Post by ajgreeny on 2017-10-14
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

