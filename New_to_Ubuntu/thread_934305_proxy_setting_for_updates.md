---
title: "proxy setting for updates"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by pardesi on 2008-09-30
hi i just installed ubuntu in my laptop 
i cant install updates because of failed proxy authentication...
i went to the System>Applications>Synaptic Package manager>Settings>Preferences>Network..
then tehre wrote the appropriate http proxy and authentication usrname and passwd yet i am unable to connect...anyway out


EDIT:
The output  i am getting for 
```
sudo apt-get update
```
is
```
Ign http://security.ubuntu.com hardy-security Release.gpg
Ign http://in.archive.ubuntu.com hardy Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_IN
Ign http://in.archive.ubuntu.com hardy/main Translation-en_IN
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com hardy/restricted Translation-en_IN
Ign http://security.ubuntu.com hardy-security/universe Translation-en_IN
Ign http://in.archive.ubuntu.com hardy/universe Translation-en_IN
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_IN
Ign http://in.archive.ubuntu.com hardy/multiverse Translation-en_IN
Ign http://security.ubuntu.com hardy-security Release
Ign http://in.archive.ubuntu.com hardy-updates Release.gpg
Ign http://security.ubuntu.com hardy-security/main Packages
Ign http://in.archive.ubuntu.com hardy-updates/main Translation-en_IN
Ign http://security.ubuntu.com hardy-security/restricted Packages
Ign http://in.archive.ubuntu.com hardy-updates/restricted Translation-en_IN
Ign http://security.ubuntu.com hardy-security/main Sources
Ign http://in.archive.ubuntu.com hardy-updates/universe Translation-en_IN
Ign http://security.ubuntu.com hardy-security/restricted Sources
Ign http://in.archive.ubuntu.com hardy-updates/multiverse Translation-en_IN
Ign http://security.ubuntu.com hardy-security/universe Packages
Ign http://in.archive.ubuntu.com hardy Release
Ign http://security.ubuntu.com hardy-security/universe Sources
Ign http://in.archive.ubuntu.com hardy-updates Release
Ign http://security.ubuntu.com hardy-security/multiverse Packages
Ign http://in.archive.ubuntu.com hardy/main Packages
Ign http://security.ubuntu.com hardy-security/multiverse Sources
Ign http://in.archive.ubuntu.com hardy/restricted Packages
Err http://security.ubuntu.com hardy-security/main Packages
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com hardy/main Sources
Err http://security.ubuntu.com hardy-security/restricted Packages
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com hardy/restricted Sources
Err http://security.ubuntu.com hardy-security/main Sources
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com hardy/universe Packages
Err http://security.ubuntu.com hardy-security/restricted Sources
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com hardy/universe Sources
Err http://security.ubuntu.com hardy-security/universe Packages
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com hardy/multiverse Packages
Err http://security.ubuntu.com hardy-security/universe Sources
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com hardy/multiverse Sources
Err http://security.ubuntu.com hardy-security/multiverse Packages
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com hardy-updates/main Packages
Err http://security.ubuntu.com hardy-security/multiverse Sources
  407 Proxy Authentication Required
Ign http://in.archive.ubuntu.com hardy-updates/restricted Packages
Ign http://in.archive.ubuntu.com hardy-updates/main Sources
Ign http://in.archive.ubuntu.com hardy-updates/restricted Sources
Ign http://in.archive.ubuntu.com hardy-updates/universe Packages
Ign http://in.archive.ubuntu.com hardy-updates/universe Sources
Ign http://in.archive.ubuntu.com hardy-updates/multiverse Packages
Ign http://in.archive.ubuntu.com hardy-updates/multiverse Sources
Err http://in.archive.ubuntu.com hardy/main Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy/restricted Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy/main Sources
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy/restricted Sources
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy/universe Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy/universe Sources
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy/multiverse Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy/multiverse Sources
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy-updates/main Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy-updates/restricted Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy-updates/main Sources
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy-updates/restricted Sources
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy-updates/universe Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy-updates/universe Sources
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy-updates/multiverse Packages
  407 Proxy Authentication Required
Err http://in.archive.ubuntu.com hardy-updates/multiverse Sources
  407 Proxy Authentication Required
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz  407 Proxy Authentication Required

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
though using the same proxy i am able to connect net thru firefox

---

### Post by littletinman on 2008-09-30
Hrmmm, that is odd. I think i had the same problem a while ago, and I had to make sure my software sources were selected correctly. Try updating using Update manager, or Synaptic.

---

