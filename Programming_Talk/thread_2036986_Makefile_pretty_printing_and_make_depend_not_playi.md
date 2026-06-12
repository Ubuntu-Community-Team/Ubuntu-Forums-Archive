---
title: "Makefile pretty printing and make depend not playing nice"
date: 2012-08-03
forum: Programming Talk
---

### Post by qyot27 on 2012-08-03
I don't actually use the 'make depend' command when I compile said code, but make depend is called by the default rule.

The issue is, I realized that the pretty-printing instruction in utvideo's Makefile was rather nicely compact*, so I tried to use it with the FFMS2 C-plugin and x264.  With a really small change, both of them work fine with this, except for one part: generating .depend.

*the snippet itself from my attempt at using it with FFMS2:
```
ifndef V
$(foreach VAR, CC CXX AR RANLIB RC, \
    $(eval override $(VAR) = @printf " %s\t%s\n" $(VAR) "$$@"; $($(VAR))))
endif
```

More specifically, something in the steps that generate .depend is trying to access the prettyprinting step in a way it clearly doesn't like, because it complains that sh cannot find printf, like so:

```
$ make
 CC     .depend
/bin/sh: @printf: command not found
 CXX    .depend
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
/bin/sh: @printf: command not found
 CC     src/core/matroskaparser.o
 CC     src/core/stdiostream.o
 CXX    src/core/audiosource.o
src/core/audiosource.cpp: In member function 'void FFMS_AudioSource::DecodeNextBlock()':
src/core/audiosource.cpp:183:13: warning: 'int avcodec_decode_audio3(AVCodecContext*, int16_t*, int*, AVPacket*)' is deprecated (declared at /home/qyot27/win32_build/include/libavcodec/avcodec.h:3743) [-Wdeprecated-declarations]
src/core/audiosource.cpp:183:92: warning: 'int avcodec_decode_audio3(AVCodecContext*, int16_t*, int*, AVPacket*)' is deprecated (declared at /home/qyot27/win32_build/include/libavcodec/avcodec.h:3743) [-Wdeprecated-declarations]
 CXX    src/core/ffms.o
 CXX    src/core/haaliaudio.o
[...and so on]
```

Normally - that is, when it's not prettyprinting - the step that generates the .depend file isn't shown at all since those lines are prefaced with a @:
```
.depend: config.mak
	@rm -f .depend
	@$(foreach SRC, $(CORE_C), $(CC) $(CPPFLAGS) $(CFLAGS) $(SRC) -MT $(SRC:%.c=%.o) -MM -g0 1>> .depend;)
	@$(foreach SRC, $(CORE_CXX) $(IDX_CXX), $(CXX) $(CPPFLAGS) $(CXXFLAGS) $(SRC) -MT $(SRC:%.cpp=%.o) -MM -g0 1>> .depend;)
```


I understand the general principle behind what it's doing, but I'm not seeing the underlying reason why the printf failure is occurring.  It works fine afterward, it only occurs with the .depend step.

Ideally, I'd like to have it set up to where the .depend file still generates correctly, but it's not shown in the output to screen.  Errors/warnings in the actual .c and .cpp files need to be thrown to screen, though.  So, it *should* look like this:
```
$ make
[.depend is generated silently]
 CC     src/core/matroskaparser.o
 CC     src/core/stdiostream.o
 CXX    src/core/audiosource.o
src/core/audiosource.cpp: In member function 'void FFMS_AudioSource::DecodeNextBlock()':
src/core/audiosource.cpp:183:13: warning: 'int avcodec_decode_audio3(AVCodecContext*, int16_t*, int*, AVPacket*)' is deprecated (declared at /home/qyot27/win32_build/include/libavcodec/avcodec.h:3743) [-Wdeprecated-declarations]
src/core/audiosource.cpp:183:92: warning: 'int avcodec_decode_audio3(AVCodecContext*, int16_t*, int*, AVPacket*)' is deprecated (declared at /home/qyot27/win32_build/include/libavcodec/avcodec.h:3743) [-Wdeprecated-declarations]
 CXX    src/core/ffms.o
 CXX    src/core/haaliaudio.o
```
although I'd even be fine if there was no other choice but to have it look like:
```
$ make
 CC     .depend
 CXX    .depend
 CC     src/core/matroskaparser.o
 CC     src/core/stdiostream.o
 CXX    src/core/audiosource.o
src/core/audiosource.cpp: In member function 'void FFMS_AudioSource::DecodeNextBlock()':
src/core/audiosource.cpp:183:13: warning: 'int avcodec_decode_audio3(AVCodecContext*, int16_t*, int*, AVPacket*)' is deprecated (declared at /home/qyot27/win32_build/include/libavcodec/avcodec.h:3743) [-Wdeprecated-declarations]
src/core/audiosource.cpp:183:92: warning: 'int avcodec_decode_audio3(AVCodecContext*, int16_t*, int*, AVPacket*)' is deprecated (declared at /home/qyot27/win32_build/include/libavcodec/avcodec.h:3743) [-Wdeprecated-declarations]
 CXX    src/core/ffms.o
 CXX    src/core/haaliaudio.o
```
Just so long as the printf warnings are resolved.

---

### Post by spjackson on 2012-08-03
The problem is the @printf. You don't want @ there. I'm not sure whether you need one at all at this point, if so, then maybe before the foreach, like this.
```

ifndef V
@$(foreach VAR, CC CXX AR RANLIB RC, \
    $(eval override $(VAR) = printf " %s\t%s\n" $(VAR) "$$@"; $($(VAR))))
endif

```

