---
title: "Xubuntu boots slowly..."
date: 2018-01-01
forum: New to Ubuntu
---

### Post by xipho2 on 2018-01-01
i. e. 2min 40s. It is installed on a SSD. Win10 needs 40s on a HDD. What is the reason and solution? Thanx!
```
xubuntu@xubuntu:~$ systemd-analyze blame
           6.317s NetworkManager-wait-online.service
           4.792s dev-sda5.device
           4.728s dev-sdb1.device
           4.121s console-setup.service
           3.939s dev-loop0.device
           2.201s snapd.autoimport.service
           1.990s ModemManager.service
           1.658s NetworkManager.service
           1.431s accounts-daemon.service
           1.314s networking.service
            981ms grub-common.service
            937ms systemd-logind.service
            932ms thermald.service
            858ms ondemand.service
            823ms speech-dispatcher.service
            822ms apport.service
            753ms lm-sensors.service
            727ms rsyslog.service
            719ms ubiquity.service
            705ms gpu-manager.service
            675ms lightdm.service
            635ms avahi-daemon.service
            577ms upower.service
            563ms lvm2-monitor.service
            548ms irqbalance.service
            496ms systemd-journald.service
            462ms keyboard-setup.service
            387ms systemd-modules-load.service
            341ms systemd-udev-trigger.service
            241ms polkitd.service
            235ms apparmor.service
            222ms systemd-udevd.service
            166ms wpa_supplicant.service
            117ms systemd-tmpfiles-setup-dev.service
             99ms ufw.service
             99ms dev-mqueue.mount
             96ms systemd-remount-fs.service
             86ms systemd-backlight@backlight:intel_backlight.service
             80ms systemd-backlight@backlight:acpi_video0.service
             73ms udisks2.service
             65ms pppd-dns.service
             61ms systemd-user-sessions.service
             58ms kmod-static-nodes.service
             55ms plymouth-start.service
             54ms user@999.service
             54ms sys-kernel-debug.mount
             46ms systemd-journal-flush.service
             45ms resolvconf.service
             44ms systemd-update-utmp-runlevel.service
             39ms hddtemp.service
             34ms systemd-timesyncd.service
             34ms systemd-update-utmp.service
             31ms systemd-sysctl.service
             30ms dev-hugepages.mount
             30ms setvtrgb.service
             28ms plymouth-read-write.service
             25ms systemd-tmpfiles-setup.service
             19ms rc-local.service
 lines 1-58To run a command as administrator (user "root"), use "sudo <command>".
 See "man sudo_root" for details.
 
 
 xubuntu@xubuntu:~$ systemd-analyze time
 Startup finished in 2min 27.178s (kernel) + 10.551s (userspace) = 2min 37.729s
 xubuntu@xubuntu:~$ d
 
 
 
 
 
 
 
 
 
```

---

### Post by Autodave on 2018-01-01
Is Xubuntu on its own disk and is Win10 on its own disk? Did you disable fast boot in the BIOS?

What version of Xubuntu are you running?  What video card are you using and did you install a driver for it? If so, what drtiver and where did you get it from?

---

### Post by HermanAB on 2018-01-01
You could do the same as Windows:  Don't reboot.  Use Suspend.

---

### Post by Autodave on 2018-01-01
Never bothered to check mine before, so I just did. 1 minute 34 seconds. Xubuntu on an SSD, Win10 on separate HD.  But, I have a rather fast machine: 8 core clocked at 3.5, 8 gig RAM.

I have a 1.8 quad core laptop with 6 gig RAM. SSD with Xubuntu on it, no Windows. That machine boots in 18 seconds.

---

