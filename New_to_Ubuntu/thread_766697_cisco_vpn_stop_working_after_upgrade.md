---
title: "cisco vpn stop working after upgrade"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by peterlauri on 2008-04-25
Hi,

I updated to the latest ubuntu 8.04 from 7.10, and after that my Cisco VPN stopped working. So I guessed that the vpn didn't work due to some problems, so I uninstalled and tried to install again. However, no progress, complaining about inserting module. Below is the complete sequence of what I did from command line.

Anyone with insights?

/Peter

==========

lauri@pjotr:~/vpnclient$ sudo ./vpn_uninstall 
./vpn_uninstall: line 48: chkconfig: command not found
Cisco Systems VPN Client Version BUILDVER_STRING Linux UnInstaller
Copyright (C) 1998-2001 Cisco Systems, Inc. All Rights Reserved.

Are you sure that you wish to uninstall the VPN Client?  [no] yes

Do you wish to remove all existing profiles and certificates?  [no] yes
 - Existing Profiles and Certificates will be removed
 - Binary uninstall directory set to /usr/local/bin

Cleaning up installed files and directory....
Shutting down /opt/cisco-vpnclient/bin/vpnclient: module cisco_ipsec is not running.
Stopped: /etc/init.d/vpnclient_init (VPN init script)
Removed: /usr/local/bin/vpnclient
Removed: /usr/local/bin/ipseclog
Removed: /usr/local/bin/cisco_cert_mgr
Removed: /opt/cisco-vpnclient (package install directory)
Removed: /etc/rc3.d/S85vpnclient_init (VPN rc3.d link)
Removed: /etc/rc4.d/S85vpnclient_init (VPN rc4.d link)
Removed: /etc/rc5.d/S85vpnclient_init (VPN rc5.d link)
Removed: /etc/init.d/vpnclient_init (VPN init script)
Removed: /etc/opt/cisco-vpnclient (profiles, certificates, INI)
Removed: /etc/CiscoSystemsVPNClient (symlink)
Done.
lauri@pjotr:~/vpnclient$ sudo ./vpn_install 
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-16-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-16-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-16-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/lauri/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/lauri/vpnclient/linuxcniapi.o
In file included from /home/lauri/vpnclient/Cniapi.h:15,
                 from /home/lauri/vpnclient/linuxcniapi.c:30:
/home/lauri/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/lauri/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/lauri/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
Create module directory "/lib/modules/2.6.24-16-generic/CiscoVPN".
Copying module to directory "/lib/modules/2.6.24-16-generic/CiscoVPN".
Already have group 'bin'

Creating start/stop script "/etc/init.d/vpnclient_init".
    /etc/init.d/vpnclient_init
Enabling start/stop script for run level 3,4 and 5.
Creating global config /etc/opt/cisco-vpnclient

Installing license.txt (VPN Client license) in "/opt/cisco-vpnclient/":

Installing bundled user profiles in "/etc/opt/cisco-vpnclient/Profiles/":
* New Profiles     : sample 

Copying binaries to directory "/opt/cisco-vpnclient/bin".
Adding symlinks to "/usr/local/bin".
    /opt/cisco-vpnclient/bin/vpnclient
    /opt/cisco-vpnclient/bin/cisco_cert_mgr
    /opt/cisco-vpnclient/bin/ipseclog
Copying setuid binaries to directory "/opt/cisco-vpnclient/bin".
    /opt/cisco-vpnclient/bin/cvpnd
Copying libraries to directory "/opt/cisco-vpnclient/lib".
    /opt/cisco-vpnclient/lib/libvpnapi.so
Copying header files to directory "/opt/cisco-vpnclient/include".
    /opt/cisco-vpnclient/include/vpnapi.h

Setting permissions.
    /opt/cisco-vpnclient/bin/cvpnd (setuid root)
    /opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient/Profiles (group bin readable)
    /etc/opt/cisco-vpnclient/Certificates (group bin readable)
* You may wish to change these permissions to restrict access to root.
* You must run "/etc/init.d/vpnclient_init start" before using the client.
* This script will be run AUTOMATICALLY every time you reboot your computer.
lauri@pjotr:~/vpnclient$ /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: Failed (super user access required)
lauri@pjotr:~/vpnclient$ sudo /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.24-16-generic/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)
lauri@pjotr:~/vpnclient$ 
lauri@pjotr:~/vpnclient$ uname -a
Linux pjotr 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

---

### Post by ShreveportLA on 2008-04-28
Hey Peter,

I am getting the same error.

edmorin@edmorin-desktop:~$ sudo /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.24-16-generic/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)
edmorin@edmorin-desktop:~$ 

Any help would be appreciated.

Ed

---

### Post by hackmeister on 2008-04-29
Issue is with Linux kernels => 2.6.24. Fix is pretty easy:
[http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/](http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/)

---

