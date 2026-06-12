---
title: "Problems with &quot;pae&quot; on Ubuntu 12.04"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by chulik on 2012-04-27
Dear sirs,

I've tried to install pae kernel on my dell inspiron M5110 note and got "kernel panic". So, it seems that ubuntu can't find some packages. Here is the log:
```

# apt-get install linux-image-3.2.0-23-generic-pae

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils:i386 linux-doc-3.2.0:i386 linux-source-3.2.0:i386 linux-tools:i386
The following NEW packages will be installed:
  linux-image-3.2.0-23-generic-pae:i386
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/37.9 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Selecting previously unselected package linux-image-3.2.0-23-generic-pae:i386.
(Reading database ... 181396 files and directories currently installed.)
Unpacking linux-image-3.2.0-23-generic-pae:i386 (from .../linux-image-3.2.0-23-generic-pae_3.2.0-23.36_i386.deb) ...
Done.
Setting up linux-image-3.2.0-23-generic-pae:i386 (3.2.0-23.36) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-23-generic-pae /boot/vmlinuz-3.2.0-23-generic-pae
[COLOR=Red]Error! Your kernel headers for kernel 3.2.0-23-generic-pae cannot be found.
Please install the linux-headers-3.2.0-23-generic-pae package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.2.0-23-generic-pae cannot be found.
Please install the linux-headers-3.2.0-23-generic-pae package,[/COLOR]
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-23-generic-pae /boot/vmlinuz-3.2.0-23-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic-pae
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-23-generic-pae /boot/vmlinuz-3.2.0-23-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-23-generic-pae /boot/vmlinuz-3.2.0-23-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-23-generic-pae /boot/vmlinuz-3.2.0-23-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found linux image: /boot/vmlinuz-3.2.0-20-generic
Found initrd image: /boot/initrd.img-3.2.0-20-generic
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
done

```And my sources file:
```

# cat /etc/apt/sources.list.nk
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://by.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://by.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://by.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://by.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://by.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://by.archive.ubuntu.com/ubuntu/ precise universe
deb http://by.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://by.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://by.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://by.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://by.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://by.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://by.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://by.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
 deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```
```

# uname -a
Linux chul-book 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

Thanks in advance!

---

### Post by Irihapeti on 2012-04-27
Is the earlier kernel version still there? If so, you should be able to boot Ubuntu from it, either from the main listing or by going into the "older versions" option in grub. That should be just under the current kernel at the top of the listing.

Then you need to install linux-headers-3.2.0-23-generic-pae to match the new kernel.

---

### Post by chulik on 2012-04-27
> **Irihapeti said:**
> Is the earlier kernel version still there? If so, you should be able to boot Ubuntu from it, either from the main listing or by going into the "older versions" option in grub. That should be just under the current kernel at the top of the listing.

Then you need to install linux-headers-3.2.0-23-generic-pae to match the new kernel.


Sorry,
I'm stupid ). I've installed 64bit kernel. I don't need pae at all. But I see only 3.5 Gb in #free. I'll check video memory usage.

---

### Post by chulik on 2012-04-27
> **Irihapeti said:**
> Is the earlier kernel version still there? If so, you should be able to boot Ubuntu from it, either from the main listing or by going into the "older versions" option in grub. That should be just under the current kernel at the top of the listing.

Then you need to install linux-headers-3.2.0-23-generic-pae to match the new kernel.

Sorry, I'm stupid ). I've installed 64bit kernel and tried to use PAE ). I think 512 Mb used by hybrid video card (by internal part).

Thread may be closed.

---

### Post by mörgæs on 2012-04-27
> **chulik said:**
> 
Thread may be closed.

We prefer that you mark it 'solved' using 'thread tools'.

---

### Post by garvinrick4 on 2012-04-27
If anyone wants to use 386i pae kernel to use all you RAM available. Go to this link and download to
lets say Desktop the 3 you need: headers in pae, all.deb and linux image in pae.
Here is site below choose the kernel you wish and download
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

```
cd Desktop
```
```
sudo dpkg -i *.deb
```
```
sudo update-grub
```
```
sudo shutdown -r now
```

####Make sure you have no other .deb files on Desktop except 3 you need. 
The second line of code will install all .debs in that directory: Can do one at a time if choose:
example below use without quotes
```
sudo dpkg -i "name of .deb file" 
```

---

### Post by mcduck on 2012-04-27
> **Irihapeti said:**
> Is the earlier kernel version still there? If so, you should be able to boot Ubuntu from it, either from the main listing or by going into the "older versions" option in grub. That should be just under the current kernel at the top of the listing.

Then you need to install linux-headers-3.2.0-23-generic-pae to match the new kernel.

There's actually even better way; you shouldn't ever install a specific kernel version as that would mean you only get that exact version and no updates.

Instead you should always install the metapackage for the kernel you want to use, for example "linux-pae" would install the PAE kernel image and all other related packages, and make sure you also get updates for all of them.

---

### Post by Irihapeti on 2012-04-27
> **mcduck said:**
> There's actually even better way; you shouldn't ever install a specific kernel version as that would mean you only get that exact version and no updates.

Instead you should always install the metapackage for the kernel you want to use, for example "linux-pae" would install the PAE kernel image and all other related packages, and make sure you also get updates for all of them.

That's true - I thought of that afterwards but for some reason didn't come back to edit my reply.

Thanks for pointing it out.

---

