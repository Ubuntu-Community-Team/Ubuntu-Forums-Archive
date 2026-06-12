---
title: "Need help picking out a distro for laptop..."
date: 2008-08-21
forum: Other OS Talk
---

### Post by Sukido Nymira on 2008-08-21
Okay, I've been familiar with *NIX distros for at least 2 years now, but I've been using windows mostly throughout last year.

My laptop that I use frequently is an Acer Aspire 4315:
- Intel Celeron processor 530 (1.73GHz, 533MHz FSB, 1 MB L2 cache)
- 64 MB Mobile Intel Graphics Media Accelerator X3100 (Mobile Intel® 945GM Express Chipset Family)
- 512 MB DDR2 (I upgraded it to 1 GB)
- 80 GB HDD
- DVD/CD-RW combo
- 802.11b/g WLAN (Atheros-based)

I got it in February with windows vista home basic preinstalled and have been waiting for something to f*ck it over so i could switch it over to linux, and now it finally has.  I'm looking for a distro that comes with the latest WINE for those windows apps i can't let go and support for the graphics card (I've been using Second Life alot lol), and most important of all it MUST support the wireless card right out of the box (I ran linux mint 4.0 in livecd mode and couldn't seem to  get it to work, but backtrack 3 livecd supports it nicely).  I wouldn't mind a distro with some eyecandy either.  And I'm generally more comfy with Debian/Ubuntu-based distros, but I'm willing to try something new (PCLinuxOS is one of my favorite RPM distros) ;)

Anyone got any suggestions on what i should get?

---

### Post by c2olen on 2008-08-21
I've installed 08.04 on my wife's Acer 5315 with about the same specs a while ago.
All worked like a charm, except for the athereos wireless card. There was no support for it at that time.
I can recommend Ubuntu 08.04, since I am running it myself for quite some time now.
I am not using WINE though.

---

### Post by pro003 on 2008-08-21
ubuntu 8.04 is definitely my choice - wine works perfect, restricted drivers too, and bunch of things are improved, I felt it on myself ;-)

---

### Post by milasch on 2008-08-21
I've just installed 8.04 on my old N600c, P4 1.8 with 512MB RAM... Everything worked fine, even suspend (although I haven't tested if sound and USB work nice after resume).

I switched from opensuse to ubuntu recently, and found ubuntu's package manager is way more stable, faster and more reliable than any rpm based distro... my opinion, I'm not saying its better (before those 50 pages thread starts discussing this).

---

### Post by mikjp on 2008-08-21
> **Sukido Nymira said:**
> - - latest WINE for those windows apps i can't let go - - 

Which apps you mean?

openSUSE 11.0 is my favourite KDE4 based distribution, Ubuntu is my favourite GNOME distribution. Both are great.

mikko

---

### Post by raul_ on 2008-08-21
If you're familiar with Linux I would definitely recommend Arch Linux. I don't recommend it for beginners (Ubuntu and PCLinuxOS are good distros for that), but any more experience than that I always say "Arch".One of the advantages is that you make the system, so it can be as heavy or as light as you want, making it perfect for low specs. Be sure to check out reviews and stuff before you try it.

---

### Post by mips on 2008-08-21
> **raul_ said:**
> If you're familiar with Linux I would definitely recommend Arch Linux. I don't recommend it for beginners (Ubuntu and PCLinuxOS are good distros for that), but any more experience than that I always say "Arch".One of the advantages is that you make the system, so it can be as heavy or as light as you want, making it perfect for low specs. Be sure to check out reviews and stuff before you try it.

+1

But things are not going to "just work out of the box". You will have to build the box first.

---

### Post by wolfen69 on 2008-08-21
i have an acer travelmate with similar specs, and hardy runs great on it.

---

### Post by Sukido Nymira on 2008-08-24
i have a dual boot install with windows xp and ubuntu 8.04.1 now

the second life linux client runs with no problem, but no indications of anything wireless connections or wireless interfaces in the network manager???

---

### Post by DemonBob on 2008-08-25
Acer 5315, Ubuntu 8.10 Alpha4 works great :D

---

### Post by Sukido Nymira on 2008-08-25
> **DemonBob said:**
> Acer 5315, Ubuntu 8.10 Alpha4 works great :D

does that work with the wireless card?

---

### Post by DemonBob on 2008-08-25
I had to install the latest snapshot from madwifi.org. 

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)

Other then that everything worked.

---

### Post by MaxIBoy on 2008-08-25
WINE doesn't have to be a requirement for what distro you pick. What doesn't come bundled can be installed later. Except, of course, for Internet support. If that doesn't work out of the box, pick something else.

---

### Post by volkswagner on 2008-08-26
I must have a different card.

lspci:
```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

The above card has worked out of the box with most any distro I threw at it.  This includes Ubuntu Fiesty-Hardy.  I have used UE 1.6 and 1.8 so not sure if the wireless would be any different than vanilla Ubuntu versions.  Others I tried include, Slax, Puppy, and DSL.

The only distro that did not work was Insert linux.

---

### Post by Sukido Nymira on 2008-08-26
> **DemonBob said:**
> I had to install the latest snapshot from madwifi.org. 

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)

Other then that everything worked.


```
suki@ubuntu:~$ cd /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801
suki@ubuntu:~/Desktop/madwifi-hal-0.10.5.6-r3835-20080801$ export KERNELPATH=/usr/src/linux-headers-2.6.24-19-generic
suki@ubuntu:~/Desktop/madwifi-hal-0.10.5.6-r3835-20080801$ make cleanfor i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i clean; \
	done
