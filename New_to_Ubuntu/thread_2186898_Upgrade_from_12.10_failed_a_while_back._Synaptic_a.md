---
title: "Upgrade from 12.10 failed a while back. Synaptic also fails."
date: 2013-11-09
forum: New to Ubuntu
---

### Post by cheapodonuts on 2013-11-09
Problems started occurring after an attampted auto upgrade a while back, update manager and synaptic aso fail. I made a 13.10 iso DVD but it won't start. I have a 11.04 original Ubuntu disc that runs ok.

If no one has any ideas how I can sort my system, I shall buy a new 13.10 disc from the shop and do it that way.

Thanx in advance for any help people. :)

---

### Post by bkline on 2013-11-09
I've done lots of Ubuntu upgrades over the years, and more often than not the update system gets confused and messes something up.  When that happens, I back up my user data, install a fresh system from scratch, and restore my data from the backups.  Yes, this means re-installing and configuring some software, but in the end this takes much less time than wrestling with a broken system.  Others' mileage may vary. :-)

---

### Post by cheapodonuts on 2013-11-09
Thanx for a quik response bkline, yes I'm leaning that way, I'll admit.

---

### Post by ian-weisser on 2013-11-10
> **cheapodonuts said:**
> Problems started occurring after an attampted auto upgrade a while back, update manager and synaptic aso fail.

Okay, so your package management is broken.
Have you backed up your data?
Open a terminal, and post the *entire* result of 
```
sudo dpkg --configure -a
```
Remember to use [CODE] tags on your paste.



> **cheapodonuts said:**
> I made a 13.10 iso DVD but it won't start
Drive doesn't spin?
BIOS set to boot from HDD instead?
Bad burn?
Doesn't work in another machine?
Starts but then errors? What's the error?
Does your BIOS support booting from a USB?



> **cheapodonuts said:**
> I have a 11.04 original  Ubuntu disc that runs ok.
11.04 is past end-of-life. No longer supported. No easy upgrade path, since 11.10 is also past end-of-life.

---

### Post by cheapodonuts on 2013-11-11
I appreciate your assistance Ian :)

I'm partly deaf, so can't actually hear the cd drive spinning, but I see the green 'reading' led flickering.

sudo dpkg --configure -a result[CODE]cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ sudo dpkg --configure -a
[sudo] password for cheapo: 
Setting up initramfs-tools (0.103ubuntu0.2) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-extra-3.5.0-37-generic (3.5.0-37.58) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.5.0-38-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-37-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.5.0-37-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-extra-3.5.0-37-generic.postinst line 1010.
dpkg: error processing linux-image-extra-3.5.0-37-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.5.0-38-generic (3.5.0-38.59) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.5.0-38-generic /boot/vmlinuz-3.5.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-38-generic /boot/vmlinuz-3.5.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-38-generic /boot/vmlinuz-3.5.0-38-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-38-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.5.0-38-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-38-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-38-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-38-generic:
 linux-image-extra-3.5.0-38-generic depends on linux-image-3.5.0-38-generic; however:
  Package linux-image-3.5.0-38-generic is not configured yet.

dpkg: error processing linux-image-extra-3.5.0-38-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.5.0-38-generic; however:
  Package linux-image-3.5.0-38-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.5.0-38-generic; however:
  Package linux-image-extra-3.5.0-38-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.

dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-37-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.5.0-37-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.5.0-37-generic
 linux-image-3.5.0-38-generic
 linux-image-extra-3.5.0-38-generic
 linux-image-generic
 linux-generic
 initramfs-tools
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ 
[CODE]

Drive doesn't spin?  -------------------------------------------------It reads
BIOS set to boot from HDD instead?------------------------------- I have to manually set it in bios each time but disc is ignored even though it seems to be reading it, and bios returns to HDD boot next time
Bad burn? ----------------------------------------------------------- maybe, I'll dl and burn another
Doesn't work in another machine? -------------------------------- don't know
Starts but then errors? What's the error? ------------------------ no start with burnt disc. First boot gives kernel panic etc and secone boot shows multiple kernel options, choosing anything other than latest kernel is ok. Sorry, should have mentioned that in the beginning. :oops:
Does your BIOS support booting from a USB? ------------------- No