---

### Post by qyot27 on 2012-08-03
The result of removing the @ from @printf:
```
$ make
 CC     .depend
 CC     .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
 CXX    .depend
printf " %s\t%s\n" CC "src/core/matroskaparser.o"; gcc -Wall -march=pentium3 -mtune=pentium3 -std=gnu99 -s -fomit-frame-pointer -I/home/qyot27/win32_build/include    -I. -Iinclude -D_FILE_OFFSET_BITS=64 -DFFMS_USE_FFMPEG_COMPAT  -c -o src/core/matroskaparser.o src/core/matroskaparser.c
 CC     src/core/matroskaparser.o
printf " %s\t%s\n" CC "src/core/stdiostream.o"; gcc -Wall -march=pentium3 -mtune=pentium3 -std=gnu99 -s -fomit-frame-pointer -I/home/qyot27/win32_build/include    -I. -Iinclude -D_FILE_OFFSET_BITS=64 -DFFMS_USE_FFMPEG_COMPAT  -c -o src/core/stdiostream.o src/core/stdiostream.c
 CC     src/core/stdiostream.o
printf " %s\t%s\n" CXX "src/core/audiosource.o"; g++ -Wall -D__STDC_CONSTANT_MACROS -s -fomit-frame-pointer -I/home/qyot27/win32_build/include    -I. -Iinclude -D_FILE_OFFSET_BITS=64 -DFFMS_USE_FFMPEG_COMPAT  -c -o src/core/audiosource.o src/core/audiosource.cpp
 CXX    src/core/audiosource.o
```
It stops suppressing the actual commands because printf is no longer hidden.  And there's a ton more .depend lines.  It basically swapped the working and non-working parts.

Removing the @ from printf and putting it before the foreach:
```
$ make
gcc -Wall -march=pentium3 -mtune=pentium3 -std=gnu99 -s -fomit-frame-pointer -I/home/qyot27/win32_build/include    -I. -Iinclude -D_FILE_OFFSET_BITS=64 -DFFMS_USE_FFMPEG_COMPAT  -c -o src/core/matroskaparser.o src/core/matroskaparser.c
gcc -Wall -march=pentium3 -mtune=pentium3 -std=gnu99 -s -fomit-frame-pointer -I/home/qyot27/win32_build/include    -I. -Iinclude -D_FILE_OFFSET_BITS=64 -DFFMS_USE_FFMPEG_COMPAT  -c -o src/core/stdiostream.o src/core/stdiostream.c
g++ -Wall -D__STDC_CONSTANT_MACROS -s -fomit-frame-pointer -I/home/qyot27/win32_build/include    -I. -Iinclude -D_FILE_OFFSET_BITS=64 -DFFMS_USE_FFMPEG_COMPAT  -c -o src/core/audiosource.o src/core/audiosource.cpp
```
Ignores the prettyprinting instructions entirely.

---

### Post by qyot27 on 2012-08-04
I figured it out after fiddling with it some more this morning.

The reason for the warnings were the semi-colons.  The printf command contains a semicolon between what it is supposed to output to screen and the real command that gets run.  The step that generates the .depend file uses a semi-colon to end the loop, and moreover, that loop is supposed to iterate for every source file it finds.  Only the first iteration for the dependencies of the .c and .cpp files were getting treated correctly by the printf command, displaying the condensed version on screen.

The rest of the iterations, while still being performed correctly, were getting spammed by the extraneous printf information that was coming immediately before them, leading to sh not knowing what to do with those commands.

This part of it was solved by forcing the .depend loop to insert a new line after every iteration.  This resolved the '/bin/sh: @printf: command not found' warnings, and resulted in both a lot of .depend lines (although unlike the case of removing the @ from @printf, both the .depend lines and the main source code were being displayed concisely).

All those .depend lines were showing up because the commands to generate them contained $(CC) and $(CXX), and since printf was supposed to clean up the output of anything containing those variables, it cleaned up the .depend lines and displayed them even though they were supposed to be silent.

To make them silent again, I just created some dummy variables in configure that made sure that printf wouldn't see them as targets to clean up.  The full changes below:

configure changes (to the step that generates config.mak):
```
PLC=$CC
PLPL=$CXX
```

GNUmakefile:
The printf command is unchanged
```
ifndef V
$(foreach VAR,CC CXX AR RANLIB RC,\
    $(eval override $(VAR) = @printf " %s\t%s\n" $(VAR) "$$@"; $($(VAR))))
endif
```

The .depend step:
```
define \n


endef

.depend: config.mak
	@rm -f .depend
	@$(foreach SRC_C, $(CORE_C), \
            $(PLC) $(CPPFLAGS) $(CFLAGS) $(SRC_C) -MT $(SRC_C:%.c=%.o) -MM -g0 1>> .depend;${\n})
	@$(foreach SRC_CXX, $(CORE_CXX) $(IDX_CXX), \
            $(PLPL) $(CPPFLAGS) $(CXXFLAGS) $(SRC_CXX) -MT $(SRC_CXX:%.cpp=%.o) -MM -g0 1>> .depend;${\n})
```

The end result is that .depend still gets generated (but silently) and the actual .c and .cpp steps have consise output except when a warning occurs.

---

