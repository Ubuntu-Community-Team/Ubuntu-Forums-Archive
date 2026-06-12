---
title: "Ubuntu 18.04 LTS boot problems"
date: 2019-09-06
forum: New to Ubuntu
---

### Post by vanio2 on 2019-09-06
Hi guys,

I am kinda new to Ubuntu and currently experiencing super slow boot times. On top of that, when I hibernate my laptop and it tries to restart the system just crashes. I started reading how I can fix that and so far I have:

1. Reduced the duration of the kept logs to only 5 days which reduced the size of the files and helped speed up a little bit. - sudo journalctl --vacuum-time=5d
2. I think my swap partition is messed up - the fstab file looks like below (the partition does **not** show in GParted)

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=cfc177a0-e961-4d5d-bb0f-ad84ff4280d6 /boot           ext2    defaults        0       2
/dev/disk/by-uuid/66684ddb-4542-4823-aabe-b7d06ebfb14b none swap sw,noauto 0 0
```

The output of **systemd-analyze blame**
         ```
40.204s dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
         28.065s systemd-sysctl.service
         25.601s snap-gnome\x2dcharacters-317.mount
         24.251s snap-gtk\x2dcommon\x2dthemes-1313.mount
         24.233s snap-core-7396.mount
         24.229s snap-core-7270.mount
         24.229s snap-spotify-35.mount
         24.207s snap-gnome\x2dlogs-45.mount
         24.183s snap-gnome\x2dlogs-61.mount
         24.182s snap-gnome\x2dcharacters-296.mount
         24.159s snap-gnome\x2dcalculator-260.mount
         24.158s snap-gnome\x2dcalculator-406.mount
         11.755s plymouth-quit-wait.service
         10.502s NetworkManager-wait-online.service
          9.015s snapd.service
          7.107s gpu-manager.service
          7.057s [EMAIL="lvm2-pvscan@8:5.servic"]lvm2-pvscan@8:5.servic[/EMAIL]e
          6.299s dev-loop22.device
          6.219s udisks2.service
          5.988s ModemManager.service
          5.692s dev-loop24.device
          5.684s networking.service
          5.641s NetworkManager.service
          5.611s dev-loop25.device
          5.485s dev-loop21.device
          5.484s dev-loop15.device
          5.484s dev-loop12.device
          5.257s dev-loop27.device
          4.858s fwupd.service
          4.626s dev-loop6.device
          4.622s speech-dispatcher.service
          4.462s systemd-tmpfiles-setup-dev.service
          4.416s dev-loop26.device
          4.251s dev-loop20.device
          4.173s dev-loop23.device
          4.056s dev-loop16.device
          4.051s networkd-dispatcher.service
          3.926s systemd-modules-load.service
          3.830s dev-loop19.device
          3.821s wpa_supplicant.service
          3.818s pppd-dns.service
          3.813s bluetooth.service
          3.792s rsyslog.service
          3.708s dev-loop1.device
          3.572s dev-loop10.device
          3.498s dev-loop18.device
          3.497s dev-loop17.device
          3.137s rc-local.service
          3.077s dev-loop4.device
          3.051s thermald.service
          3.035s dev-loop14.device
          3.033s dev-loop13.device
          3.031s dev-loop7.device
          2.762s dev-loop11.device
          2.759s dev-loop8.device
          2.624s dev-loop9.device
          2.593s dev-loop5.device
          2.487s dev-loop2.device
          2.459s dev-loop3.device
          2.401s accounts-daemon.service
          2.354s preload.service
          2.217s dev-loop0.device
          2.111s apparmor.service
          1.900s grub-common.service
          1.848s nmbd.service
          1.528s avahi-daemon.service
          1.395s smbd.service
          1.115s systemd-udevd.service
          1.039s systemd-logind.service
           956ms systemd-resolved.service
           911ms apport.service
           787ms systemd-udev-trigger.service
           766ms resolvconf.service
           750ms packagekit.service
           722ms polkit.service
           713ms systemd-tmpfiles-setup.service
           696ms systemd-journald.service
           688ms plymouth-read-write.service
           622ms snap-gnome\x2d3\x2d28\x2d1804-71.mount
           606ms snap-canonical\x2dlivepatch-77.mount
           536ms snap-firefox-258.mount
           535ms snap-gnome\x2dcalculator-352.mount
           529ms snap-pycharm\x2dprofessional-147.mount
           525ms snap-gnome\x2d3\x2d26\x2d1604-90.mount
           525ms snap-gnome\x2d3\x2d28\x2d1804-67.mount
           524ms snap-gnome\x2dlogs-57.mount
           513ms snap-gnome\x2dsystem\x2dmonitor-100.mount
           497ms snap-firefox-253.mount
           496ms snap-gnome\x2dsystem\x2dmonitor-95.mount
           491ms systemd-timesyncd.service
           488ms snap-spotify-36.mount
           487ms snap-gnome\x2d3\x2d26\x2d1604-92.mount
           487ms snap-core18-1098.mount
           486ms snap-gtk\x2dcommon\x2dthemes-1198.mount
           478ms systemd-random-seed.service
           440ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-cfc177a0\x2de961\x2d4d5d\x2dbb0f\x2dad84ff4280d6.servic"]systemd-fsck@dev-disk-by\x2duuid-cfc177a0\x2de961\x2d4d5d\x2dbb0f\x2dad84ff4280d6.servic[/EMAIL]e
           346ms blk-availability.service
           345ms [EMAIL="user@125.servic"]user@125.servic[/EMAIL]e
           257ms tlp.service
           251ms gdm.service
           236ms systemd-update-utmp.service
           233ms snap-pycharm\x2dprofessional-151.mount
           225ms systemd-remount-fs.service
           222ms bolt.service
           201ms [EMAIL="systemd-backlight@backlight:intel_backlight.servic"]systemd-backlight@backlight:intel_backlight.servic[/EMAIL]e
           175ms plymouth-start.service
           172ms boot.mount
           165ms apport-autoreport.service
           149ms upower.service
           130ms snapd.socket
           126ms ufw.service
           120ms console-setup.service
           108ms dev-mqueue.mount
           107ms dev-hugepages.mount
           105ms colord.service
           102ms snapd.seeded.service
            92ms kmod-static-nodes.service
            68ms sys-kernel-debug.mount
            66ms snap-canonical\x2dlivepatch-81.mount
            54ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
            46ms setvtrgb.service
            31ms snap-core18-1074.mount
            27ms systemd-tmpfiles-clean.service
            13ms smartmontools.service
            12ms alsa-restore.service
            11ms resolvconf-pull-resolved.service
             9ms ureadahead-stop.service
             8ms kerneloops.service
             4ms dns-clean.service
             4ms systemd-update-utmp-runlevel.service
             3ms rtkit-daemon.service
             2ms systemd-user-sessions.service
             1ms sys-kernel-config.mount
             1ms sys-fs-fuse-connections.mount
