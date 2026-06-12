---
title: "Windows (PE) Executable Disassembly on Linux"
date: 2010-03-29
forum: Programming Talk
---

### Post by mikazo on 2010-03-29
Anyone know of any graphical Windows Portable Executable (PE) disassemblers that run on Linux? I've been looking for one, but can't seem to find any. I would imagine there are tools to analyze PEs on a platform other than Windows.

I've tried the HT console disassembler, but I'd prefer a real GUI.

Thanks for any suggestions.

---

### Post by jpkotta on 2010-03-30
The MinGW toolchain will probably do it, but it's all command line.  There's dissy which is just a frontend to GNU disassemblers (and thus MinGW's), but it doesn't work with MinGW.  Anyway, just install the mingw32 package and try 
```
i586-mingw32msvc-objdump -d foo.exe
```

---

### Post by the_unforgiven on 2010-03-30
> **jpkotta said:**
> The MinGW toolchain will probably do it, but it's all command line.  There's dissy which is just a frontend to GNU disassemblers (and thus MinGW's), but it doesn't work with MinGW.  Anyway, just install the mingw32 package and try 
```
i586-mingw32msvc-objdump -d foo.exe
```
You don't need MinGW for that - normal objdump does the job pretty nicely.
Try:
```
objdump -x -D pe-exe-file.exe | less
```

Here is some output from one of the Microsoft KB update files on my x86-64 linux machine taken with normal objdump:
```

Windows6.0-KB948465-X86.exe:     file format pei-i386
Windows6.0-KB948465-X86.exe
architecture: i386, flags 0x0000012f:
HAS_RELOC, EXEC_P, HAS_LINENO, HAS_DEBUG, HAS_LOCALS, D_PAGED
start address 0x0100b2e0

Characteristics 0x102
	executable
	32 bit words

Time/Date		Sat Apr 11 09:52:14 2009
Magic			010b	(PE32)
MajorLinkerVersion	8
MinorLinkerVersion	0
SizeOfCode		0000ea00
SizeOfInitializedData	00002600
SizeOfUninitializedData	00000000
AddressOfEntryPoint	0000b2e0
BaseOfCode		00001000
BaseOfData		00010000
ImageBase		01000000
SectionAlignment	00001000
FileAlignment		00000200
MajorOSystemVersion	6
MinorOSystemVersion	0
MajorImageVersion	6
MinorImageVersion	0
MajorSubsystemVersion	5
MinorSubsystemVersion	1
Win32Version		00000000
SizeOfImage		00014000
SizeOfHeaders		00000400
CheckSum		15c58ab1
Subsystem		00000002	(Windows GUI)
DllCharacteristics	00008140
SizeOfStackReserve	00040000
SizeOfStackCommit	00002000
SizeOfHeapReserve	00100000
SizeOfHeapCommit	00001000
LoaderFlags		00000000
NumberOfRvaAndSizes	00000010

The Data Directory
Entry 0 00000000 00000000 Export Directory [.edata (or where ever we found it)]
Entry 1 0000ec9c 000000a0 Import Directory [parts of .idata]
Entry 2 00011000 000003f8 Resource Directory [.rsrc]
Entry 3 00000000 00000000 Exception Directory [.pdata]
Entry 4 15c4df10 00001c38 Security Directory
Entry 5 00012000 00000964 Base Relocation Directory [.reloc]
Entry 6 00001260 0000001c Debug Directory
Entry 7 00000000 00000000 Description Directory
Entry 8 00000000 00000000 Special Directory
Entry 9 00000000 00000000 Thread Storage Directory [.tls]
Entry a 00005a20 00000040 Load Configuration Directory
Entry b 00000280 00000098 Bound Import Directory
Entry c 00001000 0000022c Import Address Table Directory
Entry d 00000000 00000000 Delay Import Directory
Entry e 00000000 00000000 CLR Runtime Header
Entry f 00000000 00000000 Reserved

There is an import table in .text at 0x100ec9c

The Import Tables (interpreted .text section contents)
 vma:            Hint    Time      Forward  DLL       First
                 Table   Stamp     Chain    Name      Thunk
 0000ec9c	0000ed3c ffffffff ffffffff 0000efa8 00001000

	DLL Name: ADVAPI32.dll
	vma:  Hint/Ord Member-Name Bound-To
	ef68	  199  CryptReleaseContext	77cb3bd0
	ef7e	  189  CryptGenRandom	77cb265b
	ef90	  173  CryptAcquireContextW	77cadaee

 0000ecb0	0000ed4c ffffffff ffffffff 0000f1d4 00001010

	DLL Name: KERNEL32.dll
	vma:  Hint/Ord Member-Name Bound-To
	f0f4	  114  CreateDirectoryW	77e3d166
	f108	  463  GetFileAttributesW	77e3d281
	f11e	  502  GetModuleFileNameW	77e3b27e
	f134	  598  GetSystemWindowsDirectoryW	77e34455
	f152	  770  LocalFree	77e3ad76
	f15e	  329  FormatMessageW	77e113d4
	f170	 1157  WideCharToMultiByte	77e3cbf8
	f186	  831  OutputDebugStringA	77e30264
	f19c	  987  SetEvent	77e3a6b4
	f1a8	  454  GetExitCodeProcess	77e18b52
	f1be	 1135  WaitForSingleObject	77e397e0
	f630	  677  HeapDestroy	77e0f67a
	f63e	  674  HeapAlloc	77f36570
	f64a	  678  HeapFree	77e39a12
	f656	  681  HeapReAlloc	77f0dccc
	f664	  683  HeapSize	77f126fe
	f670	  550  GetProcessHeap	77e3b68f
	f682	  864  RaiseException	77e2fb56
	f694	  218  EnterCriticalSection	77f18af0
	f6ac	  756  LeaveCriticalSection	77f18ab0
	f6c4	  697  InitializeCriticalSection	77f1140b
	f6e0	  191  DeleteCriticalSection	77f11b41
	f6f8	  634  GetVersionExA	77e19d76
	f708	  706  InterlockedExchange	77e39428
	f0d4	  164  CreateThread	77e3c90e
	f0c0	  506  GetModuleHandleW	77e3a804
	f0aa	  832  OutputDebugStringW	77dfbe4b
	f09c	  469  GetFileSize	77e37148
	f08a	  999  SetFilePointer	77e2fc1d
	f07c	  128  CreateFileW	77e3aecb
	f06c	  981  SetEndOfFile	77e083a9
	f064	 1068  Sleep	77df1c5d
	f058	 1176  WriteFile	77e3a9c1
	f044	  480  GetFullPathNameW	77e2ec5f
	f034	  487  GetLastError	77e3a6f9
	f026	   68  CloseHandle	77e3ae8d
	f014	  313  FindResourceExW	77e369fd
	f004	  314  FindResourceW	77e37fa1
	eff4	  763  LoadResource	77e36adb
	efe4	  780  LockResource	77e368df
	efd2	 1067  SizeofResource	77e37fbf
	efc6	  878  ReadFile	77e2f02b
	efb6	 1012  SetLastError	77e3a640
	f806	 1097  UnhandledExceptionFilter	77e8fd89
	f7f2	  426  GetCurrentProcess	77e3c905
	f7de	 1080  TerminateProcess	77df18ef
	f7c4	  595  GetSystemTimeAsFileTime	77df18c0
	f7ae	  427  GetCurrentProcessId	77e3a651
	f798	  430  GetCurrentThreadId	77e399f0
	f788	  618  GetTickCount	77e39706
	f76e	  857  QueryPerformanceCounter	77e3a660
	f75a	  503  GetModuleHandleA	77e392a5
	f73c	 1056  SetUnhandledExceptionFilter	77e1a84f
	f71e	  703  InterlockedCompareExchange	77e3943c
	f0e4	  118  CreateEventW	77e3b65e

 0000ecc4	0000ee40 ffffffff ffffffff 0000f2c4 00001104

	DLL Name: USER32.dll
	vma:  Hint/Ord Member-Name Bound-To
	f1e2	  677  SetWindowLongW	77d613b4
	f1f4	  540  PeekMessageW	77d7045a
	f2b0	  284  GetDesktopWindow	77d62314
	f28e	  565  RegisterClassExW	77d5da30
	f27c	  104  CreateWindowExW	77d61305
	f26c	  160  DestroyWindow	77d67fb6
	f25a	  150  DefWindowProcW	77d703b4
	f248	  386  GetWindowLongW	77d6f8bf
	f22c	  518  MsgWaitForMultipleObjects	77d67f3b
	f218	  725  TranslateMessage	77d701ad
	f2a2	  511  MessageBoxW	77dad6cf
	f204	  169  DispatchMessageW	77d7021c
	f822	  734  UnregisterClassA	77d5bf81

 0000ecd8	0000ee78 ffffffff ffffffff 0000f470 0000113c

	DLL Name: msvcrt.dll
	vma:  Hint/Ord Member-Name Bound-To
	f41c	  212  __setusermatherr	708f566d
	f2d0	   20  ??3@YAXPAX@Z	70869de1
	f2e0	   99  _CxxThrowException	708832ba
	f2f6	 1133  _wtol	7086b46f
	f586	  478  _isatty	7086f5e4
	f57c	 1096  _write	70874d30
	f570	  587  _lseeki64	708750e9
	f566	  367  _fileno	7086bff4
	f55a	  207  __pioinfo	708fe500
	f54c	  133  __badioinfo	709018b0
	f542	 1172  ferror	70870dfc
	f538	 1390  wctomb	708aee02
	f530	  561  _itoa	708866cf
	f524	  815  _snprintf	70886657
	f51c	  475  _iob	70900958
	f4fe	  176  __mb_cur_max	70901808
	f4f4	 1255  mbtowc	7086b1a6
	f4e6	  295  _controlfp	7087097d
	f4d2	   55  ?terminate@@YAXXZ	708b2f8e
	f4c8	 1260  memmove	7086a048
	f4be	 1258  memcpy	70869ac0
	f4b4	  747  _onexit	70870d59
	f4ac	  578  _lock	70869f85
	f49e	  141  __dllonexit	7086f8d1
	f494	  934  _unlock	70869f69
	f47c	   17  ??1type_info@@UAE@XZ	708b6173
	f45e	  210  __set_app_type	708717f4
	f450	  190  __p__fmode	7087179b
	f440	  185  __p__commode	70871790
	f430	  245  _adjust_fdiv	70901880
	f50e	 1218  isleadbyte	7086c10b
	f40e	  257  _amsg_exit	708c961d
	f402	  469  _initterm	7086c4e6
	f3fa	 1167  exit	70873c08
	f3ec	  106  _XcptFilter	708c3126
	f3e4	  354  _exit	708c95ee
	f3da	  276  _cexit	70873d34
	f3c8	  225  __wgetmainargs	708725be
	f3be	 1246  malloc	70869c45
	f3b4	  342  _errno	7086a13b
	f3a0	  113  __CxxFrameHandler	70883859
	f392	  962  _vscprintf	708d59ec
	f388	 1361  wcschr	7086a23d
	f37e	 1262  memset	70869860
	f370	  974  _vsnwprintf	7086b971
	f360	   18  ??2@YAPAXI@Z	70869df1
	f356	 1157  calloc	7086c590
	f34e	 1190  free	70869bca
	f33e	   41  ??_U@YAPAXI@Z	7086b1d5
	f330	  965  _vscwprintf	708705a6
	f320	   43  ??_V@YAXPAX@Z	7086b1c5
	f314	 1007  _wcsicmp	7086ac10
	f308	 1017  _wcsnicmp	7086a2c3
	f2fe	 1216  isdigit	7086c281

 0000ecec	0000ee2c ffffffff ffffffff 0000f5e4 000010f0

	DLL Name: SHELL32.dll
	vma:  Hint/Ord Member-Name Bound-To
	f5a4	  209  SHGetPathFromIDListW	76979841
	f590	  169  SHFileOperationW	769268d0
	f5bc	  120  SHBrowseForFolderW	76b00ce0
	f5d2	  279  ShellExecuteExW	7694c135

 0000ed00	0000ef5c ffffffff ffffffff 0000f610 00001220

	DLL Name: ole32.dll
	vma:  Hint/Ord Member-Name Bound-To
	f600	   61  CoInitialize	72c5035f
	f5f0	  103  CoTaskMemFree	72c6af2e

 0000ed14	0000ef54 ffffffff ffffffff 0000f626 00001218

	DLL Name: ntdll.dll
	vma:  Hint/Ord Member-Name Bound-To
	f61a	 1163  RtlUnwind	77f09999

 0000ed28	00000000 00000000 00000000 00000000 00000000


PE File Base Relocations (interpreted .reloc section contents)

Virtual Address: 00001000 Chunk size 44 (0x2c) Number of fixups 18
	reloc    0 offset  230 [1230] HIGHLOW
	reloc    1 offset  234 [1234] HIGHLOW
	reloc    2 offset  238 [1238] HIGHLOW
	reloc    3 offset  23c [123c] HIGHLOW
	reloc    4 offset  240 [1240] HIGHLOW
	reloc    5 offset  244 [1244] HIGHLOW
	reloc    6 offset  248 [1248] HIGHLOW
	reloc    7 offset  254 [1254] HIGHLOW
	reloc    8 offset  258 [1258] HIGHLOW
	reloc    9 offset  2d0 [12d0] HIGHLOW
	reloc   10 offset  2d4 [12d4] HIGHLOW
	reloc   11 offset  2d8 [12d8] HIGHLOW

...

```

---

### Post by jpkotta on 2010-03-30
> **the_unforgiven said:**
> You don't need MinGW for that - normal objdump does the job pretty nicely.


I didn't even try that (obviously).  That's pretty slick.

---

### Post by Simian Man on 2010-03-30
Why would you want a graphical disassembler?

---

### Post by mmix on 2010-03-30
[http://en.wikibooks.org/wiki/X86_Disassembly/Disassemblers_and_Decompilers](http://en.wikibooks.org/wiki/X86_Disassembly/Disassemblers_and_Decompilers)

HTH

---

### Post by the_unforgiven on 2010-03-31
> **jpkotta said:**
> I didn't even try that (obviously).  That's pretty slick.
That's possible thanks to [libbfd]("http://en.wikipedia.org/wiki/Binary_File_Descriptor_library"). :)

---

### Post by mikazo on 2010-03-31
Here's what I get when I run objdump:

mike@mike-laptop:~$ objdump -d -M intel keygen.exe > keygen.exe.dump
objdump: keygen.exe: File format is ambiguous
objdump: Matching formats: efi-app-ia32 efi-bsdrv-ia32 efi-rtdrv-ia32

mike@mike-laptop:~$ objdump --version
GNU objdump (GNU Binutils for Ubuntu) 2.19.1
Copyright 2007 Free Software Foundation, Inc.
This program is free software; you may redistribute it under the terms of
the GNU General Public License version 3 or (at your option) any later version.
This program has absolutely no warranty.
mike@mike-laptop:~$

---

### Post by mikazo on 2010-03-31
Also, objdump --help shows this:

objdump: supported targets: elf32-i386 a.out-i386-linux efi-app-ia32 efi-bsdrv-ia32 efi-rtdrv-ia32 elf32-little elf32-big elf64-x86-64 efi-app-x86_64 efi-bsdrv-x86_64 efi-rtdrv-x86_64 elf64-little elf64-big srec symbolsrec tekhex binary ihex trad-core
objdump: supported architectures: i386 i386:x86-64 i8086 i386:intel i386:x86-64:intel

---

### Post by the_unforgiven on 2010-04-01
> **mikazo said:**
> Here's what I get when I run objdump:

mike@mike-laptop:~$ objdump -d -M intel keygen.exe > keygen.exe.dump
objdump: keygen.exe: File format is ambiguous
objdump: Matching formats: efi-app-ia32 efi-bsdrv-ia32 efi-rtdrv-ia32

mike@mike-laptop:~$ objdump --version
GNU objdump (GNU Binutils for Ubuntu) 2.19.1
Copyright 2007 Free Software Foundation, Inc.
This program is free software; you may redistribute it under the terms of
the GNU General Public License version 3 or (at your option) any later version.
This program has absolutely no warranty.
mike@mike-laptop:~$
That's probably because the keygen is hand-crafted PE32 executable - using bare-minimum PE32 structure and leaving out most of the header fields. There are lots of tricks that crack-writers play - like include hi-def animation/audio in a file ~10kb in size.

---

### Post by mikazo on 2010-04-01
> **the_unforgiven said:**
> That's probably because the keygen is hand-crafted PE32 executable - using bare-minimum PE32 structure and leaving out most of the header fields. There are lots of tricks that crack-writers play - like include hi-def animation/audio in a file ~10kb in size.

Thanks for the advice. This keygen.exe is supposedly infected with a Trojan. I'm interested in virus analysis, so I just wanted to take a look. Maybe there are tools more appropriate for that application?

---

### Post by pbrane on 2010-04-01
Have you looked at this keygen file in a hex editor? If it is a PE32 file then it will have that signature...
```

00000000   4D 5A 90 00  03 00 00 00  04 00 00 00  FF FF 00 00  MZ..............
00000010   B8 00 00 00  00 00 00 00  40 00 00 00  00 00 00 00  ........@.......
00000020   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
00000030   00 00 00 00  00 00 00 00  00 00 00 00  E0 00 00 00  ................
00000040   0E 1F BA 0E  00 B4 09 CD  21 B8 01 4C  CD 21 54 68  ........!..L.!Th
00000050   69 73 20 70  72 6F 67 72  61 6D 20 63  61 6E 6E 6F  is program canno
00000060   74 20 62 65  20 72 75 6E  20 69 6E 20  44 4F 53 20  t be run in DOS
00000070   6D 6F 64 65  2E 0D 0D 0A  24 00 00 00  00 00 00 00  mode....$.......
00000080   EC 85 5B A1  A8 E4 35 F2  A8 E4 35 F2  A8 E4 35 F2  ..[...5...5...5.
00000090   6B EB 3A F2  A9 E4 35 F2  6B EB 55 F2  A9 E4 35 F2  k.:...5.k.U...5.
000000A0   6B EB 68 F2  BB E4 35 F2  A8 E4 34 F2  63 E4 35 F2  k.h...5...4.c.5.
000000B0   6B EB 6B F2  A9 E4 35 F2  6B EB 6A F2  BF E4 35 F2  k.k...5.k.j...5.
000000C0   6B EB 6F F2  A9 E4 35 F2  52 69 63 68  A8 E4 35 F2  k.o...5.Rich..5.
000000D0   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
000000E0   50 45 00 00  4C 01 03 00  87 52 02 48  00 00 00 00  **PE**..L....R.H....

```

You may even be able to analyze the PE header that way. By knowing what the PE header consists of you'll then know what parts of the header are absolutely necessary for the OS the execute the program.

---

