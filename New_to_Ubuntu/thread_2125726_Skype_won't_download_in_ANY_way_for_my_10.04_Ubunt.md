---
title: "Skype won't download in ANY way for my 10.04 Ubuntu..."
date: 2013-03-14
forum: New to Ubuntu
---

### Post by JustDandy on 2013-03-14
Everytime I try, the Software Center says "Dependency is not satisfiable: libqt4-dbus (>= 4:4.5.3)".
Any help?

---

### Post by Moose on 2013-03-14
It is most likely a support error,Anything older than Ubuntu 12.10 are basically jurassic in the sense that no software developers support the operating systems anymore. Upgrade your operating system and you will probably have more luck.


Edit; I didn't read the OP good enough, if it is a dependency issue, try updating your operating system and your software centre.

---

### Post by Impavidus on 2013-03-15
10.04 LTS is still supported, so it should be possible to install skype from the repositories. But still, as it will only be supported for one more month it may be time to upgrade to 12.04 LTS. Skype works there, or at least, I have it installed. Haven't used it for a while though, but if it hadn't worked I would have seen more complaints here.

---

### Post by Lars Noodén on 2013-03-15
Speaking of upgrades, with the new owner, it is probable that Skype for Linux will eventually go away and you need to plan for an upgrade to SIP.  You might try Jitsi or Ekiga.  They can be used parallel to Skype, allowing you to make a gradual transition to SIP.  Neither can call Skype, that I know of, but they can talk with *any* SIP phone client.

---

### Post by JustDandy on 2013-03-15
Regarding to everyone that says I should update, when I go on Update Manager, it SAYS my system is up to date and there are no updates to install. But when I check for new updates everything fails. A message pops up that looks like the picture posted. ---> [http://imgur.com/7bUpndH](http://imgur.com/7bUpndH)
It used to ask me at the top of Update Manager if I would like to update to a newer Ubuntu (forget which version), but I don't see it anymore...

---

### Post by Impavidus on 2013-03-15
It says it can't update the package information, which may well explain your problem. But I can't read the entire message. Does it say it can't find the file? Can you reach the server?

---

### Post by JustDandy on 2013-03-15
This is the full message, with the IPs taken out, of course.

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  404  Not Found [IP: XX.XXX.XX.XX XX
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: XX.XXX.XX.XX XX]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  404  Not Found [IP: XX.XXX.XX.XXX XX]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  404  Not Found [IP: XX.XXX.XX.XXX XX]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: XX.XXX.XX.XXX XX]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: XX.XXX.XX.XXX XX]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  404  Not Found [IP: XX.XXX.XX.XXX XX]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  404  Not Found [IP: XX.XXX.XX.XXX XX]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  404  Not Found [IP: XX.XXX.XX.XXX XX]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: XX.XXX.XX.XXX XX]
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Impavidus on 2013-03-16
It tries to download the package information of Maverick Meerkat, which is Ubuntu 10.10. That is end of live, which explains why things don't work anymore. I'm not sure what's the best course of action right now. I think the official policy is that you get a live cd of either 12.04 LTS or 12.10, make some backups and reinstall, but upgrading may also be possible. Wait a moment for other people to give you some advise.

---

