---
title: "Update error Hardy"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Blur-king on 2008-07-17
Hi,

I had the error message below during update. Any idea how to resolve this?. Thanks  

:???:

                                 W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)    

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by nowshining on 2008-07-17
open up a terminal

sudo apt-get update 
then
sudo apt-get upgrade

ur pw won't show as you type.

---

