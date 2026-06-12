---
title: "Where can I find the source code for PS?"
date: 2010-04-08
forum: Programming Talk
---

### Post by PanP5 on 2010-04-08
I'm trying to write a C++ program that uses the Linux kernel APIs to list all processes and process IDs. I figure "ps" is an obvious example to use. 

Anyone know where I can find it?

---

### Post by Bachstelze on 2010-04-08
ps is in the procps package, you can get the source code [here](http://archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.2.8.orig.tar.gz) or by doing

```
apt-get source procps
```

---

### Post by tgalati4 on 2010-04-08
which ps

cat /bin/ps

(It's binary so there is a bunch of gibberish, but I did find this link:  )

[http://procps.sourceforge.net/download.html](http://procps.sourceforge.net/download.html)

There should be some source code in there somewhere.

---

### Post by PanP5 on 2010-04-08
> **Bachstelze said:**
> ps is in the procps package, you can get the source code [here](http://archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.2.8.orig.tar.gz) or by doing

```
apt-get source procps
```

I did the command line argument and it says I may be missing a package. How do I figure out if it exists? (Sorry, new to linux)

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 335kB of source archives.
Get:1 http://us.archive.ubuntu.com intrepid-updates/main procps 1:3.2.7-9ubuntu2.1 (dsc) [1152B]
Get:2 http://us.archive.ubuntu.com intrepid-updates/main procps 1:3.2.7-9ubuntu2.1 (tar) [282kB]
Get:3 http://us.archive.ubuntu.com intrepid-updates/main procps 1:3.2.7-9ubuntu2.1 (diff) [52.2kB]
Fetched 335kB in 1s (223kB/s)  
sh: dpkg-source: not found
Unpack command 'dpkg-source -x procps_3.2.7-9ubuntu2.1.dsc' failed.
Check if the 'dpkg-dev' package is installed.
E: Child process failed
```

---

### Post by gmargo on 2010-04-08
The error message told you what to do - install the **dpkg-dev** package first.

---

### Post by tgalati4 on 2010-04-08
sudo apt-get install dpkg-dev

You might also need to add the source repositories to your /etc/apt/sources.list.

The easiest way to do this is to use the software manager and add repositories.

---

