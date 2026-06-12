---
title: "Could not download all repository indexes"
date: 2006-06-20
forum: Repositories &amp; Backports
---

### Post by melb steven on 2006-06-20
Hi All,
When I start synaptic I get the following.



W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

When I do a reload I get.

[http://au.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not resolve 'http'
[http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Could not resolve 'http'
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Could not resolve 'http'
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) Could not resolve 'http'
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:) Could not resolve 'http'
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:) Could not resolve 'http'
[http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz:) Could not resolve 'http'
[http://au.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) Could not resolve 'http'
[http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) Could not resolve 'http'
[http://au.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Could not resolve 'http'
[http://au.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:) Could not resolve 'http'
[http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) Could not resolve 'http'
[http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) Could not resolve 'http'
[http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz:) Could not resolve 'http'
[http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz:) Could not resolve 'http

My sources.list is

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

I have done the key thing but it doesn't help. Any ideas would be welcome.

---

### Post by bikeboy on 2006-06-20
Can you get on the internet through Firefox?
The actual sources in the file looks the same as mine.

---

### Post by melb steven on 2006-06-20
Yes, Firefox is fine. I can go to those places by browser. I have set the proxy in synaptic, firefox and the system. I can ping the repositories.

---

### Post by bikeboy on 2006-06-20
Ok, try making a backup of your current sources.list file and then replace all the "http://au.archive etc" with:
"ftp://mirror.pacific.net.au/linux/ubuntu breezy main restricted" etc

---

### Post by melb steven on 2006-06-25
Hi,

no good.

lots of this

W: Couldn't stat source package list [ftp://mirror.pacific.net.au](ftp://mirror.pacific.net.au) breezy/main Packages (/var/lib/apt/lists/mirror.pacific.net.au_linux_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)

Then this

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

---

