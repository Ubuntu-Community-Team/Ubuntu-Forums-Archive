---
title: "Have I lost my encrypted home data?"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by dupa on 2012-07-26
Hello,
I had a Ubuntu 11.10 and I upgraded it to 12.04.

At the installation it automatically created my home  as "crypted" and gave me a message at the first login, I don't remember what I did at that moment.

Now my Hard Disk has big hardware issue and Ubuntu doesn't boot anymore.

I attached that primary Hard Disk as secondary hard disk, I was trying to mount it to recover some data.

When I mount /home I see my home empty and it says it's crypted.

The only thing I know is my username password.

Have I lost the data on the crypted home?
(I just wonder when linux was booting, where did it find the key to decrypt my homedir, maybe is somewhere in /etc and accessible with the root user?)

Thanks

---

### Post by Bufeu on 2012-07-26
I just Googled:
[http://ubuntuforums.org/showthread.php?p=10208094](http://ubuntuforums.org/showthread.php?p=10208094)
[http://www.linux-mag.com/id/7568/3/](http://www.linux-mag.com/id/7568/3/)
[http://hype-free.blogspot.se/2011/04/recovering-encrypted-home-directory.html](http://hype-free.blogspot.se/2011/04/recovering-encrypted-home-directory.html)
[http://serverfault.com/questions/160277/ubuntu-how-to-decrypt-home-directory-swap-basically-everything-without-reins](http://serverfault.com/questions/160277/ubuntu-how-to-decrypt-home-directory-swap-basically-everything-without-reins)

---

### Post by oldfred on 2012-07-26
Another link:

[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)

With encryption, you have to be even more consistent on regular backups. The entire purpose of encryption is to prevent unauthorized access, so many repair tools do not work.

---

