---
title: "Where's the bin86 package?"
date: 2005-02-16
forum: Repositories &amp; Backports
---

### Post by ulfs on 2005-02-16
I'm following the instructions from the KernelByHandHowto and it says I need to install bin86 and libncurses-dev packages. Neither of these is found by "apt-get install". I found the libncurses5-dev and downloaded it manually from [http://archive.ubuntu.com/ubuntu/pool](http://archive.ubuntu.com/ubuntu/pool), but I can't find the bin86 package. Do I really need it to compile the kernel?

/Ulf

---

### Post by Juergen on 2005-02-16
It's in pool/main/l/linux86

In the package-comment it says:
> under Linux it's used only to create the 16-bit bootsector and setup binariesso it seems to be necessary

---

### Post by carpman on 2005-02-24
I would like to know where these files are?

need to custom build kernel so i can get to my date on iteraid drives.


Someone out there must know where we can get these files, be nice guys and help a Ubuntu newbie out :)

---

### Post by p!=f on 2005-02-24
How does your /etc/apt/sources.list file look like? Post it here like this:
```

# Local personal repo
deb file:/var/cache/apt-build/repository apt-build main

# Ubuntu Hoary
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted

deb http://archive.ubuntu.com/ubuntu/ hoary universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe multiverse

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted

# Englightenment DR17
deb http://soulmachine.net/debian unstable/
#deb-src http://soulmachine.net/debian unstable/

```

---

### Post by carpman on 2005-02-24
Thanks for reply, currently looking like this:

but have tried it with everyone uncommented


> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha i386 Binary-1 (20050217)]/ unstable main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
#deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
#deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse

---

### Post by p!=f on 2005-02-24
Wierd. I have almost same set up as you do.
```

[~] > wajig policy bin86 libncurses5-dev
bin86:
  Installed: (none)
  Candidate: 0.16.14-1.2ubuntu1
  Version Table:
     0.16.14-1.2ubuntu1 0
        500 http://archive.ubuntu.com hoary/main Packages
libncurses5-dev:
  Installed: 5.4-4
  Candidate: 5.4-4
  Version Table:
 *** 5.4-4 0
        500 http://archive.ubuntu.com hoary/main Packages
        100 /var/lib/dpkg/status

```
What you get by running
```

apt-cache policy bin86

```
Try to comment that first CDROM line and run apt-get update.

---

### Post by carpman on 2005-02-24
Hello, i get following errror when i run

apt-get update

> Fetched 1354kB in 8s (151kB/s)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz)  MD5Sum mismatch
Reading Package Lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead. 


apt-cache policy bin86

gives

> bin86:
  Installed: (none)
  Candidate: 0.16.14-1.2ubuntu1
  Version Table:
     0.16.14-1.2ubuntu1 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/main Packages
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by carpman on 2005-02-24
Hello, had a brain wave :)

tried your sources.list and hey it works no errors, not sure what happened there.

---

### Post by shadesfox on 2005-02-24
I really don't think you need bin86 to build Linux 2.6.  I think it is only used by Lilo.

---

### Post by p!=f on 2005-02-25
Try apt-get update to correct that error message. 
If it doesn't work, comment all lines in your sources.list, apt-get update, uncomment and apt-get update.

---

