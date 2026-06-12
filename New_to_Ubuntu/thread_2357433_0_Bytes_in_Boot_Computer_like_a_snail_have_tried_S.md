---
title: "0 Bytes in Boot Computer like a snail have tried SOLVED solutions and no luck!"
date: 2017-04-02
forum: New to Ubuntu
---

### Post by 10speeduk on 2017-04-02
Hi all, I'm not computer savvy but have the 0bytes in partition "Boot" warning.  Have looked at similar solved threads but have not had success.  Open to any suggestions!  Thanks Paul

```
reidpa@reidpa-ThinkPad-T410:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         1.9G     0  1.9G   0% /dev
tmpfs                        375M  6.2M  369M   2% /run
/dev/mapper/ubuntu--vg-root  143G   28G  108G  21% /
tmpfs                        1.9G  1.5M  1.9G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1                    472M  464M     0 100% /boot
```

```
reidpa@reidpa-ThinkPad-T410:~$ dpkg -l | grep linux-image-
rc  linux-image-4.4.0-31-generic                4.4.0-31.50                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic                4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic                4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-43-generic                4.4.0-43.63                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-45-generic                4.4.0-45.66                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-51-generic                4.4.0-51.72                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-53-generic                4.4.0-53.74                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-57-generic                4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-59-generic                4.4.0-59.80                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic                4.4.0-62.83                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-63-generic                4.4.0-63.84                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-64-generic                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-66-generic                4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-70-generic                4.4.0-70.91                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic          4.4.0-31.50                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic          4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-generic          4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-43-generic          4.4.0-43.63                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-generic          4.4.0-45.66                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic          4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-51-generic          4.4.0-51.72                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-53-generic          4.4.0-53.74                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic          4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-59-generic          4.4.0-59.80                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic          4.4.0-62.83                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-63-generic          4.4.0-63.84                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-64-generic          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-66-generic          4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-70-generic          4.4.0-70.91                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-71-generic          4.4.0-71.92                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                         4.4.0.71.77                                   amd64        Generic Linux kernel image
```

---

