---
title: "VMware Player: Unable to build kernel module."
date: 2012-09-21
forum: New to Ubuntu
---

### Post by Luigi2012SM64DS on 2012-09-21
Since i have an x86 computer i have to stick to 3.1.6 of VMware Player:mad:. But everytime i try to "build kernel module" it always fails.
Sep 21 21:40:03.703: app-3077859008| Log for VMware Workstation pid=4742 version=7.1.6 build=build-744570 option=Release
Sep 21 21:40:03.703: app-3077859008| The process is 32-bit.
Sep 21 21:40:03.703: app-3077859008| Host codepage=UTF-8 encoding=UTF-8
Sep 21 21:40:03.703: app-3077859008| Logging to /tmp/vmware-root/setup-4742.log
Sep 21 21:40:03.965: app-3077859008| modconf query interface initialized
Sep 21 21:40:03.967: app-3077859008| modconf library initialized
Sep 21 21:40:04.003: app-3077859008| Your GCC version: 4.6
Sep 21 21:40:04.012: app-3077859008| Your GCC version: 4.6
Sep 21 21:40:04.027: app-3077859008| Your GCC version: 4.6
Sep 21 21:40:04.125: app-3077859008| Your GCC version: 4.6
Sep 21 21:40:04.160: app-3077859008| Your GCC version: 4.6
Sep 21 21:40:04.326: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:04.336: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:04.347: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:04.357: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:04.366: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:04.419: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:04.432: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:04.439: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:04.450: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:04.462: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:04.479: app-3077859008| Your GCC version: 4.6
Sep 21 21:40:04.507: app-3077859008| Your GCC version: 4.6
Sep 21 21:40:10.960: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:10.965: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:10.970: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:10.975: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:10.980: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:10.988: app-3077859008| Your GCC version: 4.6
Sep 21 21:40:11.002: app-3077859008| Your GCC version: 4.6
Sep 21 21:40:11.102: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:11.107: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:11.111: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:11.116: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:11.122: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:11.466: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:11.467: app-3077859008| Building module vmmon.
Sep 21 21:40:11.467: app-3077859008| Extracting the sources of the vmmon module.
Sep 21 21:40:11.486: app-3077859008| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-31-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
Sep 21 21:40:13.802: app-3077859008| Failed to compile module vmmon!
Sep 21 21:40:30.874: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:30.886: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:30.898: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:30.910: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:30.922: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:30.937: app-3077859008| Your GCC version: 4.6
Sep 21 21:40:30.965: app-3077859008| Your GCC version: 4.6
Sep 21 21:40:31.077: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:31.082: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:31.087: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:31.093: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:31.098: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:31.542: app-3077859008| Trying to find a suitable PBM set for kernel 3.2.0-31-generic.
Sep 21 21:40:31.543: app-3077859008| Building module vmmon.
Sep 21 21:40:31.543: app-3077859008| Extracting the sources of the vmmon module.
Sep 21 21:40:31.568: app-3077859008| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-31-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
Sep 21 21:40:33.930: app-3077859008| Failed to compile module vmmon!
EDIT: solved by myself

---

### Post by Cheesemill on 2012-09-22
You are going to have a very hard (if not impossible) time getting a version of VMware player that is that old to successfully compile modules for the 3 series kernel.

If I were you I would scrap VMware Player altogether and go with VirtualBox instead.

---

### Post by Luigi2012SM64DS on 2012-09-22
yeah but i NEED windows 98 and vbox doesn't support it.

---

### Post by Cheesemill on 2012-09-22
> **Luigi2012SM64DS said:**
> yeah but i NEED windows 98 and vbox doesn't support it.
I beg to differ...

---

### Post by Luigi2012SM64DS on 2012-09-22
There may be an option for win98 but its not officially supported (no guest additions.)

---

