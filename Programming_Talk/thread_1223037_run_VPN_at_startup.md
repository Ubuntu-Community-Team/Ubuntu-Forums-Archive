---
title: "run VPN at startup"
date: 2009-07-25
forum: Programming Talk
---

### Post by frogotronic on 2009-07-25
Hi,

Don't know if this is the right place to ask this, but I'd like to get the CISCO VPN client to be loaded at start-up on Intrepid Ibex

According to Cisco's installer, this should be the case (look at last line of output (below):

```
Create module directory "/lib/modules/2.6.24-16-generic/CiscoVPN".
Copying module to directory "/lib/modules/2.6.24-16-generic/CiscoVPN".
Already have group 'bin'
 
Creating start/stop script "/etc/init.d/vpnclient_init".
    /etc/init.d/vpnclient_init
Enabling start/stop script for run level 3,4 and 5.
Creating global config /etc/opt/cisco-vpnclient
 
Installing license.txt (VPN Client license) in "/opt/cisco-vpnclient/":
    /opt/cisco-vpnclient/license.txt
 
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
```

But, the script is NOT being run automatically at start-up...how do I accomplish this?

Thanks,
- CH    :popcorn:

---

### Post by Reiger on 2009-07-25
The /etc/init.d directory is merely a repository for scripts: what scripts are (not) called depends on the directories containing the symlinks per run-level to this repository. There is some update command... EDIT: Think it is update-rc.d but could be wrong.

---

### Post by frogotronic on 2009-07-25
Okay, I tried

```
# update-initdramfs
```


but that didn't do it...

EDIT:  I think you're (Reiger) correct [http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by frogotronic on 2009-07-26
Nope - that didn't do it either.

Neither did putting cisco_ipsec (the cisco module) in the /etc/modules file make a difference.

Hmmmm....:-k


-CH

---

### Post by Reiger on 2009-07-26
Ooh is it a module. I really should learn not to post that time of night. EDIT: Check if dmesg or modprobe complain about errors: modprobe <module_name> first, then dmesg | grep <module_name>

---

