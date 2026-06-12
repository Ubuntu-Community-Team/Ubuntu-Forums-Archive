---
title: "not able to sudo update"
date: 2018-07-29
forum: New to Ubuntu
---

### Post by gaurav+1 on 2018-07-29
```
user@user-Satellite-L850:~$ sudo apt-get update
[sudo] password for user: 
Ign:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty InRelease                     
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty InRelease                  
Ign:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates InRelease
Ign:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports InRelease
Ign:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security InRelease
Ign:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-proposed InRelease
Err:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty Release
  404  Not Found [IP: 91.189.88.161 80]
Err:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates Release
  404  Not Found [IP: 91.189.88.161 80]
Err:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-backports Release
  404  Not Found [IP: 91.189.88.161 80]
Err:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-security Release
  404  Not Found [IP: 91.189.88.161 80]
Err:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-proposed Release
  404  Not Found [IP: 91.189.88.161 80]
Reading package lists... Done
E: The repository 'http://archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty-backports Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu zesty-proposed Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
user@user-Satellite-L850:~$ apt-secure
apt-secure: command not found
```
I would be obliged if anyone could help me out

---

### Post by Taylz on 2018-07-29
Hi gaurav+1,

What version are you using? I'm assuming it looks as though you are using Zesty (possibly 17.04?) and support/updates for this version were discontinued. You need to upgrade your OS to the latest LTS.

Please refer to: [http://fridge.ubuntu.com/2018/01/17/ubuntu-17-04-zesty-zapus-reached-end-of-life-on-january-13-2018/](http://fridge.ubuntu.com/2018/01/17/ubuntu-17-04-zesty-zapus-reached-end-of-life-on-january-13-2018/)  - For the information regarding Zesty.



Regards,

Tayl.

---

### Post by Autodave on 2018-07-29
You need to install 18.04.  That is a LTS (long term service) release and will be updated for 5 years.  17.04 was not a LTS and only had 6 months of updates.  18.04 means that it was released in the 4th month of 2018.  17.04 was 4th month of 2017.  The next LTS release will be 20.04.

If you stay with a LTS release, you are good for 5 years. Otherwise, you are only good for 6 months until the next short term release is issued and then you would have to upgrade again.

At this point, you probably need to do a clean install of 18.04: don't try to upgrade to 18.04 from what you have now.  Back-up everything to an external source FIRST!

---

### Post by Impavidus on 2018-07-29
Indeed, clean install of 18.04 is the way to go. You can't upgrade your 17.04 as it's dead and its successor is dead too. 18.04 is an LTS release, which has 5 years of support (3 years for the lighter flavours). The interim releases have 9 months of support: 6 months until the next release and 3 months overlap to give users opportunity to upgrade.

---

