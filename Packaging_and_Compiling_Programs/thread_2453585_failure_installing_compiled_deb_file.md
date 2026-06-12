---
title: "failure installing compiled deb file"
date: 2020-11-13
forum: Packaging and Compiling Programs
---

### Post by klemenmo on 2020-11-13
Hi,
I have a Ubuntu server 20.04 LT, for backup we use IBM TSM client. Part of this TSM client installation is component "filepath" for which you get source code, which you have to compile. ([COLOR=#323232][FONT=ibm-plex-mono]TIVsm-filepath-source.tar.gz)[/FONT][/COLOR]
[https://www.ibm.com/support/knowledgecenter/SSGSG7_7.1.8/client/t_inst_linuxx86client.html](https://www.ibm.com/support/knowledgecenter/SSGSG7_7.1.8/client/t_inst_linuxx86client.html)

Compile process goes without any errors and I get a valid .deb file. The problem starts when I try to install this compiled .deb file.
It seems to be a problem with older version of kernel-headers, but I do not know how to solve it.

Here are the steps done and error I get:

[FONT=courier new]root@ehrambafiles05:/home/zziroot/install/linux86_DEB/jbb_gpl# uname -a
Linux ehrambafiles05 5.4.0-53-generic #59-Ubuntu SMP Wed Oct 21 09:38:44 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
root@ehrambafiles05:/home/zziroot/install/linux86_DEB/jbb_gpl# uname -r
5.4.0-53-generic
root@ehrambafiles05:/home/zziroot/install/linux86_DEB/jbb_gpl# make RELNUM=8.1.10-0 deb
Make Module:filepath Version:8.1.10-0 Flags:-g -U_FORTIFY_SOURCE -D_FORTIFY_SOURCE=0 -D_KERNEL -D__SMP__ -D_REENTRANT -D_x86_64
make -C /lib/modules/5.4.0-53-generic/build M=/home/zziroot/install/linux86_DEB/jbb_gpl modules
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-53-generic'
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/audit.o
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/error.o
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/hook.o
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/hash.o
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/ir.o
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/jbb.o
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/log.o
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/mem.o
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/pf.o
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/str_supp.o
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/trace.o
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/watch.o
  CC [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/xml.o
  LD [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/filepath.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/zziroot/install/linux86_DEB/jbb_gpl/filepath.ko
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-53-generic'
sh makedeb.sh 8.1.10-0
dpkg-deb: building package 'tivsm-filepath' in 'tivsm-filepath-8.1.10-0.deb'.
root@ehrambafiles05:/home/zziroot/install/linux86_DEB/jbb_gpl# 
-rw-r--r-- 1 root    root    202556 Nov 13 14:56 tivsm-filepath-8.1.10-0.deb


root@ehrambafiles05:/home/zziroot/install/linux86_DEB# dpkg -i jbb_gpl/tivsm-filepath-8.1.10-0.deb 
Selecting previously unselected package tivsm-filepath.
(Reading database ... 146651 files and directories currently installed.)
Preparing to unpack .../tivsm-filepath-8.1.10-0.deb ...
Unpacking tivsm-filepath (8.1.10-0) ...
Setting up tivsm-filepath (8.1.10-0) ...
insmod: ERROR: could not insert module filepath.ko: Invalid module format
ERROR: Failed to start filepath with error 1
root@ehrambafiles05:/home/zziroot/install/linux86_DEB# 


root@ehrambafiles05:/home/zziroot/install/linux86_DEB# /etc/init.d/filepath start
insmod: ERROR: could not insert module filepath.ko: Invalid module format
root@ehrambafiles05:/home/zziroot/install/linux86_DEB# 


syslog error:
Nov 13 15:17:55 ehrambafiles05 kernel: [ 2219.283543] filepath: version magic '5.4.0-52-generic SMP mod_unload ' should be '5.4.0-53-generic SMP mod_unload '[/FONT]


Any help would be very appreciated.

regards, Klemen

---

