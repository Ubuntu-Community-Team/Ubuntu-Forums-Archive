---
title: "PSP toolchain Compile Issues"
date: 2008-11-18
forum: Packaging and Compiling Programs
---

### Post by ironslave on 2008-11-18
Okay, I am trying to Install a Dev system for the PSP on my Ibex Install, but when i get about 10 Minutes into the Compile the system gets Buffer overflow errors and bails out.

here is my Output when things start going wrong. 
```
objects="_gcov.o _gcov_merge_add.o _gcov_merge_single.o _gcov_merge_delta.o _gcov_fork.o _gcov_execl.o _gcov_execlp.o _gcov_execle.o _gcov_execv.o _gcov_execvp.o _gcov_execve.o _gcov_interval_profiler.o _gcov_pow2_profiler.o _gcov_one_value_profiler.o _gcov_indirect_call_profiler.o _gcov_average_profiler.o _gcov_ior_profiler.o _gcov_merge_ior.o";                             \
        if test -z "$objects"; then                             \                                                                                                                            
          echo 'int __libgcc_eh_dummy;' > eh_dummy.c;           \                                                                                                                            
          /home/james/tmp/psptoolchain/build/gcc-4.3.2/build-psp/./gcc/xgcc -B/home/james/tmp/psptoolchain/build/gcc-4.3.2/build-psp/./gcc/ -B/usr/local/pspdev/psp/bin/ -B/usr/local/pspdev/psp/lib/ -isystem /usr/local/pspdev/psp/include -isystem /usr/local/pspdev/psp/sys-include -O2 -g -g -O2 -O2  -O2 -g -g -O2   -DIN_GCC -DCROSS_DIRECTORY_STRUCTURE   -W -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wold-style-definition  -isystem ./include  -G 0 -g  -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED -Dinhibit_libc  -I. -I. -I../.././gcc -I../../../libgcc -I../../../libgcc/. -I../../../libgcc/../gcc -I../../../libgcc/../include  -DHAVE_CC_TLS  -c eh_dummy.c         \                                                                            
             -o eh_dummy.o;                             \                                                                                                                                    
          objects=eh_dummy.o;                           \                                                                                                                                    
        fi;                                                     \                                                                                                                            
        /usr/local/pspdev/psp/bin/ar  rc libgcov.a $objects                                                                                                                                  
*** buffer overflow detected ***: /usr/local/pspdev/psp/bin/ar terminated                                                                                                                    
======= Backtrace: =========                                                                                                                                                                 
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0x40132558]                                                                                                                                
/lib/tls/i686/cmov/libc.so.6[0x40130680]                                                                                                                                                     
/lib/tls/i686/cmov/libc.so.6[0x4012fd68]                                                                                                                                                     
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0xc8)[0x400a5a18]                                                                                                                            
/lib/tls/i686/cmov/libc.so.6(_IO_padn+0xed)[0x40098e0d]                                                                                                                                      
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x27cf)[0x4007a15f]                                                                                                                                
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xa7)[0x4012fe17]                                                                                                                                
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x4012fd5d]                                                                                                                                 
/usr/local/pspdev/psp/bin/ar[0x80512e2]                                                                                                                                                      
/usr/local/pspdev/psp/bin/ar[0x804f2db]                                                                                                                                                      
/usr/local/pspdev/psp/bin/ar[0x8052158]                                                                                                                                                      
/usr/local/pspdev/psp/bin/ar[0x8059e98]                                                                                                                                                      
/usr/local/pspdev/psp/bin/ar[0x804b8f5]                                                                                                                                                      
/usr/local/pspdev/psp/bin/ar[0x804c690]                                                                                                                                                      
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0x4004e685]                                                                                                                             
/usr/local/pspdev/psp/bin/ar[0x80496e1]                                                                                                                                                      
======= Memory map: ========                                                                                                                                                                 
08048000-080c5000 r-xp 00000000 08:05 1360527    /usr/local/pspdev/psp/bin/ar                                                                                                                
080c5000-080c6000 r--p 0007c000 08:05 1360527    /usr/local/pspdev/psp/bin/ar                                                                                                                
080c6000-080c7000 rw-p 0007d000 08:05 1360527    /usr/local/pspdev/psp/bin/ar                                                                                                                
080c7000-080cb000 rw-p 080c7000 00:00 0                                                                                                                                                      
0826d000-08318000 rw-p 0826d000 00:00 0          [heap]                                                                                                                                      
40000000-4001a000 r-xp 00000000 08:05 278806     /lib/ld-2.8.90.so                                                                                                                           
4001a000-4001b000 r-xp 4001a000 00:00 0          [vdso]                                                                                                                                      
4001b000-4001c000 r--p 0001a000 08:05 278806     /lib/ld-2.8.90.so                                                                                                                           
4001c000-4001d000 rw-p 0001b000 08:05 278806     /lib/ld-2.8.90.so                                                                                                                           
4001d000-4001f000 rw-p 4001d000 00:00 0                                                                                                                                                      
4001f000-40020000 r--p 00000000 08:05 1319619    /usr/lib/locale/en_CA.utf8/LC_MESSAGES/SYS_LC_MESSAGES                                                                                      
40020000-40027000 r--s 00000000 08:05 1302665    /usr/lib/gconv/gconv-modules.cache                                                                                                          
40027000-40031000 rw-p 40027000 00:00 0                                                                                                                                                      
40038000-40190000 r-xp 00000000 08:05 295439     /lib/tls/i686/cmov/libc-2.8.90.so                                                                                                           
40190000-40192000 r--p 00158000 08:05 295439     /lib/tls/i686/cmov/libc-2.8.90.so                                                                                                           
40192000-40193000 rw-p 0015a000 08:05 295439     /lib/tls/i686/cmov/libc-2.8.90.so                                                                                                           
40193000-40197000 rw-p 40193000 00:00 0                                                                                                                                                      
40197000-401d6000 r--p 00000000 08:05 1319610    /usr/lib/locale/en_CA.utf8/LC_CTYPE                                                                                                         
401ef000-401fc000 r-xp 00000000 08:05 278597     /lib/libgcc_s.so.1                                                                                                                          
401fc000-401fd000 r--p 0000c000 08:05 278597     /lib/libgcc_s.so.1                                                                                                                          
401fd000-401fe000 rw-p 0000d000 08:05 278597     /lib/libgcc_s.so.1                                                                                                                          
bf872000-bf889000 rw-p bffe9000 00:00 0          [stack]                                                                                                                                     
/bin/bash: line 7:  7686 Aborted                 /usr/local/pspdev/psp/bin/ar rc libgcov.a $objects                                                                                          
make[2]: *** [libgcov.a] Error 134                                                                                                                                                           
make[2]: *** Waiting for unfinished jobs....                                                                                                                                                 
*** buffer overflow detected ***: /usr/local/pspdev/psp/bin/ar terminated                                                                                                                    
======= Backtrace: =========                                                                                                                                                                 
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0x40132558]                                                                                                                                
/lib/tls/i686/cmov/libc.so.6[0x40130680]                                                                                                                                                     
/lib/tls/i686/cmov/libc.so.6[0x4012fd68]                                                                                                                                                     
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0xc8)[0x400a5a18]                                                                                                                            
/lib/tls/i686/cmov/libc.so.6(_IO_padn+0xed)[0x40098e0d]                                                                                                                                      
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x27cf)[0x4007a15f]                                                                                                                                
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xa7)[0x4012fe17]                                                                                                                                
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0x4012fd5d]                                                                                                                                 
/usr/local/pspdev/psp/bin/ar[0x80512e2]                                                                                                                                                      
/usr/local/pspdev/psp/bin/ar[0x804f2db]                                                                                                                                                      
/usr/local/pspdev/psp/bin/ar[0x8052158]
/usr/local/pspdev/psp/bin/ar[0x8059e98]
/usr/local/pspdev/psp/bin/ar[0x804b8f5]
/usr/local/pspdev/psp/bin/ar[0x804c690]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0x4004e685]
/usr/local/pspdev/psp/bin/ar[0x80496e1]
======= Memory map: ========
08048000-080c5000 r-xp 00000000 08:05 1360527    /usr/local/pspdev/psp/bin/ar
080c5000-080c6000 r--p 0007c000 08:05 1360527    /usr/local/pspdev/psp/bin/ar
080c6000-080c7000 rw-p 0007d000 08:05 1360527    /usr/local/pspdev/psp/bin/ar
080c7000-080cb000 rw-p 080c7000 00:00 0
09484000-0c574000 rw-p 09484000 00:00 0          [heap]
40000000-4001a000 r-xp 00000000 08:05 278806     /lib/ld-2.8.90.so
4001a000-4001b000 r-xp 4001a000 00:00 0          [vdso]
4001b000-4001c000 r--p 0001a000 08:05 278806     /lib/ld-2.8.90.so
4001c000-4001d000 rw-p 0001b000 08:05 278806     /lib/ld-2.8.90.so
4001d000-4001f000 rw-p 4001d000 00:00 0
4001f000-40020000 r--p 00000000 08:05 1319619    /usr/lib/locale/en_CA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
40020000-40027000 r--s 00000000 08:05 1302665    /usr/lib/gconv/gconv-modules.cache
40027000-40031000 rw-p 40027000 00:00 0
40038000-40190000 r-xp 00000000 08:05 295439     /lib/tls/i686/cmov/libc-2.8.90.so
40190000-40192000 r--p 00158000 08:05 295439     /lib/tls/i686/cmov/libc-2.8.90.so
40192000-40193000 rw-p 0015a000 08:05 295439     /lib/tls/i686/cmov/libc-2.8.90.so
40193000-40197000 rw-p 40193000 00:00 0
40197000-401d6000 r--p 00000000 08:05 1319610    /usr/lib/locale/en_CA.utf8/LC_CTYPE
401ef000-401fc000 r-xp 00000000 08:05 278597     /lib/libgcc_s.so.1
401fc000-401fd000 r--p 0000c000 08:05 278597     /lib/libgcc_s.so.1
401fd000-401fe000 rw-p 0000d000 08:05 278597     /lib/libgcc_s.so.1
bff48000-bff65000 rw-p bffe3000 00:00 0          [stack]
/bin/bash: line 7:  7587 Aborted                 /usr/local/pspdev/psp/bin/ar rc libgcc.a $objects
make[2]: *** [libgcc.a] Error 134
make[2]: Leaving directory `/home/james/tmp/psptoolchain/build/gcc-4.3.2/build-psp/psp/libgcc'
make[1]: *** [all-target-libgcc] Error 2
make[1]: Leaving directory `/home/james/tmp/psptoolchain/build/gcc-4.3.2/build-psp'
make: *** [all] Error 2
../scripts/002-gcc-4.3.2-stage1.sh: Failed.
ERROR: Could not run the toolchain script.
james@LinuxMode:~/tmp/psptoolchain$

```

