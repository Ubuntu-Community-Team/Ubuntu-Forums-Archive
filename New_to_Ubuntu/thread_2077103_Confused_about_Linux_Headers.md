---
title: "Confused about Linux Headers"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by Paul Childs on 2012-10-27
Hello,

I'm quite the noob when it comes to getting into the guts of Ubuntu.

I am ultimately trying to get VirtualBox to work...

From all the Googling I have done I have found the problem but have no idea how to fix it.

Apparently the kernel headers are missing from my system. The error that I get is
```
Error! Your kernel headers for kernel 3.0.0-17-generic cannot be found.
Please install the linux-headers-3.0.0-17-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located

```

I ran the following command to confirm the kernel that is running.

```
/etc/init.d$ uname -r
3.0.0-17-generic

```

That looked good.

I tried to install these headers...
```
/etc/init.d$ sudo apt-get install linux-headers-$(uname -r) gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.0.0-17-generic
E: Couldn't find any package by regex 'linux-headers-3.0.0-17-generic'
```

When I look in Synaptic package manager it is showing that I have 3.2 Linux headers up to 3.2.0-30. OK, this is confusing.

When I look at the Ubuntu Wiki is says that 12.04 has kernel 3.2.14. Hmmm.

So I am pretty confused about what to do.

Any help would be greatly appreciated.

/Paul

---

### Post by Doug S on 2012-10-27
> So I am pretty confused about what to do.O.K., well I am also pretty confused as to how to help you.
I don't see those particular header versions anywhere on the [Ubuntu Kernel PPA site]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")
It sound as though you think you are at 12.04, is that true?
I wonder (long shot) if you are somehow booting into an old kernel, even though you have newer ones. All I can think of is to ask from more information. First, show us the contents of /boot, Example:```
doug@s15:~/sguide-1204/sguide-footnote$ ls -l /boot
total 115838
-rw-r--r-- 1 root root   791281 Jul  6 08:06 abi-3.2.0-27-generic
-rw-r--r-- 1 root root   791281 Jul 27 10:44 abi-3.2.0-29-generic
-rw-r--r-- 1 root root   791446 Aug 24 10:33 abi-3.2.0-30-generic
-rw-r--r-- 1 root root   791446 Sep  7 09:57 abi-3.2.0-31-generic
-rw-r--r-- 1 root root   792532 Sep 26 15:14 abi-3.2.0-32-generic
-rw-r--r-- 1 root root   140454 Jul  6 08:06 config-3.2.0-27-generic
-rw-r--r-- 1 root root   140432 Jul 27 10:44 config-3.2.0-29-generic
-rw-r--r-- 1 root root   140432 Aug 24 10:33 config-3.2.0-30-generic
-rw-r--r-- 1 root root   140459 Sep  7 09:57 config-3.2.0-31-generic
-rw-r--r-- 1 root root   140488 Sep 26 15:14 config-3.2.0-32-generic
drwxr-xr-x 3 root root     5120 Oct 15 15:42 grub
-rw-r--r-- 1 root root 14768089 Jul 29 14:42 initrd.img-3.2.0-27-generic
-rw-r--r-- 1 root root 14768743 Sep 18 08:40 initrd.img-3.2.0-29-generic
-rw-r--r-- 1 root root 14767969 Sep 18 08:43 initrd.img-3.2.0-30-generic
-rw-r--r-- 1 root root 14775276 Oct  9 06:44 initrd.img-3.2.0-31-generic
-rw-r--r-- 1 root root 14775271 Oct 12 14:24 initrd.img-3.2.0-32-generic
drwxr-xr-x 2 root root    12288 Mar 14  2012 lost+found
-rw-r--r-- 1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw------- 1 root root  2882027 Jul  6 08:06 System.map-3.2.0-27-generic
-rw------- 1 root root  2882108 Jul 27 10:44 System.map-3.2.0-29-generic
-rw------- 1 root root  2883362 Aug 24 10:33 System.map-3.2.0-30-generic
-rw------- 1 root root  2883401 Sep  7 09:57 System.map-3.2.0-31-generic
-rw------- 1 root root  2884076 Sep 26 15:14 System.map-3.2.0-32-generic
-rw------- 1 root root  4960848 Jul  6 08:06 vmlinuz-3.2.0-27-generic
-rw------- 1 root root  4960752 Jul 27 10:44 vmlinuz-3.2.0-29-generic
-rw------- 1 root root  4963280 Aug 24 10:33 vmlinuz-3.2.0-30-generic
-rw------- 1 root root  4963792 Sep  7 09:57 vmlinuz-3.2.0-31-generic
-rw------- 1 root root  4966768 Sep 26 15:14 vmlinuz-3.2.0-32-generic
```Then show us all of the headers you do have, example:```
doug@s15:~/sguide-1204/sguide-footnote$ dpkg -l |grep header
ii  libdw-dev                                 0.152-1ubuntu3                             libdw1 development libraries and header files
ii  libelf-dev                                0.152-1ubuntu3                             libelf1 development libraries and header files
ii  linux-headers-3.2.0-27                    3.2.0-27.43                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-27-generic            3.2.0-27.43                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-29                    3.2.0-29.46                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-29-generic            3.2.0-29.46                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-30                    3.2.0-30.48                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-30-generic            3.2.0-30.48                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-31                    3.2.0-31.50                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic            3.2.0-31.50                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-32                    3.2.0-32.51                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic            3.2.0-32.51                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-server                      3.2.0.32.35                                Linux kernel headers on Server Equipment.
```And also the kernels, example:```
doug@s15:~/sguide-1204/sguide-footnote$ dpkg -l |grep linux-image
rc  linux-image-3.2.0-18-generic              3.2.0-18.29                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-19-generic              3.2.0-19.31                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-20-generic              3.2.0-20.33                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-21-generic              3.2.0-21.34                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-22-generic              3.2.0-22.35                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-23-generic              3.2.0-23.36                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-24-generic              3.2.0-24.39                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-26-generic              3.2.0-26.41                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-27-generic              3.2.0-27.43                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-29-generic              3.2.0-29.46                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-30-generic              3.2.0-30.48                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-31-generic              3.2.0-31.50                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-32-generic              3.2.0-32.51                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.22                        3.2.22-1                                   Linux kernel, version 3.2.22
rc  linux-image-3.2.22+                       3.2.22+-2                                  Linux kernel, version 3.2.22+
rc  linux-image-3.2.23                        3.2.23-1                                   Linux kernel, version 3.2.23
rc  linux-image-3.2.23+                       3.2.23+-4                                  Linux kernel, version 3.2.23+
rc  linux-image-3.5.0-030500rc1-generic       3.5.0-030500rc1.201206022335               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-030500rc2-generic       3.5.0-030500rc2.201206082235               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-030500rc5-generic       3.5.0-030500rc5.201206302035               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-030500rc6-generic       3.5.0-030500rc6.201207072135               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-030500rc7-generic       3.5.0-030500rc7.201207142035               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.6.1-030601-generic          3.6.1-030601.201210071322                  Linux kernel image for version 3.6.1 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-030500rc2-generic 3.5.0-030500rc2.201206082235               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-030500rc5-generic 3.5.0-030500rc5.201206302035               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-030500rc6-generic 3.5.0-030500rc6.201207072135               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-030500rc7-generic 3.5.0-030500rc7.201207142035               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.6.1-030601-generic    3.6.1-030601.201210071322                  Linux kernel image for version 3.6.1 on 64 bit x86 SMP
ii  linux-image-server                        3.2.0.32.35                                Linux kernel image on Server Equipment.

```Edit: Oh, and the disto, example:```
doug@s15:~/sguide-1204/sguide-footnote$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:   precise

```If it comes it it, we might ask for the contents of /etc/default/grub, but I 'm getting ahead a bit now.

