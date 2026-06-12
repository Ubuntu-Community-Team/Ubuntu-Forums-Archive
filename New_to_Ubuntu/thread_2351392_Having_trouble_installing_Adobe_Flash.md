---
title: "Having trouble installing Adobe Flash"
date: 2017-02-02
forum: New to Ubuntu
---

### Post by jamesde93 on 2017-02-02
I've been trying to install Adobe Flash for the past week. 

From the Software Center I get this message:
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_24.0.0.186ubuntu0.16.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_24.0.0.186ubuntu0.16.04.1_i386.deb) 404  Not Found

From the terminal:
sudo apt install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'adobe-flashplugin' has no installation candidate

Can anyone help me out? Thanks!

---

### Post by deadflowr on 2017-02-02
You updates are out-of-date.
please run 
```
sudo apt update
```
post if any errors.

If no errors then retry installing flashplugin-installer


(The package adobe-flashplugin differs from the flashplugin-installer package and requires you to enable the Canonical Partners repository in Software and Updates)

---

### Post by jamesde93 on 2017-02-03
This worked good. Thank you very much!

---

