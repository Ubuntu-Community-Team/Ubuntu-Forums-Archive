---
title: "Compiling kernel module problem with header"
date: 2011-11-29
forum: Programming Talk
---

### Post by dante.signal31 on 2011-11-29
I'm programming a pretty simple kernel module just to learn. I'm in a Ubuntu 11.04 box.

The point is that my module includes these libraries at beginning of its source code:

```
#include <linux/kernel.h>
#include <linux/module.h>
#include <linux/init.h>
#include <sys/types.h>
```

To compile my source code I have a makefile like this:

```
obj-m += mymod.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```


Problem is that when I try compile my source code doing "make" I get this error:

```
fatal error: sys/types.h: no such file or directory
compilation terminated.
```

I've been searching the web for any solution but althought it seems I'm not the very first with this problem I've got no clear solution for this. 

Before compiling I had already installed build-essentials, libc6-dev, linux-headers-generic-pae and linux-source. Besides, I've checked I have sys/types.h at: /usr/include/sys/types.h, so I'm sure I have that header but somehow compiler doesn't find it.

Thanks for your help.

Dante

---

### Post by dante.signal31 on 2011-11-29
OK, I guess I've found the solution so I reply myself to leave it registered.

Problem was (I suppose) I'm trying to compile a kernel module so I have no access to userland libraries. I'm not sure because I'm a noob in kernel modules programming, but I think sys/types.h is a userland library. So switching to a kernel space library alternative like linux/types.h should work. I tried that way, changing my include to linux/types.h, and it compiled properly :D

---

### Post by Bachstelze on 2011-11-29
There is no sys/types.h in Linux, it is a BSD thing I think (I have it on OS X).

---

### Post by dante.signal31 on 2011-11-30
It may come from BSD world, but now it's not exclusive from there.

As far as I know, doing a "dpkg-query -S /usr/include/sys/types.h",  that header is provided by libc6-dev package from Ubuntu repositories.

---

### Post by Bachstelze on 2011-11-30
```
firas@itsuki ~ % dpkg-query -S /usr/include/sys/types.h
dpkg-query: no path found matching pattern /usr/include/sys/types.h.

```

---

### Post by dante.signal31 on 2011-12-01
Try to install libc6-dev package and run command again...

---

### Post by dante.signal31 on 2011-12-01
Dpkg-query works over files already present in your system. 

If you have not installed a package its files are not registered in the database dpkg-query uses.

---

### Post by Bachstelze on 2011-12-01
*sigh*

```
firas@itsuki ~ % dpkg -l | grep libc6-dev
ii  libc6-dev                                      2.13-20ubuntu5                          Embedded GNU C Library: Development Libraries and Header Files
firas@itsuki ~ % dpkg-query -S /usr/include/sys/types.h
dpkg-query: no path found matching pattern /usr/include/sys/types.h.
```

I know how dpkg-query works, thank you very much.

---

### Post by dante.signal31 on 2011-12-01
It's strange ... maybe its a problem with libc6-dev package version. Mine has that header, look:


```
@Camelot:~$ **dpkg-query -S /usr/include/sys/types.h**
libc6-dev: /usr/include/sys/types.h
@Camelot:~$ **dpkg -L libc6-dev | grep types.h**
/usr/include/bits/ioctl-types.h
/usr/include/bits/pthreadtypes.h
/usr/include/bits/types.h
/usr/include/bits/xtitypes.h
/usr/include/bits/ipctypes.h
/usr/include/sys/bitypes.h
***/usr/include/sys/types.h***
/usr/include/nl_types.h
/usr/include/rpc/types.h
/usr/include/inttypes.h
@Camelot:~$ **dpkg -l | grep libc6-dev**
ii  libc6-dev                            2.13-0ubuntu13                             Embedded GNU C Library: Development Libraries and Header Files
@Camelot:~$ **uname -a**
Linux Camelot 2.6.38-13-generic-pae #52-Ubuntu SMP Tue Nov 8 17:50:45 UTC 2011 i686 athlon i386 GNU/Linux
@Camelot:~$ **cat /etc/issue**
Ubuntu 11.04 \n \l
```

I don't know why you have not that header but mine comes from that package as you can see.

---

### Post by Bachstelze on 2011-12-01
If you are not using the latest version of Ubuntu, say so. ;) Unless otherwise stated, I always assume the latest version.

---

### Post by Bachstelze on 2011-12-01
So I guess "there's no sys/types.h in Linux" was a bit of a stretch, but it certainly isn't available on all distros. Now I'm not sure why it couldn't be found on your system if you have it, though...

