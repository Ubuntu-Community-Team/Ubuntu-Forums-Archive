---
title: "Vista loader not selectable after 10.04 install"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by Teratogenesis on 2012-03-20
deleted

---

### Post by oldfred on 2012-03-20
Welcome to the forums.

With Vista grub2 often reversed the entries for Vista and Vista recovery. I have not seen it load memory instead?

Post boot info script to see entire configuration.

Easy way to run boot script:
Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

You can directly download it also. There is a newer version in testing/git that has some fixes:
The git/testing version has some fixes:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

---

