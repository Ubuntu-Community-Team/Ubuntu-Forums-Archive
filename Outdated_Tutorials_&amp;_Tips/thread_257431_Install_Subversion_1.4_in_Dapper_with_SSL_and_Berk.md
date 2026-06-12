---
title: "Install Subversion 1.4 in Dapper with SSL and Berkeley DB Support"
date: 2006-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by rapido on 2006-09-14
I am an avid user of subversion.  The new release of version 1.4 contains many great enhancements.  [http://subversion.tigris.org/svn_1.4_releasenotes.html]("http://subversion.tigris.org/svn_1.4_releasenotes.html")
Most notable to me were the HUGE working-copy performance gains.  I wanted to start using subversion 1.4 immediately.  Since Dapper ( and Edgy ) do not yet have subversion 1.4 available, I thought I would stitch together a quick guide for installation.

Thanks to trippyd for the tips on how to make this install trackable ( and uninstallable ) through synaptic, apt-get, and aptitude as a package.

If you are on an x86 box, and want to try a quick pre-compiled install follow the "Quick Install".  Otherwise skip to "Get the latest subversion tarballs" and follow each point to the end.  In may be worthwhile to read this entire document first to make the best choice.

Quick Install

```
$ sudo apt-get install openssl libssl-dev
$ sudo apt-get install libdb4.3 libdb4.3-dev db4.3-util libdb4.3++c2 libdb4.3++-dev
$ wget http://www.shiftingheat.com/packages/subversion/subversion_1.4.0-1_i386.deb
$ sudo dpkg -i subversion_1.4.0-1_i386.deb
```

Get the latest subversion tarballs.

```
$ wget http://subversion.tigris.org/downloads/subversion-1.4.0.tar.gz
$ wget http://subversion.tigris.org/downloads/subversion-deps-1.4.0.tar.gz
```

Unpack.

```
$ tar zxf subversion-1.4.0.tar.gz
$ tar zxf subversion-deps-1.4.0.tar.gz
```

Change dir into the newly created directory.

```
$ cd subversion-1.4.0
```

Install any required dependencies.  

If you don't have support for make or compilation, you will need to install those.

```
$ sudo apt-get install make gcc g++
```

We will be utilizing auto-apt and checkinstall to build and install as a .deb package.

```
sudo apt-get install checkinstall auto-apt
```

All of my repositories are accessed via https.  Thus I needed to install the openssl packages and throw an extra switch during configuration ( --with-ssl ).  This will not be required if you do not access remote repositories with ssl.  But, it also won't hurt to have this support.

```
$ sudo apt-get install openssl libssl-dev
```

If you are interested in more than just client support, and wish to be able to work with Berkeley DB locally, also add the following.  I'm truly a little unclear of which added library or the command line switch ( --with-berkeley-db=/usr ) ultimately added the support I needed.  But, the following combination should work. 

```
$ sudo apt-get install libdb4.3 libdb4.3-dev db4.3-util libdb4.3++c2 libdb4.3++-dev
```

Build and install

```
$ auto-apt run ./configure --with-ssl --with-berkeley-db=/usr
$ make
$ sudo checkinstall
```

One can always refer to INSTALL for any other configuration specifics.  By default, I will be installing in /usr/local.  I already have subversion 1.3 installed through Ubuntu.  My PATH gives preference to /usr/local.  My newly installed subversion 1.4 should take precedence over 1.3 ( and be independent I think ).  Once subversion 1.4 is available through Ubuntu, you should be able to simply deinstall this version.

---

### Post by trippyd on 2006-09-18
I would like to make an addition to this, as I like to be able to uninstall things.  Until an ubuntu package comes out with 1.4, compiling from source as described above is the only way to get the new features.  However, I do like to be able to uninstall things, and I would like to use the real ubuntu packages when they come, so here ya go:

You will need to add 2 additional packages, auto-apt (info: [https://help.ubuntu.com/community/AutoApt](https://help.ubuntu.com/community/AutoApt)) and checkinstall (info: [https://help.ubuntu.com/community/CheckInstall)](https://help.ubuntu.com/community/CheckInstall)).

First:
```
sudo aptitude install checkinstall auto-apt
```

then download the tarball, untar it and cd into the directory as described above.  Now comes the difference, instead of the "Build and Install" commands shown above do:

```
auto-apt run ./configure --with-ssl --with-berkeley-db=/usr
make
sudo checkinstall
```

Ok, here is what you just did.  Auto-apt will verify that you have all the packages necessary to build and install the tarball, it is not totally necessary if you KNOW you have the appropriate packages, but it is helpful nonetheless.  

Checkinstall is the really cool one.  It not only does the install, but it installs it as a .deb, meaning that it will show up in synaptic, apt-get, and aptitude as a package that you have installed, and can therefore be uninstalled cleanly.  As an added bonus, in the source directory where you built subversion, there will be a subversion_1.4.0-1_i386.deb file, which can be installed on other ubuntu systems.  Congratulations, you just created a custom .deb.

Good to read about checkinstall/custom debs:
[http://www.falkotimme.com/howtos/checkinstall/](http://www.falkotimme.com/howtos/checkinstall/)
[http://www.ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall](http://www.ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall)

---

### Post by sean on 2006-09-22
Won't you also need to rebuild some of Apache2?  Because if you want to use mod_dav_svn, you will need to rebuild it with the same libraries used in svn 1.4.  The library in question is libsvn_fs.

or am I wrong?


Sean

---

### Post by rapido on 2006-09-22
> **sean said:**
> Won't you also need to rebuild some of Apache2?  Because if you want to use mod_dav_svn, you will need to rebuild it with the same libraries used in svn 1.4.  The library in question is libsvn_fs.

or am I wrong?


Sean

I'm not sure that you will HAVE to rebuild Apache2.  Here is a snippet from the release notes on tigris.org.

> Older clients and servers interoperate transparently with 1.4 servers and clients. Of course, some of the new 1.4 features may not be available unless both client and server are the latest version. There is no need to dump and reload your repositories; Subversion 1.4 can read repositories created by earlier versions. To upgrade an existing installation, just install the newest libraries and binaries on top of the older ones.

Subversion 1.4 maintains API/ABI compatibility with earlier releases, by only adding new functions. A program written to the 1.0, 1.1, 1.2 or 1.3 API can both compile and run using 1.4 libraries. However, a program written for 1.4 cannot necessarily compile or run against older libraries.

I would simply try it.  I'm guessing that out of the box with this install, Apache2 will not see the new library ( which is in /usr/local/lib ).  This library was built with the Apache Portable Runtime as packaged by tigris.org.  That would need to be made available to Apache2 to gain Subversion 1.4 benefit.  

If all else fails you may WANT to rebuild, to upgrade all related components to 1.4.  In which case, follow the longer version of the install guide, first reading the INSTALL file looking for anything Apache related.     There is an entire section devoted in the INSTALL file related to Apache.

---

### Post by loqu on 2006-10-14
Thanks a lot for the howto.  Though, apparently, if someone just wants to use the client side of subversion, one only needs these lines:

```
$ wget http://www.shiftingheat.com/packages/subversion/subversion_1.4.0-1_i386.deb
$ sudo dpkg -i subversion_1.4.0-1_i386.deb
```

Thanks to shiftingheat.com for the package hosting, and thank you all for making my life so much easier, even if it was too late.

:KS 

Cheers

---

### Post by StormWatcher on 2006-10-15
Being a complete newbie to Linux, I foudn this helpful, minus one major detail.  I just installed a Ubuntu server, with only command line.  When I did the ```
sudo aptitude install checkinstall auto-apt
``` command and received an error that it could not be found.  With a little research I found that I had to uncomment some stuff in my source.list that allowed me to search Universal repositories (or whatever they are called).  Once I did this and ran an update, everything worked fine.

---

### Post by bmeike on 2006-11-07
FWIW, this didn't work for me, on Edgy.  I got a ton of error messages, during the checkinstall, informing me that .h files in apr/include/apr-0/ were missing.  It seems they should have been copied from the package, but were not.

Fortunately, the shiftingheat.com .deb got me a working client...

bmeike

---

### Post by smurfBean on 2006-11-13
OK so I've tried this on a plain install of 6.10 (Edgy) but with no joy.

Can anyone help?

I can install subversion 1.4.2 if I follow all of the commands and use 'make install' instead of using 'sudo checkinstall' (creating a deb file) and then using 'sudo dpkg -i' on the deb file.

If I try and use the 'sudo checkinstall' command that seems to work ok...and a deb file is created, however if I try and install from the deb file it doesn't work. I get the following error message:

'(Reading database ... 93140 files and directories currently installed.)
Unpacking subversion (from subversion_1.4.2-1_i386.deb) ... 
dpkg: error processing subversion_1.4.2-1_i386.deb (--install):
 trying to overwrite '/usr/bin/ld', which is also in package binutils
dpkg-deb:subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 subversion_1.4.2-1_i386.deb'

I don't know why it's trying to overwrite /usr/bin/ld'

Can anyone help with this?  I'd like to be able to create an installable package for subversion 1.4.2 and be able to manage my install/uninstall with the packagemanger.

Thanks in advance for any help.

---

### Post by ndrake on 2006-11-14
> **bmeike said:**
> FWIW, this didn't work for me, on Edgy.  I got a ton of error messages, during the checkinstall, informing me that .h files in apr/include/apr-0/ were missing.  It seems they should have been copied from the package, but were not.

Fortunately, the shiftingheat.com .deb got me a working client...

bmeike

I also get errors when it tries to copy the apr stuff when doing the sudo checkinstall.  I'm using Edgy too.  Here are the actual messages:

```
mkdir /usr/local/apr/include/apr-0
cp -p /home/ndrake/src/subversion-1.4.2/apr/include/*.h /usr/local/apr/include/apr-0;
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_allocator.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_allocator.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_atomic.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_atomic.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_compat.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_compat.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_dso.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_dso.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_env.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_env.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_errno.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_errno.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_file_info.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_file_info.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_file_io.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_file_io.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_fnmatch.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_fnmatch.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_general.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_general.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_getopt.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_getopt.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_global_mutex.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_global_mutex.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_hash.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_hash.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_inherit.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_inherit.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_lib.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_lib.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_mmap.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_mmap.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_network_io.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_network_io.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_poll.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_poll.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_pools.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_pools.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_portable.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_portable.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_proc_mutex.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_proc_mutex.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_ring.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_ring.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_shm.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_shm.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_signal.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_signal.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_strings.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_strings.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_support.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_support.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_tables.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_tables.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_thread_cond.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_thread_cond.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_thread_mutex.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_thread_mutex.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_thread_proc.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_thread_proc.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_thread_rwlock.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_thread_rwlock.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_time.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_time.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_user.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_user.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_version.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_version.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_want.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_want.h': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/ndrake/src/subversion-1.4.2/apr'
make: *** [external-install] Error 1

****  Installation failed. Aborting package creation.

```

I should also note that I'm attempting this with Subversion 1.4.2.

EDIT: One other thing.  If I do ```
sudo make install
``` inside of the apr subdirectory, the mkdir and cp commands work fine.

---

### Post by crouton on 2006-11-14
Just as an aside, the FSFS system is much better than the Berkely DB.  Unless they've done an about-face since 1.2, there are a lot of reasons to stick with FSFS.

---

### Post by gadgetgirl on 2006-12-13
> **crouton said:**
> Just as an aside, the FSFS system is much better than the Berkely DB.  Unless they've done an about-face since 1.2, there are a lot of reasons to stick with FSFS.

They did actually do an about-face in 1.4 with regard to BDB.

> A common problem with previous versions of Subversion is that crashed server processes could leave BerkeleyDB-based repositories in an unusable "wedged" state, requiring administrators to manually intervene and bring back online. (Note: this is not due to bugs in BerkeleyDB, but due to the unorthodox way in which Subversion uses it!)

Subversion 1.4 can now be compiled against BerkeleyDB 4.4, which has a new "auto-recovery" feature. If a Subversion server process crashes and leaves the repository in an inconsistent state, the next process which attempts to access the repository will notice the problem, grab exclusive control of the repository, and automatically recover it. In theory (and in our testing), this new feature makes BerkeleyDB-based repositories just as wedge-proof as FSFS repositories.

---

### Post by desheikh on 2007-01-01
for edgy try installing the packages at this location

[http://higepon.blogspot.com/2006/12/install-subversion-142-to-ubuntu-edgy.html](http://higepon.blogspot.com/2006/12/install-subversion-142-to-ubuntu-edgy.html)

---

### Post by crisisfrog on 2007-01-18
Or...

[http://packages.debian.org/testing/devel/subversion](http://packages.debian.org/testing/devel/subversion)

Edited...

Nevermind, that does not seem to work as well. Plus, it's a test release.

---

### Post by fluxin on 2007-03-01
Look here 
[http://tux.oclug.on.ca/pipermail/oclug/2004-May/038916.html](http://tux.oclug.on.ca/pipermail/oclug/2004-May/038916.html)

> **ndrake said:**
> I also get errors when it tries to copy the apr stuff when doing the sudo checkinstall.  I'm using Edgy too.  Here are the actual messages:

```
mkdir /usr/local/apr/include/apr-0
cp -p /home/ndrake/src/subversion-1.4.2/apr/include/*.h /usr/local/apr/include/apr-0;
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_allocator.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_allocator.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_atomic.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_atomic.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_compat.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_compat.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_dso.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_dso.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_env.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_env.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_errno.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_errno.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_file_info.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_file_info.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_file_io.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_file_io.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_fnmatch.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_fnmatch.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_general.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_general.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_getopt.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_getopt.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_global_mutex.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_global_mutex.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_hash.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_hash.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_inherit.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_inherit.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_lib.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_lib.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_mmap.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_mmap.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_network_io.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_network_io.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_poll.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_poll.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_pools.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_pools.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_portable.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_portable.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_proc_mutex.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_proc_mutex.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_ring.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_ring.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_shm.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_shm.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_signal.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_signal.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_strings.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_strings.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_support.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_support.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_tables.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_tables.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_thread_cond.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_thread_cond.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_thread_mutex.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_thread_mutex.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_thread_proc.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_thread_proc.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_thread_rwlock.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_thread_rwlock.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_time.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_time.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_user.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_user.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_version.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_version.h': No such file or directory
cp: setting permissions for `/usr/local/apr/include/apr-0/apr_want.h': No such file or directory
cp: preserving ACL for `/usr/local/apr/include/apr-0/apr_want.h': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/ndrake/src/subversion-1.4.2/apr'
make: *** [external-install] Error 1

****  Installation failed. Aborting package creation.

```

I should also note that I'm attempting this with Subversion 1.4.2.

EDIT: One other thing.  If I do ```
sudo make install
``` inside of the apr subdirectory, the mkdir and cp commands work fine.

---

### Post by deez0n on 2007-03-12
> **rapido said:**
> I'm not sure that you will HAVE to rebuild Apache2.  Here is a snippet from the release notes on tigris.org.



I would simply try it.  I'm guessing that out of the box with this install, Apache2 will not see the new library ( which is in /usr/local/lib ).  This library was built with the Apache Portable Runtime as packaged by tigris.org.  That would need to be made available to Apache2 to gain Subversion 1.4 benefit.  

If all else fails you may WANT to rebuild, to upgrade all related components to 1.4.  In which case, follow the longer version of the install guide, first reading the INSTALL file looking for anything Apache related.     There is an entire section devoted in the INSTALL file related to Apache.

You don't have to rebuild apache2, but you will want to install apache2-threaded-dev and run the auto-apt configure line with --with-apxs2=/usr/lib/apxs2, --enable-dav, and --enable-so

```

sudo apt-get install apache2-threaded-dev
sudo auto-apt run ./configure --with-ssl --enable-dav --enable-so  --with-berkeley-db=/usr --with-apxs2=/usr/bin/apxs2

```

I ran into some conflicts installing the subversion deb file, so I used 
```

sudo dpkg -i --force-all subversion_1.4.2-1_i386.deb 

```

also the new subversion install will add 
the following lines to your /etc/apache2/httpd.conf
```

LoadModule dav_svn_module /usr/lib/apache2/modules/mod_dav_svn.so
LoadModule authz_svn_module /usr/lib/apache2/modules/mod_authz_svn.so

```

If you installed libapache2-svn before, then these lines are redundant.
You will receive a couple of  "module XYZ_mod is already loaded" warnings when you stop and start apache. They also appear in /etc/apache2/mods-enabled/dav_svn.load.  It is safe to remove the entries in httpd.conf.

---

### Post by crouton on 2007-03-12
> **gadgetgirl said:**
> They did actually do an about-face in 1.4 with regard to BDB.

From my reading of [http://svnbook.red-bean.com/nightly/en/svn-book.html#svn.reposadmin.basics.backends](http://svnbook.red-bean.com/nightly/en/svn-book.html#svn.reposadmin.basics.backends) it seems that not much has changed.

> The only real argument against FSFS is its relative immaturity compared to Berkeley DB. Unlike Berkeley DB, which has years of history, its own dedicated development team and, now, Oracle's mighty name attached to it, [32]  FSFS is a much newer bit of engineering. Prior to Subversion 1.4, it was still shaking out some pretty serious data integrity bugs which, while only triggered in very rare cases, nonetheless did occur. That said, FSFS has quickly become the back-end of choice for some of the largest public and private Subversion repositories, and promises a lower barrier to entry for Subversion across the board.

I think it is a great idea that there are two choices for back-end storage, but my personal leaning is towards FSFS.  Cross-platform portability and cross-operating system portability are very, very nice.

---