---

### Post by cheapodonuts on 2013-11-11
Oops.

---

### Post by ian-weisser on 2013-11-11
Thanks for the output. That's exactly what we needed.

Let's address the package manager...

> **cheapodonuts said:**
> 
update-initramfs: Generating /boot/initrd.img-3.5.0-37-generic
gzip: stdout: No space left on device

"No space left on device" means that the disk partition containing your /boot directory is full.
It may be easy to fix with just a little more information.

First, open a terminal and try the command **df** and post the result here.
Here's what mine looks like, as an example.
See my disk there, /dev/sda1? It's 84% full. Your system will have something quite close to 100% full.
```
$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda1      232188636 183697476  36696644  84% /
none                   4         0         4   0% /sys/fs/cgroup
udev             1408532         4   1408528   1% /dev
tmpfs             284192      1132    283060   1% /run
none                5120         0      5120   0% /run/lock
none             1420960       216   1420744   1% /run/shm
none              102400        68    102332   1% /run/user
```


Second, try the command **ls /boot  **and post the result here.
Here's mine, as an example. See how I have only two kernels installed? -12 and -13?
```
$ ls /boot
abi-3.11.0-12-generic     grub                          System.map-3.11.0-12-generic
abi-3.11.0-13-generic     initrd.img-3.11.0-12-generic  System.map-3.11.0-13-generic
config-3.11.0-12-generic  initrd.img-3.11.0-13-generic  vmlinuz-3.11.0-12-generic
config-3.11.0-13-generic  memtest86+.bin                vmlinuz-3.11.0-13-generic
extlinux                  memtest86+_multiboot.bin
```

Third, do the command **uname -r**
This simply tells you which kernel you are running. DON'T remove this one!
In this example, you can see that I'm running -12 (not -13).
```
$ uname -r
3.11.0-12-generic
```

There are lots of ways to remove old kernels.
If your /boot has *lots* of old kernels (from your description, that seems likely), there are lots of ways to remove them.
For example, if I wanted to remove -13, I would use the command
```
sudo apt-get remove linux-image-3.11.0.13-generic
```
See how I got most of the package name from the /boot listing?
If you have a bunch of old kernels, try it on one or two. Don't try it on the kernel you are running.
Don't delete ALL the old kernels. Keep one or two known good ones, since the latest crashes!


On to the DVD...

If the DVD drive is reading, and the BIOS supports the DVD drive, then among the many possibilities the most likely culprit is a bad burn. We have all made coasters before.

Multiple kernel options (the GRUB screen) indicates that your system is probably not booting from the DVD. Or is not finding the DVD bootable, and moving on to the next boot source on it's list. 
The Ubuntu Live disc doesn't use GRUB.

How, exactly, are you burning the disc? Which application?

---

### Post by cheapodonuts on 2013-11-11
[CODE]
~$ df
Filesystem              1K-blocks     Used Available Use% Mounted on
/dev/mapper/ubuntu-root 305467648 20533100 269417672   8% /
udev                       959056        4    959052   1% /dev
tmpfs                      386872      868    386004   1% /run
none                         5120        0      5120   0% /run/lock
none                       967172       12    967160   1% /run/shm
none                       102400       40    102360   1% /run/user
/dev/sda1                  233191   229338         0 100% /boot
[CODE]

