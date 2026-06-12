---
title: "Installing vmware-tools-distrib"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by GoranCro on 2008-09-01
I am running Windows XP with VMware Workstation and I have successfully installed Ubuntu 8.04. Right now I am trying to install the vmware tools but I am not able to get it going.

The default directory chosen by the installer appears here:
```
What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include]
```

I found that the actual directory was:
```
/lib/modules/2.6.24-19-generic/build/include
```

But I get this error:
```
What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /lib/modules/2.6.24-19-generic/build/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.24-19-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.

```

Don't know where to go from here :(

---

