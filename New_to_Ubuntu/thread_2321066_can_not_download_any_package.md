---
title: "can not download any package"
date: 2016-04-20
forum: New to Ubuntu
---

### Post by safa3 on 2016-04-20
hello
i can't download any package with "sudo apt-get install " ..
 i get the same output all the time "unable to locate this package "  so i tried "sudo apt-get update "
but i got an error

```
"Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty InRelease
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates InRelease
Err [http://repos.rcn-ee.com](http://repos.rcn-ee.com) trusty InRelease
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty Release.gpg
  Temporary failure resolving 'ports.ubuntu.com'
Err [http://repos.rcn-ee.com](http://repos.rcn-ee.com) trusty Release.gpg
  Temporary failure resolving 'repos.rcn-ee.com'
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) trusty-updates Release.gpg
  Temporary failure resolving 'ports.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty/InRelease](http://ports.ubuntu.com/ubuntu-ports/dists/trusty/InRelease)

W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/InR](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/InR)
elease

W: Failed to fetch [http://repos.rcn-ee.com/ubuntu/dists/trusty/InRelease](http://repos.rcn-ee.com/ubuntu/dists/trusty/InRelease)

W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty/Release.gpg](http://ports.ubuntu.com/ubuntu-ports/dists/trusty/Release.gpg)
  Temporary failure resolving 'ports.ubuntu.com'

W: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/Rel](http://ports.ubuntu.com/ubuntu-ports/dists/trusty-updates/Rel)
ease.gpg  Temporary failure resolving 'ports.ubuntu.com'

W: Failed to fetch [http://repos.rcn-ee.com/ubuntu/dists/trusty/Release.gpg](http://repos.rcn-ee.com/ubuntu/dists/trusty/Release.gpg)  Temp
orary failure resolving 'repos.rcn-ee.com'

W: Some index files failed to download. They have been ignored, or old ones used
 instead."
```

this is the output of source.list

```
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) trusty main universe multiverse
#deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) trusty main universe multiverse

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) trusty-updates main universe multiverse
#deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) trusty-updates main universe multiverse

#Kernel source ([repos.rcn-ee.com]("http://repos.rcn-ee.com/")) : [https://github.com/RobertCNelson/linux-stable-rcn-ee](https://github.com/RobertCNelson/linux-stable-rcn-ee)
#
#git clone [https://github.com/RobertCNelson/linux-stable-rcn-ee](https://github.com/RobertCNelson/linux-stable-rcn-ee)
#cd ./linux-stable-rcn-ee
#git checkout `uname -r` -b tmp
#
deb [arch=armhf] [http://repos.rcn-ee.com/ubuntu/](http://repos.rcn-ee.com/ubuntu/) trusty main
#deb-src [arch=armhf] [http://repos.rcn-ee.com/ubuntu/](http://repos.rcn-ee.com/ubuntu/) trusty main
```

how can i fix this ... i followed some tuto but still the same problem 

Regards

---

### Post by Bucky Ball on 2016-04-20
Welcome. What package are you trying to install?

Please share a link to whatever tutorial you are following. Will give you a better chance of support than 'some tutorial ...'. ;)).

(Note: Randomly installing PPAs is not recommended. They are not officially supported by Canonical and use at your own risk. Their health is the responsibility of the maintainer of that PPA solely. Copying code when you're not really sure what the consequences are is also not advisable. If you're ever in doubt you can always ask here first (providing a link to the tutorial).)

* Update; I realise there is something else going on now. See next post.

---

### Post by Bucky Ball on 2016-04-20
Just re-read your post. That is the entire sources.list file??? Where did you download the ISO of Ubuntu? If it was [here]("https://github.com/RobertCNelson/linux-stable-rcn-ee") then no wonder your sources.list look obscure! 

[Try here.]("http://www.ubuntu.com/download")

Looks like you may have been on a merry chase. Let's see if we can figure it out. Please provide the link to where you downloaded the ISO and any other details you think might be relevant. :D

---

### Post by safa3 on 2016-04-20
i'm actually wokring with an omap5432 board .. i download [COLOR=#000000][FONT=Arial]Ubuntu 14.04 LTS as a file system from [/FONT][/COLOR]https://rcn-ee.com/rootfs/eewiki/minfs/ubuntu-14.04.4-minimal-armhf-2016-04-02.tar.xz 
so yes this is my entire sources.list 

for me i need xen-tools and bridge-utils packages and some other dependencies

---

### Post by grahammechanical on 2016-04-20
One of my early thoughts was that the repositories in your sources.list file did not exist. But I have been able to access them. So, they do exist. I am now thinking that those repositories do not contain the packages that you are trying to install. Or the servers may have been offline for maintenance or some other reason. Or a combination of both.

[http://repos.rcn-ee.com/ubuntu/dists/trusty/](http://repos.rcn-ee.com/ubuntu/dists/trusty/)

[http://ports.ubuntu.com/dists/trusty/](http://ports.ubuntu.com/dists/trusty/)

Regards.

---

