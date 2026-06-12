---
title: "HOWTO: ATI Drivers with recompiled kernel"
date: 2004-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Evil_Homer on 2004-11-17
I found this on another forum and it worked for me

> First download the relevant source for whatever kernel you're using (e.g. 2.6.7) and unpack it to /usr/src/linux-2.6.7 and use the command ln -s /usr/src/linux-2.6.7 /usr/src/linux (or linux-2.4.26). Download the fglrx package from the ATI website and run alien fglrx_4.3.0-<version>.i386.rpm followed by dpkg -i --force-overwrite fglrx_4.3.0-<version>.i386.deb (the --force-overwrite switch is needed to overwrite libGL.so from the xlibmesa-gl package). Next compile the fglrx modules:

cd /lib/modules/fglrx/build_mod
chmod +x make.sh
./make.sh
cd ..
rmmod radeon
chmod +x make_install.sh
./make_install.sh
dpkg-divert --package fglrx --add /usr/X11R6/lib/libGL.so.1.2


The dpkg-divert will ensure that the xlibmesa-gl packages don't cause problems when being upgraded in future. Edit your /etc/X11/Xfree86Config-4 so that it used Driver "fglrx" instead of Driver "radeon". You'll also want to ensure that the default bit depth is 24, since the fglrx drivers don't provide 3D acceleration at any other depth.

---

### Post by jnaiman on 2004-11-18
How do I download a kernel? I'm a beginner, with a radeon 9550 and your instructions work up until I need a kernel in /usr/scr/linux . Any help is appreciated.

---

### Post by manadskort on 2005-05-15
I got the following error.

```
trafik@manadskort:/lib/modules/fglrx/build_mod # ./make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.11-1-k7/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6. x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.11-1-k7'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `firegl_stub_putm inor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:508: varning: `inter_module_p ut' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:510: varning: `inter_module_u nregister' is deprecated (declared at include/linux/module.h:574)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `firegl_stub_regi ster':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:530: varning: `inter_module_r egister' is deprecated (declared at include/linux/module.h:573)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:561: varning: `inter_module_p ut' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_get_vm_phys _addr':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1672: varning: passing arg 1 of `pmd_offset' from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `do_vm_shm_nopage ':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2202: varning: passing arg 1 of `pmd_offset' from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_vm_phys_add r_str':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2572: varning: passing arg 1 of `pmd_offset' from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: På toppnivå:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2660: varning: initiering fro m incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_vm_map':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2721: varning: implicit decla ration of function `remap_page_range'
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: På toppnivå:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2875: error: syntaxfel before  '*' token
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2875: varning: type defaults to `int' in declaration of `drm_agp_module_stub'
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2875: varning: data definitio n has no type or storage class
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_agpgart_ava ilable':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3017: error: `drm_agp_t' unde clared (first use in this function)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3017: error: (Each undeclared  identifier is reported only once
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3017: error: for each functio n it appears in.)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3017: error: syntaxfel before  ')' token
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3038: error: request for memb er `free_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3040: error: request for memb er `free_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3043: error: request for memb er `allocate_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3045: error: request for memb er `allocate_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3048: error: request for memb er `bind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3050: error: request for memb er `bind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3053: error: request for memb er `unbind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3055: error: request for memb er `unbind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3058: error: request for memb er `enable' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3060: error: request for memb er `enable' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3063: error: request for memb er `acquire' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3065: error: request for memb er `acquire' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3068: error: request for memb er `release' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3070: error: request for memb er `release' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3073: error: request for memb er `copy_info' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3075: error: request for memb er `copy_info' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_agp_uninit' :
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3157: varning: `inter_module_ put' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_agp_free_me mory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3190: error: request for memb er `free_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3191: error: request for memb er `free_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_agp_allocat e_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3200: error: request for memb er `allocate_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3201: error: request for memb er `allocate_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_agp_bind_me mory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3211: error: request for memb er `bind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3212: error: request for memb er `bind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_agp_unbind_ memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3222: error: request for memb er `unbind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3223: error: request for memb er `unbind_memory' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_agp_enable' :
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3233: error: request for memb er `enable' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3235: error: request for memb er `enable' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_agp_acquire ':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3281: error: request for memb er `acquire' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3282: error: request for memb er `acquire' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_agp_release ':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3292: error: request for memb er `release' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3293: error: request for memb er `release' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: I funktion `__ke_agp_copy_in fo':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3306: error: request for memb er `copy_info' in something not a structure or union
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3313: error: request for memb er `copy_info' in something not a structure or union
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o] Fel 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Fel 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.11-1-k7'
make: *** [kmod_build] Fel 2
build failed with return value 2
``` 

