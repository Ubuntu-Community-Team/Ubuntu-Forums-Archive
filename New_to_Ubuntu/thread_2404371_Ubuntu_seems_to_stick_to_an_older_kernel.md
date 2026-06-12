---
title: "Ubuntu seems to stick to an older kernel"
date: 2018-10-23
forum: New to Ubuntu
---

### Post by richterbg on 2018-10-23
Currently, I'm running Ubuntu 14.04:

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty


Well, it seems that my computer is running out of inodes. A lot of inodes are used by the /usr/src folder, where there is a bunch of folders, such as:

drwxr-xr-x 24 root root 4096 &#1072;&#1087;&#1088;  9  2016 linux-headers-3.13.0-85
drwxr-xr-x  7 root root 4096 &#1072;&#1087;&#1088;  9  2016 linux-headers-3.13.0-85-generic
drwxr-xr-x 24 root root 4096 &#1084;&#1072;&#1081; 17  2016 linux-headers-3.13.0-86
drwxr-xr-x  7 root root 4096 &#1084;&#1072;&#1081; 17  2016 linux-headers-3.13.0-86-generic
drwxr-xr-x 24 root root 4096 &#1102;&#1085;&#1080;  1  2016 linux-headers-3.13.0-87
drwxr-xr-x  7 root root 4096 &#1102;&#1085;&#1080;  1  2016 linux-headers-3.13.0-87-generic
drwxr-xr-x 24 root root 4096 &#1102;&#1085;&#1080; 15  2016 linux-headers-3.13.0-88
drwxr-xr-x  7 root root 4096 &#1102;&#1085;&#1080; 15  2016 linux-headers-3.13.0-88-generic
...

So, ** uname -r **returns:

3.13.0-85-generic

The question is why Ubuntu sticks to the 3.13.0-85-generic kernel, but keeps installing newer ones? Is it OK to switch to a newer kernel, so that the older ones can be removed?

---

### Post by TheFu on 2018-10-23
Did you reboot?
Also, when posting cmd output, plesae, pppplease, use code tags.

BTW, 14.04 support will be ending in about 6 months.  Time to actively plan the migration.

Removing 10 files isn't going to help the inode problem.  If you don't have 50K inodes available, there will be an issue soon.

After you reboot an get the new kernel (or manually chose it), try **sudo apt autoremove**.  In 16.04 and later, that retains only 2-3 old kernels.

---

### Post by richterbg on 2018-10-23
I did reboot. Each one of these is a folder with 15k files in it, so removing them will free a lot of inodes up. The issue is that the kernel is -85, while the others are newer: -86, -87, all the way up to -116.

sudo apt-get autoremove removed two older kernels: -83 and -84. It did not give an option to remove those with numbers above -85. How to switch Ubunto to the -116-generic version and is this going to allow autoremove the versions with smaller numbers?

---

### Post by TheFu on 2018-10-23
apt, not apt-get.

You can get a list of packages and manually remove them.
```
sudo apt purge linux-headers-3.13.0-86-generic
```

I don't remember when apt started cleaning up old kernels. Perhaps 14.04 still needed manual intervention?

For most end-users, going into Synaptic and removing them is probably easiest.  On a server, I used a little script. There are many of those on the internet.  [http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt)  but at some point 14.04 cleanup stopped working for my script.

---

### Post by richterbg on 2018-10-23
I used apt-get instead:

```
sudo apt-get purge linux-headers-3.13.0-87-generic
```

It seems to do the job. However, why has the system decided to stay with **[COLOR=#000000]3.13.0-85-generic[/COLOR]**[COLOR=#000000], but is still installing the new kernels...[/COLOR]

---

### Post by TheFu on 2018-10-23
At boot, you can pick the kernel you want, right?  There is either a list on the grub screen or choose "Advanced Options" <--- or something like that - -- to see the list.

Could it be that all the newer kernels failed to get installed correctly due to storage problems?
```
df -hT
df -i 
```
would be helpful and maybe **lsblk**.

---

### Post by Impavidus on 2018-10-23
The question is: Why does the system not automatically boot the latest kernel? The header packages get installed, but does it install the kernel packages too? Is your current Ubuntu 14.04 system the one that's in control of grub (maybe not if you're dual booting with another Linux)? Open a terminal, make it large so we can see long lines of output and run```
dpkg --list 'linux-*'
```

---

### Post by richterbg on 2018-10-23
Indeed, the kernel packages seem to be missing. I did install 3.13.0-161-generic manually with the following command:

```
[COLOR=#242729][FONT=Consolas]sudo apt-get install linux-image-your_version_choice linux-headers-your_version_choice linux-image-extra-your_version_choice[/FONT][/COLOR]
```

Ubuntu started using it. The output of the command is:

```
dpkg --list 'linux-*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                            Version                      Architecture                 Description
+++-===============================================-============================-============================-===================================================================================================
un  linux-doc-3.13.0                                <none>                       <none>                       (no description available)
ii  linux-firmware                                  1.127.24                     all                          Firmware for Linux kernel drivers
un  linux-headers                                   <none>                       <none>                       (no description available)
un  linux-headers-3.0                               <none>                       <none>                       (no description available)
ii  linux-headers-3.13.0-160                        3.13.0-160.210               all                          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-160-generic                3.13.0-160.210               amd64                        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-161                        3.13.0-161.211               all                          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-161-generic                3.13.0-161.211               amd64                        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-85                         3.13.0-85.129                all                          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic                 3.13.0-85.129                amd64                        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
un  linux-image                                     <none>                       <none>                       (no description available)
un  linux-image-3.0                                 <none>                       <none>                       (no description available)
ii  linux-image-3.13.0-161-generic                  3.13.0-161.211               amd64                        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-85-generic                   3.13.0-85.129                amd64                        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-161-generic            3.13.0-161.211               amd64                        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-85-generic             3.13.0-85.129                amd64                        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
un  linux-initramfs-tool                            <none>                       <none>                       (no description available)
un  linux-kernel-headers                            <none>                       <none>                       (no description available)
un  linux-kernel-log-daemon                         <none>                       <none>                       (no description available)
ii  linux-libc-dev:amd64                            3.13.0-161.211               amd64                        Linux Kernel Headers for development
un  linux-restricted-common                         <none>                       <none>                       (no description available)
ii  linux-signed-image-3.13.0-85-generic            3.13.0-85.129                amd64                        Signed kernel image generic
ii  linux-sound-base                                1.0.25+dfsg-0ubuntu4         all                          base package for ALSA and OSS sound systems
un  linux-source-3.13.0                             <none>                       <none>                       (no description available)
un  linux-tools                                     <none>                       <none>                       (no description available)



```

I do have a separate ancient Ubuntu 12.04 install on a separate disk.

---

### Post by Impavidus on 2018-10-24
Try this:```
sudo apt-get install linux-generic
```That should install the metapackages that automatically pull in the kernel upgrades.

Your old 12.04 is not in control of grub. The fact that kernel 161 is now used proves that.

---