---

### Post by Paul Childs on 2012-10-27
Hey Doug,

Yes I am running 12.04.

As requested...

```
ls -l /boot
abi-2.6.28-16-generic
abi-2.6.31-21-generic
abi-2.6.32-25-generic
abi-2.6.38-14-generic
abi-3.0.0-17-generic
abi-3.2.0-24-generic
abi-3.2.0-25-generic
abi-3.2.0-26-generic
abi-3.2.0-27-generic
abi-3.2.0-29-generic
abi-3.2.0-30-generic
abi-3.2.0-31-generic
abi-3.2.0-32-generic
config-2.6.28-16-generic
config-2.6.31-21-generic
config-2.6.32-25-generic
config-2.6.38-14-generic
config-3.0.0-17-generic
config-3.2.0-24-generic
config-3.2.0-25-generic
config-3.2.0-26-generic
config-3.2.0-27-generic
config-3.2.0-29-generic
config-3.2.0-30-generic
config-3.2.0-31-generic
config-3.2.0-32-generic
grub
initrd.img-2.6.28-16-generic
initrd.img-2.6.31-21-generic
initrd.img-2.6.32-25-generic
initrd.img-2.6.38-14-generic
initrd.img-3.0.0-17-generic
initrd.img-3.2.0-24-generic
initrd.img-3.2.0-25-generic
initrd.img-3.2.0-26-generic
initrd.img-3.2.0-27-generic
initrd.img-3.2.0-29-generic
initrd.img-3.2.0-30-generic
initrd.img-3.2.0-31-generic
initrd.img-3.2.0-32-generic
memtest86+.bin
memtest86+_multiboot.bin
System.map-2.6.28-16-generic
System.map-2.6.31-21-generic
System.map-2.6.32-25-generic
System.map-2.6.38-14-generic
System.map-3.0.0-17-generic
System.map-3.2.0-24-generic
System.map-3.2.0-25-generic
System.map-3.2.0-26-generic
System.map-3.2.0-27-generic
System.map-3.2.0-29-generic
System.map-3.2.0-30-generic
System.map-3.2.0-31-generic
System.map-3.2.0-32-generic
vmcoreinfo-2.6.28-16-generic
vmcoreinfo-2.6.31-21-generic
vmcoreinfo-2.6.32-25-generic
vmcoreinfo-2.6.38-14-generic
vmcoreinfo-3.0.0-17-generic
vmlinuz-2.6.28-16-generic
vmlinuz-2.6.31-21-generic
vmlinuz-2.6.32-25-generic
vmlinuz-2.6.38-14-generic
vmlinuz-3.0.0-17-generic
vmlinuz-3.2.0-24-generic
vmlinuz-3.2.0-25-generic
vmlinuz-3.2.0-26-generic
vmlinuz-3.2.0-27-generic
vmlinuz-3.2.0-29-generic
vmlinuz-3.2.0-30-generic
vmlinuz-3.2.0-31-generic
vmlinuz-3.2.0-32-generic
```

