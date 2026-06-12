---
title: "[SOLVED] ATI Card 3D acceleration Intrepid"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by marko_4454 on 2008-11-02
Hi all, I have an ATI X600 Radeon card (non-mobility) and I am having problems getting any kind of acceleration in Ubuntu 8.10. This is what I get:

```

marco@marco-desktop:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

I have tried downloading and installing the ATI Proprietary drivers, but I get the following:

```
marco@marco-desktop:~/Desktop$ sh ati-driver-installer-8.532-x86.x86_64-patched.run 
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.532....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.24-16-generic; make sure that the version is being
correctly set by --iscurrentdistro
```

Any help in how to make this work? 
Thanks

---

### Post by marko_4454 on 2008-11-02
I was able to get this working just by removing the fglrx driver from the Hardware Drivers tool and then activating it again. 
It seems like the steps are the same, but it avoids the error somehow.
As long as it works ;)
I get this output now:
marco@marco-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Series
OpenGL version string: 2.1.8087 Release

---

### Post by iption on 2008-12-01
Unfortunatly not working for me. I have the mobility version, and it just displays the first code.

--
Damn, why did I upgrade to 8.10? Wireless still hasn't been fixed and now even the 2D graphics doesn't work.

---

