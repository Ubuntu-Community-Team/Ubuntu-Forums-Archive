---
title: "Sharing folders with a Windows network"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Derek5272 on 2008-11-09
Hi all,

Just installed Ubuntu onto an old computer, and I'm trying to share folders with the other Windows machines on the network - Without any configuration, I can already see other computers. If I simply try to right click on a folder, enter the sharing options, and check 'Share this folder' it gives me an error message:

Sharing service is not installed
You need to install the Windows network sharing service in order to share your folders.

So, I click the button that says 'Install service' and enter my password. It then asks me to restart my session in order to enable sharing. I do so, go the folder I want to share, click the box to enable sharing, and it once again tells me that I need to install the service in order to share folders. So, I turned to Google, and everything I find talks about using Samba to share folders. Great - I just don't have Samba.

So, I go download Samba 3.2.4, and the How-To documentation tells me that, in order to install Samba, I need autoconf. Ok. I download autoconf 2.6.3, and its install documentation tells me to navigate to the folder with the source files, and use the commands:

```
./configure
make
make install
```

I do so, and for my lemming efforts am rewarded with the following:

```
derek@Derek-Ubuntu:~/autoconf-2.63$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether /bin/sh -n is known to work... no
checking for expr... /usr/bin/expr
checking for GNU M4 that supports accurate traces... configure: error: no acceptable m4 could be found in $PATH.
GNU M4 1.4.5 or later is required; 1.4.11 is recommended
derek@Derek-Ubuntu:~/autoconf-2.63$ 
```

Now, I'll admit that I'm a complete newb with this stuff, but looking at that I was pretty sure that those "no" entries meant it didn't work. However, I decided to try the 'make' command just in case:

```
derek@Derek-Ubuntu:~/autoconf-2.63$ make
There seems to be no Makefile in this directory.
You must run ./configure before running `make'.
make: *** [abort-due-to-no-makefile] Error 1
derek@Derek-Ubuntu:~/autoconf-2.63$ 
```

So that, apparently, is not working either. If anybody can shed some light on either the problem with directly sharing the folders, or installing samba/autoconf, you would have my eternal and undying gratitude. Thanks in advance for any and all help.

---

### Post by MrWES on 2008-11-09
Samba is in the repos; install it from there. No need to download it and compile it.

Bill

---

### Post by Derek5272 on 2008-11-09
Sorry, how do I install from repos? I've tried using 'apt-get install' which I have assumed is the command for installing things included with the distro, and:

```
derek@Derek-Ubuntu:~$ sudo apt-get install samba
[sudo] password for derek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  smbclient samba-common
E: Package samba has no installation candidate
derek@Derek-Ubuntu:~$ 

```

---

### Post by Derek5272 on 2008-11-09
Ok, the above can be ignored, I've found the samba stuff and have been trying to configure it. When I use testparm, I get 2 error lines:

```
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
```

What am I supposed to do that will create that directory?

---

### Post by ferdostar on 2008-11-09
Check there System->Administration->Synaptic ;)

---

