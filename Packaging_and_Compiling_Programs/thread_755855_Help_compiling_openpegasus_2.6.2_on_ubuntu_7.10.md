---
title: "Help compiling openpegasus 2.6.2 on ubuntu 7.10"
date: 2008-04-15
forum: Packaging and Compiling Programs
---

### Post by bigeyes0x0 on 2008-04-15
I don't know why but I get this error during compiling openpegasus

```
make[3]: Entering directory `/home/thuan/compile/pegasus/src/Pegasus/ProviderManager2/CMPIR/daemon'
cc -c -o /home/thuan/obj/Pegasus/ProviderManager2/CMPIR/daemon/daemon.o -W -Wall -Wno-unused -D_GNU_SOURCE -DTHREAD_SAFE -D_REENTRANT -s -O2 -m32 -fvisibility=hidden -fPIE  -DPEGASUS_INTERNALONLY -DPEGASUS_DEFAULT_CMPIR -DDEBUG  -DPEGASUS_PLATFORM_LINUX_GENERIC_GNU -DPEGASUS_PLATFORM_LINUX_IX86_GNU -DPEGASUS_USE_SYSLOGS -DPEGASUS_HAS_SIGNALS -DPEGASUS_PAM_AUTHENTICATION -DPEGASUS_NO_PASSWORDFILE -DPEGASUS_ARCH_LIB=\"lib\" -DNDEBUG -DPEGASUS_ENABLE_USERGROUP_AUTHORIZATION -DPEGASUS_DEFAULT_ENABLE_OOP -DPEGASUS_DISABLE_LOCAL_DOMAIN_SOCKET -DPEGASUS_EMBEDDED_INSTANCE_SUPPORT -DPEGASUS_ENABLE_SSL_CRL_VERIFICATION -DPEGASUS_ENABLE_SLP -DPEGASUS_USE_EXPERIMENTAL_INTERFACES -DPEGASUS_USE_DEPRECATED_INTERFACES -DPEGASUS_ENABLE_CMPI_PROVIDER_MANAGER -DPEGASUS_ENABLE_REMOTE_CMPI -DPEGASUS_USE_RELEASE_CONFIG_OPTIONS -DPEGASUS_USE_RELEASE_DIRS -DPEGASUS_DEST_LIB_DIR=\"lib\" -DPLATFORM_COMPONENT_NAME=\"CMPIRDaemon\"  -I/home/thuan/compile/pegasus/src  -I .. -I ../native daemon.c

g++ -W -Wall -Wno-unused -D_GNU_SOURCE -DTHREAD_SAFE -D_REENTRANT -s -O2 -m32 -fvisibility=hidden -fPIE  -Xlinker -rpath -Xlinker lib -Xlinker -rpath-link -Xlinker /home/thuan/lib -L/home/thuan/lib -o /home/thuan/bin/CMPIRDaemon /home/thuan/obj/Pegasus/ProviderManager2/CMPIR/daemon/daemon.o -lCMPIRNative -lCMPIRTCPCommRemote -ldl -lpthread -lcrypt -lpam
/home/thuan/obj/Pegasus/ProviderManager2/CMPIR/daemon/daemon.o: In function `main':
daemon.c:(.text+0xa8): undefined reference to `open_connection'
daemon.c:(.text+0xd8): undefined reference to `binarySerializerFT'
daemon.c:(.text+0x206): undefined reference to `native_new_CMPIContext'
daemon.c:(.text+0x20e): undefined reference to `init_activation_context'
daemon.c:(.text+0x21c): undefined reference to `tool_mm_load_lib'
daemon.c:(.text+0x258): undefined reference to `cleanup_remote_brokers'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `native_new_CMPIResult'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `find_remote_broker'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `get_indicationObject'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `native_release_CMPISelectExp'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `native_brokerEncFT'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `native_new_CMPIString'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `native_result2array'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `create_indicationObject'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `native_release_CMPIContext'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `native_new_CMPIEnumeration'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `tool_mm_get_broker'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `tool_mm_set_broker'
/home/thuan/lib/libCMPIRTCPCommRemote.so: undefined reference to `CMPI_BrokerExt_Ftab'
collect2: ld returned 1 exit status
make[3]: *** [/home/thuan/bin/CMPIRDaemon] Error 1
make[3]: Leaving directory `/home/thuan/compile/pegasus/src/Pegasus/ProviderManager2/CMPIR/daemon'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/thuan/compile/pegasus/src/Pegasus'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/thuan/compile/pegasus/src'
make: *** [all] Error 2
```
cc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
g++ (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Any one knows why, please help.

---

