---
title: "Beta Today"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by rosswmcgee on 2012-04-26
My upgrade still shows 12.04 as beta. I thought today 4/26/2012 was the 

final date? 0732 pacific day light time.

---

### Post by ptn107 on 2012-04-26
So you're running 11.10 and 12.04 LTS doesn't show up in the update manager?

---

### Post by Frogs Hair on 2012-04-26
I have been beta 2 testing and this is what appears in the terminal , so I don't know why it comes up as beta. 12.04 is displayed as the current release on the Ubuntu website also. ```
 cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
```

---

### Post by ptn107 on 2012-04-26
You have the final release.  Congrats.

Do a
```
sudo apt-get update && sudo apt-get upgrade
```
to check for any updates.

---

### Post by rosswmcgee on 2012-04-26
Yes 11.10 I go Altf2  it says new ubuntu release 12.04 lts is available,


Welcome to the Ubuntu 'Precise Pangolin' development release =

''This is still a BETA release.''
''Do not install it on production machines.''

Thanks for your interest in this development release of Ubuntu.
The Ubuntu developers are moving very quickly to bring you the
absolute latest and greatest software the Open Source Community has to
offer. This development release brings you a taste of the newest features
for the next version of Ubuntu. 

== Testing ==

Please help to test this development snapshot and report problems back to the
developers.  For more information about testing Ubuntu, please read:

  [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)


== Reporting Bugs ==

This development release of Ubuntu contains bugs. If you want to help
out with bugs, the Bug Squad is always looking for help. Please read the
following information about reporting bugs:

  [http://help.ubuntu.com/community/ReportingBugs](http://help.ubuntu.com/community/ReportingBugs)

Then report bugs using apport in Ubuntu.  For example:

  ubuntu-bug linux

will open a bug report in Launchpad regarding the linux package. Your 
comments, bug reports, patches and suggestions will help fix bugs and improve
future releases. 


== Participate in Ubuntu ==

If you would like to help shape Ubuntu, take a look at the list of
ways you can participate at

---

### Post by ptn107 on 2012-04-26
12.04 LTS is no longer in beta.  The 12.04 LTS official release announcement was made [1].  The text in the update manager must not be changed yet.  It is safe to upgrade just make a backup first.

[1] [https://lists.ubuntu.com/archives/ubuntu-announce/2012-April/000159.html](https://lists.ubuntu.com/archives/ubuntu-announce/2012-April/000159.html)

---

### Post by rosswmcgee on 2012-04-26
Thanks will do!

---

