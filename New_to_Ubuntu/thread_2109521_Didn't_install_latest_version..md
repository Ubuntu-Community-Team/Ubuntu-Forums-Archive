---
title: "Didn't install latest version."
date: 2013-01-27
forum: New to Ubuntu
---

### Post by nsingh on 2013-01-27
I installed subversion using Ubuntu software Center. I did not install latest version for me. 
I have seen that usually Ubuntu Software Center does not have latest version of software. 

Is there any way to control it using Ubuntu Software Center ?

---

### Post by 3rdalbum on 2013-01-27
Yes; it's possible to add new repositories to your Ubuntu system, containing versions of software packaged by ordinary people. These versions might be newer than in Software Center, compiled with more experimental options than Software Center, or simply be of programs that are not available in the ordinary Ubuntu repositories.

Try doing a Google search for "Subversion PPA" or "Subversion repository ubuntu" and look at any recent results.

---

### Post by jorok_tupur on 2013-01-28
This is the Subversion team's PPA:

[https://launchpad.net/~svn/+archive/ppa](https://launchpad.net/~svn/+archive/ppa)

 To install packages from the PPA, type this in the terminal:

```
sudo add-apt-repository ppa:svn/ppa
sudo apt-get update
```After this, the newer Subversion should be available. You can upgrade to the newer version.

---