[CODE]
:~$ ls /boot
abi-3.5.0-17-generic         initrd.img-3.5.0-34-generic
abi-3.5.0-29-generic         initrd.img-3.5.0-36-generic
abi-3.5.0-30-generic         initrd.img-3.5.0-37-generic
abi-3.5.0-31-generic         lost+found
abi-3.5.0-32-generic         memtest86+.bin
abi-3.5.0-33-generic         memtest86+_multiboot.bin
abi-3.5.0-34-generic         System.map-3.5.0-17-generic
abi-3.5.0-36-generic         System.map-3.5.0-29-generic
abi-3.5.0-37-generic         System.map-3.5.0-30-generic
abi-3.5.0-38-generic         System.map-3.5.0-31-generic
config-3.5.0-17-generic      System.map-3.5.0-32-generic
config-3.5.0-29-generic      System.map-3.5.0-33-generic
config-3.5.0-30-generic      System.map-3.5.0-34-generic
config-3.5.0-31-generic      System.map-3.5.0-36-generic
config-3.5.0-32-generic      System.map-3.5.0-37-generic
config-3.5.0-33-generic      System.map-3.5.0-38-generic
config-3.5.0-34-generic      vmlinuz-3.5.0-17-generic
config-3.5.0-36-generic      vmlinuz-3.5.0-29-generic
config-3.5.0-37-generic      vmlinuz-3.5.0-30-generic
config-3.5.0-38-generic      vmlinuz-3.5.0-31-generic
grub                         vmlinuz-3.5.0-32-generic
initrd.img-3.5.0-17-generic  vmlinuz-3.5.0-33-generic
initrd.img-3.5.0-29-generic  vmlinuz-3.5.0-34-generic
initrd.img-3.5.0-30-generic  vmlinuz-3.5.0-36-generic
initrd.img-3.5.0-31-generic  vmlinuz-3.5.0-37-generic
initrd.img-3.5.0-32-generic  vmlinuz-3.5.0-38-generic
initrd.img-3.5.0-33-generic
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ 
[CODE]
[CODE]
:~$ uname -r
3.5.0-37-generic
[CODE]

---

### Post by ian-weisser on 2013-11-11
> **cheapodonuts said:**
> ```

Filesystem              1K-blocks     Used Available Use% Mounted on
/dev/mapper/ubuntu-root 305467648 20533100 269417672   8% /
udev                       959056        4    959052   1% /dev
tmpfs                      386872      868    386004   1% /run
none                         5120        0      5120   0% /run/lock
none                       967172       12    967160   1% /run/shm
none                       102400       40    102360   1% /run/user
[COLOR=#ff0000]/dev/sda1                  233191   229338         0 100% /boot[/COLOR]

```

Yup, there it is. Full /boot partition.
A separate boot partition is optional, and I usually discourage it among non-power-users for precisely this reason. However, that's neither here nor there - you have one, and let's live with it.

Looking at uname -r, we should keep the runnign kernel (-37), perhaps one earlier (-36), and everything later (-38)

So you should be able to safely remove -17, -29, -30, -31, -32, -33, and -34

Here is how you remove one old kernel image. This command should take about a minute (perhaps less) to complete.
```
sudo apt-get autoremove linux-image-3.5.0-17-generic
```

Here is how you remove the remaining old kernel images at once. This command may take two or three minutes to complete.
```

sudo apt-get autoremove linux-image-3.5.0-29-generic linux-image-3.5.0-30-generic linux-image-3.5.0-31-generic linux-image-3.5.0-32-generic linux-image-3.5.0-33-generic linux-image-3.5.0-34-generic
```

Finally, let's see if the package manager has any more errors:
```
sudo apt-get update && sudo apt-get upgrade
```

And, for your own reference, take a look at the **df** command again, see how full your /boot partition is, down from 100%

---

### Post by cheapodonuts on 2013-11-12
[CODE]
:~$ df
Filesystem              1K-blocks     Used Available Use% Mounted on
/dev/mapper/ubuntu-root 305467648 19530380 270420392   7% /
udev                       959056       12    959044   1% /dev
tmpfs                      386872      876    385996   1% /run
none                         5120        0      5120   0% /run/lock
none                       967172       12    967160   1% /run/shm
none                       102400       32    102368   1% /run/user
/dev/sda1                  233191   114345    106405  52% /boot
[CODE]


Thanx again Ian. 
Heh, the apt-get update and upgrades took way longer than removing the kernels!
 Now I'll reboot and see how the system feels.

---

### Post by cheapodonuts on 2013-11-12
Boot up is normal now, (thanx again Ian) but the system still wants to send some sort of error report. Though it gives no option to view details. 
sudo dpkg --configure -a , gives no result at all.

