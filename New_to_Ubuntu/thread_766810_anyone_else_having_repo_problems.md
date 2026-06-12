---
title: "anyone else having repo problems?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by rickycodie on 2008-04-25
so i installed hardy(kubuntu) and can't access the repo's. 
this is what happens;
```
ricky@ricky-laptop:~$ sudo apt-get update
Get:1 http://archive.canonical.com hardy Release.gpg [191B]
Get:2 http://security.ubuntu.com hardy-security Release.gpg [191B]
Ign http://archive.canonical.com hardy/partner Translation-en_US
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Hit http://archive.canonical.com hardy Release
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://archive.canonical.com hardy/partner Packages
Hit http://security.ubuntu.com hardy-security Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
97% [Connecting to us.archive.ubuntu.com (91.189.88.31)]
```

and it's stuck. it just wont' go. same with an install.

---

### Post by phr0ze on 2008-04-25
This tends to happen after a new release because of server overload.

John


> **rickycodie said:**
> so i installed hardy(kubuntu) and can't access the repo's. 
this is what happens;
```
ricky@ricky-laptop:~$ sudo apt-get update
Get:1 http://archive.canonical.com hardy Release.gpg [191B]
Get:2 http://security.ubuntu.com hardy-security Release.gpg [191B]
Ign http://archive.canonical.com hardy/partner Translation-en_US
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Hit http://archive.canonical.com hardy Release
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://archive.canonical.com hardy/partner Packages
Hit http://security.ubuntu.com hardy-security Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
97% [Connecting to us.archive.ubuntu.com (91.189.88.31)]
```

and it's stuck. it just wont' go. same with an install.

---

### Post by pinoyskull on 2008-04-25
the main servers is loaded, try using mirror, japan mirror works fine with me

---

### Post by ptcbus on 2008-04-25
I think these errors are due to the jammed servers.

---

### Post by rickycodie on 2008-04-25
can you please post the repo link so i can add it?

---

