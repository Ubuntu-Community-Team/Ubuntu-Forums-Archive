---
title: "Screen goes blank. Unable to wakeup. (acpi INT3400:00: Unsupported event [0x86])"
date: 2018-07-23
forum: New to Ubuntu
---

### Post by tony0072 on 2018-07-23
Product Name: HP OMEN 17-an002no
Operating System: Linux

I installed Ubuntu 18.04 with defaults and rebooted. Started but real slow. I found this repeated message:

```

kernel: [1208.743927] acpi INT3400:00: Unsupported event [0x86]
kernel: [1209.812435] acpi INT3400:00: Unsupported event [0x86]
kernel: [1210.869855] acpi INT3400:00: Unsupported event [0x86]
kernel: [1211.939354] acpi INT3400:00: Unsupported event [0x86]
kernel: [1212.994329] acpi INT3400:00: Unsupported event [0x86]
```
 
If I'm away for a longer time and the screen goes blank I can't wake it up. The only way is to press&hold the power button down and then powering up again.
 
I also tried installing Ubuntu 16.04 but it doesn't work any better.

What did I do wrong? Response on HP Forum was "HP does not support this". Hopefully someone here knows a fix. I really don't want to use Windows10 too much.

---

### Post by mIk3_08 on 2018-07-24
you can turn it to never; 
"turn screen off when inactive for:" never

its usually under the setting -> Brightness & Lock

---

### Post by tony0072 on 2018-07-24
I found Settings -> Power -> Power Saving -> Blank Screen. Changing that to "never" solves the "Screen goes blank"-part.

However the system still alerts about "acpi INT3400:00: Unsupported event [0x86]" and runs really slow.

---

### Post by mIk3_08 on 2018-07-24
Try this commands and paste the result here in thread;
```
systemd-analyze
```

```
systemd-analyze blame
```
```
systemctl list-unit-files –type=service
```
```
systemctl --failed
```

---

### Post by tony0072 on 2018-07-24
```
tony@omenhp:~$ systemd-analyze
Startup finished in 15.644s (firmware) + 8.355s (loader) + 24.376s (kernel) + 31.035s (userspace) = 1min 19.411s
graphical.target reached after 30.938s in userspace
tony@omenhp:~$ 



```

