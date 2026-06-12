---
title: "apt-get update: error upon reaching security.ubuntu.com"
date: 2009-02-20
forum: Philippine Team
---

### Post by dodimar on 2009-02-20
Tried this several times this morning at different intervals.. checked if my net was okay and it's okay.... help...

```
root@server1:~# apt-get update
Hit http://ph.archive.ubuntu.com hardy Release.gpg
Ign http://ph.archive.ubuntu.com hardy/main Translation-en_PH
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_PH
Ign http://ph.archive.ubuntu.com hardy/restricted Translation-en_PH
Ign http://ph.archive.ubuntu.com hardy/universe Translation-en_PH
Ign http://ph.archive.ubuntu.com hardy/multiverse Translation-en_PH
Hit http://ph.archive.ubuntu.com hardy-updates Release.gpg
Ign http://ph.archive.ubuntu.com hardy-updates/main Translation-en_PH
Ign http://ph.archive.ubuntu.com hardy-updates/restricted Translation-en_PH
Ign http://ph.archive.ubuntu.com hardy-updates/universe Translation-en_PH
Ign http://ph.archive.ubuntu.com hardy-updates/multiverse Translation-en_PH
Hit http://ph.archive.ubuntu.com hardy Release
Hit http://archive.canonical.com hardy Release
Hit http://ph.archive.ubuntu.com hardy-updates Release
Hit http://archive.canonical.com hardy/partner Packages
Hit http://ph.archive.ubuntu.com hardy/main Packages
Hit http://ph.archive.ubuntu.com hardy/restricted Packages
Hit http://ph.archive.ubuntu.com hardy/main Sources
Hit http://ph.archive.ubuntu.com hardy/restricted Sources
Hit http://ph.archive.ubuntu.com hardy/universe Packages
Hit http://archive.canonical.com hardy/partner Sources
Hit http://ph.archive.ubuntu.com hardy/universe Sources
Hit http://ph.archive.ubuntu.com hardy/multiverse Packages
Hit http://ph.archive.ubuntu.com hardy/multiverse Sources
Hit http://ph.archive.ubuntu.com hardy-updates/main Packages
Hit http://ph.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://ph.archive.ubuntu.com hardy-updates/main Sources
Hit http://ph.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://ph.archive.ubuntu.com hardy-updates/universe Packages
Hit http://ph.archive.ubuntu.com hardy-updates/universe Sources
Hit http://ph.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://ph.archive.ubuntu.com hardy-updates/multiverse Sources
Err http://security.ubuntu.com hardy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://security.ubuntu.com hardy-security/main Translation-en_PH
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/restricted Translation-en_PH
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/universe Translation-en_PH
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_PH
  Unable to connect to security.ubuntu.com http:
Reading package lists... Done
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_PH.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_PH.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_PH.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_PH.bz2  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

---

### Post by loell on 2009-02-20
```
Unable to connect to security.ubuntu.com http:

```

security.ubuntu.com's http server is probably down at the momment.

---

### Post by dodimar on 2009-02-20
```

Pinging security.ubuntu.com [91.189.88.37] with 32 bytes of data:

Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 91.189.88.37:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),


```

down nga...

---

### Post by dodimar on 2009-02-21
Okay na ito... :)

---

