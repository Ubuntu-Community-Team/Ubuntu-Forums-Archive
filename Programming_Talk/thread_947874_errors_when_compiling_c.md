---
title: "errors when compiling c"
date: 2008-10-14
forum: Programming Talk
---

### Post by themusicalduck on 2008-10-14
Hey,

I'm trying to compile a very basic 'hello world' program in c using scite or geany.When pressing compile in scite or geany, on a saved file named hello.c, this is what comes up in the console..

```

>gcc -pedantic -Os -c hello.c -o hello.o -std=c99
In file included from /usr/include/stdio.h:34,
                 from hello.c:3:
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/stddef.h: In function â&#8364;&#732;mainâ&#8364;&#8482;:
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/stddef.h:214: error: storage class specified for parameter â&#8364;&#732;size_tâ&#8364;&#8482;
In file included from /usr/include/stdio.h:36,
                 from hello.c:3:
/usr/include/bits/types.h:31: error: storage class specified for parameter â&#8364;&#732;__u_charâ&#8364;&#8482;
/usr/include/bits/types.h:32: error: storage class specified for parameter â&#8364;&#732;__u_shortâ&#8364;&#8482;
/usr/include/bits/types.h:33: error: storage class specified for parameter â&#8364;&#732;__u_intâ&#8364;&#8482;
/usr/include/bits/types.h:34: error: storage class specified for parameter â&#8364;&#732;__u_longâ&#8364;&#8482;
/usr/include/bits/types.h:37: error: storage class specified for parameter â&#8364;&#732;__int8_tâ&#8364;&#8482;
/usr/include/bits/types.h:38: error: storage class specified for parameter â&#8364;&#732;__uint8_tâ&#8364;&#8482;
/usr/include/bits/types.h:39: error: storage class specified for parameter â&#8364;&#732;__int16_tâ&#8364;&#8482;
/usr/include/bits/types.h:40: error: storage class specified for parameter â&#8364;&#732;__uint16_tâ&#8364;&#8482;
/usr/include/bits/types.h:41: error: storage class specified for parameter â&#8364;&#732;__int32_tâ&#8364;&#8482;
/usr/include/bits/types.h:42: error: storage class specified for parameter â&#8364;&#732;__uint32_tâ&#8364;&#8482;
/usr/include/bits/types.h:44: error: storage class specified for parameter â&#8364;&#732;__int64_tâ&#8364;&#8482;
/usr/include/bits/types.h:45: error: storage class specified for parameter â&#8364;&#732;__uint64_tâ&#8364;&#8482;
/usr/include/bits/types.h:53: error: storage class specified for parameter â&#8364;&#732;__quad_tâ&#8364;&#8482;
/usr/include/bits/types.h:54: error: storage class specified for parameter â&#8364;&#732;__u_quad_tâ&#8364;&#8482;
In file included from /usr/include/stdio.h:36,
                 from hello.c:3:
/usr/include/bits/types.h:134: error: storage class specified for parameter â&#8364;&#732;__dev_tâ&#8364;&#8482;
/usr/include/bits/types.h:135: error: storage class specified for parameter â&#8364;&#732;__uid_tâ&#8364;&#8482;
/usr/include/bits/types.h:136: error: storage class specified for parameter â&#8364;&#732;__gid_tâ&#8364;&#8482;
/usr/include/bits/types.h:137: error: storage class specified for parameter â&#8364;&#732;__ino_tâ&#8364;&#8482;
/usr/include/bits/types.h:138: error: storage class specified for parameter â&#8364;&#732;__ino64_tâ&#8364;&#8482;
/usr/include/bits/types.h:139: error: storage class specified for parameter â&#8364;&#732;__mode_tâ&#8364;&#8482;
/usr/include/bits/types.h:140: error: storage class specified for parameter â&#8364;&#732;__nlink_tâ&#8364;&#8482;
/usr/include/bits/types.h:141: error: storage class specified for parameter â&#8364;&#732;__off_tâ&#8364;&#8482;
/usr/include/bits/types.h:142: error: storage class specified for parameter â&#8364;&#732;__off64_tâ&#8364;&#8482;
/usr/include/bits/types.h:143: error: storage class specified for parameter â&#8364;&#732;__pid_tâ&#8364;&#8482;
/usr/include/bits/types.h:144: error: storage class specified for parameter â&#8364;&#732;__fsid_tâ&#8364;&#8482;
/usr/include/bits/types.h:145: error: storage class specified for parameter â&#8364;&#732;__clock_tâ&#8364;&#8482;
/usr/include/bits/types.h:146: error: storage class specified for parameter â&#8364;&#732;__rlim_tâ&#8364;&#8482;
/usr/include/bits/types.h:147: error: storage class specified for parameter â&#8364;&#732;__rlim64_tâ&#8364;&#8482;
/usr/include/bits/types.h:148: error: storage class specified for parameter â&#8364;&#732;__id_tâ&#8364;&#8482;
/usr/include/bits/types.h:149: error: storage class specified for parameter â&#8364;&#732;__time_tâ&#8364;&#8482;
/usr/include/bits/types.h:150: error: storage class specified for parameter â&#8364;&#732;__useconds_tâ&#8364;&#8482;
/usr/include/bits/types.h:151: error: storage class specified for parameter â&#8364;&#732;__suseconds_tâ&#8364;&#8482;
/usr/include/bits/types.h:153: error: storage class specified for parameter â&#8364;&#732;__daddr_tâ&#8364;&#8482;
/usr/include/bits/types.h:154: error: storage class specified for parameter â&#8364;&#732;__swblk_tâ&#8364;&#8482;
/usr/include/bits/types.h:155: error: storage class specified for parameter â&#8364;&#732;__key_tâ&#8364;&#8482;
/usr/include/bits/types.h:158: error: storage class specified for parameter â&#8364;&#732;__clockid_tâ&#8364;&#8482;
/usr/include/bits/types.h:161: error: storage class specified for parameter â&#8364;&#732;__timer_tâ&#8364;&#8482;
/usr/include/bits/types.h:164: error: storage class specified for parameter â&#8364;&#732;__blksize_tâ&#8364;&#8482;
/usr/include/bits/types.h:169: error: storage class specified for parameter â&#8364;&#732;__blkcnt_tâ&#8364;&#8482;
/usr/include/bits/types.h:170: error: storage class specified for parameter â&#8364;&#732;__blkcnt64_tâ&#8364;&#8482;
/usr/include/bits/types.h:173: error: storage class specified for parameter â&#8364;&#732;__fsblkcnt_tâ&#8364;&#8482;
/usr/include/bits/types.h:174: error: storage class specified for parameter â&#8364;&#732;__fsblkcnt64_tâ&#8364;&#8482;
/usr/include/bits/types.h:177: error: storage class specified for parameter â&#8364;&#732;__fsfilcnt_tâ&#8364;&#8482;
/usr/include/bits/types.h:178: error: storage class specified for parameter â&#8364;&#732;__fsfilcnt64_tâ&#8364;&#8482;
/usr/include/bits/types.h:180: error: storage class specified for parameter â&#8364;&#732;__ssize_tâ&#8364;&#8482;
/usr/include/bits/types.h:184: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;__loff_tâ&#8364;&#8482;
/usr/include/bits/types.h:185: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/bits/types.h:186: error: storage class specified for parameter â&#8364;&#732;__caddr_tâ&#8364;&#8482;
/usr/include/bits/types.h:189: error: storage class specified for parameter â&#8364;&#732;__intptr_tâ&#8364;&#8482;
/usr/include/bits/types.h:192: error: storage class specified for parameter â&#8364;&#732;__socklen_tâ&#8364;&#8482;
In file included from hello.c:3:
/usr/include/stdio.h:49: error: storage class specified for parameter â&#8364;&#732;FILEâ&#8364;&#8482;
/usr/include/stdio.h:65: error: storage class specified for parameter â&#8364;&#732;__FILEâ&#8364;&#8482;
In file included from /usr/include/_G_config.h:20,
                 from /usr/include/libio.h:32,
                 from /usr/include/stdio.h:75,
                 from hello.c:3:
/usr/include/wchar.h:90: error: storage class specified for parameter â&#8364;&#732;__mbstate_tâ&#8364;&#8482;
In file included from /usr/include/libio.h:32,
                 from /usr/include/stdio.h:75,
                 from hello.c:3:
/usr/include/_G_config.h:24: error: expected specifier-qualifier-list before â&#8364;&#732;__off_tâ&#8364;&#8482;
/usr/include/_G_config.h:26: error: storage class specified for parameter â&#8364;&#732;_G_fpos_tâ&#8364;&#8482;
/usr/include/_G_config.h:29: error: expected specifier-qualifier-list before â&#8364;&#732;__off64_tâ&#8364;&#8482;
/usr/include/_G_config.h:31: error: storage class specified for parameter â&#8364;&#732;_G_fpos64_tâ&#8364;&#8482;
/usr/include/_G_config.h:53: error: storage class specified for parameter â&#8364;&#732;_G_int16_tâ&#8364;&#8482;
/usr/include/_G_config.h:54: error: storage class specified for parameter â&#8364;&#732;_G_int32_tâ&#8364;&#8482;
/usr/include/_G_config.h:55: error: storage class specified for parameter â&#8364;&#732;_G_uint16_tâ&#8364;&#8482;
/usr/include/_G_config.h:56: error: storage class specified for parameter â&#8364;&#732;_G_uint32_tâ&#8364;&#8482;
In file included from /usr/include/libio.h:53,
                 from /usr/include/stdio.h:75,
                 from hello.c:3:
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/stdarg.h:43: error: storage class specified for parameter â&#8364;&#732;__gnuc_va_listâ&#8364;&#8482;
In file included from /usr/include/stdio.h:75,
                 from hello.c:3:
/usr/include/libio.h:180: error: storage class specified for parameter â&#8364;&#732;_IO_lock_tâ&#8364;&#8482;
/usr/include/libio.h:300: error: expected specifier-qualifier-list before â&#8364;&#732;__off_tâ&#8364;&#8482;
/usr/include/libio.h:341: error: storage class specified for parameter â&#8364;&#732;_IO_FILEâ&#8364;&#8482;
/usr/include/libio.h:346: error: storage class specified for parameter â&#8364;&#732;_IO_2_1_stdin_â&#8364;&#8482;
/usr/include/libio.h:347: error: storage class specified for parameter â&#8364;&#732;_IO_2_1_stdout_â&#8364;&#8482;
/usr/include/libio.h:348: error: storage class specified for parameter â&#8364;&#732;_IO_2_1_stderr_â&#8364;&#8482;
/usr/include/libio.h:364: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;__io_read_fnâ&#8364;&#8482;
/usr/include/libio.h:372: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;__io_write_fnâ&#8364;&#8482;
/usr/include/libio.h:381: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;__off64_tâ&#8364;&#8482;
/usr/include/libio.h:381: error: storage class specified for parameter â&#8364;&#732;__io_seek_fnâ&#8364;&#8482;
/usr/include/libio.h:384: error: storage class specified for parameter â&#8364;&#732;__io_close_fnâ&#8364;&#8482;
/usr/include/libio.h:416: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/libio.h:417: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/libio.h:418: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/libio.h:458: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/libio.h:459: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;_IO_FILEâ&#8364;&#8482;
/usr/include/libio.h:459: error: storage class specified for parameter â&#8364;&#732;_IO_putcâ&#8364;&#8482;
/usr/include/libio.h:460: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/libio.h:461: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/libio.h:463: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/libio.h:469: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/libio.h:470: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/libio.h:471: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/libio.h:488: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/libio.h:490: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/libio.h:492: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;_IO_padnâ&#8364;&#8482;
/usr/include/libio.h:493: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;_IO_sgetnâ&#8364;&#8482;
/usr/include/libio.h:495: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;_IO_seekoffâ&#8364;&#8482;
/usr/include/libio.h:496: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;_IO_seekposâ&#8364;&#8482;
/usr/include/libio.h:498: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
In file included from hello.c:3:
/usr/include/stdio.h:91: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;fpos_tâ&#8364;&#8482;
In file included from hello.c:3:
/usr/include/stdio.h:145: error: storage class specified for parameter â&#8364;&#732;stdinâ&#8364;&#8482;
/usr/include/stdio.h:146: error: storage class specified for parameter â&#8364;&#732;stdoutâ&#8364;&#8482;
/usr/include/stdio.h:147: error: storage class specified for parameter â&#8364;&#732;stderrâ&#8364;&#8482;
/usr/include/stdio.h:155: error: storage class specified for parameter â&#8364;&#732;removeâ&#8364;&#8482;
/usr/include/stdio.h:157: error: storage class specified for parameter â&#8364;&#732;renameâ&#8364;&#8482;
/usr/include/stdio.h:172: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:186: error: storage class specified for parameter â&#8364;&#732;tmpnamâ&#8364;&#8482;
/usr/include/stdio.h:214: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:219: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:249: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:255: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:307: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:311: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:331: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:337: error: storage class specified for parameter â&#8364;&#732;printfâ&#8364;&#8482;
/usr/include/stdio.h:340: error: storage class specified for parameter â&#8364;&#732;sprintfâ&#8364;&#8482;
/usr/include/stdio.h:346: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:352: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;__gnuc_va_listâ&#8364;&#8482;
/usr/include/stdio.h:352: error: storage class specified for parameter â&#8364;&#732;vprintfâ&#8364;&#8482;
/usr/include/stdio.h:355: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;__gnuc_va_listâ&#8364;&#8482;
/usr/include/stdio.h:355: error: storage class specified for parameter â&#8364;&#732;vsprintfâ&#8364;&#8482;
/usr/include/stdio.h:361: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;size_tâ&#8364;&#8482;
/usr/include/stdio.h:363: error: storage class specified for parameter â&#8364;&#732;snprintfâ&#8364;&#8482;
/usr/include/stdio.h:363: error: format string argument not a string type
/usr/include/stdio.h:365: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;size_tâ&#8364;&#8482;
/usr/include/stdio.h:366: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;__gnuc_va_listâ&#8364;&#8482;
/usr/include/stdio.h:367: error: storage class specified for parameter â&#8364;&#732;vsnprintfâ&#8364;&#8482;
/usr/include/stdio.h:367: error: format string argument not a string type
/usr/include/stdio.h:403: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:409: error: storage class specified for parameter â&#8364;&#732;scanfâ&#8364;&#8482;
/usr/include/stdio.h:412: error: storage class specified for parameter â&#8364;&#732;sscanfâ&#8364;&#8482;
/usr/include/stdio.h:421: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:424: error: storage class specified for parameter â&#8364;&#732;scanfâ&#8364;&#8482;
/usr/include/stdio.h:424: error: redefinition of parameter â&#8364;&#732;scanfâ&#8364;&#8482;
/usr/include/stdio.h:409: error: previous definition of â&#8364;&#732;scanfâ&#8364;&#8482; was here
/usr/include/stdio.h:426: error: storage class specified for parameter â&#8364;&#732;sscanfâ&#8364;&#8482;
/usr/include/stdio.h:426: error: redefinition of parameter â&#8364;&#732;sscanfâ&#8364;&#8482;
/usr/include/stdio.h:412: error: previous definition of â&#8364;&#732;sscanfâ&#8364;&#8482; was here
/usr/include/stdio.h:449: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:457: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;__gnuc_va_listâ&#8364;&#8482;
/usr/include/stdio.h:458: error: storage class specified for parameter â&#8364;&#732;vscanfâ&#8364;&#8482;
/usr/include/stdio.h:462: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;__gnuc_va_listâ&#8364;&#8482;
/usr/include/stdio.h:463: error: storage class specified for parameter â&#8364;&#732;vsscanfâ&#8364;&#8482;
/usr/include/stdio.h:472: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:477: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;__gnuc_va_listâ&#8364;&#8482;
/usr/include/stdio.h:479: error: storage class specified for parameter â&#8364;&#732;vscanfâ&#8364;&#8482;
/usr/include/stdio.h:479: error: redefinition of parameter â&#8364;&#732;vscanfâ&#8364;&#8482;
/usr/include/stdio.h:458: error: previous definition of â&#8364;&#732;vscanfâ&#8364;&#8482; was here
/usr/include/stdio.h:480: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;__gnuc_va_listâ&#8364;&#8482;
/usr/include/stdio.h:484: error: storage class specified for parameter â&#8364;&#732;vsscanfâ&#8364;&#8482;
/usr/include/stdio.h:484: error: redefinition of parameter â&#8364;&#732;vsscanfâ&#8364;&#8482;
/usr/include/stdio.h:463: error: previous definition of â&#8364;&#732;vsscanfâ&#8364;&#8482; was here
/usr/include/stdio.h:509: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:510: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:516: error: storage class specified for parameter â&#8364;&#732;getcharâ&#8364;&#8482;
/usr/include/stdio.h:551: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;FILEâ&#8364;&#8482;
/usr/include/stdio.h:551: error: storage class specified for parameter â&#8364;&#732;fputcâ&#8364;&#8482;
/usr/include/stdio.h:552: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;FILEâ&#8364;&#8482;
/usr/include/stdio.h:552: error: storage class specified for parameter â&#8364;&#732;putcâ&#8364;&#8482;
/usr/include/stdio.h:558: error: storage class specified for parameter â&#8364;&#732;putcharâ&#8364;&#8482;
/usr/include/stdio.h:600: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;FILEâ&#8364;&#8482;
/usr/include/stdio.h:601: error: storage class specified for parameter â&#8364;&#732;fgetsâ&#8364;&#8482;
/usr/include/stdio.h:608: error: storage class specified for parameter â&#8364;&#732;getsâ&#8364;&#8482;
/usr/include/stdio.h:658: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;FILEâ&#8364;&#8482;
/usr/include/stdio.h:658: error: storage class specified for parameter â&#8364;&#732;fputsâ&#8364;&#8482;
/usr/include/stdio.h:664: error: storage class specified for parameter â&#8364;&#732;putsâ&#8364;&#8482;
/usr/include/stdio.h:671: error: expected declaration specifiers or â&#8364;&#732;...â&#8364;&#8482; before â&#8364;&#732;FILEâ&#8364;&#8482;
/usr/include/stdio.h:671: error: storage class specified for parameter â&#8364;&#732;ungetcâ&#8364;&#8482;
/usr/include/stdio.h:678: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;freadâ&#8364;&#8482;
/usr/include/stdio.h:684: error: expected â&#8364;&#732;=â&#8364;&#8482;, â&#8364;&#732;,â&#8364;&#8482;, â&#8364;&#732;;â&#8364;&#8482;, â&#8364;&#732;asmâ&#8364;&#8482; or â&#8364;&#732;__attribute__â&#8364;&#8482; before â&#8364;&#732;fwriteâ&#8364;&#8482;
/usr/include/stdio.h:718: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:723: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:728: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:767: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:772: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:795: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:797: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:799: error: expected â&#8364;&#732;)â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
/usr/include/stdio.h:815: error: storage class specified for parameter â&#8364;&#732;perrorâ&#8364;&#8482;
/usr/include/stdio.h:815: error: declaration for parameter â&#8364;&#732;perrorâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:671: error: declaration for parameter â&#8364;&#732;ungetcâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:664: error: declaration for parameter â&#8364;&#732;putsâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:658: error: declaration for parameter â&#8364;&#732;fputsâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:608: error: declaration for parameter â&#8364;&#732;getsâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:601: error: declaration for parameter â&#8364;&#732;fgetsâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:558: error: declaration for parameter â&#8364;&#732;putcharâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:552: error: declaration for parameter â&#8364;&#732;putcâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:551: error: declaration for parameter â&#8364;&#732;fputcâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:516: error: declaration for parameter â&#8364;&#732;getcharâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:484: error: declaration for parameter â&#8364;&#732;vsscanfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:479: error: declaration for parameter â&#8364;&#732;vscanfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:463: error: declaration for parameter â&#8364;&#732;vsscanfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:458: error: declaration for parameter â&#8364;&#732;vscanfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:426: error: declaration for parameter â&#8364;&#732;sscanfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:424: error: declaration for parameter â&#8364;&#732;scanfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:412: error: declaration for parameter â&#8364;&#732;sscanfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:409: error: declaration for parameter â&#8364;&#732;scanfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:367: error: declaration for parameter â&#8364;&#732;vsnprintfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:363: error: declaration for parameter â&#8364;&#732;snprintfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:355: error: declaration for parameter â&#8364;&#732;vsprintfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:352: error: declaration for parameter â&#8364;&#732;vprintfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:340: error: declaration for parameter â&#8364;&#732;sprintfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:337: error: declaration for parameter â&#8364;&#732;printfâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:186: error: declaration for parameter â&#8364;&#732;tmpnamâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:157: error: declaration for parameter â&#8364;&#732;renameâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:155: error: declaration for parameter â&#8364;&#732;removeâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:147: error: declaration for parameter â&#8364;&#732;stderrâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:146: error: declaration for parameter â&#8364;&#732;stdoutâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:145: error: declaration for parameter â&#8364;&#732;stdinâ&#8364;&#8482; but no such parameter
/usr/include/libio.h:459: error: declaration for parameter â&#8364;&#732;_IO_putcâ&#8364;&#8482; but no such parameter
/usr/include/libio.h:384: error: declaration for parameter â&#8364;&#732;__io_close_fnâ&#8364;&#8482; but no such parameter
/usr/include/libio.h:381: error: declaration for parameter â&#8364;&#732;__io_seek_fnâ&#8364;&#8482; but no such parameter
/usr/include/libio.h:348: error: parameter â&#8364;&#732;_IO_2_1_stderr_â&#8364;&#8482; has incomplete type
/usr/include/libio.h:348: error: declaration for parameter â&#8364;&#732;_IO_2_1_stderr_â&#8364;&#8482; but no such parameter
/usr/include/libio.h:347: error: parameter â&#8364;&#732;_IO_2_1_stdout_â&#8364;&#8482; has incomplete type
/usr/include/libio.h:347: error: declaration for parameter â&#8364;&#732;_IO_2_1_stdout_â&#8364;&#8482; but no such parameter
/usr/include/libio.h:346: error: parameter â&#8364;&#732;_IO_2_1_stdin_â&#8364;&#8482; has incomplete type
/usr/include/libio.h:346: error: declaration for parameter â&#8364;&#732;_IO_2_1_stdin_â&#8364;&#8482; but no such parameter
/usr/include/libio.h:341: error: declaration for parameter â&#8364;&#732;_IO_FILEâ&#8364;&#8482; but no such parameter
/usr/include/libio.h:180: error: parameter â&#8364;&#732;_IO_lock_tâ&#8364;&#8482; has incomplete type
/usr/include/libio.h:180: error: declaration for parameter â&#8364;&#732;_IO_lock_tâ&#8364;&#8482; but no such parameter
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/stdarg.h:43: error: declaration for parameter â&#8364;&#732;__gnuc_va_listâ&#8364;&#8482; but no such parameter
/usr/include/_G_config.h:56: error: declaration for parameter â&#8364;&#732;_G_uint32_tâ&#8364;&#8482; but no such parameter
/usr/include/_G_config.h:55: error: declaration for parameter â&#8364;&#732;_G_uint16_tâ&#8364;&#8482; but no such parameter
/usr/include/_G_config.h:54: error: declaration for parameter â&#8364;&#732;_G_int32_tâ&#8364;&#8482; but no such parameter
/usr/include/_G_config.h:53: error: declaration for parameter â&#8364;&#732;_G_int16_tâ&#8364;&#8482; but no such parameter
/usr/include/_G_config.h:31: error: declaration for parameter â&#8364;&#732;_G_fpos64_tâ&#8364;&#8482; but no such parameter
/usr/include/_G_config.h:26: error: declaration for parameter â&#8364;&#732;_G_fpos_tâ&#8364;&#8482; but no such parameter
/usr/include/wchar.h:90: error: declaration for parameter â&#8364;&#732;__mbstate_tâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:65: error: declaration for parameter â&#8364;&#732;__FILEâ&#8364;&#8482; but no such parameter
/usr/include/stdio.h:49: error: declaration for parameter â&#8364;&#732;FILEâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:192: error: declaration for parameter â&#8364;&#732;__socklen_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:189: error: declaration for parameter â&#8364;&#732;__intptr_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:186: error: declaration for parameter â&#8364;&#732;__caddr_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:180: error: declaration for parameter â&#8364;&#732;__ssize_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:178: error: declaration for parameter â&#8364;&#732;__fsfilcnt64_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:177: error: declaration for parameter â&#8364;&#732;__fsfilcnt_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:174: error: declaration for parameter â&#8364;&#732;__fsblkcnt64_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:173: error: declaration for parameter â&#8364;&#732;__fsblkcnt_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:170: error: declaration for parameter â&#8364;&#732;__blkcnt64_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:169: error: declaration for parameter â&#8364;&#732;__blkcnt_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:164: error: declaration for parameter â&#8364;&#732;__blksize_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:161: error: declaration for parameter â&#8364;&#732;__timer_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:158: error: declaration for parameter â&#8364;&#732;__clockid_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:155: error: declaration for parameter â&#8364;&#732;__key_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:154: error: declaration for parameter â&#8364;&#732;__swblk_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:153: error: declaration for parameter â&#8364;&#732;__daddr_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:151: error: declaration for parameter â&#8364;&#732;__suseconds_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:150: error: declaration for parameter â&#8364;&#732;__useconds_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:149: error: declaration for parameter â&#8364;&#732;__time_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:148: error: declaration for parameter â&#8364;&#732;__id_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:147: error: declaration for parameter â&#8364;&#732;__rlim64_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:146: error: declaration for parameter â&#8364;&#732;__rlim_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:145: error: declaration for parameter â&#8364;&#732;__clock_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:144: error: declaration for parameter â&#8364;&#732;__fsid_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:143: error: declaration for parameter â&#8364;&#732;__pid_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:142: error: declaration for parameter â&#8364;&#732;__off64_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:141: error: declaration for parameter â&#8364;&#732;__off_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:140: error: declaration for parameter â&#8364;&#732;__nlink_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:139: error: declaration for parameter â&#8364;&#732;__mode_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:138: error: declaration for parameter â&#8364;&#732;__ino64_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:137: error: declaration for parameter â&#8364;&#732;__ino_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:136: error: declaration for parameter â&#8364;&#732;__gid_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:135: error: declaration for parameter â&#8364;&#732;__uid_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:134: error: declaration for parameter â&#8364;&#732;__dev_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:54: error: declaration for parameter â&#8364;&#732;__u_quad_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:53: error: declaration for parameter â&#8364;&#732;__quad_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:45: error: declaration for parameter â&#8364;&#732;__uint64_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:44: error: declaration for parameter â&#8364;&#732;__int64_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:42: error: declaration for parameter â&#8364;&#732;__uint32_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:41: error: declaration for parameter â&#8364;&#732;__int32_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:40: error: declaration for parameter â&#8364;&#732;__uint16_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:39: error: declaration for parameter â&#8364;&#732;__int16_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:38: error: declaration for parameter â&#8364;&#732;__uint8_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:37: error: declaration for parameter â&#8364;&#732;__int8_tâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:34: error: declaration for parameter â&#8364;&#732;__u_longâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:33: error: declaration for parameter â&#8364;&#732;__u_intâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:32: error: declaration for parameter â&#8364;&#732;__u_shortâ&#8364;&#8482; but no such parameter
/usr/include/bits/types.h:31: error: declaration for parameter â&#8364;&#732;__u_charâ&#8364;&#8482; but no such parameter
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/stddef.h:214: error: declaration for parameter â&#8364;&#732;size_tâ&#8364;&#8482; but no such parameter
>Exit code: 1

```

