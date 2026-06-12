---
title: "Kernel Compiling for iptables in 15 Steps"
date: 2006-09-27
forum: Outdated Tutorials &amp; Tips
---

### Post by moore.bryan on 2006-09-27
[SIZE=2]*i put this together based on a number of other posts (namely [http://ubuntuforums.org/showthread.php?t=217657&highlight=compiling+kernel](http://ubuntuforums.org/showthread.php?t=217657&highlight=compiling+kernel) and [http://ubuntuforums.org/showpost.php?p=1174954&postcount=507](http://ubuntuforums.org/showpost.php?p=1174954&postcount=507)) because so many newbies, like myself, need a straight-forward way to understand kernel compiling.  included is iptables setup so the kernel works with it... this isn't perfect, but it should get you through the "worst" of it!  keep in mind, x.x.x is whichever kernel you're trying to compile.  also, i know some of these commands could be included on the same line with &&, but i wanted to make it as lock-step as possible.  any feedback would be greatly appeciated!  keep in mind compiling can take time, so make sure to have something else to do at certain steps!*
```

sudo aptitude install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget
cd /usr/src
sudo wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-x.x.x.tar.bz2
sudo tar -xvjf linux-x.x.x.tar.bz2
sudo rm -rf linux
sudo ln -s /usr/src/linux-x.x.x linux
cd /usr/src/linux
sudo cp /boot/config-`uname -r` .config
sudo make xconfig

```[I]
Now you're in xconfig/qconf.  For a "quick" machine and iptables support, select/unselect the following (/ indicates sub-directory of the main directory):
  [/I][/SIZE]> 
General Setup[INDENT][SIZE=2]S: Support for paging of anonymous memory (swap)[/SIZE]
[/INDENT][SIZE=2]Loadable Module Support[/SIZE][INDENT][SIZE=2]U: Module Versioning Support
U: Source checksum for all modules
[/SIZE] [/INDENT][SIZE=2]Block Layer[/SIZE][INDENT][SIZE=2]U: Large Block Devices (and others if possible)
/IO Schedulers[/SIZE][INDENT][SIZE=2]U: Anticipatory I/O Schedulers
U: Deadline I/O Schedulers
[/SIZE] [/INDENT][/INDENT][SIZE=2]Processor type and features[/SIZE][INDENT][SIZE=2]U: Symmetric processing support (unless you know your processor supports it)
U: Generic x86 support
S: HPET Timer Support
/Preemption Model[/SIZE][INDENT][SIZE=2]S: Voluntary Kernel Preemption (Desktop)
S: Local APCI support on uniprocessors
[/SIZE] [/INDENT][SIZE=2]/Local APCI Support[/SIZE][INDENT][SIZE=2]S: IO-APCI support on uniprocessors
[/SIZE] [/INDENT][SIZE=2]/High Memory Support[/SIZE][INDENT][SIZE=2]S: Off (if you have under 1GB RAM)
[/SIZE] [/INDENT][SIZE=2]/Memory Model[/SIZE][INDENT][SIZE=2]S: Sparse Memory
S: MTRR support
S: Use register arguments
S: Enable seccomp to compute untrusted bytecode
[/SIZE] [/INDENT][SIZE=2]/Timer Frequency[/SIZE][INDENT][SIZE=2]S: 1000hz
[/SIZE] [/INDENT][/INDENT][SIZE=2]Bus Options[/SIZE][INDENT][SIZE=2]S: Message Signaled Interrupts (MSI and MSI-X)(PCI_MSI)
[/SIZE] [/INDENT][SIZE=2]Networking[/SIZE][INDENT][SIZE=2]U: Anything in Amateur Radio, IrDA, or Bluetooth you don't have.
/Networking options[/SIZE][INDENT][SIZE=2]S: Network packet filtering (replaces ipchains)
[/SIZE] [/INDENT][SIZE=2]/Core Netfilter Configuration
[/SIZE] [/INDENT][INDENT][INDENT][SIZE=2]S: Netfilter Xtables support (!!!required for ip_tables)
[/SIZE] [/INDENT][SIZE=2]/Network packet filtering[/SIZE][INDENT][SIZE=2]/IP: Net Filter configuration[/SIZE][INDENT][SIZE=2]S: IP Tables support
[/SIZE] [/INDENT][/INDENT][SIZE=2]S: Packet socket:mmapped IO
[/SIZE] [/INDENT][SIZE=2]Device Drivers[/SIZE][INDENT][SIZE=2]/ATA/ATAP/MFR/RLL support[/SIZE][INDENT][SIZE=2]S: Use PCI DMA by Default
U: IDE Taskfile Access
[/SIZE] [/INDENT][SIZE=2]/Raid and LVM[/SIZE][INDENT][SIZE=2]U: everything you don't use
[/SIZE] [/INDENT][SIZE=2]/I2O support[/SIZE][INDENT][SIZE=2]U: most people do not use this
[/SIZE] [/INDENT][/INDENT][SIZE=2]Network Device Support[/SIZE][INDENT][SIZE=2]U: EQL support
U: Universal TUN/TAP device driver support
U: FDDI Driver support
U: HIPPI driver support
U: SLIP (serial line) support
U: Traffic Support
U: Network console login support
/ARCnet support[/SIZE][INDENT][SIZE=2]U: most people don't need this
[/SIZE] [/INDENT][SIZE=2]/Ethernet Support (1000 MB)[/SIZE][INDENT][SIZE=2]U: everything you don't have
[/SIZE] [/INDENT][SIZE=2]/Ethernet Support (10000 MB)[/SIZE][INDENT][SIZE=2]U: everything you don't have
[/SIZE] [/INDENT][SIZE=2]/Token Ring Devices[/SIZE][INDENT][SIZE=2]U: everything you don't connect to
[/SIZE] [/INDENT][SIZE=2]/WAN interfaces support[/SIZE][INDENT][SIZE=2]U: everything you don't need
[/SIZE] [/INDENT][/INDENT][SIZE=2]ISDN subsystem[/SIZE][INDENT][SIZE=2]U: ISDN support (if you don't need it)
[/SIZE] [/INDENT][SIZE=2]Input device support[/SIZE][INDENT][SIZE=2]U: Touchscreen interface
/TouchScreens[/SIZE][INDENT][SIZE=2]U: Touchscreens
[/SIZE] [/INDENT][/INDENT][SIZE=2]Character Devices[/SIZE][INDENT][SIZE=2]U: everything you don't have
/Watchdog cards[/SIZE][INDENT][SIZE=2]U: Watch Dog Timer support
[/SIZE] [/INDENT][/INDENT][SIZE=2]Misc. Devices[/SIZE][INDENT][SIZE=2]U: Device Driver for IBM/RSA service drivers
[/SIZE] [/INDENT][SIZE=2]Video Capture Adapters[/SIZE][INDENT][SIZE=2]U: everything you don't have
/Radio Adapters[/SIZE][INDENT][SIZE=2]U: everything you don't have
[/SIZE] [/INDENT][SIZE=2]/Digital Video Broadcasting Devices[/SIZE][INDENT][SIZE=2]U: DVB for Linux
[/SIZE] [/INDENT][/INDENT][SIZE=2]Graphics support[/SIZE][INDENT][SIZE=2]U: everything you don't have
/Logo Configuration[/SIZE][INDENT][SIZE=2]S: Bootup Logo (and everything under it)
[/SIZE] [/INDENT][/INDENT][SIZE=2]File Systems[/SIZE][INDENT][SIZE=2]U: everything you are not going to use
/DOS/FAT/NT Filesystems[/SIZE][INDENT][SIZE=2]S: NTFS write support
[/SIZE] [/INDENT][SIZE=2]/Network File Systems[/SIZE][INDENT][SIZE=2]U: NFS file system support
U: NFS server support
U: NCP fle system support
U: Coda file system support
U: Andrews file system support
U: Plan 9 resource sharing support
[/SIZE] [/INDENT][SIZE=2]/Partition Types[/SIZE][INDENT][SIZE=2]U: Advances partition selection
[/SIZE] [/INDENT][SIZE=2]/Native Language Support[/SIZE][INDENT][SIZE=2]U: everything but your native language packages
[/SIZE] [/INDENT][/INDENT][SIZE=2]Instrumentation Support[/SIZE][INDENT][SIZE=2]U: Profiling Support
U: Kprobes
[/SIZE] [/INDENT][SIZE=2]Kernel Hacking[/SIZE][INDENT][SIZE=2]U: Show timing information on printks
U: Magic SysRq Key
U: Kernel Hacking
U: Debug Filesystem
U: Compile the kernel with frame unwind information[/SIZE][/INDENT][SIZE=2]
[/SIZE][SIZE=2]*Save and quit xconfig/qconf.*
```

sudo -s -H
make-kpkg clean
make-kpkg -initrd --revision=xxx kernel_image kernel_headers modules_image (xxx is whatever you choose)
cd ..
dpkg -i kernel_headers-x.x.x
dpkg -i kernel_image-x.x.x

```[/SIZE]

---

### Post by japurcell on 2006-10-24
I just compiled 2.6.18 last night ok and accidentally left out IP tables.  Can I edit the kernel without re-compiling it, and if so, how?  Thanks.

---

### Post by japurcell on 2006-10-24
Also if anyone can tell me how to re-enable the usplash, that would be great too!  Thanks!

---

### Post by moore.bryan on 2006-10-24
*afaik, you have to recompile... what's the issue with usplash?*

---

### Post by japurcell on 2006-10-24
I just have a blank black screen on bootup where usually the usplash would be. After that system boots fine.  When shutting down, I get a weird distorted graphic of some kind.  Tried sudo apt-get install usplash --reistall and still have same problem.  I also installed a new nvidia driver after the new kernel, so I don't know if that did it too.  Any ideas?

---

### Post by moore.bryan on 2006-10-26
> **japurcell said:**
> I just have a blank black screen on bootup where usually the usplash would be. After that system boots fine.  When shutting down, I get a weird distorted graphic of some kind.  Tried sudo apt-get install usplash --reistall and still have same problem.  I also installed a new nvidia driver after the new kernel, so I don't know if that did it too.  Any ideas?

[I]you might just need to specify "splash" in your kernel line in menu.lst.  if you edit your /boot/grub/menu.lst file so your kernel line has the word splash in it, that should solve your problems...
[/I]

---

### Post by veli on 2006-11-12
Hi, I just compililed 2.6.18 kernel with IP tables support, but it seems I've made a mistake somewhere in the networking section since firestarter complained about kernel didn't have IP tables support.

In the nttworking section there are so many inputs, so could you be more specific and give more details which options have to be enabled.

Anyway, quite usuful topic for me, only I need IP tables, for security I mean.

Thanks

---

### Post by moore.bryan on 2006-11-12
*all of the options which need to be enabled are listed above.  sometimes, and for unknown reasons, you have to compile several times to get iptables to work with 2.6.18.  I viewed it as good practice.*

---

### Post by veli on 2006-11-13
Thanks, I'll try again.

How about kernel 2.6.17? Have you tried it too, because I'm gonna compile 2.6.17 kernel to see if I'll get Ip tables.

---

### Post by veli on 2006-11-15
I got the IP tables working, after the second trial, :-)

---

### Post by moore.bryan on 2006-11-18
*i'm glad it worked out for you veli; for some unknown reason, iptables setup sometimes takes more than one compiling...*

---