Headers...

```
dpkg -l |grep header
ii  libice-dev                           2:1.0.7-2build1
ii  libsm-dev                            2:1.2.0-2build1
ii  libssl-dev                           1.0.1-4ubuntu5.5
ii  libx11-dev                           2:1.4.99.1-0ubuntu2
ii  libxau-dev                           1:1.0.6-4     
ii  libxcomposite-dev                    1:0.4.3-2build1
ii  libxdamage-dev                       1:1.1.3-2build1
ii  libxdmcp-dev                         1:1.1.0-4   
ii  libxext-dev                          2:1.3.0-3build1
ii  libxfixes-dev                        1:5.0-4ubuntu4
ii  libxi-dev                            2:1.6.0-0ubuntu2
ii  libxinerama-dev                      2:1.1.1-3build1
ii  libxrandr-dev                        2:1.3.2-2
ii  linux-headers-3.2.0-24               3.2.0-24.39
ii  linux-headers-3.2.0-24-generic       3.2.0-24.39
ii  linux-headers-3.2.0-24-generic-pae   3.2.0-24.39
ii  linux-headers-3.2.0-25               3.2.0-25.40
ii  linux-headers-3.2.0-25-generic       3.2.0-25.40
ii  linux-headers-3.2.0-25-generic-pae   3.2.0-25.40
ii  linux-headers-3.2.0-26               3.2.0-26.41 
ii  linux-headers-3.2.0-26-generic       3.2.0-26.41
ii  linux-headers-3.2.0-26-generic-pae   3.2.0-26.41
ii  linux-headers-3.2.0-27               3.2.0-27.43
ii  linux-headers-3.2.0-27-generic       3.2.0-27.43
ii  linux-headers-3.2.0-27-generic-pae   3.2.0-27.43
ii  linux-headers-3.2.0-29               3.2.0-29.46
ii  linux-headers-3.2.0-29-generic       3.2.0-29.46
ii  linux-headers-3.2.0-29-generic-pae   3.2.0-29.46
ii  linux-headers-3.2.0-30               3.2.0-30.48
ii  linux-headers-3.2.0-30-generic       3.2.0-30.48
ii  linux-headers-3.2.0-30-generic-pae   3.2.0-30.48
ii  linux-headers-3.2.0-31               3.2.0-31.50
ii  linux-headers-3.2.0-31-generic       3.2.0-31.50
ii  linux-headers-3.2.0-31-generic-pae   3.2.0-31.50
ii  linux-headers-3.2.0-32               3.2.0-32.51 
ii  linux-headers-3.2.0-32-generic       3.2.0-32.51
ii  linux-headers-3.2.0-32-generic-pae   3.2.0-32.51
ii  linux-headers-generic                3.2.0.32.35
ii  linux-headers-generic-pae            3.2.0.32.35
ii  python-dev                           2.7.3-0ubuntu2
ii  x11proto-core-dev                    7.0.22-1
```

Kernels...

