---
title: "noob needing wireless help"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by cberry78 on 2008-07-06
OK...yes I'm new to Ubuntu (and linux) so please be gentle.  And yes I've done some searching of the forums already and found the same issue and followed those directions.  And yes, i'm still having problems....:(

Here's the problem, I installed Ubuntu 8.04 on a Dell Inspiron 5100 and I cannot connect to the internet.  I'm using an Airlink101 PCMCIA Wireless card (AWLC3026) and I'm not getting any power to it at all.

I have downloaded *ndiswrapper* and followed the instructions (that's a problem too).  I have downloaded the correct driver that is recommended from 3com and have the .inf and .sys files.

Other people having similiar issues were instructed to post the results of the following commands: lshw -C Network, lspci, and iwconfig.  You can see my results below.

> lshw -C Network
 WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:b6:e3:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
 
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0

lspci
 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
 00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
 00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
 00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
 00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
 00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
 00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
 00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
 00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
 02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
 02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
 02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
 03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

iwconfig
 lo        no wireless extensions.

 eth0      no wireless extensions.


Now for my ndiswrapper issues.  I downloaded the latest version (1.53) and followed the instructions to unpack the tarball.  Changed to the ndiswrapper directory and followed the installation instructions and get this in response:

> make install
make -C driver install
make[1]: Entering directory `/home/chris/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic M=/home/chris/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
echo /lib/modules/2.6.24-16-generic/misc
/lib/modules/2.6.24-16-generic/misc
mkdir -p /lib/modules/2.6.24-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.24-16-generic/misc
/sbin/depmod -a 2.6.24-16-generic -b /
make[1]: Leaving directory `/home/chris/ndiswrapper-1.53/driver'
make -C utils install
make[1]: Entering directory `/home/chris/ndiswrapper-1.53/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:28: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/chris/ndiswrapper-1.53/utils'
make: *** [install] Error 2

And if I try and run ndiswrapper I get a message saying that ndiswrapper is currently not installed.

I guess that's all I can say.  If you need anymore information just let me know and any help would be appreciated.

Thanks.
Chris

---

### Post by ibuclaw on 2008-07-06
I think ndiswrapper comes installed by default in Ubuntu.

If not,
```
sudo apt-get install ndiswrapper-utils-1.9
```

Then cd to where the windows drivers are, then run
```
sudo ndiswrapper -i **filename**.inf
```

If you aren't too keen with the terminal yet, there is a ndiswrapper gtk app. I've never used it though.
```
sudo apt-get install ndisgtk
```
Then once your drivers are installed. Run
```
sudo modprobe ndiswrapper
```
And hopefully your card will turn on at the moment you run it.

Regards
Iain

---

### Post by cberry78 on 2008-07-06
Thanks for the quick reply....

*sudo apt-get ndiswrapper-utils-1.9* gives me this response....

> E: Invalid operation ndiswrapper-utils-1.9

*sudo apt-get install ndisgtk* gives me.....

> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndisgtk

---

### Post by Sealbhach on 2008-07-06
> **cberry78 said:**
> Thanks for the quick reply....

*sudo apt-get ndiswrapper-utils-1.9* gives me this response....

.

You should add "install"

```
sudo apt-get install ndiswrapper-utils-1.9
```


.

---

### Post by cberry78 on 2008-07-06
*sudo apt-get install ndiswrapper-utils-1.9* gives me this response:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndiswrapper-tils-1.9

---

### Post by Sealbhach on 2008-07-06
> **cberry78 said:**
> *sudo apt-get install ndiswrapper-utils-1.9* gives me this response:

OK, when I looked in my terminal it found it so that means you don't have some repository enabled. 

Check in System/Administration/Software sources that you have got the first four repos ticked and also the Third Party ones.


.

---

### Post by caljohnsmith on 2008-07-06
> **cberry78 said:**
> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndiswrapper-tils-1.9
"ndiswrapper-tils-1.9" should be "ndiswrapper-utils-1.9". Try instead to *copy and paste* the following command (don't just type it in the terminal as you are making some typos it appears):
```
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```
Note you will need both packages. Then do the following:
```
sudo ndiswrapper -i filename.inf    (like Tinivole said, and make sure you are in the directory where that file is located)
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```
Let us know if that gets your wireless working. And by the way, I have a wireless card that uses that exact same Libertas 88w8335 chip, and mine works great with ndiswrapper; yours should hopefully work just as well. :)

---

### Post by cariboo on 2008-07-06
There is a gui interface for ndiswrapper, seeing as you are coming from windows this might be easier. In System-->Administration--Synaptic Package Manager, search for **ndisgtk**, mark it for installation by right clicking on it, this will also mark the rest of the packages you need, click apply, click apply and wait for in to install. Once it is installed you should be able to find in in System-->Administration as wireless tools or something similar. Once you've got it up on your screen make sure you have your windows XP drivers handy, you will need the *.inf file. The rest should be pretty simple from there.

Jim

---

### Post by tafra7 on 2008-07-06
Hi

I too am  newbie to linux. I have the same wireless chipset.

I had success using the GUI ndisgtk as mentioned below. However I could not getthe wireless to work with the XP drivers. I found a suggestion on another forum to use the windows 2000 drivers and found this solved all my problems. The win2k drivers may be worth a go if you are still having problems.

tafra7

---

### Post by ludz on 2008-07-06
found this article at: [http://www.linuxforums.org/forum/debian-linux-help/54587-wireless-pcmcia-not-working-ubuntu.html](http://www.linuxforums.org/forum/debian-linux-help/54587-wireless-pcmcia-not-working-ubuntu.html)
which might help, in which someone wrote [I]"Both of you have pretty much the same options: Using ndiswrapper (which I have no experience with) or searching for a Linux driver for your specific adapter chipset. I've never had an experience with ndiswrapper, but many people say it's good (I went with the other suggestion and found the driver online, there's actually 2 driver's available for my chipset).

Either way, it might be a good idea to mention if the command "iwconfig" give you anything useful."[/I]


just a thought...

---

### Post by falcon61102 on 2008-07-06
I was just looking through your post because I have a similar chipset and had some problems getting it to connect as well.  I was able to get my driver installed but was unable to connect and it looks like you might run into the same problem.  Once you get your drivers installed if you run:
```
lshw -C Network
```

And it still says Module=SSB as it does here:
configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes

You may have to blacklist ssb to make sure ndiswrapper loads.  Once you get the driver installed, check that and if that be the case, it's an easy fix.

---

### Post by cberry78 on 2008-07-07
Thanks for the many suggestions and all your help, but still no luck.  :(

First off, any of my typos are because I'm using two machines, and anything I post of only a couple of lines I'm just reading off the Ubuntu machine as I type here on my Vista machine (yes, feel free to pity me).  Thanks for the thought though.

Second, in my Synaptic Package Manager, **ndisgtk** is not listed, so unfortunately that's no help.  Thanks though. :(

Third....under Software Sources, I do have the first 4 repos checked and the 2 third party ones as well, still no luck though (see below).

As far as this code:

*sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common*

I get the same response:
[I]Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9[/I]

That seems to be the pretty standard reply I get whenever I run an install related to ndiswrapper.

I do have the Win2k drivers for my Wireless card as well, and those don't work either, but I will see if I can track down a Linux driver, that would make things much easier apparently.

If there are any other suggestions please come forward with them.  I have run the ndiswrapper install program and uninstalled and tried it again and keep getting the same responses (see first post) on the install procedure.

As always, thanks again all of you for your help.

---

### Post by falcon61102 on 2008-07-07
Could it be that it's trying to find the package online instead of from your CD.  You may have to change it to search for packages on the CD instead of online.  You can do that through the package manager.

And I feel for you with Vista... I know your pain :).

---

### Post by cberry78 on 2008-07-07
> **falcon61102 said:**
> Could it be that it's trying to find the package online instead of from your CD.  You may have to change it to search for packages on the CD instead of online.  You can do that through the package manager.

And I feel for you with Vista... I know your pain :).

WOO HOO.....kinda

I enabled reading off the disk and it found ndisgtk...and I installed it with *sudo apt-get install ndisgtk*....and I get a whole new error message:

> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

So yeah....any other suggestions?  Please?  :)

---

### Post by RequinB4 on 2008-07-07
> **cberry78 said:**
> WOO HOO.....kinda

I enabled reading off the disk and it found ndisgtk...and I installed it with *sudo apt-get install ndisgtk*....and I get a whole new error message:



So yeah....any other suggestions?  Please?  :)

You need to close any other instances of apt you have open -- this includes but is not limited to 1) Synaptic package manager 2) Add/remove 3) terminal apt-get program 4) terminal aptitude program 5) update manager

Then retry the command

---

### Post by cberry78 on 2008-07-07
> **RequinB4 said:**
> You need to close any other instances of apt you have open -- this includes but is not limited to 1) Synaptic package manager 2) Add/remove 3) terminal apt-get program 4) terminal aptitude program 5) update manager

Then retry the command


OK....I closed everything out and even rebooted (Windows veteran, sorry).  I re-ran the apt-get and it worked...again....kinda.

I now have power to my Wireless card (which is a big step in the right direction) but I can't connect to the network still.  Running *lshw -C network* gives me:

> lshw -C Network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:b6:e3:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 03
       serial: 00:18:e7:05:96:bd
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8335x driverversion=1.53+3Com,05/19/2005,3.1.1.10 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


So....from a noob...what's next?  Thanks though all, for all your help.  :)

---

### Post by falcon61102 on 2008-07-07
Yeah, you have the same problem I had that I mentioned a few posts ago... you need to get rid of where it says Module=ssb in the 15th line (if I counted right) on the code you just posted.  You probably should blacklist ssb also. This can be accomplished by.
```
sudo gedit /etc/modprobe.d/blacklist
```
At the bottom of the file you want to put:
# Get rid of SSB
blacklist ssb
Save and Close Blacklist

Once you blacklisted SSB, you need to unload it from the Module 
```
sudo modprobe -r ssb
```
and put ndiswrapper in its place.
```
sudo modprobe ndiswrapper
```

Once that is complete you should be able to see your wireless access points.

---

### Post by cberry78 on 2008-07-07
OK I blacklisted ssb but when I go to unload the module I get the following message:  > FATAL: Module ssb is in use.

I check lshw -C Network again and I still have module=ssb on line 15 (same as before).

The Driver is installed, I made sure of that.  And I even have power to the Card now, even after I rebooted this morning, but still no Internet connection.  So what's keeping me from connecting?

Thanks, as always, for all your help.

---

### Post by falcon61102 on 2008-07-07
That ssb being loaded is what's keeping you from connecting.  I never ran into that problem.  There are a few good HOW TO's written up on using this card, let me see if I can't find the one that worked for me.  Did you try to unload the module after restarting?  Also, try this command instead:

```
sudo rmmod ssb
```

If that works, then:

```
sudo modprobe ndiswrapper
```

and you should be set.

Also, here are a couple of the links I looked at to help me find my way through this.  There wasn't one particular one that worked but I was able to get it working by researching and trying a few different methods.

[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
[http://ubuntuforums.org/showthread.php?t=835458](http://ubuntuforums.org/showthread.php?t=835458)
[http://ubuntuforums.org/showthread.php?t=828553](http://ubuntuforums.org/showthread.php?t=828553)

---

### Post by falcon61102 on 2008-07-07
I forgot to add something else.  Once you get ndiswrapper to load, you're going to want it to load everytime you start up.  You can do this by opening your modules file:
```
gksudo gedit /etc/modules
```

And adding the word ndiswrapper to the last line.  Save and Close.  Now once you restart, ndiswrapper will start every time.

Reference:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by cberry78 on 2008-07-07
WOOO-HOOOOO!!!!!!  I am writing this post from my Ubuntu machine.  We finally got it working!  Thank you all for helping, especially **falcon61102**!!!!

I'm honestly not sure which of the last two posts you sent me were what did it, but it was one of them.  Thanks again!!!!

:)

---

### Post by falcon61102 on 2008-07-07
LOL... well, glad I could help and I'm glad it's working for you.

---

### Post by cberry78 on 2008-07-09
SIGH!  OK...I shut down my Ubuntu machine last night and this morning when I logged on I had internet as well.  I left the computer on when I went to work and at sometime during the day my Ubuntu machine shut down (might have been a power surge, might have been the comp itself [was an issue I had with XP on it]), and now I don't have internet....again.

**lshw - C Network** shows: 
*module=ssb* (if you need the full list let me know)

**sudo rmmod sbb** tells me:
*ERROR: Module sbb does not exist in /proc/modules*

**sudo modprobe -r ssb** tells me:
*FATAL: Module ssb is in use.*

**sudo gedit /etc/modprobe.d/blacklist** has *blacklist sbb* as my last entry

**System => Administration => Network** is reading my network with 23% (which is the same as it was last night).

So.....any suggestions?  Please?

---

### Post by Sealbhach on 2008-07-09
> **falcon61102 said:**
> I forgot to add something else.  Once you get ndiswrapper to load, you're going to want it to load everytime you start up.  You can do this by opening your modules file:
```
gksudo gedit /etc/modules
```

And adding the word ndiswrapper to the last line.  Save and Close.  Now once you restart, ndiswrapper will start every time.

Reference:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Did you do this bit here?

Maybe nidswrapper didn't load on startup?

You could probably confirm by looking at Sessions from the System menu.

.

---