---

### Post by dante.signal31 on 2011-12-02
It looks new versions of package relocate these headers but they are still present.

Libc6-dev in Ubuntu 11.04 installs (among others) these headers:

```
@Camelot:~$ **dpkg -L libc6-dev | grep "/sys/" | sort**
/usr/include/sys/acct.h
/usr/include/sys/bitypes.h
/usr/include/sys/cdefs.h
/usr/include/sys/debugreg.h
/usr/include/sys/dir.h
/usr/include/sys/elf.h
/usr/include/sys/epoll.h
/usr/include/sys/errno.h
/usr/include/sys/eventfd.h
/usr/include/sys/fanotify.h
/usr/include/sys/fcntl.h
/usr/include/sys/file.h
/usr/include/sys/fsuid.h
/usr/include/sys/gmon.h
/usr/include/sys/gmon_out.h
/usr/include/sys/inotify.h
/usr/include/sys/ioctl.h
/usr/include/sys/io.h
/usr/include/sys/ipc.h
/usr/include/sys/kdaemon.h
/usr/include/sys/kd.h
/usr/include/sys/klog.h
/usr/include/sys/mman.h
/usr/include/sys/mount.h
/usr/include/sys/msg.h
/usr/include/sys/mtio.h
/usr/include/sys/param.h
/usr/include/sys/pci.h
/usr/include/sys/perm.h
/usr/include/sys/personality.h
/usr/include/sys/poll.h
/usr/include/sys/prctl.h
/usr/include/sys/procfs.h
/usr/include/sys/profil.h
/usr/include/sys/ptrace.h
/usr/include/sys/queue.h
/usr/include/sys/quota.h
/usr/include/sys/raw.h
/usr/include/sys/reboot.h
/usr/include/sys/reg.h
/usr/include/sys/resource.h
/usr/include/sys/select.h
/usr/include/sys/sem.h
/usr/include/sys/sendfile.h
/usr/include/sys/shm.h
/usr/include/sys/signalfd.h
/usr/include/sys/signal.h
/usr/include/sys/socket.h
/usr/include/sys/socketvar.h
/usr/include/sys/soundcard.h
/usr/include/sys/statfs.h
/usr/include/sys/stat.h
/usr/include/sys/statvfs.h
/usr/include/sys/stropts.h
/usr/include/sys/swap.h
/usr/include/sys/syscall.h
/usr/include/sys/sysctl.h
/usr/include/sys/sysinfo.h
/usr/include/sys/syslog.h
/usr/include/sys/sysmacros.h
/usr/include/sys/termios.h
/usr/include/sys/timeb.h
/usr/include/sys/time.h
/usr/include/sys/timerfd.h
/usr/include/sys/times.h
/usr/include/sys/timex.h
/usr/include/sys/ttychars.h
/usr/include/sys/ttydefaults.h
/usr/include/sys/types.h
/usr/include/sys/ucontext.h
/usr/include/sys/uio.h
/usr/include/sys/ultrasound.h
/usr/include/sys/un.h
/usr/include/sys/unistd.h
/usr/include/sys/user.h
/usr/include/sys/ustat.h
/usr/include/sys/utsname.h
/usr/include/sys/vfs.h
/usr/include/sys/vlimit.h
/usr/include/sys/vm86.h
/usr/include/sys/vt.h
/usr/include/sys/vtimes.h
/usr/include/sys/wait.h
/usr/include/sys/xattr.h
```