Anyone know what to do?

---

### Post by dresnu on 2005-05-31
Same issue with manadskort...

---

### Post by ChristopherHansen on 2005-06-09
[QUOTE=manadskort]I got the following error.[/QUOTE]


Excellent, same errors I had. Which means I should be able to help you.

If you are using 2.6.11 you will need [these](http://ati.cchtml.com/show_bug.cgi?id=110) patches. The site seems to be down at the moment so I have attached them.

---

### Post by manadskort on 2005-08-02
how to undo the dpkg-divert? did it and now i cant install nvidia drivers.

(yes i have a new card)

---

### Post by mjkelly on 2005-08-06
If someone could write a simple step by step howto for the 2.6.11 kernel on how to recompile it so fglrx would work correctly im sure alot of ppl would use it. Ive never recompiled a kernel at all but from what ive read it seems to be pretty difficult and it appears that one could really mess things up. But it also appears that fglrx will not work until breezy arrives in about 2 months, at least in my situation with a Radeon 9250, so might as well give it a shot.

---

### Post by salle on 2005-08-22
I noticed that if you have installed package xorg-driver-fglrx (using Hoary stock kernel like I had), you have to remove it before installing drivers using this HOWTO.
I don't know if it affects any other files, but after running command

"dpkg-divert --package fglrx --add /usr/X11R6/lib/libGL.so.1.2", it complains something about /usr/X11R6/lib/libGL.so.1.2 being dependent of xorg-driver-fglrx. At least it didn't work for me before I removed that package.

---

### Post by areguly on 2005-08-22
[QUOTE=ChristopherHansen]Excellent, same errors I had. Which means I should be able to help you.

If you are using 2.6.11 you will need [these](http://ati.cchtml.com/show_bug.cgi?id=110) patches. The site seems to be down at the moment so I have attached them.[/QUOTE]
 New ATI drivers are avaliable, they support 2.6.11 and 2.6.12, I have them running fine here.

go get them!

---

### Post by shizow on 2005-08-25
[QUOTE=Evil_Homer]I found this on another forum and it worked for me[/QUOTE]

where do i get the src for the standard hoary kernel 2.6.10-5-386 ???

---

### Post by Septor on 2005-08-25
[QUOTE=shizow]where do i get the src for the standard hoary kernel 2.6.10-5-386 ???[/QUOTE]

Note that you do not need the full kernel sources if you are just running the standard  Ubuntu kernel.  In this case you just need the the kernel headers pacakge which can be installed by:
```

sudo apt-get install linux-headers-`uname -r`

```

After that you should be all set to compile the fglrx drivers.

---

### Post by NaitoNeko on 2005-09-24
[QUOTE=Septor]Note that you do not need the full kernel sources if you are just running the standard  Ubuntu kernel.  In this case you just need the the kernel headers pacakge which can be installed by:
```

sudo apt-get install linux-headers-`uname -r`

```

After that you should be all set to compile the fglrx drivers.[/QUOTE]



i can not recompile the drivers...
```
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.12-9-amd64-k8/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-amd64-k8'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:124:25: asm/ioctl32.h: No existe el fichero o el directorio
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:498: aviso: `inter_module_put' es obsoleto (declarado en include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:500: aviso: `inter_module_unregister' es obsoleto (declarado en include/linux/module.h:565)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:520: aviso: `inter_module_register' es obsoleto (declarado en include/linux/module.h:564)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:551: aviso: `inter_module_put' es obsoleto (declarado en include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_get_user_ptr':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1067: aviso: asignación se crea un puntero desde un entero sin una conversión
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_put_user_ptr':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1099: aviso: conversión de puntero a entero de tamaño diferente
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1099: aviso: conversión de puntero a entero de tamaño diferente
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1099: aviso: conversión de puntero a entero de tamaño diferente
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1099: aviso: conversión de puntero a entero de tamaño diferente
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_verify_area':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1428: aviso: `verify_area' es obsoleto (declarado en include/asm/uaccess.h:54)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_register_ioctl32_conversion':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2177: aviso: declaración implícita de la función `register_ioctl32_conversion'
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_unregister_ioctl32_conversion':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2182: aviso: declaración implícita de la función `unregister_ioctl32_conversion'
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1921: aviso: se definió 'deferred_flush' pero no se usa
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-amd64-k8'
make: *** [kmod_build] Error 2
build failed with return value 2
``` 

Really i dont know how can i fix it..... the first time i use the ati installer, but some ".so" files werent overwriten. Then i uninstall everithing and tried an other form but i got this error, if someone can help i will be very gratefull....  :roll:

---

