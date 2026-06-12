---
title: "py2exe build issues"
date: 2010-01-22
forum: Packaging and Compiling Programs
---

### Post by jaybstory on 2010-01-22
Hello,

I'm having trouble installing py2exe on ubuntu 9.10 64 bit.  I get these errors when I run python setup.py build.  I'm not sure what the issue is or how to fix it.  Thank you in advance.

```


abbs@abbs-ubuntu-be111:~/Downloads/py2exe-0.6.9$ python setup.py build
/home/abbs/Downloads/py2exe-0.6.9/py2exe/build_exe.py:16: DeprecationWarning: the sets module is deprecated
  import sets
running build
running build_py
creating build
creating build/lib.linux-x86_64-2.6
copying zipextimporter.py -> build/lib.linux-x86_64-2.6
creating build/lib.linux-x86_64-2.6/py2exe
copying py2exe/mf.py -> build/lib.linux-x86_64-2.6/py2exe
copying py2exe/boot_com_servers.py -> build/lib.linux-x86_64-2.6/py2exe
copying py2exe/boot_ctypes_com_server.py -> build/lib.linux-x86_64-2.6/py2exe
copying py2exe/build_exe.py -> build/lib.linux-x86_64-2.6/py2exe
copying py2exe/__init__.py -> build/lib.linux-x86_64-2.6/py2exe
copying py2exe/boot_service.py -> build/lib.linux-x86_64-2.6/py2exe
copying py2exe/boot_common.py -> build/lib.linux-x86_64-2.6/py2exe
creating build/lib.linux-x86_64-2.6/py2exe/resources
copying py2exe/resources/VersionInfo.py -> build/lib.linux-x86_64-2.6/py2exe/resources
copying py2exe/resources/__init__.py -> build/lib.linux-x86_64-2.6/py2exe/resources
copying py2exe/resources/StringTables.py -> build/lib.linux-x86_64-2.6/py2exe/resources
running build_ext
building '_memimporter' extension
creating build/temp.linux-x86_64-2.6
creating build/temp.linux-x86_64-2.6/source
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DPYTHONDLL=\"PYTHON26.DLL\" -DPYTHONCOM=\"pythoncom26.dll\" -I/usr/include/python2.6 -c source/MemoryModule.c -o build/temp.linux-x86_64-2.6/source/MemoryModule.o
<command-line>: warning: missing terminating " character
<command-line>: warning: missing terminating " character
source/MemoryModule.c:30: warning: ignoring #pragma warning 
source/MemoryModule.c:32:21: error: Windows.h: No such file or directory
source/MemoryModule.c:33:19: error: winnt.h: No such file or directory
In file included from source/MemoryModule.c:42:
source/MemoryModule.h:38: warning: function declaration isn’t a prototype
source/MemoryModule.h:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘MemoryGetProcAddress’
source/MemoryModule.h:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘MyFreeLibrary’
source/MemoryModule.h:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘MyLoadLibrary’
source/MemoryModule.h:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘MyGetProcAddress’
source/MemoryModule.h:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘MyGetModuleHandle’
source/MemoryModule.c:54: error: expected specifier-qualifier-list before ‘DWORD’
source/MemoryModule.c:58: error: expected specifier-qualifier-list before ‘PIMAGE_NT_HEADERS’
source/MemoryModule.c:71: error: expected ‘)’ before ‘*’ token
source/MemoryModule.c: In function ‘_Register’:
source/MemoryModule.c:80: error: ‘MEMORYMODULE’ has no member named ‘next’
source/MemoryModule.c:82: error: ‘MEMORYMODULE’ has no member named ‘prev’
source/MemoryModule.c:83: error: ‘MEMORYMODULE’ has no member named ‘prev’
source/MemoryModule.c:83: error: ‘NULL’ undeclared (first use in this function)
source/MemoryModule.c:83: error: (Each undeclared identifier is reported only once
source/MemoryModule.c:83: error: for each function it appears in.)
source/MemoryModule.c: In function ‘_Unregister’:
source/MemoryModule.c:90: warning: implicit declaration of function ‘free’
source/MemoryModule.c:90: warning: incompatible implicit declaration of built-in function ‘free’
source/MemoryModule.c:90: error: ‘MEMORYMODULE’ has no member named ‘name’
source/MemoryModule.c:91: error: ‘MEMORYMODULE’ has no member named ‘prev’
source/MemoryModule.c:92: error: ‘MEMORYMODULE’ has no member named ‘prev’
source/MemoryModule.c:92: error: ‘MEMORYMODULE’ has no member named ‘next’
source/MemoryModule.c:93: error: ‘MEMORYMODULE’ has no member named ‘next’
source/MemoryModule.c:94: error: ‘MEMORYMODULE’ has no member named ‘next’
source/MemoryModule.c:94: error: ‘MEMORYMODULE’ has no member named ‘prev’
source/MemoryModule.c:96: error: ‘MEMORYMODULE’ has no member named ‘next’
source/MemoryModule.c: At top level:
source/MemoryModule.c:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘MyGetModuleHandle’
source/MemoryModule.c:117: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘MyLoadLibrary’
source/MemoryModule.c:143: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘MyGetProcAddress’
source/MemoryModule.c:155: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘MyFreeLibrary’
source/MemoryModule.c:202: error: expected declaration specifiers or ‘...’ before ‘PIMAGE_NT_HEADERS’
source/MemoryModule.c: In function ‘CopySections’:
source/MemoryModule.c:205: error: ‘struct tagMEMORYMODULE’ has no member named ‘codeBase’
source/MemoryModule.c:207: error: ‘PIMAGE_SECTION_HEADER’ undeclared (first use in this function)
source/MemoryModule.c:207: error: expected ‘;’ before ‘section’
source/MemoryModule.c:208: error: ‘struct tagMEMORYMODULE’ has no member named ‘headers’
source/MemoryModule.c:208: error: ‘section’ undeclared (first use in this function)
source/MemoryModule.c:214: error: ‘old_headers’ undeclared (first use in this function)
source/MemoryModule.c:217: warning: implicit declaration of function ‘VirtualAlloc’
source/MemoryModule.c:219: error: ‘MEM_COMMIT’ undeclared (first use in this function)
source/MemoryModule.c:220: error: ‘PAGE_READWRITE’ undeclared (first use in this function)
source/MemoryModule.c:220: warning: cast to pointer from integer of different size
source/MemoryModule.c:222: error: ‘DWORD’ undeclared (first use in this function)
source/MemoryModule.c:222: error: expected ‘;’ before ‘dest’
source/MemoryModule.c:223: warning: implicit declaration of function ‘memset’
source/MemoryModule.c:223: warning: incompatible implicit declaration of built-in function ‘memset’
source/MemoryModule.c:234: warning: cast to pointer from integer of different size
source/MemoryModule.c:235: warning: implicit declaration of function ‘memcpy’
source/MemoryModule.c:235: warning: incompatible implicit declaration of built-in function ‘memcpy’
source/MemoryModule.c:236: error: expected ‘;’ before ‘dest’
source/MemoryModule.c: At top level:
source/MemoryModule.c:244: error: ‘PAGE_NOACCESS’ undeclared here (not in a function)
source/MemoryModule.c:244: error: ‘PAGE_WRITECOPY’ undeclared here (not in a function)
source/MemoryModule.c:245: error: ‘PAGE_READONLY’ undeclared here (not in a function)
source/MemoryModule.c:245: error: ‘PAGE_READWRITE’ undeclared here (not in a function)
source/MemoryModule.c:248: error: ‘PAGE_EXECUTE’ undeclared here (not in a function)
source/MemoryModule.c:248: error: ‘PAGE_EXECUTE_WRITECOPY’ undeclared here (not in a function)
source/MemoryModule.c:249: error: ‘PAGE_EXECUTE_READ’ undeclared here (not in a function)
source/MemoryModule.c:249: error: ‘PAGE_EXECUTE_READWRITE’ undeclared here (not in a function)
source/MemoryModule.c: In function ‘FinalizeSections’:
source/MemoryModule.c:257: error: ‘PIMAGE_SECTION_HEADER’ undeclared (first use in this function)
source/MemoryModule.c:257: error: expected ‘;’ before ‘section’
source/MemoryModule.c:260: error: ‘struct tagMEMORYMODULE’ has no member named ‘headers’
source/MemoryModule.c:260: error: ‘section’ undeclared (first use in this function)
source/MemoryModule.c:262: error: ‘DWORD’ undeclared (first use in this function)
source/MemoryModule.c:262: error: expected ‘;’ before ‘protect’
source/MemoryModule.c:263: error: ‘IMAGE_SCN_MEM_EXECUTE’ undeclared (first use in this function)
source/MemoryModule.c:264: error: ‘IMAGE_SCN_MEM_READ’ undeclared (first use in this function)
source/MemoryModule.c:265: error: ‘IMAGE_SCN_MEM_WRITE’ undeclared (first use in this function)
source/MemoryModule.c:267: error: ‘IMAGE_SCN_MEM_DISCARDABLE’ undeclared (first use in this function)
source/MemoryModule.c:270: warning: implicit declaration of function ‘VirtualFree’
source/MemoryModule.c:270: error: ‘LPVOID’ undeclared (first use in this function)
source/MemoryModule.c:270: error: expected ‘)’ before ‘section’
source/MemoryModule.c:275: error: ‘protect’ undeclared (first use in this function)
source/MemoryModule.c:276: error: ‘IMAGE_SCN_MEM_NOT_CACHED’ undeclared (first use in this function)
source/MemoryModule.c:277: error: ‘PAGE_NOCACHE’ undeclared (first use in this function)
source/MemoryModule.c:280: error: ‘size’ undeclared (first use in this function)
source/MemoryModule.c:283: error: ‘IMAGE_SCN_CNT_INITIALIZED_DATA’ undeclared (first use in this function)
source/MemoryModule.c:284: error: ‘struct tagMEMORYMODULE’ has no member named ‘headers’
source/MemoryModule.c:285: error: ‘IMAGE_SCN_CNT_UNINITIALIZED_DATA’ undeclared (first use in this function)
source/MemoryModule.c:286: error: ‘struct tagMEMORYMODULE’ has no member named ‘headers’
source/MemoryModule.c:292: warning: implicit declaration of function ‘VirtualProtect’
source/MemoryModule.c:292: error: expected ‘)’ before ‘section’
source/MemoryModule.c: At top level:
source/MemoryModule.c:302: error: expected declaration specifiers or ‘...’ before ‘DWORD’
source/MemoryModule.c: In function ‘PerformBaseRelocation’:
source/MemoryModule.c:304: error: ‘DWORD’ undeclared (first use in this function)
source/MemoryModule.c:304: error: expected ‘;’ before ‘i’
source/MemoryModule.c:305: error: ‘struct tagMEMORYMODULE’ has no member named ‘codeBase’
source/MemoryModule.c:307: error: ‘PIMAGE_DATA_DIRECTORY’ undeclared (first use in this function)
source/MemoryModule.c:307: error: expected ‘;’ before ‘directory’
source/MemoryModule.c:308: error: ‘directory’ undeclared (first use in this function)
source/MemoryModule.c:310: error: ‘PIMAGE_BASE_RELOCATION’ undeclared (first use in this function)
source/MemoryModule.c:310: error: expected ‘;’ before ‘relocation’
source/MemoryModule.c:311: error: ‘relocation’ undeclared (first use in this function)
source/MemoryModule.c:314: error: ‘IMAGE_BASE_RELOCATION’ undeclared (first use in this function)
source/MemoryModule.c:315: error: ‘i’ undeclared (first use in this function)
source/MemoryModule.c:315: warning: left-hand operand of comma expression has no effect
source/MemoryModule.c:317: error: ‘patchAddrHL’ undeclared (first use in this function)
source/MemoryModule.c:327: error: ‘IMAGE_REL_BASED_ABSOLUTE’ undeclared (first use in this function)
source/MemoryModule.c:331: error: ‘IMAGE_REL_BASED_HIGHLOW’ undeclared (first use in this function)
source/MemoryModule.c:333: error: expected expression before ‘)’ token
source/MemoryModule.c:334: error: ‘delta’ undeclared (first use in this function)
source/MemoryModule.c:344: error: expected ‘)’ before ‘relocation’
source/MemoryModule.c: In function ‘BuildImportTable’:
source/MemoryModule.c:353: error: ‘struct tagMEMORYMODULE’ has no member named ‘codeBase’
source/MemoryModule.c:355: error: ‘PIMAGE_DATA_DIRECTORY’ undeclared (first use in this function)
source/MemoryModule.c:355: error: expected ‘;’ before ‘directory’
source/MemoryModule.c:356: error: ‘directory’ undeclared (first use in this function)
source/MemoryModule.c:358: error: ‘PIMAGE_IMPORT_DESCRIPTOR’ undeclared (first use in this function)
source/MemoryModule.c:358: error: expected ‘;’ before ‘importDesc’
source/MemoryModule.c:359: warning: implicit declaration of function ‘IsBadReadPtr’
source/MemoryModule.c:359: error: ‘importDesc’ undeclared (first use in this function)
source/MemoryModule.c:359: error: ‘IMAGE_IMPORT_DESCRIPTOR’ undeclared (first use in this function)
source/MemoryModule.c:361: error: ‘DWORD’ undeclared (first use in this function)
source/MemoryModule.c:361: error: ‘thunkRef’ undeclared (first use in this function)
source/MemoryModule.c:361: error: ‘funcRef’ undeclared (first use in this function)
source/MemoryModule.c:361: warning: left-hand operand of comma expression has no effect
source/MemoryModule.c:362: error: ‘HMODULE’ undeclared (first use in this function)
source/MemoryModule.c:362: error: expected ‘;’ before ‘handle’
source/MemoryModule.c:364: error: ‘handle’ undeclared (first use in this function)
source/MemoryModule.c:364: warning: implicit declaration of function ‘MyLoadLibrary’
source/MemoryModule.c:365: error: ‘INVALID_HANDLE_VALUE’ undeclared (first use in this function)
source/MemoryModule.c:375: error: ‘struct tagMEMORYMODULE’ has no member named ‘modules’
source/MemoryModule.c:375: error: expected expression before ‘)’ token
source/MemoryModule.c:376: error: ‘struct tagMEMORYMODULE’ has no member named ‘modules’
source/MemoryModule.c:376: error: ‘NULL’ undeclared (first use in this function)
source/MemoryModule.c:378: warning: implicit declaration of function ‘SetLastError’
source/MemoryModule.c:378: error: ‘ERROR_NOT_ENOUGH_MEMORY’ undeclared (first use in this function)
source/MemoryModule.c:383: error: ‘struct tagMEMORYMODULE’ has no member named ‘modules’
source/MemoryModule.c:383: error: ‘struct tagMEMORYMODULE’ has no member named ‘numModules’
source/MemoryModule.c:386: error: expected expression before ‘)’ token
source/MemoryModule.c:387: error: expected expression before ‘)’ token
source/MemoryModule.c:390: error: expected expression before ‘)’ token
source/MemoryModule.c:391: error: expected expression before ‘)’ token
source/MemoryModule.c:393: warning: left-hand operand of comma expression has no effect
source/MemoryModule.c:395: error: expected ‘(’ before ‘IMAGE_SNAP_BY_ORDINAL’
source/MemoryModule.c:395: warning: implicit declaration of function ‘IMAGE_SNAP_BY_ORDINAL’
source/MemoryModule.c: In function ‘MemoryLoadLibrary’:
source/MemoryModule.c:428: error: ‘PIMAGE_DOS_HEADER’ undeclared (first use in this function)
source/MemoryModule.c:428: error: expected ‘;’ before ‘dos_header’
source/MemoryModule.c:429: error: ‘PIMAGE_NT_HEADERS’ undeclared (first use in this function)
source/MemoryModule.c:429: error: expected ‘;’ before ‘old_header’
source/MemoryModule.c:431: error: ‘DWORD’ undeclared (first use in this function)
source/MemoryModule.c:431: error: expected ‘;’ before ‘locationDelta’
source/MemoryModule.c:432: error: ‘DllEntryProc’ undeclared (first use in this function)
source/MemoryModule.c:432: error: expected ‘;’ before ‘DllEntry’
source/MemoryModule.c:433: error: ‘BOOL’ undeclared (first use in this function)
source/MemoryModule.c:433: error: expected ‘;’ before ‘successfull’
source/MemoryModule.c:438: warning: implicit declaration of function ‘stricmp’
source/MemoryModule.c:438: error: ‘MEMORYMODULE’ has no member named ‘name’
source/MemoryModule.c:439: error: ‘MEMORYMODULE’ has no member named ‘refcount’
source/MemoryModule.c:440: error: ‘HMODULE’ undeclared (first use in this function)
source/MemoryModule.c:440: error: expected ‘;’ before ‘p’
source/MemoryModule.c:442: error: ‘MEMORYMODULE’ has no member named ‘next’
source/MemoryModule.c:447: error: ‘dos_header’ undeclared (first use in this function)
source/MemoryModule.c:447: error: expected ‘;’ before ‘data’
source/MemoryModule.c:448: error: ‘IMAGE_DOS_SIGNATURE’ undeclared (first use in this function)
source/MemoryModule.c:450: error: ‘ERROR_BAD_FORMAT’ undeclared (first use in this function)
source/MemoryModule.c:454: error: ‘NULL’ undeclared (first use in this function)
source/MemoryModule.c:457: error: ‘old_header’ undeclared (first use in this function)
source/MemoryModule.c:458: error: ‘IMAGE_NT_SIGNATURE’ undeclared (first use in this function)
source/MemoryModule.c:468: error: ‘LPVOID’ undeclared (first use in this function)
source/MemoryModule.c:470: error: ‘MEM_RESERVE’ undeclared (first use in this function)
source/MemoryModule.c:471: warning: cast to pointer from integer of different size
source/MemoryModule.c:478: warning: cast to pointer from integer of different size
source/MemoryModule.c:482: error: ‘ERROR_NOT_ENOUGH_MEMORY’ undeclared (first use in this function)
source/MemoryModule.c:489: warning: implicit declaration of function ‘HeapAlloc’
source/MemoryModule.c:489: warning: implicit declaration of function ‘GetProcessHeap’
source/MemoryModule.c:489: warning: cast to pointer from integer of different size
source/MemoryModule.c:490: error: ‘struct tagMEMORYMODULE’ has no member named ‘codeBase’
source/MemoryModule.c:491: error: ‘struct tagMEMORYMODULE’ has no member named ‘numModules’
source/MemoryModule.c:492: error: ‘struct tagMEMORYMODULE’ has no member named ‘modules’
source/MemoryModule.c:493: error: ‘struct tagMEMORYMODULE’ has no member named ‘initialized’
source/MemoryModule.c:494: error: ‘struct tagMEMORYMODULE’ has no member named ‘next’
source/MemoryModule.c:494: error: ‘struct tagMEMORYMODULE’ has no member named ‘prev’
source/MemoryModule.c:495: error: ‘struct tagMEMORYMODULE’ has no member named ‘refcount’
source/MemoryModule.c:496: error: ‘struct tagMEMORYMODULE’ has no member named ‘name’
source/MemoryModule.c:496: warning: implicit declaration of function ‘strdup’
source/MemoryModule.c:496: warning: incompatible implicit declaration of built-in function ‘strdup’
source/MemoryModule.c:497: error: ‘struct tagMEMORYMODULE’ has no member named ‘name_table’
source/MemoryModule.c:503: error: ‘MEM_COMMIT’ undeclared (first use in this function)
source/MemoryModule.c:510: warning: cast to pointer from integer of different size
source/MemoryModule.c:513: warning: incompatible implicit declaration of built-in function ‘memcpy’
source/MemoryModule.c:514: error: ‘struct tagMEMORYMODULE’ has no member named ‘headers’
source/MemoryModule.c:517: error: ‘struct tagMEMORYMODULE’ has no member named ‘headers’
source/MemoryModule.c:517: error: expected ‘;’ before ‘code’
source/MemoryModule.c:520: error: too many arguments to function ‘CopySections’
source/MemoryModule.c:523: error: ‘locationDelta’ undeclared (first use in this function)
source/MemoryModule.c:525: error: too many arguments to function ‘PerformBaseRelocation’
source/MemoryModule.c:536: error: ‘struct tagMEMORYMODULE’ has no member named ‘headers’
source/MemoryModule.c:538: error: ‘DllEntry’ undeclared (first use in this function)
source/MemoryModule.c:538: error: ‘struct tagMEMORYMODULE’ has no member named ‘headers’
source/MemoryModule.c:549: error: ‘successfull’ undeclared (first use in this function)
source/MemoryModule.c:549: error: ‘HINSTANCE’ undeclared (first use in this function)
source/MemoryModule.c:549: error: expected ‘)’ before ‘code’
source/MemoryModule.c:557: error: ‘struct tagMEMORYMODULE’ has no member named ‘initialized’
source/MemoryModule.c:566: warning: incompatible implicit declaration of built-in function ‘free’
source/MemoryModule.c:566: error: ‘struct tagMEMORYMODULE’ has no member named ‘name’
source/MemoryModule.c: In function ‘GetNameTable’:
source/MemoryModule.c:584: error: ‘PIMAGE_EXPORT_DIRECTORY’ undeclared (first use in this function)
source/MemoryModule.c:584: error: expected ‘;’ before ‘exports’
source/MemoryModule.c:585: error: ‘PIMAGE_DATA_DIRECTORY’ undeclared (first use in this function)
source/MemoryModule.c:585: error: expected ‘;’ before ‘directory’
source/MemoryModule.c:586: error: ‘DWORD’ undeclared (first use in this function)
source/MemoryModule.c:586: error: expected ‘;’ before ‘i’
source/MemoryModule.c:587: error: ‘WORD’ undeclared (first use in this function)
source/MemoryModule.c:587: error: ‘ordinal’ undeclared (first use in this function)
source/MemoryModule.c:590: error: ‘struct tagMEMORYMODULE’ has no member named ‘name_table’
source/MemoryModule.c:591: error: ‘struct tagMEMORYMODULE’ has no member named ‘name_table’
source/MemoryModule.c:593: error: ‘struct tagMEMORYMODULE’ has no member named ‘codeBase’
source/MemoryModule.c:594: error: ‘directory’ undeclared (first use in this function)
source/MemoryModule.c:594: error: ‘struct tagMEMORYMODULE’ has no member named ‘headers’
source/MemoryModule.c:594: error: ‘IMAGE_DIRECTORY_ENTRY_EXPORT’ undeclared (first use in this function)
source/MemoryModule.c:595: error: ‘exports’ undeclared (first use in this function)
source/MemoryModule.c:597: error: ‘nameRef’ undeclared (first use in this function)
source/MemoryModule.c:597: error: expected expression before ‘)’ token
source/MemoryModule.c:598: error: expected expression before ‘)’ token
source/MemoryModule.c:600: error: ‘struct tagMEMORYMODULE’ has no member named ‘name_table’
source/MemoryModule.c:600: warning: implicit declaration of function ‘malloc’
source/MemoryModule.c:600: warning: incompatible implicit declaration of built-in function ‘malloc’
source/MemoryModule.c:602: error: ‘NULL’ undeclared (first use in this function)
source/MemoryModule.c:605: error: ‘i’ undeclared (first use in this function)
source/MemoryModule.c:607: error: ‘struct NAME_TABLE’ has no member named ‘ordinal’
source/MemoryModule.c:610: warning: implicit declaration of function ‘qsort’
source/MemoryModule.c: At top level:
source/MemoryModule.c:614: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘MemoryGetProcAddress’
source/MemoryModule.c: In function ‘MemoryFreeLibrary’:
source/MemoryModule.c:660: error: ‘NULL’ undeclared (first use in this function)
source/MemoryModule.c:662: error: ‘struct tagMEMORYMODULE’ has no member named ‘initialized’
source/MemoryModule.c:665: error: ‘DllEntryProc’ undeclared (first use in this function)
source/MemoryModule.c:665: error: expected ‘;’ before ‘DllEntry’
source/MemoryModule.c:666: error: ‘DllEntry’ undeclared (first use in this function)
source/MemoryModule.c:666: error: ‘HINSTANCE’ undeclared (first use in this function)
source/MemoryModule.c:666: error: expected ‘)’ before ‘module’
source/MemoryModule.c:667: error: ‘struct tagMEMORYMODULE’ has no member named ‘initialized’
source/MemoryModule.c:670: error: ‘struct tagMEMORYMODULE’ has no member named ‘modules’
source/MemoryModule.c:673: error: ‘struct tagMEMORYMODULE’ has no member named ‘numModules’
source/MemoryModule.c:674: error: ‘struct tagMEMORYMODULE’ has no member named ‘modules’
source/MemoryModule.c:674: error: ‘INVALID_HANDLE_VALUE’ undeclared (first use in this function)
source/MemoryModule.c:675: warning: implicit declaration of function ‘MyFreeLibrary’
source/MemoryModule.c:675: error: ‘struct tagMEMORYMODULE’ has no member named ‘modules’
source/MemoryModule.c:677: warning: incompatible implicit declaration of built-in function ‘free’
source/MemoryModule.c:677: error: ‘struct tagMEMORYMODULE’ has no member named ‘modules’
source/MemoryModule.c:680: error: ‘struct tagMEMORYMODULE’ has no member named ‘codeBase’
source/MemoryModule.c:682: error: ‘struct tagMEMORYMODULE’ has no member named ‘codeBase’
source/MemoryModule.c:682: error: ‘MEM_RELEASE’ undeclared (first use in this function)
source/MemoryModule.c:684: error: ‘struct tagMEMORYMODULE’ has no member named ‘name_table’
source/MemoryModule.c:685: warning: incompatible implicit declaration of built-in function ‘free’
source/MemoryModule.c:685: error: ‘struct tagMEMORYMODULE’ has no member named ‘name_table’
source/MemoryModule.c:687: warning: implicit declaration of function ‘HeapFree’
error: command 'gcc' failed with exit status 1
abbs@abbs-ubuntu-be111:~/Downloads/py2exe-0.6.9$ 


```

---

### Post by shae on 2010-01-28
Sorry, but I believe py2exe is only for Windows environments. :rolleyes:

---

