---
title: "[SOLVED] Failure to refresh synaptic repository"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by noah8956 on 2008-09-09
hello,

I'm running 8.04.1 on my eeepc 901.  I'm having two issues which I think might be related. 

1)  First, I've been trying to install missing codecs for rhythmbox (gstreamer) and i get the following message:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.



2)  Second, I try to install new software through the Synaptic Package Manager (avidemux video editing) and it does not appear in the index.  So I try to refresh the index and I get the same error message.

Any help would be greatly appreciated!  

Thanks,

Noah

---

### Post by Faolan84 on 2008-09-10
Try using a different mirror (an officially sanctioned one), then once you have that you've done that try doing a refresh.

---

### Post by noah8956 on 2008-09-10
got it thanks!

---

### Post by Sef on 2008-09-10
Moved to absolute beginners.

---

### Post by parsim on 2008-09-15
Just FYI, this bug is tracked here:

[https://bugs.launchpad.net/ubuntu-eee/+bug/261022](https://bugs.launchpad.net/ubuntu-eee/+bug/261022)

and the fix is here:

[http://www.ubuntu-eee.com/index.php5?title=Fix_the_problem_with_upgrading_and_installing_software_in_Ubuntu_Eee_8.04.1](http://www.ubuntu-eee.com/index.php5?title=Fix_the_problem_with_upgrading_and_installing_software_in_Ubuntu_Eee_8.04.1)

---

