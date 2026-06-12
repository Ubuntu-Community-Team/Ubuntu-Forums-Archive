---
title: "pitivi ubuntu update error"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-12-22
I tried to install piviti.
When updating just now I got this error:
W: GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://www.remastersys.com](http://www.remastersys.com) precise Release: The following signatures were invalid: BADSIG B6068D255563B350 Tony Brijeski (Remastersys Key) <tb6517@yahoo.com>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  
W: Some index files failed to download. They have been ignored, or old ones used instead.

Then when I try to run piviti I get error msg:
Could not initiate the video output plugins
Make sure you have at least one valid video output sink available (xvimagesink or ximagesink).

---

### Post by oldos2er on 2013-12-22
Run the following commands one at a time in a terminal:

$ sudo -i
# apt-get clean
# cd /var/lib/apt
# mv lists lists.old
# mkdir -p lists/partial
# apt-get clean
# apt-get update

---

### Post by Kevin McCready on 2013-12-22
Thanks Ann
I did all that. I then shutdown the computer and rebooted. I still get the pitivi (not piviti) error msg. When I did the last update command in your recipe, it ended with the following error:
W: Failed to fetch [http://www.remastersys.com/ubuntu/dists/precise/main/source/Sources](http://www.remastersys.com/ubuntu/dists/precise/main/source/Sources)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by oldos2er on 2013-12-23
There's no need to reboot really; any changes you make to sources.list are committed the next time *sudo apt-get update* is run.

I'd remove the remastersys repository since it's no longer supported. See [http://www.remastersys.com/](http://www.remastersys.com/)

---