### Post by Holger_Gehrke on 2018-01-01
I'm a bit surprised by the output of 'systemd-analyze time' because it's obviously not mentioning two parts of the startup process, the firmware (bios or whatever) and the loader (grub, I'd say). On my system - a Lenovo Ideapad 110 with AMD E2, running XUbuntu 17.04 from a HDD with UEFI - the same command gives:
```
Startup finished in 5.900s (firmware) + 5.113s (loader) + 6.665s (kernel) + 26.448s (userspace) = 44.127s
```
and I've never done anything to optimize it for fast booting. I'd take a close look at the output of dmesg to see what the kernel is doing in those 2 and a half minutes; it's probably waiting for something. Or systemd-analyze can't separate time used by firmware, loader and kernel on your system and gives a total for these three stages, in which case I'd take a look at the bios settings; perhaps it's doing some extensive power on self test.

Holger

---

### Post by Yellow Pasque on 2018-01-01
> Or systemd-analyze can't separate time used by firmware, loader and kernel

I don't think it works that way on legacy BIOS. [https://penguinprowess.wordpress.com/2017/07/22/systemd-analyze-blame-aint-nobody-for-boot-wait/](https://penguinprowess.wordpress.com/2017/07/22/systemd-analyze-blame-aint-nobody-for-boot-wait/)

> perhaps it's doing some extensive power on self test.

That would probably affect Windows too.

---

### Post by VMC on 2018-01-01
What's critical-chain report:
```
$ systemd-analyze critical-chainThe time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.


graphical.target @11.288s
&#9492;&#9472;multi-user.target @11.288s
  &#9492;&#9472;getty.target @11.288s
    &#9492;&#9472;getty@tty1.service @11.288s
      &#9492;&#9472;system-getty.slice @11.287s
        &#9492;&#9472;setvtrgb.service @11.227s +59ms
          &#9492;&#9472;systemd-user-sessions.service @10.343s +7ms
            &#9492;&#9472;network.target @10.341s
              &#9492;&#9472;NetworkManager.service @8.941s +1.400s
                &#9492;&#9472;dbus.service @8.798s
                  &#9492;&#9472;basic.target @8.790s
                    &#9492;&#9472;sockets.target @8.790s
                      &#9492;&#9472;snapd.socket @8.778s +12ms
                        &#9492;&#9472;sysinit.target @8.777s
                          &#9492;&#9472;swap.target @8.777s
                            &#9492;&#9472;dev-disk-by\x2duuid-f7bea333\x2d69e6\x2d4cc2\x2db591\x2df921d269ac64.swap @8.765s +11ms
                              &#9492;&#9472;dev-disk-by\x2duuid-f7bea333\x2d69e6\x2d4cc2\x2db591\x2df921d269ac64.device @8.764s
```

Maybe your disk or swap is taking too long.

---

### Post by xipho2 on 2018-01-11
X is on a SSD, Win10 on a HDD. fast boot seems not existing in the BIOS. That machine is ~10 years old. Lenovo T400. No drivers installed. Win10 was just for a check, it came with the machine, but I did not remember the boot time and I assumed it was slow and that was wrong.

---

### Post by Yellow Pasque on 2018-01-11
Please give output of the command that was asked of you:
```
systemd-analyze critical-chain
```

---

### Post by xipho2 on 2018-01-14
```
systemd-analyzecritical-chain
The time after theunit is active or started is printed after the "@"character.
The time the unittakes to start is printed after the "+" character.


graphical.target@11.221s
&#9492;&#9472;multi-user.target@11.219s
  &#9492;&#9472;getty.target@11.217s
   &#9492;&#9472;getty@tty1.service @11.210s
     &#9492;&#9472;rc-local.service @11.090s +17ms
       &#9492;&#9472;network-online.target @11.087s
         &#9492;&#9472;NetworkManager-wait-online.service @3.623s +7.463s
           &#9492;&#9472;NetworkManager.service @3.325s +288ms
             &#9492;&#9472;dbus.service @3.245s
               &#9492;&#9472;basic.target @3.183s
                 &#9492;&#9472;sockets.target @3.183s
                   &#9492;&#9472;snapd.socket @3.170s +11ms
                     &#9492;&#9472;sysinit.target @3.165s
                       &#9492;&#9472;apparmor.service @2.898s +264ms
                         &#9492;&#9472;local-fs.target @2.884s
                           &#9492;&#9472;run-user-1000-gvfs.mount @6.314s
                             &#9492;&#9472;run-user-1000.mount @5.138s
                               &#9492;&#9472;local-fs-pre.target @484ms
                                 &#9492;&#9472;keyboard-setup.service @151ms +309ms
                                   &#9492;&#9472;systemd-journald.socket @150ms
lines 1-23
 
```

---

