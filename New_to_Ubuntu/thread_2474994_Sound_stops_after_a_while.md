---
title: "Sound stops after a while"
date: 2022-05-13
forum: New to Ubuntu
---

### Post by george1792 on 2022-05-13
Hello, 

I am in unhappy position because my Lenovo thinkpad T510 , stops sound after a while from speakers, when using headphones it works correctly. I have searched and apply some of the online ubuntu solutions but nothing works. I run Ubuntu20.04.4LTS / Kernel 5.13.0-41-genneric. Let me know if u need some more info.

Thank you

---

### Post by george1792 on 2022-05-23
I would appreciate if anyone could help me .

---

### Post by Frogs Hair on 2022-05-23
How are you connecting the speakers , via a dock for the laptop , the headphone output or are they built in?

---

### Post by george1792 on 2022-05-24
I use the laptops built in speakers, when I plug in the headphones is working properly with no stops.

---

### Post by ActionParsnip on 2022-05-24
When it stops, run:
```

dmesg | tail

```
What is the output please?

---

### Post by george1792 on 2022-05-24
[ 5584.764501] audit: type=1400 audit(1653396084.170:108): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/run/mount/utab" pid=10172 comm="pool-soffice" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 6108.900802] audit: type=1400 audit(1653396608.312:109): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/usr/share/zoneinfo-icu/44/le/zoneinfo64.res" pid=10601 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 6108.901055] audit: type=1400 audit(1653396608.312:110): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/usr/share/zoneinfo-icu/44/le/timezoneTypes.res" pid=10601 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 6174.917888] audit: type=1400 audit(1653396674.332:111): apparmor="ALLOWED" operation="connect" profile="libreoffice-oopslash" name="/tmp/OSL_PIPE_1000_SingleOfficeIPC_4eba97b6d3e73097df13e9997e574945" pid=10673 comm="oosplash" requested_mask="wr" denied_mask="wr" fsuid=1000 ouid=1000
[ 6174.917908] audit: type=1400 audit(1653396674.332:112): apparmor="ALLOWED" operation="file_perm" profile="libreoffice-oopslash" name="/tmp/OSL_PIPE_1000_SingleOfficeIPC_4eba97b6d3e73097df13e9997e574945" pid=10673 comm="oosplash" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
[ 6174.917923] audit: type=1400 audit(1653396674.332:113): apparmor="ALLOWED" operation="file_perm" profile="libreoffice-oopslash" name="/tmp/OSL_PIPE_1000_SingleOfficeIPC_4eba97b6d3e73097df13e9997e574945" pid=10673 comm="oosplash" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
[ 6174.917938] audit: type=1400 audit(1653396674.332:114): apparmor="ALLOWED" operation="file_perm" profile="libreoffice-oopslash" name="/tmp/OSL_PIPE_1000_SingleOfficeIPC_4eba97b6d3e73097df13e9997e574945" pid=10673 comm="oosplash" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
[ 6174.917953] audit: type=1400 audit(1653396674.332:115): apparmor="ALLOWED" operation="file_perm" profile="libreoffice-oopslash" name="/tmp/OSL_PIPE_1000_SingleOfficeIPC_4eba97b6d3e73097df13e9997e574945" pid=10673 comm="oosplash" requested_mask="w" denied_mask="w" fsuid=1000 ouid=1000
[ 6178.419839] audit: type=1400 audit(1653396677.832:116): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/proc/10601/mountinfo" pid=10601 comm="pool-soffice" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
[ 6178.423591] audit: type=1400 audit(1653396677.836:117): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/run/mount/utab" pid=10601 comm="pool-soffice" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

---

### Post by george1792 on 2022-05-25
> **ActionParsnip said:**
> When it stops, run:
```

dmesg | tail

```
What is the output please?

[ 9628.003212] wlp3s0: authenticate with 84:16:f9:8d:07:05
[ 9628.005328] wlp3s0: send auth to 84:16:f9:8d:07:05 (try 1/3)
[ 9628.007576] wlp3s0: authenticated
[ 9628.011109] wlp3s0: associate with 84:16:f9:8d:07:05 (try 1/3)
[ 9628.015506] wlp3s0: RX AssocResp from 84:16:f9:8d:07:05 (capab=0x431 status=0 aid=6)
[ 9628.026713] wlp3s0: associated
[ 9629.071592] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 9651.513127] audit: type=1400 audit(1653461987.776:125): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/gdm/greeter/applications/gnome-initial-setup.desktop" pid=2554 comm="pool-org.gnome." requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 9651.565545] audit: type=1400 audit(1653461987.828:126): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/var/lib/snapd/hostfs/usr/share/gdm/greeter/applications/gnome-initial-setup.desktop" pid=2554 comm="pool-org.gnome." requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 9652.420186] audit: type=1326 audit(1653461988.684:127): auid=1000 uid=1000 gid=1000 ses=3 subj=snap.snap-store.ubuntu-software pid=2554 comm="pool-org.gnome." exe="/snap/snap-store/558/usr/bin/snap-store" sig=0 arch=c000003e syscall=93 compat=0 ip=0x7f711b86c3cb code=0x50000

