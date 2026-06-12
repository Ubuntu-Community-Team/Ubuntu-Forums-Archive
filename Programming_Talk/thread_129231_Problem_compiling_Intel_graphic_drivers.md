---
title: "Problem compiling Intel graphic drivers"
date: 2006-02-13
forum: Programming Talk
---

### Post by delbene on 2006-02-13
I'm trying to compile the latest Intel graphic drivers ([http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=922&DwnldID=8203&strOSs=39&OSFullName=Linux*&#9001;=eng]("http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=922&DwnldID=8203&strOSs=39&OSFullName=Linux*&lang=eng")) for my [FONT=Arial][SIZE=2]82855GM chipset.
My */proc/version* is:
[/SIZE][/FONT]```
Linux version 2.6.12-10-686
gcc version 3.4.5 20050809 (prerelease)
(Ubuntu 3.4.4-6ubuntu8))
```

I get this two errors log:

dri.log
```
make -C /lib/modules/2.6.12-10-686/build SUBDIRS=/home/federico/downloads/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/federico/downloads/dripkg/agpgart-2.0/backend.o
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:69: error: conflicting types for 'agp_backend_acquire'
include/linux/agp_backend.h:105: error: previous declaration of 'agp_backend_acquire' was here
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:69: error: conflicting types for 'agp_backend_acquire'
include/linux/agp_backend.h:105: error: previous declaration of 'agp_backend_acquire' was here
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:89: error: conflicting types for 'agp_backend_release'
include/linux/agp_backend.h:106: error: previous declaration of 'agp_backend_release' was here
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:89: error: conflicting types for 'agp_backend_release'
include/linux/agp_backend.h:106: error: previous declaration of 'agp_backend_release' was here
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:220: error: parse error before "drm_agp"
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:220: warning: type defaults to `int' in declaration of `drm_agp'
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:221: warning: initialization makes integer from pointer without a cast
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:222: warning: excess elements in scalar initializer
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:222: warning: (near initialization for `drm_agp')
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:223: warning: excess elements in scalar initializer
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:223: warning: (near initialization for `drm_agp')
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:224: warning: excess elements in scalar initializer
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:224: warning: (near initialization for `drm_agp')
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:225: warning: excess elements in scalar initializer
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:225: warning: (near initialization for `drm_agp')
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:226: warning: excess elements in scalar initializer
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:226: warning: (near initialization for `drm_agp')
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:227: warning: excess elements in scalar initializer
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:227: warning: (near initialization for `drm_agp')
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:229: warning: excess elements in scalar initializer
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:229: warning: (near initialization for `drm_agp')
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:229: warning: data definition has no type or storage class
/home/federico/downloads/dripkg/agpgart-2.0/backend.c: In function `agp_add_bridge':
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:281: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:564)
/home/federico/downloads/dripkg/agpgart-2.0/backend.c: In function `agp_remove_bridge':
/home/federico/downloads/dripkg/agpgart-2.0/backend.c:301: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:565)
make[2]: *** [/home/federico/downloads/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/federico/downloads/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/federico/downloads/dripkg/drm'
make -C /lib/modules/2.6.12-10-686/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/federico/downloads/dripkg/drm/gdg_drv.o
In file included from /home/federico/downloads/dripkg/drm/gdg_drv.c:17:
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:47: error: parse error before '*' token
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:47: warning: type defaults to `int' in declaration of `drm_agp'
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:47: warning: data definition has no type or storage class
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_info':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:69: error: request for member `copy_info' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_acquire':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:111: error: request for member `acquire' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:117: error: request for member `acquire' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_release':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:140: error: request for member `release' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:142: error: request for member `release' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_do_release':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:155: error: request for member `release' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:156: error: request for member `release' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_enable':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:178: error: request for member `enable' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:185: error: request for member `enable' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_bind':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:333: error: request for member `bind_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_init':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:407: error: `drm_agp_t' undeclared (first use in this function)
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:407: error: (Each undeclared identifier is reported only once
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:407: error: for each function it appears in.)
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:407: error: parse error before ')' token
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:412: error: request for member `copy_info' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_uninit':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:436: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_allocate_memory':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:443: error: request for member `allocate_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:445: error: request for member `allocate_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_free_memory':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:451: error: request for member `free_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:453: error: request for member `free_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_bind_memory':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:460: error: request for member `bind_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:462: error: request for member `bind_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_unbind_memory':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:468: error: request for member `unbind_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:470: error: request for member `unbind_memory' in something not a structure or union
In file included from /home/federico/downloads/dripkg/drm/gdg_drv.c:28:
/home/federico/downloads/dripkg/drm/drm_memory.h: In function `drm_follow_page':
/home/federico/downloads/dripkg/drm/drm_memory.h:139: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
In file included from /home/federico/downloads/dripkg/drm/gdg_drv.c:30:
/home/federico/downloads/dripkg/drm/drm_vm.h: In function `gdg_mmap':
/home/federico/downloads/dripkg/drm/drm_vm.h:625: warning: implicit declaration of function `remap_page_range'
In file included from /home/federico/downloads/dripkg/drm/gdg_drv.c:31:
/home/federico/downloads/dripkg/drm/drm_stub.h: In function `gdg_stub_putminor':
/home/federico/downloads/dripkg/drm/drm_stub.h:145: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/home/federico/downloads/dripkg/drm/drm_stub.h:147: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:565)
/home/federico/downloads/dripkg/drm/drm_stub.h: In function `gdg_stub_register':
/home/federico/downloads/dripkg/drm/drm_stub.h:177: warning: implicit declaration of function `inter_module_get'
/home/federico/downloads/dripkg/drm/drm_stub.h:188: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:564)
make[3]: *** [/home/federico/downloads/dripkg/drm/gdg_drv.o] Error 1
make[2]: *** [_module_/home/federico/downloads/dripkg/drm] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/federico/downloads/dripkg/drm'
make: *** [gdg.ko] Error 2

```

tmp.log
```
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/federico/downloads/dripkg/drm'
make -C /lib/modules/2.6.12-10-686/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/federico/downloads/dripkg/drm/gdg_drv.o
In file included from /home/federico/downloads/dripkg/drm/gdg_drv.c:17:
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:47: error: parse error before '*' token
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:47: warning: type defaults to `int' in declaration of `drm_agp'
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:47: warning: data definition has no type or storage class
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_info':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:69: error: request for member `copy_info' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_acquire':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:111: error: request for member `acquire' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:117: error: request for member `acquire' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_release':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:140: error: request for member `release' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:142: error: request for member `release' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_do_release':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:155: error: request for member `release' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:156: error: request for member `release' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_enable':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:178: error: request for member `enable' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:185: error: request for member `enable' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_bind':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:333: error: request for member `bind_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_init':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:407: error: `drm_agp_t' undeclared (first use in this function)
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:407: error: (Each undeclared identifier is reported only once
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:407: error: for each function it appears in.)
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:407: error: parse error before ')' token
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:412: error: request for member `copy_info' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_uninit':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:436: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_allocate_memory':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:443: error: request for member `allocate_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:445: error: request for member `allocate_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_free_memory':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:451: error: request for member `free_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:453: error: request for member `free_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_bind_memory':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:460: error: request for member `bind_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:462: error: request for member `bind_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h: In function `gdg_agp_unbind_memory':
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:468: error: request for member `unbind_memory' in something not a structure or union
/home/federico/downloads/dripkg/drm/drm_agpsupport.h:470: error: request for member `unbind_memory' in something not a structure or union
In file included from /home/federico/downloads/dripkg/drm/gdg_drv.c:28:
/home/federico/downloads/dripkg/drm/drm_memory.h: In function `drm_follow_page':
/home/federico/downloads/dripkg/drm/drm_memory.h:139: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
In file included from /home/federico/downloads/dripkg/drm/gdg_drv.c:30:
/home/federico/downloads/dripkg/drm/drm_vm.h: In function `gdg_mmap':
/home/federico/downloads/dripkg/drm/drm_vm.h:625: warning: implicit declaration of function `remap_page_range'
In file included from /home/federico/downloads/dripkg/drm/gdg_drv.c:31:
/home/federico/downloads/dripkg/drm/drm_stub.h: In function `gdg_stub_putminor':
/home/federico/downloads/dripkg/drm/drm_stub.h:145: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/home/federico/downloads/dripkg/drm/drm_stub.h:147: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:565)
/home/federico/downloads/dripkg/drm/drm_stub.h: In function `gdg_stub_register':
/home/federico/downloads/dripkg/drm/drm_stub.h:177: warning: implicit declaration of function `inter_module_get'
/home/federico/downloads/dripkg/drm/drm_stub.h:188: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:564)
make[3]: *** [/home/federico/downloads/dripkg/drm/gdg_drv.o] Error 1
make[2]: *** [_module_/home/federico/downloads/dripkg/drm] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/federico/downloads/dripkg/drm'
make: *** [gdg.ko] Error 2
```

Any suggestion?

Thanks in advance.

---

### Post by Hephaistos on 2006-02-20
Hello!

I' m new ubuntu user(and linux in general), and i have the same stupid graphic card... My problem is i have a monitor that allows more than 1024*768, but there is no way i can change it (certainly because of the internal monitor)(even with all the good things i found on this forum).

I have been on the intel website to look for some drivers, and i found some, but i have no clue on what i should do with it :(, certainly compiling it, i heard about  "make"ing things but i really have no clue... The explainations in the read-me file are verry... inacurate i think.

Thanks for your help

---

### Post by delbene on 2006-02-21
Did you try adding the resolution you want to the */etc/X11/xorg.conf* file?

---