```
rc  linux-image-2.6.28-11-generic    2.6.28-11.42
rc  linux-image-2.6.28-13-generic    2.6.28-13.45
rc  linux-image-2.6.28-14-generic    2.6.28-14.47
rc  linux-image-2.6.28-15-generic    2.6.28-15.52
ii  linux-image-2.6.28-16-generic    2.6.28-16.55
rc  linux-image-2.6.31-14-generic    2.6.31-14.48
rc  linux-image-2.6.31-15-generic    2.6.31-15.50
rc  linux-image-2.6.31-16-generic    2.6.31-16.53
rc  linux-image-2.6.31-17-generic    2.6.31-17.54
rc  linux-image-2.6.31-19-generic    2.6.31-19.56
rc  linux-image-2.6.31-20-generic    2.6.31-20.58
ii  linux-image-2.6.31-21-generic    2.6.31-21.59
rc  linux-image-2.6.32-22-generic    2.6.32-22.36
rc  linux-image-2.6.32-23-generic    2.6.32-23.37
rc  linux-image-2.6.32-24-generic    2.6.32-24.43
ii  linux-image-2.6.32-25-generic    2.6.32-25.45
rc  linux-image-2.6.35-22-generic    2.6.35-22.35
rc  linux-image-2.6.35-23-generic    2.6.35-23.41
rc  linux-image-2.6.35-24-generic    2.6.35-24.42
rc  linux-image-2.6.35-25-generic    2.6.35-25.44
rc  linux-image-2.6.35-27-generic    2.6.35-27.48
rc  linux-image-2.6.35-28-generic    2.6.35-28.50
rc  linux-image-2.6.35-30-generic    2.6.35-30.61
rc  linux-image-2.6.35-31-generic    2.6.35-31.63
rc  linux-image-2.6.35-32-generic    2.6.35-32.67
ii  linux-image-2.6.38-14-generic    2.6.38-14.58
ii  linux-image-3.0.0-17-generic     3.0.0-17.30 
ii  linux-image-3.2.0-24-generic     3.2.0-24.39 
ii  linux-image-3.2.0-25-generic     3.2.0-25.40 
ii  linux-image-3.2.0-26-generic     3.2.0-26.41 
ii  linux-image-3.2.0-27-generic     3.2.0-27.43 
ii  linux-image-3.2.0-29-generic     3.2.0-29.46 
ii  linux-image-3.2.0-30-generic     3.2.0-30.48 
ii  linux-image-3.2.0-31-generic     3.2.0-31.50 
ii  linux-image-3.2.0-32-generic     3.2.0-32.51 
ii  linux-image-generic              3.2.0.32.35 

```

Distro...

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

