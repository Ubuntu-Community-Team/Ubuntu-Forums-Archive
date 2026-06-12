---
title: "Bluetooth not working."
date: 2023-02-01
forum: New to Ubuntu
---

### Post by eldonrosen on 2023-02-01
Hi 
I am new to Ubuntu. I had a few installations before with no big problems. I installed 20.04 i had a bit unstable Bluetooth connecton so i swich to piplewire that didn't work at all so i reinstaled whole think, since that i can't get it work at all. i upgraded to 20.10 still not luck !? Can someone point me in the right direction on how to solve this problem, please?

```
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; preset: enabled)
     Active: active (running) since Wed 2023-02-01 08:04:04 GMT; 11min ago
       Docs: man:bluetoothd(8)
   Main PID: 5782 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 14148)
     Memory: 664.0K
        CPU: 50ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;5782 /usr/lib/bluetooth/bluetoothd

Feb 01 08:04:04 Sony systemd[5782]: ConfigurationDirectory 'bluetooth' already exists but the mode is different. (File system: 755 Configurat>
Feb 01 08:04:04 Sony systemd[1]: Starting Bluetooth service...
Feb 01 08:04:04 Sony bluetoothd[5782]: Bluetooth daemon 5.65
Feb 01 08:04:04 Sony systemd[1]: Started Bluetooth service.
Feb 01 08:04:04 Sony bluetoothd[5782]: Starting SDP server
Feb 01 08:04:04 Sony bluetoothd[5782]: Bluetooth management interface 1.22 initialized
lines 1-18/18 (END)

```



```

systemctl | grep -i blue
  sys-devices-pci0000:00-0000:00:14.0-usb2-2\x2d4-2\x2d4:1.0-bluetooth-hci0.device         loaded active plugged   /sys/devices/pci0000:00/0000:00:14.0/usb2/2-4/2-4:1.0/bluetooth/hci0
  sys-subsystem-bluetooth-devices-hci0.device                                              loaded active plugged   /sys/subsystem/bluetooth/devices/hci0
  run-snapd-ns-bluetooth\x2dautostart.mnt.mount                                            loaded active mounted   /run/snapd/ns/bluetooth-autostart.mnt
  run-snapd-ns-bluez.mnt.mount                                                             loaded active mounted   /run/snapd/ns/bluez.mnt
  snap-bluetooth\x2dautostart-10.mount                                                     loaded active mounted   Mount unit for bluetooth-autostart, revision 10
  snap-bluez-334.mount                                                                     loaded active mounted   Mount unit for bluez, revision 334
  bluetooth.service                                                                        loaded active running   Bluetooth service
&#9679; snap.bluetooth-autostart.autostart-bluetooth.service                                     loaded failed failed    Service for snap application bluetooth-autostart.autostart-bluetooth
&#9679; snap.bluez.bluez.service                                                                 loaded failed failed    Service for snap application bluez.bluez
&#9679; snap.bluez.obex.service                                                                  loaded failed failed    Service for snap application bluez.obex
  bluetooth.target         


```

---

### Post by MAFoElffen on 2023-02-01
20.10 is end of service and unsupported by over 6 months. Did you mean 22.10?  I would go to 22.04LTS and stay with it until 24.04 LTS is released.

Just saying...

---

### Post by eldonrosen on 2023-02-01
Ok that's fine but on both of them bluetoorh not working

---

### Post by QIII on 2023-02-01
I would also recommend 22.04.

If you still have issues, please start a thread here.  We may be able to help you avoid thrashing around trying to fix things.

---

### Post by guiverc on 2023-02-01
I suggest you check what release you're using.

Ubuntu 20.10 is the 2020-October release (Ubuntu uses a *year.month* format for releases) and reached EOL back in 2021-July.

