---
title: "Please help! Ubuntu logs me out immediately after login; FRESH install"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by JustSomeGuy on 2008-08-23
I downloaded Ubuntu 8.04 ISO and burned to CD, installed on my XP machine (completely wiped out XP, btw). Booted it up, got to the login screen. Entered UN/PW, it loads the default desktop background (no icons), hangs for a second and then....bam. Right back to the login screen. I can use the failsafe terminal, but the graphics get glitchy and the computer hangs up if I try to login non-graphically (ctrl+alt+f2).

---

### Post by thebigbluecan on 2008-08-23
What kind of video card? Nvidia Ati or onboard intel or via? Do you know?

---

### Post by JustSomeGuy on 2008-08-23
> **thebigbluecan said:**
> What kind of video card? Nvidia Ati or onboard intel or via? Do you know?

Is there a way to check? I haven't bought one so the videocard is whatever came in the computer.

---

### Post by zamadatix on 2008-08-23
happens every time to me even with live cd untill i select options on the login session and select gnome failsafe and then enable my ati restricted driver through system adminstration 3rd party hardware drivers i think. hope that helps

---

### Post by JustSomeGuy on 2008-08-23
> **zamadatix said:**
> happens every time to me even with live cd untill i select options on the login session and select gnome failsafe and then enable my ati restricted driver through system adminstration 3rd party hardware drivers i think. hope that helps

How do I go about doing that?

--nvm I feel stupid for even asking that question

--It worked, btw. Thanks a bunch!

---

### Post by mysticfrost on 2008-11-16
I have a compaq presario v6000 worked fine with 8.04 upgraded to 8.10 and suddenly the system logs me out completely , here is my system log

Nov 16 13:33:49 Rana-laptop syslogd 1.5.0#2ubuntu6: restart.
Nov 16 13:59:01 Rana-laptop -- MARK --
Nov 16 14:19:01 Rana-laptop -- MARK --
Nov 16 14:39:01 Rana-laptop -- MARK --
Nov 16 14:59:01 Rana-laptop -- MARK --
Nov 16 15:19:01 Rana-laptop -- MARK --
Nov 16 15:39:01 Rana-laptop -- MARK --
Nov 16 15:59:01 Rana-laptop -- MARK --
Nov 16 16:07:39 Rana-laptop pulseaudio[19925]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 16 16:07:39 Rana-laptop pulseaudio[19927]: pid.c: Stale PID file, overwriting.
Nov 16 16:07:39 Rana-laptop pulseaudio[19927]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 16 16:07:39 Rana-laptop pulseaudio[19927]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 16 16:07:39 Rana-laptop pulseaudio[19927]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov 16 16:07:39 Rana-laptop pulseaudio[19927]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov 16 16:07:39 Rana-laptop pulseaudio[19927]: alsa-util.c: Cannot find fallback mixer control "Mic".
Nov 16 16:14:35 Rana-laptop pulseaudio[20790]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 16 16:14:35 Rana-laptop pulseaudio[20792]: pid.c: Stale PID file, overwriting.
Nov 16 16:14:35 Rana-laptop pulseaudio[20792]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 16 16:14:35 Rana-laptop pulseaudio[20792]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 16 16:14:35 Rana-laptop pulseaudio[20792]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov 16 16:14:35 Rana-laptop pulseaudio[20792]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov 16 16:14:35 Rana-laptop pulseaudio[20792]: alsa-util.c: Cannot find fallback mixer control "Mic".

---

### Post by Peter09 on 2008-11-16
.

As a First Pass at configuring your Video Driver:
1. Boot into recovery mode and select 'xfix' from the menu, this may resolve it.

If not boot recovery mode again and select the command shell. Try the code

```
startx
```

also post the output of the command

```
lshw -C display
```

---