make[1]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f modules.order .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath'
make[1]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal'
rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd
rm -f modules.order .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal'
make[1]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i clean; \
	done
make[2]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr'
make[2]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe'
make[2]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample'
make[2]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel'
rm -f modules.order
make[1]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate'
make[1]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/net80211'
make -C ./tools clean
make[1]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey core a.out
for d in ath_info; do \
		make -C $d clean; \
	done
make[2]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
rm -f *.o ath_info
make[2]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[1]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/tools'
rm -rf .tmp_versions
rm -f modules.order *.symvers svnversion.h
suki@ubuntu:~/Desktop/madwifi-hal-0.10.5.6-r3835-20080801$ make installChecking requirements... ok.
Checking kernel configuration... ok.
make -C /usr/src/linux-headers-2.6.24-19-generic SUBDIRS=/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.o
  CC [M]  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_radar.o
  CC [M]  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_hal_extensions.o
  CC [M]  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_pci.o
  LD [M]  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.o
  CC [M]  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ah_os.o
  HOSTCC  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c: At top level:
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c: In function 'main':
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode] Error 1
make[2]: *** [/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal] Error 2
make[1]: *** [_module_/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
suki@ubuntu:~/Desktop/madwifi-hal-0.10.5.6-r3835-20080801$ 
```

Could I get some help with how to go with installing it?  If not, I'm going to try OpenGEU

---

### Post by DemonBob on 2008-08-26
> **Sukido Nymira said:**
> ```
suki@ubuntu:~$ cd /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801
suki@ubuntu:~/Desktop/madwifi-hal-0.10.5.6-r3835-20080801$ export KERNELPATH=/usr/src/linux-headers-2.6.24-19-generic
suki@ubuntu:~/Desktop/madwifi-hal-0.10.5.6-r3835-20080801$ make cleanfor i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i clean; \
	done
make[1]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f modules.order .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath'
make[1]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal'
rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd
rm -f modules.order .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal'
make[1]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i clean; \
	done
make[2]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr'
make[2]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe'
make[2]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample'
make[2]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel'
rm -f modules.order
make[1]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate'
make[1]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/net80211'
make -C ./tools clean
make[1]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey core a.out
for d in ath_info; do \
		make -C $d clean; \
	done
make[2]: Entering directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
rm -f *.o ath_info
make[2]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[1]: Leaving directory `/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/tools'
rm -rf .tmp_versions
rm -f modules.order *.symvers svnversion.h
suki@ubuntu:~/Desktop/madwifi-hal-0.10.5.6-r3835-20080801$ make installChecking requirements... ok.
Checking kernel configuration... ok.
make -C /usr/src/linux-headers-2.6.24-19-generic SUBDIRS=/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.o
  CC [M]  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_radar.o
  CC [M]  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_hal_extensions.o
  CC [M]  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_pci.o
  LD [M]  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.o
  CC [M]  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ah_os.o
  HOSTCC  /home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c: At top level:
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c: In function 'main':
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode] Error 1
make[2]: *** [/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal] Error 2
make[1]: *** [_module_/home/suki/Desktop/madwifi-hal-0.10.5.6-r3835-20080801] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
suki@ubuntu:~/Desktop/madwifi-hal-0.10.5.6-r3835-28080001$ 
```

Could I get some help with how to go with installing it?  If not, I'm going to try OpenGEU

sudo apt-get install build-essential
cd to the madwifi-hal-0.10.5.6-r3835-20080801 directory
sudo make 
sudo make install

restart computer.

---

### Post by DemonBob on 2008-08-26
> **volkswagner said:**
> I must have a different card.

lspci:
```
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

The above card has worked out of the box with most any distro I threw at it.  This includes Ubuntu Fiesty-Hardy.  I have used UE 1.6 and 1.8 so not sure if the wireless would be any different than vanilla Ubuntu versions.  Others I tried include, Slax, Puppy, and DSL.

The only distro that did not work was Insert linux.




Yes i have: 

```
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

Which is the AR5007EG series, a little bit newer the code to support it was not officially released till after hardy was released.

Unofficially, Atheros released a temp patch for the card after gusty was released do to the EEE PC, the EEE uses the same chipset, Asus and Atheros was asked to release a patch for the people that installed thier own distro on them. Although that patch only support 32 bit arch only. Eventually they release a perminent fix for it.

I knew it was possible that the Acer Model he is asking about has an older chipset that is defaultly supported, just putting in my 2 cents on my acer model. In case it does have the newer model.

---

### Post by Sukido Nymira on 2008-08-27
> **DemonBob said:**
> sudo apt-get install build-essential
cd to the madwifi-hal-0.10.5.6-r3835-20080801 directory
sudo make 
sudo make install

restart computer.

downloading the build-essential package via windows...

---

