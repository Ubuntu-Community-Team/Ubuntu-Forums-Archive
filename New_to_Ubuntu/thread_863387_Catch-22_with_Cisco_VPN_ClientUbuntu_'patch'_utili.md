---
title: "Catch-22 with Cisco VPN Client/Ubuntu 'patch' utility"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by CompBio on 2008-07-18
I've searched in vain for an answer to this question, so hopefully it's not an FAQ.

I need to install Cisco's VPN client to connect to our school's network.  Unfortunately the software I've downloaded fails to build on my Ubuntu version 2.6.24-19-generic:

vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz

When I run 'sudo ./vpn_install', it gives me the following output:

make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/usr/lib/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/lib/vpnclient/linuxcniapi.o
In file included from /usr/lib/vpnclient/Cniapi.h:15,
                 from /usr/lib/vpnclient/linuxcniapi.c:31:
/usr/lib/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/usr/lib/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/usr/lib/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

From scanning the internet, it looks as if I need a patch for this.  Unfortunately the Ubuntu default installation doesn't include a 'patch' utility.  To get it, I need to run:

sudo apt-get -y install patch

...but I can't get direct internet access without the VPN client -- Catch-22!

Does anyone know of a more recent version of Cisco's VPN client that might compile?  Or is there another way for me to get the patch utility?

Thanks!

---

### Post by TSS on 2008-07-18
My school needs Cisco VPN as well, but the method I took to get it working is not nearly as complicated.  UIUC provides software to download for Linux, but I skipped over that in favor of doing this: 
```
sudo apt-get install network-manager-vpnc
```
That installs a Ciso VPN plugin for network manager.  After that, you need to find out your VPN details and then go to Network Manager > VPN Connections > Configure VPN and then add a new connection.

---

### Post by CompBio on 2008-07-18
That doesn't work for me:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package network-manager-vpnc

I get the exact same result when I try to install 'patch'.

---

### Post by TSS on 2008-07-18
Do you have an active internet connection?  The only reason why I ask is because you mentioned in your first post that you do not.  You need an internet connection to download software from the repositories.

If you do have internet, go to System > Administration > Synaptic Package Manager > Settings > Repositories and tell us what boxes you have checked.

---

### Post by CompBio on 2008-07-18
Sorry, I left that out of my original post.  Currently the only internet access I have is through a secure gateway that our school provides for web browsers.

Is there a way to download these repositories via the web?

(BTW, thanks for your first response -- didn't mean to seem abrupt.)

---

### Post by CompBio on 2008-07-18
Update: sys admins have provided me with a real wire network tap, so for the moment I am connected.

I checked my Synaptic Package Manager and I have the following options selected under the Ubuntu Software tab:

Canonical-supported Open Source software (main)
Community-maintained Open Source software (universe)
Proprietary drivers for devices (restricted)
Software restricted by copyright or legal issues (multiverse)

Under the Third-Party Software tab, nothing is selected.
Under the Updates tab, I have selected:

Important security updates (hardy-security)
Recommended updates (hardy-updates)

Unfortunately the sudo apt-get commands still aren't working for me.

---

