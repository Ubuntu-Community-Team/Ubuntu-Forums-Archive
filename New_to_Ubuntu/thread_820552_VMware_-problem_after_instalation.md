---
title: "VMware -problem after instalation"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-06
When i started vmware its geting me these error's.

```
raj@raj-workstation:~$ vmware
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
raj@raj-workstation:~$ 




```

what should i do now.

---

### Post by bcom on 2008-06-06
Here is the link to help you install vmware server: [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

You need to install the gcc compiler:  sudo apt-get install build-essential

---

### Post by diablo75 on 2008-06-06
Did you create symbolic links?  At the bottom of the sticky you probably followed to install VMware, there are two lines you need to paste into a terminal window after installing VMware, but before attempting to run it.  Don't worry, you didn't break anything.  Simply paste the following into Terminal and try again:

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1

```

and then

```
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0
```

---

### Post by rraj.be on 2008-06-06
yes.

I did that thing.

I had the same issue two hors before and i uninstalled vmware completly and just reinstalled.

Again the same problem.:(

---