I was following the Instructions from here [http://soledadpenades.com/2008/09/01/installing-the-psp-toolchain-in-ubuntu/]("http://soledadpenades.com/2008/09/01/installing-the-psp-toolchain-in-ubuntu/")

I am not the Most intelligent with this stuff so i could use some input if possible Thanks!

---

### Post by kiwoore on 2008-11-22
The script for install psp's toolchain is incompatible with last version of gcc & g++.

Use gcc 4.2 and g++ 4.3 for compile the toolchain. 

```

source ~/.bashrc

#Install GCC 4.2 and change path

sudo apt-get install gcc-4.2
sudo rm /usr/bin/gcc /usr/bin/g++
sudo ln -s /usr/bin/gcc-4.2 /usr/bin/gcc
sudo ln -s /usr/bin/g++-4.2 /usr/bin/g++

#Install toolchain

sudo ./toolchain-sudo.sh

#Return GCC at 4.3 before installation.
sudo rm /usr/bin/gcc /usr/bin/g++
sudo ln -s /usr/bin/gcc-4.3 /usr/bin/gcc
sudo ln -s /usr/bin/g++-4.3 /usr/bin/g++

``` 

Bye ^^

---

### Post by ironslave on 2008-11-23
Thanks for the Info! but now alas i have a new error

```
g++ -Wall -g -D_PCTERM -I../psplink   -c -o pspsh.o pspsh.C
make[1]: g++: Command not found
make[1]: *** [pspsh.o] Error 127
make[1]: Leaving directory `/home/james/tmp/psptoolchain/build/psplinkusb/pspsh'
make: *** [all] Error 2
../scripts/009-psplinkusb.sh: Failed.
ERROR: Could not run the toolchain script.
```

---

### Post by icedshot on 2008-11-23
psplink is a debugging tool that you dont actually need for the psp, and is a common error during installation. to fix it while in the toolchain directory type into the console 

cd build/psplinkusb/
make && make release

---

### Post by lingenfr on 2008-11-23
> **icedshot said:**
> psplink is a debugging tool that you dont actually need for the psp, and is a common error during installation. to fix it while in the toolchain directory type into the console 

cd build/psplinkusb/
make && make release

Trying to run the second line without sudo gives me a permission problem. Running it with sudo gives me:

lingenfr@MPC-MBR:~/pspdev/psptoolchain/build/psplinkusb$ sudo make && make release
make -f Makefile.psp all
make[1]: Entering directory `/home/lingenfr/pspdev/psptoolchain/build/psplinkusb'
make -C libpsplink all
make[2]: psp-config: Command not found
make[2]: Entering directory `/home/lingenfr/pspdev/psptoolchain/build/psplinkusb/libpsplink'
psp-gcc -Os -G0 -Wall -fno-builtin-printf -I/include -DF_psplink_0000 psplink.S-c -o psplink_0000.o
make[2]: psp-gcc: Command not found
make[2]: *** [psplink_0000.o] Error 127
make[2]: Leaving directory `/home/lingenfr/pspdev/psptoolchain/build/psplinkusb/libpsplink'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/lingenfr/pspdev/psptoolchain/build/psplinkusb'
make: *** [all] Error 2

I checked and psp-config and psp-gcc are located in /usr/local/pspdev/bin. I went into .bashrc and changed PSPDEV to /usr/local/pspdev/bin from the included instructions of /usr/local/pspdev/ still no joy. Both commands run from the command line. As you say it is not needed, I will continue on with the instructions. If you are willing, I would still like to know the answer as I expect I will have a similar problem in the future.

Also, the instructions at ngine are for OE firmware. I am running 5.00m33-3 which I believe is CFW. Is there a different command for CFW? 

I should also mention that I am not trying to set up a dev system. I only want to run remotejoy on linux, so I am looking for the simplest way to do that. Thanks.

---

### Post by ironslave on 2008-11-23
> **icedshot said:**
> psplink is a debugging tool that you dont actually need for the psp, and is a common error during installation. to fix it while in the toolchain directory type into the console 

cd build/psplinkusb/
make && make release

I am getting the same error as lingenfr

i am not sure what to do, if this is not required, could i edit the Make file to skip this and come back to it later?

---

### Post by lingenfr on 2008-11-23
Maybe I am wrong, but it sure looks like the script to build the toolchain checks for gcc 4.3.2 and if you don't have it, it downloads and sets it up. I deleted everything in the directory, changed gcc, etc as suggested and started again, but it looks to me like the script is undoing the changes.

---

### Post by ironslave on 2008-11-23
it's running now and all the builds are running out of a 4.3.2 

gcc-4.3.2/gcc/ada/s-pack42.ads
gcc-4.3.2/gcc/ada/a-nuelfu.ads
gcc-4.3.2/gcc/ada/stylesw.ads
gcc-4.3.2/gcc/ada/g-soccon-hpux.ads
gcc-4.3.2/gcc/ada/s-tasdeb.adb
gcc-4.3.2/gcc/ada/s-casuti.adb
gcc-4.3.2/gcc/ada/sem_attr.adb
gcc-4.3.2/gcc/ada/prj-strt.adb
gcc-4.3.2/gcc/ada/a-exexda.adb
gcc-4.3.2/gcc/ada/exp_ch13.ads
gcc-4.3.2/gcc/ada/sem_type.adb
gcc-4.3.2/gcc/ada/a-ztgeau.ads
gcc-4.3.2/gcc/ada/a-wttest.adb
gcc-4.3.2/gcc/ada/s-pack07.ads
gcc-4.3.2/gcc/ada/s-taprob.adb
gcc-4.3.2/gcc/ada/s-tposen.adb

---

### Post by Sack Boy on 2008-11-23
> **ironslave said:**
> Thanks for the Info! but now alas i have a new error

```
g++ -Wall -g -D_PCTERM -I../psplink   -c -o pspsh.o pspsh.C
make[1]: g++: Command not found
make[1]: *** [pspsh.o] Error 127
make[1]: Leaving directory `/home/james/tmp/psptoolchain/build/psplinkusb/pspsh'
make: *** [all] Error 2
../scripts/009-psplinkusb.sh: Failed.
ERROR: Could not run the toolchain script.
```

I followed all the same steps up to this point and I have the same error. 

It seems that running the toolchain script deleted /usr/bin/g++-4.2 for some reason (I really hope that's all it deleted :confused:). So now /usr/bin/g++ is a broken symbolic link. That's why you get the "g++: Command not found" error.

I got the 009-psplinkusb.sh to succeed by changing the symbolic link back to g++-4.3:

$ sudo rm /usr/bin/g++
$ sudo ln -s /usr/bin/g++-4.3 /usr/bin/g++
$ sudo ./toolchain-sudo.sh 9

Thank you everyone. :)

---

### Post by reizencroft on 2008-11-28
Try this one out:

* Install GCC 4.2
```
sudo apt-get install gcc-4.2
```          
* Modify toolchain-sudo.sh, adding following right before “export PSPDEV=/usr/local/pspdev”
```
export CC=/usr/bin/gcc-4.2
```

like so:
```
#!/bin/bash
# toolchain-sudo.sh by Dan Peori (danpeori@oopo.net)

 ## Enter the psptoolchain directory.
 cd "`dirname $0`" || { echo "ERROR: Could not enter the psptoolchain directory."; exit 1; }

 ## Set up the environment.
 export CC=/usr/bin/gcc-4.2
 export PSPDEV=/usr/local/pspdev
 export PATH=$PATH:$PSPDEV/bin

 ## Run the toolchain script.
 ./toolchain.sh $@ || { echo "ERROR: Could not run the toolchain script."; exit 1; }
```
*run the toolchain script

BTW, use the latest g++. AFAIK only the gcc has problems with intrepid ibex.

hope this helps.

---

### Post by lingenfr on 2008-12-06
Well, this still was a nogo. I had also posted over at on the ps2dev website. Someone there commented that g++ was installed. I checked and yes g++-4.3 was installed. I read reread the posts and decided to install g++4.2 and relink it as per the post above. Success (I think). I still need to see if remotejoy works, but it did compile and it does run.

---

### Post by archman on 2009-03-28
Btw.: anyone knows if there is any compatibility list? Can I run ISO games?

They all lock up on loading the menu. Tekken DR UMD works.

---

