---
title: "[SOLVED] Upgrading from 6.10 to 7.04"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by J03y on 2008-10-16
Hi, im a new linux user, and im trying to upgrade from 6.10 to 7.04 but it always says,(Error during update. A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry). And heres a list of some failed fetches:

```
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz) 404 Not Found

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz) 404 Not Found

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz) 404 Not Found

Failed to fetch [http://pr.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://pr.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]

Failed to fetch [http://pr.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://pr.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]

Failed to fetch [http://pr.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://pr.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.45 80]

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz) 404 Not Found

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz) 404 Not Found

Failed to fetch [http://pr.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://pr.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.45 80]

Failed to fetch [http://pr.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://pr.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]

Failed to fetch [http://pr.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://pr.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]

Failed to fetch [http://pr.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://pr.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]

Failed to fetch [http://pr.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://pr.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]

Failed to fetch [http://pr.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://pr.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.45 80]

Failed to fetch [http://pr.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://pr.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.45 80]

Failed to fetch [http://pr.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz](http://pr.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]

Failed to fetch [http://pr.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://pr.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.45 80]
```

  Any answer on how to fix this would be very appreciated.:)

---

### Post by Elfy on 2008-10-16
You'll need to change your sources list - edgy repos are closed nopw afaik.

```
sudo cp /etc/apt/sources.list
gksudo gedit /etc/apt/sources.list
```

Comment out the edgy repos with a # at the beginning of each line

Do you know that the feisty repos will be closing soon too - 7.04 is end of life on Sunday, or do you intend to upgrade to gutsy and hardy (Gutsy will be eol in short order)

If you do intend to upgrade past feisty you might be better served backing up your home and doing a clean install from a downloaded iso

---

### Post by Officer Dibble on 2008-10-16
Ah! So if I wanted to upgrade all I would need to back up is what is in my Home folder?

---

### Post by Paqman on 2008-10-16
The upgrade path from 6.06 actually goes straight to 8.04, since they're both LTS versions.

---

### Post by drs305 on 2008-10-16
The reason for the error messages is that 6.10 is no longer supported. Edgy's repositories have been removed from the servers. As you have found, your current version works but you can no longer update it. You can upgrade from Dapper to Hardy but not from Edgy to Hardy. You would have to step through the intermediate releases.

A new version, Intrepid (8.10) will be out at the end of the month and you could wait until then. If you aren't into updating versions, which seems to be the case, Hardy is a LTS (Long Term Support) version that will be supported until April 2011, while Intrepid will be supported until April 2010. So Intpreid (8.10) will be newer but won't 'last' as long as Hardy.

---

### Post by prshah on 2008-10-16
> **J03y said:**
> Hi, im a new linux user, and im trying to upgrade from 6.10 to 7.04 

Heh; both versions have crossed support dates!

7.04 has closed it's repositories just recently!

I'd suggest you get hold of an 7.04 alternate CD (it's still being torrented around) and use that to upgrade your 6.10, and then upgrade further to 8.04.1 (again using the alternate CD).

---

### Post by Joeb454 on 2008-10-16
Support is only 18 Months for normal releases, 3 years for LTS Releases (Dapper & Hardy).

I would suggest upgrading to 7.10 (Gutsy) if you don't want to run Ubuntu 8.04 :)

---

### Post by J03y on 2008-10-16
Yea i think ill have to get the 7.10 CD. Oh well. Ty anyways:(

---

### Post by Elfy on 2008-10-16
I checked - 7.10 will be at end of life in April 2009

---

### Post by Joeb454 on 2008-10-16
> **forestpixie said:**
> I checked - 7.10 will be at end of life in April 2009

Indeed - though 7.04 support ends this month (if not already).

7.10 is the lowest version you can go with - 8.04 will be supported until April 2011

---

### Post by Paqman on 2008-10-16
> **J03y said:**
> Yea i think ill have to get the 7.10 CD. Oh well. Ty anyways:(

You don't need a CD if you follow the LTS upgrade path and go straight to 8.04. Just use Update Manager.

---

### Post by Elfy on 2008-10-16
> **Paqman said:**
> You don't need a CD if you follow the LTS upgrade path and go straight to 8.04. Just use Update Manager.

The LTS upgrade path is from 6.06 I thought not 6.10, which is what the OP has.

---

### Post by Keen101 on 2008-10-16
the best way i would think in your situation would be to download the **alternate install disk** of whatever version you want to upgrade to.

The alternate install disk's have a feature that you can upgrade from them. Very handy in situations like these.

this command might also help you upgrade, but i really do not recommend it for your situation. sudo apt-get upgrade -d

---

### Post by Elfy on 2008-10-16
@J03y To comment out lines in sources list.

Backup and open file to edit

```
sudo cp /etc/apt/sources.list
gksudo gedit /etc/apt/sources.list
```

At beginning of all lines which have edgy in put a #

Do not change anything else, save and close and then run

```
sudo apt-get update
```

---

### Post by J03y on 2008-10-16
> **forestpixie said:**
> @J03y To comment out lines in sources list.

Backup and open file to edit

```
sudo cp /etc/apt/sources.list
gksudo gedit /etc/apt/sources.list
```

At beginning of all lines which have edgy in put a #

Do not change anything else, save and close and then run

```
sudo apt-get update
```

i did what u said and then i got a message saying "E: Malformed line 2 in source list /etc/apt/sources.list (dist)" :confused:

---

### Post by Paqman on 2008-10-16
> **forestpixie said:**
> The LTS upgrade path is from 6.06 I thought not 6.10, which is what the OP has.

D'oh, so he does! I didn't think anyone would still be running Edgy. Wouldn't the repos be dead as a doornail?

I'll shut up now, shall I?

---

### Post by bodhi.zazen on 2008-10-16
I think the best thing to do here is a fresh install. The updates from 6.* to 7.* did not go all that smooth.

Also, FYI, the preferred method has more recently been to use update manager (an NOT via the "manual" methods of editing /etc/apt/sources.list => apt-get)

[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

---

