---
title: "Vmware workstation 8 vmware kernel module updater problem on 12.04 xubuntu"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by jcer93705 on 2012-05-25
Hey guys I'm having this problem check the pic. And here the log. 
[IMG]http://i193.photobucket.com/albums/z32/jcervantes11/Screenshot-05242012-113323PM.png[/IMG]


2012-05-24T23:27:14.568-08:00| vthread-3| I120: Log for VMware Workstation pid=9133 version=8.0.3 build=build-703057 option=Release
2012-05-24T23:27:14.568-08:00| vthread-3| I120: The process is 64-bit.
2012-05-24T23:27:14.568-08:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2012-05-24T23:27:14.568-08:00| vthread-3| I120: Host is Linux 3.2.0-24-generic Ubuntu 12.04 LTS
2012-05-24T23:27:14.568-08:00| vthread-3| I120: Msg_Reset:
2012-05-24T23:27:14.568-08:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2012-05-24T23:27:14.568-08:00| vthread-3| I120: ----------------------------------------
2012-05-24T23:27:14.568-08:00| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2012-05-24T23:27:14.568-08:00| vthread-3| I120: Msg_Reset:
2012-05-24T23:27:14.568-08:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2012-05-24T23:27:14.568-08:00| vthread-3| I120: ----------------------------------------
2012-05-24T23:27:14.568-08:00| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2012-05-24T23:27:14.568-08:00| vthread-3| I120: Msg_Reset:
2012-05-24T23:27:14.568-08:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2012-05-24T23:27:14.568-08:00| vthread-3| I120: ----------------------------------------
2012-05-24T23:27:14.568-08:00| vthread-3| I120: PREF Failed to load user preferences.
2012-05-24T23:27:14.568-08:00| vthread-3| W110: Logging to /tmp/vmware-root/modconfig-9133.log
2012-05-24T23:27:14.743-08:00| vthread-3| I120: modconf query interface initialized
2012-05-24T23:27:14.744-08:00| vthread-3| I120: modconf library initialized
2012-05-24T23:27:14.811-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:14.820-08:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-24-generic
2012-05-24T23:27:14.820-08:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-24T23:27:14.820-08:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-24T23:27:14.820-08:00| vthread-3| I120: Validating path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic
2012-05-24T23:27:14.826-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:14.848-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:14.892-08:00| vthread-3| I120: Header path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic is valid.
2012-05-24T23:27:14.892-08:00| vthread-3| I120: Validating path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic
2012-05-24T23:27:14.897-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:14.918-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:14.962-08:00| vthread-3| I120: Header path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic is valid.
2012-05-24T23:27:15.000-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.007-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.012-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.015-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.017-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.061-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.067-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.073-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.075-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.077-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.083-08:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-24-generic
2012-05-24T23:27:15.083-08:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-24T23:27:15.083-08:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-24T23:27:15.083-08:00| vthread-3| I120: Validating path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic
2012-05-24T23:27:15.089-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:15.109-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:15.156-08:00| vthread-3| I120: Header path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic is valid.
2012-05-24T23:27:15.208-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.215-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.218-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.220-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.223-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.228-08:00| vthread-3| I120: Validating path /lib/modules/preferred/build/include for kernel release 3.2.0-24-generic
2012-05-24T23:27:15.228-08:00| vthread-3| I120: Failed to find /lib/modules/preferred/build/include/linux/version.h
2012-05-24T23:27:15.228-08:00| vthread-3| I120: Failed version test: /lib/modules/preferred/build/include/linux/version.h not found.
2012-05-24T23:27:15.228-08:00| vthread-3| I120: Validating path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic
2012-05-24T23:27:15.233-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:15.254-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:15.297-08:00| vthread-3| I120: Header path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic is valid.
2012-05-24T23:27:15.380-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.385-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.387-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.389-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.392-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.822-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:15.822-08:00| vthread-3| I120: Validating path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic
2012-05-24T23:27:15.828-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:15.852-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:15.898-08:00| vthread-3| I120: Header path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic is valid.
2012-05-24T23:27:15.898-08:00| vthread-3| I120: Building module vmmon.
2012-05-24T23:27:15.898-08:00| vthread-3| I120: Extracting the sources of the vmmon module.
2012-05-24T23:27:15.924-08:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-24-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-24T23:27:18.638-08:00| vthread-3| I120: Installing module vmmon from /tmp/vmware-root/modules/vmmon.o to /lib/modules/3.2.0-24-generic/misc.
2012-05-24T23:27:18.638-08:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-24-generic/misc/vmmon.ko
2012-05-24T23:27:20.610-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:20.610-08:00| vthread-3| I120: Validating path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic
2012-05-24T23:27:20.617-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:20.634-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:20.667-08:00| vthread-3| I120: Header path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic is valid.
2012-05-24T23:27:20.667-08:00| vthread-3| I120: Building module vmnet.
2012-05-24T23:27:20.667-08:00| vthread-3| I120: Extracting the sources of the vmnet module.
2012-05-24T23:27:20.684-08:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-24-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-24T23:27:23.350-08:00| vthread-3| I120: Failed to compile module vmnet!
2012-05-24T23:27:23.359-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:23.359-08:00| vthread-3| I120: Validating path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic
2012-05-24T23:27:23.365-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:23.378-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:23.422-08:00| vthread-3| I120: Header path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic is valid.
2012-05-24T23:27:23.422-08:00| vthread-3| I120: Building module vmblock.
2012-05-24T23:27:23.423-08:00| vthread-3| I120: Extracting the sources of the vmblock module.
2012-05-24T23:27:23.445-08:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-24-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-24T23:27:26.716-08:00| vthread-3| I120: Installing module vmblock from /tmp/vmware-root/modules/vmblock.o to /lib/modules/3.2.0-24-generic/misc.
2012-05-24T23:27:26.717-08:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-24-generic/misc/vmblock.ko
2012-05-24T23:27:28.611-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:28.611-08:00| vthread-3| I120: Validating path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic
2012-05-24T23:27:28.618-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:28.641-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:28.688-08:00| vthread-3| I120: Header path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic is valid.
2012-05-24T23:27:28.688-08:00| vthread-3| I120: Building module vmci.
2012-05-24T23:27:28.688-08:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-05-24T23:27:28.706-08:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-24-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-24T23:27:31.631-08:00| vthread-3| I120: Installing module vmci from /tmp/vmware-root/modules/vmci.o to /lib/modules/3.2.0-24-generic/misc.
2012-05-24T23:27:31.632-08:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-24-generic/misc/vmci.ko
2012-05-24T23:27:33.589-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel 3.2.0-24-generic.
2012-05-24T23:27:33.590-08:00| vthread-3| I120: Validating path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic
2012-05-24T23:27:33.593-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:33.612-08:00| vthread-3| I120: Your GCC version: 4.6
2012-05-24T23:27:33.651-08:00| vthread-3| I120: Header path /lib/modules/3.2.0-24-generic/build/include for kernel release 3.2.0-24-generic is valid.
2012-05-24T23:27:33.651-08:00| vthread-3| I120: Building module vmci.
2012-05-24T23:27:33.651-08:00| vthread-3| I120: Extracting the sources of the vmci module.
2012-05-24T23:27:33.680-08:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-24-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-24T23:27:34.621-08:00| vthread-3| I120: Building module vsock.
2012-05-24T23:27:34.621-08:00| vthread-3| I120: Extracting the sources of the vsock module.
2012-05-24T23:27:34.646-08:00| vthread-3| I120: Building module with command: /usr/bin/make -j -C /tmp/vmware-root/modules/vsock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.2.0-24-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6
2012-05-24T23:27:38.137-08:00| vthread-3| I120: Installing module vsock from /tmp/vmware-root/modules/vsock.o to /lib/modules/3.2.0-24-generic/misc.
2012-05-24T23:27:38.138-08:00| vthread-3| I120: Registering file: /usr/lib/vmware-installer/2.0/vmware-installer --register-file vmware-vmx regular /lib/modules/3.2.0-24-generic/misc/vsock.ko



