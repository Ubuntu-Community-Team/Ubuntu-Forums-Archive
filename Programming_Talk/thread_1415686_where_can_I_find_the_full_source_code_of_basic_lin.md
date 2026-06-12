---
title: "where can I find the full source code of basic linux programs?"
date: 2010-02-25
forum: Programming Talk
---

### Post by guest_user on 2010-02-25
like ls, grep, cat, less, etc?

---

### Post by ssam on 2010-02-25
first track down where they come from.
```

sam@hydrogen:~$ which ls
/bin/ls
sam@hydrogen:~$ dpkg -S /bin/ls
coreutils: /bin/ls
sam@hydrogen:~$ dpkg -S /bin/grep
grep: /bin/grep

```

so /bin/ls is in coreutils (note that most shells have a built in ls command), and /bin/grep is in its own package.

now you can use apt to grab the ubuntu source package.

```

sam@hydrogen:/tmp$ cd /tmp
sam@hydrogen:/tmp$ apt-get source coreutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 9,729kB of source archives.
Get: 1 http://gb.archive.ubuntu.com karmic/main coreutils 7.4-2ubuntu1 (dsc) [1,244B]
Get: 2 http://gb.archive.ubuntu.com karmic/main coreutils 7.4-2ubuntu1 (tar) [9,709kB]
Get: 3 http://gb.archive.ubuntu.com karmic/main coreutils 7.4-2ubuntu1 (diff) [19.2kB]
Fetched 9,729kB in 0s (9,939kB/s)    
gpgv: Signature made Tue 06 Oct 2009 11:24:17 BST using DSA key ID 5E0577F2
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./coreutils_7.4-2ubuntu1.dsc
dpkg-source: info: extracting coreutils in coreutils-7.4
dpkg-source: info: unpacking coreutils_7.4.orig.tar.gz
dpkg-source: info: applying coreutils_7.4-2ubuntu1.diff.gz
sam@hydrogen:/tmp$ ls coreutils*
coreutils_7.4-2ubuntu1.diff.gz  coreutils_7.4.orig.tar.gz
coreutils_7.4-2ubuntu1.dsc

```

or track down the upstream project and download the source code (usually a tar.gz or tar.bz file)

---

### Post by Rany Albeg on 2010-02-25
Very nice :)
Thank you very much.

---

