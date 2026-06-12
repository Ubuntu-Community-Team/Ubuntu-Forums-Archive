---
title: "g++ compiler not found in ubuntu 12.10"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by musharraf on 2013-01-14
Hi all,

I installed ubuntu 12.10 but i didn't find g++ compiler in my system. I installed NetBeans 7.2.1 with C++ features but it giving compiler error... duing code compilation of C++.

Let me how I can solve this issue.

---

### Post by codemaniac on 2013-01-14
> **musharraf said:**
> Hi all,

I installed ubuntu 12.10 but i didn't find g++ compiler in my system. I installed NetBeans 7.2.1 with C++ features but it giving compiler error... duing code compilation of C++.

Let me how I can solve this issue.

build-essential contains a list of packages which are essential for building Ubuntu packages including g++ compiler, make and other required tools.

Please run the following in your terminal.
```
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install build-essential
```

---

### Post by musharraf on 2013-01-14
Hi codemaniac,

I run all these three commands on terminal, but unfortunately not success.

Status of all commands:

1- Some update not found.
2- Nothing to be upgraded everything is latest version
3-Unable to locate 'build-essential'

Note : I have ubuntu 12.10

Thanks

---

### Post by Cheesemill on 2013-01-15
Can you copy and paste the *exact* output of the commands please. Without it we don't know what's going on.

---

### Post by iMac71 on 2013-01-15
you can find g++ in [gcc-defaults]("https://launchpad.net/ubuntu/quantal/+source/gcc-defaults"); run the following commands in a Terminal:```
sudo apt-get update -y && sudo apt-upgrade -y && sudo apt-get install -y gcc-defaults
```

---

