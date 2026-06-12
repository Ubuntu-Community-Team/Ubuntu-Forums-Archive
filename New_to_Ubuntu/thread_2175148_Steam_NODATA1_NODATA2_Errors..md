---
title: "Steam NODATA1 NODATA2 Errors."
date: 2013-09-17
forum: New to Ubuntu
---

### Post by nvmaleski on 2013-09-17
I ran the apt-get update command but it would stop checking for updates after it started checking for steam updates. I would get the error NODATA1 NODATA2. I uninstalled steam, and ran the command again and it responded with the error, signatures invalid. I checked /usr/bin and it doesn't seem like there are any traces of steam left, why does it think steam is still installed and how do I fix this? Thanks!

---

### Post by cariboo on 2013-09-18
Check System Settings->Software Sources->Other Software to see if the repositories are still enabled.

---

### Post by nvmaleski on 2013-09-18
This is, uh, a little embarrasing. But, I am in the System Setting menu and there doesn't seem to be any 'Software Sources'.

---

### Post by nvmaleski on 2013-09-18
```
W: GPG error: http://repo.steampowered.com precise Release: The following signatures were invalid: BADSIG F24AEA9FB05498B7 Valve Corporation <linux@steampowered.com>
```
I realized I was being a little vague. Here's the complete error as it shows up in bash.

---

### Post by nvmaleski on 2013-09-18
Solved it! Followed these commands [http://itsfoss.com/solve-badsig-error-quick-tip/](http://itsfoss.com/solve-badsig-error-quick-tip/) and it's all working fine now.

---

