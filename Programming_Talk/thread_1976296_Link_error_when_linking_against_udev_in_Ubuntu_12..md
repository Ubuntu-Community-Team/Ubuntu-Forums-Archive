---
title: "Link error when linking against udev in Ubuntu 12.04 with NetBeans"
date: 2012-05-08
forum: Programming Talk
---

### Post by sirgreendragon on 2012-05-08
I have a set of projects which I have been building on Ubuntu 10. Everything compiles and links fine using NetBeans 7.1.

I have begun to move to 12.04 with NetBeans 7.1.2 and I have link errors which I cannot figure out how to get rid of.

I have installed all the udev related updates/software packages which I can find using the older Synaptic Package Manager and the Ubuntu software center.

I use -ludev for my linker options and I am not getting an error saying that the library cannot be found, so the library is there and the linker is picking it up.

But I have these errors:

```

g++ -ludev -o dist/Debug/GNU-Linux-x86/hostmgr.linux build/Debug/GNU-Linux-x86/_ext/1472/main.o ../hostmgrlib.linux/dist/Debug/GNU-Linux-x86/libhostmgrlib.linux.a ../../../Common/ComponentFramework/dist/Debug/GNU-Linux-x86/libcomponentframework.a ../../parser/mxml.linux/dist/Debug/GNU-Linux-x86/libmxml.linux.a ../../parser/parser.linux/dist/Debug/GNU-Linux-x86/libparser.linux.a ../httpslib.linux/dist/Debug/GNU-Linux-x86/libhttpslib.linux.a ../../../Common/updater/updater.linux/dist/Debug/GNU-Linux-x86/libupdater.linux.a ../../../Common/collection/ccollection.linux/dist/Debug/GNU-Linux-x86/libccollection.linux.a ../../../Common/collection/collection.linux/dist/Debug/GNU-Linux-x86/libcollection.linux.a ../../../Common/company/company.linux/dist/Debug/GNU-Linux-x86/libcompany.linux.a ../../../Common/cpthread/cpthread.linux/dist/Debug/GNU-Linux-x86/libcpthread.linux.a ../../../Common/discovery/discovery.linux/dist/Debug/GNU-Linux-x86/libdiscovery.linux.a ../../../Common/httpclient/clientlib/httpclientlib.linux/dist/Debug/GNU-Linux-x86/libhttpclientlib.linux.a -lcurl ../../../Common/utility/utility.linux/dist/Debug/GNU-Linux-x86/libutility.linux.a ../../../Common/logger/logger.linux/dist/Debug/GNU-Linux-x86/liblogger.linux.a ../../../Common/cutility/cutility.linux/dist/Debug/GNU-Linux-x86/libcutility.linux.a ../../../Common/wcharhelper/wcharhelper.linux/dist/Debug/GNU-Linux-x86/libwcharhelper.linux.a -lpthread ../../../Common/settings/Settings.linux/dist/Debug/GNU-Linux-x86/libsettings.linux.a ../../parser/mxml-2.6/libmxml.a -luuid ../../corelogic/clhelper/clhelper.linux/dist/Debug/GNU-Linux-x86/libclhelper.linux.a 
../hostmgrlib.linux/dist/Debug/GNU-Linux-x86/libhostmgrlib.linux.a(hid.o): In function `copy_udev_string':
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:86: undefined reference to `udev_device_get_sysattr_value'
../hostmgrlib.linux/dist/Debug/GNU-Linux-x86/libhostmgrlib.linux.a(hid.o): In function `get_device_string':
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:170: undefined reference to `udev_new'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:179: undefined reference to `udev_device_new_from_devnum'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:183: undefined reference to `udev_device_get_parent_with_subsystem_devtype'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:188: undefined reference to `udev_device_get_sysattr_value'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:198: undefined reference to `udev_device_unref'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:201: undefined reference to `udev_unref'
../hostmgrlib.linux/dist/Debug/GNU-Linux-x86/libhostmgrlib.linux.a(hid.o): In function `hid_enumerate':
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:230: undefined reference to `udev_new'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:237: undefined reference to `udev_enumerate_new'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:238: undefined reference to `udev_enumerate_add_match_subsystem'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:239: undefined reference to `udev_enumerate_scan_devices'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:240: undefined reference to `udev_enumerate_get_list_entry'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:255: undefined reference to `udev_list_entry_get_name'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:256: undefined reference to `udev_device_new_from_syspath'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:257: undefined reference to `udev_device_get_devnode'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:265: undefined reference to `udev_device_get_parent_with_subsystem_devtype'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:275: undefined reference to `udev_device_get_sysattr_value'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:277: undefined reference to `udev_device_get_sysattr_value'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:323: undefined reference to `udev_device_get_sysattr_value'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:329: undefined reference to `udev_device_get_parent_with_subsystem_devtype'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:334: undefined reference to `udev_device_get_sysattr_value'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:342: undefined reference to `udev_device_unref'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:243: undefined reference to `udev_list_entry_get_next'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:348: undefined reference to `udev_enumerate_unref'
/mnt/hgfs/Client/Component/https/hostmgrlib.linux/../../HIDAPI/linux/hid.c:349: undefined reference to `udev_unref'
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/hostmgr.linux] Error 1
make[2]: Leaving directory `/media/sf_Client/Component/https/hostmgr.linux'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/media/sf_Client/Component/https/hostmgr.linux'
make: *** [.build-impl] Error 2
```

---

### Post by Bachstelze on 2012-05-08
[font=monospace]-l[/font] flags go at the end of the command line.

---

