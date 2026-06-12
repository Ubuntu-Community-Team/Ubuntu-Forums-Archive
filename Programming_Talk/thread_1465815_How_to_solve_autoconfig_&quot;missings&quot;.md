---
title: "How to solve autoconfig &quot;missings&quot;?"
date: 2010-04-29
forum: Programming Talk
---

### Post by ZequeZ on 2010-04-29
Well, I'm new with the autoconf, automake, make, configure, etc... And I barely know what are them for...
The problem I have it's that I'm trying to compile a open source program, but after an "autoscan" I get a lot of missings...

```

configure.ac: warning: missing AC_CHECK_FUNCS([bzero]) wanted by: dep/include/mysql/m_string.h:141
configure.ac: warning: missing AC_CHECK_FUNCS([clock_gettime]) wanted by: dep/tbb/include/tbb/tick_count.h:108
configure.ac: warning: missing AC_CHECK_FUNCS([floor]) wanted by: src/game/NPCHandler.cpp:189
configure.ac: warning: missing AC_CHECK_FUNCS([ftruncate]) wanted by: contrib/vmap_extractor_v2/stormlib/StormPortLinux.cpp:111
configure.ac: warning: missing AC_CHECK_FUNCS([getcwd]) wanted by: contrib/git_id/git_id.cpp:123
configure.ac: warning: missing AC_CHECK_FUNCS([localtime_r]) wanted by: dep/src/sockets/StdoutLog.cpp:53
configure.ac: warning: missing AC_CHECK_FUNCS([mkdir]) wanted by: src/shared/vmap/TileAssembler.cpp:58
configure.ac: warning: missing AC_CHECK_FUNCS([munmap]) wanted by: contrib/vmap_extractor_v2/stormlib/zlib/minigzip.c:158
configure.ac: warning: missing AC_CHECK_FUNCS([putenv]) wanted by: contrib/git_id/git_id.cpp:299
configure.ac: warning: missing AC_CHECK_FUNCS([rint]) wanted by: contrib/vmap_extractor_v2/stormlib/GfxDecode.cpp:376
configure.ac: warning: missing AC_CHECK_FUNCS([setenv]) wanted by: dep/src/sockets/Utility.cpp:468
configure.ac: warning: missing AC_CHECK_FUNCS([stpcpy]) wanted by: dep/include/mysql/m_string.h:100
configure.ac: warning: missing AC_CHECK_FUNCS([strcasecmp]) wanted by: dep/include/sockets/Utility.h:70
configure.ac: warning: missing AC_CHECK_FUNCS([strncasecmp]) wanted by: contrib/extractor/libmpq/parser.cpp:150
configure.ac: warning: missing AC_CHECK_FUNCS([strpbrk]) wanted by: contrib/extractor/libmpq/parser.cpp:43
configure.ac: warning: missing AC_CHECK_FUNCS([strrchr]) wanted by: contrib/vmap_extractor_v2/vmapextract/wdtfile.cpp:10
configure.ac: warning: missing AC_CHECK_FUNCS([strtol]) wanted by: src/game/Level3.cpp:1919
configure.ac: warning: missing AC_CHECK_FUNCS([strtoul]) wanted by: dep/include/mysql/m_string.h:225
configure.ac: warning: missing AC_CHECK_FUNCS([strtoull]) wanted by: dep/src/gsoap/stdsoap2.cpp:10286
configure.ac: warning: missing AC_CHECK_FUNCS([utime]) wanted by: contrib/vmap_extractor_v2/stormlib/zlib/contrib/minizip/miniunz.c:68
configure.ac: warning: missing AC_CHECK_HEADERS([float.h]) wanted by: src/shared/Common.h:118
configure.ac: warning: missing AC_CHECK_HEADERS([utime.h]) wanted by: contrib/vmap_extractor_v2/stormlib/zlib/contrib/minizip/minizip.c:10
configure.ac: warning: missing AC_C_RESTRICT wanted by: dep/include/g3dlite/G3D/platform.h:193
configure.ac: warning: missing AC_FUNC_ALLOCA wanted by: dep/include/mysql/my_global.h:355
configure.ac: warning: missing AC_FUNC_CHOWN wanted by: contrib/vmap_extractor_v2/stormlib/bzip2/bzip2.c:1147
configure.ac: warning: missing AC_FUNC_MKTIME wanted by: contrib/vmap_extractor_v2/stormlib/zlib/contrib/minizip/miniunz.c:67
configure.ac: warning: missing AC_FUNC_MMAP wanted by: contrib/vmap_extractor_v2/stormlib/zlib/minigzip.c:150
configure.ac: warning: missing AC_FUNC_STRNLEN wanted by: dep/include/mysql/m_string.h:204
configure.ac: warning: missing AC_FUNC_STRTOD wanted by: dep/src/gsoap/stdsoap2.cpp:9749
configure.ac: warning: missing AC_PREREQ wanted by: autoscan
configure.ac: warning: missing AC_TYPE_INT16_T wanted by: contrib/extractor/loadlib/loadlib.h:22
configure.ac: warning: missing AC_TYPE_INT32_T wanted by: contrib/extractor/loadlib/loadlib.h:21
configure.ac: warning: missing AC_TYPE_INT64_T wanted by: contrib/extractor/loadlib/loadlib.h:20
configure.ac: warning: missing AC_TYPE_INT8_T wanted by: contrib/extractor/loadlib/loadlib.h:23
configure.ac: warning: missing AC_TYPE_OFF_T wanted by: contrib/vmap_extractor_v2/stormlib/zlib/minigzip.c:141
configure.ac: warning: missing AC_TYPE_PID_T wanted by: src/shared/Util.cpp:206
configure.ac: warning: missing AC_TYPE_SIZE_T wanted by: src/game/NPCHandler.cpp:164
configure.ac: warning: missing AC_TYPE_SSIZE_T wanted by: src/game/WorldSocket.cpp:284
configure.ac: warning: missing AC_TYPE_UINT16_T wanted by: contrib/vmap_extractor_v2/stormlib/StormPortMac.cpp:157
configure.ac: warning: missing AC_TYPE_UINT32_T wanted by: contrib/vmap_extractor_v2/stormlib/StormPortMac.cpp:112
configure.ac: warning: missing AC_TYPE_UINT64_T wanted by: contrib/extractor/loadlib/loadlib.h:15
configure.ac: warning: missing AC_TYPE_UINT8_T wanted by: contrib/vmap_extractor_v2/stormlib/GfxDecode.cpp:86

```And I don't understand why it says that is wanted by those files, because when I check those files lines there is not any call to the types or functions :S

How do I install the auto-stuff libraries missing? :(

Sorry for my English =/

EDIT: Never mind, now I'm using autoreconf and works. Still I don't get exactly what it does :(

---

### Post by soltanis on 2010-04-30
Maybe you don't have all the libraries installed? Have you installed the build-essential package?

---

