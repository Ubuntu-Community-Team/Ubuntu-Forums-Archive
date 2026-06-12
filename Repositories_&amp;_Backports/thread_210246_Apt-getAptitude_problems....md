---
title: "Apt-get/Aptitude problems..."
date: 2006-07-06
forum: Repositories &amp; Backports
---

### Post by mmcclure79 on 2006-07-06
When I run either I get Error 111 connection refused, but I have no problems at my fathers house so I know it's not my system. I'm figuring it's my ISP blocking a port. I understand apt-get goes out on port 80 (so that's not the problem), but does the repositories reply on a certain port as well or is it a random port?

---

### Post by ciscosurfer on 2006-07-06
Can you hit any sites on the Web through a browser?

---

### Post by mmcclure79 on 2006-07-06
oh yeah no problems with that. I can even hit the repository sites with the browser,but it's a no go if apt* tries it. I even saw where someone had their router blocking key words and checked that out and I'm not doing that.

sudo apt-get update
```

Err http://security.ubuntu.com breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Ign http://security.ubuntu.com breezy-security Release
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://security.ubuntu.com breezy-security/multiverse Packages
Err ftp://cipherfunk.org breezy Release.gpg
  Could not connect to cipherfunk.org:21 (127.255.102.184). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/main Packages
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/universe Packages
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Ign ftp://cipherfunk.org breezy Release
Err http://security.ubuntu.com breezy-security/multiverse Packages
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Ign ftp://cipherfunk.org breezy/main Packages
Err http://archive.ubuntu.com breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err ftp://cipherfunk.org breezy/main Packages
  Could not connect to cipherfunk.org:21 (127.255.102.184). - connect (111 Connection refused)
Ign http://archive.ubuntu.com breezy Release
Ign http://archive.ubuntu.com breezy-updates Release
Ign http://archive.ubuntu.com breezy/main Packages
Ign http://archive.ubuntu.com breezy/restricted Packages
Ign http://archive.ubuntu.com breezy/universe Packages
Ign http://archive.ubuntu.com breezy/multiverse Packages
Ign http://archive.ubuntu.com breezy-updates/main Packages
Ign http://archive.ubuntu.com breezy-updates/restricted Packages
Ign http://archive.ubuntu.com breezy-updates/universe Packages
Ign http://archive.ubuntu.com breezy-updates/multiverse Packages
Err http://archive.ubuntu.com breezy/main Packages
  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy/restricted Packages
  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy/universe Packages
  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy/multiverse Packages
  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-updates/main Packages
  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-updates/restricted Packages
  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-updates/universe Packages
  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-updates/multiverse Packages
  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch ftp://cipherfunk.org/pub/packages/ubuntu/dists/breezy/Release.gpg  Could not connect to cipherfunk.org:21 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch ftp://cipherfunk.org/pub/packages/ubuntu/dists/breezy/main/binary-i386/Packages.gz  Could not connect to cipherfunk.org:21 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz  Could not connect to archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

of course my sources.list file
```

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ breezy main

```

---

### Post by aysiu on 2006-07-06
[This](http://www.ubuntuforums.org/archive/index.php/t-78125.html) may help.

---

### Post by mmcclure79 on 2006-07-07
Looks good, I'll try some of that out. But I did notice that the user in question was not resolving the URLs properly instead they were coming up with his lo.

---

### Post by mmcclure79 on 2006-07-11
WEll it seems a fter installing Xubuntu (Dapper) over Ubuntu (Breezy) that I can now connect to the modem and get apt-get working. So I went out and bought a new and better router so lets hope that this works...

---

### Post by denschmitz on 2006-08-13
I am having the exact same problem, so if you figure out what's happening, please let me know.

---

### Post by pcfixer on 2006-08-18
I am new to Ubuntu. I have used a lot of the other versions. I was having that problem. Looked at my router settings and the box was checked to block key words. There were no words there but it still blocked the connection. Un-checked the box and presto.........now I can connect to the repo's:-D  Hope this helps you. I am using a Netgear Wireless Router (WGT624)

---

### Post by jerrytown on 2006-08-25
I had this problem also, and it turned out to be a router issue for me too.  When I first set up my Debian box I was still allowing my router (Linksys WRT54G) to assign IP addresses to the computers in my house.  Apt-get worked fine under these conditions.  Later I set up a static IP between the Debian box and the router so that I could direct SSH traffic to it.  Apparently, since apt-get was seeking out http servers for downloads of new software it required that port 80 (the http port) be directed to it also.  On my router these settings are under "Applications and Gaming" then "Port Range Forward".  Note: if you're using ftp servers I think it will need to be directed to port 21.

---

### Post by bruban on 2007-07-06
I had the same problem on a Debian 4.0 server that I use as a firewall.

The resolution was that I had to allow outgoing connections from that server via TCP port 80.

Bruce

---

