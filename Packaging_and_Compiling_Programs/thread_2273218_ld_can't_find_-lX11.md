---
title: "ld can't find -lX11"
date: 2015-04-11
forum: Packaging and Compiling Programs
---

### Post by tdogmonster1337 on 2015-04-11
Hello, I am trying to get a program to compile with make, and errors out and quits on me with an ld error.

```
make -C maker
make[1]: Entering directory `/home/theblackmidimasta/BASS/miditest/jost-v0.5.4/vst-bridge-master/maker'
gcc -D_GNU_SOURCE  -W -Wall -Wstrict-prototypes -pipe -Wfloat-equal -Wundef -Wshadow -Wpointer-arith -Wmissing-declarations -Wnested-externs -Wmissing-prototypes -g maker.c -lmagic -o vst-bridge-maker
make[1]: Leaving directory `/home/theblackmidimasta/BASS/miditest/jost-v0.5.4/vst-bridge-master/maker'
make -C plugin
make[1]: Entering directory `/home/theblackmidimasta/BASS/miditest/jost-v0.5.4/vst-bridge-master/plugin'
g++ -D_GNU_SOURCE  -W -Wall -pipe -Wundef -Wshadow -Wpointer-arith -Wabi -g -shared -fPIC plugin.cc -o vst-bridge-plugin-tpl.so -lX11 -lXcomposite
In file included from ../vstsdk2.4/pluginterfaces/vst2.x/aeffectx.h:40:0,
                 from plugin.cc:43:
../vstsdk2.4/pluginterfaces/vst2.x/aeffect.h:57:5: warning: "TARGET_API_MAC_CARBON" is not defined [-Wundef]
 #if TARGET_API_MAC_CARBON
     ^
In file included from ../vstsdk2.4/pluginterfaces/vst2.x/aeffectx.h:40:0,
                 from plugin.cc:43:
../vstsdk2.4/pluginterfaces/vst2.x/aeffect.h:120:28: warning: "_WIN64" is not defined [-Wundef]
 #define VST_64BIT_PLATFORM _WIN64 || __LP64__
                            ^
../vstsdk2.4/pluginterfaces/vst2.x/aeffect.h:144:5: note: in expansion of macro ‘VST_64BIT_PLATFORM’
 #if VST_64BIT_PLATFORM
     ^
../vstsdk2.4/pluginterfaces/vst2.x/aeffect.h:384:5: warning: "TARGET_API_MAC_CARBON" is not defined [-Wundef]
 #if TARGET_API_MAC_CARBON
     ^
In file included from plugin.cc:43:0:
../vstsdk2.4/pluginterfaces/vst2.x/aeffectx.h:45:5: warning: "TARGET_API_MAC_CARBON" is not defined [-Wundef]
 #if TARGET_API_MAC_CARBON
     ^
In file included from plugin.cc:43:0:
../vstsdk2.4/pluginterfaces/vst2.x/aeffectx.h:1161:5: warning: "TARGET_API_MAC_CARBON" is not defined [-Wundef]
 #if TARGET_API_MAC_CARBON
     ^
plugin.cc: In function ‘VstIntPtr vst_bridge_call_effect_dispatcher2(AEffect*, VstInt32, VstInt32, VstIntPtr, void*, float)’:
plugin.cc:622:12: warning: declaration of ‘len’ shadows a previous local [-Wshadow]
     size_t len = 8 + ar->numChannels * sizeof (ar->speakers[0]);
            ^
plugin.cc:347:11: warning: shadowed declaration is here [-Wshadow]
   ssize_t len;
           ^
plugin.cc:39:48: warning: format ‘%p’ expects argument of type ‘void*’, but argument 3 has type ‘pthread_t {aka long unsigned int}’ [-Wformat=]
     fprintf(g_log ? : stderr, "[CRIT] P: " Args);       \
                                                ^