```

tony@omenhp:~$ systemd-analyze blame
         13.169s plymouth-quit-wait.service
         10.555s dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
          9.276s lvm2-monitor.service
          6.665s systemd-udevd.service
          4.562s NetworkManager-wait-online.service
          4.180s snapd.service
          3.548s NetworkManager.service
          3.502s systemd-journal-flush.service
          3.257s networkd-dispatcher.service
          2.667s udisks2.service
          2.083s wpa_supplicant.service
          1.975s networking.service
          1.892s rsyslog.service
          1.694s thermald.service
          1.623s ModemManager.service
          1.613s accounts-daemon.service
          1.580s fwupd.service
          1.543s grub-common.service
          1.396s packagekit.service
          1.285s apport.service
          1.283s dev-loop1.device
          1.270s bolt.service
          1.237s avahi-daemon.service
          1.111s systemd-tmpfiles-setup-dev.service
          1.110s systemd-modules-load.service
          1.099s dev-loop0.device
          1.094s iio-sensor-proxy.service
          1.085s dev-loop4.device
          1.073s keyboard-setup.service
          1.047s dev-loop3.device
          1.036s dev-loop2.device
          1.016s systemd-resolved.service
           964ms dev-loop5.device
           692ms systemd-remount-fs.service
           649ms gpu-manager.service
           645ms dev-mqueue.mount
           644ms sys-kernel-debug.mount
           638ms speech-dispatcher.service
           635ms bluetooth.service
           634ms systemd-logind.service
           632ms pppd-dns.service
           630ms alsa-restore.service
           603ms dev-hugepages.mount
           541ms apparmor.service
           455ms systemd-sysctl.service
           357ms lvm2-pvscan@253:0.service
           339ms gdm.service
           335ms dns-clean.service
           335ms user@120.service
           279ms systemd-journald.service
           265ms systemd-tmpfiles-setup.service
           256ms colord.service
           256ms user@1000.service
           233ms dev-mapper-ubuntu\x2d\x2dvg\x2dswap_1.swap
           229ms systemd-timesyncd.service
           224ms ufw.service
           222ms kmod-static-nodes.service
           216ms snap-gnome\x2d3\x2d26\x2d1604-59.mount
           198ms snap-core-4486.mount
           188ms systemd-random-seed.service
           181ms systemd-fsck@dev-disk-by\x2duuid-B844\x2dAD7E.service
           170ms upower.service
           162ms polkit.service
           141ms snap-gnome\x2dcalculator-154.mount
           140ms systemd-update-utmp.service
           131ms systemd-fsck@dev-disk-by\x2duuid-b0447581\x2df4e5\x2d4fce\x2d89
           103ms blk-availability.service
            92ms motd-news.service
            87ms setvtrgb.service
            79ms systemd-tmpfiles-clean.service
            73ms systemd-rfkill.service
            72ms snap-gnome\x2dsystem\x2dmonitor-36.mount
            64ms plymouth-read-write.service
            55ms systemd-udev-trigger.service
            38ms snap-gnome\x2dcharacters-69.mount
            22ms snap-gnome\x2dlogs-25.mount
            20ms kerneloops.service
            15ms boot.mount
            12ms plymouth-start.service
             7ms rtkit-daemon.service
             5ms systemd-cryptsetup@sda3_crypt.service
             5ms systemd-update-utmp-runlevel.service
             4ms boot-efi.mount
             3ms ureadahead-stop.service
             3ms systemd-user-sessions.service
             2ms console-setup.service
             2ms sys-fs-fuse-connections.mount
             1ms sys-kernel-config.mount
           987us snapd.socket
tony@omenhp:~$ 


```

