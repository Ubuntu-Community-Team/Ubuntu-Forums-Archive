---
title: "Slow Booting on Ubuntu"
date: 2017-12-09
forum: New to Ubuntu
---

### Post by user261 on 2017-12-09
I recently started using Ubuntu os on Dell.
this is my systemd-analyze
```
Startup finished in 7.281s (firmware) + 6.916s (loader) + 7.426s (kernel) + 47.828s (userspace) = 1min 9.452s
```
[HR][/HR]systemd-analyze critical-chain 
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.
```
graphical.target @47.821s
&#9492;&#9472;multi-user.target @47.802s
  &#9492;&#9472;virtualbox.service @47.313s +488ms
    &#9492;&#9472;network-online.target @47.300s
      &#9492;&#9472;NetworkManager-wait-online.service @37.561s +9.738s
        &#9492;&#9472;NetworkManager.service @34.321s +3.231s
          &#9492;&#9472;firewalld.service @25.614s +8.693s
            &#9492;&#9472;dbus.service @20.637s
              &#9492;&#9472;basic.target @20.549s
                &#9492;&#9472;sockets.target @20.549s
                  &#9492;&#9472;snapd.socket @20.323s +225ms
                    &#9492;&#9472;sysinit.target @20.110s
                      &#9492;&#9472;systemd-timesyncd.service @19.649s +460ms
                        &#9492;&#9472;systemd-tmpfiles-setup.service @15.956s +3.294s
                          &#9492;&#9472;local-fs.target @15.955s
                            &#9492;&#9472;boot-efi.mount @15.949s +5ms
                              &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-5C70\x2d6614.service @15.197s +689ms
                                &#9492;&#9472;dev-disk-by\x2duuid-5C70\x2d6614.device @15.186s
```


[HR][/HR]systemd-analyze blame
      ```
   21.786s systemd-rfkill.service
         12.543s dev-sda3.device
          9.738s NetworkManager-wait-online.service
          8.693s firewalld.service
          7.269s ModemManager.service
          7.170s snapd.service
          7.095s grub-common.service
          7.050s accounts-daemon.service
          6.287s apport.service
          6.280s gpu-manager.service
          6.082s networking.service
          5.312s irqbalance.service
          5.244s systemd-logind.service
          5.175s loadcpufreq.service
          5.068s alsa-restore.service
          5.065s thinkfan.service
          5.061s systemd-user-sessions.service
          5.038s ondemand.service
          5.032s speech-dispatcher.service
          5.030s avahi-daemon.service
          5.027s bluetooth.service
          5.026s thermald.service
          4.996s pppd-dns.service
          4.996s rsyslog.service
          3.674s apparmor.service
          3.294s systemd-tmpfiles-setup.service
          3.264s lightdm.service
          3.231s NetworkManager.service
          2.989s ufw.service
          2.077s systemd-tmpfiles-setup-dev.service
          1.524s plymouth-start.service
          1.488s keyboard-setup.service
          1.389s binfmt-support.service
          1.210s systemd-udevd.service
          1.102s console-setup.service
          1.032s systemd-modules-load.service
          1.024s sys-kernel-debug.mount
           896ms [EMAIL="systemd-backlight@backlight:intel_backlight.servic"]systemd-backlight@backlight:intel_backlight.servic[/EMAIL]e
           839ms lvm2.service
           834ms polkitd.service
           820ms systemd-tmpfiles-clean.service
           770ms systemd-journald.service
           761ms dev-mqueue.mount
           760ms dev-hugepages.mount
           689ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-5C70\x2d6614.servic"]systemd-fsck@dev-disk-by\x2duuid-5C70\x2d6614.servic[/EMAIL]e
           641ms cpufrequtils.service
           586ms kmod-static-nodes.service
           549ms upower.service
           518ms colord.service
           508ms systemd-update-utmp.service
           488ms virtualbox.service
           460ms systemd-timesyncd.service
           355ms systemd-sysctl.service
           336ms udisks2.service
           302ms wpa_supplicant.service
           263ms [EMAIL="user@1001.servic"]user@1001.servic[/EMAIL]e
           225ms snapd.socket
           222ms dev-sda4.swap
           200ms dns-clean.service
           181ms proc-sys-fs-binfmt_misc.mount
           156ms systemd-random-seed.service
           136ms systemd-udev-trigger.service
           135ms [EMAIL="systemd-backlight@leds:dell::kbd_backlight.servic"]systemd-backlight@leds:dell::kbd_backlight.servic[/EMAIL]e
           133ms systemd-journal-flush.service
           112ms resolvconf.service
            90ms setvtrgb.service
            81ms systemd-remount-fs.service
            77ms plymouth-read-write.service
            11ms ureadahead-stop.service
             6ms snapd.autoimport.service
             6ms systemd-update-utmp-runlevel.service
             5ms boot-efi.mount
             3ms rtkit-daemon.service
             2ms plymouth-quit-wait.service
             2ms rc-local.service
             1ms sys-fs-fuse-connections.mount
```


any way i can improve the boot time?

---

### Post by VMC on 2017-12-09
Regarding the rfkill , have a look at this solution:
[https://ubuntuforums.org/showthread.php?t=2336978](https://ubuntuforums.org/showthread.php?t=2336978)

---

