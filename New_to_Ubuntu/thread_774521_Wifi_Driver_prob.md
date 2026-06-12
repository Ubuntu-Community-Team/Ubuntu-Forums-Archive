---
title: "Wifi Driver prob"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by xBigJayx on 2008-04-29
I have installed the ubuntu 8.04 and i have a prob in my wifi Atheros 802.11 it is telling me that there is no open source driver for this hardware. now when i enter to hardware driver i find it with a tick on enable and it's written that it is in use. but when i enter to network i don't find "Wireless Network" i only find "wired networking" and modem sth...
i found the driver on the internet but it is not compiled. Now i'm very new in linux and i tried to compile it and install it but i had lot's of errors and access denied logs... 
could anyone plz help me even in telling me how to install it or in compiling the file for me so i can just double click it and install automatically...
thx in advance any help is appreciated....

this is the link of te driver [http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233&release_id=576121](http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233&release_id=576121)

---

### Post by phr0ze on 2008-04-29
Try typing Sudo before the command you are using to compile.

for example
sudo make wifi-driver

It will then ask for your password.

Thanks,
John

---

### Post by xBigJayx on 2008-04-29
jad@jad-laptop:~/Desktop/madwifi$ sudo make 
Checking requirements... ok. 
Checking kernel configuration... ok. 
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/jad/Desktop/madwifi modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic' 
  HOSTCC  /home/jad/Desktop/madwifi/ath_hal/uudecode 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c: In function 'uudecode_usage': 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c: At top level: 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:40: error: expected ')' before '*' token 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:70: error: expected ')' before '*' token 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c: In function 'main': 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:121: error: for each function it appears in.) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function) 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu' 
/home/jad/Desktop/madwifi/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose' 
make[3]: *** [/home/jad/Desktop/madwifi/ath_hal/uudecode] Error 1 
make[2]: *** [/home/jad/Desktop/madwifi/ath_hal] Error 2 
make[1]: *** [_module_/home/jad/Desktop/madwifi] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic' 
make: *** [modules] Error 2 





this is what i get try to compile the driver

---

### Post by xBigJayx on 2008-04-30
is there any other way to compile the driver?
like using the C++ compiler on windows to compile it and then using the compiled files to install the driver on linux:(?

---

