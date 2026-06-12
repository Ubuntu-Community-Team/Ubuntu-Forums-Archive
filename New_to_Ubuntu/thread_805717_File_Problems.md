---
title: "File Problems"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by AcademyKP03 on 2008-05-24
I'd like to convert a rather big UIF file to an iso.

I found an excellent guide here:

[http://wesleybailey.com/blog/2008/03/28/linux-uif-to-iso/](http://wesleybailey.com/blog/2008/03/28/linux-uif-to-iso/)

However, when I follow the instructions - I get errors, any ideas/help?

john@john-laptop:~$ sudo apt-get install zlib1g zlib1g-dev libssl-dev build-essentials
[sudo] password for john:
Reading package lists... Done
Building dependency tree
Reading state information... Done
zlib1g is already the newest version.
E: Couldn't find package build-essentials
john@john-laptop:~$ wget [http://aluigi.altervista.org/mytoolz/uif2iso.zip](http://aluigi.altervista.org/mytoolz/uif2iso.zip)
--19:17:57-- [http://aluigi.altervista.org/mytoolz/uif2iso.zip](http://aluigi.altervista.org/mytoolz/uif2iso.zip)
=> `uif2iso.zip'
Resolving aluigi.altervista.org... 75.126.23.98
Connecting to aluigi.altervista.org|75.126.23.98|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 90,006 (88K) [application/zip]

100%[================================================== ================================================== =============>] 90,006 129.24K/s

19:17:58 (128.75 KB/s) - `uif2iso.zip' saved [90006/90006]

john@john-laptop:~$
john@john-laptop:~$ unzip uif2iso.zip
Archive: uif2iso.zip
creating: src/
inflating: src/Makefile
inflating: src/uif2iso.c
inflating: uif2iso.exe
inflating: uif2iso.txt
john@john-laptop:~$ cd src
john@john-laptop:~/src$ make
cc uif2iso.c -O2 -s -o uif2iso -lz -lssl -lcrypto
uif2iso.c:28:19: error: stdio.h: No such file or directory
uif2iso.c:29:20: error: stdlib.h: No such file or directory
uif2iso.c:30:20: error: string.h: No such file or directory
uif2iso.c:31:20: error: stdint.h: No such file or directory
uif2iso.c:32:18: error: zlib.h: No such file or directory
uif2iso.c:33:25: error: openssl/des.h: No such file or directory
uif2iso.c:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘u8’
uif2iso.c:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘u16’
uif2iso.c:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘i32’
uif2iso.c:47: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘u32’
uif2iso.c:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘i64’
uif2iso.c:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘u64’
uif2iso.c:81: error: expected specifier-qualifier-list before ‘u8’
uif2iso.c:86: error: expected specifier-qualifier-list before ‘u32’
uif2iso.c:93: error: expected specifier-qualifier-list before ‘u64’
uif2iso.c:101: error: expected specifier-qualifier-list before ‘u32’
uif2iso.c:121: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
uif2iso.c:122: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
uif2iso.c:123: error: expected ‘)’ before ‘*’ token
uif2iso.c:124: error: expected ‘)’ before ‘*’ token
uif2iso.c:125: error: expected ‘)’ before ‘*’ token
uif2iso.c:126: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
uif2iso.c:127: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
uif2iso.c:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
uif2iso.c:129: error: expected ‘)’ before ‘*’ token
uif2iso.c:130: error: expected ‘)’ before ‘*’ token
uif2iso.c:131: error: expected ‘)’ before ‘*’ token
uif2iso.c:132: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
uif2iso.c:133: error: expected ‘)’ before ‘*’ token
uif2iso.c:134: error: expected ‘)’ before ‘*’ token
uif2iso.c:135: error: expected ‘)’ before ‘*’ token
uif2iso.c:136: error: expected ‘)’ before ‘*’ token
uif2iso.c:140: error: expected ‘)’ before ‘*’ token
uif2iso.c:141: error: expected ‘)’ before ‘*’ token
uif2iso.c:142: error: expected ‘)’ before ‘*’ token
uif2iso.c:143: error: expected ‘)’ before ‘*’ token
uif2iso.c:144: error: expected ‘)’ before ‘*’ token
uif2iso.c:145: error: expected ‘)’ before ‘*’ token
uif2iso.c:146: error: expected ‘)’ before ‘*’ token
uif2iso.c:147: error: expected ‘)’ before ‘*’ token
uif2iso.c:149: error: expected ‘)’ before ‘*’ token
uif2iso.c: In function ‘main’:
uif2iso.c:159: error: ‘DES_key_schedule’ undeclared (first use in this function)
uif2iso.c:159: error: (Each undeclared identifier is reported only once
uif2iso.c:159: error: for each function it appears in.)
uif2iso.c:159: error: ‘ctx’ undeclared (first use in this function)
uif2iso.c:160: error: ‘z_stream’ undeclared (first use in this function)
uif2iso.c:160: error: expected ‘;’ before ‘z’
uif2iso.c:166: error: ‘FILE’ undeclared (first use in this function)
uif2iso.c:166: error: ‘fdi’ undeclared (first use in this function)
uif2iso.c:167: error: ‘fdo’ undeclared (first use in this function)
uif2iso.c:168: error: ‘fdcue’ undeclared (first use in this function)
uif2iso.c:169: error: ‘u64’ undeclared (first use in this function)
uif2iso.c:169: error: expected ‘;’ before ‘tot’
uif2iso.c:171: error: ‘u32’ undeclared (first use in this function)
uif2iso.c:171: error: expected ‘;’ before ‘i’
uif2iso.c:175: error: ‘u8’ undeclared (first use in this function)
uif2iso.c:175: error: expected ‘;’ before ‘ans’
uif2iso.c:188: error: ‘stdout’ undeclared (first use in this function)
uif2iso.c:188: error: ‘NULL’ undeclared (first use in this function)
uif2iso.c:216: warning: incompatible implicit declaration of built-in function ‘printf’
uif2iso.c:225: error: ‘filei’ undeclared (first use in this function)
uif2iso.c:226: error: ‘fileo’ undeclared (first use in this function)
uif2iso.c:230: error: ‘z’ undeclared (first use in this function)
uif2iso.c:230: error: ‘alloc_func’ undeclared (first use in this function)
uif2iso.c:230: error: expected ‘;’ before numeric constant
uif2iso.c:231: error: ‘free_func’ undeclared (first use in this function)
uif2iso.c:231: error: expected ‘;’ before numeric constant
uif2iso.c:232: error: ‘voidpf’ undeclared (first use in this function)
uif2iso.c:232: error: expected ‘;’ before numeric constant
uif2iso.c:234: warning: incompatible implicit declaration of built-in function ‘printf’
uif2iso.c:238: error: ‘SEEK_END’ undeclared (first use in this function)
uif2iso.c:239: error: ‘file_size’ undeclared (first use in this function)
uif2iso.c:240: error: ‘SEEK_SET’ undeclared (first use in this function)
uif2iso.c:241: warning: incompatible implicit declaration of built-in function ‘printf’
uif2iso.c:247: error: ‘bbis_t’ has no member named ‘sign’
uif2iso.c:248: warning: incompatible implicit declaration of built-in function ‘printf’
uif2iso.c:248: error: ‘bbis_t’ has no member named ‘sign’
uif2iso.c:251: error: ‘bbis_t’ has no member named ‘blhr’
uif2iso.c:253: warning: incompatible implicit declaration of built-in function ‘printf’
uif2iso.c:264: error: ‘bbis_t’ has no member named ‘ver’
uif2iso.c:265: error: ‘bbis_t’ has no member named ‘image_type’
uif2iso.c:266: error: ‘bbis_t’ has no member named ‘padding’
uif2iso.c:267: error: ‘bbis_t’ has no member named ‘sectors’
uif2iso.c:268: error: ‘bbis_t’ has no member named ‘sectorsz’
uif2iso.c:269: error: ‘bbis_t’ has no member named ‘blhr’
uif2iso.c:269: error: ‘bbis_t’ has no member named ‘blhr’
uif2iso.c:270: error: ‘bbis_t’ has no member named ‘blhrbbissz’
uif2iso.c:271: error: ‘bbis_t’ has no member named ‘hash’
uif2iso.c:277: error: ‘bbis_t’ has no member named ‘blhr’
uif2iso.c:280: error: ‘blhr_t’ has no member named ‘sign’
uif2iso.c:281: error: ‘blhr_t’ has no member named ‘sign’
uif2iso.c:283: error: ‘ans’ undeclared (first use in this function)
uif2iso.c:283: error: ‘stdin’ undeclared (first use in this function)
uif2iso.c:284: warning: incompatible implicit declaration of built-in function ‘strlen’
uif2iso.c:286: error: ‘pwdkey’ undeclared (first use in this function)
uif2iso.c:291: warning: incompatible implicit declaration of built-in function ‘malloc’
uif2iso.c:296: error: ‘blhr_t’ has no member named ‘size’
uif2iso.c:299: error: ‘SEEK_CUR’ undeclared (first use in this function)
uif2iso.c:300: warning: incompatible implicit declaration of built-in function ‘memcpy’
uif2iso.c:300: error: ‘tmphash’ undeclared (first use in this function)
uif2iso.c:300: error: ‘bbis_t’ has no member named ‘hash’
uif2iso.c:300: error: ‘bbis_t’ has no member named ‘hash’
uif2iso.c:303: error: ‘bbis_t’ has no member named ‘hash’
uif2iso.c:303: error: ‘bbis_t’ has no member named ‘hash’
uif2iso.c:306: error: ‘blhr_t’ has no member named ‘sign’
uif2iso.c:311: error: ‘blhr_t’ has no member named ‘size’
uif2iso.c:311: error: ‘blhr_t’ has no member named ‘num’
uif2iso.c:313: error: ‘bbis_t’ has no member named ‘image_type’
uif2iso.c:315: error: ‘bbis_t’ has no member named ‘image_type’
uif2iso.c:320: error: ‘blhr_t’ has no member named ‘sign’
uif2iso.c:321: error: ‘blhr_t’ has no member named ‘sign’
uif2iso.c:323: error: ‘blms_data’ undeclared (first use in this function)
uif2iso.c:323: error: ‘blhr_t’ has no member named ‘size’
uif2iso.c:323: error: ‘blhr_t’ has no member named ‘num’
uif2iso.c:328: error: ‘blhr_t’ has no member named ‘sign’
uif2iso.c:329: error: ‘blhr_t’ has no member named ‘sign’
uif2iso.c:331: error: ‘blhr_t’ has no member named ‘num’
uif2iso.c:333: error: ‘blss_data’ undeclared (first use in this function)
uif2iso.c:333: error: ‘blhr_t’ has no member named ‘size’
uif2iso.c:333: error: ‘blhr_t’ has no member named ‘num’
uif2iso.c:340: error: ‘bbis_t’ has no member named ‘image_type’
uif2iso.c:343: error: ‘in’ undeclared (first use in this function)
uif2iso.c:343: error: ‘out’ undeclared (first use in this function)
uif2iso.c:344: error: ‘insz’ undeclared (first use in this function)
uif2iso.c:344: error: ‘outsz’ undeclared (first use in this function)
uif2iso.c:345: error: ‘tot’ undeclared (first use in this function)
uif2iso.c:350: error: ‘outext’ undeclared (first use in this function)
uif2iso.c:372: error: ‘filec’ undeclared (first use in this function)
uif2iso.c:374: error: ‘blhr_t’ has no member named ‘num’
uif2iso.c:375: error: ‘blhr_t’ has no member named ‘num’
uif2iso.c:379: warning: incompatible implicit declaration of built-in function ‘fwrite’
uif2iso.c:379: error: ‘blhr_t’ has no member named ‘num’
uif2iso.c:387: error: ‘i’ undeclared (first use in this function)
uif2iso.c:387: error: ‘blhr_t’ has no member named ‘num’
uif2iso.c:390: error: ‘blhr_t’ has no member named ‘num’
uif2iso.c:412: error: ‘bbis_t’ has no member named ‘sectorsz’
uif2iso.c:421: warning: incompatible implicit declaration of built-in function ‘memcpy’
uif2iso.c:422: warning: incompatible implicit declaration of built-in function ‘memset’
uif2iso.c:426: warning: incompatible implicit declaration of built-in function ‘memset’
uif2iso.c:439: error: expected ‘)’ before ‘blhr_data’
uif2iso.c:452: error: ‘bbis_t’ has no member named ‘sectorsz’
uif2iso.c: At top level:
uif2iso.c:524: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
uif2iso.c:535: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
uif2iso.c:551: error: expected ‘)’ before ‘*’ token
uif2iso.c:682: error: expected ‘)’ before ‘*’ token
uif2iso.c:737: error: expected ‘)’ before ‘*’ token
uif2iso.c:806: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
uif2iso.c:822: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
uif2iso.c:837: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
uif2iso.c:862: error: expected ‘)’ before ‘*’ token
uif2iso.c:926: error: expected ‘)’ before ‘*’ token
uif2iso.c:952: error: expected ‘)’ before ‘*’ token
uif2iso.c:965: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
uif2iso.c:983: error: expected ‘)’ before ‘*’ token
uif2iso.c:992: error: expected ‘)’ before ‘*’ token
uif2iso.c:1000: error: expected ‘)’ before ‘*’ token
uif2iso.c:1008: error: expected ‘)’ before ‘*’ token
uif2iso.c: In function ‘l2n_blhr’:
uif2iso.c:1026: error: ‘blhr_t’ has no member named ‘sign’
uif2iso.c:1027: error: ‘blhr_t’ has no member named ‘size’
uif2iso.c:1028: error: ‘blhr_t’ has no member named ‘ver’
uif2iso.c:1029: error: ‘blhr_t’ has no member named ‘num’
uif2iso.c: In function ‘l2n_blhr_data’:
uif2iso.c:1036: error: ‘blhr_data_t’ has no member named ‘offset’
uif2iso.c:1037: error: ‘blhr_data_t’ has no member named ‘zsize’
uif2iso.c:1038: error: ‘blhr_data_t’ has no member named ‘sector’
uif2iso.c:1039: error: ‘blhr_data_t’ has no member named ‘size’
uif2iso.c:1040: error: ‘blhr_data_t’ has no member named ‘type’
uif2iso.c: In function ‘l2n_bbis’:
uif2iso.c:1047: error: ‘bbis_t’ has no member named ‘sign’
uif2iso.c:1048: error: ‘bbis_t’ has no member named ‘bbis_size’
uif2iso.c:1049: error: ‘bbis_t’ has no member named ‘ver’
uif2iso.c:1050: error: ‘bbis_t’ has no member named ‘image_type’
uif2iso.c:1051: error: ‘bbis_t’ has no member named ‘unknown1’
uif2iso.c:1052: error: ‘bbis_t’ has no member named ‘padding’
uif2iso.c:1053: error: ‘bbis_t’ has no member named ‘sectors’
uif2iso.c:1054: error: ‘bbis_t’ has no member named ‘sectorsz’
uif2iso.c:1055: error: ‘bbis_t’ has no member named ‘unknown2’
uif2iso.c:1056: error: ‘bbis_t’ has no member named ‘blhr’
uif2iso.c:1057: error: ‘bbis_t’ has no member named ‘blhrbbissz’
uif2iso.c:1058: error: ‘bbis_t’ has no member named ‘unknown3’
uif2iso.c:1059: error: ‘bbis_t’ has no member named ‘unknown4’
uif2iso.c: At top level:
uif2iso.c:1064: error: expected ‘)’ before ‘*’ token
uif2iso.c:1076: error: expected ‘)’ before ‘*’ token
uif2iso.c:1090: error: expected ‘)’ before ‘*’ token
uif2iso.c:1108: error: expected ‘)’ before ‘*’ token
uif2iso.c:1120: error: expected ‘)’ before ‘*’ token
uif2iso.c:1134: error: expected ‘)’ before ‘*’ token
uif2iso.c:1152: error: expected ‘)’ before ‘*’ token
uif2iso.c:1172: error: expected ‘)’ before ‘*’ token
uif2iso.c:1196: error: expected ‘)’ before ‘*’ token
uif2iso.c: In function ‘myexit’:
uif2iso.c:1220: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [all] Error 1
john@john-laptop:~/src$

---

### Post by joshsmith on 2008-05-24
the line to notice was:
E: Couldn't find package build-essentials

as in there is no package of that name, and indeed there isnt. E means error. 

you want the package, build-essential. If you look through synaptic package manager instead of apt-get to install packages you can notice those errors more easily

---

