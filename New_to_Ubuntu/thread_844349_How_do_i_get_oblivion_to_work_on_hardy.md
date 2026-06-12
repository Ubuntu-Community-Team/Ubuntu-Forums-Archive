---
title: "How do i get oblivion to work on hardy?"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by khr on 2008-06-29
When I run the game from the "shortcut" in my desktop, the launcher just comes up and then it disappears. When I hover over the launcher with my mouse, my mouse just disappears. When I go to the directory where the OblivionLauncher is and then "wine OblivionLauncher.exe" i just get:

```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:win:SetLayeredWindowAttributes (0x10024,0x00000000,0,2): stub!
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7d73283 (thread 0009), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7d73283).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d73283 ESP:7f21f270 EBP:7f21f28c EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:b7e4bff4 ECX:00000000 EDX:00000000
 ESI:00000033 EDI:00000000
Stack dump:
0x7f21f270:  b7d72fc5 00000000 00000087 00000087
0x7f21f280:  7e89c914 00000033 00000000 7f21f30c
0x7f21f290:  7e860d32 00000000 00000087 7baa9cc0
0x7f21f2a0:  00000001 00000000 7f000000 00000002
0x7f21f2b0:  7bc89704 7baa9cc0 7c0715d8 00000087
0x7f21f2c0:  7ec68cec 00000001 7f0461c8 7f21f2fc
Backtrace:
=>1 0xb7d73283 strlen+0x33() in libc.so.6 (0x7f21f28c)
  2 0x7e860d32 in winex11 (+0x40d32) (0x7f21f30c)
  3 0x7e862647 X11DRV_wglGetProcAddress+0x27() in winex11 (0x7f21f34c)
  4 0x7ec49d6d wglGetProcAddress+0x6d() in gdi32 (0x7f21f37c)
  5 0x7e2c3705 InitAdapters+0x155() in wined3d (0x7f21f7dc)
  6 0x7e334c92 WineDirect3DCreate+0x22() in wined3d (0x7f21f80c)
  7 0x7e37a4c7 Direct3DCreate9+0x77() in d3d9 (0x7f21f83c)
  8 0x0040812f in oblivionlauncher (+0x812f) (0x7f21fca4)
  9 0x0040446e in oblivionlauncher (+0x446e) (0x7e370000)
0xb7d73283 strlen+0x33 in libc.so.6: movl	0x0(%eax),%ecx
Modules:
Module	Address			Debug info	Name (79 modules)
PE	  400000-  5d9000	Export          oblivionlauncher
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7cd86000-7cd8f000	Deferred        librt.so.1
ELF	7cd8f000-7dd9a000	Deferred        fglrx_dri.so
ELF	7dd9a000-7dda5000	Deferred        libgcc_s.so.1
ELF	7dda5000-7de1f000	Deferred        libgl.so.1
ELF	7e114000-7e133000	Deferred        imm32<elf>
  \-PE	7e120000-7e133000	\               imm32
ELF	7e264000-7e365000	Export          wined3d<elf>
  \-PE	7e280000-7e365000	\               wined3d
ELF	7e365000-7e395000	Export          d3d9<elf>
  \-PE	7e370000-7e395000	\               d3d9
ELF	7e3b9000-7e3cc000	Deferred        libresolv.so.2
ELF	7e3de000-7e3fc000	Deferred        iphlpapi<elf>
  \-PE	7e3e0000-7e3fc000	\               iphlpapi
ELF	7e3fc000-7e45c000	Deferred        rpcrt4<elf>
  \-PE	7e410000-7e45c000	\               rpcrt4
ELF	7e45c000-7e500000	Deferred        ole32<elf>
  \-PE	7e470000-7e500000	\               ole32
ELF	7e515000-7e529000	Deferred        midimap<elf>
  \-PE	7e520000-7e529000	\               midimap
ELF	7e529000-7e54f000	Deferred        msacm32<elf>
  \-PE	7e530000-7e54f000	\               msacm32
ELF	7e54f000-7e566000	Deferred        msacm32<elf>
  \-PE	7e550000-7e566000	\               msacm32
ELF	7e566000-7e629000	Deferred        libasound.so.2
ELF	7e63b000-7e671000	Deferred        winealsa<elf>
  \-PE	7e640000-7e671000	\               winealsa
ELF	7e671000-7e6a3000	Deferred        uxtheme<elf>
  \-PE	7e680000-7e6a3000	\               uxtheme
ELF	7e6a3000-7e6ac000	Deferred        libxcursor.so.1
ELF	7e6ac000-7e6b1000	Deferred        libxfixes.so.3
ELF	7e6b1000-7e6b4000	Deferred        libxcomposite.so.1
ELF	7e6b4000-7e6ba000	Deferred        libxrandr.so.2
ELF	7e6ba000-7e6c2000	Deferred        libxrender.so.1
ELF	7e6c2000-7e6c5000	Deferred        libxinerama.so.1
ELF	7e6c5000-7e6ca000	Deferred        libxdmcp.so.6
ELF	7e6ca000-7e6e2000	Deferred        libxcb.so.1
ELF	7e6e2000-7e6e4000	Deferred        libxcb-xlib.so.0
ELF	7e6e4000-7e6e7000	Deferred        libxau.so.6
ELF	7e6e7000-7e7ce000	Deferred        libx11.so.6
ELF	7e7ce000-7e7dc000	Deferred        libxext.so.6
ELF	7e7dc000-7e7e1000	Deferred        libxxf86vm.so.1
ELF	7e7e1000-7e7f9000	Deferred        libice.so.6
ELF	7e7f9000-7e801000	Deferred        libsm.so.6
ELF	7e813000-7e8a4000	Export          winex11<elf>
  \-PE	7e820000-7e8a4000	\               winex11
ELF	7e8c2000-7e8e3000	Deferred        libexpat.so.1
ELF	7e8e3000-7e90d000	Deferred        libfontconfig.so.1
ELF	7e90d000-7e922000	Deferred        libz.so.1
ELF	7e922000-7e992000	Deferred        libfreetype.so.6
ELF	7e9a4000-7e9fd000	Deferred        shlwapi<elf>
  \-PE	7e9b0000-7e9fd000	\               shlwapi
ELF	7e9fd000-7eb07000	Deferred        shell32<elf>
  \-PE	7ea10000-7eb07000	\               shell32
ELF	7eb07000-7eb95000	Deferred        winmm<elf>
  \-PE	7eb10000-7eb95000	\               winmm
ELF	7eb95000-7ebe6000	Deferred        advapi32<elf>
  \-PE	7eba0000-7ebe6000	\               advapi32
ELF	7ebe6000-7ec81000	Export          gdi32<elf>
  \-PE	7ec00000-7ec81000	\               gdi32
ELF	7ec81000-7edc7000	Deferred        user32<elf>
  \-PE	7eca0000-7edc7000	\               user32
ELF	7edc7000-7ee86000	Deferred        comctl32<elf>
  \-PE	7edd0000-7ee86000	\               comctl32
ELF	7efa6000-7efb1000	Deferred        libnss_files.so.2
ELF	7efb1000-7efc9000	Deferred        libnsl.so.1
ELF	7efc9000-7efee000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cf3000-b7cfc000	Deferred        libnss_compat.so.2
ELF	b7cfd000-b7d01000	Deferred        libdl.so.2
ELF	b7d01000-b7e50000	Export          libc.so.6
ELF	b7e51000-b7e69000	Deferred        libpthread.so.0
ELF	b7e7b000-b7f90000	Deferred        libwine.so.1
ELF	b7f92000-b7fae000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Bethesda Softworks\Oblivion\OblivionLauncher.exe
	0000001b   15
	00000018   15
	00000009    0 <==
0000000c 
	00000017    0
	00000016    0
	00000011    0
	00000010    0
	0000000e    0
	0000000d    0
00000012 
	00000015    0
	00000014    0
	00000013    0
00000019 
	0000001c    0
	0000001a    0
Backtrace:
=>1 0xb7d73283 strlen+0x33() in libc.so.6 (0x7f21f28c)
  2 0x7e860d32 in winex11 (+0x40d32) (0x7f21f30c)
  3 0x7e862647 X11DRV_wglGetProcAddress+0x27() in winex11 (0x7f21f34c)
  4 0x7ec49d6d wglGetProcAddress+0x6d() in gdi32 (0x7f21f37c)
  5 0x7e2c3705 InitAdapters+0x155() in wined3d (0x7f21f7dc)
  6 0x7e334c92 WineDirect3DCreate+0x22() in wined3d (0x7f21f80c)
  7 0x7e37a4c7 Direct3DCreate9+0x77() in d3d9 (0x7f21f83c)
  8 0x0040812f in oblivionlauncher (+0x812f) (0x7f21fca4)
  9 0x0040446e in oblivionlauncher (+0x446e) (0x7e370000)
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```