```

Many thanks,
/Paul

---

### Post by Doug S on 2012-10-28
For whatever reason, it seems that your computer is not loading the current kernel during boot. Have a look at your /etc/default/grub file. Look for this line:```
GRUB_DEFAULT=0
```which in your case, I suspect is not set to zero.
Note that I also like to increase the timeout, in case I want to manaully select another kernel:```
GRUB_TIMEOUT=10
```Before you make changes, save the current file, as say grub.bak. You will need sudo to edit the file. After editing you need run:```
sudo update-grub
```if you have troubles, post your /etc/default/grub file here.

---

### Post by Paul Childs on 2012-10-28
Thanks for the direction Doug.

BTW I heard BC got hit with a 7.7 earthquake. I hope everything is OK. I'm still having issues with this problem and will certainly understand if you drop it due to that terrible disaster.

I looked for the grub file where you had suggested and it was not there...

```
ls -l /etc/default
total 168
-rw-r--r-- 1 root root  346 Apr 29  2010 acpid
-rw-r--r-- 1 root root 4922 Apr 23  2010 acpi-support
-rw-r--r-- 1 root root  638 Apr 29 21:31 alsa
-rw-r--r-- 1 root root  216 Feb 26  2009 apmd
-rw-r--r-- 1 root root  149 Apr 27  2012 apport
-rw-r--r-- 1 root root  219 Mar 23  2009 avahi-daemon
-rw-r--r-- 1 root root   47 Mar 31  2009 bootlogd
-rw-r--r-- 1 root root  608 Feb 16  2010 brltty
-rw------- 1 root root  384 Apr 11  2010 cacerts
-rw-r--r-- 1 root root 4331 Apr 29 21:49 console-setup
-rw-r--r-- 1 root root  549 Jan 24  2012 crda
-rw-r--r-- 1 root root  183 Jun 19 17:26 cron
-rw-r--r-- 1 root root  652 May 23  2011 cryptdisks
-rw-r--r-- 1 root root  122 Apr 17  2009 cups
-rw-r--r-- 1 root root  297 Jan 27  2009 dbus
-rw------- 1 root root  531 Mar 23  2010 ddclient
-rw-r--r-- 1 root root   92 Mar 31  2009 devpts
-rw-r--r-- 1 root root   58 Jun  1  2010 google-chrome
-rw-r--r-- 1 root root   58 Nov 12  2011 google-talkplugin
-rw-r--r-- 1 root root  220 Apr 29 21:46 gpsd
-rw-r--r-- 1 root root   86 Mar 31  2009 halt
-rw-r--r-- 1 root root  126 Apr 29 21:45 irqbalance
-rw-r--r-- 1 root root   69 Apr  8  2009 kernel-helper-rc
-rwxr-xr-x 1 root root   84 Nov  2  2009 kerneloops
-rw-r--r-- 1 root root  626 Apr 29 21:29 keyboard
-rw-r--r-- 1 root root  313 Jan 23  2009 klogd
-rw-r--r-- 1 root root   19 Jun 20  2009 locale
-rw-r--r-- 1 root root 1756 Mar  6  2012 nss
-rw-r--r-- 1 root root   48 Oct  6 23:38 ntfs-3g
-rw-r--r-- 1 root root  456 Mar 20  2009 ntpdate
-rw-r--r-- 1 root root 1166 Oct 27  2011 pulseaudio
-rw-r--r-- 1 root root  261 Apr 28  2012 rcS
-rw-r--r-- 1 root root 1768 Mar 30  2010 rsync
-rw-r--r-- 1 root root  321 Jun 17  2011 rsyslog
-rw-r--r-- 1 root root  146 Apr 29 21:50 saned
-rw-r--r-- 1 root root  132 Jun 21  2010 speech-dispatcher
-rw-r--r-- 1 root root  186 Jan 23  2009 syslogd
-rw-r--r-- 1 root root 2072 Apr  5  2012 ufw
-rw-r--r-- 1 root root 1118 Apr  4  2009 useradd
-rw-r--r-- 1 root root   31 Apr 18  2012 whoopsie
```

I executed a find:

```
find / -name 'grub'
/lib/recovery-mode/options/grub
/usr/sbin/grub
/usr/lib/grub
/usr/share/bug/grub
/usr/share/grub
/usr/share/doc/grub
/boot/grub
/etc/bash_completion.d/grub
```

I checked all the "grub" out and they were either an executable file or a directory.

I looked at the /boot/grub directory, which seemed to be the most promising for investigation and was unsure of what was in there.

Thanks,
/Paul

---

### Post by Doug S on 2012-10-28
Well, the mystery continues...
 
Earthquake: Thanks for your concern. Myself, I didn't even notice, but some around here did. It is my understanding that even in Haide Gwaii (A.K.A. Queen Charlotte Islands) area, damage was minimal.
 
Yes, /boot/grub should have a file named grub.cfg, which should be a file generated from /etc/default/grub when you run:```
sudo update-grub
```So, what is going on in your case? What do you get for this:```
doug@s15:~$ dpkg -l | grep grub
ii  grub-common                               1.99-21ubuntu3.4                           GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists                     0.6                                        GRUB gfxpayload blacklist
ii  grub-pc                                   1.99-21ubuntu3.4                           GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                               1.99-21ubuntu3.4                           GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                              1.99-21ubuntu3.4                           GRand Unified Bootloader (common files for version 2)
```Is your computer dual boot with some other Operating system? I.E. maybe grub is not your main boot loader thing (which I know nothing about, because I always use grub).

---

### Post by Paul Childs on 2012-10-28
Glad to hear that you guys are OK.

Running the two commands you suggested...

```
paul@paul-laptop:~$ sudo update-grub
[sudo] password for paul: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.2.0-32-generic
Found kernel: /boot/vmlinuz-3.2.0-31-generic
Found kernel: /boot/vmlinuz-3.2.0-30-generic
Found kernel: /boot/vmlinuz-3.2.0-29-generic
Found kernel: /boot/vmlinuz-3.2.0-27-generic
Found kernel: /boot/vmlinuz-3.2.0-26-generic
Found kernel: /boot/vmlinuz-3.2.0-25-generic
Found kernel: /boot/vmlinuz-3.2.0-24-generic
Found kernel: /boot/vmlinuz-3.0.0-17-generic
Found kernel: /boot/vmlinuz-2.6.38-14-generic
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/vmlinuz-2.6.31-21-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

paul@paul-laptop:~$ dpkg -l | grep grub
ii  grub                                          0.97-29ubuntu66                            GRand Unified Bootloader (Legacy version)
ii  grub-common                                   1.99-21ubuntu3.4                           GRand Unified Bootloader (common files)


