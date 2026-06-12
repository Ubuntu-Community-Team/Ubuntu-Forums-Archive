---
title: "Messed up my update manager"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by Angel3D on 2011-09-23
I cannot get anymore updates for my ubuntu. every time i try to get updates I get the following errors:
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.171 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.171 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Can someone help me fix this I am a new with ubuntu...I am in the process of downloading ubuntu 10 as I am running 9.04 but thought that there could be an easy fix for this?

thanks!

---

### Post by philipballew on 2011-09-23
paste the terminal output of

 ```
cat /etc/apt/sources.list 

```

---

### Post by wolfen69 on 2011-09-23
Those errors are because they are for jaunty. You need to get rid of those entries. Open Synaptic and go to Settings > Repositories. Get rid of all the jaunty stuff. Then
```
sudo apt-get update
```

---

### Post by mörgæs on 2011-09-23
If the upgrade works, you will (through the 9.10-upgrade) end with 10.04 on Grub 1 and ext3. 

If you are thinking of Grub 2 and / or ext4, a fresh install is worth considering.

---

### Post by Angel3D on 2011-09-23
Resolved. I just went ahead an installed 10.4 no more issues.
Thanks!

---

### Post by Rubi1200 on 2011-09-23
If the problem is resolved please mark this thread Solved using the Thread Tools near the top of the page.

And enjoy all your Ubuntu experiences :-)

---