this is what I'm trying to compile - 

int main()

#include <stdio.h>

{
	printf("hello world!/n");
	return 0;
}

I'm very very new to C, so could easily be something really obvious ](*,)

---

### Post by geirha on 2008-10-14
#include-lines needs to be on top. Also, it's "\n" not "/n".

---

### Post by jespdj on 2008-10-14
Well, #include lines do not necessarily need to be on top, but they should certainly not appear between the function header and the body of the function, as you are doing in your code.

---

### Post by themusicalduck on 2008-10-14
Thanks for the help. I knew it would be something blatantly stupid on my half ](*,)

but now when I click execute, it comes up with -

./geany_run_script.sh: 3: ./test: Permission denied

(program exited with code: 126)
Press return to continue

This is while running the program as root.

Edit: now it's just coming up with 'Failed to execute the terminal program'

---

### Post by mssever on 2008-10-14
> **themusicalduck said:**
> Thanks for the help. I knew it would be something blatantly stupid on my half ](*,)

but now when I click execute, it comes up with -

./geany_run_script.sh: 3: ./test: Permission denied

(program exited with code: 126)
Press return to continue

This is while running the program as root.
First, you shouldn't be running as root. It won't accomplish anything for you.

Have you checked the permissions of your executable? That could easily be the problem.

---

### Post by themusicalduck on 2008-10-14
I tried running it as root as the first thing I thought of when it said 'permission denied' was because it was trying to do something that I needed to be root as.

I tried running the program in my desktop folder instead, and this fixed the problem. When I looked in the folder I originally saved it in in home, the scripts were locked, but creating and using another folder fixed it somehow.

Thanks for the helpful replies.

---

### Post by mssever on 2008-10-14
> **themusicalduck said:**
> I tried running it as root as the first thing I thought of when it said 'permission denied' was because it was trying to do something that I needed to be root as.

I tried running the program in my desktop folder instead, and this fixed the problem. When I looked in the folder I originally saved it in in home, the scripts were locked, but creating and using another folder fixed it somehow.

Thanks for the helpful replies.
Sounds like you need to read up on Unix permissions (Wikipedia and Google are your friends here). People often think that running as root will fix all their problems. But that's only true for certain permissions problems. You can't understand when to use root and when not to--and why your script worked in one directory and not another--unless you understand permissions.

---

