---
title: "Xubuntu 12.04.02 only boots when I select older kernal"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by castletonia on 2013-07-19
I have an old IBM Thinkpad X30 that has a 1.2Ghz PIII and is maxed out at 1gb of ram.  I installed Xubuntu 12.04.02 on it and that was successful.  I immediately applied the approximately 197 updates and after a reboot it would not start, just a black screen.  If I select the old kernel, then it would boot fine.

I had almost the same issue with Debian Wheezy LXDE, except it would not boot at all after updates since I do not have that much in depth knowledge of linux, I would really prefer to stick with buntu.

I don't know specifically if it is the kernel that is causing it or something else.  Any suggestions as what I can try or how to troubleshoot this more?  I realize this is an old laptop and that it would probably be best with something lighter, but I don't have the time right now to fully learn Debian and I have had problems installing newer versions of anything Ubuntu or Mint, as in I have to connect the hard drive to a different computer in order to install.

Thanks in advance.

---

### Post by 2F4U on 2013-07-19
Do you see the boot menu? Are there any error messages visible on the screen? What are the hardware specs? With older machines, PAE is often an issue since the processor doesn't support it (I have the same issue with my ThinkPad X31), You can check whether your processor supports PAE by executing the command


grep pae /proc/cpuinfo

---

### Post by castletonia on 2013-07-19
There were no errors I saw.  After I choose the newer kernel in the grub menu, screen went black.  I will check tonight when I get home about supporting a PAE kernel.  

Dumb question, but since it will boot with the kernel the iso ships with, can how would I blacklist or prevent any kernel updates?

---

### Post by sudodus on 2013-07-19
I think Xubuntu 12.04.2 will stick to non-PAE kernels during updates. Check with the following commands

```
uname -a
```
```
cat /proc/cpuinfo
```

So I think there is some other problem, maybe a driver, that is not compatible with the hardware. Try some boot options with Xubuntu

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

or try LXLE, a Lubuntu 12.04 fork offering long time support

[http://www.lxle.net/](http://www.lxle.net/)

---

### Post by sudodus on 2013-07-19
> **castletonia said:**
> Dumb question, but since it will boot with the kernel the iso ships with, can how would I blacklist or prevent any kernel updates?

The only dumb question is the one not asked ;-)

One way would be to update manually in a terminal window, and use the following two commands

```
sudo apt-get update
```
```
sudo apt-get ugrade
```
while
```
sudo apt-get dist-upgrade
```
will upgrade the kernel (and do some advanced stuff too). From **[FONT=courier new]man apt-get[/FONT]**

```
       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles
           changing dependencies with new versions of packages; apt-get has a "smart" conflict
           resolution system, and it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade command may remove some
           packages. The /etc/apt/sources.list file contains a list of locations from which to
           retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.

```

I hope someone with more knowledge will give you a good way to blacklist kernel upgrade while preserving the "smart" conflict resolution system of dist-upgrade.

*Edit*: Maybe you can use apt-get with the following option to pin the kernel

       ```
-t, --target-release, --default-release
           This option controls the default input to the policy engine, it creates a default pin at
           priority 990 using the specified release string. This overrides the general settings in
           /etc/apt/preferences. Specifically pinned packages are not affected by the value of this
           option. In short, this option lets you have simple control over which distribution packages
           will be retrieved from. Some common examples might be -t '2.1*', -t unstable or -t sid.
           Configuration Item: APT::Default-Release; see also the apt_preferences(5) manual page.
```

---

### Post by dannyboy79 on 2013-07-19
i have been reading a ton of people having these black screen issues after rebooting, whether a new kernel or after installing a gfx driver. whatever happen to Ubuntu's safe x-server fallback? this is a major issue for ubuntu (linux gfx in general) is that people want to use the OS but all they're getting is a black screen.

can you edit your boot line and remove "quiet splash" so that you can see what the kernel messages are just prior to going black. also, when at a black screen, can you hit ctrl-alt-f1 and login textually?

---

### Post by castletonia on 2013-07-19
Wow, thanks for all the quick responses.  I will try all of this when I get home tonight and report back on what I find.

---

### Post by mörgæs on 2013-07-19
> **2F4U said:**
> Do you see the boot menu? Are there any error messages visible on the screen? What are the hardware specs? With older machines, PAE is often an issue since the processor doesn't support it (I have the same issue with my ThinkPad X31), You can check whether your processor supports PAE by executing the command


grep pae /proc/cpuinfo

All Pentium 3's support PAE.

---

