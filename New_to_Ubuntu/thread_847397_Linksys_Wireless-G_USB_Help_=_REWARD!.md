---
title: "Linksys Wireless-G USB Help = REWARD!"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Barnetto on 2008-07-02
Here the story. Its been about a year now i first downloaded ubuntu. I always thought that it would be such a good thing to have and learn. At the momment i have Ubuntu 8.04 installed on my desktop. The problem is I cant get my wireless adapter to work! Ive been trying and trying over the year to do this with not just one adapter but 3! I get frustrated try to install it and i never really get anywhere! I would love to use ubuntu if only my internet work and i cant stand switching between xp and ubuntu for internet. What im looking for is someone to help me install my apater for good! My linux skills are at a low and my install of ubuntu is fresh. Step by step guide would be good :). 
Important information:

Ubuntu 8.04
Linksys Wireless-G USB Network Adapter (with SpeedBooster) WUSB45GS Ver 2.1

REWARD: A small amount with be given to the persons paypal who helps and is succesful in getting me on the internet. 

Thanks!

---

### Post by snowpine on 2008-07-02
Hi Barnetto, 
It is really easy if you follow the instructions in the first post of this thread: [http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

Then, install wicd following the instructions here: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

(note: the correct driver for you is most likely 'rt2500usb')

I have the WUSB54G v4 and this worked perfectly for me. Installing wicd is optional but I like it better than the default Ubuntu network-manager.

---

### Post by prshah on 2008-07-02
> **Barnetto said:**
> 
At the momment i have Ubuntu 8.04 installed on my desktop. The problem is I cant get my wireless adapter to work! 


Why not try my (solved) step-by-step guide at [http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260) ? Post back here if you run into trouble.

---

### Post by Barnetto on 2008-07-02
No luck :(

Ive got as far as installing ndiswrapper (i think) and installed the wusb54gsv2 driver (i think) 

i ndiswrapper -l and get:

wusb54gsv2 : driver installed
        device (13B1 : 0014) present

this means its installed? But on the network settings i have no wireless icons or anything just the wired and ptp connections...

Anymore guides?

Barnetto

---

### Post by snowpine on 2008-07-02
> **Barnetto said:**
> No luck :(

Ive got as far as installing ndiswrapper (i think) and installed the wusb54gsv2 driver (i think) 

i ndiswrapper -l and get:

wusb54gsv2 : driver installed
        device (13B1 : 0014) present

this means its installed? But on the network settings i have no wireless icons or anything just the wired and ptp connections...

Anymore guides?

Barnetto

Did you install wicd like I suggested?

Edit: And did you reboot? :)

---

### Post by snowpine on 2008-07-02
Another application I can suggest if wicd doesn't work for you is called 'rutilt' (sudo apt-get install rutilt). I was never able to get my Linksys 54G working right with Ubuntu's network manager, but both wicd and rutilt solved the problem. I like wicd better because it can auto-connect easily to my preferred network.

I think you are almost there! The output of ndiswrapper -l is encouraging. Good luck!

---

### Post by Barnetto on 2008-07-02
[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547) the one you gave and i used this one [http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206) for abit of guidence too! 

also when I: sudo modprobe ndiswrapper
i get
FATAL: Module ndiswrapper not found if this helps?

Barnetto

---

### Post by snowpine on 2008-07-02
> **Barnetto said:**
> [http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547) the one you gave and i used this one [http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206) for abit of guidence too! 

also when I: sudo modprobe ndiswrapper
i get
FATAL: Module ndiswrapper not found if this helps?

Barnetto

Hi Barnetto, sorry my method did not work for you. It worked perfectly for me with WUSB54Gv4, but I guess WUSB54GSv2.1 is a little different. :(

I would recommend that you pick one method and follow it methodically, step by step. For example, if you get a fatal error when you sudo modprobe ndiswrapper, STOP and try to fix that before skipping ahead to ndiswrapper -l. Also, if you are mixing and matching from different peoples' threads, that will cause problems. :)

Good luck, I know you can do it! I had to try several imperfect solutions before I found the perfect solution (ndiwrapper+wicd).

ps There is also another solution that doesn't use ndiswrapper at all. It worked for me, however, I could not use roaming mode.  You can read about it here: [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)

---

### Post by Barnetto on 2008-07-02
Okay, Wicd is install but im going to unistall ndiswrapper, am i right in thinking that the line to remove ndiswrapper is:
sudo make uninstall

?

i think im getting the use to this linux stuff :)

i will the new method and get back to you!



Barnetto

---

### Post by Barnetto on 2008-07-02
reinstall ndiswrapper ive noticed soemthing.

wen i come to compile and then install the new ndiswrapper with:

make
and
sudo make install

i get this:

make:
mike@mike-desktop:~/ndiswrapper-1.53$ make
make -C driver
make[1]: Entering directory `/home/mike/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic M=/home/mike/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: Leaving directory `/home/mike/ndiswrapper-1.53/driver'
make -C utils
make[1]: Entering directory `/home/mike/ndiswrapper-1.53/utils'
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
loadndisdriver.c:71: warning: initialisation makes pointer from integer without a cast
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
make[1]: Leaving directory `/home/mike/ndiswrapper-1.53/utils'
make: *** [all] Error 2

and for sudo make install:

mike@mike-desktop:~/ndiswrapper-1.53$ sudo make install
make -C driver install
make[1]: Entering directory `/home/mike/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic M=/home/mike/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
echo /lib/modules/2.6.24-16-generic/misc
/lib/modules/2.6.24-16-generic/misc
mkdir -p /lib/modules/2.6.24-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.24-16-generic/misc
/sbin/depmod -a 2.6.24-16-generic -b /
make[1]: Leaving directory `/home/mike/ndiswrapper-1.53/driver'
make -C utils install
make[1]: Entering directory `/home/mike/ndiswrapper-1.53/utils'
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
loadndisdriver.c:71: warning: initialisation makes pointer from integer without a cast
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
make[1]: Leaving directory `/home/mike/ndiswrapper-1.53/utils'
make: *** [install] Error 2
mike@mike-desktop:~/ndiswrapper-1.53$ sudo ndiswrapper -m
sudo: ndiswrapper: command not found
mike@mike-desktop:~/ndiswrapper-1.53$ sudo ndiswrapper -m
sudo: ndiswrapper: command not found
mike@mike-desktop:~/ndiswrapper-1.53$


alot of errors there :S


Barnetto

---

### Post by Tom--d on 2008-07-02
Do not compile. 

Just download the .deb files off packages.ubuntu.com

---

### Post by Barnetto on 2008-07-02
cant find any .deb files on there?

link?

Barnetto

---

### Post by tjwallace on 2008-07-02
[http://packages.ubuntu.com/hardy/ndiswrapper-common](http://packages.ubuntu.com/hardy/ndiswrapper-common)
[http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9)
And a GUI if you wanted: [http://packages.ubuntu.com/hardy/ndisgtk](http://packages.ubuntu.com/hardy/ndisgtk)

---

### Post by prshah on 2008-07-03
> **Barnetto said:**
> 
sudo modprobe ndiswrapper
i get
FATAL: Module ndiswrapper not found if this helps?



You've probably skipped the command ```
ndiswrapper -m
```

From your past messages, it is not clear where you are stuck. Please post back output of whichever command you feel is not working correctly (compare with outputs given in the guide). Until "modprobe ndiswrapper" works, your wireless card will not be activated.

---

### Post by kevdog on 2008-07-03
Can I get a reward?

---

### Post by lincoln32 on 2008-07-03
i just set several computers with fresh Ubuntu 8.04 and found wusb54g v4 will install automatic and ver 2 used a complete different internal chipset
so i just swapped to ver4 several other computers have a broadcom or intell
chip set and were found and updated after updates done on lan then in about 20 min a green notice popped up to install drivers and read carefully and check to install a second window comes up to install second file to install
ndiswrapper should work but hard to figure out you might want to try a different adapter and run on the LAN a while. ndiswrapper will adapt windows drivers to work on Ubuntu system. But will be worth all the work when done. Stick with It

---

### Post by Barnetto on 2008-07-03
Still no luck :(

and i cant ever seem to find the right guides.


I need a step by step guide on installing ndiswrapper (without internet connection) and then finding the right driver for the wusb54gsv2 driver and installing it with ndiswrapper and then configuring ndiswrapper and driver to actually work!

would like to say the a reward is still there is someone canm forfill my needs as i will be willing to pay money as this is getting so annoying!!!! 




Barnetto

---

### Post by Barnetto on 2008-07-09
anyone?

---

### Post by youthforlinux on 2008-07-09
My cousin had the WUSB54GC which now works natively in Hardy, but before he had similar problems and no internet connection.  Here's how we did it--mind you completely over the phone...

the ndiswrapper packages are also on your installation CD.
heres wat u can do to just get them off of said cd.

for now to to make this easy we're gonna have the cd as the only repository to do this:

first we wanna make a backup

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

then we wanna edit the file to our liking

```
gksudo gedit /etc/apt/sources.list
```

then gedit will open up to edit the repository list

delete the whole contents of the file

then add this

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted

to the first line of the file


also just an add-on to that....your repository file sources.list should actually already have the cd repository listed you want to delete everything except for that line and make sure that a comment is not before it...a comment is a # sign...if it's there then that repository will be ignored....


then run this in the terminal

```
sudo aptitude update
```

make sure that the cd is in before you run that command

then you want to install ndiswrapper using this command

```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```

that should install ndiswrapper from the cd
to undo the changes to your repository list run:

```
sudo cp /etc/apt/sources.list.backup /etc/apt/sources.list
```

then ndiswrapper should be able to install your wireless driver...so at least u'll have ndiswrapper properly installed here

---

### Post by youthforlinux on 2008-07-09
ill take a look at finding the right driver tho it should be on ur installation disk for ur wireless card in windows...you should be able to find it off of that disk

---

### Post by youthforlinux on 2008-07-09
then you need to make sure that the wrong drivers are blacklisted...sadly.... do an ```
ifconfig
``` to see if anything shows up other than lo as a device and if there is you need to blacklist i don't know which one is the right one so heres a lot of code:

```

echo 'blacklist rt2500usb' | sudo tee -a /etc/modprobe.d/blacklist 
echo 'blacklist rt73usb' | sudo tee -a /etc/modprobe.d/blacklist 
echo 'blacklist rt61usb' | sudo tee -a /etc/modprobe.d/blacklist 
echo 'blacklist rt2x00usb' | sudo tee -a /etc/modprobe.d/blacklist
```

try each of these separately to see if they get rid of rausb0 or watever shows up

well if you have trouble with that wireless windows disk you can find the driver online here at:

[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859844514&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4451461879B396&displaypage=download#versiondetail]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859844514&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4451461879B396&displaypage=download#versiondetail")

save that to i guess your windows partition then copy it over to linux
then
```

unzip WUSB54GSv2_20050510.exe
``` 

```
cd WUSB54GSv2_20050510/
cd Drivers
```
```

sudo ndiswrapper -i WUSB54GSv2.inf
```
```

sudo depmod -a
sudo modprobe ndiswrapper

sudo ndiswrapper -m 
```
```

ndiswrapper -l
```

should tell you if it installed

then
```

echo 'ndiswrapper' | sudo tee -a /etc/modules 
```

to add ndiswrapper to startup

then restart the computer and look to see if network manager can find you network

hope this all works!!!!

---

### Post by ubume2 on 2008-07-09
I had a Linksys WUSB54g v4 while I had 6.06 installed. I then upgraded to 8.04.  This howto on how to install rt2500 for Dapper worked in hardy also. You need to read through the whole thread because there are some essential commands missing in the first post.

[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

I have not used this, but it might be helpful:

[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

This one is more recent. I have not used it, though.

[http://ge.ubuntuforums.com/showthread.php?t=564419](http://ge.ubuntuforums.com/showthread.php?t=564419)

I could not use network manager on either Dapper or Hardy.  I had to put the commands that you would enter manually on the command line, into /etc/rc.local.  This enabled wireless connection on bootup.  I had the same problem with WICD on Hardy.

This is a good one on how to manually configure networks.

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by youthforlinux on 2008-07-09
If you're williing to pay people for helping you and if your having that much of a problem it might not be a bad idea to purchase a new wireless adapter that works natively.  It will save you the time and trouble and will allow you to start really delving into the world of linux....as i posted before my cousin got the Linksys WUSB54GC and now that works out of the box in hardy....its a USB stick configuration with a USB extension cord for desktops....maybe worth looking into.....

---

### Post by El Viejo Lobo on 2008-07-10
Your case reminds me Broadcom wireless problems from long time ago.
I can recomand you to google the issue. I made some for you.  

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/ubuntu-linux-and-linksys-wireless-g-portable-usb-adapter-wusb54gp-problems-462105/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/ubuntu-linux-and-linksys-wireless-g-portable-usb-adapter-wusb54gp-problems-462105/)

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/ubuntu-linux-and-linksys-wireless-g-portable-usb-adapter-wusb54gp-problems-462105/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/ubuntu-linux-and-linksys-wireless-g-portable-usb-adapter-wusb54gp-problems-462105/)

One more thing is, No  $ rewards in Ubuntu Forum Just thanks.

---

