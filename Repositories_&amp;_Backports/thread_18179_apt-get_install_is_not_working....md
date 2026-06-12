---
title: "apt-get install is not working..."
date: 2005-03-05
forum: Repositories &amp; Backports
---

### Post by ilankt on 2005-03-05
Hi everyone, I'm new to ubuntu, I searched your FAQ's and HOWTO's for my answer but it seems that there is nothing about my problem out there...
when I try to install something with apt-get install I get some weird errors...
here is the output:

sudo apt-get install nvidia-glx
Reading Package Lists... Done
Building Dependency Tree... Done
Package nvidia-glx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx has no installation candidate

what should I do?
Thanks.

---

### Post by lyly on 2005-03-05
How does your /etc/apt/source.list file look like?

This error means that apt know this package (via dependencies), be don't know where to get it. The package nvidia-glx is labelled "restricted" so you need to add multiverse key word in the source.list corresponding line. You can check this on
[http://higgs.djpig.de/ubuntu/www/](http://higgs.djpig.de/ubuntu/www/).

See my source.list file if I'm not clear enough (my english is sometime bad):

deb [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) hoary main restricted universe multiverse

deb-src [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) hoary main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

Lynda

---

### Post by DJ_Max on 2005-03-05
Don't use lyly sources unless you have Ubuntu 5.04 Hoary. 

The error message means either the package is gone, or name changed. Do
```
apt-cache search nvidia
```

---

