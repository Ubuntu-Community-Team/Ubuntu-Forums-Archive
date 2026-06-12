---
title: "unable to update"
date: 2018-11-02
forum: New to Ubuntu
---

### Post by mr-mister on 2018-11-02
Hi, i was trying to install boot repair for this other [problem]("https://ubuntuforums.org/showthread.php?t=2405150"), but when i try to update i get this 
```

Ign:1 cdrom://Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412) zesty InRelease
Hit:2 cdrom://Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412) zesty Release
Ign:4 http://archive.ubuntu.com/ubuntu zesty InRelease                         
Ign:5 http://security.ubuntu.com/ubuntu zesty-security InRelease               
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu zesty InRelease [15.4 kB]
Ign:7 http://archive.ubuntu.com/ubuntu zesty-updates InRelease                 
Err:8 http://security.ubuntu.com/ubuntu zesty-security Release           
  404  Not Found [IP: 91.189.88.149 80]
Err:9 http://archive.ubuntu.com/ubuntu zesty Release                     
  404  Not Found [IP: 91.189.88.149 80]
Get:10 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu zesty/main amd64 Packages [464 B]
Err:11 http://archive.ubuntu.com/ubuntu zesty-updates Release                  
  404  Not Found [IP: 91.189.88.149 80]
Get:12 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu zesty/main Translation-en [692 B]
Reading package lists... Done                      
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```
And if i try to install boot-repair it can't locate it. I did add the corresponding repository. I am running from a live ubuntu 17.10

---

### Post by ajgreeny on 2018-11-02
17.04 has been out of support since around January this year so it will not be possible to update normally as the repos have now moved to another url.

You must upgrade to a supported version; I suggest 18.04.1 which will then be supported until 2023.

---

