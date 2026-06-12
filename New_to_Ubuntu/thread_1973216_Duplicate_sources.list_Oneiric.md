---
title: "Duplicate sources.list Oneiric"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by freedomAboveAll on 2012-05-04
Hello, I have similar problem, though it is not affecting the system:


```
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

using the grep suggestion shows these sources:

```

~$ grep -v ^# /etc/apt/sources.list | sort | uniq -c | sort
      1 deb http://archive.canonical.com/ubuntu oneiric partner
      1 deb http://extras.ubuntu.com/ubuntu oneiric main
      1 deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
      1 deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
      1 deb http://security.ubuntu.com/ubuntu oneiric-security universe
      1 deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
      1 deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
      1 deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
      1 deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
      1 deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
      1 deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
      1 deb-src http://extras.ubuntu.com/ubuntu oneiric main
      1 deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
      1 deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse
      1 deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

```





Thank you for any suggestion.

---

### Post by oldos2er on 2012-05-04
Post moved to its own thread.

---

### Post by Cheesemill on 2012-05-04
Check all of the files in /etc/apt/sources.list.d/ and see if there are any duplicates in there.

---

### Post by freedomAboveAll on 2012-05-04
Found the duplicate via Synaptic.

Settings > Repositories , Other Software tab

I had 2 entries for Canonical Partners.  Unchecked one of those, and problem solved!


Thank you for your reply.

---