```

And the **critical-chain **looks like that 
```
graphical.target @1min 19.943s
&#9492;&#9472;multi-user.target @1min 19.942s
  &#9492;&#9472;smbd.service @1min 6.897s +1.395s
    &#9492;&#9472;nmbd.service @1min 5.047s +1.848s
      &#9492;&#9472;network-online.target @1min 5.046s
        &#9492;&#9472;NetworkManager-wait-online.service @54.543s +10.502s
          &#9492;&#9472;NetworkManager.service @48.900s +5.641s
            &#9492;&#9472;dbus.service @48.698s
              &#9492;&#9472;basic.target @48.696s
                &#9492;&#9472;sockets.target @48.696s
                  &#9492;&#9472;snapd.socket @48.566s +130ms
                    &#9492;&#9472;sysinit.target @48.565s
                      &#9492;&#9472;apparmor.service @46.453s +2.111s
                        &#9492;&#9472;local-fs.target @46.450s
                          &#9492;&#9472;run-user-125.mount @1min 9.498s
```


Any help would be appreciated! Thanks

---

### Post by CatKiller on 2019-09-06
> **vanio2 said:**
> 2. I think my swap partition is messed up - the fstab file looks like below (the partition does **not** show in GParted)

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=cfc177a0-e961-4d5d-bb0f-ad84ff4280d6 /boot           ext2    defaults        0       2
/dev/disk/by-uuid/66684ddb-4542-4823-aabe-b7d06ebfb14b none swap sw,noauto 0 0
```



I don't think it's just your swap partition that's messed up: that fstab is hideous. You appear to be using LVM, which people that aren't me know about. Do you actually *have* a /boot partition? For BIOS installs it would be non-standard, and for UEFI installs it would be the ESP listed there instead: /boot/efi. The default in an Ubuntu install is to not have a swap partition at all: a swap file performs just as well and is more flexible. Were one to be using a swap partition and LVM, the swap partition would be part of the LVM volume group. Your partition setup is... odd. The syntax of that line in your fstab is peculiar, too: you only need to specify the UUID of the partition, not the device file representation. Something like 
```
UUID=66684ddb-4542-4823-aabe-b7d06ebfb14b none swap sw 0 0
``` would be fine.

For your startup time, a lot of people have reported good improvements from removing the snaps. I've certainly not missed them at all.

---