```

It looked like the update was the fix but I restarted my machine.
I don't dual boot. 
It looks like grub is booting the machine.
I still get the 3.0.0-17-generic when I run *uname -r*.

Mystery still continues...

/Paul

---

### Post by Doug S on 2012-10-28
Hi Paul,
 
O.K. I think I might have an idea what is going on. Your computer is using the old menu.lst method for generating the new grub.cfg file.
I am not familiar with the menu.lst file syntax but if you list here maybe we can figure out a suggested change. I am also not familiar with procedures to possibly update your method, yet maintain any special settings, from the menu.lst method to the /etc/default/grub method.

---

### Post by JKyleOKC on 2012-10-28
Post the content of /boot/grub/menu.lst and we can quickly tell you how to fix this. However I'm a bit concerned about your grub and grub-common packages, as listed a couple of messages back. It shows grub at version 0.97 and grub-common as 1.99; the differences between those versions are extreme since grub underwent a total rewrite a couple of years ago. 

I don't think there's a conflict, though; if there were I doubt that your system would boot at all. I suspect that the grub-common is from a more recent update, while your grub is left over from sometime around 8.04 or even before...

Doug, the menu.lst syntax will be obvious to you since you're familiar with grub.cfg. It just used direct text editing to do what /etc/default/grub does in the newer versions.

---

### Post by Paul Childs on 2012-10-28
Hello gentlemen,

Here is the content of my grub menu.lst

```
paul@paul-laptop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c01fb380-878f-40f4-8757-ecd932c2dc9b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c01fb380-878f-40f4-8757-ecd932c2dc9b

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 11.10, kernel 3.0.0-17-generic
uuid		c01fb380-878f-40f4-8757-ecd932c2dc9b
kernel		/boot/vmlinuz-3.0.0-17-generic root=UUID=c01fb380-878f-40f4-8757-ecd932c2dc9b ro quiet splash 
initrd		/boot/initrd.img-3.0.0-17-generic
quiet

title		Ubuntu 11.10, kernel 3.0.0-17-generic (recovery mode)
uuid		c01fb380-878f-40f4-8757-ecd932c2dc9b
kernel		/boot/vmlinuz-3.0.0-17-generic root=UUID=c01fb380-878f-40f4-8757-ecd932c2dc9b ro  single
initrd		/boot/initrd.img-3.0.0-17-generic

title		Ubuntu 11.10, kernel 2.6.38-14-generic
uuid		c01fb380-878f-40f4-8757-ecd932c2dc9b
kernel		/boot/vmlinuz-2.6.38-14-generic root=UUID=c01fb380-878f-40f4-8757-ecd932c2dc9b ro quiet splash 
initrd		/boot/initrd.img-2.6.38-14-generic
quiet

title		Ubuntu 11.10, kernel 2.6.38-14-generic (recovery mode)
uuid		c01fb380-878f-40f4-8757-ecd932c2dc9b
kernel		/boot/vmlinuz-2.6.38-14-generic root=UUID=c01fb380-878f-40f4-8757-ecd932c2dc9b ro  single
initrd		/boot/initrd.img-2.6.38-14-generic

title		Ubuntu 11.10, kernel 2.6.32-25-generic
uuid		c01fb380-878f-40f4-8757-ecd932c2dc9b
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=c01fb380-878f-40f4-8757-ecd932c2dc9b ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-25-generic (recovery mode)
uuid		c01fb380-878f-40f4-8757-ecd932c2dc9b
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=c01fb380-878f-40f4-8757-ecd932c2dc9b ro  single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 11.10, kernel 2.6.31-21-generic
uuid		c01fb380-878f-40f4-8757-ecd932c2dc9b
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=c01fb380-878f-40f4-8757-ecd932c2dc9b ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 11.10, kernel 2.6.31-21-generic (recovery mode)
uuid		c01fb380-878f-40f4-8757-ecd932c2dc9b
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=c01fb380-878f-40f4-8757-ecd932c2dc9b ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 11.10, kernel 2.6.28-16-generic
uuid		c01fb380-878f-40f4-8757-ecd932c2dc9b
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c01fb380-878f-40f4-8757-ecd932c2dc9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 11.10, kernel 2.6.28-16-generic (recovery mode)
uuid		c01fb380-878f-40f4-8757-ecd932c2dc9b
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c01fb380-878f-40f4-8757-ecd932c2dc9b ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 11.10, memtest86+
uuid		c01fb380-878f-40f4-8757-ecd932c2dc9b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Cheers,
/Paul

---

### Post by JKyleOKC on 2012-10-28
The most interesting thing I see in your menu.lst file is that it doesn't mention ANY version newer than 11.10. I suspect that your upgrade to 12.04.1 didn't do all that it was supposed to do, and left you with a system that's betwixt and between 11.10 and 12.04.

