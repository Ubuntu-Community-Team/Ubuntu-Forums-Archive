---
title: "Installation of Vmware - need help!"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Dev'olution on 2008-06-09
Ok so i installed it and it bombed out - and i tried to run it thru commandline and it told me to run a config script - i did - and this is what happened.

```
kristian@kristian-laptop:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-18-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-18-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config0/vmmon-only/linux/driver.c:147: warning: initialisation from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:151: warning: initialisation from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

help? :confused:

---

### Post by Anicka on 2008-06-09
You're trying to install Vmware server on a Ubuntu host?

Have you looked here: [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

---

### Post by CSEatOSU on 2008-06-09
Try this one: [http://ubuntuforums.org/showthread.php?t=788169&highlight=vmware+host+ip]("http://ubuntuforums.org/showthread.php?t=788169&highlight=vmware+host+ip")

I just did it not an hour ago and it worked perfect.  All you do is create the script file, run the script and answer 'no' to that question the first time just like the instructions say.

---

### Post by michaelaly on 2008-06-09
I second using [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934) - good instructions, worked great.

---

### Post by cj2003 on 2008-06-09
There is also [this guide: Install VMWare Tools on Ubuntu 8.04 ]("http://ubuntu-news.net/modules/news/article.php?storyid=4579")

---

### Post by Phoenixzeus on 2008-06-09
Are you running Ubuntu 8.04 or 7.10? Because from my Experience 8.04 needs a little script, and vmware on 7.10 is just an automated install away ...

---

### Post by CSEatOSU on 2008-06-09
> **Phoenixzeus said:**
> Are you running Ubuntu 8.04 or 7.10? Because from my Experience 8.04 needs a little script, and vmware on 7.10 is just an automated install away ...

I'm running 8.04

---

