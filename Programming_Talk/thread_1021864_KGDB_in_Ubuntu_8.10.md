---
title: "KGDB in Ubuntu 8.10"
date: 2008-12-26
forum: Programming Talk
---

### Post by davidbalbert on 2008-12-26
So I've been wrestling with ubuntu 8.10 to try and make it work with the kernel debugger (kgdb) that is included with 2.6.27.  I am trying to run this on a kernel I compiled myself using the same config file that the stock kernel was compiled with and compiling the source from the linux-source-2.6.27 package.  I have not changed any of the kernel config options.  The relevant sections of the file for kgdb are as follows:

```

CONFIG_HAVE_ARCH_KGDB=y
CONFIG_KGDB=y
CONFIG_KGDB_SERIAL_CONSOLE=y
# CONFIG_KGDB_TESTS is not set

```

I complied the kernel using make-kpkg as such:

```
$ fakeroot make-kpkg --revision=1 --append-to-version=-david --initrd kernel_image

```

and then installed the resulting .deb with dpkg.  Everything boots up normally and I can verify that I'm running my kernel as such:

```
$ uname -a
Linux ubuntu-test 2.6.27.2-david #1 SMP Wed Dec 24 19:23:47 EST 2008 i686 GNU/Linux
```

When I try to boot the kernel with kgdbwait, the kernel boots up normally.    Here is the grub entry:

```

title           Ubuntu 8.10, kernel 2.6.27.2-david with kgdb
uuid            a47d32d3-d5a3-454f-abd2-9e10f1aec517
kernel          /boot/vmlinuz-2.6.27.2-david root=UUID=a47d32d3-d5a3-454f-abd2-9e10f1aec517 ro crashkernel=384M-2G:64M@16M,2G-:128M@16M kgdbwait kgdb8250=0,115200
initrd          /boot/initrd.img-2.6.27.2-david
quiet


```

As far as I understand it, when I boot with these options, the kernel should hang close to the beginning of boot with the following output and wait for a remote connection from gdb with the following message:

```

Waiting for connection from remote gdb... 

```

Instead I'm just booting up as if kgdbwait isn't even there.

Some further info that is probably useful:

```

$ dmesg | grep -i kgdb
[    0.000000] Kernel command line: root=UUID=a47d32d3-d5a3-454f-abd2-9e10f1aec517 ro crashkernel=384M-2G:64M@16M,2G-:128M@16M kgdbwait kgdb8250=0,115200

```

```

$ grep -i kgdb /var/log/kern.log
Dec 26 01:24:32 ubuntu-test kernel: [    0.000000] Kernel command line: root=UUID=a47d32d3-d5a3-454f-abd2-9e10f1aec517 ro crashkernel=384M-2G:64M@16M,2G-:128M@16M kgdbwait kgdb8250=0,115200

```

I'm running this on VMware Fusion 2.0.1 with VMware Tools 7.9.3, build-128865.  Other than that, everything is standard stuff from the intrepid repository.

Any help on this would be appreciated.

Best,
-David

---

### Post by davidbalbert on 2008-12-28
For future reference, after some poking around in the kgdboc driver, I found that the kernel command line I was looking for was

```

kgdboc=ttyS0,115200

```

More info can be found here:

[http://www.kernel.org/pub/linux/kernel/people/jwessel/kgdb/ch03s03.html](http://www.kernel.org/pub/linux/kernel/people/jwessel/kgdb/ch03s03.html)

Happy Hacking,
-David

---

