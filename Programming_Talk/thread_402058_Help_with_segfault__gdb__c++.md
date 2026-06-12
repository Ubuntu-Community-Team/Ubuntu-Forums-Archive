---
title: "Help with segfault / gdb / c++"
date: 2007-04-05
forum: Programming Talk
---

### Post by simplyw00x on 2007-04-05
An odd query, I guess. I'm not asking about programming principles, *per se*, more if someone could take a few minutes to look at the source code of my project:
[https://guitarshik.bountysource.com/svn/!source/18/trunk/src/song.cpp#59]("https://guitarshik.bountysource.com/svn/!source/18/trunk/src/song.cpp#59")

and tell me why the program segfaults on line 59 of song.cpp if next_event_time is larger than 0.

Alternatively, if someone could tell me how to coax gdb into showing me more than:
```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1217710384 (LWP 24341)]
0x08059188 in jdkmidi::MIDISequencer::GetNextEvent ()
(gdb) bt
#0  0x08059188 in jdkmidi::MIDISequencer::GetNextEvent ()
#1  0x08051147 in PlayDumpSequencer (main_fretboard=0x860bb20, seq=0x858ec40,
    clock_time=488, last_time=485) at src/song.cpp:59
#2  0x08051377 in song::update (this=0x858b908) at src/song.cpp:859
#3  0x08053e1b in Gshik::main (this=0x8062d84, argc=1, argv=0xbffd22d4)
    at src/main.cpp:174
#4  0xb7eddc36 in main (argc=1, argv=0xbffd22d4) at Unix/clanapp.cpp:47
#5  0xb79f1ebc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#6  0x0804ad81 in _start ()
(gdb)
```

(i.e., **where** in jdkmidi::MIDISequencer::GetNextEvent does the segfault occur?

Sorry about my inability to generalise this into a more readable example, but the complexity of the code is perhaps the reason for the bug.

Regards,

Carl.

---

### Post by EntropicTundra on 2007-04-09
At this point, type 'frame 0'. If you've got full debugging symbols in your code, this should print the line that caused the segfault.

---

