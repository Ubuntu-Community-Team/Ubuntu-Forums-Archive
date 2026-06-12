---
title: "sudo apt-get update command producing error messages"
date: 2018-11-06
forum: New to Ubuntu
---

### Post by esc123 on 2018-11-06
Hi,

Yesterday I installed the latest LTS ubuntu version (18.04) from the main ubuntu website on my PC in a Dual boot setup. Primary OS is windows 10 pro. Today I was attempting to install Emacs on Ubuntu using the terminal using the sudo apt-get command but that was not working and the prompt suggested I enter sudo apt-get update. When I executed this command a long list of errors were printed to the terminal. They are as follows

```
~$ sudo apt-get update
Ign:1 [http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu](http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu) bionic InRelease
Ign:2 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease        
Hit:4 [http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu](http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu) bionic InRelease
Ign:5 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) bionic-updates InRelease       
Ign:6 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) bionic-backports InRelease          
Err:7 [http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu](http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu) bionic Release    
  404  Not Found [IP: 91.189.95.83 80]
Err:8 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) bionic Release
  404  Not Found [IP: 2001:770:18:aa40::c101:c145 80]
Err:9 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) bionic-updates Release
  404  Not Found [IP: 2001:770:18:aa40::c101:c145 80]
Err:10 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) bionic-backports Release
  404  Not Found [IP: 2001:770:18:aa40::c101:c145 80]
Reading package lists... Done                      
E: The repository 'http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ie.archive.ubuntu.com/ubuntu bionic Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ie.archive.ubuntu.com/ubuntu bionic-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ie.archive.ubuntu.com/ubuntu bionic-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```


I have searched for some of the errors but I can't find anyone experiencing the same issues using 18.04 hence I can't find a solution to the problem.

Any ideas on what could be causing this?

---

### Post by deadflowr on 2018-11-06
The hanipouspilot ppa has no bionic packages in it, so remove the ppa.
And the ie.archive.ubuntu.com mirror seems to be having issues.

You can switch to a different mirror and see how that works.
[https://askubuntu.com/questions/682532/how-do-i-switch-to-a-closer-ubuntu-mirror]("https://askubuntu.com/questions/682532/how-do-i-switch-to-a-closer-ubuntu-mirror")
The link is for 14.04 but works the same on 18.04.

---

### Post by esc123 on 2018-11-07
Deleted the hanipouspilot PPA and changed the mirror as suggested. Everything seems to be working fine now. Thanks!

---

### Post by oldos2er on 2018-11-09
Would you please mark your thread 'Solved' under Thread Tools at the top of the page? It will assist others with the same problem. Thanks.

---