```

tony@omenhp:~$ systemctl list-unit-files --type=service
UNIT FILE                                  STATE          
accounts-daemon.service                    enabled        
acpid.service                              disabled       
alsa-restore.service                       static         
alsa-state.service                         static         
alsa-utils.service                         masked         
anacron.service                            enabled        
apparmor.service                           enabled        
apport-forward@.service                    static         
apport.service                             generated      
apt-daily-upgrade.service                  static         
apt-daily.service                          static         
autovt@.service                            enabled        
avahi-daemon.service                       enabled        
blk-availability.service                   enabled        
bluetooth.service                          enabled        
bolt.service                               static         
bootlogd.service                           masked         
bootlogs.service                           masked         
bootmisc.service                           masked         
brltty-udev.service                        static         
brltty.service                             disabled       
checkfs.service                            masked         
checkroot-bootclean.service                masked         
checkroot.service                          masked         
clean-mount-point@.service                 static         
colord.service                             static         
configure-printer@.service                 static         
console-getty.service                      disabled       
console-setup.service                      enabled        
container-getty@.service                   static         
cron.service                               enabled        
cryptdisks-early.service                   masked         
cryptdisks.service                         masked         
cups-browsed.service                       enabled        
cups.service                               enabled        
dbus-fi.w1.wpa_supplicant1.service         enabled        
dbus-org.bluez.service                     enabled        
dbus-org.freedesktop.Avahi.service         enabled        
dbus-org.freedesktop.hostname1.service     static         
dbus-org.freedesktop.locale1.service       static         
dbus-org.freedesktop.login1.service        static         
dbus-org.freedesktop.ModemManager1.service enabled        
dbus-org.freedesktop.nm-dispatcher.service enabled        
dbus-org.freedesktop.resolve1.service      enabled        
dbus-org.freedesktop.thermald.service      enabled        
dbus-org.freedesktop.timedate1.service     static         
dbus.service                               static         
debug-shell.service                        disabled       
display-manager.service                    static         
dm-event.service                           static         
dns-clean.service                          enabled        
emergency.service                          static         
friendly-recovery.service                  enabled        
fstrim.service                             static         
fuse.service                               masked         
fwupd-offline-update.service               static         
fwupd.service                              static         
fwupdate-cleanup.service                   static         
gdm.service                                static         
gdm3.service                               static         
geoclue.service                            static         
getty-static.service                       static         
getty@.service                             enabled        
gpu-manager.service                        enabled        
grub-common.service                        generated      
halt.service                               masked         
hostname.service                           masked         
hwclock.service                            masked         
ifup@.service                              static         
iio-sensor-proxy.service                   static         
initrd-cleanup.service                     static         
initrd-parse-etc.service                   static         
initrd-switch-root.service                 static         
initrd-udevadm-cleanup-db.service          static         
irqbalance.service                         enabled        
kerneloops.service                         enabled        
keyboard-setup.service                     enabled        
killprocs.service                          masked         
kmod-static-nodes.service                  static         
kmod.service                               static         
lvm2-lvmetad.service                       static         
lvm2-lvmpolld.service                      static         
lvm2-monitor.service                       enabled        
lvm2-pvscan@.service                       static         
lvm2.service                               masked         
ModemManager.service                       enabled        
module-init-tools.service                  static         
motd-news.service                          static         
motd.service                               masked         
mountall-bootclean.service                 masked         
mountall.service                           masked         
mountdevsubfs.service                      masked         
mountkernfs.service                        masked         
mountnfs-bootclean.service                 masked         
mountnfs.service                           masked         
netplan-wpa@.service                       static         
network-manager.service                    enabled        
networkd-dispatcher.service                enabled        
networking.service                         enabled        
NetworkManager-dispatcher.service          enabled        
NetworkManager-wait-online.service         enabled        
NetworkManager.service                     enabled        
ondemand.service                           enabled        
packagekit-offline-update.service          static         
packagekit.service                         static         
plymouth-halt.service                      static         
plymouth-kexec.service                     static         
plymouth-log.service                       static         
plymouth-poweroff.service                  static         
plymouth-quit-wait.service                 static         
plymouth-quit.service                      static         
plymouth-read-write.service                static         
plymouth-reboot.service                    static         
plymouth-start.service                     static         
plymouth-switch-root.service               static         
plymouth.service                           static         
polkit.service                             static         
pppd-dns.service                           enabled        
procps.service                             static         
quotaon.service                            static         
rc-local.service                           static         
rc.local.service                           static         
rc.service                                 masked         
rcS.service                                masked         
reboot.service                             masked         
rescue.service                             static         
rmnologin.service                          masked         
rsync.service                              enabled        
rsyslog.service                            enabled        
rtkit-daemon.service                       disabled       
saned.service                              masked         
saned@.service                             indirect       
sendsigs.service                           masked         
serial-getty@.service                      disabled       
setvtrgb.service                           enabled        
single.service                             masked         
snapd.autoimport.service                   enabled        
snapd.core-fixup.service                   enabled        
snapd.service                              enabled        
snapd.snap-repair.service                  static         
snapd.system-shutdown.service              enabled        
speech-dispatcher.service                  generated      
spice-vdagent.service                      enabled        
spice-vdagentd.service                     enabled        
stop-bootlogd-single.service               masked         
stop-bootlogd.service                      masked         
sudo.service                               masked         
syslog.service                             enabled        
system-update-cleanup.service              static         
systemd-ask-password-console.service       static         
systemd-ask-password-plymouth.service      static         
systemd-ask-password-wall.service          static         
systemd-backlight@.service                 static         
systemd-binfmt.service                     static         
systemd-cryptsetup@sda3_crypt.service      generated      
systemd-exit.service                       static         
systemd-fsck-root.service                  enabled-runtime
systemd-fsck@.service                      static         
systemd-fsckd.service                      static         
systemd-halt.service                       static         
systemd-hibernate-resume@.service          static         
systemd-hibernate.service                  static         
systemd-hostnamed.service                  static         
systemd-hwdb-update.service                static         
systemd-hybrid-sleep.service               static         
systemd-initctl.service                    static         
systemd-journal-flush.service              static         
systemd-journald.service                   static         
systemd-kexec.service                      static         
systemd-localed.service                    static         
systemd-logind.service                     static         
systemd-machine-id-commit.service          static         
systemd-modules-load.service               static         
systemd-networkd-wait-online.service       disabled       
systemd-networkd.service                   disabled       
systemd-poweroff.service                   static         
systemd-quotacheck.service                 static         
systemd-random-seed.service                static         
systemd-reboot.service                     static         
systemd-remount-fs.service                 static         
systemd-resolved.service                   enabled        
systemd-rfkill.service                     static         
systemd-suspend-then-hibernate.service     static         
systemd-suspend.service                    static         
systemd-sysctl.service                     static         
systemd-timedated.service                  static         
systemd-timesyncd.service                  enabled        
systemd-tmpfiles-clean.service             static         
systemd-tmpfiles-setup-dev.service         static         
systemd-tmpfiles-setup.service             static         
systemd-udev-settle.service                static         
systemd-udev-trigger.service               static         
systemd-udevd.service                      static         
systemd-update-utmp-runlevel.service       static         
systemd-update-utmp.service                static         
systemd-user-sessions.service              static         
systemd-volatile-root.service              static         
thermald.service                           enabled        
udev.service                               static         
udisks2.service                            enabled        
ufw.service                                enabled        
umountfs.service                           masked         
umountnfs.service                          masked         
umountroot.service                         masked         
unattended-upgrades.service                enabled        
upower.service                             disabled       
urandom.service                            static         
ureadahead-stop.service                    static         
ureadahead.service                         enabled        
usb_modeswitch@.service                    static         
usbmuxd.service                            static         
user@.service                              static         
uuidd.service                              indirect       
wacom-inputattach@.service                 static         
whoopsie.service                           enabled        
wpa_supplicant-wired@.service              disabled       
wpa_supplicant.service                     enabled        
wpa_supplicant@.service                    disabled       
x11-common.service                         masked         


219 unit files listed.
tony@omenhp:~$ 



```


