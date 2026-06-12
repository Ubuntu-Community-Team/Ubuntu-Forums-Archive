---
title: "Apt Authentication issue???"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by php-zbatev on 2008-06-13
How do i fix this error:

[B]First I executed "Run this action"
[/B]Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".
**Then, I had this error:**
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://sa.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://sa.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


Please help thanks.

---

### Post by ukripper on 2008-06-13
> **php-zbatev said:**
> How do i fix this error:

[B]First I executed "Run this action"
[/B]Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".
**Then, I had this error:**
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://sa.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://sa.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


Please help thanks.

go to software sources and change the server and try again. ```
sudo apt-get update && sudo apt-get dist-upgrade
```

also can you post contents of the following:

```
gedit /etc/apt/sources.list
```

---

### Post by php-zbatev on 2008-06-14
Ok, thanks I'll try to find a new server...

---

### Post by ukripper on 2008-06-14
> **php-zbatev said:**
> Ok, thanks I'll try to find a new server...

you can try changing server from "Download From" and select the server.

and also I found this bug related to this on launchpad.
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234)

---

