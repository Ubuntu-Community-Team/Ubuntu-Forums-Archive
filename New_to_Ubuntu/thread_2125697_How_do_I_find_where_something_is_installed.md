---
title: "How do I find where something is installed"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by ktz84 on 2013-03-14
I've installed liboauth_dev from the apt-get and in the software centre I can see it is installed but how do I find where the install directory is?

I've tried search using the file manager and choosing computer and search and typing liboauth however nothing shoes. I've asked it show hidden files taht didn't help. I've tried

```
find / -type f -name liboauth*
```

And this results in this:

```
/var/lib/dpkg/info/liboauth0:amd64.md5sums
/var/lib/dpkg/info/liboauth0:amd64.shlibs
/var/lib/dpkg/info/liboauth0:amd64.symbols
/var/lib/dpkg/info/liboauth-dev.list
/var/lib/dpkg/info/liboauth0:amd64.postrm
/var/lib/dpkg/info/liboauth-dev.md5sums
/var/lib/dpkg/info/liboauth0:amd64.postinst
/var/lib/dpkg/info/liboauth0:amd64.list
/var/cache/apt/archives/liboauth-dev_0.9.7-0ubuntu1_amd64.deb
/usr/lib/signon/liboauth2plugin.so
/usr/lib/x86_64-linux-gnu/liboauth.a
/usr/lib/x86_64-linux-gnu/liboauth.so.0.8.4
/usr/lib/gthumb/extensions/liboauth.so
```

So none of that tells me anything.

So how on earth do you do a simple search?

Thanks

---

### Post by papibe on 2013-03-14
Hi ktz84.

To get the name of the actual package:
```
 $ apt-cache search liboauth
liboauth-php - PHP library implementing the OAuth secure authentication protocol
```
Once you got 'liboauth-php', you could check if it is installed by either this:
```
$ apt-cache policy liboauth-php
liboauth-php:
  **Installed: (none)**
  Candidate: 0~svn622-1
  Version table:
     0~svn622-1 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/universe Packages

```
(in my case it is not installed).

Or this:
```
$ dpkg -l  liboauth-php
No packages found matching liboauth-php.

```
Now to list all files contained on that package, you could use:
```
dpkg -L  liboauth-php
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by ktz84 on 2013-03-14
Thanks for that. I think by using the word installed I might have confused things a bit. What I'm actually trying to locate is where the actual installation is on the computer and not the software package. I need to link to the liboauth-dev that I've installed for a build that I'm doing.

---

### Post by ManamiVixen on 2013-03-14
Unlike Windows, Linux spreads the files of a installed program through out the system into specific folders. Most of the files from an install are found in /bin, /usr/bin, /usr/share, and /usr/lib, and /lib. That list up there where you did "

find / -type f -name liboauth*" was a good chunk of what was installed. Usually, they all work together intertwined to act as one program.

---

### Post by papibe on 2013-03-14
> **ktz84 said:**
> What I'm actually trying to locate is where the actual installation is on the computer and not the software package.

Try this:
```
dpkg -L liboauth-dev
```
Regards.

---

### Post by ktz84 on 2013-03-14
The output from:

```
dpkg -L liboauth-dev
```

is: 

```
/.
/usr
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/liboauth.a
/usr/lib/x86_64-linux-gnu/pkgconfig
/usr/lib/x86_64-linux-gnu/pkgconfig/oauth.pc
/usr/include
/usr/include/oauth.h
/usr/share
/usr/share/man
/usr/share/man/man3
/usr/share/man/man3/oauth.3.gz
/usr/share/doc
/usr/share/doc/liboauth-dev
/usr/share/doc/liboauth-dev/copyright
/usr/share/doc/liboauth-dev/examples
/usr/share/doc/liboauth-dev/examples/oauthexample.c.gz
/usr/share/doc/liboauth-dev/examples/oauthtest.c.gz
/usr/lib/x86_64-linux-gnu/liboauth.so
/usr/share/doc/liboauth-dev/changelog.Debian.gz
```

The build instructions are looking for an install directory and it then expects inlcude files and libs in subdirectories off that. I can specify each separately if they are spread over the place however I still dont' have a clue which directories I should be specifying.

---

### Post by steeldriver on 2013-03-14
What are you trying to build? usually it's only necessary to give explicit directories for build dependencies that are installed in 'nonstandard' locations (for example when you have multiple versions of a library, or a private version in your home dir) - anything installed via the regular package management system is usually found by default

---