If you read content of libc6-package in Ubuntu 11.10 (for instance in: [http://packages.ubuntu.com/oneiric/i386/libc6-dev/filelist](http://packages.ubuntu.com/oneiric/i386/libc6-dev/filelist)) you'll see that those headers are relocated under "/usr/include/i386-linux-gnu" subdir:

```
/usr/include/i386-linux-gnu/sys/acct.h
/usr/include/i386-linux-gnu/sys/bitypes.h
/usr/include/i386-linux-gnu/sys/cdefs.h
/usr/include/i386-linux-gnu/sys/debugreg.h
/usr/include/i386-linux-gnu/sys/dir.h
/usr/include/i386-linux-gnu/sys/elf.h
/usr/include/i386-linux-gnu/sys/epoll.h
/usr/include/i386-linux-gnu/sys/errno.h
/usr/include/i386-linux-gnu/sys/eventfd.h
/usr/include/i386-linux-gnu/sys/fanotify.h
/usr/include/i386-linux-gnu/sys/fcntl.h
/usr/include/i386-linux-gnu/sys/file.h
/usr/include/i386-linux-gnu/sys/fsuid.h
/usr/include/i386-linux-gnu/sys/gmon.h
/usr/include/i386-linux-gnu/sys/gmon_out.h
/usr/include/i386-linux-gnu/sys/inotify.h
/usr/include/i386-linux-gnu/sys/io.h
/usr/include/i386-linux-gnu/sys/ioctl.h
/usr/include/i386-linux-gnu/sys/ipc.h
/usr/include/i386-linux-gnu/sys/kd.h
/usr/include/i386-linux-gnu/sys/kdaemon.h
/usr/include/i386-linux-gnu/sys/klog.h
/usr/include/i386-linux-gnu/sys/mman.h
/usr/include/i386-linux-gnu/sys/mount.h
/usr/include/i386-linux-gnu/sys/msg.h
/usr/include/i386-linux-gnu/sys/mtio.h
/usr/include/i386-linux-gnu/sys/param.h
/usr/include/i386-linux-gnu/sys/pci.h
/usr/include/i386-linux-gnu/sys/perm.h
/usr/include/i386-linux-gnu/sys/personality.h
/usr/include/i386-linux-gnu/sys/poll.h
/usr/include/i386-linux-gnu/sys/prctl.h
/usr/include/i386-linux-gnu/sys/procfs.h
/usr/include/i386-linux-gnu/sys/profil.h
/usr/include/i386-linux-gnu/sys/ptrace.h
/usr/include/i386-linux-gnu/sys/queue.h
/usr/include/i386-linux-gnu/sys/quota.h
/usr/include/i386-linux-gnu/sys/raw.h
/usr/include/i386-linux-gnu/sys/reboot.h
/usr/include/i386-linux-gnu/sys/reg.h
/usr/include/i386-linux-gnu/sys/resource.h
/usr/include/i386-linux-gnu/sys/select.h
/usr/include/i386-linux-gnu/sys/sem.h
/usr/include/i386-linux-gnu/sys/sendfile.h
/usr/include/i386-linux-gnu/sys/shm.h
/usr/include/i386-linux-gnu/sys/signal.h
/usr/include/i386-linux-gnu/sys/signalfd.h
/usr/include/i386-linux-gnu/sys/socket.h
/usr/include/i386-linux-gnu/sys/socketvar.h
/usr/include/i386-linux-gnu/sys/soundcard.h
/usr/include/i386-linux-gnu/sys/stat.h
/usr/include/i386-linux-gnu/sys/statfs.h
/usr/include/i386-linux-gnu/sys/statvfs.h
/usr/include/i386-linux-gnu/sys/stropts.h
/usr/include/i386-linux-gnu/sys/swap.h
/usr/include/i386-linux-gnu/sys/syscall.h
/usr/include/i386-linux-gnu/sys/sysctl.h
/usr/include/i386-linux-gnu/sys/sysinfo.h
/usr/include/i386-linux-gnu/sys/syslog.h
/usr/include/i386-linux-gnu/sys/sysmacros.h
/usr/include/i386-linux-gnu/sys/termios.h
/usr/include/i386-linux-gnu/sys/time.h
/usr/include/i386-linux-gnu/sys/timeb.h
/usr/include/i386-linux-gnu/sys/timerfd.h
/usr/include/i386-linux-gnu/sys/times.h
/usr/include/i386-linux-gnu/sys/timex.h
/usr/include/i386-linux-gnu/sys/ttychars.h
/usr/include/i386-linux-gnu/sys/ttydefaults.h
/usr/include/i386-linux-gnu/sys/types.h
/usr/include/i386-linux-gnu/sys/ucontext.h
/usr/include/i386-linux-gnu/sys/uio.h
/usr/include/i386-linux-gnu/sys/ultrasound.h
/usr/include/i386-linux-gnu/sys/un.h
/usr/include/i386-linux-gnu/sys/unistd.h
/usr/include/i386-linux-gnu/sys/user.h
/usr/include/i386-linux-gnu/sys/ustat.h
/usr/include/i386-linux-gnu/sys/utsname.h
/usr/include/i386-linux-gnu/sys/vfs.h
/usr/include/i386-linux-gnu/sys/vlimit.h
/usr/include/i386-linux-gnu/sys/vm86.h
/usr/include/i386-linux-gnu/sys/vt.h
/usr/include/i386-linux-gnu/sys/vtimes.h
/usr/include/i386-linux-gnu/sys/wait.h
/usr/include/i386-linux-gnu/sys/xattr.h
```

Look at that subdir, surely you'll find it there.

---

