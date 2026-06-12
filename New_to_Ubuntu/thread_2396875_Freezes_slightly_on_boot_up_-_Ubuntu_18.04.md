---
title: "Freezes slightly on boot up - Ubuntu 18.04"
date: 2018-07-22
forum: New to Ubuntu
---

### Post by ncfcdaniel on 2018-07-22
Seems to hang for 20/30 seconds before the login screen loads
Any way to fix this?

---

### Post by jeremy31 on 2018-07-22
What kernel in use, in terminal ```
uname -a
```

---

### Post by mIk3_08 on 2018-07-22
can you install inxi in your system
in your terminal type;
```
sudo apt-get install inxi
```
after successfully installed do ff. code
```
inxi -F
```
then copy and paste the result here in thread.

---

### Post by ncfcdaniel on 2018-07-22
> **mIk3_08 said:**
> can you install inxi in your system
in your terminal type;
```
sudo apt-get install inxi
```
after successfully installed do ff. code
```
inxi -F
```
then copy and paste the result here in thread.
Here it is

```

System:    Host: DD-Laptop Kernel: 4.15.0-29-generic x86_64 bits: 64
           Desktop: Gnome 3.28.2 Distro: Ubuntu 18.04 LTS
Machine:   Device: laptop System: Hewlett-Packard product: HP 15 Notebook PC v: 0974120000405F00000620180 serial: N/A
           Mobo: Hewlett-Packard model: 2336 v: 05.28 serial: N/A
           UEFI: Insyde v: F.40 date: 07/26/2016
Battery    BAT1: charge: 33.6 Wh 100.0% condition: 33.6/41.4 Wh (81%)
CPU:       Dual core Intel Core i3-5010U (-MT-MCP-) cache: 3072 KB
           clock speeds: max: 2000 MHz 1: 859 MHz 2: 953 MHz 3: 1024 MHz
           4: 912 MHz
Graphics:  Card: Intel HD Graphics 5500
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1366x768@59.99hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 5500 (Broadwell GT2)
           version: 4.5 Mesa 18.0.5
Audio:     Card-1 Intel Broadwell-U Audio Controller driver: snd_hda_intel
           Card-2 Intel Wildcat Point-LP High Def. Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-29-generic
Network:   Card-1: Realtek RTL8101/2/6E PCIE Fast/Gigabit Ethernet controller
           driver: r8169
           IF: enp8s0 state: down mac: d0:bf:9c:59:9d:de
           Card-2: Realtek RTL8723BE PCIe Wireless Network Adapter
           driver: rtl8723be
           IF: wlp9s0 state: up mac: ac:d1:b8:0b:5c:0d
Drives:    HDD Total Size: 1000.2GB (0.7% used)
           ID-1: /dev/sda model: ST1000LM024_HN size: 1000.2GB
Partition: ID-1: / size: 916G used: 6.3G (1%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 44.5C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 250 Uptime: 10 min Memory: 1666.9/7892.7MB
           Client: Shell (bash) inxi: 2.3.56 


```

---

### Post by ncfcdaniel on 2018-07-22
> **jeremy31 said:**
> What kernel in use, in terminal ```
uname -a
```

Linux DD-Laptop 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by mIk3_08 on 2018-07-23
please run this command in your terminal;
```
ls /etc/xdg/autostart/
```
then copy and paste the result here in thread

---

