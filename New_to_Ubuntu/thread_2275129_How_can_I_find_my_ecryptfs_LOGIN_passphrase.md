---
title: "How can I find my ecryptfs LOGIN passphrase?"
date: 2015-04-24
forum: New to Ubuntu
---

### Post by _sluimers_ on 2015-04-24
I had no idea there are two types of passphrases for ecryptfs. I saved my MOUNT passphrase, but I have no idea what my LOGIN passphrase is or whether I even have one.

Can anyone enlighten me on this?

---

### Post by dino99 on 2015-04-24
some explanations [http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

### Post by _sluimers_ on 2015-04-27
That's the tutorial I used to get my MOUNT passphrase. How do I get my LOGIN passphrase?

---

### Post by sudodus on 2015-04-27
When you installed the system, you entered the password (the login password) twice. With encryption, there is no back-door. You have to remember the password to log in.

There is 'Encrypted home with cryptswap', and when you mention 'ecryptfs', I think this is what you have, but I am not sure because you mention 'passphrase' too.

-o-

There is 'Encrypted disk' (LVM with encryption), where you get a passphrase to log into the encrypted disk. This passphrase is also entered twice, when you install such a system, and there is no back-door. You have to remember the passphrase to log in. (After logging into the disk you log into your user session.)

It is possible to create a system with both 'Encrypted disk' and 'Encrypted home with cryptswap'. Such a system is created and tested with the following testcase for Lubuntu:

[http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/92394/testcases/1439/results](http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/92394/testcases/1439/results)

-o-

There is a bug affecting cryptswap, see this bug report, [https://bugs.launchpad.net/ubuntu/+s...ls/+bug/953875]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875")

This bug is squashed for the new version 15.04 LTS, but if you try to install 'Encrypted home with cryptswap' from an iso file of a previous version, you will get problems, unless you are happy with a system without swap. (Do not create unencrypted swap, it is a security hole. It is possible after updating/upgrading to create cryptswap manually, but it is complicated.)

---

