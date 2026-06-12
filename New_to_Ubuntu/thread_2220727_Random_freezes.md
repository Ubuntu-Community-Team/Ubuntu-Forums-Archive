---
title: "Random freezes"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by petercek on 2014-04-29
My laptop randomly freezes (screen & sound) doing nothing special with it. Only hard reboot helps... (5 seconds power button). I assume it happens more often if listening to music. It freezes often; may happen a couple of times per hour. Other times, I can work several hours with no problems.

It is HP Probook 470 (i5-3230M/8 GB/750 GB/AMD Radeon HD 8750M 2 GB, Ubuntu 14.04 64-bit). I use default Ubuntu's drivers, Unity desktop. I tried with fallback but did not help.

I wonder if anyone sees this, too, or it may be related to my laptop only (so hardware problem)? I checked for BIOS update but there's none on HP's site.

---

### Post by Danger_Monkey on 2014-04-29
Hi, Petercek.  Have you looked in the log files to see if there are any errors right before it freezes?  To do this, after you reboot:

```

cd /var/log
tail -50 syslog
tail -50 syslog.1

```

Hopefully, you will see something that gives som insight into what is happening.  Post the results here, and people can see them and comment.

---

### Post by petercek on 2014-07-19
It's been a while... The problem persists and drives me crazy. Here is the syslog right after reboot:

user@user-HP:/var/log$ tail -50 syslog
Jul 19 22:16:57 user-HP kernel: [   31.500549] <6>[fglrx] Firegl kernel thread PID: 1566
Jul 19 22:16:57 user-HP kernel: [   31.500654] <6>[fglrx] Firegl kernel thread PID: 1567
Jul 19 22:16:57 user-HP kernel: [   31.500712] <6>[fglrx] Firegl kernel thread PID: 1568
Jul 19 22:16:57 user-HP kernel: [   31.500783] <6>[fglrx] IRQ 52 Enabled
Jul 19 22:16:57 user-HP kernel: [   31.510397] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jul 19 22:16:57 user-HP kernel: [   31.510399] <6>[fglrx] Reserved FB block: Unshared offset:f878000, size:4000 
Jul 19 22:16:57 user-HP kernel: [   31.510400] <6>[fglrx] Reserved FB block: Unshared offset:f87c000, size:484000 
Jul 19 22:16:57 user-HP kernel: [   31.510402] <6>[fglrx] Reserved FB block: Unshared offset:7fff4000, size:c000 
Jul 19 22:16:57 user-HP NetworkManager[870]: <info> WiFi hardware radio set enabled
Jul 19 22:17:02 user-HP CRON[1596]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 19 22:17:03 user-HP ntpdate[1421]: no server suitable for synchronization found
Jul 19 22:17:10 user-HP NetworkManager[870]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul 19 22:17:10 user-HP NetworkManager[870]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 19 22:17:10 user-HP NetworkManager[870]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 19 22:17:10 user-HP NetworkManager[870]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul 19 22:17:11 user-HP dbus[687]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jul 19 22:17:11 user-HP dbus[687]: [system] Successfully activated service 'org.freedesktop.UPower'
Jul 19 22:17:11 user-HP wpa_supplicant[1120]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 19 22:17:14 user-HP dbus[687]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 19 22:17:14 user-HP dbus[687]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 19 22:17:14 user-HP anacron[1911]: Anacron 2.3 started on 2014-07-19
Jul 19 22:17:14 user-HP anacron[1911]: Normal exit (0 jobs run)
Jul 19 22:17:15 user-HP colord: Device added: xrandr-Chimei Innolux Corporation
Jul 19 22:17:16 user-HP dbus[687]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jul 19 22:17:16 user-HP dbus[687]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jul 19 22:17:16 user-HP rtkit-daemon[2009]: Successfully called chroot.
Jul 19 22:17:16 user-HP rtkit-daemon[2009]: Successfully dropped privileges.
Jul 19 22:17:16 user-HP rtkit-daemon[2009]: Successfully limited resources.
Jul 19 22:17:16 user-HP rtkit-daemon[2009]: Running.
Jul 19 22:17:16 user-HP rtkit-daemon[2009]: Canary thread running.
Jul 19 22:17:16 user-HP rtkit-daemon[2009]: Watchdog thread running.
Jul 19 22:17:16 user-HP rtkit-daemon[2009]: Successfully made thread 2007 of process 2007 (n/a) owned by '1000' high priority at nice level -11.
Jul 19 22:17:16 user-HP rtkit-daemon[2009]: Supervising 1 threads of 1 processes of 1 users.
Jul 19 22:17:16 user-HP rtkit-daemon[2009]: Successfully made thread 2012 of process 2007 (n/a) owned by '1000' RT at priority 5.
Jul 19 22:17:16 user-HP rtkit-daemon[2009]: Supervising 2 threads of 1 processes of 1 users.
Jul 19 22:17:16 user-HP rtkit-daemon[2009]: Successfully made thread 2013 of process 2007 (n/a) owned by '1000' RT at priority 5.
Jul 19 22:17:16 user-HP rtkit-daemon[2009]: Supervising 3 threads of 1 processes of 1 users.
Jul 19 22:17:16 user-HP bluetoothd[787]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/HFPAG
Jul 19 22:17:16 user-HP bluetoothd[787]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/HFPHS
Jul 19 22:17:16 user-HP bluetoothd[787]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSource
Jul 19 22:17:16 user-HP bluetoothd[787]: Endpoint registered: sender=:1.37 path=/MediaEndpoint/A2DPSink
Jul 19 22:17:17 user-HP dbus[687]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Jul 19 22:17:17 user-HP dbus[687]: [system] Successfully activated service 'org.freedesktop.locale1'
Jul 19 22:17:17 user-HP colord: Profile added: icc-2261abf5a4bedd5d959974d7c6873783
Jul 19 22:17:17 user-HP colord: Automatic metadata add icc-e29dd1ce8fd134711181cb67cd561a73 to xrandr-Chimei Innolux Corporation
Jul 19 22:17:17 user-HP colord: Profile added: icc-e29dd1ce8fd134711181cb67cd561a73
Jul 19 22:17:19 user-HP dbus[687]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Jul 19 22:17:20 user-HP udisksd[2102]: udisks daemon version 2.1.3 starting
Jul 19 22:17:20 user-HP dbus[687]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Jul 19 22:17:20 user-HP udisksd[2102]: Acquired the name org.freedesktop.UDisks2 on the system message bus
user@user-HP:/var/log$ 

I don't see any suspicious message.

I'm really surprised it's only happening to my laptop since I haven't see any other complaints...

---

### Post by sotiris2 on 2014-07-19
I would suggest running a [memory test](https://help.ubuntu.com/community/MemoryTest)

---

