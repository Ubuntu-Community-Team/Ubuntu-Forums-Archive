---
title: "[SOLVED] Warcraft 3"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by linux.convert on 2008-08-16
Heres the deal...I have Ubuntu Feisty, and an illegit copy of Warcraft 3, would soon like to change that but...anyway, I have it installed. Im pretty sure that I ran the patch, and I have replaced the original files in the .wine/drive_c/Program Files/Warcraft 3/ .exe with that cracks (also on disc) but the game doess still will not play with cracks. I still have the original files in a back up folder, but would prefer to run the game without discs. not a big deal with a p1r@ted copy, but in the event I have the real thing I dont like using my discs (same goes for starcraft and diablo). one last thing I would rather not attempt to use daemon-tools or image mounting with wine, if any of you guys know anything about that, that would be great.

any help or advice would be great. thanks.

---

### Post by Dougie187 on 2008-08-16
You know you don't need to use cracks. If you just manually patch the game blizzard's latest patch allows you to play without the cd. Just look at the patch notes from blizzard or from some file hosting site like fileshack.

Same thing goes for Diablo 2 and Starcraft. They have some files you have to copy from the cd, but then its CD free playing for you.

---

### Post by ptn107 on 2008-08-16
Warcraft 3 runs provided your using the latest patch* and have moved or renamed the Warcraft III/Movies/ folder since the movies will crash the game.


