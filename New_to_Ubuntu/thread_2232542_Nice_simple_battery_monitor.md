---
title: "Nice simple battery monitor"
date: 2014-07-02
forum: New to Ubuntu
---

### Post by vajorie on 2014-07-02
Not a question but,

I was trying to get dwm up and running and ended up finding this gorgeous battery monitor app / indicator thing that I now just adore and wanted to let others know. 

This command makes it run after you install it

```

/usr/bin/xbattbar -a -c top -i green -I black &

```

and it places a very thin bar on top of your screen that goes from green to red as the battery is depleted. It's non-obtrusive and stays there whatever other application you may be using (e.g. you don't have to worry about your laptop dying while watching a movie fullscreen or browsing the web in full screen, or forgetting that you had unplugged your power, etc).

Edit: Had posted the wrong command.... More coffee needed...

---

### Post by Al1000 on 2014-07-03
That sounds great.

Do you know if it runs any background processes when the charger is plugged in?

---

### Post by vajorie on 2014-07-03
(Edited first post since I had posted the wrong command lol)

Yea, it's running in the background whether charging or not but takes very little resources. You can change the "-I black" to the color of your status bar on top of your screen, in which case you won't see that it is running and showing stuff while charged. That's especially nice because your eyes don't get used to seeing it all the time and it draws a little of your attention when discharging. (I always forget that the laptop is not plugged in.)

Here's the detailed view of the resources it takes while running (taking up 216Kb of memory and no active cpu usage): 

```

$ ps aux | grep xbattbar
user    6613  0.0  0.0  15968  1156 ?        S    12:34   0:00 /usr/bin/xbattbar -a -c top -i green -I black &

$ top -b -n 1 -p 6613
top - 12:52:17 up 18 min,  2 users,  load average: 0.03, 0.10, 0.13
Tasks:   1 total,   0 running,   1 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.3%us,  1.3%sy,  0.2%ni, 93.8%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   5971636k total,  2698676k used,  3272960k free,   150540k buffers
Swap:  7105532k total,        0k used,  7105532k free,  1349244k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                      
 6613 user    20   0 15968 1156  940 S    0  0.0   0:00.02 xbattbar

$ cat /proc/6613/status
Name:	xbattbar
State:	S (sleeping)
Tgid:	6613
Pid:	6613
PPid:	6495
TracerPid:	0
Uid:	1000	1000	1000	1000
Gid:	1000	1000	1000	1000
FDSize:	64
Groups:	4 24 30 46 109 124 1000 
VmPeak:	   15968 kB
VmSize:	   15968 kB
VmLck:	       0 kB
VmPin:	       0 kB
VmHWM:	    1156 kB
VmRSS:	    1156 kB
VmData:	     192 kB
VmStk:	     136 kB
VmExe:	      16 kB
VmLib:	    3252 kB
VmPTE:	      56 kB
VmSwap:	       0 kB
Threads:	1
SigQ:	0/46465
SigPnd:	0000000000000000
ShdPnd:	0000000000000000
SigBlk:	0000000000000000
SigIgn:	0000000000000000
SigCgt:	0000000000002000
CapInh:	0000000000000000
CapPrm:	0000000000000000
CapEff:	0000000000000000
CapBnd:	ffffffffffffffff
Cpus_allowed:	f
Cpus_allowed_list:	0-3
Mems_allowed:	00000000,00000001
Mems_allowed_list:	0
voluntary_ctxt_switches:	178
nonvoluntary_ctxt_switches:	16

$ pmap -x 6613
6613:   /usr/bin/xbattbar -a -c top -i green -I black &
Address           Kbytes     RSS   Dirty Mode   Mapping
0000000000400000       0      16       0 r-x--  xbattbar
0000000000603000       0       4       4 r----  xbattbar
0000000000604000       0       4       4 rw---  xbattbar
0000000000fba000       0      60      60 rw---    [ anon ]
00007fc523978000       0      12       0 r-x--  libXdmcp.so.6.0.0
00007fc52397d000       0       0       0 -----  libXdmcp.so.6.0.0
00007fc523b7c000       0       4       4 r----  libXdmcp.so.6.0.0
00007fc523b7d000       0       4       4 rw---  libXdmcp.so.6.0.0
00007fc523b7e000       0       8       0 r-x--  libXau.so.6.0.0
00007fc523b80000       0       0       0 -----  libXau.so.6.0.0
00007fc523d7f000       0       4       4 r----  libXau.so.6.0.0
00007fc523d80000       0       4       4 rw---  libXau.so.6.0.0
00007fc523d81000       0       8       0 r-x--  libdl-2.15.so
00007fc523d83000       0       0       0 -----  libdl-2.15.so
00007fc523f83000       0       4       4 r----  libdl-2.15.so
00007fc523f84000       0       4       4 rw---  libdl-2.15.so
00007fc523f85000       0      60       0 r-x--  libxcb.so.1.1.0
00007fc523fa2000       0       0       0 -----  libxcb.so.1.1.0
00007fc5241a1000       0       4       4 r----  libxcb.so.1.1.0
00007fc5241a2000       0       4       4 rw---  libxcb.so.1.1.0
00007fc5241a3000       0     480       0 r-x--  libc-2.15.so
00007fc524358000       0       0       0 -----  libc-2.15.so
00007fc524558000       0      16      16 r----  libc-2.15.so
00007fc52455c000       0       8       8 rw---  libc-2.15.so
00007fc52455e000       0      12      12 rw---    [ anon ]
00007fc524563000       0     244       0 r-x--  libX11.so.6.3.0
00007fc524693000       0       0       0 -----  libX11.so.6.3.0
00007fc524893000       0       4       4 r----  libX11.so.6.3.0
00007fc524894000       0      16      16 rw---  libX11.so.6.3.0
00007fc524898000       0     108       0 r-x--  ld-2.15.so
00007fc524a92000       0      20      20 rw---    [ anon ]
00007fc524ab7000       0      12      12 rw---    [ anon ]
00007fc524aba000       0       4       4 r----  ld-2.15.so
00007fc524abb000       0       8       8 rw---  ld-2.15.so
00007fffff765000       0      16      16 rw---    [ stack ]
00007fffff7ff000       0       4       0 r-x--    [ anon ]
ffffffffff600000       0       0       0 r-x--    [ anon ]
----------------  ------  ------  ------
total kB           15968    1156     216

```

---

