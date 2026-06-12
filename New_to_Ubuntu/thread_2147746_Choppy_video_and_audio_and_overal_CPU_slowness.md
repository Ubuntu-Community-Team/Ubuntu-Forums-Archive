---
title: "Choppy video and audio and overal CPU slowness"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by Pieman15 on 2013-05-22
I've fairly new to ubuntu and I'm looking for assistance in troubleshooting some issues I'm experiencing within the past  two weeks. Online videos are now very choppy and impossible to watch. I'm not sure if this is Flash or Java related, perhaps something else. Also, simultaneous to the choppy video issue, my laptop began running very slowly. I'm experiencing a lot lag, for instance, the mouse skips across the screen, there's a several second delay when typing, and programs and files take a long time to open.

Granted this laptop is a little old, but the issues I'm experiencingoccured abruptly, so I'm thinking there might be a fix. I have restarted a few times to no avail.

Thank you in advance for your assistance.
```
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux Pieman 3.2.0-41-generic-pae #66-Ubuntu SMP Thu Apr 25 03:50:20 UTC 2013 i686 i686 i386 GNU/Linux

```

```
cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T5470  @ 1.60GHz
stepping    : 13
microcode    : 0xa3
cpu MHz        : 800.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida dtherm
bogomips    : 3192.11
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T5470  @ 1.60GHz
stepping    : 13
microcode    : 0xa3
cpu MHz        : 800.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida dtherm
bogomips    : 3192.54
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```

```
cat /proc/meminfo 
MemTotal:        2059904 kB
MemFree:          121296 kB
Buffers:          298104 kB
Cached:           529648 kB
SwapCached:         2516 kB
Active:           956456 kB
Inactive:         638540 kB
Active(anon):     519264 kB
Inactive(anon):   249908 kB
Active(file):     437192 kB
Inactive(file):   388632 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       1182140 kB
HighFree:          54856 kB
LowTotal:         877764 kB
LowFree:           66440 kB
SwapTotal:       2093052 kB
SwapFree:        2060056 kB
Dirty:              1460 kB
Writeback:             0 kB
AnonPages:        764976 kB
Mapped:           146720 kB
Shmem:              1828 kB
Slab:             283284 kB
SReclaimable:     263608 kB
SUnreclaim:        19676 kB
KernelStack:        3616 kB
PageTables:        10416 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3123004 kB
Committed_AS:    3481312 kB
VmallocTotal:     122880 kB
VmallocUsed:       60724 kB
VmallocChunk:      57612 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      198648 kB
DirectMap2M:      714752 kB

```

My dmesg is full of these, not sure if that's normal, but there are hundreds of similar lines.
```
dmesg
[195601.394357] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:26:97:80:17:00:22:fb:bf:cc:bc:08:00 SRC=192.168.1.103 DST=192.168.1.100 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=29118 PROTO=UDP SPT=52703 DPT=161 LEN=86 
[195601.394504] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:26:97:80:17:00:22:fb:bf:cc:bc:08:00 SRC=192.168.1.103 DST=192.168.1.100 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=29119 PROTO=UDP SPT=52703 DPT=161 LEN=86 
[195611.547665] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:26:97:80:17:00:22:fb:bf:cc:bc:08:00 SRC=192.168.1.103 DST=192.168.1.100 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=29130 PROTO=UDP SPT=52703 DPT=161 LEN=86 
[195661.323360] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:26:97:80:17:00:22:fb:bf:cc:bc:08:00 SRC=192.168.1.103 DST=192.168.1.100 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=29163 PROTO=UDP SPT=52703 DPT=161 LEN=86 
[195661.323911] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:26:97:80:17:00:22:fb:bf:cc:bc:08:00 SRC=192.168.1.103 DST=192.168.1.100 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=29164 PROTO=UDP SPT=52703 DPT=161 LEN=86 
[195671.643266] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1c:26:97:80:17:00:22:fb:bf:cc:bc:08:00 SRC=192.168.1.103 DST=192.168.1.100 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=29178 PROTO=UDP SPT=52703 DPT=161 LEN=86 

```

---

### Post by 2F4U on 2013-05-23
The messages in dmesg are coming from a firewall (UFW) and seem to indicate that incoming pakets are blocked. What would be interesting is the CPU utilization. Your memory utilization seems to be ok to me. Choppy video, in particular over may also indicate a weak or instable network connection. Are you connecting wired or wireless? If your connection is wireless, have tried if the connection is better when the machine is connected wired?

---

### Post by gordintoronto on 2013-05-23
Online videos from what site, viewed in what browser? Do you shre your internet connection with other computers? Java has nothing to do with viewing videos.

Your computer is quite slow, and if it's running hot, that might make things worse. Have you cleaned the insides recently?

---

### Post by Pieman15 on 2013-05-23
Thanks for the responses.

The video issue is effecting all videos. I experience choppy videos online, in both firefox and chrome, and while wired and wireless. It also occurs when watching DVDs played through VLC. Maybe my video card and/or entire PC is beginning to bite it...

Regarding the cleaning question, no, I've actually never cleaned this thing. It's a laptop that I think I started using in 2006 or 7.

---

### Post by Mark Phelps on 2013-05-24
Do you know the make and model video chipset you're using? If not, open a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA".  That will show the make and model video chipset in use.  Post that information back here.

---

### Post by Pieman15 on 2013-05-26
Here you go:
```
$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GS] (rev a1)
```

---

### Post by Pieman15 on 2013-06-02
Bump

---

### Post by gordintoronto on 2013-06-02
Install lm-sensors. Run sensors-detect, and if it suggests adding something, say yes. (No is the default.) After rebooting, run sensors to see how hot things are. Then get out the vacuum cleaner.

I would also have a look at whatever your router will tell you about activity there. If one of your neighbours is watching Netflix via your router, that's going to affect you.

---

### Post by Pieman15 on 2013-06-03
Thank you gordintoronto. lm-sensors added the following to /etc/modules :
# Chip drivers
coretemp

Just restarted and this seemed to work. Awesome! Thanks again.

Just to mention, there's definitely no one else using my wifi as confirmed by router logs and I have pretty good wifi security. Also, my choppy video and audio issue occured both for online and local videos (like DVDs and downloaded videos).

---

### Post by gordintoronto on 2013-06-03
How hot is your CPU? Do you get a reading from your video card?

Choppy playback on local videos, when it wasn't a problem previously, smacks of clogged up airflow.

---

