---
title: "NDAS on AMD64"
date: 2008-01-31
forum: Packaging and Compiling Programs
---

### Post by lomm on 2008-01-31
Hello,

currently I'm trying to make the NDAS drivers work on amd64. I've downloaded and installed the current version as explained on [http://code.ximeta.com/cgi-bin/tracX.cgi/wiki/HowToBuildDEB](http://code.ximeta.com/cgi-bin/tracX.cgi/wiki/HowToBuildDEB) and tried to create a debian package for my amd64 ubuntu 7.10. Things have been running ok, until i got to the step 
m-a auto-install ndas
which obviously tries to compile the ndas-modules from src. Since there's no native 64-bit version, i was hoping i could compile the 32-bit on my amd64, but i got:

   gcc -Wp,-MD,/usr/src/modules/ndas/.ndas_sal_main.o.d  -nostdinc           
  -isystem /usr/lib/gcc/x86_64-linux-gnu/4.1.3/include -D__KERNEL__           
  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef                  
  -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2     
  -mtune=generic -m64 -mno-red-zone -mcmodel=kernel -pipe                     
  -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-time          
  -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -maccumulate-outgoing-args           
  -fomit-frame-pointer -g  -fno-stack-protector                               
  -Wdeclaration-after-statement -Wno-pointer-sign -DMODULE -DLINUX            
  -I/usr/src/modules/ndas/inc  -D_X86_64   -DMODULE -D"KBUILD_STR(s)=#s"      
  -D"KBUILD_BASENAME=KBUILD_STR(ndas_sal_main)"                               
  -D"KBUILD_MODNAME=KBUILD_STR(ndas_sal)" -c -o                               
  /usr/src/modules/ndas/.tmp_ndas_sal_main.o                                 
  /usr/src/modules/ndas/ndas_sal_main.c                                      
   ld -m elf_x86_64  -r -o /usr/src/modules/ndas/ndas_sal.o                  
  /usr/src/modules/ndas/sal/debug.o /usr/src/modules/ndas/sal/io.o           
  /usr/src/modules/ndas/sal/libc.o /usr/src/modules/ndas/sal/mem.o           
  /usr/src/modules/ndas/sal/net.o /usr/src/modules/ndas/sal/sal.o            
  /usr/src/modules/ndas/sal/sync.o /usr/src/modules/ndas/sal/thread.o        
  /usr/src/modules/ndas/sal/time.o /usr/src/modules/ndas/ndas_sal_main.o    
    ld -m elf_x86_64  -r -o /usr/src/modules/ndas/ndas_core.o               
  /usr/src/modules/ndas/ndas.o /usr/src/modules/ndas/ndas_core_main.o       
[COLOR="Red"]  ld: Relocatable linking with relocations from format elf32-i386           
  (/usr/src/modules/ndas/ndas.o) to format elf64-x86-64                     
  (/usr/src/modules/ndas/ndas_core.o) is not supported     [/COLOR]                 
  make[4]: *** [/usr/src/modules/ndas/ndas_core.o] Fehler 1                 
  make[3]: *** [_module_/usr/src/modules/ndas] Fehler 2                     
  make[3]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.22-14-generic'  
  make[2]: *** [/usr/src/modules/ndas/ndas_sal.ko] Fehler 2                 
  make[2]: Verlasse Verzeichnis '/usr/src/modules/ndas'                     
  make[1]: *** [binary-modules] Fehler 2                                    
  make[1]: Verlasse Verzeichnis '/usr/src/modules/ndas'                     
  make: *** [kdist_build] Fehler 2                            

Since the error message points me to the fact, that this is not 64-bit, i wanted to know if there's a way to make such a package, without intimate knowledge about the sources, e.g. is this just a matter of installing some more libraries to /lib32, or do i need to build this package completely differently (i've seen posts about building 32-bit applications for 64-bit with pbuilder), or am i completely on the wrong track (and should try to bother the ximeta people to finally develop their 64-bit linux-version, like all other before me there ;) )

I hope this is the right forum for this question, all help is very much appreciated.

---

### Post by hsjC on 2008-04-13
Please post more updates on this issue when you have news.

I have been working on this problem for  a while too. Ximeta should really release some 64bit drivers.

---

