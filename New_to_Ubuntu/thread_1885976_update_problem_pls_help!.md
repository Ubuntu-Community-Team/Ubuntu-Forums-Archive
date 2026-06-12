---
title: "update problem pls help!"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by sabdullahi on 2011-11-24
hi! guys, pls am having problem when updating my ubuntu, can anyone help me please?
am using tohiba satellite and ubuntu 11 86x bit onerichi desktop version. 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.:confused:

---

### Post by fantab on 2011-11-24
> **sabdullahi said:**
> hi! guys, pls am having problem when updating my ubuntu, can anyone help me please?
am using tohiba satellite and ubuntu 11 86x bit onerichi desktop version. 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.:confused:

WELCOME to the forum!

Hit Ctrl+Alt+T to open Terminal and then run following commands one after another:

[INDENT]```
$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update

```


[/INDENT]

---

### Post by KazarSanaga on 2011-11-24
I was having a similar error message as sabdullahi and I tried the commands you posted, fantab.

It seems to cleared up most of it, but I still get this:
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A9E15C2F2B944FEE


---

### Post by fantab on 2011-11-25
> **KazarSanaga said:**
> I was having a similar error message as sabdullahi and I tried the commands you posted, fantab.

It seems to cleared up most of it, but I still get this:

Try this in Terminal:

> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys **A9E15C2F2B944FEE**

Replace error key (one in **bold face**) in the above command with one you are having problems with.

Hope this helps.

---

### Post by birdsarah on 2011-12-17
Thanks - this worked great for me! Was having problems with "Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release"

---

### Post by Gurtej22 on 2013-03-28
**W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0**
please helpeme

---

### Post by coffeecat on 2013-03-28
Old thread closed.

@Gurtej22, if you need help, please start your own new thread rather than posting to old, dead threads.

---