*[http://us.blizzard.com/support/article.xml?articleId=20673](http://us.blizzard.com/support/article.xml?articleId=20673)

---

### Post by linux.convert on 2008-08-16
What??? theres a way to get diablo 2 too run WITHOUT the CD!?!?!?!?? im partly kidding. I ran the patch using: wine media/cdrom0/Patch/(filename)

and it appeared to have run, but im not sure.

---

### Post by linux.convert on 2008-08-16
how and why do you move the movies folder? ive never heard of this before

---

### Post by ptn107 on 2008-08-16
> **linux.convert said:**
> how and why do you move the movies folder? ive never heard of this before

wine cannot play them so war3.exe will crash.  You can still view them with your preferred movie player.  I just renamed /Movies to /Mouvies and the game starts right up.

Here's how you can just rename the folder from the terminal:
```
mv .wine/drive_c/Program\ Files/Warcraft\ III/Movies/ .wine/drive_c/Program\ Files/Warcraft\ III/Mouviz/
```

---

### Post by linux.convert on 2008-08-16
apparently, when I first ran the patch, I ran the Frozen throne patch, only ROC is installed, so ive been trying to uninstall/reinstall without much success. when i wine War3Unin.exe is says something like invalid parameters

---

### Post by linux.convert on 2008-08-16
when I try to wine /media/cdrom0/autoplay.exe
it does this

ldc@ldc-laptop:~$ wine /media/cdrom0/autoplay.exe
ldc@ldc-laptop:~$ wine: Unhandled page fault on write access to 0x025324e0 at address 0x418ec4 (thread 000b), starting debugger...
*

and leaves the cursor where I placed the *

it does something different with install.exe (both locations are on the main disc)

ldc@ldc-laptop:~$ wine /media/cdrom0/autoplay.exe
ldc@ldc-laptop:~$ wine: Unhandled page fault on write access to 0x025324e0 at address 0x418ec4 (thread 000b), starting debugger...

ldc@ldc-laptop:~$ wine /media/cdrom0/install.exe
wine: Unhandled page fault on write access to 0x023024e0 at address 0x418ec4 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x023024e0 in 32-bit code (0x00418ec4).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00418ec4 ESP:0033fe18 EBP:0033fe58 EFLAGS:00010206(   - 00      - RIP1)
 EAX:0033fe58 EBX:7ea16684 ECX:00700760 EDX:7ea30874
 ESI:00436074 EDI:00436184
Stack dump:
0x0033fe18:  0040ef35 7e9efa15 0033fe60 7e9efbfb
0x0033fe28:  00000000 00030000 7bc7b550 7ffdc000
0x0033fe38:  0033ff08 7bc3a876 0000023f 7ea1bd08
0x0033fe48:  7ea11cab 00000000 0041d5ff 7ffdf000
0x0033fe58:  0033ff08 0041d6c9 00436000 00436184
0x0033fe68:  0033fea8 0033fe98 0033fea4 00000000
Backtrace:
=>1 0x00418ec4 in install (+0x18ec4) (0x0033fe58)
  2 0x0041d6c9 in install (+0x1d6c9) (0x0033ff08)
  3 0x7b87221e in kernel32 (+0x5221e) (0x0033ffe8)
  4 0xb7e3d897 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00418ec4: movl        %ecx,0x0(%ecx,%ecx,4)
Modules:
Module  Address                 Debug info      Name (77 modules)
PE      400000-457000   Export          install
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c900000-7c932000       Deferred        uxtheme<elf>
  \-PE  7c910000-7c932000       \               uxtheme
ELF     7c932000-7c947000       Deferred        midimap<elf>
  \-PE  7c940000-7c947000       \               midimap
ELF     7c947000-7c96d000       Deferred        msacm32<elf>
  \-PE  7c950000-7c96d000       \               msacm32
ELF     7c96d000-7c985000       Deferred        msacm32<elf>
  \-PE  7c970000-7c985000       \               msacm32
ELF     7c985000-7c9c1000       Deferred        wineoss<elf>
  \-PE  7c990000-7c9c1000       \               wineoss
ELF     7c9c1000-7c9ca000       Deferred        libxcursor.so.1
ELF     7c9ca000-7c9e7000       Deferred        imm32<elf>
  \-PE  7c9d0000-7c9e7000       \               imm32
ELF     7c9e7000-7c9ed000       Deferred        libxrandr.so.2
ELF     7d012000-7d017000       Deferred        libxfixes.so.3
ELF     7d017000-7d01f000       Deferred        libxrender.so.1
ELF     7d96d000-7d976000       Deferred        librt.so.1
ELF     7d978000-7d97b000       Deferred        libxinerama.so.1
ELF     7da3f000-7e370000       Deferred        fglrx_dri.so
ELF     7e370000-7e410000       Deferred        libgl.so.1
ELF     7e410000-7e415000       Deferred        libxdmcp.so.6
ELF     7e415000-7e418000       Deferred        libxau.so.6
ELF     7e418000-7e509000       Deferred        libx11.so.6
ELF     7e509000-7e517000       Deferred        libxext.so.6
ELF     7e517000-7e51c000       Deferred        libxxf86vm.so.1
ELF     7e51c000-7e534000       Deferred        libice.so.6
ELF     7e534000-7e53d000       Deferred        libsm.so.6
ELF     7e53d000-7e5cb000       Deferred        winex11<elf>
  \-PE  7e550000-7e5cb000       \               winex11
ELF     7e63b000-7e65b000       Deferred        libexpat.so.1
ELF     7e65b000-7e686000       Deferred        libfontconfig.so.1
ELF     7e686000-7e69a000       Deferred        libz.so.1
ELF     7e69a000-7e705000       Deferred        libfreetype.so.6
ELF     7e705000-7e7c1000       Deferred        comctl32<elf>
  \-PE  7e710000-7e7c1000       \               comctl32
ELF     7e7c1000-7e81a000       Deferred        shlwapi<elf>
  \-PE  7e7d0000-7e81a000       \               shlwapi
ELF     7e81a000-7e90f000       Deferred        shell32<elf>
  \-PE  7e830000-7e90f000       \               shell32
ELF     7e90f000-7e923000       Deferred        lz32<elf>
  \-PE  7e920000-7e923000       \               lz32
ELF     7e923000-7e93c000       Deferred        version<elf>
  \-PE  7e930000-7e93c000       \               version
ELF     7e93c000-7e9cb000       Deferred        winmm<elf>
  \-PE  7e950000-7e9cb000       \               winmm
ELF     7e9cb000-7ea32000       Deferred        msvcrt<elf>
  \-PE  7e9e0000-7ea32000       \               msvcrt
ELF     7ea32000-7ea45000       Deferred        libresolv.so.2
ELF     7ea45000-7ea63000       Deferred        iphlpapi<elf>
  \-PE  7ea50000-7ea63000       \               iphlpapi
ELF     7ea63000-7eab8000       Deferred        rpcrt4<elf>
  \-PE  7ea70000-7eab8000       \               rpcrt4
ELF     7eab8000-7eac4000       Deferred        libgcc_s.so.1
ELF     7ebbd000-7ec7a000       Deferred        gdi32<elf>
  \-PE  7ebd0000-7ec7a000       \               gdi32
ELF     7ec7a000-7edb6000       Deferred        user32<elf>
  \-PE  7eca0000-7edb6000       \               user32
ELF     7edb6000-7edfc000       Deferred        advapi32<elf>
  \-PE  7edc0000-7edfc000       \               advapi32
ELF     7edfc000-7ee96000       Deferred        ole32<elf>
  \-PE  7ee10000-7ee96000       \               ole32
ELF     7efa8000-7efb3000       Deferred        libnss_files.so.2
ELF     7efb3000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7eff1000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cc0000-b7cc9000       Deferred        libnss_compat.so.2
ELF     b7cca000-b7cce000       Deferred        libdl.so.2
ELF     b7cce000-b7e0f000       Deferred        libc.so.6
ELF     b7e10000-b7e27000       Deferred        libpthread.so.0
ELF     b7e36000-b7f47000       Export          libwine.so.1
ELF     b7f49000-b7f64000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\install.exe
        00000009    0 <==
ldc@ldc-laptop:~$

---

### Post by ptn107 on 2008-08-16
You should be able to just delete Patch.txt and War3Patch.mpq from the folder and then install the correct patch.

As for running the CD from the cdrom drive, I recommend against it.  Wine seems to have too many problems with this.  To install most games in wine I just copy the cd to the local drive first and install from there.  I've installed Diablo 2/exp, Wow, and War3 this way.

I assume this is the problem since wine complains about a fault on write access.

---

### Post by overdrank on 2008-08-16
> **linux.convert said:**
> Heres the deal...I have Ubuntu Feisty, and an **illegit **copy of Warcraft 3, not a big deal with a** p1r@ted copy**, 

Please do not use the forums for these activities.

---

