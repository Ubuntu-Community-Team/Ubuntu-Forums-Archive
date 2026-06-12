---
title: "[SOLVED] Wireless problem on acer"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by causeitsme on 2008-04-28
Hi, 

I just installed Ubuntu 8.04 on my laptop as a dualboot with Vista.
I can't get online. I see in my Hardware Drivers window that the wireless card is enabled and in use. It isn't finding my wireless router apparently. I have been searching and found one site that I thought might help but it went to a dead link about halfway through the process.

I was here
[http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html]("http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html") and installed the three packages: ndisgtk , ndiswrapper-common , and ndiswrapper-utils .

Later on down the page is where I hit the dead end. I went to the page referred to find my driver and I found a link to it but it wasn't valid. 

So, I'm now at a loss, any help would be greatly appreciated. I've never used Ubuntu before, only windows, so I'm really at a loss as to what's going on here for the most part.

Computer info:
Acer Aspire 5100 notebook
AMD Turion 64 x2
1.5 gig memory
Atheros wireless card

P.S. This is what my Hardware Drivers window says.... [IMG][[img=http://img142.imageshack.us/img142/2893/screenshotow1.th.png]](http://img142.imageshack.us/my.php?image=screenshotow1.png)[/IMG]

---

### Post by Anduu on 2008-04-28
[http://ubuntuforums.org/showthread.php?t=662877&highlight=atheros+hardy](http://ubuntuforums.org/showthread.php?t=662877&highlight=atheros+hardy)

This is the how-to I used to get the Atheros card on my Acer working.

---

### Post by causeitsme on 2008-05-03
Thanks Anduu, 

I tried the link you sent and went through the steps.

I first did the "build essential" thing and got this...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

So, I didn't know what that was so moved on and did the next step and got this...

bobby@bobby-laptop:~$ cd /home/bobby/Desktop
bobby@bobby-laptop:~/Desktop$ tar xfz madwifi-ng-r2756+ar5007.tar.gz
bobby@bobby-laptop:~/Desktop$ cd madwifi-ng-r2756+ar5007
bobby@bobby-laptop:~/Desktop/madwifi-ng-r2756+ar5007$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/bobby/Desktop/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath/if_ath.o
  CC [M]  /home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath/if_ath_pci.o
  LD [M]  /home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath/ath_pci.o
  CC [M]  /home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/ah_os.o
  HOSTCC  /home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: At top level:
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'main':
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode] Error 1
make[2]: *** [/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal] Error 2
make[1]: *** [_module_/home/bobby/Desktop/madwifi-ng-r2756+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2


Seems that didn't work either but, I moved on and did this....

bobby@bobby-laptop:~/Desktop/madwifi-ng-r2756+ar5007$ sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/bobby/Desktop/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  HOSTCC  /home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: At top level:
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c: In function 'main':
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal/uudecode] Error 1
make[2]: *** [/home/bobby/Desktop/madwifi-ng-r2756+ar5007/ath_hal] Error 2
make[1]: *** [_module_/home/bobby/Desktop/madwifi-ng-r2756+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2



I hope that's not too much for one thread. Sorry if it is. 

So, I don't know what is happening with all that. I was thinking about re-installing but, I don't know if that will help.

Any help would still be greatly appreciated!

---

### Post by Anduu on 2008-05-03
Open up Synaptic and make sure the universe and multiverse repos are activated...you should then be able to install build_essential.

All those errors you are getting are because build_essential isnt present.

---

### Post by lazydesi on 2008-05-03
hey did u done this step before installing

UNCHECK Atheros Hardware Abstraction Layer (HAL)

just middle one

---

### Post by causeitsme on 2008-05-03
> **lazydesi said:**
> hey did u done this step before installing

UNCHECK Atheros Hardware Abstraction Layer (HAL)

just middle one

Hi,

Yes, I did that. I couldn't get anything to work so, I reinstalled Ubuntu 8.04 and started over, I finally figured out what Anduu meant with the Synaptic and was able to get build-install to install and then everything seemed great. Terminal accepted all the commands and didn't give any error codes. 

On the downside.... It didn't work. My wireless still doesn't work. I opened up Devices - Network Tools and I see this there.....
[IMG][[IMG]http://img387.imageshack.us/img387/4269/devicesnetworktools2yc3.th.jpg[/IMG]](http://img387.imageshack.us/my.php?image=devicesnetworktools2yc3.jpg)[/IMG]
[IMG][[IMG]http://img166.imageshack.us/img166/1373/screenshotdevicesnetworej6.th.jpg[/IMG]](http://img166.imageshack.us/my.php?image=screenshotdevicesnetworej6.jpg)[/IMG]

If you notice on the pic that shows 'unknown device (wifi0) it shows received bytes and packets I don't really understand how or why, but, there you go.

By the way, should I recheck the Atheros Hardware Abstraction Layer (HAL) once all the steps were done? I didn't but it just occurred to me that maybe I should.

---

### Post by errold32 on 2008-05-04
What kind of atheros card do you have? I have an atheros wifi card, and it worked with the live cd using the atheros proprietary drivers. 
8.04 LTS

---

### Post by tashmooclam on 2008-05-04
If you want to forget your problems, see if Intel makes a wireless card for your computer. Then, get one for $25 and you'll be all set. I found using a screwdriver for 15 minutes much more effective than reading endless threads with links to other threads. Other people may disagree. There is a reason that Dell uses an Intel wireless card in the Ubuntu laptops it sells.

---

### Post by causeitsme on 2008-05-04
> **errold32 said:**
> What kind of atheros card do you have? I have an atheros wifi card, and it worked with the live cd using the atheros proprietary drivers. 
8.04 LTS

It's an ar2413, I got the madwifi download from here [http://www.atheros.cz/](http://www.atheros.cz/)
Then applied the steps listed but used the one that atheros.cz listed as correct for me instead of the one in the tutorial thread.

---

### Post by causeitsme on 2008-05-04
> **tashmooclam said:**
> If you want to forget your problems, see if Intel makes a wireless card for your computer. Then, get one for $25 and you'll be all set. I found using a screwdriver for 15 minutes much more effective than reading endless threads with links to other threads. Other people may disagree. There is a reason that Dell uses an Intel wireless card in the Ubuntu laptops it sells.

That may just be what I'll do, I have been fiddling around with this for days. One good thing though, I have learned some cool things about Ubuntu from this experience. Good advice though. I was wondering if the ndiswrapper thing I heard about would work though.

---

### Post by ndo on 2008-05-11
Oh my god - someone please help a brother out. 

I'm in Kuwait, Windows crapped out on me, had no restore, long and short - installed Hardy Heron 8.04 for AMD 64 (I, too, have the Acer Despisre 5100, with the Atheros AR5700eg card in it).

I'm really glad to have a functioning operating system, which allows me to USE my computer again. The bad part is, I can't get many things to work, the wireless being just one. 

Can someone please clarify what Synaptic is and how to make sure you have Universe and Multiverse repositories enabled? I opened up Synaptic, there are 24,555 packages to search through? Just like the infomercials say, "there's got to be a better WAY!"

I'm trying the obvious ndiswrapper thing first, because frankly, thats the only route I understand, having never used linux in my life (thus rendering all the info posted in these boards way beyond my understanding). But if someone could school me as to how Synaptic should look, I'll try the link above and see if that will work.

Thanks in advance to anyone cool enough to help - its appreciated.

---

