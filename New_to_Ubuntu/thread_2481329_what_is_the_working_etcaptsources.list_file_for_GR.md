---
title: "what is the working /etc/apt/sources.list file for GROOVY Ubuntu ?"
date: 2022-11-26
forum: New to Ubuntu
---

### Post by patrick2957672 on 2022-11-26
Hello

apt-get update  does not work.

root@user-E202SA:/home/user# uname -a
Linux user-E202SA 5.8.0-25-generic #26-Ubuntu SMP Thu Oct 15 10:30:38 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


Please would you have a working /etc/apt/sources.list file, which is for ubuntu groovy amd64 ?

Regards

---

### Post by ajgreeny on 2022-11-26
Your problem is that Groovy Gorilla is no longer a supported version.

Ubuntu and its other DE versions are released in two different support types, those in April of the even number years are supported for either 5 or 3 years; if you use Ubuntu it is 5 yrs, if the other DE versions just 3 yrs.
Other numbered versions, eg, 20.10 (Groovy), 21.04, 21.10 are supported for only 9 months so your groovy version lost any further updates in July 2021.

For safety of yourself and other users on the internet it is imperative that you upgrade to a supported version; I recommend you do a clean install of Jammy (22.04) as soon as you can.  It will not be possible to do a release upgrade, or not easy, though you could create a bootable USB of Jammy and then install from that, reusing the same partitions you currently have but ensuring that you do not format those partitions during the install.

As you are a new Ubuntu user of Ubuntu I strongly recommend that you backup all your personal files in the home folder (or partition if you used one) and start again then restore all those personal files to the new home that is created.

---

### Post by patrick2957672 on 2022-11-26
is there a mirror of the packages on some place on the web, that is designed for groovy ?


packages list and the debs

---

### Post by tea for one on 2022-11-26
As mentioned by ajgreeny above, now is the time to backup your personal files, install a supported release (Ubuntu 22.04 LTS) and restore your data.
This is the best solution.

There may well be some place on the web where you can find unsupported Groovy packages but you could only upgrade to 21.04, which is also unsupported since January 2022?

---

### Post by deadflowr on 2022-11-26
Groovy's repos were moved into the old-releases.ubuntu.com archives, so replace the current url with that.
As explained here: [https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

We have no need to help you as far as dealing with issues running groovy, it's a waste of everyone's time.
But we will help you try to install or upgrade to a supported release.
I guess that's putting it bluntly.

---

### Post by grahammechanical on 2022-11-27
I would like to add that once the repositories (sources) of a Ubuntu version are moved to the old-releases.ubuntu.com archives the packages in those repositories are no longer updated with security fixes. 

Regards

---