```

tony@omenhp:~$ systemctl --failed
0 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'.
tony@omenhp:~$ 

```

---

### Post by mIk3_08 on 2018-07-25
This systemctl command allows you to start, stop, or restart a service. You can also tell a service to “reload” its configuration. 
```
systemctl status name.service
systemctl start name.service
systemctl stop name.service
systemctl restart name.service
systemctl reload name.service
systemctl enable name.service
systemctl disable name.service
```
I think you must have to use systemctl disable command to disables a services and stops it from starting automatically with your computer.
I think you must have to disbale those services that you think that are not much important in your system to run.
Choose the services that is running under the result of;
```
systemctl list-unit-files --type=service
```

---

### Post by markackerman8@gmail.com on 2018-09-12
Same issue with my new Omen X 17-ap0xx

What the he$# is wrong, and sadly the keyboard lighting does NOT load like my previous Omen did in Ubuntu

Please help

Mark

---

### Post by hackman86 on 2018-10-14
I have the same issue when shutting down my Omen 15-CE080ND

My solution:
Just open my terminal and shutdown now does the trick.

---

### Post by jainesh3012 on 2019-01-23
Hi,

I have installed Ubuntu 16.04 on HP Omen Laptop and facing the below issues,
- Display goes blank after few mins and cannot recover unless hard press power button
- Keyboard LED backlight not working
- continuous error message on Ctl+Alt+F1 prompt,

unsupported event 0x86
unsupported event 0x86
unsupported event 0x86

Anyone have solution for these issues? Please help

---

### Post by davemc on 2019-05-04
Same acpi issue on Lenovo 20L4000BAU 10" touchscreen tablet, Celeron n4100, UHD 600 graphics, aka gemini lake.

Screen goes blank straight away, never gets to login prompt (Ubuntu 18.04 server, no X installed)

---

### Post by davemc on 2019-05-04
The acpi logging is reported in this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1786906?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1786906?comments=all)

But there is no mention of the black screen.

---

