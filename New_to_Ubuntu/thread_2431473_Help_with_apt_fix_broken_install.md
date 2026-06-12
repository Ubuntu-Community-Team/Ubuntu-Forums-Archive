---
title: "Help with apt fix broken install"
date: 2019-11-17
forum: New to Ubuntu
---

### Post by steezy on 2019-11-17
Hello Newbie to Ubuntu...

   This is the error i get when I try to run 

```
sudo apt --fix broken install
```


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-aws-tools-5.3.0-1008
The following NEW packages will be installed:
  linux-aws-tools-5.3.0-1008
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
17 not fully installed or removed.
Need to get 5,496 kB of archives.
After this operation, 25.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu eoan-proposed/main amd64 linux-aws-tools-5.3.0-1008 amd64 5.3.0-1008.9 [5,496 kB]
Fetched 5,496 kB in 4s (1,495 kB/s)                     
(Reading database ... 315265 files and directories currently installed.)
Preparing to unpack .../linux-aws-tools-5.3.0-1008_5.3.0-1008.9_amd64.deb ...
Unpacking linux-aws-tools-5.3.0-1008 (5.3.0-1008.9) ...
dpkg: error processing archive /var/cache/apt/archives/linux-aws-tools-5.3.0-100
8_5.3.0-1008.9_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libcpupower.so.5.3.0-1008', which is also in pack
age linux-gcp-tools-5.3.0-1008 5.3.0-1008.9
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-aws-tools-5.3.0-1008_5.3.0-1008.9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Any insight on figuring out exactly what to look for would be greatly appreciated. Thank You

---

### Post by Impavidus on 2019-11-18
The packages linux-aws-tools-5.3.0-1008 and linux-gcp-tools-5.3.0-1008 can't be both installed at the same time. There is a package conflict between them. This rarely happens between packages from the official repositories. One of them must go, along with its dependencies.

I notice that your linux-aws-tools-5.3.0-1008 is from the proposed repository. People enable the proposed repository to test upgrades before they are put in the main repositories (which I wouldn't recommend to beginners) or if they urgently need a bugfix, and in that case only to get one particular package and its dependencies.

So unless you have a good reason to enable the proposed repository, I suggest you disable it and remove or downgrade all packages (and dependencies) you got from it.

I haven't upgraded to eoan myself yet and have some difficulty to find the details.

---

### Post by SeijiSensei on 2019-11-18
The man page for apt doesn't show fix-broken as an option, but it is an option for apt-get. Also it should be --fix-broken:

```
sudo apt-get --fix-broken install packagename
```

---

