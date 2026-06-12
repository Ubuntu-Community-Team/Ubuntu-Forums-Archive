---
title: "Banshee GLib Assertion Error"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by danjl1100 on 2012-07-25
Hello all,

   When running Banshee 2.4.1 on Ubuntu 12.04, it intermittently crashes after finishing a song. After 5 to 15 minutes of playing music, it suddenly crashes, with no warning. The Banshee log (~/.config/banshee-1/log) provides the following:

> exec -a banshee mono  /usr/lib/banshee/Banshee.exe    --redirect-log --play-enqueued

[Info  22:10:46.596] Running Banshee 2.4.1: [Ubuntu 12.04 LTS (linux-gnu, x86_64) @ 2012-07-17 02:26:43 UTC]
[Info  22:10:48.701] Updating web proxy from GConf
[Info  22:10:48.821] All services are started 1.189753
[Info  22:10:51.830] AmazonMP3 store redirect URL: [https://one.ubuntu.com/music/store/amz/](https://one.ubuntu.com/music/store/amz/)

(Banshee:11943): GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed

My first thought was a problem with some sort of metadata on the next song to be played. When searching for the cause of the problem, I came across a few dead-end mailing lists mentioning the same assertion fail message in Tomboy. This gives me the idea that it's not specific to music playing, but rather to some common components among both Banshee and Tomboy.

Any thoughts as to what is causing the issue, what the assertion "tag < 0" could actually mean, or how I can resolve this issue?

Thanks in advance

---

### Post by stlsaint on 2012-07-26
Try figuring out where the crash happens with a debugger like gdb.
[https://wiki.ubuntu.com/Backtrace](https://wiki.ubuntu.com/Backtrace)

---

