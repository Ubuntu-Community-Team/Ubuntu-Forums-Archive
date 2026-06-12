---
title: "Slow boot time after ubuntu 17.10 fresh install"
date: 2017-11-02
forum: New to Ubuntu
---

### Post by turalmalik on 2017-11-02
I have very slow boot time after installing 17.10. 
Here is result of this command.
```
systemd-analyze blame
         23.729s plymouth-quit-wait.service
         11.666s dev-sda1.device
          9.560s grub-common.service
          7.987s apport.service
          7.821s apparmor.service
          7.456s speech-dispatcher.service
          7.081s NetworkManager-wait-online.service
          6.216s NetworkManager.service
          6.090s snapd.service
          5.858s ModemManager.service
          4.853s dns-clean.service
          4.724s accounts-daemon.service
          4.656s udisks2.service
          3.841s rsyslog.service
          3.657s systemd-tmpfiles-setup.service
          3.569s plymouth-start.service
          3.188s nmbd.service
          2.788s thermald.service
          2.588s packagekit.service
          2.308s avahi-daemon.service
          2.114s systemd-backlight@backlight:acpi_video0.service
          2.055s fwupd.service
          1.972s networking.service
          1.915s gpu-manager.service
          1.690s smbd.service
          1.245s polkit.service
          1.224s systemd-random-seed.service
          1.116s plymouth-read-write.service
          1.060s keyboard-setup.service
          1.047s colord.service
           962ms dev-mqueue.mount
           962ms sys-kernel-debug.mount
           961ms dev-hugepages.mount
           904ms gdm.service
           901ms systemd-backlight@backlight:nv_backlight.service
           856ms systemd-modules-load.service
           787ms systemd-rfkill.service
           764ms systemd-tmpfiles-setup-dev.service
           539ms kerneloops.service
           507ms systemd-resolved.service
           498ms systemd-logind.service
           491ms alsa-restore.service
           486ms pppd-dns.service
           450ms systemd-update-utmp.service
           415ms wpa_supplicant.service
           412ms swapfile.swap
           408ms systemd-journal-flush.service
           378ms systemd-udevd.service
           378ms systemd-user-sessions.service
           367ms kmod-static-nodes.service
           353ms upower.service
           281ms console-setup.service
           264ms systemd-journald.service
           260ms user@1000.service
           226ms systemd-udev-trigger.service
           168ms ufw.service
           129ms systemd-timesyncd.service
           120ms systemd-sysctl.service
           103ms setvtrgb.service
            67ms systemd-remount-fs.service
            30ms rtkit-daemon.service
             9ms snapd.socket
             8ms systemd-update-utmp-runlevel.service
             2ms sys-kernel-config.mount
             2ms sys-fs-fuse-connections.mount
```

---

### Post by VMC on 2017-11-02
What are your system specs. cpu,ram,hd, computer model, etc.

---