- [https://fridge.ubuntu.com/2021/07/25/ubuntu-20-10-groovy-gorilla-end-of-life-reached-on-july-22-2021/](https://fridge.ubuntu.com/2021/07/25/ubuntu-20-10-groovy-gorilla-end-of-life-reached-on-july-22-2021/)
- [https://lubuntu.me/lubuntu-20-10-end-of-life-and-current-support-statuses/](https://lubuntu.me/lubuntu-20-10-end-of-life-and-current-support-statuses/)

You also mention an upgrade to 20.10; which means either

- you're incorrectly stating 20.10 but mean another release, you need to correct your details so we can understand what you're running & thus provide you with useful advice, 

- the upgrade you mention to 20.10 occurred before 25 July 2021, but are asking the question now ~18 months later

- you're not running Ubuntu/Lubuntu at all, have a *corrupted* system or one so changed its not working right, and thus has more serious issues 

The reason is the file [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release) was modified on 25-July-2021 making a *release-upgrade* to 20.10 impossible with a valid Ubuntu/Lubuntu system.  Have a look in that file and you'll see
> Dist: groovy
Name: Groovy Gorilla
Version: 20.10
Date: Thu, 22 October 2020 20:22:00 UTC
Supported: 0
Description: This is the 20.10 release
Release-File: [http://old-releases.ubuntu.com/ubuntu/dists/groovy-updates/Release](http://old-releases.ubuntu.com/ubuntu/dists/groovy-updates/Release)
ReleaseNotes: [http://changelogs.ubuntu.com/EOLReleaseAnnouncement](http://changelogs.ubuntu.com/EOLReleaseAnnouncement)
UpgradeTool: [http://old-releases.ubuntu.com/ubuntu/dists/groovy-updates/main/dist-upgrader-all/current/groovy.tar.gz](http://old-releases.ubuntu.com/ubuntu/dists/groovy-updates/main/dist-upgrader-all/current/groovy.tar.gz)
UpgradeToolSignature: [http://old-releases.ubuntu.com/ubuntu/dists/groovy-updates/main/dist-upgrader-all/current/groovy.tar.gz.gpg](http://old-releases.ubuntu.com/ubuntu/dists/groovy-updates/main/dist-upgrader-all/current/groovy.tar.gz.gpg)

The *release-upgrade* from 20.04 LTS (*2020-April release*) to 22.04 LTS (*2022-April releas*e) is possible, but *upgrades *using the [Ubuntu Release Upgrader]("https://launchpad.net/ubuntu-release-upgrader") tool used by all Ubuntu systems including Lubuntu, checks the meta release file before proceeding.  If you did upgrade to 20.10 then I suggest Bluetooth is likely not your major concern.

---

### Post by eldonrosen on 2023-02-01
Okay, I reinstalled my laptop to 22.04 and encountered the same issue.Bluetooth is not working; the only difference is that I can turn it on, but it does not search for devices.

---

### Post by eldonrosen on 2023-02-01
sudo journalctl  -b 0 | grep blue
```

Feb 01 16:48:44 sony NetworkManager[802]: <info>  [1675270124.3618] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.36.6/libnm-device-plugin-bluetooth.so)
Feb 01 16:48:45 sony dbus-daemon[715]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service' requested by ':1.38' (uid=127 pid=969 comm="/usr/bin/pulseaudio --daemonize=no --log-target=jo" label="unconfined")
Feb 01 16:49:10 sony dbus-daemon[715]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
Feb 01 16:49:13 sony dbus-daemon[715]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service' requested by ':1.78' (uid=1000 pid=1537 comm="/usr/bin/pulseaudio --daemonize=no --log-target=jo" label="unconfined")
Feb 01 16:49:38 sony dbus-daemon[715]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
Feb 01 17:08:57 sony bluetoothd[7415]: Bluetooth daemon 5.64
Feb 01 17:08:57 sony bluetoothd[7415]: Starting SDP server
Feb 01 17:08:57 sony dbus-daemon[715]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.183' (uid=0 pid=7415 comm="/usr/lib/bluetooth/bluetoothd " label="unconfined")
Feb 01 17:08:57 sony bluetoothd[7415]: Bluetooth management interface 1.21 initialized
Feb 01 17:08:59 sony pulseaudio[1537]: Could not find org.bluez.BatteryProviderManager1.RegisterBatteryProvider(), is bluetoothd started with experimental features enabled (-E flag)?
Feb 01 17:08:59 sony bluetoothd[7415]: Endpoint registered: sender=:1.78 path=/MediaEndpoint/A2DPSink/sbc
Feb 01 17:08:59 sony bluetoothd[7415]: Endpoint registered: sender=:1.78 path=/MediaEndpoint/A2DPSource/sbc
Feb 01 17:08:59 sony bluetoothd[7415]: Endpoint registered: sender=:1.78 path=/MediaEndpoint/A2DPSink/sbc_xq_453
Feb 01 17:08:59 sony bluetoothd[7415]: Endpoint registered: sender=:1.78 path=/MediaEndpoint/A2DPSource/sbc_xq_453
Feb 01 17:08:59 sony bluetoothd[7415]: Endpoint registered: sender=:1.78 path=/MediaEndpoint/A2DPSink/sbc_xq_512
Feb 01 17:08:59 sony bluetoothd[7415]: Endpoint registered: sender=:1.78 path=/MediaEndpoint/A2DPSource/sbc_xq_512
Feb 01 17:08:59 sony bluetoothd[7415]: Endpoint registered: sender=:1.78 path=/MediaEndpoint/A2DPSink/sbc_xq_552
Feb 01 17:08:59 sony bluetoothd[7415]: Endpoint registered: sender=:1.78 path=/MediaEndpoint/A2DPSource/sbc_xq_552
Feb 01 17:09:15 sony dbus-daemon[1550]: [session uid=1000 pid=1550] Activating via systemd: service name='org.bluez.obex' unit='dbus-org.bluez.obex.service' requested by ':1.171' (uid=1000 pid=7439 comm="gnome-control-center " label="unconfined")
Feb 01 17:09:15 sony dbus-daemon[1550]: [session uid=1000 pid=1550] Successfully activated service 'org.bluez.obex'
Feb 01 17:10:55 sony bluetoothd[7415]: Endpoint unregistered: sender=:1.78 path=/MediaEndpoint/A2DPSink/sbc
Feb 01 17:10:55 sony bluetoothd[7415]: Endpoint unregistered: sender=:1.78 path=/MediaEndpoint/A2DPSource/sbc
Feb 01 17:10:55 sony bluetoothd[7415]: Endpoint unregistered: sender=:1.78 path=/MediaEndpoint/A2DPSink/sbc_xq_453
Feb 01 17:10:55 sony bluetoothd[7415]: Endpoint unregistered: sender=:1.78 path=/MediaEndpoint/A2DPSource/sbc_xq_453
Feb 01 17:10:55 sony bluetoothd[7415]: Endpoint unregistered: sender=:1.78 path=/MediaEndpoint/A2DPSink/sbc_xq_512
Feb 01 17:10:55 sony bluetoothd[7415]: Endpoint unregistered: sender=:1.78 path=/MediaEndpoint/A2DPSource/sbc_xq_512
Feb 01 17:10:55 sony bluetoothd[7415]: Endpoint unregistered: sender=:1.78 path=/MediaEndpoint/A2DPSink/sbc_xq_552
Feb 01 17:10:55 sony bluetoothd[7415]: Endpoint unregistered: sender=:1.78 path=/MediaEndpoint/A2DPSource/sbc_xq_552
Feb 01 17:13:41 sony pulseaudio[1537]: Could not find org.bluez.BatteryProviderManager1.RegisterBatteryProvider(), is bluetoothd started with experimental features enabled (-E flag)?

```

$ bluetoothctl

```

[bluetooth]# show
Controller 34:23:87:97:98:44 (public)
    Name: sony
    Alias: sony
    Class: 0x007c010c
    Powered: yes
    Discoverable: yes
    DiscoverableTimeout: 0x000000b4
    Pairable: yes
    UUID: Message Notification Se.. (00001133-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: OBEX Object Push          (00001105-0000-1000-8000-00805f9b34fb)
    UUID: Message Access Server     (00001132-0000-1000-8000-00805f9b34fb)
    UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
    UUID: IrMC Sync                 (00001104-0000-1000-8000-00805f9b34fb)
    UUID: Vendor specific           (00005005-0000-1000-8000-0002ee000001)
    UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
    UUID: Phonebook Access Server   (0000112f-0000-1000-8000-00805f9b34fb)
    UUID: Device Information        (0000180a-0000-1000-8000-00805f9b34fb)
    UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
    UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
    UUID: Handsfree Audio Gateway   (0000111f-0000-1000-8000-00805f9b34fb)
    UUID: Audio Source              (0000110a-0000-1000-8000-00805f9b34fb)
    UUID: OBEX File Transfer        (00001106-0000-1000-8000-00805f9b34fb)
    Modalias: usb:v1D6Bp0246d0540
    Discovering: yes
    Roles: central
    Roles: peripheral
Advertising Features:
    ActiveInstances: 0x00 (0)
    SupportedInstances: 0x05 (5)
    SupportedIncludes: tx-power
    SupportedIncludes: appearance
    SupportedIncludes: local-name

```

```

[bluetooth]# scan on
Failed to start discovery: org.bluez.Error.InProgress

```

---

### Post by eldonrosen on 2023-02-01
[COLOR=#252525]Okay, problem solved. Not bad for a Linux newbie.[/COLOR]
 [COLOR=#252525] 
[/COLOR]for anyone who faces the same problem.
run:
```
sudo dmesg | grep -i bluetooth # Shows all Bluetooth driver info
```

if you see something like that: 
```
[   12.850097] Bluetooth: hci0: BCM20702B0 (002.001.014) build 0607
[   13.054492] Bluetooth: hci0: BCM: firmware Patch file not found, tried:

```
solution is here 

[https://github.com/winterheart/broadcom-bt-firmware](https://github.com/winterheart/broadcom-bt-firmware)

---

### Post by guiverc on 2023-02-01
**Well done** for solving it, and **thank** **you** for sharing your fix so it helps others.

---

