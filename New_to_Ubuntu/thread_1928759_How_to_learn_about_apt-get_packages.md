---
title: "How to learn about apt-get packages"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by rockaday on 2012-02-20
Hello,

How can I find out about apt-get packages without installing them?  I looked at man apt-get and didn't figure this out.  For example:

```

~$ pms
The program 'pms' is currently not installed.  You can install it by typing:
sudo apt-get install pms

```

I'm not sure I want pms.  How can I find out more about it?

Background:
I run windows 7 x64 and have Ubuntu 11.10 x64 dual boot.  I am trying to gradually transition from Windows to Ubuntu as my primary operating system, and am learning more about how to use Ubuntu so I can do that.

Thanks for your help,

Rockaday

---

### Post by haqking on 2012-02-20
> **rockaday said:**
> Hello,

How can I find out about apt-get packages without installing them?  I looked at man apt-get and didn't figure this out.  For example:

```

~$ pms
The program 'pms' is currently not installed.  You can install it by typing:
sudo apt-get install pms

```

I'm not sure I want pms.  How can I find out more about it?

Background:
I run windows 7 x64 and have Ubuntu 11.10 x64 dual boot.  I am trying to gradually transition from Windows to Ubuntu as my primary operating system, and am learning more about how to use Ubuntu so I can do that.

Thanks for your help,

Rockaday

nobody wants PMS ;-)

anyways there are no apt-get packages per se

apt or aptitude and get means go off and get this package 

A package is a package, if you want to know what it is then look it up online.

There are thousands of packages for various things, whether you want them or not is upto you based on what you are looking for.

you can search for packages here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

but not every package in existence is there as packages are not just maintained in the repos.

peace

---

### Post by oldos2er on 2012-02-20
```
apt-cache show pms
``` will give you the package info.

---

### Post by haqking on 2012-02-20
> **oldos2er said:**
> ```
apt-cache show pms
``` will give you the package info.

ahh yeah good point, i guess that is a better answer than mine ;-)

peace

---

### Post by rockaday on 2012-02-20
Great, thanks to both of you.  apt-cache show gave me what I was looking for, and it's nice to know where I can browse packages online too.

```
~$ apt-cache show pms
Package: pms
Priority: extra
Section: universe/sound
Installed-Size: 392
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Alejandro Garrido Mota <garridomota@gmail.com>
Architecture: amd64
Version: 0.41-1
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.12.0), libncurses5 (>= 5.6+20071006-3), libstdc++6 (>= 4.2.1)
Recommends: mpd
Filename: pool/universe/p/pms/pms_0.41-1_amd64.deb
Size: 145686
MD5sum: 84d0f1fcad702ab211bbff5284630b9d
SHA1: 46d1dc6a37a7eb2b9e9329ac907040fc8dfdfade
SHA256: dc04273e1aa23aadb6b819ec3b59f45de8836a9c6f0791a4dacaa85230084f9c
Description-en: Practical Music Search, an MPD client
 PMS is an ncurses based client for Music Player Daemon. It aims
 to be accessible and highly configurable, with a light but
 powerful interface much like Vim, and supports custom colors,
 layouts, and key bindings
Homepage: http://pms.sourceforge.net
Description-md5: 6f7891bf02ac2b00c338d9d1c2ae04f9
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```

Thanks again,

Rockaday

---

### Post by kaldor on 2012-02-20
There's also *dpkg -s packagename*.

---

### Post by snowpine on 2012-02-20
There is also Ubuntu Software Center, which shows you the same info in an easy-to-read graphical format. :)

---

### Post by rockaday on 2012-02-20
> **kaldor said:**
> There's also *dpkg -s packagename*.

Thanks, easy to remember.  But why didn't it work for me?

```
~$ dpkg -s pms
Package `pms' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
~$ dpkg --info pms
dpkg-deb: error: failed to read archive `pms': No such file or directory

```

Thanks,

Rockaday

---

### Post by rockaday on 2012-02-20
> **snowpine said:**
> There is also Ubuntu Software Center, which shows you the same info in an easy-to-read graphical format. :)

A good point, a search of the package name in Ubuntu Software Center gave me the same information, but with formatting.

Thanks,

Rockaday

---

### Post by Lisiano on 2012-02-20
There is also Synaptic which I still consider better that Ubuntu Software Center and dpkg will only work with packages already installed so in CLI, only apt-cache will work if you know the name.
There is also apropos if you know a function the package does, though apt-cache also does it if you do search instead of show.

---

### Post by dFlyer on 2012-02-20
form a terminal enter:

man apt-get

---

### Post by cortman on 2012-02-20
> **rockaday said:**
> Thanks, easy to remember.  But why didn't it work for me?

```
~$ dpkg -s pms
Package `pms' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
~$ dpkg --info pms
dpkg-deb: error: failed to read archive `pms': No such file or directory

```

Thanks,

Rockaday

That's because dpkg -s only gives info about installed packages. Apt-cache is more useful.
Also if you want to search for a particular package or program, you can use

```
apt-cache search package_name
```

or if you just want names of packages, 

```
apt-cache search --names-only package_name 
```

If you want a GUI to do this, I'd recommend Synaptic over the USC, as it's far more stable and powerful.

---

### Post by rockaday on 2012-02-20
> **Lisiano said:**
> There is also Synaptic which I still consider better that Ubuntu Software Center and dpkg will only work with packages already installed so in CLI, only apt-cache will work if you know the name.
There is also apropos if you know a function the package does, though apt-cache also does it if you do search instead of show.

Nice.  I'm installing Synaptic right now so I can give it a try.

Thanks all!

Rockaday

---

### Post by wildmanne39 on 2012-02-20
Hi, I use synaptic to look up what packages do if I do not know but I install most thing from the command line.

---