### Post by yancek on 2017-04-02
Take a look at the Ubunt page regarding removing kernels at the link below.  You have a separate boot partition and a nice collection of kernels so the boot partition is full.  Which Ubuntu release are you using?  I believe the newest versions will do this automatically, at least I read that somewhere.  Bookmark the link below and keep an eye on the size of the boot partition.

 [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

---

### Post by 10speeduk on 2017-04-02
Thanks Yancek, I read the article and tried the first two suggestions:

```
reidpa@reidpa-ThinkPad-T410:~$ sudo apt-get autoremove --purge
[sudo] password for reidpa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-image-extra-4.4.0-71-generic : Depends: linux-image-4.4.0-71-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-71-generic but it is not installed
E: Unmet dependencies. Try using -f.
reidpa@reidpa-ThinkPad-T410:~$ sudo purge-old-kernels
sudo: purge-old-kernels: command not found
reidpa@reidpa-ThinkPad-T410:~$ ^C
reidpa@reidpa-ThinkPad-T410:~$ 
```

```
reidpa@reidpa-ThinkPad-T410:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
reidpa@reidpa-ThinkPad-T410:~$ 
```

Tried cleaning unmet dependencies:

```
reidpa@reidpa-ThinkPad-T410:~$ sudo apt-get clean linux-image-extra-4.4.0-71-generic
```

nothing happens....!

I am running Ubuntu 16.4

Thanks

Paul

so the unmet dependency is with  linux-image-4.4.0-71-generic but it is not installed.  I have attempted to reinstall it and get this:

```
reidpa@reidpa-ThinkPad-T410:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-image-extra-4.4.0-71-generic : Depends: linux-image-4.4.0-71-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-71-generic but it is not installed
E: Unmet dependencies. Try using -f.
reidpa@reidpa-ThinkPad-T410:~$ sudo apt-get update linux-image-4.4.0-71-generic
E: The update command takes no arguments
reidpa@reidpa-ThinkPad-T410:~$ sudo apt-get install --reinstall linux-image-4.4.0-71-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-47 linux-headers-4.4.0-47-generic linux-headers-4.4.0-51
  linux-headers-4.4.0-51-generic linux-headers-4.4.0-53
  linux-headers-4.4.0-53-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-image-4.4.0-47-generic
  linux-image-4.4.0-51-generic linux-image-4.4.0-53-generic
  linux-image-4.4.0-57-generic linux-image-4.4.0-59-generic
  linux-image-4.4.0-62-generic linux-image-4.4.0-63-generic
  linux-image-4.4.0-64-generic linux-image-extra-4.4.0-47-generic
  linux-image-extra-4.4.0-51-generic linux-image-extra-4.4.0-53-generic
  linux-image-extra-4.4.0-57-generic linux-image-extra-4.4.0-59-generic
  linux-image-extra-4.4.0-62-generic linux-image-extra-4.4.0-63-generic
  linux-image-extra-4.4.0-64-generic ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed
  linux-image-4.4.0-71-generic
0 to upgrade, 1 to newly install, 0 to remove and 144 not to upgrade.
7 not fully installed or removed.
Need to get 0 B/21.8 MB of archives.
After this operation, 66.4 MB of additional disk space will be used.
(Reading database ... 515471 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
Done.
Unpacking linux-image-4.4.0-71-generic (4.4.0-71.92) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-71-generic' to '/boot/vmlinuz-4.4.0-71-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
reidpa@reidpa-ThinkPad-T410:~$ 
```

What now...?!  Any suggestions please?

So the system won't delete old kernals due to a dependancy on linux-image4.4.0-71-generic which isn't installed, I cannot install it as their is not enough space in Boot.  What can I do? Would it be simpler to resize the boot partition?  Thanks Paul

---

### Post by Bashing-om on 2017-04-02
10speeduk; Hello;

Well we do know can not do anything :
> 
cannot copy extracted data for './boot/vmlinuz-4.4.0-71-generic' to '/boot/vmlinuz-4.4.0-71-generic.dpkg-new': failed to write (No space left on device)

until we get some head room to operate in.

Let's get a better idea, for my thought processes, of what our targets are.
Post back:
```

uname -r # so we do not mess with this kernel ##
df -h
df -i
dpkg -l | grep linux- 

```
Once we know maybe we can sic 'dpkg' on a/some old kernel(s) and get some head room . dpkg can and will operate at a lower level than apt ; We try our best here to remain within the package manage system and NOT break things !

Keep in mind this system requires updating ( " 0 to remove and 144 not to upgrade.") during the reconstruction process .

[INDENT][INDENT]so far
[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 10speeduk on 2017-04-02
Thank you for your help! :)

```
reidpa@reidpa-ThinkPad-T410:~$ uname -r
4.4.0-66-generic
```
 
 
```
reidpa@reidpa-ThinkPad-T410:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         1.9G     0  1.9G   0% /dev
tmpfs                        375M  6.2M  369M   2% /run
/dev/mapper/ubuntu--vg-root  143G   28G  108G  21% /
tmpfs                        1.9G  180K  1.9G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1                    472M  464M     0 100% /boot
tmpfs                        375M   52K  375M   1% /run/user/1000
reidpa@reidpa-ThinkPad-T410:~$ ^C
reidpa@reidpa-ThinkPad-T410:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         1.9G     0  1.9G   0% /dev
tmpfs                        375M  6.2M  369M   2% /run
/dev/mapper/ubuntu--vg-root  143G   28G  108G  21% /
tmpfs                        1.9G  180K  1.9G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda1                    472M  464M     0 100% /boot
tmpfs                        375M   52K  375M   1% /run/user/1000
reidpa@reidpa-ThinkPad-T410:~$ 
```

```
reidpa@reidpa-ThinkPad-T410:~$ df -i
Filesystem                   Inodes  IUsed   IFree IUse% Mounted on
udev                         474767    601  474166    1% /dev
tmpfs                        479942    820  479122    1% /run
/dev/mapper/ubuntu--vg-root 9486336 659253 8827083    7% /
tmpfs                        479942      6  479936    1% /dev/shm
tmpfs                        479942      6  479936    1% /run/lock
tmpfs                        479942     16  479926    1% /sys/fs/cgroup
/dev/sda1                    124928    346  124582    1% /boot
tmpfs                        479942     28  479914    1% /run/user/1000
reidpa@reidpa-ThinkPad-T410:~$ 
```

```
reidpa@reidpa-ThinkPad-T410:~$ dpkg -l | grep linux-
ii  linux-base                                  4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                              1.157.8                                       all          Firmware for Linux kernel drivers
iU  linux-generic                               4.4.0.71.77                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-47                      4.4.0-47.68                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-generic              4.4.0-47.68                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-51                      4.4.0-51.72                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-51-generic              4.4.0-51.72                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-53                      4.4.0-53.74                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-53-generic              4.4.0-53.74                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57                      4.4.0-57.78                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic              4.4.0-57.78                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-59                      4.4.0-59.80                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic              4.4.0-59.80                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-62                      4.4.0-62.83                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-62-generic              4.4.0-62.83                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-63                      4.4.0-63.84                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-63-generic              4.4.0-63.84                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-64                      4.4.0-64.85                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-64-generic              4.4.0-64.85                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-66                      4.4.0-66.87                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic              4.4.0-66.87                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-70                      4.4.0-70.91                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-70-generic              4.4.0-70.91                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-71                      4.4.0-71.92                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-71-generic              4.4.0-71.92                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                       4.4.0.71.77                                   amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-31-generic                4.4.0-31.50                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic                4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic                4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-43-generic                4.4.0-43.63                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-45-generic                4.4.0-45.66                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-51-generic                4.4.0-51.72                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-53-generic                4.4.0-53.74                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-57-generic                4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-59-generic                4.4.0-59.80                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic                4.4.0-62.83                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-63-generic                4.4.0-63.84                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-64-generic                4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-66-generic                4.4.0-66.87                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-70-generic                4.4.0-70.91                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic          4.4.0-31.50                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic          4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-generic          4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-43-generic          4.4.0-43.63                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-generic          4.4.0-45.66                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic          4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-51-generic          4.4.0-51.72                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-53-generic          4.4.0-53.74                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic          4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-59-generic          4.4.0-59.80                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic          4.4.0-62.83                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-63-generic          4.4.0-63.84                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-64-generic          4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-66-generic          4.4.0-66.87                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-70-generic          4.4.0-70.91                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-71-generic          4.4.0-71.92                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                         4.4.0.71.77                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        4.4.0-70.91                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
reidpa@reidpa-ThinkPad-T410:~$
```


Tried this:
```

reidpa@reidpa-ThinkPad-T410:~$ sudo apt-get install -f
[sudo] password for reidpa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-47 linux-headers-4.4.0-47-generic linux-headers-4.4.0-51
  linux-headers-4.4.0-51-generic linux-headers-4.4.0-53
  linux-headers-4.4.0-53-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-image-4.4.0-47-generic
  linux-image-4.4.0-51-generic linux-image-4.4.0-53-generic
  linux-image-4.4.0-57-generic linux-image-4.4.0-59-generic
  linux-image-4.4.0-62-generic linux-image-4.4.0-63-generic
  linux-image-4.4.0-64-generic linux-image-extra-4.4.0-47-generic
  linux-image-extra-4.4.0-51-generic linux-image-extra-4.4.0-53-generic
  linux-image-extra-4.4.0-57-generic linux-image-extra-4.4.0-59-generic
  linux-image-extra-4.4.0-62-generic linux-image-extra-4.4.0-63-generic
  linux-image-extra-4.4.0-64-generic ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-71-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed
  linux-image-4.4.0-71-generic
0 to upgrade, 1 to newly install, 0 to remove and 144 not to upgrade.
7 not fully installed or removed.
Need to get 0 B/21.8 MB of archives.
After this operation, 66.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 515471 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
Done.
Unpacking linux-image-4.4.0-71-generic (4.4.0-71.92) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-71-generic' to '/boot/vmlinuz-4.4.0-71-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
reidpa@reidpa-ThinkPad-T410:~$ 
```

---

### Post by deadflowr on 2017-04-02
You tried running the apt-get install -f command without sudo, so it denied you.
Try that command again, but this time with sudo.

---

### Post by Bashing-om on 2017-04-02
10speeduk; Ho Kay !

Let's roll up our sleeves and see what we can do .

We have these problems:
> 
iU linux-generic 4.4.0.71.77 amd64 Complete Generic Linux kernel and headers
iF linux-image-4.4.0-70-generic 4.4.0-70.91 amd64 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF linux-image-extra-4.4.0-66-generic 4.4.0-66.87 amd64 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU linux-image-extra-4.4.0-70-generic 4.4.0-70.91 amd64 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU linux-image-extra-4.4.0-71-generic 4.4.0-71.92 amd64 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU linux-image-generic 4.4.0.71.77 amd64 Generic Linux kernel image

( which the "iF linux-image-extra-4.4.0-66-generic" begs the question of how you are even able to boot the -66 kernel ) .


Please also place all requested posting between code tags:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
to maintain formatting and promote readability .

Now I need to know what grub has set for the booting kernels :
show me - between code tags !
```

ls -al /vmlinuz*
ls -al /initrd.img*

```

What makes this the more challenging is that the broken kernels are the  ones we want to keep ! Ouch !

[INDENT][INDENT]we may have our work cut out for us !
[/INDENT][/INDENT]

---

### Post by 10speeduk on 2017-04-02
Thanks mate, you are a real gentleman. 

```

reidpa@reidpa-ThinkPad-T410:~$ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 29 Mar 28 13:28 /vmlinuz -> boot/vmlinuz-4.4.0-70-generic
lrwxrwxrwx 1 root root 29 Mar 11 09:25 /vmlinuz.old -> boot/vmlinuz-4.4.0-66-generic

```

```

reidpa@reidpa-ThinkPad-T410:~$ ls -al /initrd.img*
ls: cannot access '/initrd.img*': No such file or directory
reidpa@reidpa-ThinkPad-T410:~$ 

Tried this:

[code] reidpa@reidpa-ThinkPad-T410:~$ sudo apt-get install -f
[sudo] password for reidpa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-47 linux-headers-4.4.0-47-generic linux-headers-4.4.0-51
  linux-headers-4.4.0-51-generic linux-headers-4.4.0-53
  linux-headers-4.4.0-53-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-image-4.4.0-47-generic
  linux-image-4.4.0-51-generic linux-image-4.4.0-53-generic
  linux-image-4.4.0-57-generic linux-image-4.4.0-59-generic
  linux-image-4.4.0-62-generic linux-image-4.4.0-63-generic
  linux-image-4.4.0-64-generic linux-image-extra-4.4.0-47-generic
  linux-image-extra-4.4.0-51-generic linux-image-extra-4.4.0-53-generic
  linux-image-extra-4.4.0-57-generic linux-image-extra-4.4.0-59-generic
  linux-image-extra-4.4.0-62-generic linux-image-extra-4.4.0-63-generic
  linux-image-extra-4.4.0-64-generic ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-71-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed
  linux-image-4.4.0-71-generic
0 to upgrade, 1 to newly install, 0 to remove and 144 not to upgrade.
7 not fully installed or removed.
Need to get 0 B/21.8 MB of archives.
After this operation, 66.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 515471 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
Done.
Unpacking linux-image-4.4.0-71-generic (4.4.0-71.92) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-71-generic' to '/boot/vmlinuz-4.4.0-71-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-71-generic /boot/vmlinuz-4.4.0-71-generic
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-71-generic_4.4.0-71.92_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
reidpa@reidpa-ThinkPad-T410:~$ 
```

[/code]

---

### Post by Bashing-om on 2017-04-02
10speeduk; erkkkk !

" ls -al /initrd.img*" should have returned something similar:
> 
sysop@x1604:~$ ls -al /initrd.img*
lrwxrwxrwx 1 root root 32 Mar 30 15:04 /initrd.img -> boot/initrd.img-4.4.0-71-generic
lrwxrwxrwx 1 root root 32 Mar 28 19:58 /initrd.img.old -> boot/initrd.img-4.4.0-70-generic
sysop@x1604:~$ 


So now why not ?
Show :
```

ls -al /boot/

```

[INDENT][INDENT]walking on eggs now !
[/INDENT][/INDENT]

---

### Post by 10speeduk on 2017-04-02
```
reidpa@reidpa-ThinkPad-T410:~$ ls -al /boot/
total 465596
drwxr-xr-x  4 root root     4096 Apr  2 20:03 .
drwxr-xr-x 24 root root     4096 Apr  2 16:10 ..
-rw-r--r--  1 root root  1243086 Oct 26 23:27 abi-4.4.0-47-generic
-rw-r--r--  1 root root  1243479 Nov 24 21:12 abi-4.4.0-51-generic
-rw-r--r--  1 root root  1243479 Dec  2 19:11 abi-4.4.0-53-generic
-rw-r--r--  1 root root  1243800 Dec 10 04:04 abi-4.4.0-57-generic
-rw-r--r--  1 root root  1244118 Jan  7 00:44 abi-4.4.0-59-generic
-rw-r--r--  1 root root  1244118 Jan 18 15:59 abi-4.4.0-62-generic
-rw-r--r--  1 root root  1245512 Feb  1 19:39 abi-4.4.0-63-generic
-rw-r--r--  1 root root  1245512 Feb 20 13:40 abi-4.4.0-64-generic
-rw-r--r--  1 root root  1245512 Mar  3 18:25 abi-4.4.0-66-generic
-rw-r--r--  1 root root  1245659 Mar 22 16:11 abi-4.4.0-70-generic
-rw-r--r--  1 root root   189809 Oct 26 23:27 config-4.4.0-47-generic
-rw-r--r--  1 root root   189877 Nov 24 21:12 config-4.4.0-51-generic
-rw-r--r--  1 root root   189877 Dec  2 19:11 config-4.4.0-53-generic
-rw-r--r--  1 root root   189991 Dec 10 04:04 config-4.4.0-57-generic
-rw-r--r--  1 root root   190047 Jan  7 00:44 config-4.4.0-59-generic
-rw-r--r--  1 root root   190047 Jan 18 15:59 config-4.4.0-62-generic
-rw-r--r--  1 root root   190247 Feb  1 19:39 config-4.4.0-63-generic
-rw-r--r--  1 root root   190247 Feb 20 13:40 config-4.4.0-64-generic
-rw-r--r--  1 root root   190247 Mar  3 18:25 config-4.4.0-66-generic
-rw-r--r--  1 root root   190236 Mar 22 16:11 config-4.4.0-70-generic
drwxr-xr-x  5 root root     1024 Mar 11 09:26 grub
-rw-r--r--  1 root root 38927043 Feb 12 11:29 initrd.img-4.4.0-47-generic
-rw-r--r--  1 root root 38932702 Feb 12 11:29 initrd.img-4.4.0-51-generic
-rw-r--r--  1 root root 38934545 Feb 12 11:29 initrd.img-4.4.0-53-generic
-rw-r--r--  1 root root 38938582 Feb 12 11:28 initrd.img-4.4.0-57-generic
-rw-r--r--  1 root root 38940464 Feb 12 11:28 initrd.img-4.4.0-59-generic
-rw-r--r--  1 root root 38938453 Feb 12 11:28 initrd.img-4.4.0-62-generic
-rw-r--r--  1 root root 38928376 Feb 21 07:36 initrd.img-4.4.0-63-generic
-rw-r--r--  1 root root 38927025 Feb 23 19:32 initrd.img-4.4.0-64-generic
-rw-r--r--  1 root root 38928474 Mar 11 09:26 initrd.img-4.4.0-66-generic
drwx------  2 root root    12288 Oct  8 20:35 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3873447 Oct 26 23:27 System.map-4.4.0-47-generic
-rw-------  1 root root  3874377 Nov 24 21:12 System.map-4.4.0-51-generic
-rw-------  1 root root  3874377 Dec  2 19:11 System.map-4.4.0-53-generic
-rw-------  1 root root  3875329 Dec 10 04:04 System.map-4.4.0-57-generic
-rw-------  1 root root  3875594 Jan  7 00:44 System.map-4.4.0-59-generic
-rw-------  1 root root  3875553 Jan 18 15:59 System.map-4.4.0-62-generic
-rw-------  1 root root  3883990 Feb  1 19:39 System.map-4.4.0-63-generic
-rw-------  1 root root  3883990 Feb 20 13:40 System.map-4.4.0-64-generic
-rw-------  1 root root  3883990 Mar  3 18:25 System.map-4.4.0-66-generic
-rw-------  1 root root  3882277 Mar 22 16:11 System.map-4.4.0-70-generic
-rw-------  1 root root  7060896 Oct 26 23:27 vmlinuz-4.4.0-47-generic
-rw-------  1 root root  7064208 Nov 24 21:12 vmlinuz-4.4.0-51-generic
-rw-------  1 root root  7065648 Dec  2 19:11 vmlinuz-4.4.0-53-generic
-rw-------  1 root root  7067152 Dec 10 04:04 vmlinuz-4.4.0-57-generic
-rw-------  1 root root  7069136 Jan  7 00:44 vmlinuz-4.4.0-59-generic
-rw-------  1 root root  7070992 Jan 18 15:59 vmlinuz-4.4.0-62-generic
-rw-------  1 root root  7087088 Feb  1 19:39 vmlinuz-4.4.0-63-generic
-rw-------  1 root root  7087152 Feb 20 13:40 vmlinuz-4.4.0-64-generic
-rw-------  1 root root  7087024 Mar  3 18:25 vmlinuz-4.4.0-66-generic
-rw-------  1 root root  7083344 Mar 22 16:11 vmlinuz-4.4.0-70-generic
reidpa@reidpa-ThinkPad-T410:~$ 


```

---

### Post by deadflowr on 2017-04-02
Try removing a single kernel image.
```
sudo apt-get purge linux-image-4.4.0-51-generic
```

---

### Post by 10speeduk on 2017-04-02
> **deadflowr said:**
> Try removing a single kernel image.
```
sudo apt-get purge linux-image-4.4.0-51-generic
```

Thanks DF:

```
 reidpa@reidpa-ThinkPad-T410:~$ sudo apt-get purge linux-image-4.4.0-51-generic
[sudo] password for reidpa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-extra-4.4.0-51-generic : Depends: linux-image-4.4.0-51-generic but it is not going to be installed
 linux-image-extra-4.4.0-71-generic : Depends: linux-image-4.4.0-71-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-4.4.0-71-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
reidpa@reidpa-ThinkPad-T410:~$ 


```

---

### Post by Bashing-om on 2017-04-02
10speeduk; Uh Huh =

Not surprised.

See if we get any headway :
```

sudo dpkg -P linux-headers-4.4-51 linux-headers-4.4.0-51-generic linux-image-4.4.0-51-generic linux-image-extra-4.4.0-51-generic

```

As we do want to RE-install 4.4.0-71; we try and leave it .

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by 10speeduk on 2017-04-03
Ok, that sounded promising (computer made busy but happy noises!):

```
reidpa@reidpa-ThinkPad-T410:~$ sudo dpkg -P linux-headers-4.4-51 linux-headers-4.4.0-51-generic linux-image-4.4.0-51-generic linux-image-extra-4.4.0-51-generic
[sudo] password for reidpa: 
dpkg: warning: ignoring request to remove linux-headers-4.4-51 which isn't installed
(Reading database ... 515470 files and directories currently installed.)
Removing linux-headers-4.4.0-51-generic (4.4.0-51.72) ...
Removing linux-image-extra-4.4.0-51-generic (4.4.0-51.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-51-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-51-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-51-generic (4.4.0-51.72) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
dkms: removing: virtualbox 5.0.24 (4.4.0-51-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 5.0.24
Kernel:  4.4.0-51-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-51-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-51-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-51-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-51-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-4.4.0-51-generic (4.4.0-51.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Errors were encountered while processing:
 linux-image-extra-4.4.0-51-generic
reidpa@reidpa-ThinkPad-T410:~$ 


```

---

### Post by 10speeduk on 2017-04-03
Ok, maybe not so good. Turned on computer and the screen says this:

[IMG]http://imageshack.com/a/img924/4532/Gy3oG1.jpg[/IMG]

---

### Post by Bashing-om on 2017-04-03
10speeduk; Hummm ...

How does " virtualbox 5.0.24" enter into this ? I have seen no other indications of this running virtually .
How does DKMS ( Dynamic Kernel Mode Setting ) enter into this ? A proprietary driver that was built on the -51 kernel and not updated to interface with the present kernel ?

And lastly, what results in booting any of those alternate older kernels ? We are going to have to boot something - somewhere - to effect a repair of this system .

[INDENT][INDENT]the truth, the whole truth and nothing but the truth[/INDENT][/INDENT]

---

### Post by 10speeduk on 2017-04-03
ok got this...

[IMG]http://imageshack.com/a/img924/3039/U1WLZs.jpg[/IMG]

---

### Post by Bashing-om on 2017-04-03
10speeduk; Well ... 

What results when "resume normal boot" is executed ?

Maybe what we do have here is a broken proprietary graphic's driver . Not detailed enough info to have a real opinion .

" virtualbox 5.0.24"  ??
DKMS ??

[INDENT]got to be a reason
[INDENT][INDENT][INDENT]got to be a cause
[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 10speeduk on 2017-04-03
ok, we're in!

---

### Post by Bashing-om on 2017-04-03
10speeduk; Great .

But I have no idea - not enough info to know - what to do next .

[INDENT][INDENT]mushroom feelings
[/INDENT][/INDENT]

---

### Post by 10speeduk on 2017-04-03
I am  in terminal, anything I can type in to give you info?

---

### Post by Bashing-om on 2017-04-03
10speeduk; Well ..

present;y I am lost . no idea of how virtualbox 5.0.24 or DKMS plays into these problems .
All I know is that there is a relationship . You will have to advise on what these relationships are .
Keep in mind, we can not look over your shoulder at the terminal, you will have to tell us what is not going on .

I have no virtualbox experience and do not know what is not taking place .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by 10speeduk on 2017-04-03
No worries. When I first installed Ubuntu I tried to install VB so I could run windows programs via an XP disk, but it was to difficult for me to understand so I left it. I don't know what is installed related to VB on the computer. I think if we can clear out the old Kernels it will be fine.  On the emergency boot purple menu there was an option to auto fix but again it needed space in the boot to download the necessary software so it failed...

---

### Post by Bashing-om on 2017-04-03
10speeduk; Ho Kay !
VB then we can do away with .. However, I see no related files - Let me get some additional help pulled in here that does know virtual systems .

we will get to the bottom of this.


[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by 10speeduk on 2017-04-03
Thanks Bashing Om!

---

### Post by Paddy Landau on 2017-04-04
Bashing-Om has asked me to weigh in on this, if I can. I'm no expert, but I think that we might be able to do something. I hope so, anyway. Follow these instructions.

**Enter Recovery Mode**

Go to the Recovery Menu (as in your last photo), and select "root" &#8212; "Drop to root shell prompt", then press Enter for maintenance when prompted.

Run the commands as indicated below. Note that in the Recovery Mode, you don't need [FONT=lucida console]sudo[/FONT].

**Get your system ready for maintenance**

Enter these two commands and let us know if you get errors.
```
mount --options remount,rw /
mount --all
```

**Remove everything that you don't need or is in error**

This long command may give a few warnings, but as long as they aren't errors, you should be fine. Please check that you have all the hyphens and asterisks in the right place, and especially that you don't include an extra space before or after an asterisk (only the spaces indicated are OK). Be sure to exclude 4.4.0-66 from the command, because you need it in order to boot.
```
apt purge linux-*-4.4.0-47* linux-*-4.4.0-51* linux-*-4.4.0-53* linux-*-4.4.0-57* linux-*-4.4.0-59* linux-*-4.4.0-62* linux-*-4.4.0-63* linux-*-4.4.0-64* linux-*-4.4.0-70* linux-*-4.4.0-71* linux-*generic virtualbox*
```

**Fix any problems**

Warnings are fine, but let us know of any errors from these three commands.
```
apt --fix-broken install
dpkg --configure --pending
apt autoremove
```

**Reboot**

Press Ctrl+Alt+Delete to reboot your machine.

**Finally**

I am not finished! So, let us know what happens before we move on. Oh, also let us know if you need VirtualBox.

---

### Post by Bashing-om on 2017-04-04
@ Paddy Landau :)

Heaps of thanks - I had no inkling of how to cope with the old VB install .

@10speeduk;
Let's see how this goes; knowing we will have to go back and fix the symlinks for grub in / to point to the freshly installed kernels in /boot .

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by 10speeduk on 2017-04-04
Thanks Paddy L and Bashing Om!

I typed the first line of code and got this screen:

[IMG]http://imageshack.com/a/img924/3390/wzuGPM.jpg[/IMG]

---

### Post by 10speeduk on 2017-04-04
just realised I have gone full circle... hang on will try again to get further...

---

### Post by 10speeduk on 2017-04-04
results are in....

[IMG]http://imageshack.com/a/img924/5028/oKsw46.jpg[/IMG]

---

### Post by Bashing-om on 2017-04-04
10speeduk; HeY !


> 
will try again to get further...

Been a long time since ....

[INDENT][INDENT]getting any further ?
[INDENT][INDENT][INDENT]how do we help ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by 10speeduk on 2017-04-04
There are no longer any Ubuntu options on start up now, just 2 Memory Test options.

---

### Post by 10speeduk on 2017-04-04
I'm away with work until the weekend now. But if you think of anything I'm all ears :)  Worst case I have a boot disk for Ubuntu if its belly up..

---

### Post by Bashing-om on 2017-04-04
10speeduk; Hey ..

Real quick .
```

sudo apt install --reinstall linux-image-generic

```
to try and get the latest kernel installed .

[INDENT][INDENT]maybe Yes
[/INDENT][/INDENT]

---

### Post by Paddy Landau on 2017-04-04
10speeuk, I shall post something tomorrow for you. It might be a little complicated, but I think that we can do it.

We'll need your boot disk. If possible, please prepare a Live CD (or Live USB) using the latest version of 16.04, which is 16.04.2. If you can't, we'll just use the one that you already have.

---

### Post by Paddy Landau on 2017-04-04
> **Bashing-om said:**
> ```
sudo apt install --reinstall linux-image-generic

```
That might help, yes.

**EDIT: No, don't do that yet.**

---

### Post by Paddy Landau on 2017-04-05
10speekuk, I need to confirm a couple of things.

[LIST=1]
[*]You have only Ubuntu, and no other operating system (e.g. Windows) on your system. 
[*]You installed Ubuntu 16.04 using the whole disk and with LVM, but you did *not* use full-disk encryption. (The attached screenshot should look familiar.) 
[/LIST]
Are those both correct? Or have I got something wrong? If you're not sure, there are ways to check.

---

### Post by Paddy Landau on 2017-04-06
I have a bunch of commands for you.
*This assumes that my two queries in the previous post are correct.*
Please follow these carefully. If you get an error, stop and report back to me.

**Boot the machine**

[LIST=1]
[*]Boot from a Live CD or Live USB. Preferably Ubuntu 16.04.2 (the latest download), but if you can't, that's OK; an earlier version of 16.04 will do. It should be the 64-bit version, which you most likely already have.
[*]When prompted, choose "**Try Ubuntu**" — don't choose "Install Ubuntu".
[*]Once you have booted the Live system, check that you have the right keyboard set up. The process is documented in [step 3.1 in another page]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcess#Check_your_keyboard") (just do step 3.1; don't go any further).
[*]You might find it easier if, at this point, you start Firefox and open this page. This will allow you to copy-and-paste the following commands, which will cut down typing and errors.
[*]Open a terminal ([FONT=lucida console]Ctrl[/FONT]+[FONT=lucida console]Alt[/FONT]+[FONT=lucida console]T[/FONT]).
[/LIST]
**Mount partitions**

Enter the following commands, in order. Remember: If you get an error, stop and report back.
```
sudo mkdir /mnt/root
sudo mount /dev/mapper/ubuntu--vg-root /mnt/root
cd /mnt/root
sudo mount /dev/sda1 /mnt/root/boot
```

**Enter chroot**

Enter the following commands, in order. Halfway through, you'll notice that your prompt changes from green-and-blue to only white.
```
sudo mount --bind /dev /mnt/root/dev
sudo mount --bind /run /mnt/root/run
sudo chroot /mnt/root
mount --types=proc proc /proc
mount --types=sysfs sys /sys
```
From here on, you don't use [FONT=lucida console]sudo[/FONT], because [FONT=lucida console]chroot[/FONT] doesn't use it.

**Install Linux**

This will install the latest kernels for 16.04 with the latest hardware support.
```
apt install linux-generic-hwe-16.04
```

**Install Grub**

```
grub-install --target=x86_64 --recheck /dev/sda
```

**Create Grub for your machine**

```
grub-mkconfig --output=/boot/grub/grub.cfg
```

**Recreate initramfs**

You need to recreate initramfs, which is something needed during boot.
```
update-initramfs -ck all
```

**Update packages**

This will update any packages that need updating.
```
apt update
apt upgrade
```

**Reboot your machine**

[LIST=1]
[*]Press [FONT=lucida console]Ctrl[/FONT]+[FONT=lucida console]D[/FONT] in the terminal (this will exit [FONT=lucida console]chroot[/FONT]).
[*]Close all open windows.
[*]Reboot.
[/LIST]
If all has gone well, your machine should be back in working order. Let me know what happens!

---

### Post by xhattam on 2017-04-28
Hi, 

Not sure if this is exactly the same situation here, but I hit a full /boot partition too (I'm on en _**encrypted**_ Ubuntu 16.04), and I got a lot of problems. I read this thread, and found a couple of useful commands, but no solution. After:

- checking that my boot was indeed full (with df -h)
- trying to install maven (what I was trying to do), trying to update an get missing dependencies (and failing at everything)

I CAREFULLY followed the steps in the **_Safely Removing Old Kernels_** section on  [this page]("https://help.ubuntu.com/community/RemoveOldKernels") (by replacing the kernel version numbers according to what on your own system, _**DO read the comments on each command to avoid deleting the wrong stuff !**_), I was FINALLY able to solve my problem.
Note: I had to **repeat all the steps twice**, moving to a slightly less old kernel, for it to **finally work**.

My /boot is now down(ish) to 93% space, and I was able to update and install everything properly (I didn't have to reboot, I might get a surprise at my next boot, but everything seems to have run smoothly).

If this doesn't solve your problem, maybe it'll help...

xhattam

---

