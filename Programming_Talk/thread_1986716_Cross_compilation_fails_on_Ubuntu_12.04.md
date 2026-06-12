---
title: "Cross compilation fails on Ubuntu 12.04"
date: 2012-05-25
forum: Programming Talk
---

### Post by fgcl2k on 2012-05-25
After upgrading to Ubuntu 12.04 the project I am working on does not
compile/link any more.  It worked/works on Ubuntu 11.10, Debian Squeeze,
Slackware 13.37 and Centos 5.4.

I get the following message:
attempt to open /opt/hardhat/devkit/x86/586/lib/gcc-lib/i586-hardhat-linux/3.2.1/.././opt/hardhat/devkit/x86/586/lib/gcc-lib/i586-hardhat-linux/3.2.1/../../../../i586-hardhat-linux/bin/ld: warning: ld-linux.so.2, needed by /opt/hardhat/devkit/x86/586/lib/gcc-lib/../../target/lib/libc.so.6, not found (try using -rpath or -rpath-link)

I have same settings (environment, PATH, etc). I have tested both
releases booting from the live CD and mounting the same hard disk in
order to be sure I didn't change some settings.

Here is part of the output with the options CXXFLAGS="-Wl,-verbose"

> On Ubuntu 11.10:
> attempt to open libc_nonshared.a failed
> attempt to open /opt/hardhat/devkit/x86/586/lib/gcc-lib/i586-hardhat-linux/3.2.1/libc_nonshared.a failed
> attempt to open /opt/hardhat/devkit/x86/586/lib/gcc-lib/libc_nonshared.a failed
> attempt to open /opt/hardhat/devkit/x86/586/lib/gcc-lib/i586-hardhat-linux/3.2.1/../../../../i586-hardhat-linux/lib/libc_nonshared.a failed
> attempt to open /opt/hardhat/devkit/x86/586/lib/gcc-lib/i586-hardhat-linux/3.2.1/../../../../i586-hardhat-linux/lib/libc_nonshared.a failed
> attempt to open /opt/hardhat/devkit/x86/586/lib/gcc-lib/../../target/lib/libc_nonshared.a failed
> attempt to open /opt/hardhat/devkit/x86/586/lib/gcc-lib/../../target/usr/lib/libc_nonshared.a succeeded
> ...
> ld-linux.so.2 needed by /opt/hardhat/devkit/x86/586/lib/gcc-lib/../../target/lib/libc.so.6
> found ld-linux.so.2 at /mnt/sda6/opt/hardhat/devkit/x86/586/target/lib/ld-linux.so.2


< On Ubuntu 12.04:
< attempt to open /opt/hardhat/devkit/x86/586/lib/gcc-lib/i586-hardhat-linux/3.2.1/libc_nonshared.a failed
< attempt to open /opt/hardhat/devkit/x86/586/lib/gcc-lib/libc_nonshared.a failed
> attempt to open /opt/hardhat/devkit/x86/586/lib/gcc-lib/i586-hardhat-linux/3.2.1/.././opt/hardhat/devkit/x86/586/lib/gcc-lib/i586-hardhat-linux/3.2.1/../../../../i586-hardhat-linux/bin/ld: warning: ld-linux.so.2, needed by /opt/hardhat/devkit/x86/586/lib/gcc-lib/../../target/lib/libc.so.6, not found (try using -rpath or -rpath-link)
< /opt/hardhat/devkit/x86/586/lib/gcc-lib/../../target/lib/libc.so.6: undefined reference to `_dl_lazy@GLIBC_2.1.1'
< /opt/hardhat/devkit/x86/586/lib/gcc-lib/../../target/lib/libc.so.6: undefined reference to `_dl_dst_substitute@GLIBC_2.1.1'
< ...

It looks like Ubuntu 12.04 searches different paths for the libraries
than Ubuntu 11.10, Debian, Slackware and Centos.

Thanks in advance for your help.

---

