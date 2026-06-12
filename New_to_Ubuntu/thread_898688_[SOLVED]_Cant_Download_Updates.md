---
title: "[SOLVED] Cant Download Updates"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Hoonakwa on 2008-08-23
Hi,
 Total newbe here. I can get on the internet but when I try to download updates I get a message saying.

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

I have no idea what to do.

---

### Post by pfdevil on 2008-08-23
Hey 

So this is a fresh install? Thus your repositories should be correct. Are you connected to your own router, or some network with a proxy and firewall?

---

### Post by bubba_169 on 2008-08-23
Open a terminal and type 

```
sudo apt-get update
```

then paste the output here so we know whats happening :)

---

### Post by Hoonakwa on 2008-08-23
ok here are the results. I am connecting through a router and a dsl modem. This is not a wireless. I am connected with a cable.

james@james-desktop:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by SunnyRabbiera on 2008-08-23
Did you try another mirror?

---

### Post by tangibleorange on 2008-08-23
6.10 Edgy Eft is no longer supported as of April 2008. you will need to download a newer version to continue using ubuntu.

---

### Post by Hoonakwa on 2008-08-23
Thanks for the speedy reply. Ill get a new version.

---

### Post by Hoonakwa on 2008-08-23
I downloaded ubuntu-8.04.1-desktop-i386.iso, i used InfraRecorder and used the checksum program. Everything looked good but cannot boot from disk. I get to the main page but when I select install I get a error saying cant read from disk.

Any help would be appreciated

---

### Post by jbuttler on 2008-08-24
> **tangibleorange said:**
> 6.10 Edgy Eft is no longer supported as of April 2008. you will need to download a newer version to continue using ubuntu.
I need to use 6.10 for my kids old powerpc G4. Are there any archives I can point to anywhere?
Thanks!

---

### Post by tangibleorange on 2008-08-24
> **Hoonakwa said:**
> I downloaded ubuntu-8.04.1-desktop-i386.iso, i used InfraRecorder and used the checksum program. Everything looked good but cannot boot from disk. I get to the main page but when I select install I get a error saying cant read from disk.

Any help would be appreciated

try using the inbuilt 'check disk' function. it's one of the options when you first boot. that might find an error. if it does, you will need to try burning at a lower speed.

---

### Post by tangibleorange on 2008-08-24
> **jbuttler said:**
> I need to use 6.10 for my kids old powerpc G4. Are there any archives I can point to anywhere?
Thanks!

i'm afraid i don't know of any. you might consider using 6.06, which still has support for PPC until June 2009.

---

### Post by jbuttler on 2008-08-24
PERFECT! Thank you. :)

---

### Post by tangibleorange on 2008-08-24
> **jbuttler said:**
> PERFECT! Thank you. :)

this link might also be of some use:

[http://https://wiki.ubuntu.com/PowerPCFAQ]("http://https://wiki.ubuntu.com/PowerPCFAQ")

---

### Post by Hoonakwa on 2008-08-25
Well,
 I tried reburning and checking the disk. I said no error but still woudnt boot. I tried the alternate download, check the disk all looked good but still wont boot. I am getting very frustrated with the new distro. My old disk will load and boot but I get no updates because its not supported anymore. I guess I will try to download and burn the disk one more time. Then if that dosent work I guess its back to WINDO$.

Izzy the wannbe Linux user.

---

### Post by Gregmond on 2008-08-25
> **Hoonakwa said:**
> Well,
 I tried reburning and checking the disk. I said no error but still woudnt boot. I tried the alternate download, check the disk all looked good but still wont boot. I am getting very frustrated with the new distro. My old disk will load and boot but I get no updates because its not supported anymore. I guess I will try to download and burn the disk one more time. Then if that dosent work I guess its back to WINDO$.

Izzy the wannbe Linux user.

When this happened to me - it was my burner. No prob with the image. I burned a new copy on a different burner and all good.
Can you boot the CD in another PC to check it ?

6.06 or 7.10 might be better options for older hardware although I am no expert on that.

---

### Post by Hoonakwa on 2008-08-25
Well,
 I burned the disk at a slower speed and it worked. I am now useing my new Ubuntu system to write this. 
 Thanks For All the Help Guys.

:lolflag:

---