Your previous list of the report from update-grub clearly shows that it was processing 12.04.1, but then says it applied its findings to update the menu.lst file -- and your listing of that file doesn't show any of the eight 3.2 kernel entries resulting from subsequent updates. What this implies to me is that the updating of menu.lst simply didn't happen despite the report that it did.

Were it my system, I'd be inclined to purge the current grub packages and re-install grub from the Live CD, taking care to install the latest (grub2) version rather than "legacy grub." This would bring that part of the system up to date and make it easier for the rest of us to advise you, since only a few of us old-timers remember enough about "legacy grub" to spot problems. I resisted the change to grub longer than most, but eventually gave up and made the switch when I replaced 8.04 with 10.04 as a clean install. Now it has changed again so a clean install of 12.04 is still different. I have 12.04 on another box and continually run into these differences.

However, Doug has been helping you the most, and I certainly don't want to butt into his advice. I jumped in only because I do remember parts of the legacy grub system and felt I could probably help.

The lines that follow the default options, grouped together with the first word of each group being "title" are the legacy version of the "menuentry" areas of grub.cfg. Each group is called a "stanza" in grub-speak. Each stanza provides a single line of the displayed menu, together with the data and commands that implement that choice.

If your menu.lst file had stanzas for the eight 3.2 kernels shown in the update-grub report, all you would need to do is change the "default=0" line near the top of the file to refer to the one you wanted to boot automatically. The "0"th stanza is the first one, and as you can see from the update-grub report, they are sorted with the newest one first, so "0" is usually what you want. Since it does not, though, the entire update process seems suspect.

You could manually edit an appropriate stanza into the file, but Murphy's Law would probably strike and leave you with an unbootable system. That's why I would nuke and rebuild.

What's your opinion, Doug?

---

### Post by Doug S on 2012-10-29
@Jim: I very much appreciate your chiming in to help. I have been busy and away from my computer for many hours, and now it is late in my time zone. I agree things seem somewhat messed up. I had written Paul a respone earlier suggesting to try a default /etc/default/grub file and to rename /boot/grub/menu.lst to something else, but then I deleted it, as I (also) was worried the suggestion might lead to an unbootable system. Anyway, I'll have to come back to this tomorrow.

---

### Post by NikTh on 2012-10-29
I will suggest something that **[COLOR=Red]maybe destroy your system[/COLOR] and leave it in unbootable state**.

_Drastic measures _

If I were you . 

Boot from the Ubuntu 12.04 (can you boot ? ) 

To ensure this , open a terminal and run these commands 
```
lsb_release -rcd 
uname -r
```The results must be ```
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
3.2.0-32-generic
```Proceed with the **complete remove - purge of grub** and re-installation. 

```
apt-get remove --purge grub*
rm /boot/grub/menu.lst
```Above commands need sudo prefix. 

**Install grub 1.99**
```
sudo apt-get install grub-common grub-pc
```

**Install grub to /dev/sda** (disk you boot from)
```
sudo grub-install /dev/sda
```

