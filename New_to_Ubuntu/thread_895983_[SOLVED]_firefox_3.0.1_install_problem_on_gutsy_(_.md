---
title: "[SOLVED] firefox 3.0.1 install problem on gutsy ( 7.10 )"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by mitza on 2008-08-20
hy! i have tried a lot of tricks to install the latest firefox on ubuntu 7.10 but it just doesn't seem possible! please help me install firefox 3.0.1 on gutsy so that  it has a menu icon like firefox 2 , and i am able to update it and install add-ons .

---

### Post by alienexplorers on 2008-08-20
Go to mozilla.com and download the program (3.0.1) and un pack it in Ubuntu Gutsy.  Run it and it should setup a .mozilla file in your home directory.  You will then be able to load the add-ons you want and will also give you the option of loading updates.

---

### Post by aysiu on 2008-08-20
> **mitza said:**
> hy! i have tried a lot of tricks to install the latest firefox on ubuntu 7.10 but it just doesn't seem possible! please help me install firefox 3.0.1 on gutsy so that  it has a menu icon like firefox 2 , and i am able to update it and install add-ons .
Can you describe what these "lot of tricks" are? And can you also paste (do not retype) these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here? ```
ls -l /usr/bin/firefox
ls /opt
cat /etc/lsb-release
```

---

### Post by mitza on 2008-08-20
well i tried installing it from the repositories, after enableing the pre-releases list ... but that unfortunately gave me an error and i couldn't install it.   in my second attempt i tried an instalation of the tar file but  when i tried to start firefox it told me that he couldn't find it.
in my third attempt i tried to uninstall firefox 2 fron the terminal and do an upgrade but that didn;t work either
 isn't out there somewere a .deb file that can be easely installed?? (i couldn't find one)

---

### Post by aysiu on 2008-08-20
> **mitza said:**
> well i tried installing it from the repositories, after enableing the pre-releases list ... but that unfortunately gave me an error and i couldn't install it.   in my second attempt i tried an instalation of the tar file but  when i tried to start firefox it told me that he couldn't find it.
in my third attempt i tried to uninstall firefox 2 fron the terminal and do an upgrade but that didn;t work either
 isn't out there somewere a .deb file that can be easely installed?? (i couldn't find one)
No .deb that I know of.

Try this:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

---

### Post by mitza on 2008-08-20
the script from that page worked seamlessly!! thank you very much.

---

