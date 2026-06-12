---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-08-03
forum: New to Ubuntu
---

### Post by totappa on 2016-08-03
hi guys.. I am new to ubuntu and unable to update/upgrade or install anything.I am using ubuntu on USB stick.
Following errors are occuring.I tried few things found online, didn't work.

```
ubuntu@ubuntu:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial InRelease
Hit:2 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                        
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]    
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]      
Fetched 190 kB in 5s (34.4 kB/s)                                      

** (appstreamcli:27526): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
ubuntu@ubuntu:~$
```
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
```
ubuntu@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up libc-bin (2.23-0ubuntu3) ...
Bus error (core dumped)
/sbin/ldconfig.real: Path `/lib/x86_64-linux-gnu' given more than once
/sbin/ldconfig.real: Path `/usr/lib/x86_64-linux-gnu' given more than once
/usr/lib/x86_64-linux-gnu/libfakeroot:
    libfakeroot-0.so -> libfakeroot-tcp.so
/usr/local/lib:
/lib/x86_64-linux-gnu:
    libz.so.1 -> libz.so.1.2.8
    libxtables.so.11 -> libxtables.so.11.0.0
    libx86.so.1 -> libx86.so.1
    libwrap.so.0 -> libwrap.so.0.7.6
    libuuid.so.1 -> libuuid.so.1.3.0
    libutil.so.1 -> libutil-2.23.so
    libusb-1.0.so.0 -> libusb-1.0.so.0.1.0
    libusb-0.1.so.4 -> libusb-0.1.so.4.4.4
    libulockmgr.so.1 -> libulockmgr.so.1.0.1
    libudev.so.1 -> libudev.so.1.6.4
    libtinfo.so.5 -> libtinfo.so.5.9
    libthread_db.so.1 -> libthread_db-1.0.so
    libsystemd.so.0 -> libsystemd.so.0.14.0
    libssl.so.1.0.0 -> libssl.so.1.0.0
    libss.so.2 -> libss.so.2.0
    libsmartcols.so.1 -> libsmartcols.so.1.1.0
    libslang.so.2 -> libslang.so.2.3.0
    libsepol.so.1 -> libsepol.so.1
    libselinux.so.1 -> libselinux.so.1
    libseccomp.so.2 -> libseccomp.so.2.2.3
    librt.so.1 -> librt-2.23.so
    libresolv.so.2 -> libresolv-2.23.so
    libreadline.so.6 -> libreadline.so.6.3
    libreadline.so.5 -> libreadline.so.5.2
    libpthread.so.0 -> libpthread-2.23.so
    libprocps.so.4 -> libprocps.so.4.0.0
    libpopt.so.0 -> libpopt.so.0.0.0
    libpng12.so.0 -> libpng12.so.0.54.0
    libply.so.4 -> libply.so.4.0.0
    libply-splash-graphics.so.4 -> libply-splash-graphics.so.4.0.0
    libply-splash-core.so.4 -> libply-splash-core.so.4.0.0
    libply-boot-client.so.4 -> libply-boot-client.so.4.0.0
    libpcsclite.so.1 -> libpcsclite.so.1.0.0
    libpcre.so.3 -> libpcre.so.3.13.2
    libpcprofile.so -> libpcprofile.so
    libpci.so.3 -> libpci.so.3.3.1
    libparted.so.2 -> libparted.so.2.0.1
    libparted-fs-resize.so.0 -> libparted-fs-resize.so.0.0.1
    libpamc.so.0 -> libpamc.so.0.82.1
    libpam_misc.so.0 -> libpam_misc.so.0.82.0
    libpam.so.0 -> libpam.so.0.83.1
    libntfs-3g.so.861 -> libntfs-3g.so.861.0.0
    libnss_nisplus.so.2 -> libnss_nisplus-2.23.so
    libnss_nis.so.2 -> libnss_nis-2.23.so
    libnss_mdns_minimal.so.2 -> libnss_mdns_minimal.so.2
    libnss_mdns6_minimal.so.2 -> libnss_mdns6_minimal.so.2
    libnss_mdns6.so.2 -> libnss_mdns6.so.2
    libnss_mdns4_minimal.so.2 -> libnss_mdns4_minimal.so.2
    libnss_mdns4.so.2 -> libnss_mdns4.so.2
    libnss_mdns.so.2 -> libnss_mdns.so.2
    libnss_hesiod.so.2 -> libnss_hesiod-2.23.so
    libnss_files.so.2 -> libnss_files-2.23.so
    libnss_dns.so.2 -> libnss_dns-2.23.so
    libnss_compat.so.2 -> libnss_compat-2.23.so
    libnsl.so.1 -> libnsl-2.23.so
    libnl-genl-3.so.200 -> libnl-genl-3.so.200.22.0
    libnl-3.so.200 -> libnl-3.so.200.22.0
    libnih.so.1 -> libnih.so.1.0.0
    libnih-dbus.so.1 -> libnih-dbus.so.1.0.0
    libnewt.so.0.52 -> libnewt.so.0.52.18
    libncursesw.so.5 -> libncursesw.so.5.9
    libncurses.so.5 -> libncurses.so.5.9
    libmvec.so.1 -> libmvec-2.23.so
    libmount.so.1 -> libmount.so.1.1.0
    libmnl.so.0 -> libmnl.so.0.1.0
    libmemusage.so -> libmemusage.so
    libm.so.6 -> libm-2.23.so
    liblzo2.so.2 -> liblzo2.so.2.0.0
    liblzma.so.5 -> liblzma.so.5.0.0
    liblvm2cmd.so.2.02 -> liblvm2cmd.so.2.02
    liblvm2app.so.2.2 -> liblvm2app.so.2.2
    libkmod.so.2 -> libkmod.so.2.3.0
    libkeyutils.so.1 -> libkeyutils.so.1.5
    libjson-c.so.2 -> libjson-c.so.2.0.0
    libiw.so.30 -> libiw.so.30
    libisc-export.so.160 -> libisc-export.so.160.0.0
    libiptc.so.0 -> libiptc.so.0.0.0
    libip6tc.so.0 -> libip6tc.so.0.1.0
    libip4tc.so.0 -> libip4tc.so.0.1.0
    libhistory.so.6 -> libhistory.so.6.3
    libhistory.so.5 -> libhistory.so.5.2
    libgpg-error.so.0 -> libgpg-error.so.0.17.0
    libglib-2.0.so.0 -> libglib-2.0.so.0.4800.1
    libgcrypt.so.20 -> libgcrypt.so.20.0.5
    libgcc_s.so.1 -> libgcc_s.so.1
    libfuse.so.2 -> libfuse.so.2.9.4
    libfdisk.so.1 -> libfdisk.so.1.1.0
    libext2fs.so.2 -> libext2fs.so.2.4
    libexpat.so.1 -> libexpat.so.1.6.0
    libe2p.so.2 -> libe2p.so.2.3
    libdns-export.so.162 -> libdns-export.so.162.1.3
    libdl.so.2 -> libdl-2.23.so
    libdevmapper.so.1.02.1 -> libdevmapper.so.1.02.1
    libdevmapper-event.so.1.02.1 -> libdevmapper-event.so.1.02.1
    libdevmapper-event-lvm2.so.2.02 -> libdevmapper-event-lvm2.so.2.02
    libdbus-1.so.3 -> libdbus-1.so.3.14.6
    libcryptsetup.so.4 -> libcryptsetup.so.4.6.0
    libcrypto.so.1.0.0 -> libcrypto.so.1.0.0
    libcrypt.so.1 -> libcrypt-2.23.so
    libcom_err.so.2 -> libcom_err.so.2.1
    libcidn.so.1 -> libcidn-2.23.so
    libcgmanager.so.0 -> libcgmanager.so.0.0.0
    libcap.so.2 -> libcap.so.2.24
    libc.so.6 -> libc-2.23.so
    libbz2.so.1.0 -> libbz2.so.1.0.4
    libbsd.so.0 -> libbsd.so.0.8.2
    libbrlapi.so.0.6 -> libbrlapi.so.0.6.4
    libblkid.so.1 -> libblkid.so.1.1.0
    libaudit.so.1 -> libaudit.so.1.0.0
    libattr.so.1 -> libattr.so.1.1.0
    libatm.so.1 -> libatm.so.1.0.0
    libatasmart.so.4 -> libatasmart.so.4.0.5
    libapparmor.so.1 -> libapparmor.so.1.4.0
    libanl.so.1 -> libanl-2.23.so
    libacl.so.1 -> libacl.so.1.1.0
    libSegFault.so -> libSegFault.so
    libBrokenLocale.so.1 -> libBrokenLocale-2.23.so
/sbin/ldconfig.real: /lib/x86_64-linux-gnu/ld-2.23.so is the dynamic linker, ignoring

    ld-linux-x86-64.so.2 -> ld-2.23.so
/usr/lib/x86_64-linux-gnu:
Bus error (core dumped)
dpkg: error processing package libc-bin (--configure):
 subprocess installed post-installation script returned error exit status 135
Errors were encountered while processing:
 libc-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$
```
------------------------------------------------------------------------------------------------------------------
PLEASE HELP!!!!!

---

### Post by mörgæs on 2016-08-04
What exactly are you trying to achieve? A persistent Ubuntu install on a USB stick?

---

### Post by totappa on 2016-08-05
Actually the problem was with mdk5 checksum.I downloaded the new file and I m trying to use ubuntu through USB(I haven't installed on my computer).
now i am getting only the first error.
----------------------------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo apt-get update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]
Fetched 95.7 kB in 3s (30.7 kB/s)   

** (appstreamcli:10339): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Is it because I m using through USB?I want to work for few days and then install.
HELP!!!

---

### Post by mörgæs on 2016-08-05
If you want to test Ubuntu using USB for a few days I don't think you need updates. Just don't use the system for anything personal or sensitive while testing.

---

