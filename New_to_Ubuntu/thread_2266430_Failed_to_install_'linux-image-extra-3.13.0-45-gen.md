---
title: "Failed to install 'linux-image-extra-3.13.0-45-generic'"
date: 2015-02-22
forum: New to Ubuntu
---

### Post by enigmasentinel on 2015-02-22
Hello, 
I am currently using **Ubuntu 12.04** **(32-bit) **and am trying to install 'linux-image-extra-3.13.0-45-generic'. I started off by running Update Manager (installed other updates but it failed to install that specific one). If I try to install it through Update Manager, it gives me (after expanding details)
```

The following packages have unmet dependences:

linux-image-generic-lts-trusty: Depends: linux-image-3.13.0-45-generic but it is not installed
```
If I use "apt-get install -f" in Terminal as it suggests, I receive the following
```

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied) 
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

After running:
sudo apt-get update (works fine)
sudo apt-get upgrade (see below)
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-45-generic but it is not installed
E: Unmet dependencies. Try using -f.
```
sudo apt-get -f upgrade (see below)
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  linux-image-3.13.0-45-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/52.5 MB of archives.
After this operation, 148 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 169700 files and directories currently installed.)
Unpacking linux-image-3.13.0-45-generic (from .../linux-image-3.13.0-45-generic_3.13.0-45.74~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-45-generic_3.13.0-45.74~precise1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-45-generic_3.13.0-45.74~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Within another 30 seconds or so, a window pops up from Ubuntu Software Center saying that the "Package operation failed". Opening the details of it shows the following
```

installArchives() failed: (Reading database ... 
(Reading database ... 5% 
(Reading database ... 10% 
(Reading database ... 15% 
(Reading database ... 20% 
(Reading database ... 25%
(Reading database ... 30% 
(Reading database ... 35% 
(Reading database ... 40% 
(Reading database ... 45% 
(Reading database ... 50% 
(Reading database ... 55% 
(Reading database ... 60% 
(Reading database ... 65% 
(Reading database ... 70% 
(Reading database ... 75% 
(Reading database ... 80% 
(Reading database ... 85% 
(Reading database ... 90% 
(Reading database ... 95% 
(Reading database ... 100% 
(Reading database ... 169700 files and directories currently installed.) 
Unpacking linux-image-3.13.0-45-generic (from .../linux-image-3.13.0-45-generic_3.13.0-45.74~precise1_i386.deb) ... 
This kernel does not support a non-PAE CPU. 
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-45-generic_3.13.0-45.74~precise1_i386.deb (--unpack): subprocess new pre-installation script returned error exit status 1 
No apport report written because MaxReports is reached already 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
Errors were encountered while processing: 
  /var/cache/apt/archives/linux-image-3.13.0-45-generic_3.13.0-45.74~precise1_i386.deb 
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
dpkg: dependency problems prevent configuration of linux-image-generic-lts-trusty: 
 linux-image-generic-lts-trusty depends on linux-image-3.13.0-45-generic; however: 
  Package linux-image-3.13.0-45-generic is not installed. 
dpkg: error processing linux-image-generic-lts-trusty (--configure): 
  dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic-lts-trusty: 
 linux-generic-lts-trusty depends on linux-image-generic-lts-trusty; however: 
  Package linux-image-generic-lts-trusty is not configured yet. 
dpkg: error processing linux-generic-lts-trusty (--configure): 
  dependency problems - leaving unconfigured
```
I also try to install another program (Adobe Flash) using the command: sudo apt-get install flashplugin-installer (to see if another program would install without needing to install 'linux-image-extra-3.13.0-45-generic') but gives me the following
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 flashplugin-installer : Depends: libnss3-1d but it is not going to be installed
                         Depends: libnspr4-0d but it is not going to be installed
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-45-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

My apologies that this post is so lengthy.

---

### Post by TheFu on 2015-02-22
If the installation uses LVM or encryption, the /boot partition may be out of space.
```
df -h
df -i
```
will check for that issue.
I'm not saying this is the issue, just something easy to check.

---

### Post by enigmasentinel on 2015-02-24
Unfortunately, the hard drive still has space for installing the package, so space is not an issue.

---

### Post by plucky on 2015-02-25
> If I use "apt-get install -f" in Terminal as it suggests, I receive the following
Code:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied) 
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?



You need to use sudo in front of that command.

Post output for ```
sudo apt-get install -f
```

> This kernel does not support a non-PAE CPU.

This might be relevant, please post output for ```
cat /proc/cpuinfo
```

Good Luck

---

### Post by enigmasentinel on 2015-02-25
After doing **sudo apt-get install -f**:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-45-generic
Suggested packages:
  fdutils linux-lts-trusty-doc-3.13.0 linux-lts-trusty-source-3.13.0
  linux-lts-trusty-tools
The following NEW packages will be installed:
  linux-image-3.13.0-45-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/52.5 MB of archives.
After this operation, 148 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 169700 files and directories currently installed.)
Unpacking linux-image-3.13.0-45-generic (from .../linux-image-3.13.0-45-generic_3.13.0-45.74~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-45-generic_3.13.0-45.74~precise1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-45-generic_3.13.0-45.74~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

After doing **cat /proc/cpuinfo**:
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 9
model name	: Intel(R) Pentium(R) M processor 1600MHz
stepping	: 5
microcode	: 0x7
cpu MHz		: 600.000
cache size	: 1024 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 tm pbe bts est tm2
bogomips	: 1198.95
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 32 bits virtual
power management:
```

---

### Post by v3.xx on 2015-02-25
Force PAE?

[http://ubuntuforums.org/showthread.php?t=2211590](http://ubuntuforums.org/showthread.php?t=2211590)

---

### Post by enigmasentinel on 2015-03-08
Would I put -forcepae=1 in Terminal when trying to install software?

---

### Post by plucky on 2015-03-09
> **enigmasentinel said:**
> Would I put -forcepae=1 in Terminal when trying to install software?

You need to put the **forcepae** into the boot options for grub.

```
sudo nano /etc/default/grub
``` and add ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash forcepae"
``` into this line then run ```
sudo update-grub
```
Then your system should always have the pae flag set after every re-boot.

Good Luck

---