**Generate a grub.cfg**
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```If something goes wrong and you cannot boot  , then is good to have a LiveCD-USB of Ubuntu and boot from there you can use [boot-repair]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") 2nd option. 

Thanks (good luck)

---

### Post by JKyleOKC on 2012-10-29
That's a well-detailed version of what I called "nuke and rebuild" and while it might make the system temporarily unbootable if something went wrong midway through the process, a Live CD should be able to recover from such an event.

For a good description of the differences between GRUB versions, see this link: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Paul, the diagnostics you ran earlier do show definitely that you are booting into 12.04.1, but that it's still using the older 3.0.0 kernel from 10.04. You should be perfectly safe going through the steps NikTh lists; we're just all terribly aware of Murphy's Law and the remote possibility that something could go wrong.

NikTh, thanks for jumping in with the step-by-step details.

EDIT: Something just occurred to me. Sometimes when I'm installing updates, I'll get a dialog that asks whether to keep an existing configuration or overwrite it with the maintainer's version. That's a difficult decision to make, especially if I don't know any more details. You might have gotten such a question when upgrading to 12.04, and your response might have resulted in keeping the legacy grub version instead of replacing it. Just a guess, but a possible explanation of what happened. In any event, your current grub-update utility is obviously NOT doing what it's supposed to do...

---

### Post by Doug S on 2012-10-29
@Jim, very well said.
@NikTh, yes thanks for the detail.
@Paul, I think you see a consensus as to how to proceed, but with worry about the potential downside risk. Please let use know how you make out.

---

### Post by JKyleOKC on 2012-10-29
Farther down that grub2 wiki entry, I see a recommendation to use "Boot Repair" to replace a legacy grub installation with the latest version. That would be the simplest way of all to fix things!

I've used the Boot Repair program to correct a situation in which my 12.04 installation was totally unbootable due to other problems, and it worked perfectly. Its author, YannBuntu, is active here on the forums and responds immediately to requests for help.

So I'm changing my recommendation to "Download the Boot Repair package from the repositories and use it to update your grub installation." Things are much less likely to go sour unexpectedly, since the critical commands are all in the boot repair script.

---

### Post by Paul Childs on 2012-10-29
Thanks to everyone! 

What an awesome community! I have learned quite a bit going through this.

I'm not too worried about things going wrong. I will back up my data and try the boot repair that Jim suggested. We'll see how it goes.

Worst case is, hopefully, I will have to install from scratch with the CD.

I'll post how things go. 

FYI, I am pretty busy this week so I probably won't get to this until Thursday at the earliest.

Cheers,
/Paul

---

### Post by JKyleOKC on 2012-10-30
Well, I tried following my own advice to use boot-repair, on a system that was originally 8.04, upgraded on-line to 10.04, and then ungraded again to 12.04 -- and the necessary tab in the boot-repair options dialog was grayed out! I contacted Yann but since boot still works with legacy grub he said he was unable to help. You may have to do it the more detailed way that NikTh laid out...

---

### Post by Paul Childs on 2012-10-30
Thanks for the heads-up Jim.
Cheers,
/Paul

---

### Post by JKyleOKC on 2012-10-30
Still another update. I opened Synaptic from the applications menu's System category, typed "grub2" without the quotes into the search box, and selected it for installation. The program told me several other packages were required; I told it to mark them too. This was WITHOUT going through all the purging that NikTh suggested -- but Synaptic automatically set it up. I then clicked the "Apply" icon at top center of the Synaptic window, and the system chugged away. It asked me where I wanted the boot data placed and I selected /dev/sda from the list it offered, clicked forward, and it continued. When I rebooted after it finished, I had a Grub2 menu in place of the old legacy grub one, and the /etc/default/grub file in place with default settings.

This is almost as simple as I expected boot-repair to be!

Good luck Thursday...

---

### Post by Paul Childs on 2012-10-31
Hi Jim,

I will definitely give that a try.

If it doesn't work I think that I will download 12.10, back up my data and install from scratch.

Cheers,
/Paul

---

### Post by Paul Childs on 2012-10-31
Hello gentlemen,

Success. I was waiting around for trick-or-treaters, so decided to use Synaptic, as suggested by Jim. I rebooted and ran the following.

```
paul@paul-laptop:~$ uname -r
3.2.0-32-generic

```

Thank you everyone for your help!

---

### Post by JKyleOKC on 2012-10-31
Glad it worked for you also!

Now back to your original problem of compiling the drivers for VirtualBox. Have you already installed the build-essential package? If not, you may need it to be able to compile those drivers. You also need the "dkms" package to create the new drivers automatically any time you get a kernel update, but I think that one is now installed by default.

I'm fighting a problem myself now, with a 64-bit 12.04.1 system when attempting to install the Linux Guest Additions in VirtualBox; it goes part-way through the installation, then aborts because it's unable to find a file named "autoconf.h" although that file definitely exists on the system in question. I'm sure it's just not looking in the right place but have not yet figured out how to show it what to do...

---

### Post by Paul Childs on 2012-11-01
Hi Jim,

I was able to get to VirtualBox later on last night. I just started it up it worked just fine.

Before I had posted to this forum, I had tried a variety of ways of installing it but the one that seemed to cause the least amount of grief was going to their web site, downloading their deb package and installing it according to their instructions. 

Once my kernel problem was fixed everything went smoothly. 

My system is 32 bit. It's my perception that 32 bit systems cause the least amount of problems. Not sure why.

I am in the process of installing Arch in the VM. I want to install a system from scratch to learn more. So far I have partitioned and installed a file system. So I haven't gotten very far. It will probably take a while to get through the process.

If there is something I can do to help out let me know. I'll give it my best shot.

Thanks.
/Paul

---

### Post by JKyleOKC on 2012-11-01
I'm just experimenting, in some VMs, to learn more myself. I think the problem here might be that on this box I'm using vbox 3.2.12 which is really old. I've not found any significant difference in reliability between 32 and 64 bit versions; in fact I have a 64-bit 12.04.1 host system on another box, running 4.1.22 vbox, that's doing great, and almost a dozen VMs on this box which runs Xubuntu 10.04.4 and vbox 3.2.12...

I agree that downloading vbox from the Oracle site is the best way to go; I've set up their PPA on both boxes here that handle virtualization.

Good luck with ARCH; I went through that initial learning process using Mandrake on a very old Pentium 2 machine -- and it IS fun but also frustrating at times.

---

