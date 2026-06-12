---
title: "Trying to setup an NFS server"
date: 2018-09-04
forum: New to Ubuntu
---

### Post by hirno93 on 2018-09-04
I'm following this guide [https://wiki.debian.org/NFSServerSetup](https://wiki.debian.org/NFSServerSetup)

i want to change my .config file to so it enables the module named knfsd.ko since using the command 
  $ grep NFSD /boot/config-`uname -r`shows NFSD is not set.

but how do i go about doing this? changing the config file so it installs the module
[FONT=sans-serif][/FONT]

---

### Post by SeijiSensei on 2018-09-04
The NFS kernel server doesn't require you to do anything like that.  Install the nfs-kernel-server package, edit /etc/exports, and you're good to go.  When you install that package, it will configure the system to start the NFS server at boot.

---

### Post by oldfred on 2018-09-04
Thread from 2006 and still current as it is what I do.
[https://ubuntuforums.org/showthread.php?t=249889](https://ubuntuforums.org/showthread.php?t=249889)

---

