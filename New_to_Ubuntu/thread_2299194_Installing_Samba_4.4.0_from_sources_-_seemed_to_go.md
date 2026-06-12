---
title: "Installing Samba 4.4.0 from sources - seemed to go okay but smbd not running?"
date: 2015-10-16
forum: New to Ubuntu
---

### Post by michael325 on 2015-10-16
So I'm fairly new to this, and this is only the second time I've installed something direct from compiling the sources myself.

I'm on Ubuntu 14.04 LTS and I wanted the latest and greatest version of Samba instead of the old one that aptitude gives you, so I cloned the Git repo and got Samba 4.4.0pre1

So I followed lots of old and outdated instructions on how to install Samba (really the documentation on installing Samba 4 is shocking) and managed to coble together a list of things to do from multiple sources.

I downloaded the sources into /usr/local/src/samba and ran ./configure, then make, then make install. And this all worked fine after apt-getting a few missing packages.

Now what?

- The Daemons are not running that I can see when I search for them within htop.
- I managed to find that the executables have been installed to /usr/local/samba/sbin/smbd and /usr/local/samba/sbin/nmbd
- But when I run them, as outlined [here]("https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/compiling.html#id2688579"), The command line returns nothing, I cant see them running in the process list and I cant see any network shares come up on my windows box.

Does anyone know where to go from here?

```

root@brave-server:/usr/local/samba/sbin# ll
total 1968
drwxr-xr-x  2 root root    4096 Oct 16 13:37 ./
drwxr-xr-x 10 root root    4096 Oct 16 13:20 ../
-rwxr-xr-x  1 root root  332377 Oct 16 13:20 nmbd*
-rwxr-xr-x  1 root root  100933 Oct 16 13:21 samba*
-rwxr-xr-x  1 root root   21227 Oct 16 13:12 samba_dnsupdate*
-rwxr-xr-x  1 root root   11045 Oct 16 13:12 samba_kcc*
-rwxr-xr-x  1 root root    8069 Oct 16 13:12 samba_spnupdate*
-rwxr-xr-x  1 root root   19614 Oct 16 13:12 samba_upgradedns*
-rwxr-xr-x  1 root root  103377 Oct 16 13:22 smbd*
-rwxr-xr-x  1 root root     104 Oct 16 13:37 startsmb*
-rwxr-xr-x  1 root root 1391206 Oct 16 13:21 winbindd*
root@brave-server:/usr/local/samba/sbin# ./smbd -D
root@brave-server:/usr/local/samba/sbin# ./smbd -V
Version 4.4.0pre1-GIT-5aab31a
root@brave-server:/usr/local/samba/sbin#

```

---

### Post by bab1 on 2015-10-16
> **michael325 said:**
> So I'm fairly new to this, and this is only the second time I've installed something direct from compiling the sources myself.

I'm on Ubuntu 14.04 LTS and I wanted the latest and greatest version of Samba instead of the old one that aptitude gives you, so I cloned the Git repo and got Samba 4.4.0pre1

So I followed lots of old and outdated instructions on how to install Samba (really the documentation on installing Samba 4 is shocking) and managed to coble together a list of things to do from multiple sources.

I downloaded the sources into /usr/local/src/samba and ran ./configure, then make, then make install. And this all worked fine after apt-getting a few missing packages.

Now what?

- The Daemons are not running that I can see when I search for them within htop.
- I managed to find that the executables have been installed to /usr/local/samba/sbin/smbd and /usr/local/samba/sbin/nmbd
- But when I run them, as outlined [here]("https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/compiling.html#id2688579"), The command line returns nothing, I cant see them running in the process list and I cant see any network shares come up on my windows box.

Does anyone know where to go from here?

```

root@brave-server:/usr/local/samba/sbin# ll
total 1968
drwxr-xr-x  2 root root    4096 Oct 16 13:37 ./
drwxr-xr-x 10 root root    4096 Oct 16 13:20 ../
-rwxr-xr-x  1 root root  332377 Oct 16 13:20 nmbd*
-rwxr-xr-x  1 root root  100933 Oct 16 13:21 samba*
-rwxr-xr-x  1 root root   21227 Oct 16 13:12 samba_dnsupdate*
-rwxr-xr-x  1 root root   11045 Oct 16 13:12 samba_kcc*
-rwxr-xr-x  1 root root    8069 Oct 16 13:12 samba_spnupdate*
-rwxr-xr-x  1 root root   19614 Oct 16 13:12 samba_upgradedns*
-rwxr-xr-x  1 root root  103377 Oct 16 13:22 smbd*
-rwxr-xr-x  1 root root     104 Oct 16 13:37 startsmb*
-rwxr-xr-x  1 root root 1391206 Oct 16 13:21 winbindd*
root@brave-server:/usr/local/samba/sbin# ./smbd -D
root@brave-server:/usr/local/samba/sbin# ./smbd -V
Version 4.4.0pre1-GIT-5aab31a
root@brave-server:/usr/local/samba/sbin#

```
Installing Samba v4 this way does not get you a later version of *smbd* or *nmbd*.  These two daemons are adapted from Samba 3.5 and will be eliminated in the future sometime.  The Ubuntu Samba package has the same daemons and includes all the start up scripts for the version of Ubuntu that you are using.  The Ubuntu init system is changing from *upstart* to *systemd* so the start up scripts are changing also.

My advice is to remove Samba and all the dependency packages that you installed.  Then install Samba using the apt-get packages.  This will get you the same file sharing daemons plus all of the correct dependencies and the init scripts that work for the version of Ubuntu you are currently using.

Concerns, questions or comments?

---

### Post by michael325 on 2015-10-19
Thanks Bab1, 

I'll try using checkinstall to remove the whole mess now.

---

