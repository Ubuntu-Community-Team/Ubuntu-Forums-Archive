---
title: "missing package when installing gcc"
date: 2007-07-09
forum: Programming Talk
---

### Post by sdmike on 2007-07-09
I get some errors when installing the gcc compiler. I can't seem to find the packages

[COLOR="Red"]binaryjack@LittleSlave:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev libstdc++6-4.1-doc
The following NEW packages will be installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 7816kB of archives.
After unpacking 29.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main linux-libc-dev 2.6.17.1-11.35
  404 Not Found
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main libc6-dev 2.4-1ubuntu12.3 [                                                                             1852kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libstdc++6-4.1-dev 4.1.1-13ubuntu5                                                                              [1619kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main g++-4.1 4.1.1-13ubuntu5 [2573kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main g++ 4:4.1.1-6ubuntu3 [1434B]
Fetched 6045kB in 32s (186kB/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.1](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.1)                                                                             7/linux-libc-dev_2.6.17.1-11.35_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis                                                                             sing?
[/COLOR]

---

### Post by christhemonkey on 2007-07-09
I think you need to perform a:
```
sudo apt-get update 
```

As that file is there just at version 2.6.17.1-11.38_i386 instead of 2.6.17.1-11.35_i386.

---

### Post by sdmike on 2007-07-09
boy am I a noob. It worked like a charm thank you.

---