What should i do?

btw.
Ubuntu Hardy
ATi Mobility Radeon X1600 256MB
Intel Core 2 Duo
1GB RAM
wine version 0.9.59

---

### Post by Canis familiaris on 2008-06-29
Perhaps this may help:
(Found by a quick google search)
[http://ubuntuforums.org/showthread.php?t=349764](http://ubuntuforums.org/showthread.php?t=349764)

But it may not work still due to version change in WINE. Worth trying though.

---

### Post by khr on 2008-06-29
> **Anurag_panda said:**
> Perhaps this may help:
(Found by a quick google search)
[http://ubuntuforums.org/showthread.php?t=349764](http://ubuntuforums.org/showthread.php?t=349764)

But it may not work still due to version change in WINE. Worth trying though.

Thanks, I'll look at that now.

---

### Post by khr on 2008-06-29
The tutorial didn't work at all, probably since it's outdated.
I just hope that this isn't a rare bug...

PLEASE, help me...

---

### Post by khr on 2008-06-29
Now, Diablo 2 Lord of destruction don't work either...
When i try to launch it from the shortcut in the desktop i just get

UNHANDLED EXCEPTION:
ACCESS_VIOLATION (c0000005)

At least steam is working.

Anyway, I'll deal with that later.
I just want to get Oblivion to work...

Ops! Sorry for the triple post, i forgot the existence of the edit button.

---

### Post by Marshal0505 on 2008-06-29
I can't solve your problem (don't even know the game) But i'd check wine's appdb for updated info on how to run this game.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by khr on 2008-06-29
> **Marshal0505 said:**
> I can't solve your problem (don't even know the game) But i'd check wine's appdb for updated info on how to run this game.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Nothing there helped, except that it told me that I had an outdated version of Wine, so thanks for that. :)

After I updated Wine, it still won't work, so please help!

wine 1.1.0

---

### Post by Marshal0505 on 2008-06-29
> **khr said:**
> Nothing there helped, except that it told me that I had an outdated version of Wine, so thanks for that. :)

After I updated Wine, it still won't work, so please help!

wine 1.1.0

I'm sorry to hear that :( hope there is someone here that can help you.if not you might want to consider making a new post in the 'wine' section of this forum.As there are bound to be more ppl there running this game in wine :)

---

### Post by khr on 2008-06-29
I didn't know there was a wine section here...
Thanks, I'll try to ask there in a while.

---

