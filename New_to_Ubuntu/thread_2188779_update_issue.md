---
title: "update issue"
date: 2013-11-19
forum: New to Ubuntu
---

### Post by mikel2 on 2013-11-19
hi ther i update my linux with this commands since i no  update through the update managersudo apt-get upgrade, update and in the upload manager i still see a important update to install why?

---

### Post by Bucky Ball on 2013-11-19
You should be running:

```
sudo apt-get update
```

THEN:

```
sudo apt-get upgrade
```

You're doing them backwards (as far as I can work out from your post): ALWAYS 'update' before 'upgrade'. You may have to repeat the process.

PS: Try and make your posts a bit clearer by using a paragraph and spaces. Use [code] tags for terminal commands. The post here is a mess. ;)

---

### Post by mikel2 on 2013-11-19
i did. still 7 important updates on the update manager this is the message ive get

The following packages have been kept back:
linux-headers-generic-lts-quantal linux-image-generic-lts-quantal
linux-signed-image-generic-lts-quantal
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by Ghost_Mazal on 2013-11-19
I've have picked up also that > sudo apt-get upgrade does not update the kernels. I always have to update kernels via the update manager.
I have been told it is because it see the new kernel as a new app or something to that effect and that if you want to update kernels also via cli
you must use>  sudo apt-get dist-upgrade instead.

I have never done it that way myself though and always use update manager. So let's hear what other say first.

---

### Post by grahammechanical on 2013-11-19
It is not uncommon for packages to be kept back. There is nothing wrong. Certain packages need other packages to be installed at the same time otherwise the system will break. Sometimes those other packages are not yet available to be put in the repositories. So, the packages that are already available are held back. This often happens with kernel updates. Sometimes it will take two or three days for all the relevant kernel packages to get put in the repositories and allow the complete upgrade of the kernel to take place. One day you will see a message that there are packages that have been downloaded but not installed and that they will be installed as part of the apt-get upgrade instruction.

Regards.

---

### Post by philinux on 2013-11-19
> **mikel2 said:**
> hi ther i update my linux with this commands since i no  update through the update managersudo apt-get upgrade, update and in the upload manager i still see a important update to install why?

What you are seeing is the new behaviour called Phased Updates.

See these links.
[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

---

