---
title: "wine - could load game"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by benste on 2008-04-26
Hy guys, I tried to install some games with wine. Several games are runnign smoothy and better tahn in windows :-)
but some games doesn't load:

1. Star Wars Battlefront -> white window where normally should be the starmenu of the game + installed something like "gecko" automaticly, but doesn't work - can you help me?

2. [http://emergency4.de/en/](http://emergency4.de/en/) -> I'm using the german edition.
I tried to start up, but only one balckscreen 1024x800 appeared. Then it closed automaticlay. I typed the wine prefix thing into gnome-terminal and I did have the following output after the black screen:

--> can you help me to do something against this error?

```
benste@vaiofe31m:~$ env WINEPREFIX="/home/benste/.wine" wine "C:\Programme\sixteen tons entertainment\Emergency4\Em4.exe"
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:win:EnumDisplayDevicesW ((null),0,0x7f31f4dc,0x00000000), stub!
fixme:quartz:AsyncReader_FindPin (L"Output", 0x7f31f8f4)
fixme:quartz:AsyncReader_FindPin (L"Output", 0x7f31f8f4)
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
fixme:quartz:AsyncReader_FindPin (L"Output", 0x7f31f6d0)
wine: Unhandled page fault on read access to 0x000000f8 at address 0x6fe2cd (thread 0009), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on read access to 0x000000f8 in 32-bit code (0x006fe2cd).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:006fe2cd ESP:7f31f8b0 EBP:00000004 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:79704900 ECX:00000000 EDX:77a97308
 ESI:77aa0b78 EDI:7f31fa24
Stack dump:
0x7f31f8b0:  77aa0b78 79704910 00a02a60 00000000
0x7f31f8c0:  00000000 00000001 00a02a60 00000000
0x7f31f8d0:  00000000 77aa0b01 7f31f8f4 009aa820
0x7f31f8e0:  ffffffff 0093b0b3 ffffffff 0093fdb8
0x7f31f8f0:  77aa0b78 7f31f910 009bc86a ffffffff
0x7f31f900:  006f6ffe 00000000 ffffffff 77aa0b78
Backtrace:
0x006fe2cd: movl	0xf8(%ecx),%ecx
Modules:
Module	Address			Debug info	Name (128 modules)
PE	  400000-  e08000	Export          em4
PE	10000000-10291000	Deferred        vision71
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7b95e000-7ba00000	Deferred        oleaut32<elf>
  \-PE	7b970000-7ba00000	\               oleaut32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7bf9c000-7c000000	Deferred        quartz<elf>
  \-PE	7bfb0000-7c000000	\               quartz
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
ELF	7c42e000-7c442000	Deferred        lz32<elf>
  \-PE	7c430000-7c442000	\               lz32
ELF	7c442000-7c46a000	Deferred        msvfw32<elf>
  \-PE	7c450000-7c46a000	\               msvfw32
ELF	7c6ce000-7c7cf000	Deferred        wined3d<elf>
  \-PE	7c6e0000-7c7cf000	\               wined3d
ELF	7c7cf000-7c7fa000	Deferred        d3d8<elf>
  \-PE	7c7e0000-7c7fa000	\               d3d8
ELF	7ca0b000-7ca2a000	Deferred        imm32<elf>
  \-PE	7ca10000-7ca2a000	\               imm32
ELF	7ca2a000-7caed000	Deferred        libasound.so.2
ELF	7cd5c000-7cd75000	Deferred        version<elf>
  \-PE	7cd60000-7cd75000	\               version
ELF	7cd75000-7cd89000	Deferred        midimap<elf>
  \-PE	7cd80000-7cd89000	\               midimap
ELF	7cd89000-7cdaf000	Deferred        msacm32<elf>
  \-PE	7cd90000-7cdaf000	\               msacm32
ELF	7cdaf000-7cdc6000	Deferred        msacm32<elf>
  \-PE	7cdb0000-7cdc6000	\               msacm32
ELF	7cdc6000-7cdfc000	Deferred        winealsa<elf>
  \-PE	7cdd0000-7cdfc000	\               winealsa
ELF	7d141000-7d145000	Deferred        libgpg-error.so.0
ELF	7d145000-7d192000	Deferred        libgcrypt.so.11
ELF	7d192000-7d1a2000	Deferred        libtasn1.so.3
ELF	7d1a2000-7d1aa000	Deferred        libkrb5support.so.0
ELF	7d1aa000-7d1dc000	Deferred        libcrypt.so.1
ELF	7d1dc000-7d251000	Deferred        libgnutls.so.13
ELF	7d251000-7d274000	Deferred        libk5crypto.so.3
ELF	7d274000-7d301000	Deferred        libkrb5.so.3
ELF	7d301000-7d32a000	Deferred        libgssapi_krb5.so.2
ELF	7d32a000-7d35d000	Deferred        libcups.so.2
ELF	7d3bb000-7d3ed000	Deferred        uxtheme<elf>
  \-PE	7d3c0000-7d3ed000	\               uxtheme
ELF	7d3ed000-7d3f6000	Deferred        libxcursor.so.1
ELF	7d3f6000-7d3fb000	Deferred        libxfixes.so.3
ELF	7d3fb000-7d3fe000	Deferred        libxcomposite.so.1
ELF	7d3fe000-7d404000	Deferred        libxrandr.so.2
ELF	7d404000-7d40c000	Deferred        libxrender.so.1
ELF	7d40f000-7d412000	Deferred        libkeyutils.so.1
ELF	7d41c000-7d41f000	Deferred        libcom_err.so.2
ELF	7d421000-7d4b2000	Deferred        winex11<elf>
  \-PE	7d430000-7d4b2000	\               winex11
ELF	7d4f1000-7d512000	Deferred        libexpat.so.1
ELF	7d512000-7d53c000	Deferred        libfontconfig.so.1
ELF	7d53c000-7d551000	Deferred        libz.so.1
ELF	7d551000-7d5c1000	Deferred        libfreetype.so.6
ELF	7d5d6000-7d60d000	Deferred        dinput<elf>
  \-PE	7d5e0000-7d60d000	\               dinput
ELF	7d60d000-7d625000	Deferred        dinput8<elf>
  \-PE	7d610000-7d625000	\               dinput8
ELF	7d625000-7d651000	Deferred        ws2_32<elf>
  \-PE	7d630000-7d651000	\               ws2_32
ELF	7d651000-7d6df000	Deferred        winmm<elf>
  \-PE	7d660000-7d6df000	\               winmm
ELF	7d6df000-7d729000	Deferred        dsound<elf>
  \-PE	7d6f0000-7d729000	\               dsound
ELF	7d729000-7d73f000	Deferred        glu32<elf>
  \-PE	7d730000-7d73f000	\               glu32
ELF	7d7a3000-7d7a8000	Deferred        libxdmcp.so.6
ELF	7d7a8000-7d7b3000	Deferred        libgcc_s.so.1
ELF	7d8a6000-7d8a8000	Deferred        libnvidia-tls.so.1
ELF	7d8a8000-7e3bd000	Deferred        libglcore.so.1
ELF	7e3bd000-7e3d5000	Deferred        libxcb.so.1
ELF	7e3d5000-7e3d8000	Deferred        libxau.so.6
ELF	7e3d8000-7e45b000	Deferred        libglu.so.1
ELF	7e45b000-7e4ff000	Deferred        libgl.so.1
ELF	7e4ff000-7e5e6000	Deferred        libx11.so.6
ELF	7e5e6000-7e5f4000	Deferred        libxext.so.6
ELF	7e5f4000-7e60c000	Deferred        libice.so.6
ELF	7e60c000-7e614000	Deferred        libsm.so.6
ELF	7e614000-7e695000	Deferred        opengl32<elf>
  \-PE	7e630000-7e695000	\               opengl32
ELF	7e695000-7e6cb000	Deferred        winspool<elf>
  \-PE	7e6a0000-7e6cb000	\               winspool
ELF	7e6cb000-7e774000	Deferred        comdlg32<elf>
  \-PE	7e6d0000-7e774000	\               comdlg32
ELF	7e774000-7e833000	Deferred        comctl32<elf>
  \-PE	7e780000-7e833000	\               comctl32
ELF	7e833000-7e93d000	Deferred        shell32<elf>
  \-PE	7e840000-7e93d000	\               shell32
ELF	7e93d000-7e95e000	Deferred        mpr<elf>
  \-PE	7e940000-7e95e000	\               mpr
ELF	7e95e000-7e9ac000	Deferred        wininet<elf>
  \-PE	7e970000-7e9ac000	\               wininet
ELF	7e9ac000-7ea05000	Deferred        shlwapi<elf>
  \-PE	7e9c0000-7ea05000	\               shlwapi
ELF	7ea05000-7ea18000	Deferred        libresolv.so.2
ELF	7ea18000-7ea1b000	Deferred        libxinerama.so.1
ELF	7ea2d000-7ea4b000	Deferred        iphlpapi<elf>
  \-PE	7ea30000-7ea4b000	\               iphlpapi
ELF	7ea4b000-7eaab000	Deferred        rpcrt4<elf>
  \-PE	7ea60000-7eaab000	\               rpcrt4
ELF	7eaab000-7eb46000	Deferred        gdi32<elf>
  \-PE	7eac0000-7eb46000	\               gdi32
ELF	7eb46000-7ec8c000	Deferred        user32<elf>
  \-PE	7eb60000-7ec8c000	\               user32
ELF	7ec8c000-7ecdd000	Deferred        advapi32<elf>
  \-PE	7eca0000-7ecdd000	\               advapi32
ELF	7ecdd000-7ed81000	Deferred        ole32<elf>
  \-PE	7ecf0000-7ed81000	\               ole32
ELF	7ed81000-7edc0000	Deferred        urlmon<elf>
  \-PE	7ed90000-7edc0000	\               urlmon
ELF	7efae000-7efc6000	Deferred        libnsl.so.1
ELF	7efc6000-7efeb000	Deferred        libm.so.6
ELF	7efeb000-7eff6000	Deferred        libnss_files.so.2
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
PE	7f320000-7f3f8000	Deferred        vbase71
ELF	b7c50000-b7c52000	Deferred        libxcb-xlib.so.0
ELF	b7c52000-b7c5b000	Deferred        libnss_compat.so.2
ELF	b7c5c000-b7c60000	Deferred        libdl.so.2
ELF	b7c60000-b7daf000	Deferred        libc.so.6
ELF	b7db0000-b7dc8000	Deferred        libpthread.so.0
ELF	b7dc9000-b7dce000	Deferred        libxxf86vm.so.1
ELF	b7ddd000-b7ef2000	Deferred        libwine.so.1
ELF	b7ef4000-b7f10000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Programme\sixteen tons entertainment\Emergency4\Em4.exe
	00000021    0
	00000020    0
	00000009    0 <==
0000000c 
	0000001c    0
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
00000018 
	0000001b    0
	0000001a    0
	00000019    0
0000001d 
	0000001f    0
	0000001e    0
Backtrace:
benste@vaiofe31m:~$ 

```

---

### Post by neoMAX on 2008-04-26
[http://winehq.org](http://winehq.org)

Check their app-db to see how to get things working. It's where I would start as a beginner myself :)

---

### Post by benste on 2008-04-26
I know this site, but there are no parts for me,
one game is listed: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=3007]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=3007") and normally it should work.

the secound game isnt' listed only one older version is aviable:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3769](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3769)

Maybe here are some freaks who know what this errors mean, and how to solve them

---

### Post by benste on 2008-04-26
tried some thing for starwars battlefront:

Now there is no reaction - only cursor jumps to middle.
+ I used hardware test of swbf and it said NO SOUND card.
swbf gives the following out put:

```
benste@vaiofe31m:~$ env WINEPREFIX="/home/benste/.wine" wine "C:\Programme\LucasArts\Star Wars Battlefront\GameData\battlefront.exe"
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:ntoskrnl:KeInitializeTimerEx 0x7f001768 0
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (240,100)-(1040,700)
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f360,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
wine: Unhandled page fault on write access to 0x00000004 at address 0x5e9e83 (thread 0009), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on write access to 0x00000004 in 32-bit code (0x005e9e83).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:005e9e83 ESP:7f21e5d4 EBP:00000004 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:3fff0000 EBX:00000000 ECX:3effff00 EDX:00000000
 ESI:01c94100 EDI:00000001
Stack dump:
0x7f21e5d4:  00000000 01c94100 00000000 00000001
0x7f21e5e4:  005ef341 00000001 00000000 3f000000
0x7f21e5f4:  00000000 00000001 00000002 00000001
0x7f21e604:  005df3a1 00000001 3f000000 3f000000
0x7f21e614:  00000000 7ebdbaa0 00000000 7f21fc5c
0x7f21e624:  00000001 00000000 beef0201 00000000
Backtrace:
0x005e9e83: movl	%eax,0x0(%ebp)
Modules:
Module	Address			Debug info	Name (80 modules)
PE	  400000- 1f27000	Export          battlefront
PE	30000000-3006d000	Deferred        binkw32
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d024000-7d02f000	Deferred        libgcc_s.so.1
ELF	7d524000-7e039000	Deferred        libglcore.so.1
ELF	7e039000-7e0dd000	Deferred        libgl.so.1
ELF	7e314000-7e333000	Deferred        imm32<elf>
  \-PE	7e320000-7e333000	\               imm32
ELF	7e333000-7e359000	Deferred        msacm32<elf>
  \-PE	7e340000-7e359000	\               msacm32
ELF	7e359000-7e370000	Deferred        msacm32<elf>
  \-PE	7e360000-7e370000	\               msacm32
ELF	7e370000-7e433000	Deferred        libasound.so.2
ELF	7e434000-7e448000	Deferred        midimap<elf>
  \-PE	7e440000-7e448000	\               midimap
ELF	7e448000-7e47e000	Deferred        winealsa<elf>
  \-PE	7e450000-7e47e000	\               winealsa
ELF	7e4a3000-7e4ac000	Deferred        libxcursor.so.1
ELF	7e4ac000-7e4b1000	Deferred        libxfixes.so.3
ELF	7e4b1000-7e4b4000	Deferred        libxcomposite.so.1
ELF	7e4b4000-7e4ba000	Deferred        libxrandr.so.2
ELF	7e4ba000-7e4c2000	Deferred        libxrender.so.1
ELF	7e4c2000-7e4c5000	Deferred        libxinerama.so.1
ELF	7e4c5000-7e4ca000	Deferred        libxdmcp.so.6
ELF	7e4ca000-7e4e2000	Deferred        libxcb.so.1
ELF	7e4e2000-7e4e4000	Deferred        libxcb-xlib.so.0
ELF	7e4e4000-7e4e7000	Deferred        libxau.so.6
ELF	7e4e7000-7e5ce000	Deferred        libx11.so.6
ELF	7e5ce000-7e5dc000	Deferred        libxext.so.6
ELF	7e5dc000-7e5e1000	Deferred        libxxf86vm.so.1
ELF	7e5e1000-7e5f9000	Deferred        libice.so.6
ELF	7e5f9000-7e601000	Deferred        libsm.so.6
ELF	7e612000-7e614000	Deferred        libnvidia-tls.so.1
ELF	7e616000-7e6a7000	Deferred        winex11<elf>
  \-PE	7e620000-7e6a7000	\               winex11
ELF	7e6f0000-7e711000	Deferred        libexpat.so.1
ELF	7e711000-7e73b000	Deferred        libfontconfig.so.1
ELF	7e73b000-7e750000	Deferred        libz.so.1
ELF	7e750000-7e7c0000	Deferred        libfreetype.so.6
ELF	7e7c0000-7e7f7000	Deferred        dinput<elf>
  \-PE	7e7d0000-7e7f7000	\               dinput
ELF	7e7f7000-7e80f000	Deferred        dinput8<elf>
  \-PE	7e800000-7e80f000	\               dinput8
ELF	7e80f000-7e86f000	Deferred        rpcrt4<elf>
  \-PE	7e820000-7e86f000	\               rpcrt4
ELF	7e86f000-7e913000	Deferred        ole32<elf>
  \-PE	7e880000-7e913000	\               ole32
ELF	7e913000-7e9a1000	Deferred        winmm<elf>
  \-PE	7e920000-7e9a1000	\               winmm
ELF	7e9a1000-7e9eb000	Deferred        dsound<elf>
  \-PE	7e9b0000-7e9eb000	\               dsound
ELF	7e9eb000-7e9fe000	Deferred        libresolv.so.2
ELF	7ea13000-7ea31000	Deferred        iphlpapi<elf>
  \-PE	7ea20000-7ea31000	\               iphlpapi
ELF	7ea31000-7ea5d000	Deferred        ws2_32<elf>
  \-PE	7ea40000-7ea5d000	\               ws2_32
ELF	7ea5d000-7eaae000	Deferred        advapi32<elf>
  \-PE	7ea70000-7eaae000	\               advapi32
ELF	7eaae000-7eb49000	Deferred        gdi32<elf>
  \-PE	7eac0000-7eb49000	\               gdi32
ELF	7eb49000-7ec8f000	Deferred        user32<elf>
  \-PE	7eb60000-7ec8f000	\               user32
ELF	7ec8f000-7ed90000	Deferred        wined3d<elf>
  \-PE	7eca0000-7ed90000	\               wined3d
ELF	7ed90000-7edc0000	Deferred        d3d9<elf>
  \-PE	7eda0000-7edc0000	\               d3d9
ELF	7efae000-7efc6000	Deferred        libnsl.so.1
ELF	7efc6000-7efeb000	Deferred        libm.so.6
ELF	7efeb000-7eff6000	Deferred        libnss_files.so.2
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cc0000-b7cc9000	Deferred        libnss_compat.so.2
ELF	b7cca000-b7cce000	Deferred        libdl.so.2
ELF	b7cce000-b7e1d000	Deferred        libc.so.6
ELF	b7e1e000-b7e36000	Deferred        libpthread.so.0
ELF	b7e4b000-b7f60000	Deferred        libwine.so.1
ELF	b7f62000-b7f7e000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Programme\LucasArts\Star Wars Battlefront\GameData\battlefront.exe
	0000002f   15
	0000002e   15
	0000002d   15
	0000002b    0
	0000002a    0
	00000009    0 <==
0000000c 
	00000026    0
	00000021    0
	0000001c    0
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
00000018 
	0000001b    0
	0000001a    0
	00000019    0
0000001d 
	00000020    0
	0000001f    0
	0000001e    0
00000022 
	00000025    0
	00000024    0
	00000023    0
00000027 
	00000029    0
	00000028    0
Backtrace:
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

PS: there is also no sound notification in pidgin since ubuntu uses pulseaudio - I hate this thing, can someone help me?

---

