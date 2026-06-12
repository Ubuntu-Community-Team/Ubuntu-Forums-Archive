---
title: "Problems with updating package list, installing and upgrading software"
date: 2014-07-16
forum: New to Ubuntu
---

### Post by msschambach on 2014-07-16
Hi guys, ):P been using ubuntu 14.04 for about 2 and a half months now. Recently I started having problems with upgrading software and even installing new software. When I run ```
sudo apt-get update 
``` the console spits the following out at the end:

```
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/restricted amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages)
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

```

And when I run ```
sudo apt-get upgrade
``` the console spits out pretty much the same thing. 
To add to all that, I can't start synaptic package manager. It closes immediately after it launches with the following error: 

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/restricted amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages)
```

I've been googling for weeks but I still have no idea how to fix this. It all started when one day I wanted Totem to be able to play mp4 videos(even though I'd installed restricted extras) because it was always giving this error: 
Videos requires to install plugins to play files of the following types:
[LIST]
[*]MPEG-4 AAC decoder
[*]H.264 decoder
[/LIST]

So when it scanned and found the packages to install, I went ahead and installed them(can't remember what they were). I found out though after installing them that not only was the problem not fixed, installing them had uninstalled vlc! So I tried to reinstall vlc to no avail and it was only when I tried with aptitude that it worked. At that time apt-get was telling me that I had held broken packages. After several trials and much googling, I was able to release them but lo and behold I got the above errors. Please help, I can't afford to format my computer right now and reinstall ubuntu afresh.

---

### Post by chris5pens on 2014-07-16
I'm getting a similar problem whenever updating and installing packages on Xubuntu 14.04

Setting up apt (1.0.1ubuntu2.1) ...
dpkg: error processing package apt (--configure):
 cannot compute MD5 hash for file '/etc/cron.daily/apt': failed to read (Input/output error)
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)

Same message every time.


Chris

---

### Post by chris5pens on 2014-07-16
Just found this at [http://serverfault.com/questions/368669/debian-ubuntu-is-it-possible-to-reinitialize-var-lib-apt-lists-and-var-apt-cac](http://serverfault.com/questions/368669/debian-ubuntu-is-it-possible-to-reinitialize-var-lib-apt-lists-and-var-apt-cac) - it worked for me:

$ rm -r /var/cache/apt /var/lib/apt/lists
$ apt-get update #takes a while re-fetching everything
$ apt-get install <some-random-package>

Chris

---

### Post by Old_Grey_Wolf on 2014-07-16
If what chris5pens posted doesn't work; then, post the output of the command below so that someone can determine the cause of the problem:
```
cat /etc/apt/sources.list
```

---

### Post by msschambach on 2014-07-17
Thanks chris5pens! That totally worked, I can install stuff and update again! :KS

---