---

### Post by ian-weisser on 2013-11-12
Glad you got the package manager working!

Look in /var/crash for automatically-generated error reports.
Here is an example:
```
$ ls -l /var/crash
total 28304
-rw-r----- 1 ian  whoopsie   262099 Nov  6 19:42 _usr_bin_nmcli.1000.crash
-rw-r----- 1 ian  whoopsie 26288823 Nov  9 12:23 _usr_bin_xfdesktop.1000.crash
-rw-r----- 1 root whoopsie  2384336 Nov  7 08:27 _usr_games_xconq.0.crash
```

Since Nov 6, I have had three applications crash: nmcli, xfdesktop, and xconq
This will tell you what crashed and when. That's the first step in chasing down mysterious error reports.

---

### Post by cheapodonuts on 2013-11-13
[CODE]
:~$ ls -l /var/crash
total 2200
-rw-r----- 1 cheapo whoopsie   12072 Nov  9 20:51 _usr_bin_software-properties-gtk.1000.crash
-rw-r----- 1 cheapo whoopsie    8005 Nov 12 18:29 _usr_bin_update-manager.1000.crash
-rw-r----- 1 cheapo whoopsie 1115595 Nov 11 10:37 _usr_bin_update-notifier.1000.crash
---------- 1 cheapo whoopsie 1079438 Nov 12 22:12 _usr_lib_firefox_firefox.1000.crash
-rw-r----- 1 root   whoopsie    9239 Nov  9 13:19 _usr_sbin_aptd.0.crash
-rw-r----- 1 root   whoopsie    7734 Nov  6 17:56 _usr_share_apport_apport-gtk.0.crash
-rw-r----- 1 cheapo whoopsie    8217 Nov 13 10:25 _usr_share_apport_apport-gtk.1000.crash
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ 
[CODE]

I went to the var file and opened the latest one with text editor

[CODE]
ProblemType: Crash
CrashCounter: 1
Date: Wed Nov 13 10:25:41 2013
ExecutablePath: /usr/share/apport/apport-gtk
ExecutableTimestamp: 1382617646
InterpreterPath: /usr/bin/python3.2mu
ProcCmdline: /usr/bin/python3 /usr/share/apport/apport-gtk -c /var/crash/_usr_bin_software-properties-gtk.1000.crash
ProcCwd: /home/cheapo
ProcEnviron:
 LANGUAGE=en_GB:en
 LC_TIME=en_GB.UTF-8
 LC_MONETARY=en_GB.UTF-8
 PATH=(custom, no user)
 XDG_RUNTIME_DIR=<set>
 LC_ADDRESS=en_GB.UTF-8
 LANG=en_GB.UTF-8
 LC_TELEPHONE=en_GB.UTF-8
 SHELL=/bin/bash
 LC_NAME=en_GB.UTF-8
 LC_MEASUREMENT=en_GB.UTF-8
 LC_IDENTIFICATION=en_GB.UTF-8
 LC_NUMERIC=en_GB.UTF-8
 LC_PAPER=en_GB.UTF-8
