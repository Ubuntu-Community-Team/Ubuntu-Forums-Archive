---
title: "Terminal command problem"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by lescarlin on 2008-10-27
I am trying to issue a series of commands via Terminal to get my atheros adaptor working.  The solution is tried and tested - i've used it before.  But on this occasion it gets stuck when the 'make'command is issued.  Strangely i've done this series of commands before on anther machine with a similar atheros problem, and it worked perfectly.  Here's the copy:

"@les-laptop:~$ wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
--09:39:15--  [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
           => `madwifi-ng-r2756+ar5007.tar.gz.6'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 485 [application/x-gzip]

100%[===========>] 485           --.--K/s        09:39:15 (30.36 MB/s) - `madwifi-ng-r2756+ar5007.tar.gz.6' saved [485/485]
@les-laptop:~$ sudo apt-get install build-essential
[sudo] password for l: 
Reading package lists... Done
Building dependency tree  
Reading state information... Done build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 263 not upgraded.
l
@les-laptop:~$ tar xfz madwifi-ng-r2756+ar5007.tar.gz
l
@les-laptop:~$ cd madwifi-ng-r2756+ar5007
l
@les-laptop:~/madwifi-ng-r2756+ar5007$
@les-laptop:~/madwifi-ng-r2756+ar5007$ make
make: *** No targets specified and no makefile found. Stop.
@les-laptop:~/madwifi-ng-r2756+ar5007$ sudo make install
make: *** No rule to make target `install'. Stop.
@les-laptop:~/madwifi-ng-r2756+ar5007$ sudo modprobe ath_pci
@les-laptop:~/madwifi-ng-r2756+ar5007$ sudo reboot

As you see everything goes swimmingly until  'make' is issued.

---

### Post by hyper_ch on 2008-10-27
(1) output of commands and commands and context of files should be put into [noparse]```

```[/noparse] brackets because that makes it simpler to read

(2) before running ```
make
```run```
./configure
```

---

### Post by lescarlin on 2008-10-28
> **hyper_ch said:**
> (1) output of commands and commands and context of files should be put into [noparse]```

```[/noparse] brackets because that makes it simpler to read

(2) before running ```
make
```run```
./configure
```

ok i tried what you suggested with same rsult, but maybe i didnt enter the commands correctly.  So here's the output of my various attempts:

l@les-laptop:~/madwifi-ng-r2756+ar5007$ ```
make
```
bash: ```
make
```: No such file or directory
l@les-laptop:~/madwifi-ng-r2756+ar5007$ [code make /code]
bash: [code: command not found
l@les-laptop:~/madwifi-ng-r2756+ar5007$ code
bash: code: command not found
l@les-laptop:~/madwifi-ng-r2756+ar5007$ code make
bash: code: command not found
l@les-laptop:~/madwifi-ng-r2756+ar5007$ ```

bash: [code]: command not found
l@les-laptop:~/madwifi-ng-r2756+ar5007$ ./configure
bash: ./configure: No such file or directory
l@les-laptop:~/madwifi-ng-r2756+ar5007$ [code]./configure
```
bash: ```
./configure
```: No such file or directory
l@les-laptop:~/madwifi-ng-r2756+ar5007$ ./configure
bash: ./configure: No such file or directory
l@les-laptop:~/madwifi-ng-r2756+ar5007$

---

### Post by wizard10000 on 2008-10-28
You've gotta run both configure and make from within the directory where configure and the makefile is, Les.

Good luck -

---

### Post by hyper_ch on 2008-10-28
yeah, both are required from within the actual folder and you first have to run
```

./configure

```
and then
```

make

```

and put all of the output in [noparse]```

```[/noparse] brackets (basically everything that's not for explanation in the thread) :)

You should get an output like this:
```

hyper@xubi:/home/svn/rtorrent/trunk/rtorrent$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
[...]
config.status: creating src/input/Makefile
config.status: creating src/rpc/Makefile
config.status: creating src/ui/Makefile
config.status: creating src/utils/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
hyper@xubi:/home/svn/rtorrent/trunk/rtorrent$

```
and then your run make
```

hyper@xubi:/home/svn/rtorrent/trunk/rtorrent$make

```
of course your output is different as you are compiling something else.

---

### Post by aeiah on 2008-10-28
if you cant find where your configure script is then in your madwifi directory, do ```
ls -R
```

and show us what's in there. perhaps its in a subdirectory or something that you'll have to navigate to, or perhaps you didnt untar it properly or something

---

### Post by lescarlin on 2008-10-28
> **aeiah said:**
> if you cant find where your configure script is then in your madwifi directory, do ```
ls -R
```

and show us what's in there. perhaps its in a subdirectory or something that you'll have to navigate to, or perhaps you didnt untar it properly or something

ok u asked :)  here's the result of ls -R:

l@les-laptop:~$ ls -R
.:
Desktop                              madwifi-ng-r2756+ar5007.tar.gz.4
Documents                            madwifi-ng-r2756+ar5007.tar.gz.5
Examples                             madwifi-ng-r2756+ar5007.tar.gz.6
madwifi-hal-0.10.5.6-current.tar.gz  madwifi-ng-r2756+ar5007.tar.gz.7
madwifi-hal-0.10.5.6-r3861-20080903  madwifi-ng-r2756+ar5007.tar.gz.8
madwifi-ng-r2756+ar5007              Music
madwifi-ng-r2756+ar5007.tar.gz       Pictures
madwifi-ng-r2756+ar5007.tar.gz.1     Public
madwifi-ng-r2756+ar5007.tar.gz.2     Templates
madwifi-ng-r2756+ar5007.tar.gz.3     Videos

./Desktop:
AtherosAr5007egTomXSOlution   atheros forUbuntuInstructions.txt
AtherosAr5007egTomXSOlution~  madwifi-ng-r2756+ar5007.tar.gz

./Documents:

./madwifi-hal-0.10.5.6-r3861-20080903:
ath            COPYRIGHT        Makefile         README      SNAPSHOT
ath_hal        hal              Makefile.inc     README.dfs  THANKS
ath_rate       include          Makefile.kernel  regression  tools
BuildCaps.inc  INSTALL          net80211         release.h
contrib        kernelversion.c  patch-kernel     scripts

./madwifi-hal-0.10.5.6-r3861-20080903/ath:
if_ath_ahb.c             if_ath_hal.h           if_ath_radar.c
if_ath_ahb.h             if_ath_hal_macros.h    if_ath_radar.h
if_ath.c                 if_ath_hal_wrappers.h  if_athvar.h
if_ath_debug.h           if_athioctl.h          Makefile
if_ath_hal_extensions.c  if_ath_pci.c           Makefile.kernel
if_ath_hal_extensions.h  if_ath_pci.h

./madwifi-hal-0.10.5.6-r3861-20080903/ath_hal:
ah_os.c     ah_os.h        Makefile         opt_ah.h
ah_osdep.h  ah_target.inc  Makefile.kernel  uudecode.c

./madwifi-hal-0.10.5.6-r3861-20080903/ath_rate:
amrr  Makefile  minstrel  onoe  sample

./madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/amrr:
amrr.c  amrr.h  Makefile  Makefile.kernel

./madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/minstrel:
Makefile  Makefile.kernel  minstrel.c  minstrel.h  minstrel.txt

./madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/onoe:
Makefile  Makefile.kernel  onoe.c  onoe.h

./madwifi-hal-0.10.5.6-r3861-20080903/ath_rate/sample:
Makefile  Makefile.kernel  sample.c  sample.h

./madwifi-hal-0.10.5.6-r3861-20080903/contrib:
madwifi.spec  madwifi.spec.in

./madwifi-hal-0.10.5.6-r3861-20080903/hal:
ah_desc.h  ah_devid.h  ah.h  ah_soc.h  COPYRIGHT  public  README  version.h

./madwifi-hal-0.10.5.6-r3861-20080903/hal/public:
alpha-elf.hal.o.uu          i386-elf.opt_ah.h          powerpc-le-eabi.inc
alpha-elf.inc               mips1-be-elf.hal.o.uu      powerpc-le-eabi.opt_ah.h
alpha-elf.opt_ah.h          mips1-be-elf.inc           sh4-le-elf.hal.o.uu
ap30.hal.o.uu               mips1-be-elf.opt_ah.h      sh4-le-elf.inc
ap30.inc                    mips1-le-elf.hal.o.uu      sh4-le-elf.opt_ah.h
ap30.opt_ah.h               mips1-le-elf.inc           sparc64-be-elf.hal.o.uu
ap43.hal.o.uu               mips1-le-elf.opt_ah.h      sparc64-be-elf.inc
ap43.inc                    mips-be-elf.hal.o.uu       sparc64-be-elf.opt_ah.h
ap43.opt_ah.h               mips-be-elf.inc            sparc-be-elf.hal.o.uu
ap51.hal.o.uu               mips-be-elf.opt_ah.h       sparc-be-elf.inc
ap51.inc                    mipsisa32-be-elf.hal.o.uu  sparc-be-elf.opt_ah.h
ap51.opt_ah.h               mipsisa32-be-elf.inc       wackelf.c
ap61.hal.o.uu               mipsisa32-be-elf.opt_ah.h  wisoc.hal.o.uu
ap61.inc                    mipsisa32-le-elf.hal.o.uu  wisoc.inc
ap61.opt_ah.h               mipsisa32-le-elf.inc       wisoc.opt_ah.h
arm9-le-thumb-elf.hal.o.uu  mipsisa32-le-elf.opt_ah.h  x86_64-elf.hal.o.uu
arm9-le-thumb-elf.inc       mips-le-elf.hal.o.uu       x86_64-elf.inc
arm9-le-thumb-elf.opt_ah.h  mips-le-elf.inc            x86_64-elf.opt_ah.h
armv4-be-elf.hal.o.uu       mips-le-elf.opt_ah.h       xscale-be-elf.hal.o.uu
armv4-be-elf.inc            powerpc-be-eabi.hal.o.uu   xscale-be-elf.inc
armv4-be-elf.opt_ah.h       powerpc-be-eabi.inc        xscale-be-elf.opt_ah.h
armv4-le-elf.hal.o.uu       powerpc-be-eabi.opt_ah.h   xscale-le-elf.hal.o.uu
armv4-le-elf.inc            powerpc-be-elf.hal.o.uu    xscale-le-elf.inc
armv4-le-elf.opt_ah.h       powerpc-be-elf.inc         xscale-le-elf.opt_ah.h
i386-elf.hal.o.uu           powerpc-be-elf.opt_ah.h
i386-elf.inc                powerpc-le-eabi.hal.o.uu

./madwifi-hal-0.10.5.6-r3861-20080903/include:
compat.h  sys

./madwifi-hal-0.10.5.6-r3861-20080903/include/sys:
queue.h

./madwifi-hal-0.10.5.6-r3861-20080903/net80211:
ieee80211_acl.c          ieee80211_linux.h     ieee80211_scan.h
ieee80211_beacon.c       ieee80211_monitor.c   ieee80211_scan_sta.c
ieee80211.c              ieee80211_monitor.h   ieee80211_skb.c
ieee80211_crypto.c       ieee80211_node.c      ieee80211_skb.h
ieee80211_crypto_ccmp.c  ieee80211_node.h      ieee80211_var.h
ieee80211_crypto.h       ieee80211_output.c    ieee80211_wireless.c
ieee80211_crypto_none.c  ieee80211_power.c     ieee80211_xauth.c
ieee80211_crypto_tkip.c  ieee80211_power.h     if_athproto.h
ieee80211_crypto_wep.c   ieee80211_proto.c     if_ethersubr.h
ieee80211_debug.h        ieee80211_proto.h     if_llc.h
_ieee80211.h             ieee80211_radiotap.h  if_media.c
ieee80211.h              ieee80211_rate.c      if_media.h
ieee80211_input.c        ieee80211_rate.h      Makefile
ieee80211_ioctl.h        ieee80211_scan_ap.c   Makefile.kernel
ieee80211_linux.c        ieee80211_scan.c

./madwifi-hal-0.10.5.6-r3861-20080903/patch-kernel:
Config.in  Configure.help.patch  install.sh  Kconfig  README

./madwifi-hal-0.10.5.6-r3861-20080903/regression:
ccmp  Makefile  tkip  wep

./madwifi-hal-0.10.5.6-r3861-20080903/regression/ccmp:
Makefile  test_ccmp.c

./madwifi-hal-0.10.5.6-r3861-20080903/regression/tkip:
Makefile  test_tkip.c

./madwifi-hal-0.10.5.6-r3861-20080903/regression/wep:
Makefile  test_wep.c

./madwifi-hal-0.10.5.6-r3861-20080903/scripts:
find-madwifi-modules.sh  hal_unmangle.sed         make-release.bash
get_arch.mk              if_ath_hal_generator.pl  update_hal_unmangle
hal_unmangle_log         madwifi-indent
hal_unmangle.objcopy     madwifi-unload

./madwifi-hal-0.10.5.6-r3861-20080903/tools:
80211debug.c  athctrl.c   athkey.c    man              wpakey.c
80211stats.c  athdebug.c  athstats.c  wireless_copy.h
athchans.c    ath_info    Makefile    wlanconfig.c

./madwifi-hal-0.10.5.6-r3861-20080903/tools/ath_info:
ath_info.8  ath_info.c  Makefile  README

./madwifi-hal-0.10.5.6-r3861-20080903/tools/man:
80211debug.8  athchans.8  athdebug.8  athstats.8
80211stats.8  athctrl.8   athkey.8    wlanconfig.8

./madwifi-ng-r2756+ar5007:
README

./Music:

./Pictures:

./Public:

./Templates:

---