Release Xubuntu 12.04 precise 64 bit
Kernel Linux 3.2.0-24-generic

---

### Post by rai4shu2 on 2012-05-25
Maybe this could help:

[http://communities.vmware.com/message/1401588#1401588](http://communities.vmware.com/message/1401588#1401588)

It's a pretty old patch, so I don't know. I don't have VMware.

---

### Post by mapes12 on 2012-05-26
Are you using the trial or paid for version?

---

### Post by Toz on 2012-05-26
Have a look here: [http://askubuntu.com/questions/116565/unable-to-install-vmware-workstation-v8]("http://askubuntu.com/questions/116565/unable-to-install-vmware-workstation-v8"). Looks like you might need to patch the source.

---

### Post by jcer93705 on 2012-05-27
> **mapes12 said:**
> Are you using the trial or paid for version?

Paid.

---

### Post by mapes12 on 2012-05-27
In that case the Vmware tech guys should be able to help. You can raise a support ticket by logging on here:-

[https://my.vmware.com/web/vmware/login](https://my.vmware.com/web/vmware/login)

---

### Post by jcer93705 on 2012-05-27
> **mapes12 said:**
> In that case the Vmware tech guys should be able to help. You can raise a support ticket by logging on here:-

[https://my.vmware.com/web/vmware/login](https://my.vmware.com/web/vmware/login)

Thank you. I already gotten working with a patch. Thanks.

---

