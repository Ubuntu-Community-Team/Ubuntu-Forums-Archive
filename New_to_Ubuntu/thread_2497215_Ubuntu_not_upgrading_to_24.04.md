---
title: "Ubuntu not upgrading to 24.04"
date: 2024-04-27
forum: New to Ubuntu
---

### Post by filiprybar on 2024-04-27
Hello everyone, I'm trying to update my ubuntu from 23.10 to 24.04, but I get message no new release found. Idon't know why I get this error, because it's after april 25. Can you help me please?

---

### Post by Impavidus on 2024-04-27
24.04 has just been released for fresh installs. The upgrade path from the preceding release is normally opened in the next week, but delays of a few weeks are common. This is because, after the new release itself, the upgrade process must be properly debugged. The upgrade path from the preceding LTS release is normally opened after three months, to allow for additional debugging of the new LTS release. Users of LTS releases expect a stable system.

---

### Post by MAFoElffen on 2024-04-27
At this moment, if you do
```

sudo do-release-upgrade -d

```
Then it should find it.

As I remember (don't quote me), the reasoning for this, only the day of, or a few days after a release, is that the focus on testing of the Dev releases are on new installs. Once the release is released, then they bless the upgrade path, which takes about a week to sign off on that. So for about a week or so, the Release Upgrade Path" is still considered as still being in the "Development" Cycle stage. As being active as "a Tester" in Dev Cycles, I don't think "we" were ever asked to test the upgrade path itself. It's my understanding that the Canonical Developers do that themselves.

Even though I do Dev Testing in the Dev Cycles... And I have it installed natively on at least one machine here... I usually wait one or two weeks after the LTS release before upgrading my main machines and servers to that release. That gives the Dev's time to work things out for that. At least, that is what I have followed over the past 14 years with that. I know some others here, who are more cautious, and wait until the first LTS point release to upgrade theirs.

---

### Post by grahammechanical on 2024-04-27
This link gives a powerful reason not to force an upgrade to Ubuntu 24.04 LTS at the moment.

[https://www.omgubuntu.co.uk/2024/04/dont-upgrade-to-ubuntu-24-04-yet](https://www.omgubuntu.co.uk/2024/04/dont-upgrade-to-ubuntu-24-04-yet)

> Right now there are major bugs impacting direct upgrades from earlier versions. We&#8217;re talking *&#8220;your system may become unrecoverable&#8221;* type issues. Snafus stem from the switch to *Thunderbird* snap[SUP][1]("https://www.omgubuntu.co.uk/2024/04/dont-upgrade-to-ubuntu-24-04-yet#94ddbde0-2633-42e6-8360-98e861b8650e")[/SUP]  (on installs with the DEB installed upgrading to 24.04 replaces it with  the snap) and the complicated tangle of Y2028 time_t transitions[SUP][2]("https://www.omgubuntu.co.uk/2024/04/dont-upgrade-to-ubuntu-24-04-yet#1ffe46bc-7ba3-40b1-8e0c-ce8a6ecd546c")[/SUP] (anyone who used daily builds will be familiar with the pain they caused).

Regards

---

### Post by guiverc on 2024-04-28
I'll provide a link to an answer I wrote elsewhere if you want more.

[https://askubuntu.com/questions/1511602/cant-upgrade-to-kubuntu-24-04/1511642#1511642](https://askubuntu.com/questions/1511602/cant-upgrade-to-kubuntu-24-04/1511642#1511642)

It contains the link for *nobleupgrades*, why your system doesn't see the upgrade, and most importantly the release status page for checking how *safe/problematic* forcing it will be.

Ubuntu and all *flavors* use the same [Ubuntu Release Upgrader]("https://launchpad.net/ubuntu-release-upgrader") code, so the upgrade will be trigger by the same process I *vagely* cover in my answer (*the question related to Kubuntu - but it applies to Ubuntu Desktop/Server & all flavors*).

---

### Post by regs4 on 2024-05-13
tried to upgrade with -d, but installation fail at a step of installing Thunderbird Snap

```

Installing the thunderbird snap
error: cannot perform the following tasks:
- Make snap "thunderbird" (470) available to the system (cannot cleanup failed attempt at making snap "thunderbird" available to the system: cannot update-desktop-database "update-desktop-database: error while loading shared libraries: libglib-2.0.so.0: cannot open shared object file: No such file or directory\n": exit status 127)
- Make snap "thunderbird" (470) available to the system (cannot update-desktop-database "update-desktop-database: error while loading shared libraries: libglib-2.0.so.0: cannot open shared object file: No such file or directory\n": exit status 127)

Errors were encountered while processing:
 /tmp/apt-dpkg-install-TJ8s5y/22-thunderbird_2%3a1snap1-0ubuntu3_amd64.deb
/usr/bin/gdbus: error while loading shared libraries: libgio-2.0.so.0: cannot open shared object file: No such file or directory
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/thunderbird.0.crash'
/usr/bin/gdbus: error while loading shared libraries: libgio-2.0.so.0: cannot open shared object file: No such file or directory
/usr/bin/gdbus: error while loading shared libraries: libgio-2.0.so.0: cannot open shared object file: No such file or directory
Exception during pm.DoInstall():  E:Sub-process /usr/bin/dpkg returned an error code (1)

Could not install the upgrades 

The upgrade has aborted. Your system could be in an unusable state.


```


I think snaps should be installed in the end of upgrade process, when upgrade is done, rather than in the middle

---

### Post by Impavidus on 2024-05-14
Yes, that's the problem mentioned above in post #4.

---

