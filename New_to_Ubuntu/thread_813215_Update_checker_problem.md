---
title: "Update checker problem"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by SamerBerjawi on 2008-05-30
Everytime I try to check for new updates I get the following:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by bjm1904 on 2008-05-30
Make sure you have the relevant repositories enabled:

System > Administration > Sofware Sources

And make sure that 'security' and 'recommended' are checked.

Assuming it's not that simple, then what you're missing is a GPG key. This is a known Ubuntu bug:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/215694](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/215694)

It's not exactly what you're looking for, but I think you'll find the information helpful.

---

### Post by SamerBerjawi on 2008-05-31
All my sources are checked, i'll try the link you gave me.
Thank you

---

