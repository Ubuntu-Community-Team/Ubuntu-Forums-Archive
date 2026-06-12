---
title: "apt-get update errors"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by ambienthack on 2013-01-11
I'm trying to install imagemagick & had to run apt-get update to update package list.

apt-get update says:
```

Ign http://archive.ubuntu.com maverick Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com maverick-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com maverick-security Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com maverick Release
Ign http://archive.ubuntu.com maverick-updates Release
Ign http://archive.ubuntu.com maverick-security Release
Ign http://archive.ubuntu.com maverick/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-security/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-security/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick-security/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com maverick/main i386 Packages
Ign http://archive.ubuntu.com maverick/restricted i386 Packages
Ign http://archive.ubuntu.com maverick/universe i386 Packages
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://archive.ubuntu.com maverick-security/main i386 Packages
Ign http://archive.ubuntu.com maverick-security/restricted i386 Packages
Ign http://archive.ubuntu.com maverick-security/universe i386 Packages
Ign http://archive.ubuntu.com maverick/main i386 Packages
Ign http://archive.ubuntu.com maverick/restricted i386 Packages
Ign http://archive.ubuntu.com maverick/universe i386 Packages
Ign http://archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://archive.ubuntu.com maverick-security/main i386 Packages
Ign http://archive.ubuntu.com maverick-security/restricted i386 Packages
Ign http://archive.ubuntu.com maverick-security/universe i386 Packages
Err http://archive.ubuntu.com maverick/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err http://archive.ubuntu.com maverick/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err http://archive.ubuntu.com maverick/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err http://archive.ubuntu.com maverick-updates/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err http://archive.ubuntu.com maverick-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err http://archive.ubuntu.com maverick-updates/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err http://archive.ubuntu.com maverick-security/main i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err http://archive.ubuntu.com maverick-security/restricted i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
Err http://archive.ubuntu.com maverick-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.201 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.201 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

my sources.list is 
```

deb http://archive.ubuntu.com/ubuntu maverick main restricted universe
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted universe
deb http://archive.ubuntu.com/ubuntu maverick-security main restricted universe

```

when I try to install imagemagick some packages are not found

can anyone help?

---

### Post by deadflowr on 2013-01-11
You'll either need to update to a supported release, such 11.10  up to 12.10, or switch your repos to the old-release repos.
Maverick is dead my friend, so the repos you have are too.

Look here for how to change the repos to the old releases:

[http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions]("http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions")

---

### Post by ambienthack on 2013-01-11
many thanks

---

