---
title: "boot error  - link generated from boot-repair"
date: 2015-09-06
forum: New to Ubuntu
---

### Post by sagar10 on 2015-09-06
hello,
I am using vmware player and ubuntu.

I built my own kernel from sources and installed it successfully (at least it shows up in grub).

However, I got a boot-time  error for that kernel:
"gave up waiting for root device"
[COLOR=#000000]"/dev/disk/by-uuid/daa0761d-0492-4773-b369-5c81183b3fcf does not exist. Dropping to a shell"
[/COLOR]
Hence, I ran boot-repair but that did not help. 

Please see the link: [http://paste.ubuntu.com/12298252/](http://paste.ubuntu.com/12298252/)

Note:
[COLOR=#000000](original kernel) vmlinuz-3.16.0-30-generic boots fine!
(new kernel) [/COLOR][COLOR=#000000]vmlinuz-4.2.0-rc8 fails to boot 

Thanks,
Sagar[/COLOR]

---

### Post by sandyd on 2015-09-06
Looks fine, is not an error caused by your system, but by your kernel as you can boot using the old kernel.

How did you build the kernel and what sources are you using?

If you've modified the config options using the .config file, menuconfig or another utility, please attach your configuration to your post. It is possible that a driver or option is missing from your config, which is causing the kernel to not see your partition. 

If you do not have a .config for your kernel, you can get the default .config files that Ubuntu uses from [http://kernel.ubuntu.com/~kernel-ppa/configs/](http://kernel.ubuntu.com/~kernel-ppa/configs/). Copy it to the root of the kernel sources, and build it again.

Side note: The Ubuntu kernel has it's own modifications/patches, and the .config file may reference options that do not exist. Run
```

make oldconfig
```
to ensure compatability.

Some more instructions in Ubuntu Wiki for building a vanilla kernel (ignore what it says about git, you can just download whatever version you want) [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

---