### Post by deadflowr on 2018-07-23
```
systemd-analyze blame
``` 
will output what's going on during boot up.
[https://www.freedesktop.org/software/systemd/man/systemd-analyze.html]("https://www.freedesktop.org/software/systemd/man/systemd-analyze.html")
This assume you mean before the login screen shows.
(Or that's as I read it)

---

### Post by mIk3_08 on 2018-07-23
yes, ncfcdaniel you can try this command below in terminal;
```
systemd-analyze blame
```
This command will view how long each process took to start, run this command:
Thanks a lot deadflowr

---

### Post by ncfcdaniel on 2018-07-23
> **mIk3_08 said:**
> yes, ncfcdaniel you can try this command below in terminal;
```
systemd-analyze blame
```
This command will view how long each process took to start, run this command:
Thanks a lot deadflowr

19.039s plymouth-quit-wait.service
         11.111s dev-sda3.device
          9.353s networkd-dispatcher.service
          9.148s networking.service
          8.366s NetworkManager-wait-online.service
          8.150s plymouth-start.service
          7.974s snapd.service
          7.677s ModemManager.service
          6.292s udisks2.service
          5.461s NetworkManager.service
          5.239s dev-loop5.device
          4.897s apport.service
          4.879s wpa_supplicant.service
          4.219s dev-loop2.device
          4.096s dev-loop4.device
          3.908s dev-loop3.device
          3.506s dev-loop0.device
          3.462s dev-loop1.device
          3.004s gpu-manager.service
          2.920s bluetooth.service
          2.904s pppd-dns.service
          2.810s rsyslog.service
          2.674s thermald.service

---

### Post by ncfcdaniel on 2018-07-23
> **mIk3_08 said:**
> please run this command in your terminal;
```
ls /etc/xdg/autostart/
```
then copy and paste the result here in thread


Here it is
> 

at-spi-dbus-bus.desktop
gnome-initial-setup-copy-worker.desktop
gnome-initial-setup-first-login.desktop
gnome-keyring-pkcs11.desktop
gnome-keyring-secrets.desktop
gnome-keyring-ssh.desktop
gnome-software-service.desktop
gnome-welcome-tour.desktop
nautilus-autostart.desktop
nm-applet.desktop
orca-autostart.desktop
org.gnome.SettingsDaemon.A11ySettings.desktop
org.gnome.SettingsDaemon.Clipboard.desktop
org.gnome.SettingsDaemon.Color.desktop
org.gnome.SettingsDaemon.Datetime.desktop
org.gnome.SettingsDaemon.DiskUtilityNotify.desktop
org.gnome.SettingsDaemon.Housekeeping.desktop
org.gnome.SettingsDaemon.Keyboard.desktop
org.gnome.SettingsDaemon.MediaKeys.desktop
org.gnome.SettingsDaemon.Mouse.desktop
org.gnome.SettingsDaemon.Power.desktop
org.gnome.SettingsDaemon.PrintNotifications.desktop
org.gnome.SettingsDaemon.Rfkill.desktop
org.gnome.SettingsDaemon.ScreensaverProxy.desktop
org.gnome.SettingsDaemon.Sharing.desktop
org.gnome.SettingsDaemon.Smartcard.desktop
org.gnome.SettingsDaemon.Sound.desktop
org.gnome.SettingsDaemon.Wacom.desktop
org.gnome.SettingsDaemon.XSettings.desktop
print-applet.desktop
pulseaudio.desktop
snap-userd-autostart.desktop
spice-vdagent.desktop
update-notifier.desktop
user-dirs-update-gtk.desktop
xdg-user-dirs.desktop



---

### Post by mIk3_08 on 2018-07-23
run again this command;
```
systemd-analyze
```

---

### Post by mIk3_08 on 2018-07-23
run this command also
```
systemctl list-unit-files &#8211;type=service
```
paste the result here in thread
as well as the result of;
```
systemd-analyze
```

---

### Post by ncfcdaniel on 2018-07-23
> **mIk3_08 said:**
> run again this command;
```
systemd-analyze
```

Startup finished in 3.809s (kernel) + 30.687s (userspace) = 34.497s
graphical.target reached after 30.651s in userspace

---

### Post by ncfcdaniel on 2018-07-23
> **mIk3_08 said:**
> run this command also
```
systemctl list-unit-files –type=service
```
paste the result here in thread
as well as the result of;
```
systemd-analyze
```

systemctl list-unit-files –type=service

0 unit files listed.

Startup finished in 3.809s (kernel) + 30.687s (userspace) = 34.497s
graphical.target reached after 30.651s in userspace



It does not seem to hang like this on the other distros

---

### Post by twily2018 on 2018-07-23
Show the output of: ```
systemctl --failed
```

It could be a start job that makes it wait.

---

