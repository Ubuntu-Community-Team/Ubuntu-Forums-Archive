---
title: "Ubuntu 18.04 | pulseaudio Daemon startup failed"
date: 2019-02-01
forum: New to Ubuntu
---

### Post by theyellowpolarbear on 2019-02-01
Upon restarting pulseaudio in the terminal by using ```
pulseaudio -k 
```and then ```
pulseaudio --start 
```I receive the following output.

  
```
E: [pulseaudio] main.c: Daemon startup failed.
```

  
When typing ```
pulseaudio -vvv
``` I receive the following output.

  
```
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 11.1
D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fdebug-prefix-map=/build/pulseaudio-EOwPuF/pulseaudio-11.1=. -fstack-protector-strong -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -fno-common -fdiagnostics-show-option -fdiagnostics-color=auto
D: [pulseaudio] main.c: Running on host: Linux x86_64 4.15.0-43-generic #46-Ubuntu SMP Thu Dec 6 14:45:28 UTC 2018
D: [pulseaudio] main.c: Found 8 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimized build: yes
D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I: [pulseaudio] main.c: Machine ID is f8def17f479a479fb03bc39dc2d9b6fb.
I: [pulseaudio] main.c: Session ID is 1.
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/samuel/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-11.1/modules.
I: [pulseaudio] main.c: Running in system mode: no
I: [pulseaudio] main.c: System supports high resolution timers
D: [pulseaudio] memblock.c: Using shared memfd memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472
I: [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 SSE4_2 
I: [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions.
I: [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers.
I: [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions.
I: [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers.
I: [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions.
I: [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions.
E: [pulseaudio] main.c: Unknown command: You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.# General Public License for more details.
E: [pulseaudio] main.c: Failed to initialise daemon.
I: [pulseaudio] main.c: Daemon terminated.
```

  
Is there a way where I can get pulseaudio to start back up again?

---

