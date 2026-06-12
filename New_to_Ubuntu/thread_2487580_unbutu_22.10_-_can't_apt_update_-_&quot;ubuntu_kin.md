---
title: "unbutu 22.10 - can't apt update - &quot;ubuntu kinetic Release' does not have a Release fi"
date: 2023-06-08
forum: New to Ubuntu
---

### Post by seso532 on 2023-06-08
I'm on ubuntu standalone, after fresh install I can't update and can't figure out how to resolve it. Guidance much appreciated.

Distributor ID: Ubuntu Description: Ubuntu 22.10 Release: 22.10 Codename: kinetic

uname: 5.19.0-43-generic

```
sergio@dkf23:~$ sudo apt update
[sudo] password for sergio: 
Hit:1 http://gb.archive.ubuntu.com/ubuntu kinetic InRelease
Hit:2 http://security.ubuntu.com/ubuntu kinetic-security InRelease             
Hit:3 http://gb.archive.ubuntu.com/ubuntu kinetic-updates InRelease            
Hit:4 http://gb.archive.ubuntu.com/ubuntu kinetic-backports InRelease          
Hit:5 https://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:6 https://download.sublimetext.com apt/stable/ InRelease                   
Ign:7 https://packagecloud.io/github/git-lfs/ubuntu kinetic InRelease          
Err:8 https://packagecloud.io/github/git-lfs/ubuntu kinetic Release       
  404  Not Found [IP: 2600:1f1c:2e5:6900:f8e6:a790:2559:42e4 443]
Reading package lists... Done
E: The repository 'https://packagecloud.io/github/git-lfs/ubuntu kinetic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by #&amp;thj^% on 2023-06-08
Kinetic EOL in April, what is your migration plan ...

---

### Post by ne29914 on 2023-06-08
You're being told that "packagecloud" is insecure (never heard of it). Why don't you use the official repositories?

---

### Post by guiverc on 2023-06-08
Did you open up [https://packagecloud.io/github/git-lfs/ubuntu](https://packagecloud.io/github/git-lfs/ubuntu) in a browser to explore the problem?

Did you check it was valid before adding it?

From what I can see, they provide *deb* package support only, and its somewhat dated too (*nothing in the last 6+ months so nothing as new as kinetic/22.10*)

---

### Post by seso532 on 2023-06-09
Cool, thanks a bunch for your help all, I didn't realize it was not official and the deb supported only. I deleted /etc/apt/sources.list.d/github_git-lfs.list.save and github_git-lfs.list and solved the prob.

@1fallen thanks for bringing EOL to my attention, I had not considered a higher version would have different LTS support, another got'cha for me ](*,)! I read downgrading to LTS 22.04 can be painful, so I'll think I'll upgrade to Lunar but I'd like to end up at LTS. I'll post this question in a new thread [https://ubuntuforums.org/showthread.php?t=2487588](https://ubuntuforums.org/showthread.php?t=2487588)

---