### Post by vanio2 on 2019-09-07
So removed snaps as suggested and there is a slight speed up but not huge. Also, changed the last line of the fstab file to have the form of "UUID=......"

Additionally, that is what my partitions look like - 


```
NAME                  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                     8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1                  8:1    0   487M  0 part /boot
&#9500;&#9472;sda2                  8:2    0     1K  0 part 
&#9492;&#9472;sda5                  8:5    0   931G  0 part 
  &#9500;&#9472;ubuntu--vg-root   253:0    0 923.3G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1 253:1    0   7.7G  0 lvm  
sr0                    11:0    1  1024M  0 rom  

```

Updated output from [B]systemd-analyze


[/B]```

         32.113s dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
         24.581s systemd-tmpfiles-setup-dev.service
         11.419s NetworkManager-wait-online.service
          9.520s systemd-sysctl.service
          9.429s gpu-manager.service
          8.255s ModemManager.service
          5.830s udisks2.service
          5.190s accounts-daemon.service
          4.928s rsyslog.service
          4.815s thermald.service
          4.814s preload.service
          4.793s grub-common.service
          4.784s networkd-dispatcher.service
          4.757s NetworkManager.service
          4.359s wpa_supplicant.service
          4.237s systemd-udev-trigger.service
          4.078s networking.service
          3.555s systemd-journald.service
          3.396s ufw.service
          3.126s systemd-random-seed.service
          3.058s rc-local.service
          2.086s lvm2-pvscan@8:5.service
          1.546s avahi-daemon.service
          1.392s nmbd.service
          1.386s apport.service
          1.355s boot.mount
          1.296s apport-autoreport.service
          1.295s speech-dispatcher.service
          1.167s sys-kernel-debug.mount
          1.167s sys-kernel-debug.mount
          1.161s kmod-static-nodes.service
          1.099s systemd-modules-load.service
          1.093s dev-hugepages.mount
          1.087s blk-availability.service
          1.000s apparmor.service
           943ms systemd-udevd.service
           841ms dev-mqueue.mount
           756ms bluetooth.service
           745ms systemd-logind.service
           725ms smartmontools.service
           716ms alsa-restore.service
           710ms pppd-dns.service
           653ms systemd-remount-fs.service
           513ms systemd-fsck@dev-disk-by\x2duuid-cfc177a0\x2de961\x2d4d5d\x2dbb0f\x2dad84ff4280d6.service
           499ms systemd-tmpfiles-setup.service
           420ms systemd-resolved.service
           317ms systemd-timesyncd.service
           316ms packagekit.service
           288ms smbd.service
           265ms polkit.service
           241ms systemd-localed.service
           217ms user@125.service
           203ms upower.service
           197ms systemd-update-utmp.service
           173ms sys-kernel-config.mount
           172ms tlp.service
           163ms bolt.service
           156ms console-setup.service
           144ms sys-fs-fuse-connections.mount
           139ms gdm.service
           139ms systemd-hostnamed.service
           136ms resolvconf.service
           135ms systemd-timedated.service
           130ms systemd-backlight@backlight:intel_backlight.service
           120ms plymouth-read-write.service
            98ms colord.service
            73ms user@1000.service
            49ms setvtrgb.service
             8ms kerneloops.service
             5ms dns-clean.service
             5ms resolvconf-pull-resolved.service
             4ms systemd-update-utmp-runlevel.service
             2ms rtkit-daemon.service
             2ms systemd-user-sessions.service
             1ms plymouth-quit-wait.service

```

```

graphical.target @1min 722ms
&#9492;&#9472;gdm.service @1min 581ms +139ms
  &#9492;&#9472;rc-local.service @57.520s +3.058s
    &#9492;&#9472;network-online.target @57.516s
      &#9492;&#9472;NetworkManager-wait-online.service @46.096s +11.419s
        &#9492;&#9472;NetworkManager.service @41.337s +4.757s
          &#9492;&#9472;dbus.service @40.637s
            &#9492;&#9472;basic.target @40.527s
              &#9492;&#9472;paths.target @40.526s
                &#9492;&#9472;apport-autoreport.path @40.524s
                  &#9492;&#9472;sysinit.target @40.402s
                    &#9492;&#9472;apparmor.service @39.401s +1.000s
                      &#9492;&#9472;local-fs.target @39.397s
                        &#9492;&#9472;boot.mount @37.996s +1.355s
                          &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-cfc177a0\x2de961\x2d4d5d\x2dbb0f\x2dad84ff4280d6.service @37.422s +513ms
                            &#9492;&#9472;dev-disk-by\x2duuid-cfc177a0\x2de961\x2d4d5d\x2dbb0f\x2dad84ff4280d6.device @37.395s

```


Any other suggestions?

---

