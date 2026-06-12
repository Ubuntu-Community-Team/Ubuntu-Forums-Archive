---
title: "Cross Compiling Mono for ARM"
date: 2009-12-17
forum: Programming Talk
---

### Post by kartiknatarajan on 2009-12-17
Hi, 

I am trying to cross compile Mono for an ARM target (XScale Intel PXA255). While cross compiling my ./configure breaks, I am pasting the last few lines of the error below. 

checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking grp.h usability... yes
checking grp.h presence... yes
checking for grp.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking ieeefp.h usability... no
checking ieeefp.h presence... no
checking for ieeefp.h... no
checking for isinf... yes
checking for void *... yes
checking size of void *... 4
checking for -Wdeclaration-after-statement option to gcc... no
checking integrity of package... ok
checking for pkg-config... /usr/bin/pkg-config
checking for arm-unknown-linux-gnu-pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... yes
checking for -mno-tls-direct-seg-refs option to gcc... no
checking for visibility __attribute__... yes
checking for library containing clock_gettime... -lrt
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for preceeding underscore in symbols... configure: error: cannot run test program while cross compiling
See `config.log' for more details.

Can anyone please let me know why is this happening. It is kind of urgent and any help will be of great use.

Thanks.

---

### Post by kartiknatarajan on 2009-12-18
Hi Mods,

Please let me know if I have incorrectly posted here for this question. As I could not find a Embedded Linux subforum I searched for a cross compiliation thread and posted into the same thread.

Others, 

Please let me know if you have any suggestions to this issue.

---

### Post by dwhitney67 on 2009-12-18
I do not have any direct experience with what you are attempting, but as for your issue, have you done anything with respect to this message?...
```

See `config.log' for more details.

```
If so, what information was in the log file?

---

### Post by WitchCraft on 2009-12-18
> **kartiknatarajan said:**
> Hi, 

I am trying to cross compile Mono for an ARM target (XScale Intel PXA255). While cross compiling my ./configure breaks, I am pasting the last few lines of the error below. 

checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking grp.h usability... yes
checking grp.h presence... yes
checking for grp.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking ieeefp.h usability... no
checking ieeefp.h presence... no
checking for ieeefp.h... no
checking for isinf... yes
checking for void *... yes
checking size of void *... 4
checking for -Wdeclaration-after-statement option to gcc... no
checking integrity of package... ok
checking for pkg-config... /usr/bin/pkg-config
checking for arm-unknown-linux-gnu-pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... yes
checking for -mno-tls-direct-seg-refs option to gcc... no
checking for visibility __attribute__... yes
checking for library containing clock_gettime... -lrt
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for preceeding underscore in symbols... configure: error: cannot run test program while cross compiling
See `config.log' for more details.

Can anyone please let me know why is this happening. It is kind of urgent and any help will be of great use.

Thanks.

What's your cross-compiler/environment ?

---

### Post by kartiknatarajan on 2009-12-18
The output of the config.log does not suggest much. please check - [http://pastebin.com/m3ab11f0a](http://pastebin.com/m3ab11f0a).

The build environment is a Intel X64 machine and I am using Ubuntu. The target is a Intel Xscale PXA 255 processor (ARM) and the cross compiler is a arm-linux cross compiler. You can find more details in the above pastebin link. 

Also the variables I am using for configure -

./configure CC='/home/kartik/stargate-linux/bin/arm-linux-gcc' CXX='/home/kartik/stargate-linux/bin/arm-linux-g++' --x-libraries=/home/kartik/stargate-linux/lib CPP='/home/kartik/stargate-linux/bin/arm-linux-cpp' --cache-file=config.cache --host=arm-unknown-linux-gnu --target=arm-unknown-linux-gnu --with-includes=/usr/local/arm.new/arm-unknown-linux-gnu/include/ --disable-mcs-build

Output till where ./configure breaks - [http://pastebin.com/m6fe09a07](http://pastebin.com/m6fe09a07)

Thanks for your assistance.

---

### Post by kartiknatarajan on 2009-12-18
Anyone has any inputs on this?

---

### Post by cszikszoy on 2009-12-19
I would ask the people in the official mono channel, #mono on irc.gimp.org

---

