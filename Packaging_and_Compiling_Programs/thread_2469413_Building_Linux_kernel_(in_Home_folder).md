---
title: "Building Linux kernel (in Home folder)"
date: 2021-11-28
forum: Packaging and Compiling Programs
---

### Post by player02 on 2021-11-28
Hello,

I am new to Ubuntu. In an intent to learn more about Linux and Ubuntu etc. I downloaded the book Linux Kernel in a Nutshell.

Sadly there are most likely two problems. The first is that I am not as smart as I want to be.
Other thing that also must be is that Ubuntu 21.10 and Linux 5.15.5 are too evolved since 2006.

After following the steps in the book it was not possible to boot the new kernel. Boot status kept hanging at loading ram..

I think it went wrong with these lines (from the book):
# cp arch/i386/boot/bzImage /boot/bzImage-KERNEL_VERSION
# cp System.map /boot/System.map-KERNEL_VERSION

I did change i386 to [COLOR=#232629][FONT=-apple-system]x86_64 though.

After this attempt I tried other more recent instructions on the internet:

[/FONT][/COLOR]https://www.maketecheasier.com/build-custom-kernel-ubuntu/
[https://dev.to/wxyz/howto-compile-linux-kernel-on-ubuntu-applies-to-any-distro-44k7](https://dev.to/wxyz/howto-compile-linux-kernel-on-ubuntu-applies-to-any-distro-44k7)
[https://tutorialforlinux.com/2020/12/30/step-by-step-build-kernel-ubuntu-20-10-guide/](https://tutorialforlinux.com/2020/12/30/step-by-step-build-kernel-ubuntu-20-10-guide/)


Long story short.

Could you please point me to an instruction from which you think its helpful building Linux kernel 5.15.5 on Ubuntu 21.10?
And perhaps you could name the steps for which I have to do some more work instead of just typing over the code.

I would like to stay on Ubuntu 21.10 but the Linux kernel version may be another if that would make things more easy (only goal for now is learning). 


Excuses for asking this much without having contributed anything to this forum.








P.s.
Problems I met following the other instructions from the internet

[TABLE]
[TR]
[TD="align: left"][SIZE=3]-dpkg-source: warning: source directory 'linux-5.15.5' is not <sourcepackage>-<upstreamversion> 'linux-upstream-5.15.5-custom'[/SIZE][/TD]
[/TR]
[TR]
[TD="align: left"][SIZE=3]-Makefile:142: CONFIG_X86_X32 enabled but no binutils support[/SIZE][/TD]
[/TR]
[TR]
[TD="align: left"][SIZE=3]-missing kernel-package[/SIZE][/TD]
[/TR]
[TR]
[TD="align: left"][SIZE=3]-error: debian/rules binary subprocess returned exit status 2[/SIZE][/TD]
[/TR]
[/TABLE]









[COLOR=#232629][FONT=-apple-system]





[/FONT][/COLOR]

---

### Post by Doug S on 2021-11-28
While not exactly what you have asked for, my method for compiling the mainline kernel is detailed [here]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662"). I have been doing it for years, and do keep the method in that link up to date.

---

### Post by mikewhatever on 2021-11-28
So, what is the installed kernel size without "DEBUG_INFO"?

---

### Post by player02 on 2021-11-28
> **Doug S said:**
> While not exactly what you have asked for, my method for compiling the mainline kernel is detailed [here]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662"). I have been doing it for years, and do keep the method in that link up to date.

Wow, great!

This is exactly what I was looking for.

[FONT=var(--ff-mono)]Very complete.

[/FONT]Probably it kept going wrong earlier today because of the config file of my actual kernel 5.13 not being (auto) compatible with that for kernel 5.15.5. I don't know.

But it's working with 5.13.0-rc7-stock.

Thanks a lot Doug!

---

### Post by Doug S on 2021-11-28
> **player02 said:**
> But it's working with 5.13.0-rc7-stock.Suggest kernel 5.13 if you want to stay on that series. However, I recommend you try the latest mainline release, 5.15 or 5.16-rc3. Just steal the kernel configuration from [the mainline PPA ]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D")version, with changes as per [the compile reference link]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662") from earlier.

@mikewhatever: re: DEBUG_INFO: I never cared about the kernel size, only that it takes so much longer to compile. However, I am curious so am compiling kernel 5.16-rc3 now, with the only change being DEBUG_INFO. I'll edit this later.

EDIT 1: As usual, something went wrong:

```
BTF: .tmp_vmlinux.btf: pahole (pahole) is not available
Failed to generate BTF for vmlinux
Try to disable CONFIG_DEBUG_INFO_BTF
make[4]: *** [Makefile:1161: vmlinux] Error 1
make[3]: *** [debian/rules:7: build-arch] Error 2
dpkg-buildpackage: error: debian/rules binary subprocess returned exit status 2
make[2]: *** [scripts/Makefile.package:83: bindeb-pkg] Error 2
make[1]: *** [Makefile:1554: bindeb-pkg] Error 2
make: *** [Makefile:350: __build_one_by_one] Error 2
``` At least now I know why I keep hearing that pahole is needed, but I have never needed it.

EDIT 2: O.K., without CONFIG_DEBUG_INFO_BTF: It takes forever to install the kernel, even if one doesn't select the debug version of the image; It creates 2 images, one is huge.

```
doug@s19:~/temp-k-git/linux$ ls -l ../linux-image-5.16.0-rc3-debug*
-rw-r--r-- 1 doug doug   69911256 Nov 28 16:30 ../linux-image-5.16.0-rc3-debug_5.16.0-rc3-debug-988_amd64.deb
-rw-r--r-- 1 doug doug 1226046784 Nov 28 16:37 ../linux-image-5.16.0-rc3-debug-dbg_5.16.0-rc3-debug-988_amd64.deb
```

Note that Ubuntu doesn't supply the -dbg version of the image anyhow, so I question why should we bother with the substantial overhead when compiling ourselves, unless we really need it?

Installed, I can not tell a difference, so maybe I am doing something wrong. I use this:

```
$ du -ck /lib/modules/5.16.0-rc3-debug /boot/vmlinuz-5.16.0-rc3-debug /boot/System.map-5.16.0-rc3-debug /boot/config-5.16.0-rc3-debug /usr/src/linux-headers-5.16.0-rc3-debug
...
470352  total

```Although, when I uninstalled the debug kernel I got over 9.5 gigabytes of disk space back, whereas with the normal kernel it's 571 megabytes.

EDIT 3: with a debug kernel there are many files in /usr/lib/debug/lib/modules

---

### Post by player02 on 2021-11-29
Thanks for the tips Doug! I hope to try a lot of these things in the near future. Greetings!

---

