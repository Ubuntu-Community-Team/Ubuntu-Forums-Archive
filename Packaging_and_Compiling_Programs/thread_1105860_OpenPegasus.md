---
title: "OpenPegasus"
date: 2009-03-25
forum: Packaging and Compiling Programs
---

### Post by CHaoSlayeR on 2009-03-25
Hi there,

I was wondering if anyone has had any success to compile OpenPegasus on either Debian 4.0+ or Ubuntu 8.10 recently.

If I download the release 2.8.1 branch from CVS and try to compile I get the following errors:

```

chaoslayer@lilith:~/Downloads/OpenPegasus/pegasus$ make world
make --directory=/home/chaoslayer/Downloads/OpenPegasus/pegasus/src/utils/mu -f Makefile
make[1]: Entering directory `/home/chaoslayer/Downloads/OpenPegasus/pegasus/src/utils/mu'
g++ -c -o DependCmd.o -W -Wall -Wno-unused  -D_GNU_SOURCE -DTHREAD_SAFE -D_REENTRANT -s -O2 -m32 -fvisibility=hidden    -DPEGASUS_PLATFORM_LINUX_GENERIC_GNU -DPEGASUS_PLATFORM_LINUX_IX86_GNU -DPEGASUS_USE_SYSLOGS -DPEGASUS_ARCH_LIB=\"lib\" -DNDEBUG -DPEGASUS_ENABLE_USERGROUP_AUTHORIZATION -DPEGASUS_DEFAULT_ENABLE_OOP -DPEGASUS_EMBEDDED_INSTANCE_SUPPORT -DPEGASUS_DISABLE_EXECQUERY -DPEGASUS_HAS_SSL  -DPEGASUS_SSL_RANDOMFILE -DPEGASUS_ENABLE_SSL_CRL_VERIFICATION -DPEGASUS_ENABLE_AUDIT_LOGGER -DPEGASUS_ENABLE_IPV6 -DPEGASUS_ENABLE_INDICATION_COUNT -DPEGASUS_ENABLE_INTEROP_PROVIDER -DPEGASUS_USE_EXPERIMENTAL_INTERFACES -DPEGASUS_USE_DEPRECATED_INTERFACES -DPEGASUS_ENABLE_CMPI_PROVIDER_MANAGER -DPEGASUS_USE_RELEASE_CONFIG_OPTIONS -DPEGASUS_USE_RELEASE_DIRS -DPEGASUS_DEST_LIB_DIR=\"lib\" -DPEGASUS_PAM_AUTHENTICATION -DPEGASUS_NO_PASSWORDFILE -DPEGASUS_USE_PAM_STANDALONE_PROC  -I/home/chaoslayer/Downloads/OpenPegasus/pegasus/src  DependCmd.cpp
DependCmd.cpp: In function ‘int DependCmdMain(int, char**)’:
DependCmd.cpp:163: error: ‘strrchr’ was not declared in this scope
DependCmd.cpp:171: error: ‘strcmp’ was not declared in this scope
make[1]: *** [DependCmd.o] Error 1
make[1]: Leaving directory `/home/chaoslayer/Downloads/OpenPegasus/pegasus/src/utils/mu'
make: *** [buildmu] Error 2

```

As I am not familiar with writing C/C++ (I'm just a lazy Java web developer) I don't really know why those errors occur.

Thanx for any help.

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-05-25
For the record:

I've fixed those errors (which just occured with gcc 4.x) by replacing several includes with the new ones as the standard headers files have been cleaned up.

After some more error fixing I finally managed to compile the whole thing but never got it to work. So I gave up and went on to SBLIM which is more or less straight forward and much much cleaner and smaller. In addition it is modular (OpenPegasus doesn't seem to be modular at all) and has a very (!!!) small footprint. That's what enterprise really needs!

But nevertheless, the OpenPegasus package has already been marked as "needs packaging" (if someone wants to do that): [https://bugs.launchpad.net/ubuntu/+bug/322620](https://bugs.launchpad.net/ubuntu/+bug/322620)

I for myself am currently working on getting additional data provider packages into upcoming Ubuntu versions upstreamed.


C]-[aoZ

---

