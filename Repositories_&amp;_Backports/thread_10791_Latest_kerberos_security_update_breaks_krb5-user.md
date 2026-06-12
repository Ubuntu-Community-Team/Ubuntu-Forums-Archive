---
title: "Latest kerberos security update breaks krb5-user"
date: 2005-01-11
forum: Repositories &amp; Backports
---

### Post by corydodt on 2005-01-11
I think this should say enough:

[INDENT]$ sudo apt-get dist-upgrade -su
Reading Package Lists... Done
Building Dependency Tree... Done
Calculating Upgrade... Done
The following packages will be REMOVED:
  krb5-user
The following packages will be upgraded:
  libkadm55 libkrb53
2 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Remv krb5-user (1.3.4-3 Ubuntu:warty)
Inst libkadm55 [1.3.4-3] (1.3.4-3ubuntu0.1 Ubuntu:4.10/warty-security) []
Inst libkrb53 [1.3.4-3] (1.3.4-3ubuntu0.1 Ubuntu:4.10/warty-security)
Conf libkrb53 (1.3.4-3ubuntu0.1 Ubuntu:4.10/warty-security)
Conf libkadm55 (1.3.4-3ubuntu0.1 Ubuntu:4.10/warty-security)[/INDENT]

But just in case it doesn't, I'll go into more detail.  I have 4 different servers configured with Kerberos packages and they all exhibit the same behavior.  This 
[security update](http://ubuntuforums.org/showthread.php?t=10691) specifically lists krb5-user as one of the updated packages.  However when I do an upgrade it does not upgrade krb5-user.  This tells me krb5-user is probably not in the Packages file in the security archive.

Further confirming this theory, "apt-get showpkg krb5-user" does not list a version from the security forum.

I have not done this security update yet because of this issue, and I'm sure I'm not alone, so that makes this problem itself a security issue.

---

### Post by nocturn on 2005-01-12
[QUOTE=corydodt]I think this should say enough:

[INDENT]$ sudo apt-get dist-upgrade -su
Reading Package Lists... Done
Building Dependency Tree... Done
Calculating Upgrade... Done
The following packages will be REMOVED:
  krb5-user
The following packages will be upgraded:
  libkadm55 libkrb53
2 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Remv krb5-user (1.3.4-3 Ubuntu:warty)
Inst libkadm55 [1.3.4-3] (1.3.4-3ubuntu0.1 Ubuntu:4.10/warty-security) []
Inst libkrb53 [1.3.4-3] (1.3.4-3ubuntu0.1 Ubuntu:4.10/warty-security)
Conf libkrb53 (1.3.4-3ubuntu0.1 Ubuntu:4.10/warty-security)
Conf libkadm55 (1.3.4-3ubuntu0.1 Ubuntu:4.10/warty-security)[/INDENT]

But just in case it doesn't, I'll go into more detail.  I have 4 different servers configured with Kerberos packages and they all exhibit the same behavior.  This 
[security update](http://ubuntuforums.org/showthread.php?t=10691) specifically lists krb5-user as one of the updated packages.  However when I do an upgrade it does not upgrade krb5-user.  This tells me krb5-user is probably not in the Packages file in the security archive.

Further confirming this theory, "apt-get showpkg krb5-user" does not list a version from the security forum.

I have not done this security update yet because of this issue, and I'm sure I'm not alone, so that makes this problem itself a security issue.[/QUOTE]


Ditto over here.  It has prevented me from installing the updates.

---

### Post by corydodt on 2005-01-12
**Workaround:**

You can download the missing file.  It's actually there, but as I said, not in the Packages file.  (They need to re-run the script that rebuilds Packages.gz I guess.)  Download the file to your apt cache dir manually, then apt-get install -d any other krb files you need to upgrade at the same time--I only needed libkrb53 and libkadm55--then install them with dpkg -i.

$ cd /var/cache/apt/archives
$ sudo apt-get clean
$ sudo wget  \
[http://security.ubuntu.com/ubuntu/pool/universe/k/krb5/krb5-user_1.3.4-3ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/k/krb5/krb5-user_1.3.4-3ubuntu0.1_i386.deb)
$ sudo apt-get install -d libkrb53 libkadm55
$ sudo dpkg -i libkrb53* libkadm55* krb5-user*

---

### Post by jdong on 2005-01-12
If this is still an issue, report it to [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com)

---

### Post by corydodt on 2005-01-13
Someone got there ahead of me.  See [https://bugzilla.ubuntu.com/show_bug.cgi?id=5452](https://bugzilla.ubuntu.com/show_bug.cgi?id=5452)

You can download the missing file. It's actually there, but as I said, not in the Packages file. Download the file to your apt cache dir manually, then apt-get install -d any other krb files you need to upgrade at the same time--I only needed libkrb53 and libkadm55--then install them with dpkg -i.

$ cd /var/cache/apt/archives
$ sudo apt-get clean
$ sudo wget \
[http://security.ubuntu.com/ubuntu/p...ntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/p...ntu0.1_i386.deb)
$ sudo apt-get install -d libkrb53 libkadm55
$ sudo dpkg -i libkrb53* libkadm55* krb5-user*

---

