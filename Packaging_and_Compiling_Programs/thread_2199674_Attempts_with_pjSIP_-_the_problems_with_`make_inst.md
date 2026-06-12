---
title: "Attempts with pjSIP - the problems with `make install`"
date: 2014-01-15
forum: Packaging and Compiling Programs
---

### Post by koloryk on 2014-01-15
[COLOR=#000000][FONT=Arial]I wanted to compile from source PJSIP library in order to run it on your Android device. I used the manual:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The problem already encountered in carrying out the command ./configure-android. On my Ubuntu 13.10 Console said that there is no such file or directory. I figured that this is a fault so I changed paths ruthless ./ to ../ file both the performance and the rest other related configuration files. Here is the log:

```
[FONT=Consolas]configure[/FONT][FONT=Consolas]-[/FONT][FONT=Consolas]android[/FONT][FONT=Consolas]:[/FONT][FONT=Consolas] APP_PLATFORM [/FONT][COLOR=#00008B][FONT=Consolas]not[/FONT][/COLOR][FONT=Consolas] specified[/FONT][FONT=Consolas],[/FONT][COLOR=#00008B][FONT=Consolas]using[/FONT][/COLOR][FONT=Consolas] android[/FONT][FONT=Consolas]-[/FONT][COLOR=#800000][FONT=Consolas]19[/FONT][/COLOR]
```[/FONT][/COLOR]```

configure-android: TARGET_ABI [COLOR=#00008B]not[/COLOR] specified, [COLOR=#00008B]using[/COLOR] armeabi
configure-android: calling ./configure [COLOR=#00008B]with[/COLOR] env vars:
 CC = [COLOR=#800000]/home/[/COLOR]android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/toolchains/arm-linux-androideabi-[COLOR=#800000]4.8[/COLOR]/prebuilt/linux-x86_64/bin/arm-linux-androideabi-gcc
 CXX = [COLOR=#800000]/home/[/COLOR]android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/toolchains/arm-linux-androideabi-[COLOR=#800000]4.8[/COLOR]/prebuilt/linux-x86_64/bin/arm-linux-androideabi-g++
 CFLAGS =  -I/home/android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/platforms/android-[COLOR=#800000]19[/COLOR]/arch-arm/usr/include
 CXXFLAGS =  -shared --sysroot=[COLOR=#800000]/home/[/COLOR]android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/platforms/android-[COLOR=#800000]19[/COLOR]/arch-arm
 LDFLAGS =  -nostdlib -L/home/android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/platforms/android-[COLOR=#800000]19[/COLOR]/arch-arm/usr/lib/
 LIBS =  -lc -lgcc
 AR = [COLOR=#800000]/home/[/COLOR]android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/toolchains/arm-linux-androideabi-[COLOR=#800000]4.8[/COLOR]/prebuilt/linux-x86_64/bin/arm-linux-androideabi-ar
 RANLIB = [COLOR=#800000]/home/[/COLOR]android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/toolchains/arm-linux-androideabi-[COLOR=#800000]4.8[/COLOR]/prebuilt/linux-x86_64/bin/arm-linux-androideabi-ranlib
aconfigure: error: missing argument to --prefix
android@android-[COLOR=#2B91AF]VirtualBox[/COLOR]:~[COLOR=#800000]/Downloads/[/COLOR]trunk/pjsip$ ../configure-android --prefix=/usr
configure-android: APP_PLATFORM [COLOR=#00008B]not[/COLOR] specified, [COLOR=#00008B]using[/COLOR] android-[COLOR=#800000]19[/COLOR]
configure-android: TARGET_ABI [COLOR=#00008B]not[/COLOR] specified, [COLOR=#00008B]using[/COLOR] armeabi
configure-android: calling ./configure [COLOR=#00008B]with[/COLOR] env vars:
 CC = [COLOR=#800000]/home/[/COLOR]android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/toolchains/arm-linux-androideabi-[COLOR=#800000]4.8[/COLOR]/prebuilt/linux-x86_64/bin/arm-linux-androideabi-gcc
 CXX = [COLOR=#800000]/home/[/COLOR]android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/toolchains/arm-linux-androideabi-[COLOR=#800000]4.8[/COLOR]/prebuilt/linux-x86_64/bin/arm-linux-androideabi-g++
 CFLAGS =  -I/home/android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/platforms/android-[COLOR=#800000]19[/COLOR]/arch-arm/usr/include
 CXXFLAGS =  -shared --sysroot=[COLOR=#800000]/home/[/COLOR]android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/platforms/android-[COLOR=#800000]19[/COLOR]/arch-arm
 LDFLAGS =  -nostdlib -L/home/android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/platforms/android-[COLOR=#800000]19[/COLOR]/arch-arm/usr/lib/
 LIBS =  -lc -lgcc
 AR = [COLOR=#800000]/home/[/COLOR]android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/toolchains/arm-linux-androideabi-[COLOR=#800000]4.8[/COLOR]/prebuilt/linux-x86_64/bin/arm-linux-androideabi-ar
 RANLIB = [COLOR=#800000]/home/[/COLOR]android/[COLOR=#2B91AF]Downloads[/COLOR]/android-ndk-r9c/toolchains/arm-linux-androideabi-[COLOR=#800000]4.8[/COLOR]/prebuilt/linux-x86_64/bin/arm-linux-androideabi-ranlib
aconfigure: WARNING: [COLOR=#00008B]if[/COLOR] you wanted to [COLOR=#00008B]set[/COLOR] the --build type, don[COLOR=#800000]'t use --host.
    If a cross compiler is detected then cross compile mode will be used
checking build system type... x86_64-unknown-linux-gnu
checking host system type... arm-unknown-linux-androideabi
checking target system type... arm-unknown-linux-androideabi
checking for arm-linux-androideabi-gcc... /home/android/Downloads/android-ndk-r9c/toolchains/arm-linux-androideabi-4.8/prebuilt/linux-x86_64/bin/arm-linux-androideabi-gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... yes
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether /home/android/Downloads/android-ndk-r9c/toolchains/arm-linux-androideabi-4.8/prebuilt/linux-x86_64/bin/arm-linux-androideabi-gcc accepts -g... yes
checking for /home/android/Downloads/android-ndk-r9c/toolchains/arm-linux-androideabi-4.8/prebuilt/linux-x86_64/bin/arm-linux-androideabi-gcc option to accept ISO C89... none needed
checking whether we are using the GNU C++ compiler... yes
checking whether /home/android/Downloads/android-ndk-r9c/toolchains/arm-linux-androideabi-4.8/prebuilt/linux-x86_64/bin/arm-linux-androideabi-g++ accepts -g... yes
checking for arm-linux-androideabi-ranlib... /home/android/Downloads/android-ndk-r9c/toolchains/arm-linux-androideabi-4.8/prebuilt/linux-x86_64/bin/arm-linux-androideabi-ranlib
checking for arm-linux-androideabi-ar... /home/android/Downloads/android-ndk-r9c/toolchains/arm-linux-androideabi-4.8/prebuilt/linux-x86_64/bin/arm-linux-androideabi-ar
checking for pthread_create in -lpthread... no
checking for puts in -lwsock32... no
checking for puts in -lws2_32... no
checking for puts in -lole32... no
checking for puts in -lwinmm... no
checking for puts in -lsocket... no
checking for puts in -lrt... no
checking for puts in -lnsl... no
checking for sin in -lm... yes
checking for uuid_generate in -luuid... no
checking for uuid_generate in -luuid... (cached) no
Setting PJ_M_NAME to arm
checking memory alignment... 4 bytes (default)
checking how to run the C preprocessor... /home/android/Downloads/android-ndk-r9c/toolchains/arm-linux-androideabi-4.8/prebuilt/linux-x86_64/bin/arm-linux-androideabi-gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether byte ordering is bigendian... no
Checking if floating point is disabled... no
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking linux/socket.h usability... yes
checking linux/socket.h presence... yes
checking for linux/socket.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in_systm.h usability... yes
checking netinet/in_systm.h presence... yes
checking for netinet/in_systm.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for netinet/ip.h... no
checking netinet/tcp.h usability... yes
checking netinet/tcp.h presence... yes
checking for netinet/tcp.h... yes
checking ifaddrs.h usability... no
checking ifaddrs.h presence... no
checking for ifaddrs.h... no
checking semaphore.h usability... yes
checking semaphore.h presence... yes
checking for semaphore.h... yes
checking setjmp.h usability... yes
checking setjmp.h presence... yes
checking for setjmp.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/timeb.h usability... yes
checking sys/timeb.h presence... yes
checking for sys/timeb.h... yes
checking for sys/types.h... (cached) yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for unistd.h... (cached) yes
checking winsock.h usability... no
checking winsock.h presence... no
checking for winsock.h... no
checking winsock2.h usability... no
checking winsock2.h presence... no
checking for winsock2.h... no
checking for mswsock.h... no
checking ws2tcpip.h usability... no
checking ws2tcpip.h presence... no
checking for ws2tcpip.h... no
checking uuid/uuid.h usability... no
checking uuid/uuid.h presence... no
checking for uuid/uuid.h... no
checking for net/if.h... yes
Setting PJ_OS_NAME to arm-unknown-linux-androideabi
Setting PJ_HAS_ERRNO_VAR to 1
Setting PJ_HAS_HIGH_RES_TIMER to 1
Setting PJ_HAS_MALLOC to 1
Setting PJ_NATIVE_STRING_IS_UNICODE to 0
Setting PJ_ATOMIC_VALUE_TYPE to long
checking if inet_aton() is available... yes
checking if inet_pton() is available... yes
checking if inet_ntop() is available... yes
checking if getaddrinfo() is available... yes
checking if sockaddr_in has sin_len member... no
checking if socklen_t is available... yes
checking if SO_ERROR is available... yes
checking if pthread_rwlock_t is available... yes
checking if pthread_mutexattr_settype() is available... no
checking if pthread_mutexattr_t has recursive member... no
checking ioqueue backend... select()
Building shared libraries... no
checking sys/soundcard.h usability... no
checking sys/soundcard.h presence... no
checking for sys/soundcard.h... no
checking linux/soundcard.h usability... yes
checking linux/soundcard.h presence... yes
checking for linux/soundcard.h... yes
checking machine/soundcard.h usability... no
checking machine/soundcard.h presence... no
checking for machine/soundcard.h... no
Checking sound device backend... OpenSL ES
Video is disabled
Checking if small filter is disabled... no
Checking if large filter is disabled... no
Checking if Speex AEC is disabled...no
Checking if G.711 codec is disabled...no
Checking if L16 codec is disabled...no
Checking if GSM codec is disabled...no
Checking if G.722 codec is disabled...no
Checking if G.722.1 codec is disabled...no
Checking if Speex codec is disabled...no
Checking if iLBC codec is disabled...no
Skipping libsamplerate detection
Building libresample as shared library... no
Checking if SDL is disabled... yes
Checking if ffmpeg is disabled... yes
Checking if V4L2 is disabled... yes
Skipping Intel IPP settings (not wanted)
Checking if SSL support is disabled... yes
Checking if OpenCORE AMR support is disabled... yes
Checking if SILK support is disabled... yes
checking if select() needs correct nfds... no (default)
** Decided that select() doesn'[/COLOR]t need correct nfds (please check)
checking [COLOR=#00008B]if[/COLOR] pj_thread_create() should enforce stack size... [COLOR=#00008B]no[/COLOR] ([COLOR=#00008B]default[/COLOR])
checking [COLOR=#00008B]if[/COLOR] pj_thread_create() should allocate stack... [COLOR=#00008B]no[/COLOR] ([COLOR=#00008B]default[/COLOR])
** [COLOR=#2B91AF]Setting[/COLOR] non-blocking recv() retval to EAGAIN (please check)
** [COLOR=#2B91AF]Setting[/COLOR] non-blocking connect() retval to EINPROGRESS (please check)
aconfigure: creating ./config.status
config.status: creating build.mak
config.status: creating build/os-[COLOR=#00008B]auto[/COLOR].mak
config.status: creating build/cc-[COLOR=#00008B]auto[/COLOR].mak
config.status: creating pjlib/build/os-[COLOR=#00008B]auto[/COLOR].mak
config.status: creating pjlib-util/build/os-[COLOR=#00008B]auto[/COLOR].mak
config.status: creating pjmedia/build/os-[COLOR=#00008B]auto[/COLOR].mak
config.status: creating pjsip/build/os-[COLOR=#00008B]auto[/COLOR].mak
config.status: creating third_party/build/os-[COLOR=#00008B]auto[/COLOR].mak
config.status: creating third_party/build/portaudio/os-[COLOR=#00008B]auto[/COLOR].mak
config.status: creating pjlib/include/pj/compat/os_auto.h
config.status: pjlib/include/pj/compat/os_auto.h [COLOR=#00008B]is[/COLOR] unchanged
config.status: creating pjlib/include/pj/compat/m_auto.h
config.status: pjlib/include/pj/compat/m_auto.h [COLOR=#00008B]is[/COLOR] unchanged
config.status: creating pjmedia/include/pjmedia/config_auto.h
config.status: pjmedia/include/pjmedia/config_auto.h [COLOR=#00008B]is[/COLOR] unchanged
config.status: creating pjmedia/include/pjmedia-codec/config_auto.h
config.status: pjmedia/include/pjmedia-codec/config_auto.h [COLOR=#00008B]is[/COLOR] unchanged
config.status: creating pjsip/include/pjsip/sip_autoconf.h
config.status: pjsip/include/pjsip/sip_autoconf.h [COLOR=#00008B]is[/COLOR] unchanged


[COLOR=#2B91AF]Configurations[/COLOR] [COLOR=#00008B]for[/COLOR] current target have been written to [COLOR=#800000]'build.mak'[/COLOR], [COLOR=#00008B]and[/COLOR] [COLOR=#800000]'os-auto.mak'[/COLOR] [COLOR=#00008B]in[/COLOR] various build directories, [COLOR=#00008B]and[/COLOR] pjlib/include/pj/compat/os_auto.h.

[COLOR=#2B91AF]Further[/COLOR] customizations can be put [COLOR=#00008B]in[/COLOR]:
  - [COLOR=#800000]'user.mak'[/COLOR]
  - [COLOR=#800000]'pjlib/include/pj/config_site.h'[/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#2B91AF][FONT=Consolas]The[/FONT][/COLOR][COLOR=#00008B][FONT=Consolas]next[/FONT][/COLOR][FONT=Consolas] step now [/FONT][COLOR=#00008B][FONT=Consolas]is[/FONT][/COLOR][FONT=Consolas] to run [/FONT][COLOR=#800000][FONT=Consolas]'make dep'[/FONT][/COLOR][COLOR=#00008B][FONT=Consolas]and[/FONT][/COLOR][COLOR=#800000][FONT=Consolas]'make'[/FONT][/COLOR][FONT=Consolas].[/FONT][/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]

It seemed to me that the configuration was correct. I went, so the next step, causing the command make dep && make clean && make. Unfortunately, I encountered here wall to die. The program throws:

[/FONT][/COLOR]```
 make: *** No rule to make target `install'.  Stop.

 make: *** No rule to make target `dep'.  Stop.

 make: *** No rule to make target `clean'.  Stop.
```[COLOR=#000000][FONT=Arial]
PS. I also tried the same make command, and then just sudo make install. also avail
PS2. I'm not sure a good forum, if not please move this topic.[/FONT][/COLOR]

---

### Post by steeldriver on 2014-01-15
Hello and welcome to the forums

> 
[COLOR=#000000][FONT=Arial]changed paths ruthless ./ to ../ file both the performance and the rest other related configuration files

[/FONT][/COLOR]
What does this mean exactly? It sounds like you were just in the wrong directory when you tried to execute the original ./configure command.

---

### Post by koloryk on 2014-01-15
Because when I performed at the beginning of the command in Terminal ./configure-android, it threw an error:


> No such file or directory.


And for sure the file is in the directory above. I thought that Ubuntu recognizes ./ as the directory above, but did not, just as in that case the tutorial on the official website of the library is the syntax ./ instead of ../?

---

### Post by steeldriver on 2014-01-15
Yes but what did you actually **do**? Did you modify files, or cd to the above directory, or run '**..**/configure'?

The important thing now is where is the top level Makefile that was produced by the configure process? you need to execute the 'make' command from inside the same directory

---

### Post by koloryk on 2014-01-15
In fact, I tried to execute the command make from the directory above, but this time I get this message:

> Makefile: 1 build.mak: No such file or directory.
Makefile: 2 build/host-.mak: No such file or directory.
make *** No rule to make target `build/host-.mak'. Stop.

It turns out then that the configuration process does not proceed to the end successfully because some of the files as you can see none.


Please bear with us, I'm both new terms of use Ubuntu and compile from source.

@EDIT

[SIZE=2][FONT=arial][COLOR=#444444]The problem was solved. I just was doing the command 'make' in the directory 'pjsip', and you had to directory above. [/COLOR][/FONT][/SIZE]Thanks for help, the topic to close.

---