plugin.cc:683:5: note: in expansion of macro ‘CRIT’
     CRIT("[%p] !!!!!!!!!! UNHANDLED effect_dispatcher(%s, %d, %d, %p, %f)\n",
     ^
plugin.cc:39:48: warning: format ‘%d’ expects argument of type ‘int’, but argument 6 has type ‘VstIntPtr {aka long int}’ [-Wformat=]
     fprintf(g_log ? : stderr, "[CRIT] P: " Args);       \
                                                ^
plugin.cc:683:5: note: in expansion of macro ‘CRIT’
     CRIT("[%p] !!!!!!!!!! UNHANDLED effect_dispatcher(%s, %d, %d, %p, %f)\n",
     ^
plugin.cc:39:48: warning: format ‘%f’ expects a matching ‘double’ argument [-Wformat=]
     fprintf(g_log ? : stderr, "[CRIT] P: " Args);       \
                                                ^
plugin.cc:683:5: note: in expansion of macro ‘CRIT’
     CRIT("[%p] !!!!!!!!!! UNHANDLED effect_dispatcher(%s, %d, %d, %p, %f)\n",
     ^
plugin.cc:347:11: warning: unused variable ‘len’ [-Wunused-variable]
   ssize_t len;
           ^
make[1]: Leaving directory `/home/theblackmidimasta/BASS/miditest/jost-v0.5.4/vst-bridge-master/plugin'
make -C host
make[1]: Entering directory `/home/theblackmidimasta/BASS/miditest/jost-v0.5.4/vst-bridge-master/host'
wineg++ -m32 -D_GNU_SOURCE  -W -Wall -pipe -Wundef -Wshadow -Wpointer-arith -Wabi -g host.cc -lpthread -lshell32 -lws2_32 -lX11 -o vst-bridge-host-32.exe
In file included from ../vstsdk2.4/pluginterfaces/vst2.x/aeffectx.h:40:0,
                 from host.cc:23:
../vstsdk2.4/pluginterfaces/vst2.x/aeffect.h:57:5: warning: "TARGET_API_MAC_CARBON" is not defined [-Wundef]
 #if TARGET_API_MAC_CARBON
     ^
In file included from ../vstsdk2.4/pluginterfaces/vst2.x/aeffectx.h:40:0,
                 from host.cc:23:
../vstsdk2.4/pluginterfaces/vst2.x/aeffect.h:120:28: warning: "_WIN64" is not defined [-Wundef]
 #define VST_64BIT_PLATFORM _WIN64 || __LP64__
                            ^
../vstsdk2.4/pluginterfaces/vst2.x/aeffect.h:144:5: note: in expansion of macro ‘VST_64BIT_PLATFORM’
 #if VST_64BIT_PLATFORM
     ^
../vstsdk2.4/pluginterfaces/vst2.x/aeffect.h:120:38: warning: "__LP64__" is not defined [-Wundef]
 #define VST_64BIT_PLATFORM _WIN64 || __LP64__
                                      ^
../vstsdk2.4/pluginterfaces/vst2.x/aeffect.h:144:5: note: in expansion of macro ‘VST_64BIT_PLATFORM’
 #if VST_64BIT_PLATFORM
     ^
../vstsdk2.4/pluginterfaces/vst2.x/aeffect.h:384:5: warning: "TARGET_API_MAC_CARBON" is not defined [-Wundef]
 #if TARGET_API_MAC_CARBON
     ^
In file included from host.cc:23:0:
../vstsdk2.4/pluginterfaces/vst2.x/aeffectx.h:45:5: warning: "TARGET_API_MAC_CARBON" is not defined [-Wundef]
 #if TARGET_API_MAC_CARBON
     ^
In file included from host.cc:23:0:
../vstsdk2.4/pluginterfaces/vst2.x/aeffectx.h:1161:5: warning: "TARGET_API_MAC_CARBON" is not defined [-Wundef]
 #if TARGET_API_MAC_CARBON
     ^
/usr/bin/ld: cannot find -lX11
collect2: error: ld returned 1 exit status
winegcc: g++ failed
make[1]: *** [vst-bridge-host-32.exe] Error 2
make[1]: Leaving directory `/home/theblackmidimasta/BASS/miditest/jost-v0.5.4/vst-bridge-master/host'
make: *** [all] Error 2

```

Can anyone help me? What package provides -lX11? Or do I have to make a symbolic link? :confused:

Please help!

---

### Post by steeldriver on 2015-04-11
The package that provides the X11 headers and development libraries is libx11-dev

For a larger (superset) of X11 dev related stuff, you could install xorg-dev instead

---

