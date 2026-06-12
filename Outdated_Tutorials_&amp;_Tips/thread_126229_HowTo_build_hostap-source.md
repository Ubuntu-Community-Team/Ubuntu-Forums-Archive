---
title: "HowTo: build hostap-source"
date: 2006-02-06
forum: Outdated Tutorials &amp; Tips
---

### Post by zencoder on 2006-02-06
This is a short and sweet HowTo.  I'm not going to go into every single detail, but I will mention all points.

I use an SMC2532W-B for work, where I occasionally perform a Technical Security Analysis of a location, including wifi signal detection.  This card is ideal for .11b/g, and hostap is one of the better drivers for monitor mode.  I do *not* use this card/drive for wifi network connectivity, so if you do *YMMV*.

First off, I have Breezy 5.10 installed, with all repositories enabled (that is, I did not have to download any .tgz files or compile anything from a source besides the Ubuntu repositories.)
```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

You will need the following:[LIST]
[*]*linux-headers* package for your kernel
[*]*build-essential* package
[*]*gcc-3.4* package (build kept failing on this command, 5.10 showed gcc-3.3 was installed. This fixed it.)
[*]*hostap-source* package
[*]*fakeroot* package
[/LIST]
get them with your package manager of choice (Synaptic, apt-get install, etc.)

Change to superuser account, go to the source directory, and unpack the hostap-source.tar.bz2 file.
```

$ sudo su -
# cd /usr/src
# bunzip2 ./hostap-source.tar.bz2
# tar xvf ./hostap-source.tar
```

Change directory to the sources root and compile the module.
```

# cd modules/hostap-source
# fakeroot debian/rules binary-modules \
         KSRC=/usr/src/linux-headers-$VERSION KVERS=$VERSION

[I]**$VERSION** must be replaced by the
**exact version string** of the kernel you
want to build the module for (e.g. 2.6.12-10-686).[/i]
```

Install your newly compiled module.
```

# dpkg -i /usr/src/hostap-modules-blah-blah-blah.deb

```

Thats it!  You should now have an installed working module.


---
If you are using the WIFI hi-power card I mentioned above (SMC2532W-B) you'll need to do one more thing...modify a single file for device recognition.  As the superuser, open your favorite editor and go to the file **/etc/pcmcia/hostap_cs.conf**.  Add the following line, and save the file.
```

card "SMC2532W-B EliteConnect Wireless Adapter"
  manfid 0xd601, 0x0010
  bind "hostap_cs"

```

I've written this HOWTO late at night and mostly from memory.  If you have difficulty, please reply to the thread and I'll try to help as I can.

---

