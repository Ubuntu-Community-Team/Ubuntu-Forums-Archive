---
title: "unsafe ownership on configuration file"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-02-12
bump@bumpyputer:~$ sudo gpg --list-keys
[sudo] password for bump: 
gpg: WARNING: unsafe ownership on configuration file `/home/bump/.gnupg/gpg.conf'
bump@bumpyputer:~$

/home/bump/.gnupg/gpg.conf
listed under # Passphrase agent
    as uncommented  use-agent
the rest of the file is all commented.
What does this mean & how do I correct it?

---

### Post by oldos2er on 2012-02-12
See this thread: [http://ubuntuforums.org/showthread.php?t=1448524](http://ubuntuforums.org/showthread.php?t=1448524)

Short answer, that warning can be safely ignored.

---

### Post by lechien73 on 2012-02-12
This happens because you're running it with sudo. GPG is warning that the user you are running as is not the owner of the gpg.conf file.

GPG sees this as unsafe because it means that someone else (the file's owner) could manipulate the file, and it would be a potential security risk.

In other words - because you're running gpg as sudo, it's correct behaviour.

---

