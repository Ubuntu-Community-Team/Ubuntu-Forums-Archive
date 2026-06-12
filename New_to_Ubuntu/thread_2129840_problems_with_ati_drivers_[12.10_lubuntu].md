---
title: "problems with ati drivers [12.10 lubuntu]"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by darvin on 2013-03-27
Hi all, im from Bulgaria and im a beginner on linux.
I have problems with ATI driver installation.
I download 13.1 version on AMD site.
My video card is: ATI HD 4200 (integrated in Asrock 880g extreeme 3)
When i run installation and finished it, i get:
```

loki_setup: directory: (null)
DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details
Removing temporary directory: fglrx-install.ZS7bBO

```
In fglrx-install.log i have this:
```

Check if system has the tools required for installation.
Uninstalling any previously installed drivers.


Creating symlink /var/lib/dkms/fglrx/8.97.100.7/source ->
                 /usr/src/fglrx-8.97.100.7


DKMS: add completed.


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.97.100.7/build; sh make.sh --nohints --uname_r=3.5.0-26-generic --norootcheck......(bad exit status: 1)
[Error] Kernel Module : Failed to build fglrx-8.97.100.7 with DKMS
[Error] Kernel Module : Removing fglrx-8.97.100.7 from DKMS


------------------------------
Deleting module version: 8.97.100.7
completely from the DKMS tree.
------------------------------
Done.
[Reboot] Kernel Module : update-initramfs
```


Please, give me a full guide how to install the ati drivers (fglrx)
Thanks!

---

### Post by deadflowr on 2013-03-27
See this

[http://askubuntu.com/questions/209876/upgraded-ubuntu-from-12-04-to-12-10-ati-radeon-hd-3450-catastrophe](http://askubuntu.com/questions/209876/upgraded-ubuntu-from-12-04-to-12-10-ati-radeon-hd-3450-catastrophe)

Though that instance is for a different card, it applies to your situation as well.

---

### Post by darvin on 2013-03-27
Thanks, it works!

---

