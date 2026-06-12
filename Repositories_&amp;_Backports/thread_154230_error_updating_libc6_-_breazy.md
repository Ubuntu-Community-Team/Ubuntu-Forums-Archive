---
title: "error updating libc6 - breazy"
date: 2006-04-02
forum: Repositories &amp; Backports
---

### Post by wpollans on 2006-04-02
For the past few days I've been getting the following error when trying to update libc6:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.5-1ubuntu12.5.10.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.5-1ubuntu12.5.10.1_i386.deb)
  Error reading from server. Remote end closed connection


Could someone suggest a different repository to use?

Thanks

---

### Post by Xian on 2006-04-02
[QUOTE=wpollans]Could someone suggest a different repository to use?
[/QUOTE]

Just remove the preceeding 'us' and go with [http://archive.ubuntu.com](http://archive.ubuntu.com).

---

### Post by wpollans on 2006-04-03
OK, now I get:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.5-1ubuntu12.5.10.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.5-1ubuntu12.5.10.1_i386.deb)
  Error reading from server. Remote end closed connection [IP: 82.211.81.151 80]


I can't believe that I'm the only person who can't perform this update   :-(

Is it possible to just download the three packages (libc6, libc6-dev, libcr-i686) so I can install them with dpkg instead synaptic package manager?

---

### Post by wpollans on 2006-04-07
OK, I got the pkgs using "apt-get -d install libc6-i686" - if there was a failure of the type mentioned previously, I could just rerun the command till apt-get got everything.  It was easier than I thought  :-)

---

