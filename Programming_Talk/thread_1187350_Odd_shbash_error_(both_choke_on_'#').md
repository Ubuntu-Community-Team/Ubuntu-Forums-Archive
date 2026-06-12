---
title: "Odd sh/bash error (both choke on '#')"
date: 2009-06-14
forum: Programming Talk
---

### Post by altonbr on 2009-06-14
This is an excerpt of my program:

```
#!/bin/bash

# Banshee / https://launchpad.net/~banshee-team/+archive/ppa 
echo 'deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main' | sudo tee -a /etc/apt/sources.list.d/launchpad.list 
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 9D2C2E0A3C88DD807EC787D74874D3686E80C6B7
```These are the errors in 'sh' and 'bash':

> [B]sh /home/brett/my_programming/bash/ubuntu_assistant/20090614/jaunty-brett.sh 
#: not foundmy_programming/bash/ubuntu_assistant/20090614/jaunty-brett.sh: 2: [/B]
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 9D2C2E0A3C88DD807EC787D74874D3686E80C6B7
gpg: requesting key 6E80C6B7 from hkp server keyserver.ubuntu.com
gpg: key 6E80C6B7: "Launchpad PPA for Banshee Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1> [B]bash /home/brett/my_programming/bash/ubuntu_assistant/20090614/jaunty-brett.sh 
/home/brett/my_programming/bash/ubuntu_assistant/20090614/jaunty-brett.sh: line #: command not found[/B]
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 9D2C2E0A3C88DD807EC787D74874D3686E80C6B7
gpg: requesting key 6E80C6B7 from hkp server keyserver.ubuntu.com
gpg: key 6E80C6B7: "Launchpad PPA for Banshee Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1Am I missing something here? Why can 'sh' and 'bash' not recognized the shebang or my comment?

---

### Post by ibuclaw on 2009-06-14
What text editor are you using?

Regards
Iain

---

### Post by altonbr on 2009-07-17
> **tinivole said:**
> What text editor are you using?

Regards
Iain

gEdit

---

### Post by typedef on 2009-07-17
The file is probably saved with some weird encoding. Try this:

head -n1 *yourfile.sh* | od -x
0000000 2123 622f 6e69 622f 7361 0a68

Does the hex output match? If not, you may have a character encoding issue.


edit: Another useful trick you can use if you suspect you have non-printing characters in your base is cat -v filename.

---

