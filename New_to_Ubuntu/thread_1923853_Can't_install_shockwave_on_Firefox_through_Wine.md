---
title: "Can't install shockwave on Firefox through Wine"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by Mediosordo on 2012-02-11
My mother has began learning english through a website called busuu.com, but apparently she can't do pronunciation exercises as these need of  the shockwave plugin, so I though it would be a good idea to configure a Firefox version through Wine for her to use (following these instructions: [https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave) )

However, after instaling the latest Firefox version under wine (10.0.1), I tried to install the shockwave plugin but the whole thing crashed as it was finishing. Now Firefox works fine, but if I go to a page with shockwave content, Firefox crashes. This is the report I'm given:

```
Unhandled exception: unimplemented function msvcp80.dll.??0?$basic_ifstream@DU?$char_traits@D@std@@@std@@QAE@XZ called in 32-bit code (0x7b839f62).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b839f62 ESP:0033fb00 EBP:0033fb64 EFLAGS:00000207(   - --  I   - -P-C)
 EAX:7b826255 EBX:7b895ff4 ECX:6887e7d2 EDX:0033fb28
 ESI:80000100 EDI:004115d4
Stack dump:
0x0033fb00:  0033fb84 00000008 7bc4790a 80000100
0x0033fb10:  00000001 00000000 7b839f62 00000002
0x0033fb20:  6887b3b4 6887e7d2 00110000 00000000
0x0033fb30:  00000000 7bc450b4 00110014 00000002
0x0033fb40:  001369d8 7bc47aed 6dab6ff4 0033fc10
0x0033fb50:  0000008c 0033fba4 7b839f1a 00000002
Backtrace:
=>0 0x7b839f62 in kernel32 (+0x29f62) (0x0033fb64)
  1 0x6887b358 in msvcp80 (+0x1b357) (0x0033fb94)
  2 0x6886b799 in msvcp80 (+0xb798) (0x0033fbd4)
  3 0x00401497 in crashreporter (+0x1496) (0x0033fbd4)
  4 0x00401697 in crashreporter (+0x1696) (0x0033fc30)
  5 0x00402715 in crashreporter (+0x2714) (0x0033fd8c)
  6 0x0040300e in crashreporter (+0x300d) (0x0033fddc)
  7 0x0040a7cb in crashreporter (+0xa7ca) (0x0033fe70)
  8 0x7b859fdc call_process_entry+0xb() in kernel32 (0x0033fe88)
  9 0x7b85b24f in kernel32 (+0x4b24e) (0x0033fec8)
  10 0x7bc71f10 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  11 0x7bc749dd call_thread_func+0x7c() in ntdll (0x0033ffa8)
  12 0x7bc71eee RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  13 0x7bc4a03e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8)
0x7b839f62: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (74 modules)
PE      400000-  41d000    Export          crashreporter
ELF    68000000-6801e000    Deferred        ld-linux.so.2
ELF    6801e000-68038000    Deferred        libpthread.so.0
ELF    68038000-68195000    Deferred        libc.so.6
ELF    68195000-68199000    Deferred        libdl.so.2
ELF    68199000-681bf000    Deferred        libm.so.6
ELF    681bf000-681c7000    Deferred        libnss_compat.so.2
ELF    681c7000-681de000    Deferred        libnsl.so.1
ELF    681de000-681e9000    Deferred        libnss_nis.so.2
ELF    681e9000-68329000    Deferred        user32<elf>
  \-PE    68200000-68329000    \               user32
ELF    68329000-683e4000    Deferred        gdi32<elf>
  \-PE    68340000-683e4000    \               gdi32
ELF    683e4000-68444000    Deferred        advapi32<elf>
  \-PE    683f0000-68444000    \               advapi32
ELF    68444000-6845d000    Deferred        version<elf>
  \-PE    68450000-6845d000    \               version
ELF    6845d000-68554000    Deferred        comctl32<elf>
  \-PE    68460000-68554000    \               comctl32
ELF    68554000-68764000    Deferred        shell32<elf>
  \-PE    68560000-68764000    \               shell32
ELF    68764000-687ce000    Deferred        shlwapi<elf>
  \-PE    68770000-687ce000    \               shlwapi
ELF    687ce000-6883d000    Deferred        wininet<elf>
  \-PE    687e0000-6883d000    \               wininet
ELF    6883d000-68852000    Deferred        libz.so.1
ELF    68852000-688fb000    Dwarf           msvcp80<elf>
  \-PE    68860000-688fb000    \               msvcp80
ELF    688fb000-689e0000    Deferred        msvcp90<elf>
  \-PE    68920000-689e0000    \               msvcp90
ELF    689e0000-68a0b000    Deferred        msvcr80<elf>
  \-PE    689f0000-68a0b000    \               msvcr80
ELF    68a0b000-68a3a000    Deferred        msvcr90<elf>
  \-PE    68a10000-68a3a000    \               msvcr90
ELF    68a3a000-68ab1000    Deferred        libfreetype.so.6
ELF    68ab1000-68aba000    Deferred        libsm.so.6
ELF    68aba000-68ad3000    Deferred        libice.so.6
ELF    68ad3000-68bf0000    Deferred        libx11.so.6
ELF    68bf0000-68bf5000    Deferred        libuuid.so.1
ELF    68bf5000-68c0f000    Deferred        libxcb.so.1
ELF    68c0f000-68c13000    Deferred        libxau.so.6
ELF    68c13000-68c19000    Deferred        libxdmcp.so.6
ELF    68c19000-68c1d000    Deferred        libxinerama.so.1
ELF    68c1d000-68c23000    Deferred        libxxf86vm.so.1
ELF    68c23000-68c2b000    Deferred        libxrandr.so.2
ELF    68c2b000-68c2f000    Deferred        libxcomposite.so.1
ELF    68c2f000-68c35000    Deferred        libxfixes.so.3
ELF    68c35000-68c43000    Deferred        libxi.so.6
ELF    68c43000-68c6a000    Deferred        libexpat.so.1
ELF    68c6a000-68c74000    Deferred        libxcursor.so.1
ELF    68c74000-68ca8000    Deferred        uxtheme<elf>
  \-PE    68c80000-68ca8000    \               uxtheme
ELF    68ca8000-68d1d000    Deferred        rpcrt4<elf>
  \-PE    68cb0000-68d1d000    \               rpcrt4
ELF    68d4d000-68d59000    Deferred        libnss_files.so.2
ELF    68d59000-68e5f000    Deferred        ole32<elf>
  \-PE    68d70000-68e5f000    \               ole32
ELF    6a844000-6a8d8000    Deferred        winex11<elf>
  \-PE    6a850000-6a8d8000    \               winex11
ELF    6c05f000-6c081000    Deferred        imm32<elf>
  \-PE    6c070000-6c081000    \               imm32
ELF    6da33000-6dac0000    Deferred        msvcrt<elf>
  \-PE    6da50000-6dac0000    \               msvcrt
ELF    6dd23000-6dd33000    Deferred        libxext.so.6
ELF    75094000-750c4000    Deferred        libfontconfig.so.1
ELF    78155000-7817b000    Deferred        mpr<elf>
  \-PE    78160000-7817b000    \               mpr
ELF    7b329000-7b333000    Deferred        libxrender.so.1
ELF    7b800000-7b9b8000    Dwarf           kernel32<elf>
  \-PE    7b810000-7b9b8000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cbaa000-7cceb000    Dwarf           libwine.so.1
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001f    0
    0000001e    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000018    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001d    0
    0000001b    0
00000021 explorer.exe
    00000022    0
0000002b (D) C:\Archivos de programa\Mozilla Firefox\crashreporter.exe
    0000002e    0 <==
System information:
    Wine build: wine-1.4-rc2
```Can anyone tell me what's going wrong or any way to solve this?

On her EeePc she's running Maverick Meerkat, and the microphone works fine on the system.
Many thanks!

---

### Post by josephmills on 2012-02-11
try and give this a shot 
[http://www.ubuntu-unleashed.com/2008/03/howto-install-safari-on-ubuntu-with.html](http://www.ubuntu-unleashed.com/2008/03/howto-install-safari-on-ubuntu-with.html)

let us know how it works out.

---

### Post by Mediosordo on 2012-02-11
No good, I'm afraid. The repositories he's using don't seem to work..

```
blanca@blanca-1215P:~$ wget http://ubuntu-debs.googlecode.com/files/install_flash_player.exe
--2012-02-11 21:26:05--  http://ubuntu-debs.googlecode.com/files/install_flash_player.exe
Resolviendo ubuntu-debs.googlecode.com... 173.194.67.82
Conectando a ubuntu-debs.googlecode.com|173.194.67.82|:80... conectado.
Petición HTTP enviada, esperando respuesta... 403 Forbidden
2012-02-11 21:26:06 ERROR 403: Forbidden.
```

..and the Safari version I get from the apple website doesn't seem to work properly neither, not being able to load any webpage with it.

---

