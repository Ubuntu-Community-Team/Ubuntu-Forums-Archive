---
title: "Dell XPS 9315 upgraded from 20.04 to 22.04"
date: 2022-11-27
forum: New to Ubuntu
---

### Post by gadgetwho on 2022-11-27
Everything seems to be working except for the the occasional freeze, I did have get rid of the Dell Support Assistant Linux (could not find repositories to update?) but my concern are the errors in the Log file & that 22.04 seems to be a little slower than 20.04 was over all. 

[IMG]https://postimg.cc/yWZzRtHG[/IMG]
[B]
IMPORTANT[/B]

```
13:27:24 gdm-session-wor: GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
13:27:19 systemd: Failed to start Application launched by gnome-session-binary.
13:27:19 systemd: Failed to start Application launched by gnome-session-binary.
13:27:03 systemd: Failed to start Service for snap application snapd-desktop-integration.snapd-desktop-integration.
13:27:02 canonical-livep: Task "refresh" returned an error: livepatch check failed: POST request to "https://livepatch.canonical.com/v1/client/ac0e8a94e1483a515e60642963680c85/updates" failed, retrying in 30s.
13:27:02 kernel: ACPI Error: Aborting method \_SB.IETM._OSC due to previous error (AE_NOT_FOUND) (20210604/psparse-529)
13:27:02 thermald: Unsupported conditions are present
13:27:01 gnome-session-b: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
13:27:01 (sistantd): dell-linux-assistant.service: Failed at step EXEC spawning /usr/bin/dell-linux-assistantd: No such file or directory
13:27:01 systemd: Failed to start casper-md5check Verify Live ISO checksums.
13:27:01 kernel: dell_smm_hwmon: unable to get SMM Dell signature
13:26:51 kernel: int3472-discrete INT3472:01: INT3472 seems to have no dependents.
13:26:51 kernel: pci 0000:00:07.1: DPC: RP PIO log size 0 is invalid

[B]
```
ALL[/B]

