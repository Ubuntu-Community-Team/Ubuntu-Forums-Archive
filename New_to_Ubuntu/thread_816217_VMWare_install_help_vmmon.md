---
title: "VMWare install help: vmmon?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by kevn3k on 2008-06-02
Hi all,

I've been trying to install VMWare so I can run vista through a virtual machine just until I'm comfortable enough with Ubuntu at work to not need it (figuring out Samba and such to navigate the network successfully).  Everything goes fine until it starts asking about *.png files and then vmmon and I get this: 

```

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path

/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 
Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-17-generic/build/include] 
Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-17-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

What does this mean?  I'm pretty sure I have gcc installed (according to Synaptic I do, anyway), so I know I have a C compiler... any ideas?

---

### Post by hyper_ch on 2008-06-02
There's a howto on how to install vmware server on hardy heron. Search the forum and you'll find it.

---

### Post by kevn3k on 2008-06-02
okay, thanks, just found it, working through it now

---