ProcMaps:
 08048000-0827d000 r-xp 00000000 fc:00 7865173    /usr/bin/python3.2mu
 0827d000-0827e000 r--p 00234000 fc:00 7865173    /usr/bin/python3.2mu
 0827e000-082dd000 rw-p 00235000 fc:00 7865173    /usr/bin/python3.2mu
 082dd000-082f5000 rw-p 00000000 00:00 0 
 09f62000-0a51a000 rw-p 00000000 00:00 0          [heap]
 b6c68000-b6d44000 r-xp 00000000 fc:00 7869724    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17
 b6d44000-b6d45000 ---p 000dc000 fc:00 7869724    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17
 b6d45000-b6d49000 r--p 000dc000 fc:00 7869724    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17
 b6d49000-b6d4a000 rw-p 000e0000 fc:00 7869724    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.17
 b6d4a000-b6d51000 rw-p 00000000 00:00 0 
 b6d51000-b6e6f000 r-xp 00000000 fc:00 7865739    /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 b6e6f000-b6e70000 ---p 0011e000 fc:00 7865739    /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 b6e70000-b6e72000 r--p 0011e000 fc:00 7865739    /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 b6e72000-b6e73000 rw-p 00120000 fc:00 7865739    /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
 b6e73000-b6eb2000 r-xp 00000000 fc:00 7995400    /usr/lib/python3/dist-packages/apt_pkg.cpython-32mu.so
 b6eb2000-b6eb3000 r--p 0003e000 fc:00 7995400    /usr/lib/python3/dist-packages/apt_pkg.cpython-32mu.so
 b6eb3000-b6eb8000 rw-p 0003f000 fc:00 7995400    /usr/lib/python3/dist-packages/apt_pkg.cpython-32mu.so
 b6eb8000-b6ec7000 r-xp 00000000 fc:00 6030005    /lib/i386-linux-gnu/libbz2.so.1.0.4
 b6ec7000-b6ec8000 r--p 0000e000 fc:00 6030005    /lib/i386-linux-gnu/libbz2.so.1.0.4
 b6ec8000-b6ec9000 rw-p 0000f000 fc:00 6030005    /lib/i386-linux-gnu/libbz2.so.1.0.4
 b6edf000-b6f30000 r-xp 00000000 fc:00 6030023    /lib/i386-linux-gnu/libssl.so.1.0.0
 b6f30000-b6f32000 r--p 00050000 fc:00 6030023    /lib/i386-linux-gnu/libssl.so.1.0.0
 b6f32000-b6f36000 rw-p 00052000 fc:00 6030023    /lib/i386-linux-gnu/libssl.so.1.0.0
 b6f36000-b70c8000 r-xp 00000000 fc:00 6030024    /lib/i386-linux-gnu/libcrypto.so.1.0.0
 b70c8000-b70d7000 r--p 00192000 fc:00 6030024    /lib/i386-linux-gnu/libcrypto.so.1.0.0
 b70d7000-b70de000 rw-p 001a1000 fc:00 6030024    /lib/i386-linux-gnu/libcrypto.so.1.0.0
 b70de000-b70e1000 rw-p 00000000 00:00 0 
 b70ed000-b70f4000 r-xp 00000000 fc:00 8269917    /usr/lib/python3.2/lib-dynload/bz2.cpython-32mu.so
 b70f4000-b70f5000 r--p 00006000 fc:00 8269917    /usr/lib/python3.2/lib-dynload/bz2.cpython-32mu.so
 b70f5000-b70f7000 rw-p 00007000 fc:00 8269917    /usr/lib/python3.2/lib-dynload/bz2.cpython-32mu.so
 b70f7000-b70fb000 r-xp 00000000 fc:00 8269939    /usr/lib/python3.2/lib-dynload/_hashlib.cpython-32mu.so
 b70fb000-b70fc000 r--p 00003000 fc:00 8269939    /usr/lib/python3.2/lib-dynload/_hashlib.cpython-32mu.so
 b70fc000-b70fd000 rw-p 00004000 fc:00 8269939    /usr/lib/python3.2/lib-dynload/_hashlib.cpython-32mu.so
 b70fd000-b715e000 rw-p 00000000 00:00 0 
 b715f000-b7263000 rw-p 00000000 00:00 0 
 b7264000-b72a5000 rw-p 00000000 00:00 0 
 b72a5000-b74a5000 r--p 00000000 fc:00 7864449    /usr/lib/locale/locale-archive
 b74a5000-b74a6000 rw-p 00000000 00:00 0 
 b74a6000-b74e7000 r-xp 00000000 fc:00 6029525    /lib/i386-linux-gnu/libm-2.17.so
 b74e7000-b74e8000 r--p 00040000 fc:00 6029525    /lib/i386-linux-gnu/libm-2.17.so
 b74e8000-b74e9000 rw-p 00041000 fc:00 6029525    /lib/i386-linux-gnu/libm-2.17.so
 b74e9000-b74ea000 rw-p 00000000 00:00 0 
 b74ea000-b7506000 r-xp 00000000 fc:00 6030031    /lib/i386-linux-gnu/libgcc_s.so.1
 b7506000-b7507000 r--p 0001b000 fc:00 6030031    /lib/i386-linux-gnu/libgcc_s.so.1
 b7507000-b7508000 rw-p 0001c000 fc:00 6030031    /lib/i386-linux-gnu/libgcc_s.so.1
 b7508000-b76b6000 r-xp 00000000 fc:00 6029526    /lib/i386-linux-gnu/libc-2.17.so
 b76b6000-b76b8000 r--p 001ae000 fc:00 6029526    /lib/i386-linux-gnu/libc-2.17.so
 b76b8000-b76b9000 rw-p 001b0000 fc:00 6029526    /lib/i386-linux-gnu/libc-2.17.so
 b76b9000-b76bc000 rw-p 00000000 00:00 0 
 b76bc000-b76e1000 r-xp 00000000 fc:00 6034239    /lib/i386-linux-gnu/libexpat.so.1.6.0
 b76e1000-b76e3000 r--p 00025000 fc:00 6034239    /lib/i386-linux-gnu/libexpat.so.1.6.0
 b76e3000-b76e4000 rw-p 00027000 fc:00 6034239    /lib/i386-linux-gnu/libexpat.so.1.6.0
 b76e4000-b76fb000 r-xp 00000000 fc:00 6034237    /lib/i386-linux-gnu/libz.so.1.2.7
 b76fb000-b76fc000 r--p 00016000 fc:00 6034237    /lib/i386-linux-gnu/libz.so.1.2.7
 b76fc000-b76fd000 rw-p 00017000 fc:00 6034237    /lib/i386-linux-gnu/libz.so.1.2.7
 b76fd000-b76ff000 r-xp 00000000 fc:00 6029510    /lib/i386-linux-gnu/libutil-2.17.so
 b76ff000-b7700000 r--p 00001000 fc:00 6029510    /lib/i386-linux-gnu/libutil-2.17.so
 b7700000-b7701000 rw-p 00002000 fc:00 6029510    /lib/i386-linux-gnu/libutil-2.17.so
 b7701000-b7702000 rw-p 00000000 00:00 0 
 b7702000-b7705000 r-xp 00000000 fc:00 6029531    /lib/i386-linux-gnu/libdl-2.17.so
 b7705000-b7706000 r--p 00002000 fc:00 6029531    /lib/i386-linux-gnu/libdl-2.17.so
 b7706000-b7707000 rw-p 00003000 fc:00 6029531    /lib/i386-linux-gnu/libdl-2.17.so
 b7707000-b771e000 r-xp 00000000 fc:00 6029524    /lib/i386-linux-gnu/libpthread-2.17.so
 b771e000-b771f000 r--p 00016000 fc:00 6029524    /lib/i386-linux-gnu/libpthread-2.17.so
 b771f000-b7720000 rw-p 00017000 fc:00 6029524    /lib/i386-linux-gnu/libpthread-2.17.so
 b7720000-b7722000 rw-p 00000000 00:00 0 
 b7725000-b772e000 r-xp 00000000 fc:00 8269928    /usr/lib/python3.2/lib-dynload/_ssl.cpython-32mu.so
 b772e000-b772f000 r--p 00008000 fc:00 8269928    /usr/lib/python3.2/lib-dynload/_ssl.cpython-32mu.so
 b772f000-b7730000 rw-p 00009000 fc:00 8269928    /usr/lib/python3.2/lib-dynload/_ssl.cpython-32mu.so
 b7730000-b7737000 r--s 00000000 fc:00 7876044    /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
 b7737000-b7738000 r--p 002bd000 fc:00 7864449    /usr/lib/locale/locale-archive
 b7738000-b773a000 rw-p 00000000 00:00 0 
 b773a000-b773b000 r-xp 00000000 00:00 0          [vdso]
 b773b000-b775b000 r-xp 00000000 fc:00 6029527    /lib/i386-linux-gnu/ld-2.17.so
 b775b000-b775c000 r--p 0001f000 fc:00 6029527    /lib/i386-linux-gnu/ld-2.17.so
 b775c000-b775d000 rw-p 00020000 fc:00 6029527    /lib/i386-linux-gnu/ld-2.17.so
 bfe34000-bfe55000 rw-p 00000000 00:00 0          [stack]
