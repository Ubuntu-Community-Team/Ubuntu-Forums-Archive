---
title: "Install Firefox 8 tar.bz2 after extracting?"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by vsr1312 on 2011-11-09
i had downloaded firefox8.tar.bz2....and now i'm unable to figure out how should i install it

---

### Post by Frogs Hair on 2011-11-09
> **vsr1312 said:**
> i had downloaded firefox8.tar.bz2....and now i'm unable to figure out how should i install it

[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)


If that is the final version the PPA may be a better way ensure that updates are received . 

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install firefox
```

---

### Post by mikewhatever on 2011-11-09
You should not need to install it. The extracted binaries are all ready to use, that is, if you got the binaries.

The stable PPA doesn't have Firefox 8 yet.

---

### Post by oldos2er on 2011-11-09
OP moved to its own thread.

---

### Post by sikander3786 on 2011-11-09
Firefox specific installation instructions are here under the label 'Other Linux':

[http://www.tuxgarage.com/2011/08/firefox-6-stable-released-linux-ubuntu.html](http://www.tuxgarage.com/2011/08/firefox-6-stable-released-linux-ubuntu.html)

Make sure you replace '6.0' in all the commands with '8.0'.

As you are using Ubuntu, it doesn't make sense to install Firefox from a tar.bz2 package. Just wait for a few hours and Firefox 8 would be available in the stable PPA as mentioned above.

You didn't mention which version of Ubuntu you are using. If Natty or Oneiric, you don't even need to add the PPA as Firefox 8 would be available in the official repositories:

[http://www.tuxgarage.com/2011/11/firefox-8-ubuntu-linux-installation.html](http://www.tuxgarage.com/2011/11/firefox-8-ubuntu-linux-installation.html)

---

