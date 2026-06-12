---
title: "Ubuntu am64 udisks compilation"
date: 2011-09-28
forum: Packaging and Compiling Programs
---

### Post by christophevr on 2011-09-28
Compiling ubuntu's udisks.
Hello, It's now since a while (as from ubuntu 10.10) That We can not execute script files or (linux)binaries from usb Vfat stick.

Reading all stuff on that at the end 50 % is now happy that it is not possible and the other 50 % not happy a lot are really pissed. As in many cases it's really important to be able to start binary and script files. from a vfat formatted usb stick. Wht vfat ?? just simple cause it needs to be used on Windows,Mac and Linux.

All work arounds ok with fstab and so can work but are really not handy. And for a lot off users understandable.

So I'm in the case that I really need vfat to be executable on an usb stick.
(and I do not mean windows exe files but Linux script or binaries)
And it al needs with strictly basic ubuntu. So yes I stay using udisks and ... Actually the udisks-deamon.

So for that I was forced !!! To recompile my own udisks-deamon corrected to mount script and binaries executable again.

Now there is a problem whit that:

What I did was downloading the latest udisks_1.0.2.orig.tar.gz , udisks_1.0.2-4ubuntu2.debian.tar.gz and udisks_1.0.2-4ubuntu2.dsc into /usr/local/src (My user login is the owner of src in local)
From (standaard non root or sudo command)
~$ dpkg-source -x udisks_1.0.2-4ubuntu2.dsc
Then I had the udisks-1.0.2 map with the ubuntu patches applied.

There I first modified

into device.c the two lines Nr 5879 and 5880 from:

```

static const char *vfat_defaults[] = { "uid=", "gid=", "shortname=mixed", "dmask=0077", "utf8=1", "showexec", NULL };
static const char *vfat_allow[] = { "flush", "utf8=", "shortname=", "umask=", "dmask=", "fmask=", "codepage=", "iocharset=", "usefree", "showexec", NULL };

```

To:

```

static const char *vfat_defaults[] = { "uid=", "gid=", "shortname=mixed", "dmask=0077", "utf8=1", "showexec", "exec", NULL };
static const char *vfat_allow[] = { "flush", "utf8=", "shortname=", "umask=", "dmask=", "fmask=", "codepage=", "iocharset=", "usefree", "showexec", "exec", NULL };

```

Then I used as normal user (non root nor sudo)
/usr/local/src/udisks-1.0.2$ ./configure

it did configure nice after I added all the needed dev files

/usr/local/src/udisks-1.0.2$ make

It did compile nicely.

Then I just copied udisks-deamon from my compiled version to replace that in /usr/lib (as root user now )

I restarted pc . And yes it does mount the usb vfat with exec option.

But if I now unmount (from nautilus as normal user) de usb stick, It does NOT erase the moint point anymore into /media/ map.

Wich by removing and reinserting the stick does leave an endless numbers of moint points with label from usb stick and --- and so on behind.

When I use the original deamon it does erase.

How do I compile the udisks so that it as well removes the created mount point into /media ?

---

### Post by christophevr on 2011-10-02
Finally I found the problem. I forgot to insert the correct paths for ubuntu. configure does not determine them automatically like I thaught.

For ubuntu natty :

the lib, bin, sbin, include and libexec dir are in /usr they are:
/usr/lib
/usr/bin
The libexec dir:
/usr/lib
The datadir :
/usr/share
The docdir:
/usr/share/doc
The mandir:
/usr/share/man
The sysconfdir :
/etc
The localstatedir:
/var
The slashlibdir:
/lib
The slashsbindir:
/sbin
The includedir:
/usr/include

With --prefix=/usr , The /lib /bin /sbin  slashlibdir slashsbindir 
are already ok to the right path.

the /etc /var /include /man /doc /datadir needs to be set as well.

Now when I :

unpack the ubuntu source as regular user with:

dpkg-source -x udisks_1.0.2-4ubuntu2.dsc

goto udisks-1.0.2/src path and patch device.c line 5879 and 5880 from

```

static const char *vfat_defaults[] = { "uid=", "gid=", "shortname=mixed", "dmask=0077", "utf8=1", "showexec", "NULL };
static const char *vfat_allow[] = { "flush", "utf8=", "shortname=", "umask=", "dmask=", "fmask=", "codepage=", "iocharset=", "usefree", "showexec", NULL };

```

In :

```

static const char *vfat_defaults[] = { "uid=", "gid=", "shortname=mixed", "dmask=0077", "utf8=1", "exec", "NULL };
static const char *vfat_allow[] = { "flush", "utf8=", "shortname=", "umask=", "dmask=", "fmask=", "codepage=", "iocharset=", "usefree", "exec", NULL };

```
 
Then from path (as regular user)

udisks-1.0.2 $ ./configure --prefix=/usr --libexecdir=/usr/lib --sysconfdir=/etc --localstatedir=/var --docdir=/usr/share/doc --datadir=/usr/share --mandir=/usr/share/man --includedir=/usr/include

Followed by make

Then just copy as root the udisks-deamon to /usr/lib/udisks/

Do not forget to first backup your original udisks-deamon.

Now the vfat usb devices are again mounted with exec option. as well for 
exe files are script or linux binaries. Off course also all other text files.

;)

---

