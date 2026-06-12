---
title: "How to update distro/kernel via command line?"
date: 2015-03-07
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-03-07
I'm using minimal Ubuntu.

Quick newbie questions: 

1. How to update distro version and kernel to the stable version via command line? Will sudo apt-get update followed by sudo apt-get dist-upgrade update both the distro and the kernel?

2. Are there ever any reasons to install the latest "stable" kernel available (one that has not been tested specifically for an Ubuntu version)?

3. Any other maintenance-related commands/actions/tips a Linux user would do in regard go a newer version of Ubuntu that is available?

4. On minimal Ubuntu, I only have Synapticinstalled. I can't find a way to get Synaptic to replicate Muon (for Kubuntu) in constantly checking (or automatically checking at system startup) and asking for security/package updates in general. Is there an option for Synaptic to do this (I would like to have Synaptic do everything package-related if possible)? Is there an option to automatically update security packages without being prompted and is it a good idea to do it this way?

Thanks.

---

### Post by grahammechanical on 2015-03-07
The usual commands for updating a released version of Ubuntu using the command line are:

```

sudo apt-get update
sudo apt-get upgrade
```

I would not recommend using apt-get dist-upgrade except when we have installed a PPA and want to bring in the software from it. Using apt-get dist-upgrade will bring in packages that are being held back for some reason. You may find that something important is removed. If we do use apt-get dist-upgrade it should be after using apt-get upgrade.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

We can only update/upgrade to packages that are in the archive/repositories. Untested kernels are not called "stable." What the Linux developers call a "stable" kernel is not necessarily called "stable" by the Ubuntu developers. Which is why they are not put in the normal update channels without being tested.

Newer Linux kernels are put in the next release of Ubuntu. Ubuntu LTS releases get these later kernels by means of point releases and the hardware enablement stack.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

If a newer Linux kernel has improvements or bug fixes that will benefit you then installing that kernel maybe a useful thing to do. I am running Vivid Vervet which is the development code of Ubuntu 15.04.

Recently I installed Linux kernel 4.0 release candidate which the Linux developers consider stable. Everything worked fine when using the open source video driver but the proprietary video driver would not build a model for the 4.0 kernel. I got a very low resolution screen. I had no reason to install it except curiosity and to test. It added nothing I did not already have.

Regards.

---

### Post by garycheng12 on 2015-03-09
Thank you.

---

### Post by Bucky Ball on 2015-03-09
Actually ...

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

These commands will upgrade the kernel, if it needs to be, and the installed OS. It will NOT upgrade your release to a newer one. ;)

---

### Post by deadflowr on 2015-03-09
> **Bucky Ball said:**
> Actually ...

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

These commands will upgrade the kernel, if it needs to be, and the installed OS. It will NOT upgrade your release to a newer one. ;)

Adding: if by chance you actually wanted to upgrade the release from, let's say, Ubuntu 12.04 to Ubuntu 14.04 you would use the command
```
do-release-upgrade
```
you can use/add sudo to begin, or not.
it'll ask for a password eventually if you choose not to add sudo.
So if you want to use sudo to start or not is really up to you.

---

### Post by garycheng12 on 2015-03-09
> **Bucky Ball said:**
> Actually ...

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

These commands will upgrade the kernel, if it needs to be, and the installed OS. It will NOT upgrade your release to a newer one. ;)

What's the difference between upgrading the installed OS and upgrading the release to a newer one? Also, anyone know the answer to my 4th question? Thanks.

---

### Post by Bucky Ball on 2015-03-09
The former upgrades all software that needs to be in the current installed release. The latter, upgrading to a newer release, does just that: upgrades to a newer release. If you are on 14.04 and run the 'do-release-upgrade' command provided by deadflowr, you will upgrade 14.04 to the 14.10 release.

---

### Post by garycheng12 on 2015-03-09
Yea, I just realized it. Knew it would be a silly question--as a Windows user, "upgrading Windows" typically means upgrading it to a newer release. Thanks all.

---

### Post by garycheng12 on 2015-03-09
> **Bucky Ball said:**
> Actually ...

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

These commands will upgrade the kernel, if it needs to be, and the installed OS. It will NOT upgrade your release to a newer one. ;)

Out of curiosity and for clarity, why run both apt-get upgrade and apt-get dist-upgrade and not one or the other? Doesn't apt-get dist-upgrade do everything apt-get upgrade does and more (where it also updates packages that require installing or uninstalling of dependencies unlike apt-get ugprade)?

---

### Post by Bucky Ball on 2015-03-09
> apt-get dist-upgrade differs from apt-get upgrade in that it will remove obsolete packages and add new dependencies, while apt-get upgrade will not. this is necessary when upgrading from one distro release to another, but it is not the *only* time it is necessary. 

From [here]("http://ubuntulinuxtipstricks.blogspot.com.au/2010/02/dist-upgrade-misnomer-confusion.html"). Sure there's plenty more explanations out there. ;)

Wondering if there's any reason to use apt-get upgrade, actually.

---

