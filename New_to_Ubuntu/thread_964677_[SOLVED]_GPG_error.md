---
title: "[SOLVED] GPG error"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by MJWitter on 2008-10-31
I was wondering if anyone can give me a hand:

I have been updating from Intrepid Beta through to Final and all has been smooth sailing, except for the last few days I have been getting the following error:

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


Now running apt-get update is what gives the error, so repeating it doesn't help matters.

Anyone have any ideas? (Sources.list below)

> # 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta amd64 (20080930.4)]/ intrepid main restricted

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta amd64 (20080930.4)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe
deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) intrepid main

Thanks in advance, 
Michael

---

### Post by Daveth on 2008-10-31
Is this just not a case of moving from beta to final, so they have moved the security file versioning, and you are hunting for the final, failing to get the key, and falling back to beta? My guess would be that the error lies in the authenification zone rather than the sources, as you only have what looks like the new version, but the system is trying to marry it up with the old key and then getting upset.
Just a hunch though.

---

### Post by JPorter on 2008-10-31
Daveth,

You are probably correct... would you mind explaining the proper method to delete the old key and get the new one?

Thanks!

---

### Post by unutbu on 2008-10-31
Try this: [http://ubuntuforums.org/showpost.php?p=4459462&postcount=3](http://ubuntuforums.org/showpost.php?p=4459462&postcount=3)
If that does not work, then try vnevoa's method:
[http://ubuntuforums.org/showpost.php?p=4837934&postcount=6](http://ubuntuforums.org/showpost.php?p=4837934&postcount=6)

---

### Post by banditti on 2008-10-31
Neither worked for me!

But, this did:

ALT + F2

```
sudo apt-get update -o Acquire::http::No-Cache=true
```

---

### Post by sikk on 2008-11-01
This also worked for me!

---

### Post by r3l1c on 2008-11-01
> **banditti said:**
> Neither worked for me!

But, this did:

ALT + F2

```
sudo apt-get update -o Acquire::http::No-Cache=true
```



Worked for me as well : ) i was about to go mental on this .... thanks a milion

---

