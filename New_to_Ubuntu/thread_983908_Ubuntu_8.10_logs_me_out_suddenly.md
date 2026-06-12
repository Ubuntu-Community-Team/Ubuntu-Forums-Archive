---
title: "Ubuntu 8.10 logs me out suddenly"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by mysticfrost on 2008-11-16
Hello upgraded to ubuntu 8.10 recently the system logs me out suddenly for no reason my log is as follows:

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
Nov 16 16:37:13 Rana-laptop kernel: [11926.960000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 4
Nov 16 16:37:13 Rana-laptop kernel: [11926.964000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Nov 16 16:37:13 Rana-laptop kernel: [11926.972000] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.
Nov 16 16:37:13 Rana-laptop kernel: [11927.148000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Nov 16 16:37:13 Rana-laptop kernel: [11927.148000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Nov 16 16:37:13 Rana-laptop kernel: [11927.152000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Nov 16 16:37:13 Rana-laptop kernel: [11927.152000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Nov 16 16:37:13 Rana-laptop kernel: [11927.156000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
Nov 16 16:37:13 Rana-laptop kernel: [11927.156000] psmouse.c: issuing reconnect request
Nov 16 16:37:16 Rana-laptop kernel: [11929.408000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
Nov 16 16:37:16 Rana-laptop kernel: [11929.472000] input: SynPS/2 Synaptics TouchPad as /class/input/input8

Can anyone help please!

---

### Post by nikgare on 2008-11-16
Maybe it's X crashing, have a look in /var/log/Xorg.0.log
(or older Xorg log files there)

---

