---
title: "Getting this error when running apt-get update?"
date: 2017-02-24
forum: New to Ubuntu
---

### Post by Joe_Martin on 2017-02-24
Is it ok to remove this file or is there another fix?  Thank you.

N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension

---

### Post by arochester on 2017-02-24
[https://askubuntu.com/questions/829370/n-ignoring-file-50unattended-upgrades-ucf-dist-in-directory-etc-apt-apt-con](https://askubuntu.com/questions/829370/n-ignoring-file-50unattended-upgrades-ucf-dist-in-directory-etc-apt-apt-con)

---

### Post by deadflowr on 2017-02-24
> **Joe_Martin said:**
> Is it ok to remove this file or is there another fix?  Thank you.

N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension

Yep.
You can either remove it or revert it to replace the current file or ignore it altogether.
It's only an annoying warning.

---

