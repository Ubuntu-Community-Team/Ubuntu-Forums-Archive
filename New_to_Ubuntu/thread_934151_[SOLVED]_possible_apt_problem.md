---
title: "[SOLVED] possible apt problem"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by r3bol on 2008-09-30
Hey, I've just updated to the latest Ubuntu 8.04 and I'm trying to install Scratchbox from a script and get the following error...

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Running apt-get update failed.
E: Please correct the problem with apt and try again.
E: Or try an alternative installation method.

Before the error this is what I had...

This script will install Scratchbox 1.0.8 'apophis' release to your computer.

Install options
---------------

Install from packages=apt
Scratchbox install path=/scratchbox
Scratchbox group=sbox
armel compiler=cs2005q3.2-glibc2.5-arm
i386 compiler=cs2005q3.2-glibc2.5-i386
armel devkits=perl:debian-etch:maemo3-tools:cputransp
i386 devkits=perl:debian-etch:maemo3-tools
armel CPU transparency=qemu-arm-0.8.2-sb2

Checking for prerequisites
--------------------------

Running as user root... yes
Not running as user root inside fakeroot... yes
Running outside of scratchbox... yes
Running on Linux kernel... yes
Running on i386 architecture... yes
Host kernel binfmt_misc support... yes
Host kernel VDSO support... yes
No host kernel SELinux extensions... yes
Host kernel local IPv4 port range... yes
Scratchbox installation not existing... yes
No conflicting binfmt_misc interpreter... yes
Scratchbox user names... yes

Everything seems to be ok.
Hit [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy Release.gpg
Ign [http://mirrors.nic.funet.fi](http://mirrors.nic.funet.fi) hardy/main Translation-en_US
Then it continues to list all the content addresses. 

Could this be a possible APT problem. Is there anything I could run to check it. 

Thanks.

---

### Post by r3bol on 2008-09-30
Sorry, I just realised - I had Synaptic open. It looks like that was stopping it.

---

