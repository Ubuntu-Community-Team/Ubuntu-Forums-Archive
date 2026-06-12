---
title: "What's up with 10.10?"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by Karl10 on 2013-02-09
I'm suddenly finding that I can't upgrade or install a whole lot of packages or services.  In "Software Center, I get this error message:"*The action would require the installation of packages from not authenticated sources.*"

In Synaptic Package Manager, I get messages like this:
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E585066A30C18A2B

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80][/I]

as well as the [I]The action would require the installation of packages from not authenticated sources.
```

I get similar error messages in Terminal too.

May or may not be related: I install an application package (such as Mondo), all appears to go well, but the app never appears in the menu, or anywhere else that I can see.

Is it just time to nuke it and upgrade?  I'm not one to upgrade just because it's there; I upgrade only if my current install is no longer sufficient or there are compelling reasons to upgrade (hate the "learning curve" that comes with every major change). I LIKE 10.10; it's just been getting wonkier by the day.

Thoughts?

---

### Post by arpanaut on 2013-02-09
10,10 is End of Life, i.e. no longer supported, those repositories no longer exist.
this should help: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by deadflowr on 2013-02-09
The very simple answer is maverick is dead.
It's been dead for close to a year.
The repos are still available, but they have been move to the old-release repos.

I recommend upgrading to a supported version, but I won't beg you to.
You can switch out your current repos with the old ones following the advice in this :

[http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions]("http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions")

Understand, though, that the old release repos get absolutely no support and are full of all the old bugs and unpatched security problems that were still in the release before it was shuttered.

---

### Post by Karl10 on 2013-02-09
Thanks, guys.

One thing about these forums; you never have to wait long for a reply!

Yeah, I figured as much.  I've insufficient disk space to upgrade... guess I'll have to save 'off-disk' what I don't want to lose, fdisk it, and start from scratch.  Not happy, but that's life.

---