```
14:06:33 NetworkManager: <warn>  [1669586793.4033] platform-linux: do-add-ip6-address[2: fe80::7887:920e:24e5:6c56]: failure 13 (Permission denied)
14:04:40 rtkit-daemon: Supervising 10 threads of 4 processes of 1 users.
14:04:31 NetworkManager: <warn>  [1669586671.3631] ipv6ll[04ad0a65bb5d7473,ifindex=2]: changed: no IPv6 link local address to retry after Duplicate Address Detection failures (back off)
14:02:39 kernel: audit: type=1326 audit(1669586559.659:220): auid=1001 uid=1001 gid=1001 ses=3 subj=snap.brave.brave pid=10945 comm="brave" exe="/snap/brave/189/opt/brave.com/brave/brave" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fa6890574e7 code=0x50000
14:02:39 brave: SECCOMP auid=1001 uid=1001 gid=1001 ses=3 subj=snap.brave.brave pid=10945 comm="brave" exe="/snap/brave/189/opt/brave.com/brave/brave" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fa6890574e7 code=0x50000
14:02:39 NetworkManager: <warn>  [1669586559.3289] platform-linux: do-add-ip6-address[2: fe80::4416:e622:40fc:919f]: failure 13 (Permission denied)
14:01:53 systemd: systemd-hostnamed.service: Deactivated successfully.
14:01:53 NetworkManager: <warn>  [1669586513.3155] platform-linux: do-add-ip6-address[2: fe80::751b:4979:5623:98f1]: failure 13 (Permission denied)
14:01:45 dbus-daemon: [session uid=1001 pid=3266] Successfully activated service 'org.gnome.gedit'
14:01:45 NetworkManager: <warn>  [1669586505.3124] platform-linux: do-add-ip6-address[2: fe80::39ea:cac7:af67:1a64]: failure 13 (Permission denied)
14:01:32 systemd: Started Tracker metadata extractor.
14:01:32 dbus-daemon: [session uid=1001 pid=3266] Successfully activated service 'org.freedesktop.Tracker3.Miner.Extract'
14:01:32 systemd: Starting Tracker metadata extractor...
14:01:32 dbus-daemon: [session uid=1001 pid=3266] Activating via systemd: service name='org.freedesktop.Tracker3.Miner.Extract' unit='tracker-extract-3.service' requested by ':1.7' (uid=1001 pid=3323 comm="/usr/libexec/tracker-miner-fs-3 " label="unconfined")
14:01:31 NetworkManager: <warn>  [1669586491.3067] platform-linux: do-add-ip6-address[2: fe80::751b:4979:5623:98f1]: failure 13 (Permission denied)
14:01:23 systemd: Started Hostname Service.
14:01:23 dbus-daemon: [system] Successfully activated service 'org.freedesktop.hostname1'
14:01:23 systemd: Starting Hostname Service...
14:01:23 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.185' (uid=1001 pid=7140 comm="/usr/bin/gnome-logs --gapplication-service " label="unconfined")
14:01:23 NetworkManager: <warn>  [1669586483.3029] platform-linux: do-add-ip6-address[2: fe80::39ea:cac7:af67:1a64]: failure 13 (Permission denied)
13:58:43 rtkit-daemon: Supervising 10 threads of 4 processes of 1 users.
13:58:39 NetworkManager: <warn>  [1669586319.2545] ipv6ll[04ad0a65bb5d7473,ifindex=2]: changed: no IPv6 link local address to retry after Duplicate Address Detection failures (back off)
13:58:38 rtkit-daemon: Supervising 10 threads of 4 processes of 1 users.
13:58:37 NetworkManager: <warn>  [1669586317.2540] platform-linux: do-add-ip6-address[2: fe80::4416:e622:40fc:919f]: failure 13 (Permission denied)
13:58:33 rtkit-daemon: Supervising 10 threads of 4 processes of 1 users.
13:58:31 NetworkManager: <warn>  [1669586311.2514] platform-linux: do-add-ip6-address[2: fe80::b18b:903e:e9ce:3d58]: failure 13 (Permission denied)
13:58:28 rtkit-daemon: Supervising 10 threads of 4 processes of 1 users.
13:58:27 NetworkManager: <warn>  [1669586307.2504] platform-linux: do-add-ip6-address[2: fe80::39ea:cac7:af67:1a64]: failure 13 (Permission denied)
13:56:19 rtkit-daemon: Supervising 10 threads of 4 processes of 1 users.
13:56:19 NetworkManager: <warn>  [1669586179.2117] platform-linux: do-add-ip6-address[2: fe80::b18b:903e:e9ce:3d58]: failure 13 (Permission denied)
13:55:41 rtkit-daemon: Supervising 10 threads of 4 processes of 1 users.
13:55:41 NetworkManager: <warn>  [1669586141.2017] platform-linux: do-add-ip6-address[2: fe80::4416:e622:40fc:919f]: failure 13 (Permission denied)
13:55:15 kernel: audit: type=1326 audit(1669586115.657:219): auid=1001 uid=1001 gid=1001 ses=3 subj=snap.brave.brave pid=10424 comm="brave" exe="/snap/brave/189/opt/brave.com/brave/brave" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fa6890574e7 code=0x50000
13:55:15 brave: SECCOMP auid=1001 uid=1001 gid=1001 ses=3 subj=snap.brave.brave pid=10424 comm="brave" exe="/snap/brave/189/opt/brave.com/brave/brave" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fa6890574e7 code=0x50000
13:55:15 NetworkManager: <warn>  [1669586115.1926] platform-linux: do-add-ip6-address[2: fe80::2c4d:8f6a:4660:d5cf]: failure 13 (Permission denied)
13:55:12 kernel: audit: type=1326 audit(1669586112.993:218): auid=1001 uid=1001 gid=1001 ses=3 subj=snap.brave.brave pid=10411 comm="brave" exe="/snap/brave/189/opt/brave.com/brave/brave" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fa6890574e7 code=0x50000
13:55:12 brave: SECCOMP auid=1001 uid=1001 gid=1001 ses=3 subj=snap.brave.brave pid=10411 comm="brave" exe="/snap/brave/189/opt/brave.com/brave/brave" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fa6890574e7 code=0x50000
13:55:11 NetworkManager: <warn>  [1669586111.1911] platform-linux: do-add-ip6-address[2: fe80::7887:920e:24e5:6c56]: failure 13 (Permission denied)
13:55:09 kernel: audit: type=1326 audit(1669586109.976:217): auid=1001 uid=1001 gid=1001 ses=3 subj=snap.brave.brave pid=10396 comm="brave" exe="/snap/brave/189/opt/brave.com/brave/brave" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fa6890574e7 code=0x50000
13:55:09 brave: SECCOMP auid=1001 uid=1001 gid=1001 ses=3 subj=snap.brave.brave pid=10396 comm="brave" exe="/snap/brave/189/opt/brave.com/brave/brave" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fa6890574e7 code=0x50000
13:55:09 NetworkManager: <warn>  [1669586109.1903] platform-linux: do-add-ip6-address[2: fe80::39ea:cac7:af67:1a64]: failure 13 (Permission denied)
13:55:00 kernel: audit: type=1326 audit(1669586100.216:216): auid=1001 uid=1001 gid=1001 ses=3 subj=snap.brave.brave pid=10369 comm="brave" exe="/snap/brave/189/opt/brave.com/brave/brave" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fa6890574e7 code=0x50000
13:55:00 brave: SECCOMP auid=1001 uid=1001 gid=1001 ses=3 subj=snap.brave.brave pid=10369 comm="brave" exe="/snap/brave/189/opt/brave.com/brave/brave" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fa6890574e7 code=0x50000
13:54:59 NetworkManager: <warn>  [1669586099.1893] ipv6ll[04ad0a65bb5d7473,ifindex=2]: changed: no IPv6 link local address to retry after Duplicate Address Detection failures (back off)
13:52:00 systemd: systemd-hostnamed.service: Deactivated successfully.
13:51:59 NetworkManager: <warn>  [1669585919.1189] platform-linux: do-add-ip6-address[2: fe80::751b:4979:5623:98f1]: failure 13 (Permission denied)
13:51:48 kernel: audit: type=1326 audit(1669585908.782:215): auid=1001 uid=1001 gid=1001 ses=3 subj=snap.brave.brave pid=10220 comm="brave" exe="/snap/brave/189/opt/brave.com/brave/brave" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fa6890574e7 code=0x50000
13:51:48 brave: SECCOMP auid=1001 uid=1001 gid=1001 ses=3 subj=snap.brave.brave pid=10220 comm="brave" exe="/snap/brave/189/opt/brave.com/brave/brave" sig=0 arch=c000003e syscall=330 compat=0 ip=0x7fa6890574e7 code=0x50000
13:51:41 NetworkManager: <warn>  [1669585901.1122] ipv6ll[04ad0a65bb5d7473,ifindex=2]: changed: no IPv6 link local address to retry after Duplicate Address Detection failures (back off)
13:51:30 systemd: Started Hostname Service.
13:51:30 dbus-daemon: [system] Successfully activated service 'org.freedesktop.hostname1'
```

---

### Post by gadgetwho on 2022-11-27
Forgot to mention that the Dell XPS 13 9315 is only certificated for Ubuntu 20.04 which seems to have issues with my corporate VPN, I have to use 24.04 for VPN to work properly.

---

### Post by noutram on 2023-05-16
I too have tried to upgrade. Most things seems to work (I installed the MIPI camera support using the instructions on the Ubuntu Wiki, and removed support assistant as well). However, I notice power drains more quickly than expected when I close the lid and put it into sleep mode. Do you find the same?

---

