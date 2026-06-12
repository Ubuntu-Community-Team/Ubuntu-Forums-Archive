---
title: "Problem porting aircrack to mips with ubuntu"
date: 2009-08-17
forum: Packaging and Compiling Programs
---

### Post by berni69 on 2009-08-17
hi everybody, i'm trying to port aircrack to my fonera, but i have a lot of problems to compile it,  i solved few problems, but now i dont know how to solve that, i had created my own toolchain for openwrt, with openssl and the others dependences that aircrack require. I've configured makefiles and others build variables and that it's the problem:

```
bernat@bernat-laptop:~/Escriptori/aircrack-ng-1.0-rc4$ make
make -C src all
make[1]: Entering directory `/home/bernat/Escriptori/aircrack-ng-1.0-rc4/src'
make -C osdep
make[2]: Entering directory `/home/bernat/Escriptori/aircrack-ng-1.0-rc4/src/osdep'
Building for Linux
make[3]: Entering directory `/home/bernat/Escriptori/aircrack-ng-1.0-rc4/src/osdep'
mips-linux-gcc -g -W -Wall -Werror -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=0 -I/home/bernat/Escriptori/kamikaze_8.09.1/staging_dir/toolchain-mips_gcc4.2.4/include -fPIC -I..    -c -o osdep.o osdep.c
mips-linux-gcc -g -W -Wall -Werror -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=0 -I/home/bernat/Escriptori/kamikaze_8.09.1/staging_dir/toolchain-mips_gcc4.2.4/include -fPIC -I..    -c -o network.o network.c
mips-linux-gcc -g -W -Wall -Werror -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=0 -I/home/bernat/Escriptori/kamikaze_8.09.1/staging_dir/toolchain-mips_gcc4.2.4/include -fPIC -I..    -c -o linux.o linux.c
mips-linux-gcc -g -W -Wall -Werror -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=0 -I/home/bernat/Escriptori/kamikaze_8.09.1/staging_dir/toolchain-mips_gcc4.2.4/include -fPIC -I..    -c -o linux_tap.o linux_tap.c
mips-linux-gcc -g -W -Wall -Werror -O3 -Wno-strict-aliasing -D_FILE_OFFSET_BITS=64 -D_REVISION=0 -I/home/bernat/Escriptori/kamikaze_8.09.1/staging_dir/toolchain-mips_gcc4.2.4/include -fPIC -I..    -c -o radiotap/radiotap-parser.o radiotap/radiotap-parser.c
radiotap/radiotap-parser.c: In function 'ieee80211_radiotap_iterator_init':
radiotap/radiotap-parser.c:57: error: 'u_int16_t' undeclared (first use in this function)
radiotap/radiotap-parser.c:57: error: (Each undeclared identifier is reported only once
radiotap/radiotap-parser.c:57: error: for each function it appears in.)
radiotap/radiotap-parser.c:57: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:57: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:61: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:61: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:63: error: 'u_int32_t' undeclared (first use in this function)
radiotap/radiotap-parser.c:63: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:63: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:63: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:63: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:72: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:72: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:72: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:72: error: expected ')' before numeric constant
radiotap/radiotap-parser.c: In function 'ieee80211_radiotap_iterator_next':
radiotap/radiotap-parser.c:225: error: 'u_int32_t' undeclared (first use in this function)
radiotap/radiotap-parser.c:225: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:225: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:225: error: expected ')' before numeric constant
radiotap/radiotap-parser.c:225: error: expected ')' before numeric constant
make[3]: *** [radiotap/radiotap-parser.o] Error 1
make[3]: Leaving directory `/home/bernat/Escriptori/aircrack-ng-1.0-rc4/src/osdep'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bernat/Escriptori/aircrack-ng-1.0-rc4/src/osdep'
make[1]: *** [osd] Error 2
make[1]: Leaving directory `/home/bernat/Escriptori/aircrack-ng-1.0-rc4/src'
make: *** [all] Error 2

```the same problem i have if i configure my osname to 'mips-linux' or 'linux-mips', but now it have when the system compiles airdecloak, the executables run on my fonera (i see the main help)  but aireplay and airodump cant inject and scan ... 

what am i doing wrong?

PD: i put this thread here beacouse i dont know whrere i have to put this post, if I mistaked, please move it thx

---

### Post by berni69 on 2009-08-19
hi everybody if somebody is  interested how to solve this problem he can see

[http://www.bitsdelocos.es/2009/08/portando-aircrack-ng-1-0-a-la-fonera/](http://www.bitsdelocos.es/2009/08/portando-aircrack-ng-1-0-a-la-fonera/)

---

