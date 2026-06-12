---
title: "ubuntu  6.10 how to upgrade to new ubuntu?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by davejustdave on 2008-07-16
just installed ubuntu 6.10 and i know there is a new version out there. i tried to use the update manager but i get a error message...

Authentication failed

Authenticating the upgrade failed. There may be a problem with the network or with the server. 

... this is when i choose to upgrade to the "new distribution release 7.04 available"

do i need to update to 7.04 or 8.1 or whatever is out there? or can i just go along with my out initial setup? are there security risks for me since i have installed a 2 year old ubuntu without any updates?

when i choose to "check for updates i get this message...

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]

... so any help is apreciated
dave

---

### Post by scragar on 2008-07-16
I don't think there is support for 6.10 anymore(6.6 was a long term release, and that's ending very shortly)... You have only a few options from my point of veiw, you can either download an ISO for the new release or(and this is unlikly to work) edit your apt repo's list manualy replacing edgy with hardy, then update the list, check the dependencies, then run the update procedure, but this is likly to be a rather slow process.
```
gksudo gedit /etc/apt/sources.list

sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```

---

### Post by davejustdave on 2008-07-16
another issue (or maybe the same one happening again) i open the add / remove programs file and recieve this message...

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]

---

### Post by avtolle on 2008-07-16
To upgrade from 6.10 (no longer supported, as you have learned) to 8.04 at this point would take, IMHO, downloading the appropriate 8.04 iso from a mirror, burn it to CD, and do a clean install. The other way is a sequential upgrade, from 6.10 to 7.04 to 7.10 to 8.04, but at each step the previous version (in your case, 6.10) needs to be fully updated to upgrade to the next release. As you just installed, I'm guessing there is no way to fully update the 6.10 installation you have, and thus, the clean install seems to me to be your only method if you want to get to 8.04.

---

### Post by davejustdave on 2008-07-16
i tried to burn the newest version onto cd but my windows xp did not recognize the .iso file and did not open it in any way... did i burn it wrong?

---

### Post by avtolle on 2008-07-16
If you want to try the sequential upgrade route, take a look at [https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades) importantly the bit about changing the sources.list and installing a newer update manager.

How did you burn the iso? As an image, which you need to do, or otherwise? BTW, you need to boot from the CD, not try to open in XP.

---

### Post by appi2012 on 2008-07-16
try using an alternate cd of 7.04 to upgrade to 7.04 just download and burn the alternate cd and then insert it into your cd drive while ubuntu is running. A dialog should pop up asking whether you want to upgrade or not. Say that you want to. From 7.04, if the update manager still doesn't work, then just use another alternate cd to upgrade to 7.10. Then just upgrade to 8.04 (latest) using whatever works (cd or update manager). 

I know that this sounds like too much work, but I'm not sure how to fix those update manager errors, and I know that the alternate cd will work. since your release isn't a LTS release or the 7.10 release, you can't directly upgrade to hardy (8.04)

I agree with scargar, it seems as if 6.10 isn't supported. So sequentially upgrading to hardy should fix that problem.

---

### Post by appi2012 on 2008-07-16
take a look here to see how to burn on windows:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by phidia on 2008-07-16
Someone please correct me if I'm wrong but I believe 6.10 is no longer supported. It was released in '06, it's not an LTS version because 6.06 was-either way it's out of date now.
It does seem like you should be able to update it though. Take a look at [this howto]("http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html") and see if those steps work for you.

---

### Post by davejustdave on 2008-07-16
will try again to boot from the cd i burned...

bummer part is computer that has burning drive is behaving badly.
thanks for help i will report back

---