ProcStatus:
 Name:    apport-gtk
 State:    R (running)
 Tgid:    3441
 Pid:    3441
 PPid:    1
 TracerPid:    0
 Uid:    1000    1000    1000    1000
 Gid:    1000    1000    1000    1000
 FDSize:    32
 Groups:    4 24 27 30 46 107 124 1000 
 VmPeak:       19796 kB
 VmSize:       19796 kB
 VmLck:           0 kB
 VmPin:           0 kB
 VmHWM:       11500 kB
 VmRSS:       11500 kB
 VmData:        7724 kB
 VmStk:         136 kB
 VmExe:        2260 kB
 VmLib:        6920 kB
 VmPTE:          52 kB
 VmSwap:           0 kB
 Threads:    1
 SigQ:    0/14937
 SigPnd:    0000000000000000
 ShdPnd:    0000000000000000
 SigBlk:    0000000000000000
 SigIgn:    0000000001001000
 SigCgt:    0000000180000002
 CapInh:    0000000000000000
 CapPrm:    0000000000000000
 CapEff:    0000000000000000
 CapBnd:    ffffffffffffffff
 Cpus_allowed:    f
 Cpus_allowed_list:    0-3
 Mems_allowed:    1
 Mems_allowed_list:    0
 voluntary_ctxt_switches:    10
 nonvoluntary_ctxt_switches:    50