---

### Post by george1792 on 2022-05-31
Kindly reminder

---

### Post by iamjiwjr on 2022-05-31
I"m having similar sound issues. I'm not a sophistated terminal-wizard so I can't offer those kind of solution possibilities. As for me, I'm trying the below suggestion that I read yesterday in Distrowatch (see last line of quote) to see if this applies. I'll let you know if it helps. Maybe it might help you.

[COLOR=#000000][FONT=Arial]"Some people running the new 22.04 version of [/FONT][/COLOR][Ubuntu]("https://distrowatch.com/ubuntu")[COLOR=#000000][FONT=Arial] have reported a problem with the way the distribution now handles low memory situations. In the past, Ubuntu (like most Linux distributions) would allow processes to consume as much memory as they wanted. This would sometimes result in applications gobbling up memory and then swap space, resulting in more disk access and poor performance. Ubuntu now employs the systemd out of memory (OOM) [/FONT][/COLOR][service]("https://www.freedesktop.org/software/systemd/man/systemd-oomd.html")[COLOR=#000000][FONT=Arial] which will kill processes when memory gets close to full. [/FONT][/COLOR][Some]("https://askubuntu.com/questions/1404888/how-do-i-disable-the-systemd-oom-process-killer-in-ubuntu-22-04")[people]("https://old.reddit.com/r/Ubuntu/comments/uyl4i6/ubuntu_2204s_new_oom_killing_system_is_killing/")[COLOR=#000000][FONT=Arial] are feeling the side effects of this change, specifically finding applications (and their related processes) are suddenly terminating without warning. "[/FONT][/COLOR][COLOR=#990000][FONT=Arial]Ubuntu 22.04 comes with the systemd-oomd service enabled by default, which has been 'helpfully' killing my IDE and/or terminals whenever I try to compile an application using an abundance of threads/memory. What is the right way to either turn this off, or configure the service to not shoot random processes in the face while I'm using them?[/FONT][/COLOR][COLOR=#000000][FONT=Arial]" The new behaviour can be turned off using the command "sudo systemctl disable --now systemd-oomd" and a [/FONT][/COLOR][bug]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1972159")[COLOR=#000000][FONT=Arial] has been filed for this issue."[/FONT][/COLOR]

---

### Post by TheFu on 2022-05-31
With pulse audio, sometimes the program crashes.  Restarting it often make it work again.  PulseAudio is brought to us by the same people behind SystemD, FYI.

The commands to restart it are
```
/usr/bin/pulseaudio -k
/usr/bin/pulseaudio -D
```

I've made many assumptions which may not be true in the situation on your system.

---

### Post by george1792 on 2022-07-02
It didn't work. Probably because I am working on Ubuntu 20.04 . 

> **iamjiwjr said:**
> I"m having similar sound issues. I'm not a sophistated terminal-wizard so I can't offer those kind of solution possibilities. As for me, I'm trying the below suggestion that I read yesterday in Distrowatch (see last line of quote) to see if this applies. I'll let you know if it helps. Maybe it might help you.

[COLOR=#000000][FONT=Arial]"Some people running the new 22.04 version of [/FONT][/COLOR][Ubuntu]("https://distrowatch.com/ubuntu")[COLOR=#000000][FONT=Arial] have reported a problem with the way the distribution now handles low memory situations. In the past, Ubuntu (like most Linux distributions) would allow processes to consume as much memory as they wanted. This would sometimes result in applications gobbling up memory and then swap space, resulting in more disk access and poor performance. Ubuntu now employs the systemd out of memory (OOM) [/FONT][/COLOR][service]("https://www.freedesktop.org/software/systemd/man/systemd-oomd.html")[COLOR=#000000][FONT=Arial] which will kill processes when memory gets close to full. [/FONT][/COLOR][Some]("https://askubuntu.com/questions/1404888/how-do-i-disable-the-systemd-oom-process-killer-in-ubuntu-22-04")[people]("https://old.reddit.com/r/Ubuntu/comments/uyl4i6/ubuntu_2204s_new_oom_killing_system_is_killing/")[COLOR=#000000][FONT=Arial] are feeling the side effects of this change, specifically finding applications (and their related processes) are suddenly terminating without warning. "[/FONT][/COLOR][COLOR=#990000][FONT=Arial]Ubuntu 22.04 comes with the systemd-oomd service enabled by default, which has been 'helpfully' killing my IDE and/or terminals whenever I try to compile an application using an abundance of threads/memory. What is the right way to either turn this off, or configure the service to not shoot random processes in the face while I'm using them?[/FONT][/COLOR][COLOR=#000000][FONT=Arial]" The new behaviour can be turned off using the command "sudo systemctl disable --now systemd-oomd" and a [/FONT][/COLOR][bug]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1972159")[COLOR=#000000][FONT=Arial] has been filed for this issue."[/FONT][/COLOR]

---

