---
title: "Slow boot on Ubuntu 18.01 LTS"
date: 2018-05-20
forum: New to Ubuntu
---

### Post by priyankkjain on 2018-05-20
[COLOR=#111111][FONT=Ubuntu][FONT=inherit][COLOR=#6A737C][FONT=inherit][COLOR=#111111][FONT=inherit]I am new to Ubuntu just installed it today, Ubuntu is taking to much time to boot like 2 minutes I found some command 
named "systemd-an[/FONT][/COLOR][COLOR=#111111][FONT=inherit]alyze blame" so I got output like this,

[/FONT][/COLOR][/FONT][/COLOR][/FONT]
[/FONT][/COLOR]

```

     15.267s dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
     13.088s plymouth-quit-wait.service
     11.207s NetworkManager-wait-online.service
     10.302s systemd-journal-flush.service
      8.938s lvm2-monitor.service
      7.964s plymouth-start.service
      7.528s systemd-tmpfiles-setup-dev.service
      5.744s udisks2.service
      5.737s networking.service
      5.388s dev-loop2.device
      5.369s dev-loop0.device
      5.330s dev-loop1.device
      5.275s dev-loop3.device
      5.241s dev-loop5.device
      5.217s dev-loop7.device
      5.196s dev-loop6.device
      5.159s dev-loop4.device
      4.708s ModemManager.service
      4.421s NetworkManager.service
      4.011s accounts-daemon.service
      3.527s apport.service
      3.331s wpa_supplicant.service
      2.957s thermald.service
      2.807s grub-common.service
      2.426s avahi-daemon.service
      2.418s gpu-manager.service
      2.103s systemd-logind.service
      1.903s rsyslog.service
      1.875s iio-sensor-proxy.service
      1.809s polkit.service
      1.690s keyboard-setup.service
      1.662s systemd-rfkill.service
      1.661s networkd-dispatcher.service
      1.639s systemd-sysctl.service
      1.556s pppd-dns.service
      1.541s packagekit.service
      1.466s apparmor.service
      1.399s systemd-modules-load.service
      1.111s fwupd.service
      1.053s [EMAIL="systemd-backlight@backlight:intel_backlight.servic"]systemd-backlight@backlight:intel_backlight.servic[/EMAIL]e
      1.029s kmod-static-nodes.service
       805ms dev-mqueue.mount
       797ms systemd-remount-fs.service
       778ms bluetooth.service
       752ms sys-kernel-debug.mount
       748ms dev-hugepages.mount
       652ms ufw.service
       648ms [EMAIL="lvm2-pvscan@8:2.servic"]lvm2-pvscan@8:2.servic[/EMAIL]e
       556ms dns-clean.service
       526ms systemd-journald.service
       508ms [EMAIL="user@120.servic"]user@120.servic[/EMAIL]e
       474ms systemd-timesyncd.service
       465ms systemd-resolved.service
       447ms systemd-random-seed.service
       444ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-6365\x2d58F6.servic"]systemd-fsck@dev-disk-by\x2duuid-6365\x2d58F6.servic[/EMAIL]e
       391ms blk-availability.service
       363ms kerneloops.service
       356ms snap-gnome\x2d3\x2d26\x2d1604-59.mount
       352ms systemd-tmpfiles-setup.service
       319ms snap-gnome\x2dlogs-25.mount
       315ms speech-dispatcher.service
       299ms snap-core-4486.mount
       294ms gdm.service
       281ms snap-gnome\x2dsystem\x2dmonitor-36.mount
       250ms upower.service
       248ms snap-gnome\x2dcharacters-69.mount
       224ms snap-gnome\x2dcalculator-154.mount
       220ms dev-mapper-ubuntu\x2d\x2dvg\x2dswap_1.swap
       210ms systemd-udevd.service
       199ms snap-canonical\x2dlivepatch-39.mount
       190ms plymouth-read-write.service
       179ms snap-intellij\x2didea\x2dultimate-44.mount
       173ms snapd.seeded.service
       171ms console-setup.service
       157ms systemd-update-utmp.service
       155ms systemd-tmpfiles-clean.service
       145ms systemd-user-sessions.service
       141ms boot-efi.mount
       116ms bolt.service
       116ms setvtrgb.service
       115ms colord.service
        59ms snapd.service
        53ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
        50ms systemd-udev-trigger.service
        43ms dev-loop11.device
        43ms alsa-restore.service
        40ms snap-gnome\x2dsystem\x2dmonitor-39.mount
        39ms dev-loop9.device
        34ms snap-gnome\x2dcharacters-86.mount
        32ms dev-loop10.device
        32ms snap-gnome\x2dcalculator-167.mount
        32ms snap-gnome\x2dlogs-31.mount
        30ms dev-loop8.device
        29ms dev-loop12.device
        26ms snapd.socket
        26ms rtkit-daemon.service
        24ms snap-core-4571.mount
         8ms systemd-update-utmp-runlevel.service
         6ms ureadahead-stop.service
         2ms sys-fs-fuse-connections.mount
         1ms sys-kernel-config.mount
```
[COLOR=#111111][FONT=Ubuntu][FONT=inherit]Now I don't know what to do from here. also, I have not selected encryption option during installation but I selected an option called LVM for partition. So any guide would be useful.[/FONT]
Also my laptop is HP-au620tx with 8gb RAM and 1TB HDD
[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2018-05-20
Seems that  LLVM maybe the culprit, did you encrypt your drive?

Also a bunch of dev-loops those are snaps.

---

### Post by priyankkjain on 2018-05-20
No I didn't encrypted my hard drive. Also what is dev-loops and snap ?

---

