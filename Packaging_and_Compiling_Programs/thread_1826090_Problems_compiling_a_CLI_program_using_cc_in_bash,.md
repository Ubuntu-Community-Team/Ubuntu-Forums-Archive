---
title: "Problems compiling a CLI program using cc in bash, written for DOS using open watcom."
date: 2011-08-16
forum: Packaging and Compiling Programs
---

### Post by megamasha on 2011-08-16
I am fairly determined to wean myself off Micro$oft, and so far the only things keeping me booting into windows are
a) The lastest flash player update has broken all flash content in firfox and rekonq
b) I can't get my C programs to compile.

I have written a CLI program (vt.exe) for cmd.exe in C.
I have compiled it under windows using open watcom and it works. Yay!
I can even make the file executable in linux and it works in bash (Yay again - it's portable, unless wine is jumping in there somehow).
But when I put the vt.c source in a linux directory and run ```
make vt
``` or ```
cc vt.c
``` I get ```
fatal error: process.h: No such file or directory
```So I put process.h from /windows/WATCOM/h in /usr/include.
Access denied
do it as superuser... success.

cc gives access denied, sudo...success.

Then I get
```
cc     vt.c   -o vt
In file included from vt.c:4:0:
/usr/include/process.h:23:22: fatal error: _comdef.h: No such file or directory
compilation terminated.
make: *** [vt] Error 1
```So I copy the entire contents of  /windows/WATCOM/h to /usr/include, skipping any duplicates - after all, the contents of the headers should be roughly the same, right?.

```
rob@SCKubuntu:~/Documents/programming/c/vocabtest$ sudo make vt
[sudo] password for rob: 
cc     vt.c   -o vt
In file included from vt.c:4:0:
/usr/include/process.h: In function ‘__declspec’:
/usr/include/process.h:45:22: error: storage class specified for parameter ‘execl’
/usr/include/process.h:46:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:47:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:48:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:49:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:51:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:55:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:66:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:67:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:94:2: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:98:2: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:100:3: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:111:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:113:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:119:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:120:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:121:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:122:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:131:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:133:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:134:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:135:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:136:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:137:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:139:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:141:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:143:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:145:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:147:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:150:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:152:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:156:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:157:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:160:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:162:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:163:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:164:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:165:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:166:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:168:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:169:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:170:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:172:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:174:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:176:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:178:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:180:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:182:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:185:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:187:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:190:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:202:1: error: expected declaration specifiers before ‘__declspec’
/usr/include/process.h:203:1: error: expected declaration specifiers before ‘__declspec’
In file included from vt.c:5:0:
/usr/include/ctype.h:81:37: error: storage class specified for parameter ‘__ctype_b_loc’
/usr/include/ctype.h:83:28: error: storage class specified for parameter ‘__ctype_tolower_loc’
/usr/include/ctype.h:85:28: error: storage class specified for parameter ‘__ctype_toupper_loc’
/usr/include/ctype.h:102:1: error: storage class specified for parameter ‘isalnum’
/usr/include/ctype.h:103:1: error: storage class specified for parameter ‘isalpha’
/usr/include/ctype.h:104:1: error: storage class specified for parameter ‘iscntrl’
/usr/include/ctype.h:105:1: error: storage class specified for parameter ‘isdigit’
/usr/include/ctype.h:106:1: error: storage class specified for parameter ‘islower’
/usr/include/ctype.h:107:1: error: storage class specified for parameter ‘isgraph’
/usr/include/ctype.h:108:1: error: storage class specified for parameter ‘isprint’
/usr/include/ctype.h:109:1: error: storage class specified for parameter ‘ispunct’
/usr/include/ctype.h:110:1: error: storage class specified for parameter ‘isspace’
/usr/include/ctype.h:111:1: error: storage class specified for parameter ‘isupper’
/usr/include/ctype.h:112:1: error: storage class specified for parameter ‘isxdigit’
/usr/include/ctype.h:116:12: error: storage class specified for parameter ‘tolower’
/usr/include/ctype.h:119:12: error: storage class specified for parameter ‘toupper’
/usr/include/ctype.h:128:1: error: storage class specified for parameter ‘isblank’
/usr/include/ctype.h:142:12: error: storage class specified for parameter ‘isascii’
/usr/include/ctype.h:146:12: error: storage class specified for parameter ‘toascii’
/usr/include/ctype.h:150:1: error: storage class specified for parameter ‘_toupper’
/usr/include/ctype.h:151:1: error: storage class specified for parameter ‘_tolower’
/usr/include/ctype.h:247:1: error: storage class specified for parameter ‘isalnum_l’
/usr/include/ctype.h:248:1: error: storage class specified for parameter ‘isalpha_l’
/usr/include/ctype.h:249:1: error: storage class specified for parameter ‘iscntrl_l’
/usr/include/ctype.h:250:1: error: storage class specified for parameter ‘isdigit_l’
/usr/include/ctype.h:251:1: error: storage class specified for parameter ‘islower_l’
/usr/include/ctype.h:252:1: error: storage class specified for parameter ‘isgraph_l’
/usr/include/ctype.h:253:1: error: storage class specified for parameter ‘isprint_l’
/usr/include/ctype.h:254:1: error: storage class specified for parameter ‘ispunct_l’
/usr/include/ctype.h:255:1: error: storage class specified for parameter ‘isspace_l’
/usr/include/ctype.h:256:1: error: storage class specified for parameter ‘isupper_l’
/usr/include/ctype.h:257:1: error: storage class specified for parameter ‘isxdigit_l’
/usr/include/ctype.h:259:1: error: storage class specified for parameter ‘isblank_l’
/usr/include/ctype.h:263:12: error: storage class specified for parameter ‘__tolower_l’
/usr/include/ctype.h:264:12: error: storage class specified for parameter ‘tolower_l’
/usr/include/ctype.h:267:12: error: storage class specified for parameter ‘__toupper_l’
/usr/include/ctype.h:268:12: error: storage class specified for parameter ‘toupper_l’
In file included from vt.c:6:0:
/usr/include/string.h:44:14: error: storage class specified for parameter ‘memcpy’
/usr/include/string.h:49:14: error: storage class specified for parameter ‘memmove’
/usr/include/string.h:57:14: error: storage class specified for parameter ‘memccpy’
/usr/include/string.h:65:14: error: storage class specified for parameter ‘memset’
/usr/include/string.h:68:12: error: storage class specified for parameter ‘memcmp’
/usr/include/string.h:95:14: error: storage class specified for parameter ‘memchr’
/usr/include/string.h:128:14: error: storage class specified for parameter ‘strcpy’
/usr/include/string.h:131:14: error: storage class specified for parameter ‘strncpy’
/usr/include/string.h:136:14: error: storage class specified for parameter ‘strcat’
/usr/include/string.h:139:14: error: storage class specified for parameter ‘strncat’
/usr/include/string.h:143:12: error: storage class specified for parameter ‘strcmp’
/usr/include/string.h:146:12: error: storage class specified for parameter ‘strncmp’
/usr/include/string.h:150:12: error: storage class specified for parameter ‘strcoll’
/usr/include/string.h:153:15: error: storage class specified for parameter ‘strxfrm’
/usr/include/string.h:165:12: error: storage class specified for parameter ‘strcoll_l’
/usr/include/string.h:168:15: error: storage class specified for parameter ‘strxfrm_l’
/usr/include/string.h:175:14: error: storage class specified for parameter ‘strdup’
/usr/include/string.h:183:14: error: storage class specified for parameter ‘strndup’
/usr/include/string.h:235:14: error: storage class specified for parameter ‘strchr’
/usr/include/string.h:262:14: error: storage class specified for parameter ‘strrchr’
/usr/include/string.h:284:15: error: storage class specified for parameter ‘strcspn’
/usr/include/string.h:288:15: error: storage class specified for parameter ‘strspn’
/usr/include/string.h:314:14: error: storage class specified for parameter ‘strpbrk’
/usr/include/string.h:342:14: error: storage class specified for parameter ‘strstr’
/usr/include/string.h:348:14: error: storage class specified for parameter ‘strtok’
/usr/include/string.h:354:14: error: storage class specified for parameter ‘__strtok_r’
/usr/include/string.h:359:14: error: storage class specified for parameter ‘strtok_r’
/usr/include/string.h:399:15: error: storage class specified for parameter ‘strlen’
/usr/include/string.h:406:15: error: storage class specified for parameter ‘strnlen’
/usr/include/string.h:413:14: error: storage class specified for parameter ‘strerror’
/usr/include/string.h:427:12: error: storage class specified for parameter ‘strerror_r’
/usr/include/string.h:445:14: error: storage class specified for parameter ‘strerror_l’
/usr/include/string.h:451:13: error: storage class specified for parameter ‘__bzero’
/usr/include/string.h:455:13: error: storage class specified for parameter ‘bcopy’
/usr/include/string.h:459:13: error: storage class specified for parameter ‘bzero’
/usr/include/string.h:462:12: error: storage class specified for parameter ‘bcmp’
/usr/include/string.h:489:14: error: storage class specified for parameter ‘index’
/usr/include/string.h:517:14: error: storage class specified for parameter ‘rindex’
/usr/include/string.h:523:12: error: storage class specified for parameter ‘ffs’
/usr/include/string.h:536:12: error: storage class specified for parameter ‘strcasecmp’
/usr/include/string.h:540:12: error: storage class specified for parameter ‘strncasecmp’
/usr/include/string.h:559:14: error: storage class specified for parameter ‘strsep’
/usr/include/string.h:566:14: error: storage class specified for parameter ‘strsignal’
/usr/include/string.h:569:14: error: storage class specified for parameter ‘__stpcpy’
/usr/include/string.h:571:14: error: storage class specified for parameter ‘stpcpy’
/usr/include/string.h:576:14: error: storage class specified for parameter ‘__stpncpy’
/usr/include/string.h:579:14: error: storage class specified for parameter ‘stpncpy’
vt.c:19:1: warning: empty declaration
vt.c:32:1: warning: empty declaration
vt.c:41:1: error: parameter ‘maxtextlength’ is initialized
vt.c:61:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:114:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:149:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:174:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:192:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:243:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:255:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:293:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:479:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:506:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:519:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:525:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:531:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:537:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:549:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
vt.c:58:6: error: declaration for parameter ‘clearinputbuffer’ but no such parameter
vt.c:57:6: error: declaration for parameter ‘cls’ but no such parameter
vt.c:56:6: error: declaration for parameter ‘testrandom’ but no such parameter
vt.c:55:6: error: declaration for parameter ‘wank’ but no such parameter
vt.c:54:5: error: declaration for parameter ‘getyesorno’ but no such parameter
vt.c:53:8: error: declaration for parameter ‘gettextfromkeyboard’ but no such parameter
vt.c:52:6: error: declaration for parameter ‘testme’ but no such parameter
vt.c:51:5: error: declaration for parameter ‘writeliststofile’ but no such parameter
vt.c:50:6: error: declaration for parameter ‘reindex’ but no such parameter
vt.c:49:5: error: declaration for parameter ‘removefromlist’ but no such parameter
vt.c:48:16: error: declaration for parameter ‘addtolist’ but no such parameter
vt.c:47:5: error: declaration for parameter ‘readnumberfromfile’ but no such parameter
vt.c:46:8: error: declaration for parameter ‘readtextfromfile’ but no such parameter
vt.c:45:6: error: declaration for parameter ‘getrecordsfromfile’ but no such parameter
vt.c:43:8: error: declaration for parameter ‘outputfile’ but no such parameter
vt.c:42:8: error: declaration for parameter ‘inputfile’ but no such parameter
vt.c:41:5: error: declaration for parameter ‘maxtextlength’ but no such parameter
vt.c:40:5: error: declaration for parameter ‘n2l_flag’ but no such parameter
vt.c:39:35: error: declaration for parameter ‘old’ but no such parameter
vt.c:39:28: error: declaration for parameter ‘known’ but no such parameter
vt.c:39:22: error: declaration for parameter ‘norm’ but no such parameter
vt.c:39:17: error: declaration for parameter ‘n2l’ but no such parameter
/usr/include/string.h:579:14: error: declaration for parameter ‘stpncpy’ but no such parameter
/usr/include/string.h:576:14: error: declaration for parameter ‘__stpncpy’ but no such parameter
/usr/include/string.h:571:14: error: declaration for parameter ‘stpcpy’ but no such parameter
/usr/include/string.h:569:14: error: declaration for parameter ‘__stpcpy’ but no such parameter
/usr/include/string.h:566:14: error: declaration for parameter ‘strsignal’ but no such parameter
/usr/include/string.h:559:14: error: declaration for parameter ‘strsep’ but no such parameter
/usr/include/string.h:540:12: error: declaration for parameter ‘strncasecmp’ but no such parameter
/usr/include/string.h:536:12: error: declaration for parameter ‘strcasecmp’ but no such parameter
/usr/include/string.h:523:12: error: declaration for parameter ‘ffs’ but no such parameter
/usr/include/string.h:517:14: error: declaration for parameter ‘rindex’ but no such parameter
/usr/include/string.h:489:14: error: declaration for parameter ‘index’ but no such parameter
/usr/include/string.h:462:12: error: declaration for parameter ‘bcmp’ but no such parameter
/usr/include/string.h:459:13: error: declaration for parameter ‘bzero’ but no such parameter
/usr/include/string.h:455:13: error: declaration for parameter ‘bcopy’ but no such parameter
/usr/include/string.h:451:13: error: declaration for parameter ‘__bzero’ but no such parameter
/usr/include/string.h:445:14: error: declaration for parameter ‘strerror_l’ but no such parameter
/usr/include/string.h:427:12: error: declaration for parameter ‘strerror_r’ but no such parameter
/usr/include/string.h:413:14: error: declaration for parameter ‘strerror’ but no such parameter
/usr/include/string.h:406:15: error: declaration for parameter ‘strnlen’ but no such parameter
/usr/include/string.h:399:15: error: declaration for parameter ‘strlen’ but no such parameter
/usr/include/string.h:359:14: error: declaration for parameter ‘strtok_r’ but no such parameter
/usr/include/string.h:354:14: error: declaration for parameter ‘__strtok_r’ but no such parameter
/usr/include/string.h:348:14: error: declaration for parameter ‘strtok’ but no such parameter
/usr/include/string.h:342:14: error: declaration for parameter ‘strstr’ but no such parameter
/usr/include/string.h:314:14: error: declaration for parameter ‘strpbrk’ but no such parameter
/usr/include/string.h:288:15: error: declaration for parameter ‘strspn’ but no such parameter
/usr/include/string.h:284:15: error: declaration for parameter ‘strcspn’ but no such parameter
/usr/include/string.h:262:14: error: declaration for parameter ‘strrchr’ but no such parameter
/usr/include/string.h:235:14: error: declaration for parameter ‘strchr’ but no such parameter
/usr/include/string.h:183:14: error: declaration for parameter ‘strndup’ but no such parameter
/usr/include/string.h:175:14: error: declaration for parameter ‘strdup’ but no such parameter
/usr/include/string.h:168:15: error: declaration for parameter ‘strxfrm_l’ but no such parameter
/usr/include/string.h:165:12: error: declaration for parameter ‘strcoll_l’ but no such parameter
/usr/include/string.h:153:15: error: declaration for parameter ‘strxfrm’ but no such parameter
/usr/include/string.h:150:12: error: declaration for parameter ‘strcoll’ but no such parameter
/usr/include/string.h:146:12: error: declaration for parameter ‘strncmp’ but no such parameter
/usr/include/string.h:143:12: error: declaration for parameter ‘strcmp’ but no such parameter
/usr/include/string.h:139:14: error: declaration for parameter ‘strncat’ but no such parameter
/usr/include/string.h:136:14: error: declaration for parameter ‘strcat’ but no such parameter
/usr/include/string.h:131:14: error: declaration for parameter ‘strncpy’ but no such parameter
/usr/include/string.h:128:14: error: declaration for parameter ‘strcpy’ but no such parameter
/usr/include/string.h:95:14: error: declaration for parameter ‘memchr’ but no such parameter
/usr/include/string.h:68:12: error: declaration for parameter ‘memcmp’ but no such parameter
/usr/include/string.h:65:14: error: declaration for parameter ‘memset’ but no such parameter
/usr/include/string.h:57:14: error: declaration for parameter ‘memccpy’ but no such parameter
/usr/include/string.h:49:14: error: declaration for parameter ‘memmove’ but no such parameter
/usr/include/string.h:44:14: error: declaration for parameter ‘memcpy’ but no such parameter
/usr/include/ctype.h:268:12: error: declaration for parameter ‘toupper_l’ but no such parameter
/usr/include/ctype.h:267:12: error: declaration for parameter ‘__toupper_l’ but no such parameter
/usr/include/ctype.h:264:12: error: declaration for parameter ‘tolower_l’ but no such parameter
/usr/include/ctype.h:263:12: error: declaration for parameter ‘__tolower_l’ but no such parameter
/usr/include/ctype.h:259:1: error: declaration for parameter ‘isblank_l’ but no such parameter
/usr/include/ctype.h:257:1: error: declaration for parameter ‘isxdigit_l’ but no such parameter
/usr/include/ctype.h:256:1: error: declaration for parameter ‘isupper_l’ but no such parameter
/usr/include/ctype.h:255:1: error: declaration for parameter ‘isspace_l’ but no such parameter
/usr/include/ctype.h:254:1: error: declaration for parameter ‘ispunct_l’ but no such parameter
/usr/include/ctype.h:253:1: error: declaration for parameter ‘isprint_l’ but no such parameter
/usr/include/ctype.h:252:1: error: declaration for parameter ‘isgraph_l’ but no such parameter
/usr/include/ctype.h:251:1: error: declaration for parameter ‘islower_l’ but no such parameter
/usr/include/ctype.h:250:1: error: declaration for parameter ‘isdigit_l’ but no such parameter
/usr/include/ctype.h:249:1: error: declaration for parameter ‘iscntrl_l’ but no such parameter
/usr/include/ctype.h:248:1: error: declaration for parameter ‘isalpha_l’ but no such parameter
/usr/include/ctype.h:247:1: error: declaration for parameter ‘isalnum_l’ but no such parameter
/usr/include/ctype.h:151:1: error: declaration for parameter ‘_tolower’ but no such parameter
/usr/include/ctype.h:150:1: error: declaration for parameter ‘_toupper’ but no such parameter
/usr/include/ctype.h:146:12: error: declaration for parameter ‘toascii’ but no such parameter
/usr/include/ctype.h:142:12: error: declaration for parameter ‘isascii’ but no such parameter
/usr/include/ctype.h:128:1: error: declaration for parameter ‘isblank’ but no such parameter
/usr/include/ctype.h:119:12: error: declaration for parameter ‘toupper’ but no such parameter
/usr/include/ctype.h:116:12: error: declaration for parameter ‘tolower’ but no such parameter
/usr/include/ctype.h:112:1: error: declaration for parameter ‘isxdigit’ but no such parameter
/usr/include/ctype.h:111:1: error: declaration for parameter ‘isupper’ but no such parameter
/usr/include/ctype.h:110:1: error: declaration for parameter ‘isspace’ but no such parameter
/usr/include/ctype.h:109:1: error: declaration for parameter ‘ispunct’ but no such parameter
/usr/include/ctype.h:108:1: error: declaration for parameter ‘isprint’ but no such parameter
/usr/include/ctype.h:107:1: error: declaration for parameter ‘isgraph’ but no such parameter
/usr/include/ctype.h:106:1: error: declaration for parameter ‘islower’ but no such parameter
/usr/include/ctype.h:105:1: error: declaration for parameter ‘isdigit’ but no such parameter
/usr/include/ctype.h:104:1: error: declaration for parameter ‘iscntrl’ but no such parameter
/usr/include/ctype.h:103:1: error: declaration for parameter ‘isalpha’ but no such parameter
/usr/include/ctype.h:102:1: error: declaration for parameter ‘isalnum’ but no such parameter
/usr/include/ctype.h:85:28: error: declaration for parameter ‘__ctype_toupper_loc’ but no such parameter
/usr/include/ctype.h:83:28: error: declaration for parameter ‘__ctype_tolower_loc’ but no such parameter
/usr/include/ctype.h:81:37: error: declaration for parameter ‘__ctype_b_loc’ but no such parameter
/usr/include/process.h:45:22: error: declaration for parameter ‘execl’ but no such parameter
vt.c:599:1: error: expected ‘{’ at end of input
make: *** [vt] Error 1
```Now I'm stuck.

It looks to me like a problem with the files I've copied over, but they worked with another ANSI C compiler.

 I know there's a version of open watcom for linux, but I want to use the linux build chain.

I do have a backup of my original include directory.

Help anyone?

MM

---

