---
title: "Trouble Upgrading From 14.10 to 16.04"
date: 2016-08-10
forum: New to Ubuntu
---

### Post by tr3v10 on 2016-08-10
I am having trouble upgrading from 14.10 to 16.04. After using```
sudo apt-get update
```to update my system I get the following errors:
```
Ign http://us.archive.ubuntu.com utopic InRelease
Ign http://us.archive.ubuntu.com utopic-updates InRelease
Ign http://security.ubuntu.com utopic-security InRelease
Ign http://extras.ubuntu.com utopic InRelease  
Ign http://us.archive.ubuntu.com utopic-backports InRelease
Ign http://us.archive.ubuntu.com utopic Release.gpg
Ign http://security.ubuntu.com utopic-security Release.gpg
Hit http://extras.ubuntu.com utopic Release.gpg
Ign http://us.archive.ubuntu.com utopic-updates Release.gpg
Ign http://us.archive.ubuntu.com utopic-backports Release.gpg
Ign http://security.ubuntu.com utopic-security Release
Hit http://extras.ubuntu.com utopic Release    
Ign http://us.archive.ubuntu.com utopic Release                       
Ign http://security.ubuntu.com utopic-security/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com utopic-updates Release
Hit http://extras.ubuntu.com utopic/main Sources
Ign http://us.archive.ubuntu.com utopic-backports Release                          
Ign http://security.ubuntu.com utopic-security/restricted Sources/DiffIndex
Hit http://extras.ubuntu.com utopic/main amd64 Packages
Ign http://us.archive.ubuntu.com utopic/main Sources/DiffIndex                      
Ign http://us.archive.ubuntu.com utopic/restricted Sources/DiffIndex 
Ign http://security.ubuntu.com utopic-security/universe Sources/DiffIndex
Hit http://extras.ubuntu.com utopic/main i386 Packages
Ign http://us.archive.ubuntu.com utopic/universe Sources/DiffIndex                  
Ign http://us.archive.ubuntu.com utopic/multiverse Sources/DiffIndex 
Ign http://security.ubuntu.com utopic-security/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com utopic/main amd64 Packages/DiffIndex
Ign http://security.ubuntu.com utopic-security/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic/universe amd64 Packages/DiffIndex
Ign http://security.ubuntu.com utopic-security/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic/main i386 Packages/DiffIndex
Ign http://security.ubuntu.com utopic-security/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic/universe i386 Packages/DiffIndex
Ign http://security.ubuntu.com utopic-security/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic/multiverse i386 Packages/DiffIndex
Ign http://security.ubuntu.com utopic-security/main i386 Packages/DiffIndex
Ign http://security.ubuntu.com utopic-security/restricted i386 Packages/DiffIndex
Ign http://security.ubuntu.com utopic-security/universe i386 Packages/DiffIndex
Ign http://security.ubuntu.com utopic-security/multiverse i386 Packages/DiffIndex
Ign http://extras.ubuntu.com utopic/main Translation-en_US
Ign http://extras.ubuntu.com utopic/main Translation-en
Ign http://us.archive.ubuntu.com utopic-updates/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com utopic-updates/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com utopic-updates/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com utopic-updates/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com utopic-updates/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-updates/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-updates/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-updates/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-updates/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-updates/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-updates/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-updates/multiverse i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-backports/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com utopic-backports/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com utopic-backports/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com utopic-backports/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com utopic-backports/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-backports/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-backports/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-backports/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-backports/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-backports/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-backports/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com utopic-backports/multiverse i386 Packages/DiffIndex
Ign http://security.ubuntu.com utopic-security/main Translation-en_US
Ign http://security.ubuntu.com utopic-security/main Translation-en
Ign http://security.ubuntu.com utopic-security/multiverse Translation-en_US
Ign http://security.ubuntu.com utopic-security/multiverse Translation-en
Ign http://security.ubuntu.com utopic-security/restricted Translation-en_US
Ign http://security.ubuntu.com utopic-security/restricted Translation-en
Ign http://security.ubuntu.com utopic-security/universe Translation-en_US
Ign http://security.ubuntu.com utopic-security/universe Translation-en
Err http://security.ubuntu.com utopic-security/main Sources
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com utopic-security/restricted Sources
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com utopic-security/universe Sources
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com utopic-security/multiverse Sources
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com utopic-security/main amd64 Packages
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com utopic-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com utopic-security/universe amd64 Packages
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com utopic-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com utopic-security/main i386 Packages
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com utopic-security/restricted i386 Packages
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com utopic-security/universe i386 Packages
  404  Not Found [IP: 91.189.88.161 80]
Err http://security.ubuntu.com utopic-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.161 80]
Ign http://us.archive.ubuntu.com utopic/main Translation-en_US
Ign http://us.archive.ubuntu.com utopic/main Translation-en
Ign http://us.archive.ubuntu.com utopic/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com utopic/multiverse Translation-en
Ign http://us.archive.ubuntu.com utopic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com utopic/restricted Translation-en
Ign http://us.archive.ubuntu.com utopic/universe Translation-en_US
Ign http://us.archive.ubuntu.com utopic/universe Translation-en
Ign http://us.archive.ubuntu.com utopic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com utopic-updates/main Translation-en
Ign http://us.archive.ubuntu.com utopic-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com utopic-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com utopic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com utopic-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com utopic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com utopic-updates/universe Translation-en
Ign http://us.archive.ubuntu.com utopic-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com utopic-backports/main Translation-en
Ign http://us.archive.ubuntu.com utopic-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com utopic-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com utopic-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com utopic-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com utopic-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com utopic-backports/universe Translation-en
Err http://us.archive.ubuntu.com utopic/main Sources
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic/restricted Sources
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic/universe Sources
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic/multiverse Sources
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic/main amd64 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic/universe amd64 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic/main i386 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic/restricted i386 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic/universe i386 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-updates/main Sources
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-updates/restricted Sources
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-updates/universe Sources
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-backports/main Sources
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-backports/restricted Sources
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-backports/universe Sources
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-backports/main amd64 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-backports/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-backports/universe amd64 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-backports/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-backports/main i386 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-backports/universe i386 Packages
  404  Not Found [IP: 91.189.91.26 80]
Err http://us.archive.ubuntu.com utopic-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.26 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/utopic-security/main/source/Sources  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/source/Sources  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic/main/source/Sources  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic/restricted/source/Sources  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/utopic-security/universe/source/Sources  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic/universe/source/Sources  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/source/Sources  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/utopic-security/multiverse/source/Sources  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/utopic-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/utopic-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/utopic-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/utopic-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/utopic-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.161 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/main/source/Sources  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/restricted/source/Sources  404  Not Found [IP: 91.189.91.26 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/utopic-updates/universe/source/Sources  404  Not Found [IP: 91.189.91.26 80]
```
Also after changing the DNS servers around and trying ```
sudo apt-get install -f
```I get
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  resolvconf
The following NEW packages will be installed:
  resolvconf
0 upgraded, 1 newly installed, 0 to remove and 104 not upgraded.
Need to get 57.8 kB of archives.
After this operation, 260 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
WARNING: The following packages cannot be authenticated!
  resolvconf
Install these packages without verification? [y/N] y
Err http://us.archive.ubuntu.com/ubuntu/ utopic/main resolvconf all 1.69ubuntu4
  404  Not Found [IP: 91.189.91.26 80]
E:  Failed to fetch  http://us.archive.ubuntu.com/ubuntu/pool/main/r/resolvconf/resolvconf_1.69ubuntu4_all.deb   404  Not Found [IP: 91.189.91.26 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

How can i resolve this? Im also using foxfi wireless tether if that is any help.

---

### Post by QIII on 2016-08-10
Hello!

14.10 went out of support just over a year ago and the repositories have been moved.

Although on can try to update an old, unsupported release, I recommend strongly against doing so.  It is more likely to result in a significant emotional event than success.

I would recommend backing up your important files and doing a fresh installation of 16.04.

---

### Post by tr3v10 on 2016-08-10
I understand, thank you for your response! I'll do that fresh install.

---

