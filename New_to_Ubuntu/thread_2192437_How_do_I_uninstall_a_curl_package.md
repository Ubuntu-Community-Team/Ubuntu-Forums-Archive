---
title: "How do I uninstall a curl package?"
date: 2013-12-07
forum: New to Ubuntu
---

### Post by r3bol on 2013-12-07
I installed a curl process on my raspberry pi, but now I want to remove it via the command line. 
I tried apt-get remove piJS but the os reports it was not able to locate the package. 

Any advice? 

The install command was...
curl [http://pijs.io/install-pijs.sh](http://pijs.io/install-pijs.sh) |bash

---

### Post by efflandt on 2013-12-07
Judging from reading that install script you likely need to stop that process if it is running, remove that init script, then remove the symlinks to that script, and it must be done in that order:```
sudo /etc/init.d/pijs stop
sudo rm /etc/init.d/pijs
sudo update-rc.d pijs remove
```

---

### Post by tgalati4 on 2013-12-07
This is the script:

```

#!/bin/sh

VERSION=0.1.1
PRECOMPILED=http://pijs.s3.amazonaws.com/pijs-precompiled-$VERSION.tar.gz

PING_INSTALL_1='http://io.tbideas.com/pijs/installing?precompiled=true'
PING_INSTALL_2='http://io.tbideas.com/pijs/install-done'

echo "# Installing piJS on this Raspberry Pi... (using precompiled binaries)"

echo "## Pinging stat server to record a new installation... (no personal info sent)"
curl $PING_INSTALL_1

echo "## Downloading package with nodejs, pi-blaster and dependencies ..."
curl $PRECOMPILED -o /tmp/pijs-precompiled.tar.gz

echo "## Installing nodejs and dependencies"
cd / && sudo tar zxvf /tmp/pijs-precompiled.tar.gz

echo "Configuring auto-start"
sudo cp /usr/local/lib/node_modules/pi-steroid/pijs-boot.sh /etc/init.d/pijs
sudo chmod +x /etc/init.d/pijs
sudo update-rc.d pijs defaults
**sudo /etc/init.d/pijs start**

echo "# Installation finished! Pinging stat server"
curl $PING_INSTALL_2


```

So it did not install a package.  But it did install a service *pijs*.

Try stopping it first:

```
sudo /etc/init.d/pijs stop
```

I have a raspberrypi, what does this service do?

You can look at the script /etc/init.d/pijs and see what binaries are called.  Then delete those one-by-one.

---

### Post by r3bol on 2013-12-07
Thanks, the 3 steps seemed to work. 

> **tgalati4 said:**
> I have a raspberrypi, what does this service do?

It is an in-browser, cloud based programming tool from [http://pijs.io/](http://pijs.io/) 
I gave it a try but didn't really have a use for it. Then I noticed it was a redundant service so I wanted to remove it. I develop on my pi with gedit over ssh.

---