PythonArgs: ['/usr/share/apport/apport-gtk', '-c', '/var/crash/_usr_bin_software-properties-gtk.1000.crash']
Traceback:
 Traceback (most recent call last):
   File "/usr/share/apport/apport-gtk", line 16, in <module>
     from gi.repository import GObject, GLib, Wnck, GdkX11, Gdk
   File "/usr/lib/python3/dist-packages/gi/__init__.py", line 27, in <module>
     from ._gi import _API, Repository
 ImportError: No module named _gi
UserGroups: adm cdrom dip lpadmin plugdev sambashare sudo
[CODE]

---

### Post by ian-weisser on 2013-11-13
> **cheapodonuts said:**
> 
[...]
ProcCmdline: /usr/bin/python3 /usr/share/apport/apport-gtk -c /var/crash/_usr_bin_software-properties-gtk.1000.crash
[...]
PythonArgs: ['/usr/share/apport/apport-gtk', '-c', '/var/crash/_usr_bin_software-properties-gtk.1000.crash']
Traceback:
 Traceback (most recent call last):
   File "/usr/share/apport/apport-gtk", line 16, in <module>
     from gi.repository import GObject, GLib, Wnck, GdkX11, Gdk
   File "/usr/lib/python3/dist-packages/gi/__init__.py", line 27, in <module>
     from ._gi import _API, Repository
 ImportError: No module named _gi


Here's what the file means:
The program software-properties-gtk crashed. That's the program that provides the "Software Sources" control panel in Software Center.
We don't know why it crashed, because during the crash-reporting process, the reporter itself crashed. So that's two separate failures.
We know a lot about why the reporter crashed, we have it's traceback.

I'm not an expert on GObject introspection using Python3, so I'm hesitant to offer a fix. I will leave that open to another community member.

---

### Post by cheapodonuts on 2013-11-13
Ok Ian, the system is running in a reasonably normal way anyhow. So once again I thank you.

Havd a donut or nine. :D

[[IMG]http://i81.photobucket.com/albums/j226/chashugh/Donuts/donutsdetail.jpg[/IMG]]("http://s81.photobucket.com/user/chashugh/media/Donuts/donutsdetail.jpg.html")

Best regards, Pete.

PS. After looking twice at this picture, I'm not totally sure if they are real. Haha! Bon apetite!

---

